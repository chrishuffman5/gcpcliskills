# gcloud access-context-manager — Access Context Manager (VPC Service Controls)

## Overview

`gcloud access-context-manager` manages Access Context Manager (ACM) resources for a Google Cloud organization: **access policies** (the container), **access levels** (attribute-based conditions on requests, such as IP range, region, or device state), and **service perimeters** (the resource sandboxes enforced by VPC Service Controls). ACM defines the rules in one central place; enforcement is performed by VPC Service Controls and Identity-Aware Proxy. Reach for it to lock down which Google Cloud services projects can reach, to gate access on request attributes, and to manage cloud access bindings and cross-organization trust. Most operations act on an organization-level policy, so identifiers are typically `organizations/...`, `folders/...`, or `projects/<projectnumber>`.

## Quick reference — common workflows

### Enable the API
```bash
gcloud services enable accesscontextmanager.googleapis.com
```

### Create an access policy (org-wide or scoped)
```bash
# Organization-wide policy (an org has at most one)
gcloud access-context-manager policies create \
    --organization=organizations/123 --title="My Org Policy"

# Scoped to a single folder (only projects under it can be perimeter-protected)
gcloud access-context-manager policies create \
    --organization=organizations/123 --scopes=folders/345 \
    --title="My Folder Policy"

# List policies to retrieve the POLICY_ID
gcloud access-context-manager policies list --organization=organizations/123
```

### Create a basic access level
Access levels specify the conditions a request must meet. Define a basic level from a YAML conditions spec.
```bash
gcloud access-context-manager levels create corp_network \
    --policy=POLICY_ID --title="Corp Network Level" \
    --basic-level-spec=ip-conditions.yaml --combine-function=and

gcloud access-context-manager levels describe corp_network --policy=POLICY_ID
gcloud access-context-manager levels list --policy=POLICY_ID
```

### Create a service perimeter (enforced)
A regular perimeter restricts the listed services for the projects inside the boundary.
```bash
gcloud access-context-manager perimeters create my_perimeter \
    --policy=POLICY_ID --title="My Storage Perimeter" \
    --resources=projects/12345 \
    --restricted-services=storage.googleapis.com \
    --access-levels=corp_network

gcloud access-context-manager perimeters describe my_perimeter --policy=POLICY_ID
```

### Test before enforcing with dry-run mode
Dry-run logs policy violations without denying requests — recommended before enforcement.
```bash
# Create a dry-run config on an existing perimeter
gcloud access-context-manager perimeters dry-run create my_perimeter \
    --policy=POLICY_ID --resources=projects/12345 \
    --restricted-services=bigquery.googleapis.com \
    --access-levels=accessPolicies/POLICY_ID/accessLevels/corp_network

# Inspect the dry-run vs enforced diff, then list across all perimeters
gcloud access-context-manager perimeters dry-run describe my_perimeter --policy=POLICY_ID
gcloud access-context-manager perimeters dry-run list --policy=POLICY_ID

# Promote one perimeter, or enforce all dry-run configs at once
gcloud access-context-manager perimeters dry-run enforce my_perimeter --policy=POLICY_ID
gcloud access-context-manager perimeters dry-run enforce-all --policy=POLICY_ID
```

### Update a perimeter (add/remove resources or services)
```bash
gcloud access-context-manager perimeters update my_perimeter \
    --policy=POLICY_ID \
    --add-resources=projects/67890 \
    --add-restricted-services=bigquery.googleapis.com \
    --remove-restricted-services=storage.googleapis.com \
    --add-access-levels=accessPolicies/POLICY_ID/accessLevels/other_level
```

### Check VPC-SC service support
```bash
gcloud access-context-manager supported-services list
gcloud access-context-manager supported-services describe bigquery.googleapis.com
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `access-context-manager authorized-orgs` | [`authorized-orgs.md`](authorized-orgs.md) | 5 | manage authorized organizations descriptions (cross-org trust) |
| `access-context-manager cloud-bindings` | [`cloud-bindings.md`](cloud-bindings.md) | 5 | manage cloud access bindings (per-group access level + session settings) |
| `access-context-manager levels` | [`levels.md`](levels.md) | 7 | manage access levels (incl. `levels conditions list`) |
| `access-context-manager perimeters` | [`perimeters.md`](perimeters.md) | 14 | manage service perimeters (incl. the `perimeters dry-run` subgroup) |
| `access-context-manager policies` | [`policies.md`](policies.md) | 9 | manage access policies and their IAM bindings |
| `access-context-manager supported-services` | [`supported-services.md`](supported-services.md) | 2 | list/describe VPC Service Controls supported services |

See [`index.md`](index.md) for a one-line index of all 42 GA commands.

## Common flags & tips

- **Policy identification.** Almost every command needs the policy. Pass `--policy=POLICY_ID`, set the `access_context_manager/policy` property, or rely on auto-detection when the account's organization has exactly one policy. On `levels`/`perimeters`, the resource can instead be given as a fully qualified name (e.g. `accessPolicies/123/accessLevels/abc`).
- **Resource forms.** `--organization` accepts `organizations/<number>`; `--scopes` accepts one `folders/<id>` or `projects/<number>`; `--resources` for perimeters takes `projects/<projectnumber>` (project numbers, not IDs).
- **Access levels: basic vs custom.** On `levels create`/`update`, supply *either* `--basic-level-spec=FILE` (with `--combine-function=and|or`, default `and`) *or* `--custom-level-spec=FILE` (a CEL expression) — they are mutually exclusive.
- **Perimeter add/remove/set/clear.** `perimeters update` (and `perimeters dry-run update`) offer `--add-*`, `--remove-*`, `--set-*`, and `--clear-*` variants for `resources`, `restricted-services`, `access-levels`, and `vpc-allowed-services`. Use `--enable-vpc-accessible-services` with `--add-vpc-allowed-services`/`--vpc-allowed-services`; disable with `--no-enable-vpc-accessible-services`.
- **Ingress/egress rules** are passed as YAML files: `--ingress-policies=FILE` / `--egress-policies=FILE` on create; `--set-ingress-policies` / `--set-egress-policies` / `--clear-*-policies` on update.
- **Bulk replace** with optimistic concurrency: `levels replace-all POLICY --source-file=FILE [--etag=ETAG]` and `perimeters replace-all POLICY --source-file=FILE [--etag=ETAG]`. Only the latest etag is accepted.
- **Long-running ops.** Most create/update/delete commands accept `--async` to return immediately without waiting.
- **Filtering & formatting** (standard gcloud flags on `list`/`get-iam-policy`):
  ```bash
  gcloud access-context-manager perimeters list --policy=POLICY_ID \
      --filter="title:prod" --format="table(name, title, perimeterType)"
  gcloud access-context-manager levels list --policy=POLICY_ID \
      --format="value(name, title)"
  ```
- **Policy IAM.** Manage access at the policy scope with `policies add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy`. Org-level roles: `roles/accesscontextmanager.policyAdmin` (full), `policyEditor` (read-write), `policyReader` (read-only); `roles/resourcemanager.organizationViewer` is needed for the Console.

## beta / alpha

- `gcloud beta access-context-manager` and `gcloud alpha access-context-manager` mirror the GA surface and expose pre-GA capabilities that may change without notice.
- **alpha-only** adds `levels config export`, `policies config export`, and a `supported-permissions` subgroup. **beta** also includes `supported-permissions` (not in GA). The `perimeters dry-run` subgroup is present in GA as well.
- Prefer GA for stable workflows; use alpha only when `config export` or `supported-permissions` is required.

## Official documentation

- Access Context Manager documentation home: https://cloud.google.com/access-context-manager/docs/overview — what ACM is, core concepts, relationship to VPC Service Controls.
- Create an access policy: https://cloud.google.com/access-context-manager/docs/create-access-policy — org-level and scoped policies.
- VPC Service Controls overview: https://cloud.google.com/vpc-service-controls/docs/overview — how perimeters enforce ACM rules.
- Create service perimeters: https://cloud.google.com/vpc-service-controls/docs/create-service-perimeters — Console and gcloud workflows.
- Ingress and egress rules: https://cloud.google.com/vpc-service-controls/docs/ingress-egress-rules — YAML syntax and evaluation semantics.
- Access control (IAM): https://cloud.google.com/access-context-manager/docs/access-control — roles and permissions for ACM.
- Access levels REST reference: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.accessLevels — BasicLevel/CustomLevel/Condition schema for spec files.
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/access-context-manager — all subgroups and commands.

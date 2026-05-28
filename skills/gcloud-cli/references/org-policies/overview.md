# gcloud org-policies — Organization Policy Service

## Overview
The Organization Policy Service gives administrators centralized, programmatic control over an organization's Google Cloud resources. You set *constraints* (built-in or custom) into *policies* attached at any node of the resource hierarchy — organization, folder, or project — and child nodes inherit them. Reach for `gcloud org-policies` to enforce guardrails (allowed resource locations, required OS Login, disabled service-account key creation, CMEK requirements, and more) across many projects from a single point of administration.

## Quick reference — common workflows

### Prerequisite — enable the API
```bash
gcloud services enable orgpolicy.googleapis.com
# Cloud Resource Manager API is also required (usually already enabled):
gcloud services enable cloudresourcemanager.googleapis.com
```

### 1. List policies set on a resource
```bash
# Policies currently set on a project
gcloud org-policies list --project=foo-project

# Policies on a folder, or the whole organization
gcloud org-policies list --folder=123456789
gcloud org-policies list --organization=1234

# Include every available constraint, even ones with no policy set
gcloud org-policies list --project=foo-project --show-unset
```

### 2. Describe a policy (set vs. effective)
```bash
# The policy set directly on this project for a constraint
gcloud org-policies describe gcp.resourceLocations --project=foo-project

# The effective policy — merged with everything inherited from parents
gcloud org-policies describe gcp.resourceLocations \
    --project=foo-project --effective

# A policy at the organization level
gcloud org-policies describe compute.requireOsLogin --organization=1234
```

### 3. Set a policy from a YAML/JSON file
Create `policy.yaml`:
```yaml
name: projects/PROJECT_ID/policies/gcp.resourceLocations
spec:
  rules:
  - values:
      denied_values:
      - in:us-east1-locations
```
Then apply it. `set-policy` creates the policy if it does not exist, or updates it if it does:
```bash
gcloud org-policies set-policy policy.yaml

# Overwrite only the live spec (leave any dry-run spec untouched)
gcloud org-policies set-policy policy.yaml --update-mask=policy.spec
```

### 4. Reset a policy to the constraint default
```bash
# Remove the explicit policy on a project (inherit from the parent again)
gcloud org-policies reset gcp.resourceLocations --project=foo-project

# Reset on a folder
gcloud org-policies reset compute.requireOsLogin --folder=123456789
```

### 5. Delete a policy
```bash
# Delete the policy for a constraint on a project
gcloud org-policies delete gcp.resourceLocations --project=foo-project

# Delete at the organization level, guarding against concurrent edits
gcloud org-policies delete compute.requireOsLogin \
    --organization=1234 --etag=CURRENT_ETAG
```

### 6. Manage custom constraints
Custom constraints live at the organization level. Create `constraint.yaml`:
```yaml
name: organizations/ORGANIZATION_ID/customConstraints/custom.requireCmekKey
resourceTypes:
- storage.googleapis.com/Bucket
methodTypes:
- CREATE
- UPDATE
condition: resource.encryption.defaultKmsKeyName != ""
actionType: ALLOW
displayName: Require CMEK key on Cloud Storage buckets
```
```bash
# Create or update the custom constraint
gcloud org-policies set-custom-constraint constraint.yaml

# Verify, list, and remove
gcloud org-policies describe-custom-constraint \
    custom.requireCmekKey --organization=1234
gcloud org-policies list-custom-constraints --organization=1234
gcloud org-policies delete-custom-constraint \
    custom.requireCmekKey --organization=1234
```
Once a custom constraint exists, enforce it like any built-in constraint with `set-policy` (referencing `custom.requireCmekKey` in the policy file).

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| Top-level commands | [`_commands.md`](_commands.md) | 9 | Full lifecycle for organization policies and custom constraints: list, describe, set-policy, reset, delete, and the four custom-constraint commands. |

See [`index.md`](index.md) for a one-line index of all 9 commands.

## Common flags & tips
- **Resource selector (required, mutually exclusive):** every policy command takes exactly one of `--project=PROJECT_ID`, `--folder=FOLDER_ID`, or `--organization=ORGANIZATION_ID`. Custom-constraint commands (`set-custom-constraint`, `describe-custom-constraint`, `list-custom-constraints`, `delete-custom-constraint`) operate only at the organization level (`--organization`), since custom constraints can only be defined there.
- **Constraint vs. custom constraint:** `describe` / `reset` / `delete` / `set-policy` act on *policies* (built-in or custom constraints applied to a resource). The `*-custom-constraint` commands manage the *definition* of custom constraints.
- **`--effective` (describe):** shows the merged result after inheritance from parent nodes — the policy actually enforced — rather than just the policy set directly on this resource.
- **`--show-unset` (list):** surfaces all available constraints for the resource, including those with no policy set, which is useful for discovering what you can govern.
- **`--update-mask` (set-policy, reset):** accepts an empty value, `policy.spec`, `policy.dry_run_spec`, or `*`. If the policy contains no dry-run spec and the flag is omitted, it defaults to `policy.spec`. Use this to update the dry-run spec without disturbing the live spec.
- **`--etag` (delete):** supply the current top-level policy etag to guard against concurrent modifications; a mismatch fails the delete with a concurrent error.
- **Filtering and output:** `list` and `list-custom-constraints` support the standard `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri` flags, plus `--format`. For example, list just the constraint names:
  ```bash
  gcloud org-policies list --organization=1234 --format="value(constraint)"
  ```
- **Policy files:** both `set-policy` and `set-custom-constraint` read a JSON or YAML file as a positional argument; the same command creates or updates. The `name` field in the file embeds the resource (`projects/`, `folders/`, or `organizations/`) and constraint, so it must agree with your intended target.

## Official documentation
- [Organization Policy Service overview](https://cloud.google.com/resource-manager/docs/organization-policy/overview) — core concepts: constraints, policies, inheritance, and dry-run mode.
- [Organization policy constraints catalog](https://cloud.google.com/resource-manager/docs/organization-policy/org-policy-constraints) — full list of built-in managed constraints across Google Cloud services.
- [Creating and managing policies](https://cloud.google.com/resource-manager/docs/organization-policy/creating-managing-policies) — how-to guide for applying policies via Console and gcloud.
- [Using constraints](https://cloud.google.com/resource-manager/docs/organization-policy/using-constraints) — prerequisites, required API and IAM roles, and how to apply constraints with gcloud.
- [Access control (Resource Manager / Org Policy)](https://cloud.google.com/resource-manager/docs/access-control-org) — IAM roles, including `roles/orgpolicy.policyAdmin`.
- [`set-policy` reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/set-policy) — policy YAML/JSON file format details.
- [`set-custom-constraint` reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/set-custom-constraint) — custom constraint file format.
- [gcloud org-policies command reference](https://cloud.google.com/sdk/gcloud/reference/org-policies) — GA reference for all 9 commands.

---
name: gcloud-organizations
description: >-
  Cloud Resource Manager (Organizations) via gcloud (`gcloud organizations`). Create and manage Google Cloud Platform Organizations.
---

# gcloud organizations — Cloud Resource Manager (Organizations)

## Overview

`gcloud organizations` manages the **organization** resource — the root node of the Google Cloud resource hierarchy (organization → folders → projects → resources), backed by the Cloud Resource Manager API. An organization is created automatically when a Google Workspace or Cloud Identity domain is associated with Google Cloud; you don't create one with the CLI. The command group is small and IAM-centric: you use it to identify your org, read its metadata, and — most importantly — view and manage the **org-level IAM policy**, whose bindings cascade down to every folder, project, and resource beneath it.

## Quick reference — common workflows

### 1. Enable the API and identify your organization

```bash
# Cloud Resource Manager backs all gcloud organizations commands
gcloud services enable cloudresourcemanager.googleapis.com

# List every organization the active account can see
gcloud organizations list

# Describe a specific org by numeric ID, or by domain
gcloud organizations describe 3589215982
gcloud organizations describe example.com
```

### 2. Inspect the org-level IAM policy

Org-level bindings are inherited by all child resources, so reviewing them is the
first step in any access audit.

```bash
# Full policy as YAML
gcloud organizations get-iam-policy 123456789

# Just the principals holding Organization Admin (filter on the policy bindings)
gcloud organizations get-iam-policy 123456789 \
  --filter="bindings.role:roles/resourcemanager.organizationAdmin" \
  --flatten="bindings[].members" \
  --format="table(bindings.role, bindings.members)"
```

### 3. Grant an org-level role (user or service account)

```bash
# Make a user Organization Administrator across the whole org
gcloud organizations add-iam-policy-binding 123456789 \
  --member='user:admin@example.com' \
  --role='roles/resourcemanager.organizationAdmin'

# Give a service account read-only org visibility
gcloud organizations add-iam-policy-binding 123456789 \
  --member='serviceAccount:auditor@my-project.iam.gserviceaccount.com' \
  --role='roles/resourcemanager.organizationViewer'
```

### 4. Grant a time-bound (conditional) binding

```bash
# Browser access that expires automatically at the start of 2019
gcloud organizations add-iam-policy-binding 123456789 \
  --member='user:test-user@example.com' \
  --role='roles/browser' \
  --condition='expression=request.time < timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,description=Expires at midnight on 2018-12-31'
```

### 5. Revoke an org-level binding

```bash
# Remove one specific binding
gcloud organizations remove-iam-policy-binding 123456789 \
  --member='user:former-admin@example.com' \
  --role='roles/resourcemanager.organizationAdmin'

# Remove every binding for this principal+role, regardless of condition
gcloud organizations remove-iam-policy-binding 123456789 \
  --member='user:test-user@gmail.com' \
  --role='roles/browser' \
  --all
```

### 6. Replace the whole policy from a file (read-modify-write)

```bash
# Export, edit, then apply atomically (set-iam-policy uses the etag for concurrency)
gcloud organizations get-iam-policy 123456789 --format=json > policy.json
# ...edit policy.json...
gcloud organizations set-iam-policy 123456789 policy.json
```

## Command groups

`gcloud organizations` has no subgroups — all six commands are top-level. Full flag
tables and per-command examples are in [`_commands.md`](_commands.md).

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| (top-level) | [`_commands.md`](_commands.md) | `add-iam-policy-binding`, `describe`, `get-iam-policy`, `list`, `remove-iam-policy-binding`, `set-iam-policy` | Identify organizations and manage their org-level IAM policy |

See [`index.md`](index.md) for the one-line command index.

## Common flags & tips

- **Org identifier:** every command accepts either the numeric organization ID
  (e.g. `3589215982`) or the associated domain (e.g. `example.com`). Domain lookup
  fails if the domain does not map to a unique org ID. Get the ID from
  `gcloud organizations list`.
- **IAM binding flags** (`add-iam-policy-binding` / `remove-iam-policy-binding`):
  `--member` and `--role` are both required. `--member` takes the
  `user:|group:|serviceAccount:|domain:` prefix form, plus the special values
  `allUsers` and `allAuthenticatedUsers`. `--role` is a full role path such as
  `roles/resourcemanager.organizationAdmin` or a custom role ID like
  `organizations/{ORG_ID}/roles/myRole`.
- **Conditional bindings:** supply `--condition` as `expression=...,title=...,description=...`
  (or `--condition-from-file=PATH`). Because condition expressions usually contain a
  comma, switch the delimiter, e.g. `--condition=^:^title=TITLE:expression=EXPRESSION`.
  `--condition=None` targets the no-condition binding. A conditional binding cannot use
  a basic role (`roles/owner`, `roles/editor`, `roles/viewer`).
- **Removing bindings:** on `remove-iam-policy-binding`, `--all`, `--condition`, and
  `--condition-from-file` are mutually exclusive. Use `--all` to drop every binding for a
  principal+role no matter the condition; omit it (or pass `--condition=None`) to target
  the unconditioned binding only.
- **Read-modify-write safety:** prefer `add-/remove-iam-policy-binding` for single
  changes — they handle the read-modify-write and etag for you. Use `set-iam-policy`
  only for bulk edits; export with `--format=json` first so the `etag` is preserved.
- **Listing & filtering:** `list` and `get-iam-policy` support `--filter`, `--limit`,
  `--sort-by`, and `--page-size`; `list` also supports `--uri`. Combine `--flatten`
  with `--format=table(...)` (gcloud-wide flags) to pivot policy bindings into a
  readable per-member view.

```bash
# Print just the org IDs and display names, sorted by name
gcloud organizations list --format="table(name, displayName)" --sort-by=displayName

# Emit resource URIs only (handy for scripting)
gcloud organizations list --uri
```

## beta / alpha

`gcloud beta organizations` and `gcloud alpha organizations` exist and expose the
**same six subcommands** as GA, with no additional capabilities. They carry the standard
pre-GA stability caveat ("might change without notice"). Prefer the GA commands for all
production use.

## Official documentation

- **Product docs home:** https://docs.cloud.google.com/resource-manager/docs — Cloud Resource Manager documentation hub.
- **Resource hierarchy overview:** https://docs.cloud.google.com/resource-manager/docs/overview — how organization, folders, and projects relate.
- **Creating & managing an organization:** https://docs.cloud.google.com/resource-manager/docs/creating-managing-organization — provisioning the org and assigning the Organization Admin role.
- **Org-level IAM roles:** https://docs.cloud.google.com/resource-manager/docs/access-control-org — predefined roles (`organizationAdmin`, `organizationViewer`, `orgpolicy.policyAdmin`).
- **Organization Policy:** https://docs.cloud.google.com/resource-manager/docs/organization-policy/overview — centralized constraints that govern all child resources.
- **IAM conditions overview:** https://cloud.google.com/iam/docs/conditions-overview — syntax for the `--condition` flag.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/organizations — authoritative command/flag reference.
- **Cloud Resource Manager REST API:** https://docs.cloud.google.com/resource-manager/reference/rest — v3 API (`cloudresourcemanager.googleapis.com`).

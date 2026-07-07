---
name: gcloud-resource-manager
description: >-
  Cloud Resource Manager via gcloud (`gcloud resource-manager`). Manage Cloud Resources — capabilities, folders, org-policies, tags.
---

# gcloud resource-manager — Cloud Resource Manager

## Overview

Cloud Resource Manager lets you hierarchically organize Google Cloud resources and control them centrally. Use `gcloud resource-manager` to manage **folders** (group projects under an organization), **org policies** (centralized constraints on resource configuration), **tags** (key/value labels for access control, policy enforcement, and cost attribution), and folder **capabilities**. Reach for it when structuring an org's resource hierarchy, enforcing governance guardrails, or attaching tags to resources.

## Quick reference — common workflows

### 1. Build a folder hierarchy under an organization

```bash
# Ensure the API is enabled (idempotent)
gcloud services enable cloudresourcemanager.googleapis.com

# Create a top-level folder under the org
gcloud resource-manager folders create \
    --display-name="Engineering" \
    --organization=123456789

# Create a sub-folder under the Engineering folder (use the returned folder ID)
gcloud resource-manager folders create \
    --display-name="Production" \
    --folder=111111111

# List folders under the org to confirm
gcloud resource-manager folders list --organization=123456789
```

### 2. Grant and inspect IAM on a folder

```bash
# Grant a user the Folder Admin role
gcloud resource-manager folders add-iam-policy-binding 111111111 \
    --member='user:admin@example.com' \
    --role='roles/resourcemanager.folderAdmin'

# Read the current IAM policy on the folder
gcloud resource-manager folders get-iam-policy 111111111

# Get IAM policies for the folder and all its ancestors
gcloud resource-manager folders get-ancestors-iam-policy 111111111
```

### 3. Move and rename a folder

```bash
# Move folder 222222222 under a different parent folder
gcloud resource-manager folders move 222222222 --folder=111111111

# Rename folder 222222222
gcloud resource-manager folders update 222222222 \
    --display-name="Staging"
```

### 4. Apply and inspect an Organization Policy (boolean constraint)

```bash
# Turn on enforcement of a boolean constraint on a project
gcloud resource-manager org-policies enable-enforce \
    compute.disableSerialPortAccess --project=my-project

# Turn it off on a folder
gcloud resource-manager org-policies disable-enforce \
    compute.disableSerialPortAccess --folder=111111111

# List set policies on a project, including available constraints
gcloud resource-manager org-policies list --project=my-project --show-unset

# Describe the effective policy on a project
gcloud resource-manager org-policies describe \
    compute.disableSerialPortAccess --project=my-project --effective
```

### 5. Create a tag taxonomy and bind a tag to a resource

```bash
# Create a tag key under the organization
gcloud resource-manager tags keys create env \
    --parent=organizations/123456789 \
    --description="Deployment environment"

# Create tag values under the key (use the returned key ID, e.g. tagKeys/456)
gcloud resource-manager tags values create production --parent=tagKeys/456
gcloud resource-manager tags values create staging --parent=tagKeys/456

# Bind a tag value to a project resource (use the returned value ID, e.g. tagValues/789)
gcloud resource-manager tags bindings create \
    --tag-value=tagValues/789 \
    --parent=//cloudresourcemanager.googleapis.com/projects/1234567890

# List all tags bound to the resource
gcloud resource-manager tags bindings list \
    --parent=//cloudresourcemanager.googleapis.com/projects/1234567890
```

### 6. Delete and recover a folder

```bash
# Delete a folder (must be empty — no projects or sub-folders)
gcloud resource-manager folders delete 222222222

# Recover a recently deleted folder
gcloud resource-manager folders undelete 222222222
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `resource-manager capabilities` | [`capabilities.md`](capabilities.md) | 2 | manage Cloud Folder Capabilities |
| `resource-manager folders` | [`folders.md`](folders.md) | 12 | manage Cloud Folders |
| `resource-manager org-policies` | [`org-policies.md`](org-policies.md) | 8 | manage Org Policies |
| `resource-manager tags` | [`tags.md`](tags.md) | 24 | create and manipulate tag keys, values, and bindings |

See [`index.md`](index.md) for a one-line index of all 46 GA commands.

## Common flags & tips

- **Parent selection.** `folders create`, `folders list`, and `folders move` take exactly one of `--organization=ORG_ID` or `--folder=FOLDER_ID` as the parent. Org-policy commands (`allow`, `deny`, `describe`, `delete`, `list`, `set-policy`, `enable-enforce`, `disable-enforce`) require exactly one of `--organization`, `--folder`, or `--project`.
- **Folder IDs are bare numbers.** Pass the numeric folder ID positionally (e.g. `folders describe 3589215982`); there is no `folders/` prefix on the GA surface.
- **Tag naming.** Tag keys/values accept either a numeric resource name (`tagKeys/456`, `tagValues/789`) or a namespaced name (`123456789/env`, `123456789/env/production`). Tag key parents must be `organizations/{org_id}`; tag value parents are `tagKeys/{id}` or `{org_id}/{tag_key_short_name}`.
- **Tag bindings use full resource names.** `--parent` for `tags bindings` must be the full resource name, e.g. `//cloudresourcemanager.googleapis.com/projects/1234567890`. Add `--location=REGION` for regional/zonal resources (omit for global resources like projects, folders, organizations). Use `--effective` on `tags bindings list` to include inherited bindings.
- **Async operations.** `folders create/move`, `tags keys/values create/update/delete`, and `tags bindings create/delete` accept `--async` to return immediately without waiting.
- **Filtering & formatting.** List/get-iam-policy commands support the standard `--filter`, `--sort-by`, `--limit`, and `--format`. Example: `gcloud resource-manager folders list --organization=123456789 --filter="displayName:Prod*" --format="table(displayName, name, lifecycleState)"`.
- **Org Policy constraints reference.** Use `--show-unset` on `org-policies list` to discover available constraint names before applying them.

## beta / alpha

- **`gcloud beta resource-manager`** — same four subgroups as GA (capabilities, folders, org-policies, tags), marked as possibly changing without notice; no documented functionality beyond GA.
- **`gcloud alpha resource-manager`** — adds three subgroups not present in GA/beta:
  - `liens` — manage liens that prevent project deletion (create/remove project deletion locks).
  - `operations` — query long-running Resource Manager operations.
  - `semantics-catalog` — view semantic catalog entries.

## Official documentation

- [Cloud Resource Manager docs (product home)](https://cloud.google.com/resource-manager/docs) — overview of the resource hierarchy (organizations, folders, projects) and all sub-topics.
- [gcloud resource-manager CLI reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager) — full command/flag reference for folders, org-policies, tags, and capabilities.
- [Creating and managing folders](https://cloud.google.com/resource-manager/docs/creating-managing-folders) — how to create, move, delete, and restore folders.
- [Access control for folders](https://cloud.google.com/resource-manager/docs/access-control-folders) — folder IAM roles (folderAdmin, folderCreator, folderEditor, folderMover, folderViewer).
- [Access control for organizations](https://cloud.google.com/resource-manager/docs/access-control-org) — organization IAM roles (organizationAdmin, orgpolicy.policyAdmin, organizationViewer).
- [Organization Policy overview](https://cloud.google.com/resource-manager/docs/organization-policy/overview) — centralized, programmatic control over resource configuration.
- [Understanding constraints](https://cloud.google.com/resource-manager/docs/organization-policy/understanding-constraints) — how list and boolean constraints restrict service behavior.
- [Tags overview](https://cloud.google.com/resource-manager/docs/tags/tags-overview) — key-value tags for access control, policy enforcement, and cost attribution.
- [Creating and managing tags](https://cloud.google.com/resource-manager/docs/tags/tags-creating-and-managing) — create tag keys/values and bind tags to resources with gcloud.

See [`sources.md`](sources.md) for the full citation record.

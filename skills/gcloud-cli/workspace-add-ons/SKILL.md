---
name: gcloud-workspace-add-ons
description: >-
  Google Workspace Add-ons via gcloud (`gcloud workspace-add-ons`). Manage Google Workspace Add-ons resources — deployments.
---

# gcloud workspace-add-ons — Google Workspace Add-ons

## Overview
`gcloud workspace-add-ons` manages Google Workspace Add-ons deployments — the resources that extend Google Workspace host apps (Gmail, Docs, Sheets, Slides, Calendar, Drive, etc.) and can be built on Apps Script or any HTTP-based alternate runtime. Reach for it to create, install, replace, and delete add-on deployments from the command line, and to inspect the project's add-on authorization (service account) info. It wraps the `gsuiteaddons.googleapis.com` (v1) API; deployment configuration is supplied as a JSON manifest file or inline JSON object.

## Quick reference — common workflows

### 1. Enable the API and check project authorization
```bash
# Enable the Google Workspace Add-ons API
gcloud services enable gsuiteaddons.googleapis.com

# Get the service-account authorization info for the current project
gcloud workspace-add-ons get-authorization
```

### 2. Create a deployment from a manifest file
```bash
# Create a new deployment from a deployment manifest (JSON) file
gcloud workspace-add-ons deployments create my-deployment \
    --deployment-file=my-deployment.json

# Confirm it was created
gcloud workspace-add-ons deployments describe my-deployment
```

### 3. List and inspect deployments
```bash
# List all deployments in the current project
gcloud workspace-add-ons deployments list

# Describe a specific deployment
gcloud workspace-add-ons deployments describe my-deployment
```

### 4. Install and verify a deployment (for testing)
```bash
# Install the deployment into your own account for testing
gcloud workspace-add-ons deployments install my-deployment

# Check whether it is installed
gcloud workspace-add-ons deployments install-status my-deployment
```

### 5. Update (replace) a deployment
```bash
# Replace an existing deployment with an updated manifest
gcloud workspace-add-ons deployments replace my-deployment \
    --deployment-file=my-deployment-v2.json

# Use --etag for optimistic concurrency (value from describe output)
gcloud workspace-add-ons deployments replace my-deployment \
    --deployment-file=my-deployment-v2.json \
    --etag="abc123"
```

### 6. Uninstall and delete a deployment
```bash
# Uninstall the test deployment from your account
gcloud workspace-add-ons deployments uninstall my-deployment

# Delete the deployment resource from the project (optionally with --etag)
gcloud workspace-add-ons deployments delete my-deployment --etag="abc123"
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `workspace-add-ons deployments` | [`deployments.md`](deployments.md) | 8 | Manage Google Workspace Add-ons deployments (create, delete, describe, install, install-status, list, replace, uninstall) |
| `workspace-add-ons` (top-level) | [`_commands.md`](_commands.md) | 1 | `get-authorization` — authorization info for deployments in a project |

See [`index.md`](index.md) for a one-line index of all 9 commands.

## Common flags & tips
- **Deployment source (mutually exclusive, required on `create`/`replace`):** supply either `--deployment-file=PATH` (path to a JSON manifest) or `--deployment-object=JSON` (inline JSON string). Exactly one must be given.
- **Optimistic concurrency:** `deployments delete` and `deployments replace` accept `--etag=ETAG`. Pass the etag returned by `deployments describe` to avoid overwriting/deleting a deployment that changed since you last read it.
- **Project scoping:** the `DEPLOYMENT` positional can be a bare ID or a fully qualified resource name. The project is resolved from a fully qualified name, `--project`, or the `core/project` property.
- **install vs. install-status:** `install` deploys the add-on into the calling user's account for testing; `install-status` reports whether it is currently installed; `uninstall` removes it.
- **Listing:** `deployments list` supports the standard `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri` flags. Examples:
  - `gcloud workspace-add-ons deployments list --limit=10`
  - `gcloud workspace-add-ons deployments list --uri` — print just resource URIs
  - `gcloud workspace-add-ons deployments list --format="table(name)"`
- **Inspecting one deployment:** `gcloud workspace-add-ons deployments describe my-deployment --format="value(etag)"` to grab the etag for a subsequent `replace`/`delete`.

## Official documentation
- Product docs home — Google Workspace Add-ons: https://developers.google.com/workspace/add-ons
- Overview (types, capabilities, entry points): https://developers.google.com/workspace/add-ons/overview
- Alternate runtimes (HTTP / non-Apps Script add-ons): https://developers.google.com/workspace/add-ons/guides/alternate-runtimes
- REST API reference (`gsuiteaddons.googleapis.com` v1): https://developers.google.com/workspace/add-ons/reference/rest
- REST resource `projects.deployments` (create/delete/get/install/list/replace/uninstall): https://developers.google.com/workspace/add-ons/reference/rest/v1/projects.deployments
- gcloud CLI reference — command group: https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons
- gcloud CLI reference — deployments subcommands: https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons/deployments

# gcloud deployment-manager — Cloud Deployment Manager

## Overview

> **END OF SUPPORT: March 31, 2026.** Cloud Deployment Manager reaches end of support on this date. Google recommends migrating to **[Infrastructure Manager](https://cloud.google.com/infrastructure-manager/docs)** (`gcloud infra-manager`, which uses Terraform) or to Terraform directly. Do not start new projects on Deployment Manager.

Cloud Deployment Manager is Google Cloud's legacy infrastructure-as-code service. It creates and manages Google Cloud resources declaratively from YAML configuration files plus Jinja2/Python templates, grouping them into a single unit called a *deployment*. Reach for it only to inspect, update, or wind down existing deployments; for new work use Infrastructure Manager or Terraform instead.

## Quick reference — common workflows

**Prerequisite — enable the API once per project:**

```bash
gcloud services enable deploymentmanager.googleapis.com
```

### 1. Create a deployment from a YAML config

```bash
# Create a deployment from a top-level YAML configuration file
gcloud deployment-manager deployments create my-deployment \
    --config=config.yaml \
    --description="My first deployment"

# Check status, then list the resources it created
gcloud deployment-manager deployments describe my-deployment
gcloud deployment-manager resources list --deployment=my-deployment
```

### 2. Preview a deployment, then instantiate it

```bash
# Preview without instantiating the underlying resources
gcloud deployment-manager deployments create my-deployment \
    --config=config.yaml \
    --preview

# Inspect what would be created
gcloud deployment-manager resources list --deployment=my-deployment

# Apply the previewed deployment — run update with NO config flag
gcloud deployment-manager deployments update my-deployment
```

### 3. Update an existing deployment

```bash
# Update with a new config file (preview first, then apply)
gcloud deployment-manager deployments update my-deployment \
    --config=new_config.yaml \
    --preview
gcloud deployment-manager deployments update my-deployment

# Update with explicit create/delete policies for changed resources
gcloud deployment-manager deployments update my-deployment \
    --config=new_config.yaml \
    --create-policy=acquire \
    --delete-policy=abandon
```

### 4. Deploy directly from a template or composite type

```bash
# From a Jinja or Python template, passing properties
gcloud deployment-manager deployments create my-deployment \
    --template=template.jinja \
    --properties="string-key:'string-value',integer-key:12345"

# From a composite type registered in the project
gcloud deployment-manager deployments create my-deployment \
    --composite-type=<project-id>/composite:<type-name> \
    --properties="string-key:'string-value',integer-key:12345"
```

### 5. Inspect manifests and operations

```bash
# List manifests for a deployment; describe the latest one
gcloud deployment-manager manifests list --deployment=my-deployment
gcloud deployment-manager manifests describe --deployment=my-deployment

# List all operations in the project, then wait for one to finish
gcloud deployment-manager operations list
gcloud deployment-manager operations wait operation-name
```

### 6. Manage labels and delete deployments

```bash
# Add labels at create time
gcloud deployment-manager deployments create my-deployment \
    --config=config.yaml \
    --labels=env=prod,team=infra

# Change labels on an existing deployment (no config flag needed)
gcloud deployment-manager deployments update my-deployment \
    --update-labels=env=staging \
    --remove-labels=team

# Delete a deployment and all its resources (use -q to skip the prompt)
gcloud deployment-manager deployments delete my-deployment

# Abandon resources instead of deleting them; or delete asynchronously
gcloud deployment-manager deployments delete my-deployment --delete-policy=abandon
gcloud deployment-manager deployments delete my-deployment --async
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `deployment-manager deployments` | [`deployments.md`](deployments.md) | 7 | Create, preview, update, stop, cancel-preview, describe, list, and delete deployments |
| `deployment-manager manifests` | [`manifests.md`](manifests.md) | 2 | Describe and list the manifests (expanded config snapshots) of a deployment |
| `deployment-manager operations` | [`operations.md`](operations.md) | 3 | Describe, list, and wait on asynchronous operations |
| `deployment-manager resources` | [`resources.md`](resources.md) | 2 | Describe and list the resources within a deployment |
| `deployment-manager types` | [`types.md`](types.md) | 1 | List the resource types available in the project |

See [`index.md`](index.md) for a one-line index of all 15 commands.

## Common flags & tips

- **Source flags are mutually exclusive (create/update):** exactly one of `--config` (top-level YAML), `--template` (a `.jinja`/`.py` template), or `--composite-type` defines what to deploy. On `update`, all three are optional — omit them to instantiate an already-previewed deployment, or to change only metadata via `--update-labels` / `--remove-labels` / `--description`.
- **Preview/apply pattern:** `--preview` on `create` or `update` validates and plans without touching real resources. Apply the previewed change by running `deployments update <name>` with no source flag.
- **Optimistic locking:** `--fingerprint` is accepted by `update`, `stop`, and `cancel-preview` to guard against concurrent modifications. If omitted, gcloud fetches the latest fingerprint first.
- **Policies (update/delete):** `--create-policy` is one of `acquire` or `create-or-acquire` (default `create-or-acquire`); `--delete-policy` is one of `abandon` or `delete` (default `delete`). `abandon` removes the resource from the deployment without deleting it.
- **Async:** `--async` (on `create`, `update`, `delete`, `stop`, `cancel-preview`) returns immediately; track progress with `operations list` / `operations wait`.
- **List helpers:** most `list` commands accept `--simple-list` (print only names/IDs), plus the standard `--filter`, `--limit`, `--sort-by`, and `--uri` flags. `manifests` commands require `--deployment`; for `resources` it is optional.
- **`--format` / `--filter` examples:**
  - `gcloud deployment-manager deployments list --format="table(name, operation.operationType, operation.status)"`
  - `gcloud deployment-manager deployments list --filter="labels.env=prod" --simple-list`
  - `gcloud deployment-manager resources list --deployment=my-deployment --format="value(name)"`
- **Resource naming / scope:** deployments are project-global (not regional or zonal). Set the project with `--project` or `gcloud config set project`. Composite types are referenced as `<project-id>/composite:<type-name>`.
- **Service account:** the Deployment Manager service account must hold `editor` (or appropriate resource-specific roles) on the project so it can actuate the underlying resources.

## beta / alpha

The 15 GA commands cover all core operations; no critical functionality is known to be beta/alpha-only for this service group. Some capabilities may also be available under `gcloud beta deployment-manager` or `gcloud alpha deployment-manager` — check `gcloud beta deployment-manager --help` and `gcloud alpha deployment-manager --help` for any experimental flags or subcommands not present in GA.

## Official documentation

- **Product docs home:** https://docs.cloud.google.com/deployment-manager/docs — service overview, with the March 31, 2026 end-of-support notice.
- **Fundamentals:** https://docs.cloud.google.com/deployment-manager/docs/fundamentals — core concepts (configurations, templates, resources, types, manifests, deployments).
- **Quickstart:** https://docs.cloud.google.com/deployment-manager/docs/quickstart — deploy a VM from a YAML config using `deployments create`/`describe`/`delete`.
- **Create a basic configuration:** https://docs.cloud.google.com/deployment-manager/docs/configuration/create-basic-configuration — author a YAML config defining resources, imports, and outputs.
- **Updating deployments:** https://docs.cloud.google.com/deployment-manager/docs/deployments/updating-deployments — add/remove resources, change properties, and choose update policies.
- **Composite types:** https://docs.cloud.google.com/deployment-manager/docs/configuration/templates/create-composite-types — build reusable template bundles callable like native types.
- **Access control (IAM):** https://docs.cloud.google.com/deployment-manager/docs/access-control — admin, editor, viewer, type-editor, and type-viewer roles.
- **Migration target — Infrastructure Manager:** https://cloud.google.com/infrastructure-manager/docs — recommended replacement (Terraform-based).
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/deployment-manager — all 5 command groups.

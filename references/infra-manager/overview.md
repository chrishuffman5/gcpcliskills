# gcloud infra-manager — Infrastructure Manager

## Overview

Infrastructure Manager is a managed Google Cloud service that automates the deployment and lifecycle management of Google Cloud infrastructure using Terraform configurations. Reach for it when you want Google to run `terraform apply`/`plan` for you — sourcing configs from a Cloud Storage bucket, a Git repository, or a local directory — without operating your own Terraform runner. Each apply is tracked as a numbered revision, you can run plan-only previews before committing changes, and the service can detect drift between deployed state and live resources. The CLI surface lives under `gcloud infra-manager` and the underlying API is `config.googleapis.com`.

## Quick reference — common workflows

### 1. Enable the API and grant the deploying service account
```bash
# One-time per project
gcloud services enable config.googleapis.com

# A dedicated service account (passed via --service-account below) must hold
# roles/config.agent plus permissions to actuate the target resources.
```

### 2. Preview infrastructure changes (terraform plan) before applying
```bash
# Create a plan-only preview from a Git-sourced Terraform module
gcloud infra-manager previews create \
    projects/p1/locations/us-central1/previews/my-preview \
    --service-account="projects/p1/serviceAccounts/infra-sa@p1.iam.gserviceaccount.com" \
    --git-source-repo="https://github.com/examples/repository.git" \
    --git-source-directory="staging/compute" \
    --git-source-ref="mainline" \
    --input-values="project=p1,region=us-central1"

# Check preview status, then download the plan artifacts
gcloud infra-manager previews describe \
    projects/p1/locations/us-central1/previews/my-preview
gcloud infra-manager previews export \
    projects/p1/locations/us-central1/previews/my-preview --file=preview.zip

# Clean up the preview when done
gcloud infra-manager previews delete \
    projects/p1/locations/us-central1/previews/my-preview
```

### 3. Create or update a deployment from a Git source
```bash
# apply creates the deployment if it does not exist, otherwise updates it
gcloud infra-manager deployments apply \
    projects/p1/locations/us-central1/deployments/my-deployment \
    --service-account="projects/p1/serviceAccounts/infra-sa@p1.iam.gserviceaccount.com" \
    --git-source-repo="https://github.com/examples/repository.git" \
    --git-source-directory="staging/compute" \
    --git-source-ref="mainline" \
    --labels="env=prod,team=finance"

gcloud infra-manager deployments describe \
    projects/p1/locations/us-central1/deployments/my-deployment
```

### 4. Create a deployment from Cloud Storage
```bash
gcloud infra-manager deployments apply \
    projects/p1/locations/us-central1/deployments/my-deployment \
    --gcs-source="gs://my-bucket" \
    --input-values="project=p1,region=us-central1" \
    --artifacts-gcs-bucket="gs://my-artifacts-bucket/logs"

gcloud infra-manager deployments list --location=us-central1
```

### 5. Inspect revisions and managed resources
```bash
# Each apply produces a new revision; list them for a deployment
gcloud infra-manager revisions list \
    --deployment=projects/p1/locations/us-central1/deployments/my-deployment

gcloud infra-manager revisions describe \
    projects/p1/locations/us-central1/deployments/my-deployment/revisions/r-0

# List the resources a revision manages, then export its Terraform state
gcloud infra-manager resources list \
    --revision=projects/p1/locations/us-central1/deployments/my-deployment/revisions/r-0
gcloud infra-manager revisions export-statefile \
    projects/p1/locations/us-central1/deployments/my-deployment/revisions/r-0
```

### 6. Lock a deployment to import an external state file
```bash
gcloud infra-manager deployments lock \
    projects/p1/locations/us-central1/deployments/my-deployment

gcloud infra-manager deployments import-statefile \
    projects/p1/locations/us-central1/deployments/my-deployment \
    --lock-id=1658343229583347 --file=./terraform.tfstate

gcloud infra-manager deployments unlock \
    projects/p1/locations/us-central1/deployments/my-deployment \
    --lock-id=1658343229583347
```

### 7. Delete a deployment
```bash
# Destroy all resources actuated by the deployment
gcloud infra-manager deployments delete \
    projects/p1/locations/us-central1/deployments/my-deployment \
    --delete-policy=delete

# Or abandon resources and delete only the deployment metadata
gcloud infra-manager deployments delete \
    projects/p1/locations/us-central1/deployments/my-deployment \
    --delete-policy=abandon
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `infra-manager automigrationconfig` | [`automigrationconfig.md`](automigrationconfig.md) | 3 | manage auto migration config resources |
| `infra-manager deployments` | [`deployments.md`](deployments.md) | 9 | manage Deployment resources |
| `infra-manager previews` | [`previews.md`](previews.md) | 5 | manage Preview resources |
| `infra-manager resource-changes` | [`resource-changes.md`](resource-changes.md) | 2 | manage resource change resources |
| `infra-manager resource-drifts` | [`resource-drifts.md`](resource-drifts.md) | 2 | manage resource drift resources |
| `infra-manager resources` | [`resources.md`](resources.md) | 2 | list or describe resources under a Revision |
| `infra-manager revisions` | [`revisions.md`](revisions.md) | 3 | manage Revision resources |
| `infra-manager terraform-versions` | [`terraform-versions.md`](terraform-versions.md) | 2 | manage Terraform version resources |

See [`index.md`](index.md) for a one-line index of all 28 commands.

## Common flags & tips

- **Resource naming.** Most commands take a fully qualified resource path as a positional argument, e.g. `projects/PROJECT/locations/LOCATION/deployments/DEPLOYMENT`. Revisions nest under deployments (`.../deployments/D/revisions/r-0`) and resources nest under revisions (`.../revisions/r-0/resources/RESOURCE`). If you pass only the short ID you must supply `--location` (and `--deployment`/`--revision` where applicable), or set the `infra-manager/location` property.
- **Location is required and regional.** Deployments, previews, revisions, and Terraform versions are regional (e.g. `us-central1`). Set a default with `gcloud config set infra-manager/location us-central1` to omit `--location`.
- **Source selection (mutually exclusive).** `deployments apply` and `previews create` accept exactly one source: `--gcs-source`, the Git trio (`--git-source-repo` + `--git-source-directory` + `--git-source-ref`), `--local-source`, or an `--inputs-file`. Pass Terraform variables with `--input-values=KEY=VALUE,...`.
- **Service account.** Use `--service-account=projects/PROJECT/serviceAccounts/SA@PROJECT.iam.gserviceaccount.com` so Infra Manager actuates resources as a dedicated identity rather than your user credentials.
- **Long operations.** `apply`, `delete`, `lock`, `unlock`, and the `automigrationconfig` enable/disable commands accept `--async` to return immediately instead of waiting.
- **Idempotent apply.** `deployments apply` creates the deployment if it is absent and updates it otherwise — there is no separate create/update command. `--labels`/`--annotations` overwrite existing values (pass `--labels=""` to clear).
- **Drift and change review.** After a preview, inspect planned changes with `resource-changes list --preview=...` and detected drift with `resource-drifts list --preview=...`.
- **Filtering and formatting** work on every `list` command, e.g.:
  ```bash
  gcloud infra-manager deployments list --location=us-central1 \
      --filter="labels.env=prod" \
      --format="table(name, state, latestRevision)"
  ```
- **State management.** Export a deployment's state with `deployments export-statefile` (add `--draft` for the draft state) or a specific revision's state with `revisions export-statefile`. To import external state you must first `lock` the deployment and pass the returned `--lock-id` to `import-statefile`.

## Official documentation

- Product docs home: https://docs.cloud.google.com/infrastructure-manager/docs — Infrastructure Manager documentation hub.
- Product overview: https://docs.cloud.google.com/infrastructure-manager/docs/overview — what Infra Manager is, scope, and key concepts.
- Quickstart: https://docs.cloud.google.com/infrastructure-manager/docs/quickstart — deploy a VPC using a Git-sourced Terraform module.
- Preview a deployment: https://docs.cloud.google.com/infrastructure-manager/docs/preview-deployment — create and use previews (terraform plan) before deploying.
- View managed resources: https://docs.cloud.google.com/infrastructure-manager/docs/view-resources — list and describe resources under a revision.
- Access control (IAM): https://docs.cloud.google.com/infrastructure-manager/docs/access-control — roles and permissions for Infrastructure Manager.
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/infra-manager — full command reference for all `infra-manager` groups.

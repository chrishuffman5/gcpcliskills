# gcloud workbench — Vertex AI Workbench

## Overview
`gcloud workbench` manages **Vertex AI Workbench instances** — managed, JupyterLab-based notebook environments for data science and ML on Google Cloud, integrated with BigQuery, Cloud Storage, and Vertex AI. This is the newer **unified Workbench** ("instances"), which supersedes the older user-managed and managed notebook products that live under `gcloud notebooks`. Reach for this group to create, configure, and run the lifecycle of Workbench instance VMs from the command line. All 19 GA commands fall under the single `workbench instances` subgroup.

> **Relationship to `gcloud notebooks`:** the legacy `gcloud notebooks` group manages the older User-managed and Managed notebooks. New work should use `gcloud workbench instances`. The two share the same backing API (`notebooks.googleapis.com`) and IAM roles (`roles/notebooks.*`).

## Quick reference — common workflows

### 1. Create a Workbench instance from a VM image
```bash
# One-time: enable the Notebooks API
gcloud services enable notebooks.googleapis.com

# Create from the managed VM image family (default project: cloud-notebooks-managed)
gcloud workbench instances create example-instance \
    --vm-image-project=cloud-notebooks-managed \
    --vm-image-family=workbench-instances \
    --machine-type=n1-standard-4 \
    --location=us-central1-b
```

### 2. Create an instance from a custom container
```bash
gcloud workbench instances create example-instance \
    --container-repository=gcr.io/deeplearning-platform-release/base-cpu \
    --container-tag=latest \
    --machine-type=n1-standard-4 \
    --location=us-central1-b
```

### 3. Start, stop, and reset an instance
```bash
# Stop a running instance to save cost
gcloud workbench instances stop example-instance --location=us-central1-a

# Start a stopped instance
gcloud workbench instances start example-instance --location=us-central1-a

# Reset (hard reboot)
gcloud workbench instances reset example-instance --location=us-central1-a
```

### 4. List, describe, and inspect valid configurations
```bash
# List instances in a location
gcloud workbench instances list --location=us-central1-a

# Describe one instance
gcloud workbench instances describe example-instance --location=us-central1-b

# Show valid machine/config options for a zone
gcloud workbench instances get-config --location=us-west1-a
```

### 5. Resize a disk and change the machine type
```bash
# Resize the boot disk to 200 GB (boot/data are mutually exclusive per call)
gcloud workbench instances resize-disk example-instance \
    --boot-disk-size=200 --location=us-central1-a

# Resize the data disk to 200 GB
gcloud workbench instances resize-disk example-instance \
    --data-disk-size=200 --location=us-central1-a

# Change the machine type
gcloud workbench instances update example-instance \
    --machine-type=n1-standard-8 --location=us-central1-a
```

### 6. Upgrade, manage IAM, and diagnose
```bash
# Check whether an instance can be upgraded, then upgrade it
gcloud workbench instances check-instance-upgradability example-instance \
    --location=us-central1-a
gcloud workbench instances upgrade example-instance --location=us-central1-a

# Grant Notebooks Admin to a user on a single instance
gcloud workbench instances add-iam-policy-binding example-instance \
    --member='user:analyst@example.com' \
    --role='roles/notebooks.admin' \
    --location=us-central1-a

# Capture diagnostic logs to a Cloud Storage bucket
gcloud workbench instances diagnose example-instance \
    --location=us-west1-b \
    --gcs-bucket=gs://example-bucket \
    --relative-path=logs
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `workbench instances` | [`instances.md`](instances.md) | 19 | Create and manage the full lifecycle of Vertex AI Workbench instances (create, lifecycle, resize, upgrade, restore/rollback, diagnose, IAM) |

See [`index.md`](index.md) for a one-line index of all 19 commands.

## Common flags & tips

- **`--location` is required and zonal.** Workbench instances live in a specific zone (e.g. `us-central1-a`), not just a region. Most commands need `--location`; you can also set it once with `gcloud config set notebooks/location us-central1-a`.
- **Image source is a choice on `create`.** Use either a VM image (`--vm-image-family` / `--vm-image-name` with `--vm-image-project`, default `cloud-notebooks-managed`) **or** a container (`--container-repository` with `--container-tag`) — not both.
- **`resize-disk` takes exactly one disk.** Pass `--boot-disk-size` *or* `--data-disk-size` (GB, up to 64000), one per invocation.
- **`--async` on long-running ops.** `create`, `delete`, `start`, `stop`, `reset`, `upgrade`, `resize-disk`, `restore`, `rollback`, and `diagnose` accept `--async` to return without waiting.
- **Shielded VM options** on `create`/`update`: `--shielded-secure-boot`, `--shielded-vtpm`, `--shielded-integrity-monitoring` (each takes a boolean, e.g. `=false`).
- **IAM is per-instance.** `add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy` operate on a single instance; common roles are `roles/notebooks.admin`, `roles/notebooks.editor`, and `roles/notebooks.viewer`. Granting an IAM role does **not** by itself grant JupyterLab access — JupyterLab access mode is fixed at creation.
- **Backup / recovery:** `restore` brings an instance back from a snapshot (`--snapshot` + `--snapshot-project`); `rollback` reverts to a saved snapshot (`--target-snapshot`).
- **Filtering and formatting** work on `list` (and `get-iam-policy`):
  ```bash
  # Only show instance names and states as a table
  gcloud workbench instances list --location=us-central1-a \
      --format='table(name, state, gceSetup.machineType)'

  # Filter by a label
  gcloud workbench instances list --location=us-central1-a \
      --filter='labels.team=ml'
  ```

## beta / alpha

`gcloud beta workbench` adds two command groups not present in GA:

- **`gcloud beta workbench executions`** — create, delete, describe, and list one-time notebook execution jobs.
- **`gcloud beta workbench schedules`** — create, delete, describe, list, pause, resume, and update scheduled notebook executions.

The `instances` subgroup is feature-equivalent between GA and beta. No `gcloud alpha workbench` surface is documented in the official reference.

## Official documentation

- [Vertex AI Workbench overview](https://cloud.google.com/vertex-ai/docs/workbench/overview) — product docs home; introduces the unified Workbench instances model.
- [Introduction to Workbench instances](https://cloud.google.com/vertex-ai/docs/workbench/instances/introduction) — the JupyterLab environment and access model.
- [Create an instance (console quickstart)](https://cloud.google.com/vertex-ai/docs/workbench/instances/create-console-quickstart) — first instance, required APIs and roles.
- [Manage instances](https://cloud.google.com/vertex-ai/docs/workbench/instances/manage) — lifecycle tasks: create, stop, start, upgrade, resize, backup.
- [IAM access control](https://cloud.google.com/vertex-ai/docs/workbench/instances/iam) — predefined roles and JupyterLab access mode configuration.
- [gcloud workbench CLI reference](https://cloud.google.com/sdk/gcloud/reference/workbench) — full GA command reference.
- [gcloud beta workbench CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/workbench) — beta reference, including `executions` and `schedules`.

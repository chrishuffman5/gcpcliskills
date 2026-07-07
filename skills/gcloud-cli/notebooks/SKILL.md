---
name: gcloud-notebooks
description: >-
  Vertex AI Workbench via gcloud (`gcloud notebooks`). Notebooks Command Group — environments, instances, locations, runtimes.
---

# gcloud notebooks — Vertex AI Workbench

## Overview
`gcloud notebooks` manages Vertex AI Workbench (formerly AI Platform Notebooks), a managed Jupyter
notebook environment for the data science workflow with integrated access to BigQuery, Cloud Storage,
and GPU acceleration. The command group manages two resource types: **instances** (managed Jupyter VMs
— the current Workbench instances) and **runtimes** (a legacy managed runtime; users should migrate to
instances). Reach for it to create, start/stop, upgrade, diagnose, and control IAM access on Workbench
notebook VMs from the command line.

## Quick reference — common workflows

### 1. Create a Workbench instance from a Deep Learning VM image
```bash
# Enable the API (one-time)
gcloud services enable notebooks.googleapis.com

# Create an instance from a Deep Learning VM image family (location is a zone)
gcloud notebooks instances create example-instance \
    --location=us-central1-a \
    --vm-image-project=deeplearning-platform-release \
    --vm-image-family=common-cpu \
    --machine-type=n1-standard-4

# Verify it is listed
gcloud notebooks instances list --location=us-central1-a
```

### 2. Stop, start, and health-check an instance
```bash
# Stop to save cost while idle
gcloud notebooks instances stop example-instance --location=us-central1-a

# Start it again
gcloud notebooks instances start example-instance --location=us-central1-a

# Check health and upgrade eligibility
gcloud notebooks instances get-health example-instance --location=us-central1-a
gcloud notebooks instances is-upgradeable example-instance --location=us-central1-a
```

### 3. Resize an instance and update labels
```bash
# Change machine type (stop the instance first)
gcloud notebooks instances update example-instance \
    --location=us-central1-a \
    --machine-type=n1-standard-8

# Update labels (update requires at least one of: --machine-type, --labels,
# --accelerator-core-count, --accelerator-type)
gcloud notebooks instances update example-instance \
    --location=us-central1-a \
    --labels=env=prod,team=data-science
```

### 4. Manage IAM access on an instance
```bash
# Grant a user the Notebooks Admin role on a specific instance
gcloud notebooks instances add-iam-policy-binding example-instance \
    --location=us-central1-a \
    --member='user:alice@example.com' \
    --role='roles/notebooks.admin'

# View the current IAM policy
gcloud notebooks instances get-iam-policy example-instance --location=us-central1-a

# Remove the binding
gcloud notebooks instances remove-iam-policy-binding example-instance \
    --location=us-central1-a \
    --member='user:alice@example.com' \
    --role='roles/notebooks.admin'
```

### 5. Diagnose a problematic instance
```bash
# Run diagnostics and write logs to a Cloud Storage bucket
gcloud notebooks instances diagnose example-instance \
    --location=us-central1-a \
    --gcs-bucket=gs://my-diagnostics-bucket \
    --relative-path=logs

# Add packet capture for network issues
gcloud notebooks instances diagnose example-instance \
    --location=us-central1-a \
    --gcs-bucket=gs://my-diagnostics-bucket \
    --enable-packet-capture
```

### 6. Migrate a legacy runtime to a Workbench instance
```bash
# List existing runtimes (runtime location is a region)
gcloud notebooks runtimes list --location=us-central1

# Migrate a runtime, rerunning its post-startup script on the new instance
gcloud notebooks runtimes migrate example-runtime \
    --location=us-central1 \
    --post-startup-script-option=POST_STARTUP_SCRIPT_OPTION_RERUN
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `notebooks environments` | [`environments.md`](environments.md) | 4 | Manage notebook environments (legacy container/VM-image definitions) |
| `notebooks instances` | [`instances.md`](instances.md) | 19 | Manage Workbench instances: create, lifecycle, IAM, diagnose, upgrade |
| `notebooks locations` | [`locations.md`](locations.md) | 1 | List locations available for a project |
| `notebooks runtimes` | [`runtimes.md`](runtimes.md) | 10 | Manage legacy managed runtimes (migrate to instances) |

See [`index.md`](index.md) for a one-line index of all 34 GA commands.

## Common flags & tips
- **`--location` is required and resource-specific.** Instances and environments use a **zone**
  (e.g. `us-central1-a`); runtimes use a **region** (e.g. `us-central1`). It can be set per-command,
  via a fully qualified resource name, or via the `notebooks/location` property.
- **Most mutating commands accept `--async`** (create, delete, start, stop, reset, update, upgrade,
  migrate, rollback, diagnose) to return immediately without waiting for the long-running operation.
- **`instances create` image source** is one of: a VM image (`--vm-image-project` +
  `--vm-image-family` or `--vm-image-name`, defaulting to `deeplearning-platform-release`/`common-cpu`),
  a container (`--container-repository` + `--container-tag`), or an environment (`--environment` +
  `--environment-location`).
- **`instances update` is constrained** — you must pass at least one of `--machine-type`, `--labels`,
  `--accelerator-core-count`, or `--accelerator-type`.
- **Diagnostics** (`instances diagnose` / `runtimes diagnose`) require `--gcs-bucket=gs://...`; the
  bucket's writer needs `storage.buckets.writer`. Add `--enable-packet-capture`,
  `--enable-copy-home-files`, or `--enable-repair` as needed.
- **Filtering / formatting** — `list`, `get-iam-policy` and similar support standard flags such as
  `--filter`, `--limit`, `--sort-by`, and `--uri`. Examples:
  ```bash
  gcloud notebooks instances list --location=us-central1-a \
      --filter="state=ACTIVE" --format="table(name, machineType, state)"
  gcloud notebooks instances list --location=us-central1-a --uri
  ```

## beta / alpha
Both `gcloud beta notebooks` and `gcloud alpha notebooks` exist but are **deprecated** — their
reference pages state "This command is deprecated. Please use `gcloud notebooks` instead." Neither
surfaces additional commands beyond the GA group. **Use the GA `gcloud notebooks` exclusively.**

## Official documentation
- [Vertex AI Workbench — Introduction](https://cloud.google.com/vertex-ai/docs/workbench/introduction) — product overview and capabilities (docs home).
- [Create a Workbench instance (Console quickstart)](https://cloud.google.com/vertex-ai/docs/workbench/instances/create-console-quickstart) — getting-started quickstart.
- [Manage Workbench instances](https://cloud.google.com/vertex-ai/docs/workbench/instances/manage) — start, stop, upgrade, and migrate instances.
- [IAM access control for Workbench instances](https://cloud.google.com/vertex-ai/docs/workbench/instances/iam) — roles and access modes.
- [gcloud notebooks CLI reference](https://cloud.google.com/sdk/gcloud/reference/notebooks) — full command/flag reference.
- [gcloud notebooks instances create](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/create) — instance creation flags and examples.
- [gcloud notebooks runtimes create](https://cloud.google.com/sdk/gcloud/reference/notebooks/runtimes/create) — legacy runtime creation flags and examples.

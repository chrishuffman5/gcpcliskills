---
name: gcloud-lustre
description: >-
  Managed Lustre via gcloud (`gcloud lustre`). Manage Lustre resources — instances, operations.
---

# gcloud lustre — Managed Lustre

## Overview
Google Cloud Managed Lustre is a fully managed, high-performance parallel file system (built with DDN) for AI/ML and HPC workloads that need very high throughput and POSIX-compliant shared storage. Use `gcloud lustre` to create and manage zonal Lustre instances, import/export data between Cloud Storage and the file system, and track the long-running operations those actions produce. Instances are zonal and attach to Compute Engine VMs and GKE clusters over a VPC network.

## Quick reference — common workflows

### 1. Enable the API (one-time)
```bash
gcloud services enable lustre.googleapis.com --project=my-project
```

### 2. Create an instance
```bash
# 18 TiB instance at the 1000 MBps/TiB performance tier
gcloud lustre instances create my-instance \
    --location=us-central1-a \
    --capacity-gib=18000 \
    --filesystem=lustrefs \
    --network=projects/my-project/global/networks/default \
    --per-unit-storage-throughput=1000

# Customer-managed encryption + labels, returning immediately
gcloud lustre instances create my-instance \
    --location=us-central1-a \
    --capacity-gib=18000 \
    --filesystem=lustrefs \
    --network=projects/my-project/global/networks/default \
    --per-unit-storage-throughput=1000 \
    --kms-key=projects/my-project/locations/us-central1/keyRings/my-ring/cryptoKeys/my-key \
    --labels=env=prod,team=ml \
    --async
```
Required: `--capacity-gib`, `--filesystem`, `--network`, `--per-unit-storage-throughput`. Valid throughput tiers are 125, 250, 500, 1000 (MBps/TiB); capacity ranges 18000–7632000 GiB depending on tier.

### 3. List and inspect instances
```bash
gcloud lustre instances list --location=us-central1-a
gcloud lustre instances describe my-instance --location=us-central1-a
```

### 4. Update an instance (resize or edit description)
```bash
# Scale capacity up
gcloud lustre instances update my-instance \
    --location=us-central1-a \
    --capacity-gib=36000

# Change description only
gcloud lustre instances update my-instance \
    --location=us-central1-a \
    --description="Production AI training filesystem"
```
Updatable: `--capacity-gib`, `--description`, `--per-unit-storage-throughput`, `--placement-policy`, labels (`--update-labels` / `--remove-labels` / `--clear-labels`), and access-rule / squash settings.

### 5. Import data from Cloud Storage
```bash
gcloud lustre instances import-data my-instance \
    --location=us-central1-a \
    --gcs-path-uri=gs://my-training-data/ \
    --lustre-path=/
```
`--lustre-path` defaults to `/`; any non-default target path must already exist on the file system.

### 6. Export data to Cloud Storage
```bash
gcloud lustre instances export-data my-instance \
    --location=us-central1-a \
    --gcs-path-uri=gs://my-output-bucket/ \
    --lustre-path=/results/
```

### 7. Track and manage long-running operations
```bash
gcloud lustre operations list --location=us-central1-a
gcloud lustre operations describe OPERATION_ID --location=us-central1-a
gcloud lustre operations wait OPERATION_ID --location=us-central1-a
gcloud lustre operations cancel OPERATION_ID --location=us-central1-a
```
Add `--async` to `create` / `delete` / `update` / `import-data` / `export-data` to return the operation immediately, then poll with `operations wait` or `operations describe`.

### 8. Delete an instance
```bash
gcloud lustre instances delete my-instance --location=us-central1-a
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `lustre instances` | [`instances.md`](instances.md) | 7 | manage Instance resources (create, delete, describe, list, update, import-data, export-data) |
| `lustre operations` | [`operations.md`](operations.md) | 5 | manage Operation resources (cancel, delete, describe, list, wait) |

See [`index.md`](index.md) for a one-line index of all 12 commands.

## Common flags & tips
- **Location is zonal and required.** Every command takes `--location=ZONE` (e.g. `us-central1-a`), not a region. `instances list` and `operations list` require `--location`.
- **Instance/operation identifiers** can be a short ID (with `--location`) or a fully qualified name (`projects/PROJECT/locations/ZONE/instances/INSTANCE`).
- **Network** must be supplied at create time as a full path: `projects/PROJECT/locations.../global/networks/NETWORK` (e.g. `projects/my-project/global/networks/default`).
- **Encryption:** omit `--kms-key` for Google-managed keys; supply a CMEK key (in the instance's region) to control your own.
- **`--filesystem`** must be 8 characters or fewer, letters and numbers only.
- **Filtering / formatting:**
  - `gcloud lustre instances list --location=us-central1-a --filter="capacityGib>18000"`
  - `gcloud lustre instances list --location=us-central1-a --format="table(name,capacityGib,perUnitStorageThroughput)"`
  - `gcloud lustre operations list --location=us-central1-a --filter="done=false"`
- **`--request-id`** (a UUID) makes create/delete/update/import/export idempotent across retries.

## Official documentation
- Managed Lustre documentation home: https://cloud.google.com/managed-lustre/docs — all guides and references.
- Product overview: https://cloud.google.com/managed-lustre/docs/overview — architecture, performance specs, key features.
- Create an instance: https://cloud.google.com/managed-lustre/docs/create-instance — creation steps and performance-tier / capacity details.
- Transfer data: https://cloud.google.com/managed-lustre/docs/transfer-data — import/export between Cloud Storage and Managed Lustre.
- Access control: https://cloud.google.com/managed-lustre/docs/access-control — IAM roles (`roles/lustre.admin`, `roles/lustre.viewer`) and permissions.
- Enable the API: https://cloud.google.com/managed-lustre/docs/enable-api — enabling `lustre.googleapis.com` before first use.
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/lustre — all `gcloud lustre` commands (GA).

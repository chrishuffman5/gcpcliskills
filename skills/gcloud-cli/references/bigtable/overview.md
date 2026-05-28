# gcloud bigtable — Cloud Bigtable

## Overview

`gcloud bigtable` manages Cloud Bigtable instances, clusters, tables, app profiles, and backups — Google Cloud's fully managed, scalable NoSQL database for large analytical and operational workloads (time-series, IoT, ad-tech, ML feature stores). Reach for it to provision and scale instances/clusters, define table schemas and column-family garbage-collection policies, configure traffic routing with app profiles, and create/restore backups. The CLI drives the admin plane; the data plane is served separately (use the `cbt` tool or client libraries to read/write rows).

## Quick reference — common workflows

### Enable the APIs
```bash
# Admin/management plane and data plane
gcloud services enable bigtableadmin.googleapis.com
gcloud services enable bigtable.googleapis.com
```

### Create an instance (single or multi-cluster)
```bash
# Single-cluster production instance (--cluster-config is recommended)
gcloud bigtable instances create my-instance \
    --display-name="My Instance" \
    --cluster-config=id=my-cluster,zone=us-east1-c,nodes=3

# Replicated, multi-cluster instance
gcloud bigtable instances create my-replicated-instance \
    --display-name="Replicated Instance" \
    --cluster-config=id=cluster-us,zone=us-east1-c,nodes=3 \
    --cluster-config=id=cluster-eu,zone=europe-west1-b,nodes=3

gcloud bigtable instances describe my-instance
gcloud bigtable instances list
```

### Scale a cluster (manual or autoscaling)
```bash
# Manual resize
gcloud bigtable clusters update my-cluster \
    --instance=my-instance --num-nodes=10

# Enable autoscaling (all four flags are required together)
gcloud bigtable clusters update my-cluster \
    --instance=my-instance \
    --autoscaling-min-nodes=3 \
    --autoscaling-max-nodes=10 \
    --autoscaling-cpu-target=60 \
    --autoscaling-storage-target=2560

# Add another cluster to an existing instance
gcloud bigtable clusters create my-new-cluster \
    --instance=my-instance --zone=us-west1-b --num-nodes=3
```

### Manage tables and column families
```bash
# Create a table with two column families and GC policies
gcloud bigtable instances tables create my-table \
    --instance=my-instance \
    --column-families="cf1:maxage=7d,cf2:maxversions=3"

# Create with deletion protection and a change stream
gcloud bigtable instances tables create my-safe-table \
    --instance=my-instance --column-families="cf1" \
    --deletion-protection \
    --change-stream-retention-period=7d

gcloud bigtable instances tables list --instances=my-instance
gcloud bigtable instances tables describe my-table --instance=my-instance

# Turn on the default automated backup policy; undelete a soft-deleted table
gcloud bigtable instances tables update my-table \
    --instance=my-instance --enable-automated-backup
gcloud bigtable instances tables undelete my-table --instance=my-instance
```

### Back up and restore
```bash
# Create a backup that expires in 2 weeks
gcloud bigtable backups create my-backup \
    --instance=my-instance --cluster=my-cluster \
    --table=my-table --retention-period=2w

gcloud bigtable backups list --instance=my-instance

# Restore the backup to a new table
gcloud bigtable instances tables restore \
    --source-instance=my-instance --source-cluster=my-cluster \
    --source=my-backup \
    --destination-instance=my-instance --destination=my-restored-table

# Extend retention; copy a backup to another cluster/project
gcloud bigtable backups update my-backup \
    --instance=my-instance --cluster=my-cluster --retention-period=30d
gcloud bigtable backups copy \
    --source-instance=my-instance --source-cluster=my-cluster \
    --source-backup=my-backup \
    --destination-instance=my-other-instance \
    --destination-cluster=my-other-cluster \
    --destination-backup=my-backup-copy --retention-period=14d
```

### Configure app profiles for traffic routing
```bash
# Multi-cluster routing (uses all healthy clusters)
gcloud bigtable app-profiles create my-read-profile \
    --instance=my-instance --route-any \
    --description="Read-heavy workload profile"

# Single-cluster routing with transactional writes
gcloud bigtable app-profiles create my-write-profile \
    --instance=my-instance --route-to=my-cluster --transactional-writes

# Data Boost (serverless reads billed to the host project)
gcloud bigtable app-profiles create my-analytics-profile \
    --instance=my-instance --data-boost \
    --data-boost-compute-billing-owner=HOST_PAYS

gcloud bigtable app-profiles update my-read-profile \
    --instance=my-instance --route-any --priority=PRIORITY_MEDIUM
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `bigtable app-profiles` | [`app-profiles.md`](app-profiles.md) | 5 | manage Cloud Bigtable app profiles |
| `bigtable authorized-views` | [`authorized-views.md`](authorized-views.md) | 9 | manage Cloud Bigtable Authorized Views |
| `bigtable backups` | [`backups.md`](backups.md) | 10 | manage Cloud Bigtable backups |
| `bigtable clusters` | [`clusters.md`](clusters.md) | 5 | manage Cloud Bigtable clusters |
| `bigtable hot-tablets` | [`hot-tablets.md`](hot-tablets.md) | 1 | list hot tablets in a cluster |
| `bigtable instances` | [`instances.md`](instances.md) | 21 | manage instances (includes `instances tables`) |
| `bigtable logical-views` | [`logical-views.md`](logical-views.md) | 5 | manage Bigtable logical views |
| `bigtable materialized-views` | [`materialized-views.md`](materialized-views.md) | 5 | manage Bigtable materialized views |
| `bigtable operations` | [`operations.md`](operations.md) | 2 | describe/list long-running operations |
| `bigtable schema-bundles` | [`schema-bundles.md`](schema-bundles.md) | 9 | manage Bigtable schema bundles |
| `bigtable tables` | [`tables.md`](tables.md) | 11 | top-level alias of `instances tables` |

See [`index.md`](index.md) for a one-line index of all 83 GA commands.

## Common flags & tips

- **Instance vs. cluster.** A Bigtable *instance* is the container; *clusters* hold the serving nodes in a zone. Most cluster, table, backup, and app-profile commands require `--instance=INSTANCE`; backup commands also require `--cluster=CLUSTER`.
- **Always prefer `--cluster-config`** on `instances create` (key-value dict: `id`, `zone`, `nodes`, `kms-key`, autoscaling keys). The single-cluster flags `--cluster`, `--cluster-zone`, `--cluster-num-nodes` are deprecated; `--instance-type` is deprecated (all instances are PRODUCTION).
- **Two ways to address tables.** `gcloud bigtable instances tables ...` and the top-level `gcloud bigtable tables ...` expose the same commands. `tables list` uses `--instances=` (plural, repeatable); other table commands use `--instance=`.
- **Autoscaling on `clusters update`** requires all four flags together: `--autoscaling-min-nodes`, `--autoscaling-max-nodes`, `--autoscaling-cpu-target` (10–80), `--autoscaling-storage-target` (2560–5120 SSD / 8192–16384 HDD). Use `--num-nodes` with `--disable-autoscaling` to return to manual scaling.
- **Column families & GC** are set via `--column-families` as a quoted, comma-separated list, e.g. `"cf1:maxage=5d&&maxversions=2,cf2:maxage=10d||maxversions=5"`. Durations accept `d/h/m/s`.
- **Backup timing.** `--retention-period` (relative, e.g. `2w`, `30d`) or `--expiration-date` (absolute timestamp). Hot backups: `--backup-type=HOT` plus `--hot-to-standard-time`.
- **Filtering & formatting** (standard gcloud flags available on `list`/`describe`):
  ```bash
  gcloud bigtable instances list --filter="displayName:prod" \
      --format="table(name, displayName, state)"
  gcloud bigtable clusters list --instances=my-instance \
      --format="value(name, defaultStorageType)"
  ```
- **Diagnose load.** `gcloud bigtable hot-tablets list my-cluster --instance=my-instance` surfaces hot tablets; track admin work with `gcloud bigtable operations list` / `operations describe`.
- **IAM** can be applied at instance, table, and backup scope via `add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy` on each group. Common roles: `roles/bigtable.admin`, `roles/bigtable.user`, `roles/bigtable.reader`, `roles/bigtable.viewer`.

## beta / alpha

- `gcloud beta bigtable` and `gcloud alpha bigtable` mirror the GA surface and add preview features.
- **`gcloud beta bigtable memory-layers`** exists only under beta (manages Cloud Bigtable memory layers); not present in GA.
- `authorized-views`, `logical-views`, `materialized-views`, and `schema-bundles` appear in both GA and beta; beta variants may surface options not yet graduated to GA.
- Prefer GA for production; reach for beta/alpha only for features explicitly documented as preview.

## Official documentation

- Cloud Bigtable documentation home: https://cloud.google.com/bigtable/docs — product overview and resource hub.
- Bigtable overview: https://cloud.google.com/bigtable/docs/overview — architecture, storage model, scalability.
- Quickstart with the cbt CLI: https://cloud.google.com/bigtable/docs/quickstart-cbt — create an instance, write and read data.
- Managing backups: https://cloud.google.com/bigtable/docs/managing-backups — create, restore, copy, delete backups.
- App profiles: https://cloud.google.com/bigtable/docs/app-profiles — routing policies, Data Boost, request priority.
- Access control (IAM): https://cloud.google.com/bigtable/docs/access-control — predefined roles and resource-level permissions.
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/bigtable — all GA subcommand groups.

# gcloud alloydb — AlloyDB for PostgreSQL

## Overview

AlloyDB for PostgreSQL is a fully managed, PostgreSQL-compatible database for demanding transactional, analytical, and AI workloads. The `gcloud alloydb` command group manages the full resource hierarchy: clusters (the top-level container holding configuration, backups, and connectivity), instances (the compute serving a cluster — `PRIMARY` for read/write, `READ_POOL` for scaled-out reads), backups, database users, and long-running operations. Reach for it to provision clusters and instances, configure high availability and automated/continuous backups, set up cross-region disaster recovery, and manage database users from the CLI.

## Quick reference — common workflows

### 1. Create a cluster and primary instance

```bash
# Enable the API (one-time per project)
gcloud services enable alloydb.googleapis.com

# Create the cluster (private IP via a VPC network)
gcloud alloydb clusters create my-cluster \
    --region=us-central1 \
    --password=my-initial-password \
    --network=default

# Create the primary instance (4 vCPUs, regional high availability)
gcloud alloydb instances create my-primary \
    --cluster=my-cluster \
    --region=us-central1 \
    --instance-type=PRIMARY \
    --cpu-count=4 \
    --availability-type=REGIONAL

# Confirm the cluster and instance are ready
gcloud alloydb clusters describe my-cluster --region=us-central1
gcloud alloydb instances list --cluster=my-cluster --region=us-central1
```

### 2. Add a read pool for horizontal read scaling

```bash
gcloud alloydb instances create my-read-pool \
    --cluster=my-cluster \
    --region=us-central1 \
    --instance-type=READ_POOL \
    --read-pool-node-count=2 \
    --cpu-count=4 \
    --availability-type=REGIONAL

# Scale the read pool out later
gcloud alloydb instances update my-read-pool \
    --cluster=my-cluster \
    --region=us-central1 \
    --read-pool-node-count=4
```

### 3. Take an on-demand backup and restore

```bash
# On-demand backup
gcloud alloydb backups create my-backup \
    --cluster=my-cluster \
    --region=us-central1

gcloud alloydb backups list --region=us-central1

# Restore from the backup into a new cluster
gcloud alloydb clusters restore my-restored-cluster \
    --region=us-central1 \
    --backup=my-backup

# Or restore to a point in time from a source cluster (requires continuous backup)
gcloud alloydb clusters restore my-pitr-cluster \
    --region=us-central1 \
    --source-cluster=my-cluster \
    --point-in-time=2025-05-01T12:00:00.000Z
```

### 4. Configure automated backups on a cluster

```bash
gcloud alloydb clusters update my-cluster \
    --region=us-central1 \
    --automated-backup-days-of-week=MONDAY,WEDNESDAY,FRIDAY \
    --automated-backup-start-times=02:00 \
    --automated-backup-window=1h \
    --automated-backup-retention-count=14
```

### 5. Manage database users

```bash
# Built-in (password) user
gcloud alloydb users create app-user \
    --cluster=my-cluster \
    --region=us-central1 \
    --type=BUILT_IN \
    --password=my-app-password

# IAM-based user (no password)
gcloud alloydb users create iam-user@example.com \
    --cluster=my-cluster \
    --region=us-central1 \
    --type=IAM_BASED

# Grant database roles, reset a password, and list users
gcloud alloydb users set-roles app-user \
    --cluster=my-cluster --region=us-central1 \
    --db-roles=pg_read_all_data,pg_write_all_data
gcloud alloydb users set-password app-user \
    --cluster=my-cluster --region=us-central1 --password=new-password
gcloud alloydb users list --cluster=my-cluster --region=us-central1
```

### 6. Cross-region secondary cluster (disaster recovery)

```bash
# Secondary cluster pointing at the primary
gcloud alloydb clusters create-secondary my-secondary-cluster \
    --region=us-east1 \
    --primary-cluster=projects/my-project/locations/us-central1/clusters/my-cluster

# Secondary instance inside the secondary cluster
gcloud alloydb instances create-secondary my-secondary-instance \
    --cluster=my-secondary-cluster \
    --region=us-east1

# Promote the secondary to a standalone primary (unplanned failover)
gcloud alloydb clusters promote my-secondary-cluster --region=us-east1

# Or perform a planned, zero-data-loss switchover
gcloud alloydb clusters switchover my-secondary-cluster --region=us-east1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `alloydb backups` | [`backups.md`](backups.md) | 4 | Create, describe, list, and delete on-demand and cross-region backups |
| `alloydb clusters` | [`clusters.md`](clusters.md) | 13 | Create, restore, update, upgrade, export/import, and run DR operations on clusters |
| `alloydb instances` | [`instances.md`](instances.md) | 9 | Create primary/read-pool/secondary instances; failover, restart, update |
| `alloydb operations` | [`operations.md`](operations.md) | 4 | Describe, list, cancel, and delete long-running operations |
| `alloydb users` | [`users.md`](users.md) | 6 | Manage built-in and IAM database users, roles, passwords, and superuser |

See [`index.md`](index.md) for a one-line index of all 36 commands.

## Common flags & tips

- **`--region` is required on almost every command** (clusters, instances, backups, users, operations). Instance and user commands also require `--cluster`. List commands default `--region` to `-` (all regions).
- **`--instance-type`** must be `PRIMARY` or `READ_POOL`; pair `READ_POOL` with `--read-pool-node-count`. Use `--availability-type=REGIONAL` for production HA (`ZONAL` has no automatic cross-zone failover).
- **Sizing:** set `--cpu-count` (one of 1, 2, 4, 8, 16, 32, 64, 96, 128, …) or `--machine-type` directly. If both are set they must agree.
- **`--database-version` / `clusters upgrade --version`** accept `POSTGRES_14`, `POSTGRES_15`, `POSTGRES_16`, `POSTGRES_17`.
- **Backups:** on `clusters create`, configure continuous backup with `--enable-continuous-backup --continuous-backup-recovery-window-days=N`, or automated backups with the `--automated-backup-*` flags; CMEK via the `--kms-key`/`--continuous-backup-encryption-key` flag groups.
- **`--async`** returns immediately and prints an operation you can track with `gcloud alloydb operations describe OPERATION --region=...`.
- **Async note:** `instances update` is async by default — pass `--no-async` to wait for completion.
- **Connectivity:** clusters use private IP via `--network`; use `--enable-private-service-connect` for PSC, or per-instance `--assign-inbound-public-ip=ASSIGN_IPV4` with `--authorized-external-networks` for public IP.
- **Filtering/formatting** works on every list command, e.g.:
  ```bash
  gcloud alloydb instances list --cluster=my-cluster --region=us-central1 \
      --filter="instanceType=PRIMARY" --format="table(name, state, machineType)"
  gcloud alloydb backups list --region=us-central1 \
      --format="table(name, size_bytes)"
  ```

## beta / alpha

- `gcloud beta alloydb` exposes the same five command groups as GA plus a standalone `gcloud beta alloydb connect` command that launches the AlloyDB Auth Proxy to connect directly to an instance — this command is not present in the GA surface.
- `gcloud alpha alloydb` also exists; experimental features may appear there before graduating to beta/GA.
- All 36 GA commands documented here are fully available without the beta/alpha prefix.

## Official documentation

- [AlloyDB for PostgreSQL documentation home](https://cloud.google.com/alloydb/docs) — product docs landing page.
- [AlloyDB overview](https://cloud.google.com/alloydb/docs/overview) — architecture, compute/storage separation, high availability, AlloyDB AI, and CMEK.
- [Quickstart: create and connect](https://cloud.google.com/alloydb/docs/quickstart/create-and-connect) — create a cluster and connect via AlloyDB Studio.
- [Create a cluster and its primary instance](https://cloud.google.com/alloydb/docs/cluster-create) — how-to for cluster/instance creation via gcloud or console.
- [Manage database users](https://cloud.google.com/alloydb/docs/database-users/about) — built-in vs. IAM database users.
- [Cross-region replication](https://cloud.google.com/alloydb/docs/cross-region-replication/about-cross-region-replication) — secondary clusters, switchover, and promote for DR.
- [gcloud alloydb CLI reference](https://cloud.google.com/sdk/gcloud/reference/alloydb) — full GA command reference.
- [gcloud beta alloydb reference](https://cloud.google.com/sdk/gcloud/reference/beta/alloydb) — beta surface, including the `connect` command.

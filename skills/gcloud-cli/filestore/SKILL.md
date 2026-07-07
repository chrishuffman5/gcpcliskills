---
name: gcloud-filestore
description: >-
  Filestore via gcloud (`gcloud filestore`). Create and manipulate Filestore resources — backups, instances, locations, operations, regions, zones.
---

# gcloud filestore — Filestore

## Overview
Filestore provides fully managed NFS file servers for Compute Engine VMs, GKE clusters, and on-premises clients. Use `gcloud filestore` to create and manage instances across service tiers (Basic HDD/SSD, Zonal, Regional, Enterprise), protect data with backups and snapshots, configure replication, and inspect long-running operations. Reach for it when a workload needs shared POSIX file storage rather than block (Persistent Disk) or object (Cloud Storage) storage.

## Quick reference — common workflows

### 1. Enable the API, create a Basic HDD instance, inspect it
```bash
# One-time per project
gcloud services enable file.googleapis.com

# Create a Basic HDD instance with a 1TB file share on the default network
gcloud filestore instances create my-instance \
    --zone=us-central1-c --tier=BASIC_HDD \
    --file-share=name=my_vol,capacity=1TB --network=name=default

# List and inspect
gcloud filestore instances list --limit=5 --sort-by=~name
gcloud filestore instances describe my-instance --location=us-central1-c
```

### 2. Create a Regional (high-availability) instance
```bash
gcloud filestore instances create my-regional \
    --region=us-central1 --tier=REGIONAL \
    --file-share=name=data,capacity=2TB \
    --network=name=default,connect-mode=PRIVATE_SERVICE_ACCESS
```

### 3. Take a snapshot and revert to it
```bash
# Snapshot an instance (use --instance-region for Regional, --instance-location for zonal)
gcloud filestore instances snapshots create my-snapshot \
    --instance=my-instance --instance-region=us-central1 \
    --description="Pre-upgrade snapshot"

# List snapshots, then revert the instance to one
gcloud filestore instances snapshots list \
    --instance=my-instance --instance-region=us-central1 --limit=5

gcloud filestore instances revert my-instance \
    --target-snapshot=my-snapshot --location=us-central1
```

### 4. Back up a file share and restore from it
```bash
# Create a backup of a file share (instance lives in a zone, backup in a region)
gcloud filestore backups create my-backup \
    --instance=my-instance --file-share=my_vol \
    --instance-zone=us-central1-c --region=us-central1 \
    --description="Daily backup"

gcloud filestore backups list --region=us-central1

# Restore into an instance (target tier must be compatible)
gcloud filestore instances restore my-instance \
    --zone=us-central1-c --file-share=my_vol \
    --source-backup=my-backup --source-backup-region=us-central1
```

### 5. Scale capacity, update labels, set IOPS
```bash
# Grow the file share to 2TB
gcloud filestore instances update my-instance \
    --zone=us-central1-c --file-share=name=my_vol,capacity=2TB

# Add and remove labels
gcloud filestore instances update my-instance \
    --zone=us-central1-c --update-labels=env=prod --remove-labels=old-key

# Configure provisioned IOPS (Zonal/Regional tiers)
gcloud filestore instances update my-instance \
    --zone=us-central1-c --performance=max-iops-per-tb=17000
```

### 6. Delete an instance (with its snapshots) and a backup
```bash
gcloud filestore instances delete my-instance --zone=us-central1-c --force
gcloud filestore backups delete my-backup --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|---------------|----------|-------------|
| `filestore instances` | [instances.md](instances.md) | 15 | Manage Filestore instances (create, delete, describe, list, restore, revert, update, pause/promote/resume-replica) plus nested `instances snapshots` (create, delete, describe, list, update) |
| `filestore backups` | [backups.md](backups.md) | 5 | Create and manage on-demand backups of instance file shares |
| `filestore locations` | [locations.md](locations.md) | 2 | List and describe locations where Filestore is available |
| `filestore operations` | [operations.md](operations.md) | 3 | Read and manipulate long-running Filestore operations (cancel, describe, list) |
| `filestore regions` | [regions.md](regions.md) | 1 | List regions where Filestore is available |
| `filestore zones` | [zones.md](zones.md) | 1 | List zones where Filestore is available |

See [index.md](index.md) for a one-line index of all 27 GA commands.

## Common flags & tips
- **Location targeting is per-tier.** Basic and Zonal/High-Scale instances live in a **zone** (`--zone=us-central1-c`); Regional and Enterprise instances live in a **region** (`--region=us-central1`). Most commands also accept the generic `--location`; `instances describe`/`revert` use `--location` for both kinds. Properties `filestore/zone`, `filestore/region`, and `filestore/location` set defaults.
- **`--file-share`** requires both `name` and `capacity` (e.g. `--file-share=name=my_vol,capacity=1TB`). If no capacity unit is given, GB is assumed. Acceptable capacity ranges and increments vary by `--tier`.
- **`--tier`** defaults to `BASIC_HDD`. Options include `basic-hdd`, `basic-ssd`, `zonal`, `regional`, `enterprise`, plus aliases `high-scale-ssd` (→ZONAL), `premium`/`standard` (→BASIC_SSD/BASIC_HDD).
- **`--network`** sets `name` and optional `connect-mode` (`DIRECT_PEERING`, `PRIVATE_SERVICE_ACCESS`, `PRIVATE_SERVICE_CONNECT`), `reserved-ip-range`, and `address-mode`.
- **`--performance`** takes `max-iops` (multiple of 1000) or `max-iops-per-tb`; supported on Zonal/Regional tiers.
- **NFS export options** can only be set via a JSON/YAML config passed with `--flags-file` (not inline on `--file-share`).
- **Replication:** `instances create --source-instance=...` builds a replica; manage standbys with `pause-replica`, `resume-replica`, and `promote-replica` (the last accepts `--peer-instance`).
- **`--async`** on mutating commands returns immediately; poll progress with `gcloud filestore operations describe`/`list`.
- **Encryption:** `instances create` and `backups create` accept `--kms-key` (CMEK).
- Useful read patterns:
  ```bash
  gcloud filestore instances list --filter="tier=REGIONAL" \
      --format="table(name,tier,state,fileShares[0].capacityGb)"
  gcloud filestore backups list --region=us-central1 --format="value(name)"
  ```

## beta / alpha
The reference notes: *"These variants are also available: gcloud alpha filestore, gcloud beta filestore."*
- **`gcloud beta filestore`** mirrors the GA command groups and may expose pre-GA flag variants before they graduate.
- **`gcloud alpha filestore`** is used for testing pre-GA behavior, including standalone snapshot management surfaces in addition to the GA `gcloud filestore instances snapshots` nesting.

## Official documentation
- [Filestore product overview](https://cloud.google.com/filestore/docs/overview) — architecture, use cases, and feature summary (product docs home).
- [Quickstart with gcloud](https://cloud.google.com/filestore/docs/quickstart-gcloud) — create an instance, mount it on a VM, and run file I/O.
- [Create instances](https://cloud.google.com/filestore/docs/creating-instances) — full how-to covering all tiers, capacity, and networking.
- [Service tiers](https://cloud.google.com/filestore/docs/instance-tiers) — Basic HDD/SSD, Zonal, Regional, Enterprise differences.
- [Backups and restore](https://cloud.google.com/filestore/docs/backup-restore) — on-demand backups and disaster recovery.
- [Snapshots](https://cloud.google.com/filestore/docs/snapshots) — what they are, limitations, and best practices.
- [Access control (IAM)](https://cloud.google.com/filestore/docs/access-control) — roles for instances, backups, and snapshots.
- [Performance](https://cloud.google.com/filestore/docs/performance) — IOPS configuration and capacity-based limits.
- [gcloud filestore CLI reference](https://cloud.google.com/sdk/gcloud/reference/filestore) — all command groups and flags.

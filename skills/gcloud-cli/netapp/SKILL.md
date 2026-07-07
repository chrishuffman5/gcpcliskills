---
name: gcloud-netapp
description: >-
  Google Cloud NetApp Volumes via gcloud (`gcloud netapp`). Create and manipulate Cloud NetApp Files resources — active-directories, backup-policies, backup-vaults, host-groups, kms-configs, locations, operations, storage-pools.
---

# gcloud netapp — Google Cloud NetApp Volumes

## Overview

`gcloud netapp` manages **Google Cloud NetApp Volumes**, a fully managed, cloud-based file
storage service for enterprise workloads. It provisions **storage pools** (capacity containers
with a service level) that in turn hold **volumes** served over NFS (v3/v4.1), SMB, and block
(iSCSI) protocols. Reach for it when you need managed NFS/SMB shares with snapshots, scheduled
backups, cross-region replication, quota rules, and CMEK/Active-Directory integration without
running your own file servers. NetApp Volumes resources are **regional** — almost every command
needs `--location=REGION`.

## Quick reference — common workflows

### 1. Enable the API and create a Standard storage pool

```bash
gcloud services enable netapp.googleapis.com

# Standard service level, 2 TiB (capacity is GiB unless a unit is given), default VPC
gcloud netapp storage-pools create my-pool \
  --location=us-central1 \
  --service-level=standard \
  --capacity=2048 \
  --network=name=default

gcloud netapp storage-pools describe my-pool --location=us-central1
```

### 2. Create a Flex (Unified) storage pool with auto-tiering

```bash
gcloud netapp storage-pools create my-flex-pool \
  --location=us-central1 \
  --service-level=flex \
  --capacity=2048 \
  --network=name=default \
  --type=unified \
  --allow-auto-tiering=true

gcloud netapp storage-pools list --location=us-central1
```

### 3. Create an NFS volume in a pool

```bash
# Prerequisite: storage pool my-pool must already exist
gcloud netapp volumes create my-nfs-vol \
  --location=us-central1 \
  --storage-pool=my-pool \
  --capacity=1024 \
  --protocols=nfsv3 \
  --share-name=nfs-share1 \
  --unix-permissions=0755

gcloud netapp volumes describe my-nfs-vol --location=us-central1
```

### 4. Take an on-demand snapshot and revert

```bash
gcloud netapp volumes snapshots create snap-20260527 \
  --location=us-central1 --volume=my-nfs-vol

gcloud netapp volumes snapshots list \
  --location=us-central1 --volume=my-nfs-vol

# Roll the volume back to that snapshot
gcloud netapp volumes revert my-nfs-vol \
  --location=us-central1 --snapshot=snap-20260527
```

### 5. Cross-region volume replication

```bash
# Create replication (source vol -> a pool/volume in another region)
gcloud netapp volumes replications create my-replication \
  --location=us-central1 \
  --volume=my-nfs-vol \
  --replication-schedule=EVERY_10_MINUTES \
  --destination-volume-parameters=storage_pool=dest-pool,volume_id=dest-vol,share_name=dest-share

gcloud netapp volumes replications describe my-replication \
  --location=us-central1 --volume=my-nfs-vol

# On-demand sync, then stop / reverse (failover) as needed
gcloud netapp volumes replications sync my-replication \
  --location=us-central1 --volume=my-nfs-vol
gcloud netapp volumes replications stop my-replication \
  --location=us-central1 --volume=my-nfs-vol
gcloud netapp volumes replications reverse my-replication \
  --location=us-central1 --volume=my-nfs-vol
```

### 6. Scheduled backups for a volume

```bash
# A vault holds backups; a policy defines the schedule/retention
gcloud netapp backup-vaults create my-vault --location=us-central1

gcloud netapp backup-policies create my-policy \
  --location=us-central1 --enabled=true \
  --daily-backup-limit=7 --weekly-backup-limit=4 --monthly-backup-limit=3

# Attach vault + policy to the volume and turn on scheduled backups
gcloud netapp volumes update my-nfs-vol \
  --location=us-central1 \
  --backup-config=backup-vault=my-vault,backup-policies=my-policy,enable-scheduled-backups=true

gcloud netapp backup-vaults backups list \
  --location=us-central1 --backup-vault=my-vault
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `netapp active-directories` | [`active-directories.md`](active-directories.md) | 5 | Create and manage Active Directory configs for SMB / LDAP-backed volumes |
| `netapp backup-policies` | [`backup-policies.md`](backup-policies.md) | 5 | Define daily/weekly/monthly backup schedules and retention |
| `netapp backup-vaults` | [`backup-vaults.md`](backup-vaults.md) | 10 | Manage backup vaults and the backups stored in them (`backups` sub-group) |
| `netapp host-groups` | [`host-groups.md`](host-groups.md) | 5 | Manage iSCSI initiator host groups for block volumes |
| `netapp kms-configs` | [`kms-configs.md`](kms-configs.md) | 7 | Configure, verify, and apply CMEK encryption keys |
| `netapp locations` | [`locations.md`](locations.md) | 2 | Discover regions where NetApp Volumes is available |
| `netapp operations` | [`operations.md`](operations.md) | 2 | Inspect long-running operations |
| `netapp storage-pools` | [`storage-pools.md`](storage-pools.md) | 7 | Create and manage storage pools (capacity + service level) |
| `netapp volumes` | [`volumes.md`](volumes.md) | 27 | Create and manage volumes plus `snapshots`, `replications`, `quota-rules` sub-groups |

See [`index.md`](index.md) for a one-line index of all 70 GA commands.

## Common flags & tips

- **`--location=REGION` is near-universal.** Almost every command requires it; you can instead
  set a default with `gcloud config set netapp/location us-central1`. `list` commands default to
  all locations when `--location` is omitted.
- **Capacity units.** `--capacity` is in GiB unless a unit suffix is given (e.g. `2048`, `2TiB`).
- **Service levels** (`storage-pools create --service-level`): `standard`, `premium`, `extreme`,
  and `flex`. Flex pools support `--type=unified` (file + block) and `--allow-auto-tiering`.
- **Protocols** (`volumes create --protocols`): comma-separated `nfsv3`, `nfsv4`, `smb`. Use
  `--unix-permissions` only with NFS; use `--security-style=ntfs` and `--smb-settings` for SMB.
- **Nested resources need their parent.** Snapshots, replications, and quota-rules take
  `--volume`; backups take `--backup-vault`; quota-rules can be created on a volume with
  `--type` (e.g. `DEFAULT_USER_QUOTA`) and `--disk-limit-mib`.
- **Async.** Most mutating commands accept `--async` to return immediately instead of waiting on
  the operation; track progress with `gcloud netapp operations describe`.
- **Filter / format examples:**
  ```bash
  gcloud netapp volumes list --location=us-central1 \
    --filter="capacityGib>1024" --format="table(name,state,capacityGib)"
  gcloud netapp storage-pools list --location=us-central1 \
    --format="value(name)"
  ```
- **CMEK & directory services.** Encrypt existing resources in a region with
  `gcloud netapp kms-configs encrypt`, and validate a pool's directory service with
  `gcloud netapp storage-pools validate-directory-service`.

## beta / alpha

Both `gcloud beta netapp` and `gcloud alpha netapp` exist and mirror the same nine GA subgroups
(`active-directories`, `backup-policies`, `backup-vaults`, `host-groups`, `kms-configs`,
`locations`, `operations`, `storage-pools`, `volumes`). They carry the standard pre-release
caveats ("might change without notice"). New iSCSI/block-storage capabilities under
`host-groups` and the `backup-vaults backups` sub-group sometimes surface flags in
`gcloud beta netapp` / `gcloud alpha netapp` before reaching GA — check those tracks for the
latest options.

## Official documentation

- [Google Cloud NetApp Volumes — docs home](https://cloud.google.com/netapp/volumes/docs) — product documentation landing page.
- [Product overview](https://cloud.google.com/netapp/volumes/docs/discover/overview) — architecture, protocols, and core concepts.
- [Storage pools overview](https://cloud.google.com/netapp/volumes/docs/configure-and-use/storage-pools/overview) — service levels and capacity containers.
- [Create a storage pool](https://cloud.google.com/netapp/volumes/docs/configure-and-use/storage-pools/create-storage-pool) — gcloud how-to (Standard and Flex Unified).
- [Volumes overview](https://cloud.google.com/netapp/volumes/docs/configure-and-use/volumes/overview) — capacity, protocols, data protection, quota rules.
- [Create a volume](https://cloud.google.com/netapp/volumes/docs/configure-and-use/volumes/create-volume) — gcloud how-to for NFS, SMB, and iSCSI volumes.
- [REST API reference](https://cloud.google.com/netapp/volumes/docs/reference/rest) — API surface (`netapp.googleapis.com`).
- [gcloud netapp CLI reference](https://cloud.google.com/sdk/gcloud/reference/netapp) — full command/flag reference.

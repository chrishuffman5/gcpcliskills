---
name: gcloud-oracle-database
description: >-
  Oracle Database@Google Cloud via gcloud (`gcloud oracle-database`). Manage Oracle Database resources — autonomous-database-backups, autonomous-database-character-sets, autonomous-databases, autonomous-db-versions, cloud-exadata-infrastructures, cloud-vm-clusters, database-character-sets, databases.
---

# gcloud oracle-database — Oracle Database@Google Cloud

## Overview

`gcloud oracle-database` manages **Oracle Database@Google Cloud**, which runs Oracle Cloud
Infrastructure (OCI) Exadata hardware inside Google Cloud data centers. Use it to provision
the networking, infrastructure, and database resources behind Oracle's Autonomous AI Database,
Exadata Database Service, Base Database Service, and Exadata-on-Exascale offerings — all from
the gcloud CLI and billed through Google Cloud. Reach for it when you need Oracle-compatible
databases with low-latency access to other Google Cloud services on the same network.

All 63 commands are GA. The API must be enabled first:

```bash
gcloud services enable oracledatabase.googleapis.com
```

Almost every command is regional and requires `--location` (for example `us-east4`). Resource
IDs can be given as a short name plus `--location`, or as a fully qualified
`projects/PROJECT/locations/LOCATION/...` path.

## Quick reference — common workflows

### 1. Set up networking (ODB Network + client subnet)

Required before provisioning any Exadata or Autonomous Database resource.

```bash
# Associate a VPC with the Oracle OCI child site
gcloud oracle-database odb-networks create my-odbnetwork \
    --location=us-east4 \
    --network=projects/MY_PROJECT/locations/global/networks/default

# Create a client subnet inside the ODB Network
gcloud oracle-database odb-networks odb-subnets create my-odbsubnet \
    --odb-network=my-odbnetwork \
    --location=us-east4 \
    --cidr-range=10.0.10.0/24 \
    --purpose=CLIENT_SUBNET

# Verify
gcloud oracle-database odb-networks describe my-odbnetwork --location=us-east4
gcloud oracle-database odb-networks odb-subnets list \
    --odb-network=my-odbnetwork --location=us-east4
```

### 2. Create and inspect an Autonomous Database

```bash
gcloud oracle-database autonomous-databases create my-adb \
    --location=us-east4 \
    --display-name="My Autonomous DB" \
    --database=myadb \
    --admin-password=My123Password \
    --properties-compute-count=2 \
    --properties-db-version=19c \
    --properties-license-type=LICENSE_INCLUDED \
    --properties-db-workload=DW \
    --odb-network=projects/MY_PROJECT/locations/us-east4/odbNetworks/my-odbnetwork \
    --odb-subnet=projects/MY_PROJECT/locations/us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-odbsubnet

gcloud oracle-database autonomous-databases describe my-adb --location=us-east4
gcloud oracle-database autonomous-databases list --location=us-east4
```

### 3. Manage Autonomous Database lifecycle (stop / start / restart)

```bash
gcloud oracle-database autonomous-databases stop my-adb --location=us-east4
gcloud oracle-database autonomous-databases start my-adb --location=us-east4
gcloud oracle-database autonomous-databases restart my-adb --location=us-east4
```

### 4. Generate a connection wallet and restore from backup

```bash
# Generate a wallet (base64-encoded zip) for client connections
gcloud oracle-database autonomous-databases generate-wallet my-adb \
    --location=us-east4 \
    --password=WalletPass123

# Find a backup, then restore to its endTime (RESTORE_TIME)
gcloud oracle-database autonomous-database-backups list --location=us-east4
gcloud oracle-database autonomous-databases restore my-adb \
    --location=us-east4 \
    --restore-time=2024-05-01T00:00:00.000Z
```

### 5. Provision Exadata Infrastructure + VM Cluster

```bash
# List available shapes for the region first
gcloud oracle-database db-system-shapes list --location=us-east4

# Create the Exadata Infrastructure
gcloud oracle-database cloud-exadata-infrastructures create my-exadata \
    --location=us-east4 \
    --display-name="My Exadata" \
    --properties-shape=Exadata.X9M \
    --properties-compute-count=2 \
    --properties-storage-count=3

# Once provisioned, list its DB servers
gcloud oracle-database cloud-exadata-infrastructures db-servers list \
    --cloud-exadata-infrastructure=my-exadata \
    --location=us-east4

# Create a VM Cluster on the infrastructure (ODB Network-based)
gcloud oracle-database cloud-vm-clusters create my-vmcluster \
    --location=us-east4 \
    --exadata-infrastructure=my-exadata \
    --odb-network=projects/MY_PROJECT/locations/us-east4/odbNetworks/my-odbnetwork \
    --odb-subnet=projects/MY_PROJECT/locations/us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-odbsubnet \
    --backup-odb-subnet=projects/MY_PROJECT/locations/us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-backup-subnet \
    --properties-cpu-core-count=4 \
    --properties-license-type=LICENSE_INCLUDED \
    --properties-gi-version=19.0.0.0

gcloud oracle-database cloud-vm-clusters describe my-vmcluster --location=us-east4
```

### 6. High availability: switchover / failover for an Autonomous Database

```bash
# Planned switchover (no data loss)
gcloud oracle-database autonomous-databases switchover my-adb \
    --location=us-east4 \
    --peer-autonomous-database=projects/MY_PROJECT/locations/us-west3/autonomousDatabases/my-adb-standby

# Emergency failover (standby becomes primary)
gcloud oracle-database autonomous-databases failover my-adb \
    --location=us-east4 \
    --peer-autonomous-database=projects/MY_PROJECT/locations/us-west3/autonomousDatabases/my-adb-standby
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `oracle-database autonomous-database-backups` | [`autonomous-database-backups.md`](autonomous-database-backups.md) | 1 | manage Autonomous Database Backup resources |
| `oracle-database autonomous-database-character-sets` | [`autonomous-database-character-sets.md`](autonomous-database-character-sets.md) | 1 | manage Autonomous Database Character Set resources |
| `oracle-database autonomous-databases` | [`autonomous-databases.md`](autonomous-databases.md) | 12 | manage Autonomous Database resources |
| `oracle-database autonomous-db-versions` | [`autonomous-db-versions.md`](autonomous-db-versions.md) | 1 | manage Autonomous Db Version resources |
| `oracle-database cloud-exadata-infrastructures` | [`cloud-exadata-infrastructures.md`](cloud-exadata-infrastructures.md) | 5 | manage Cloud Exadata Infrastructure resources |
| `oracle-database cloud-vm-clusters` | [`cloud-vm-clusters.md`](cloud-vm-clusters.md) | 5 | manage Cloud Vm Cluster resources |
| `oracle-database database-character-sets` | [`database-character-sets.md`](database-character-sets.md) | 1 | manage Database Character Set resources |
| `oracle-database databases` | [`databases.md`](databases.md) | 2 | manage Database resources |
| `oracle-database db-system-initial-storage-sizes` | [`db-system-initial-storage-sizes.md`](db-system-initial-storage-sizes.md) | 1 | manage Db System Initial Storage Size resources |
| `oracle-database db-system-shapes` | [`db-system-shapes.md`](db-system-shapes.md) | 1 | manage Db System Shape resources |
| `oracle-database db-systems` | [`db-systems.md`](db-systems.md) | 4 | manage Db System resources |
| `oracle-database db-versions` | [`db-versions.md`](db-versions.md) | 1 | manage Db Version resources |
| `oracle-database entitlements` | [`entitlements.md`](entitlements.md) | 1 | manage Entitlement resources |
| `oracle-database exadb-vm-clusters` | [`exadb-vm-clusters.md`](exadb-vm-clusters.md) | 6 | manage Exadb Vm Cluster (Exascale) resources |
| `oracle-database exascale-db-storage-vaults` | [`exascale-db-storage-vaults.md`](exascale-db-storage-vaults.md) | 4 | manage Exascale Db Storage Vault resources |
| `oracle-database gi-versions` | [`gi-versions.md`](gi-versions.md) | 2 | manage Grid Infrastructure (Gi) Version resources |
| `oracle-database odb-networks` | [`odb-networks.md`](odb-networks.md) | 8 | manage Odb Network (and odb-subnet) resources |
| `oracle-database operations` | [`operations.md`](operations.md) | 5 | manage long-running Operation resources |
| `oracle-database pluggable-databases` | [`pluggable-databases.md`](pluggable-databases.md) | 2 | manage Pluggable Database resources |

See [`index.md`](index.md) for a one-line index of all 63 commands.

## Common flags & tips

- **`--location` is required almost everywhere.** It accepts a Google Cloud region (e.g.
  `us-east4`). For nested resources you can instead pass a fully qualified resource path and
  omit `--location`.
- **Networking comes first.** Create an `odb-network` and at least one `odb-subnet`
  (`--purpose=CLIENT_SUBNET`) before creating Autonomous Databases, VM Clusters, or DB Systems.
  ODB-Network-based configuration is the recommended path; network + CIDR (`--cidr`,
  `--backup-subnet-cidr`) is also supported.
- **`--async`** on create/delete/lifecycle commands returns immediately instead of blocking.
  Track the returned operation with the `operations` group:

  ```bash
  gcloud oracle-database operations list --location=us-east4
  gcloud oracle-database operations wait OPERATION_ID --location=us-east4
  ```

- **Property flags use the `--properties-*` prefix** on create/update (for example
  `--properties-compute-count`, `--properties-db-workload`, `--properties-license-type`,
  `--properties-gi-version`, `--properties-shape`).
- **`--gcp-oracle-zone`** (e.g. `us-east4-b-r2`) pins the OCI zone for `odb-networks`,
  `cloud-exadata-infrastructures`, and `exascale-db-storage-vaults`; omit it to let the system
  choose by availability.
- **List filtering / formatting.** All `list` commands accept `--filter`, `--sort-by`,
  `--limit`, and `--format`. Examples:

  ```bash
  # Backups for one database
  gcloud oracle-database autonomous-database-backups list \
      --location=us-east4 --filter='autonomous_database_id="my-adb"'

  # Compact custom columns
  gcloud oracle-database autonomous-databases list --location=us-east4 \
      --format='table(name, properties.lifecycleState, properties.dbWorkload)'
  ```

- **Deleting infrastructure.** `cloud-exadata-infrastructures delete` and
  `cloud-vm-clusters delete` support `--force` to remove dependent child resources in one step.

## Official documentation

- [Oracle Database@Google Cloud docs](https://cloud.google.com/oracle/database/docs) — product documentation home.
- [Product overview](https://cloud.google.com/oracle/database/docs/overview) — architecture and supported services (Exadata, Autonomous, Base DB, GoldenGate).
- [IAM overview](https://cloud.google.com/oracle/database/docs/iam-overview) — predefined roles such as `roles/oracledatabase.admin` and `roles/oracledatabase.viewer`.
- [Create an ODB Network](https://cloud.google.com/oracle/database/docs/create-odb-network) — required networking prerequisite.
- [Create Exadata Infrastructure](https://cloud.google.com/oracle/database/docs/create-exadata-infrastructure) and [Create a VM Cluster](https://cloud.google.com/oracle/database/docs/create-vm-cluster) — Exadata provisioning guides.
- [Create an Autonomous Database](https://cloud.google.com/oracle/database/docs/create-autonomous-database) — Autonomous DB how-to.
- [REST API reference](https://cloud.google.com/oracle/database/docs/reference/rest) — confirms the `oracledatabase.googleapis.com` endpoint.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database) — full command reference.

See [`sources.md`](sources.md) for the citation record.

---
name: gcloud-database-migration
description: >-
  Database Migration Service via gcloud (`gcloud database-migration`). Manage Database Migration Service resources — connection-profiles, conversion-workspaces, migration-jobs, objects, operations, private-connections.
---

# gcloud database-migration — Database Migration Service

## Overview
Database Migration Service (DMS) moves data and metadata from source databases to managed destinations on Google Cloud with minimal downtime, using CDC-based continuous replication. It supports **homogeneous** migrations (e.g. MySQL → Cloud SQL for MySQL, SQL Server → Cloud SQL for SQL Server) and **heterogeneous** migrations (e.g. Oracle/SQL Server → PostgreSQL) via conversion workspaces. Reach for it when migrating MySQL, PostgreSQL, SQL Server, or Oracle into Cloud SQL or AlloyDB for PostgreSQL. Resources are regional, so almost every command takes `--region`.

Enable the API once per project before using any command:

```bash
gcloud services enable datamigration.googleapis.com
```

## Quick reference — common workflows

### 1. MySQL → Cloud SQL for MySQL continuous migration
```bash
# Source connection profile (external MySQL)
gcloud database-migration connection-profiles create mysql my-src-profile \
  --region=us-central1 --host=1.2.3.4 --port=3306 \
  --username=migration-user --password=SECRET

# Destination profile — DMS provisions the Cloud SQL replica
gcloud database-migration connection-profiles create cloudsql my-dest-profile \
  --region=us-central1 --database-version=MYSQL_8_0 \
  --source-id=my-src-profile --tier=db-n1-standard-1

# Create, start, and monitor the migration job
gcloud database-migration migration-jobs create my-migration-job \
  --region=us-central1 --type=CONTINUOUS \
  --source=my-src-profile --destination=my-dest-profile
gcloud database-migration migration-jobs start my-migration-job --region=us-central1
gcloud database-migration migration-jobs describe my-migration-job --region=us-central1
```

### 2. Verify, then cut over (promote) a running job
```bash
# Validate configuration before/while running
gcloud database-migration migration-jobs verify my-migration-job --region=us-central1

# When CDC lag is near zero, promote: the destination becomes an independent primary
gcloud database-migration migration-jobs promote my-migration-job --region=us-central1
```

### 3. Heterogeneous Oracle → PostgreSQL with a conversion workspace
```bash
# Oracle source profile (static-IP connectivity)
gcloud database-migration connection-profiles create oracle my-oracle-src \
  --region=us-central1 --host=10.0.0.5 --port=1521 \
  --username=dms_user --password=SECRET \
  --database-service=ORCL --static-ip-connectivity

# Cloud SQL for PostgreSQL destination profile (existing instance)
gcloud database-migration connection-profiles create postgresql my-pg-dest \
  --region=us-central1 --cloudsql-instance=my-cloudsql-pg-instance

# Create the conversion workspace, seed it from the source, then convert
gcloud database-migration conversion-workspaces create my-cw \
  --region=us-central1 --source-database-engine=ORACLE \
  --source-database-version=19c \
  --destination-database-engine=POSTGRESQL --destination-database-version=15
gcloud database-migration conversion-workspaces seed my-cw \
  --region=us-central1 --source-connection-profile=my-oracle-src
gcloud database-migration conversion-workspaces convert my-cw --region=us-central1

# Review issues and generated DDLs, then commit
gcloud database-migration conversion-workspaces describe-issues my-cw --region=us-central1
gcloud database-migration conversion-workspaces describe-ddls my-cw --region=us-central1
gcloud database-migration conversion-workspaces commit my-cw \
  --region=us-central1 --commit-name=initial-commit

# Migration job that references the conversion workspace
gcloud database-migration migration-jobs create my-hetero-job \
  --region=us-central1 --type=CONTINUOUS \
  --source=my-oracle-src --destination=my-pg-dest --conversion-workspace=my-cw
gcloud database-migration migration-jobs start my-hetero-job --region=us-central1
```

### 4. Pause, resume, and restart a job
```bash
gcloud database-migration migration-jobs stop my-migration-job --region=us-central1
gcloud database-migration migration-jobs resume my-migration-job --region=us-central1
# Restart re-runs from the full-dump phase; skip prior verification with --skip-validation
gcloud database-migration migration-jobs restart my-migration-job \
  --region=us-central1 --skip-validation
```

### 5. List and inspect resources
```bash
gcloud database-migration connection-profiles list --region=us-central1
gcloud database-migration connection-profiles test my-src-profile --region=us-central1
gcloud database-migration migration-jobs list --region=us-central1
gcloud database-migration conversion-workspaces mapping-rules list \
  --conversion-workspace=my-cw --region=us-central1
gcloud database-migration objects list --migration-job=my-migration-job --region=us-central1
```

### 6. Reverse-SSH tunnel connectivity script
```bash
# Generate the bash script to set up an SSH tunnel on an existing bastion VM
gcloud database-migration migration-jobs generate-ssh-script my-migration-job \
  --vm=bastion-vm --vm-port=1234 --vm-zone=us-central1-a --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `database-migration connection-profiles` | [`connection-profiles.md`](connection-profiles.md) | 11 | Source/destination connection profiles (MySQL, PostgreSQL, SQL Server, Oracle, Cloud SQL, AlloyDB) |
| `database-migration conversion-workspaces` | [`conversion-workspaces.md`](conversion-workspaces.md) | 16 | Heterogeneous schema conversion: create, seed, convert, commit, mapping rules |
| `database-migration migration-jobs` | [`migration-jobs.md`](migration-jobs.md) | 14 | The migration lifecycle: create, verify, start, stop, resume, restart, promote |
| `database-migration objects` | [`objects.md`](objects.md) | 2 | List and look up the per-object state within a migration job |
| `database-migration operations` | [`operations.md`](operations.md) | 3 | Track and manage long-running operations |
| `database-migration private-connections` | [`private-connections.md`](private-connections.md) | 4 | VPC-peering / PSC private connectivity to source databases |

See [`index.md`](index.md) for a one-line index of all 50 commands.

## Common flags & tips
- **`--region` is required almost everywhere.** DMS resources are regional; commands either accept `--region=REGION` or take a fully qualified resource name. `list`, `create`, and `objects`/`mapping-rules` subcommands require it explicitly.
- **Connection-profile roles.** Most `create` subcommands accept `--role=SOURCE|DESTINATION`. The `cloudsql` and `alloydb` subcommands are destination profiles — DMS provisions the replica instance (Cloud SQL needs `--source-id`, `--tier`, and a `--database-version`; AlloyDB needs `--cpu-count`, `--password`, `--primary-id`).
- **Passwords.** Pass `--password=...` inline or use `--prompt-for-password` to avoid putting secrets in shell history (supported on `mysql`, `oracle`, `postgresql`, `sqlserver` profile creation).
- **Connectivity methods** on `migration-jobs create`/`update` are mutually exclusive: `--static-ip`, `--peer-vpc=NETWORK`, or the reverse-SSH set (`--vm`, `--vm-ip`, `--vm-port`, `--vpc`). Oracle/SQL Server source profiles also support `--private-connection`, `--static-ip-connectivity`, or forward-SSH (`--forward-ssh-hostname` …).
- **Synchronous mode.** Long-running mutations (`test`, `apply`, `seed`, `convert`, `commit`, profile/workspace `create`/`delete`) accept `--no-async` to block until the operation completes.
- **Filtering output:** standard `--filter`, `--sort-by`, `--limit`, and `--uri` apply to all `list` commands. Example: `gcloud database-migration connection-profiles list --region=us-central1 --filter="state=READY"`.
- **Entity filtering** in conversion workspaces uses AIP-160 expressions, e.g. `--filter="Company.Employee* AND type=TABLE"` on `convert` / `apply`.
- **Heterogeneous mapping rules** can be imported from an Ora2Pg config with `conversion-workspaces import-rules --file-format=ORA2PG --config-files=...`.

## Official documentation
- [Database Migration Service docs home](https://cloud.google.com/database-migration/docs) — all migration paths, concepts, and guides.
- [DMS overview](https://cloud.google.com/database-migration/docs/overview) — homogeneous vs. heterogeneous migrations, CDC, connectivity, security.
- [MySQL quickstart](https://cloud.google.com/database-migration/docs/mysql/quickstart) — end-to-end MySQL → Cloud SQL migration via gcloud/console.
- [Configure a MySQL source](https://cloud.google.com/database-migration/docs/mysql/configure-source-database) — binary logging, GTID, user privileges, InnoDB requirements.
- [Configure connectivity](https://cloud.google.com/database-migration/docs/mysql/configure-connectivity) — IP allowlist, reverse-SSH tunnel, VPC peering, Private Service Connect.
- [IAM roles for DMS](https://cloud.google.com/iam/docs/roles-permissions/datamigration) — `datamigration.admin`, `datamigration.editor`, `datamigration.serviceAgent`.
- [gcloud database-migration reference](https://cloud.google.com/sdk/gcloud/reference/database-migration) — full CLI reference for every command group.
- [REST API reference](https://cloud.google.com/database-migration/docs/reference/rest) — service ID `datamigration.googleapis.com`.

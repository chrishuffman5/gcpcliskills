---
name: gcloud-spanner
description: >-
  Cloud Spanner via gcloud (`gcloud spanner`). Command groups for Cloud Spanner — backup-schedules, backups, databases, instance-configs, instance-partitions, instances, operations, rows.
---

# gcloud spanner — Cloud Spanner

## Overview

Cloud Spanner is a fully managed, globally distributed relational database with strong
transactional consistency at scale, supporting both GoogleSQL and PostgreSQL dialects.
The `gcloud spanner` command groups manage the full lifecycle of instances, instance
configurations and partitions, databases (schema/DDL, sessions, roles, split points,
rows), backups and backup schedules, and long-running operations. Reach for it to
provision capacity, create and evolve database schemas, run ad-hoc SQL, and manage
backup/restore and IAM access from the CLI.

## Quick reference — common workflows

### 1. Enable the API and create an instance

```bash
# One-time: enable the Cloud Spanner API
gcloud services enable spanner.googleapis.com

# List available instance configurations (regional/multi-region)
gcloud spanner instance-configs list

# Create a regional instance (3 nodes, Enterprise edition)
gcloud spanner instances create my-instance \
    --config=regional-us-central1 \
    --description="My Spanner Instance" \
    --nodes=3 \
    --edition=ENTERPRISE

# Confirm it exists, then list all instances
gcloud spanner instances describe my-instance
gcloud spanner instances list
```

### 2. Create a database and apply a schema

```bash
# Create a database with an initial GoogleSQL schema
gcloud spanner databases create my-database \
    --instance=my-instance \
    --ddl='CREATE TABLE Singers (SingerId INT64 NOT NULL, FirstName STRING(1024), LastName STRING(1024)) PRIMARY KEY (SingerId)'

# Add a column via a DDL update
gcloud spanner databases ddl update my-database \
    --instance=my-instance \
    --ddl='ALTER TABLE Singers ADD COLUMN BirthDate DATE'

# Inspect current DDL and list databases
gcloud spanner databases ddl describe my-database --instance=my-instance
gcloud spanner databases list --instance=my-instance
```

### 3. Write and query data

```bash
# Insert a row
gcloud spanner rows insert --table=Singers \
    --instance=my-instance --database=my-database \
    --data=SingerId=1,FirstName=Marc,LastName=Richards

# Run a SQL query
gcloud spanner databases execute-sql my-database \
    --instance=my-instance \
    --sql='SELECT SingerId, FirstName, LastName FROM Singers'

# Inspect the query plan instead of running it
gcloud spanner databases execute-sql my-database \
    --instance=my-instance \
    --sql='SELECT * FROM Singers WHERE SingerId = 1' \
    --query-mode=PLAN
```

### 4. Create and restore a backup

```bash
# Create a backup with a 2-week retention period
gcloud spanner backups create my-backup \
    --instance=my-instance --database=my-database \
    --retention-period=2w

# List and describe backups
gcloud spanner backups list --instance=my-instance
gcloud spanner backups describe my-backup --instance=my-instance

# Restore into a new database
gcloud spanner databases restore \
    --source-backup=my-backup --source-instance=my-instance \
    --destination-database=my-restored-database \
    --destination-instance=my-instance

# Extend a backup's expiration
gcloud spanner backups update-metadata my-backup \
    --instance=my-instance --expiration-date=2026-12-31T23:59:59Z
```

### 5. Schedule recurring backups

```bash
# Create a daily full-backup schedule (2am UTC), retained 2 weeks
gcloud spanner backup-schedules create my-schedule \
    --instance=my-instance --database=my-database \
    --cron="0 2 * * *" --retention-duration=2w \
    --backup-type=full-backup

# List, then delete a schedule
gcloud spanner backup-schedules list --instance=my-instance --database=my-database
gcloud spanner backup-schedules delete my-schedule \
    --instance=my-instance --database=my-database
```

### 6. Manage IAM access

```bash
# Grant the database-user role on an instance to a service account
gcloud spanner instances add-iam-policy-binding my-instance \
    --member='serviceAccount:my-sa@my-project.iam.gserviceaccount.com' \
    --role='roles/spanner.databaseUser'

# Grant database-admin on a specific database
gcloud spanner databases add-iam-policy-binding my-database \
    --instance=my-instance \
    --member='user:dev@example.com' \
    --role='roles/spanner.databaseAdmin'

# Inspect the current instance policy
gcloud spanner instances get-iam-policy my-instance
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `spanner backup-schedules` | [`backup-schedules.md`](backup-schedules.md) | 9 | Manage Cloud Spanner backup schedules (cron, retention, full/incremental) |
| `spanner backups` | [`backups.md`](backups.md) | 10 | Create, copy, restore-source, and manage backups |
| `spanner databases` | [`databases.md`](databases.md) | 19 | Manage databases: DDL, SQL, sessions, roles, splits, restore, IAM |
| `spanner instance-configs` | [`instance-configs.md`](instance-configs.md) | 5 | Manage regional/multi-region and custom instance configurations |
| `spanner instance-partitions` | [`instance-partitions.md`](instance-partitions.md) | 5 | Manage Spanner instance partitions |
| `spanner instances` | [`instances.md`](instances.md) | 11 | Create, scale, move, and manage instances and their IAM |
| `spanner operations` | [`operations.md`](operations.md) | 3 | Describe, list, and cancel long-running operations |
| `spanner rows` | [`rows.md`](rows.md) | 3 | Insert, update, and delete rows |
| `spanner samples` | [`samples.md`](samples.md) | 5 | Cloud Spanner sample applications |

Top-level command (see [`_commands.md`](_commands.md)): `gcloud spanner cli` — an interactive
Spanner shell. Full one-line index of all 71 commands is in [`index.md`](index.md).

## Common flags & tips

- **Resource scoping:** Most database/backup/session commands take a positional resource
  ID plus `--instance` (and `--database` where applicable). You can set defaults with
  `gcloud config set spanner/instance INSTANCE` and `--project` / `core/project`.
- **Capacity:** On `instances create`/`update`, use `--nodes` *or* `--processing-units`
  (mutually exclusive), or the autoscaling flags. `--edition` accepts `STANDARD`,
  `ENTERPRISE`, or `ENTERPRISE_PLUS`.
- **Dialect:** `databases create --database-dialect=POSTGRESQL` (default is
  `GOOGLE_STANDARD_SQL`). `--ddl` is not supported for the PostgreSQL dialect.
- **Schema from a file:** `databases create --ddl-file=...` and
  `databases ddl update --ddl-file=...` accept semicolon-separated statements
  (`--ddl-file` overrides `--ddl`).
- **Backups:** `backups create` requires exactly one of `--expiration-date` or
  `--retention-period`; durations such as `2w` follow `gcloud topic datetimes`.
- **Async:** `--async` returns immediately on long operations (create/restore/ddl); track
  them with `gcloud spanner operations list --instance=my-instance` and
  `gcloud spanner operations describe`.
- **Query modes:** `execute-sql --query-mode=` is one of `NORMAL` (default), `PLAN`,
  `PROFILE`, `WITH_PLAN_AND_STATS`, or `WITH_STATS`.
- **Drop protection:** `databases update --enable-drop-protection` /
  `--no-enable-drop-protection` guards against accidental deletion.
- **Filtering/format:** standard `--filter`, `--sort-by`, `--limit`, and `--format` apply
  to list commands, e.g.
  `gcloud spanner instances list --format="table(name, config, nodeCount)"`.

## beta / alpha

- **`gcloud beta spanner`** mirrors the GA command-group surface (backup-schedules,
  backups, databases, instance-configs, instance-partitions, instances, operations, rows,
  samples) and may expose newer flags/behaviors before they are promoted to GA.
- **`gcloud alpha spanner`** adds an alpha-only group:
  - **`gcloud alpha spanner migrate`** — migrate external databases (MySQL, PostgreSQL,
    SQL Server, Oracle) into Cloud Spanner. Absent from GA and beta.
- For routine instance/database/backup work the GA surface is complete; reach for alpha
  only for migration workflows.

## Official documentation

- Cloud Spanner documentation home: https://cloud.google.com/spanner/docs — entry point for all Spanner product docs.
- gcloud spanner CLI reference: https://cloud.google.com/sdk/gcloud/reference/spanner — all GA command groups and flags.
- Set up your environment: https://cloud.google.com/spanner/docs/getting-started/set-up — API enablement and IAM prerequisites.
- Instances overview: https://cloud.google.com/spanner/docs/instances — editions, configurations, and compute capacity concepts.
- Create and manage instances: https://cloud.google.com/spanner/docs/create-manage-instances — gcloud CLI and console walkthroughs.
- Create and manage databases: https://cloud.google.com/spanner/docs/create-manage-databases — schema creation, updates, import, deletion.
- Backups overview: https://cloud.google.com/spanner/docs/backup — full/incremental backups, schedules, retention, and restore.
- IAM overview: https://cloud.google.com/spanner/docs/iam — predefined Spanner roles and access-control patterns.
- Editions overview: https://cloud.google.com/spanner/docs/editions-overview — Standard, Enterprise, and Enterprise Plus tiers.
- Quickstart (console): https://cloud.google.com/spanner/docs/quickstart-console — create an instance/database and run SQL in the console.
</content>
</invoke>

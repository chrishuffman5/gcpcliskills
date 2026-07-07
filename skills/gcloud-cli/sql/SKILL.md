---
name: gcloud-sql
description: >-
  Cloud SQL via gcloud (`gcloud sql`). Create and manage Google Cloud SQL databases — backups, databases, export, flags, import, instances, operations, ssl.
---

# gcloud sql — Cloud SQL

## Overview

Cloud SQL is a fully managed relational database service for MySQL, PostgreSQL, and
SQL Server on Google Cloud. The `gcloud sql` command group manages the full instance
lifecycle — creating instances, databases, and users; connecting; backups and
point-in-time recovery; read replicas; and import/export — through the Cloud SQL Admin
API. Enable that API once per project before running any command:
`gcloud services enable sqladmin.googleapis.com`.

## Quick reference — common workflows

**Create a MySQL instance (custom machine, HA, automated backups)**
```bash
gcloud services enable sqladmin.googleapis.com

gcloud sql instances create prod-instance \
    --database-version=MYSQL_8_0 \
    --cpu=2 --memory=4GB \
    --region=us-central1 \
    --availability-type=regional \
    --backup-start-time=03:00 \
    --enable-point-in-time-recovery \
    --root-password=STRONG_PASSWORD

gcloud sql instances describe prod-instance
```

**Create a PostgreSQL instance (Enterprise Plus, tier-based)**
```bash
gcloud sql instances create pg-instance \
    --database-version=POSTGRES_16 \
    --tier=db-perf-optimized-N-4 \
    --edition=enterprise-plus \
    --region=us-east1 \
    --availability-type=regional \
    --root-password=STRONG_PASSWORD
```
Note: `--cpu`/`--memory` are not compatible with the Enterprise Plus edition — use
`--tier` instead.

**Create a database and a user**
```bash
gcloud sql databases create app_db \
    --instance=prod-instance \
    --charset=utf8mb4 --collation=utf8mb4_unicode_ci

gcloud sql users create app-user \
    --instance=prod-instance --password=APP_USER_PASSWORD

gcloud sql databases list --instance=prod-instance
gcloud sql users list --instance=prod-instance
```

**Connect with the built-in client**
```bash
# Opens a local mysql/psql/sqlcmd client; temporarily allowlists your IP.
gcloud sql connect prod-instance --user=root
gcloud sql connect pg-instance --user=postgres --database=app_db
```

**Take an on-demand backup and restore it**
```bash
gcloud sql backups create \
    --instance=prod-instance --description="pre-migration backup"

# Find the backup ID, then restore into a target instance
gcloud sql backups list --instance=prod-instance
gcloud sql backups restore BACKUP_ID --restore-instance=prod-instance
```

**Create a read replica (and promote it later)**
```bash
# Same-region replica
gcloud sql instances create prod-replica \
    --master-instance-name=prod-instance

# Cross-region replica for DR
gcloud sql instances create prod-replica-dr \
    --master-instance-name=prod-instance --region=us-west1

gcloud sql instances promote-replica prod-replica
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `sql backups` | [`backups.md`](backups.md) | 6 | work with backups of Cloud SQL instances |
| `sql databases` | [`databases.md`](databases.md) | 5 | manage databases of Cloud SQL instances |
| `sql export` | [`export.md`](export.md) | 4 | export Cloud SQL instances (bak/csv/sql/tde) |
| `sql flags` | [`flags.md`](flags.md) | 1 | list customizable database flags |
| `sql import` | [`import.md`](import.md) | 4 | import into Cloud SQL instances (bak/csv/sql/tde) |
| `sql instances` | [`instances.md`](instances.md) | 20 | manage Cloud SQL instances |
| `sql operations` | [`operations.md`](operations.md) | 4 | work with Cloud SQL instance operations |
| `sql ssl` | [`ssl.md`](ssl.md) | 12 | manage client/server SSL certificates |
| `sql ssl-certs` | [`ssl-certs.md`](ssl-certs.md) | 4 | manage SSL certificates (legacy command set) |
| `sql tiers` | [`tiers.md`](tiers.md) | 1 | list available service tiers |
| `sql users` | [`users.md`](users.md) | 6 | manage Cloud SQL users |

Top-level commands ([`_commands.md`](_commands.md)): `gcloud sql connect`,
`gcloud sql generate-login-token`, `gcloud sql reschedule-maintenance`. See
[`index.md`](index.md) for a one-line index of all 70 GA commands.

## Common flags & tips

- **Engine & version** — `--database-version` (e.g. `MYSQL_8_0`, `POSTGRES_16`,
  `SQLSERVER_2022_STANDARD`; defaults to `MYSQL_8_0`).
- **Machine sizing** — use `--cpu` + `--memory` for a custom machine type (omit
  `--tier`), or `--tier` for shared-core / Enterprise Plus instances. The two
  approaches are mutually exclusive.
- **Location** — `--region` (default `us-central`) or pin a `--zone`/`--secondary-zone`.
- **High availability** — `--availability-type=regional` for cross-zone failover
  (default is `zonal`). Trigger a test failover with `gcloud sql instances failover`.
- **Credentials** — `--root-password` sets the built-in admin password at create time;
  `gcloud sql users set-password` rotates it later.
- **Backups & PITR** — `--backup-start-time=HH:MM` enables daily backups;
  `--enable-point-in-time-recovery` (or `--enable-bin-log` for MySQL) enables PITR.
- **Connecting** — `gcloud sql connect INSTANCE --user=USER [--database=DB]` opens a
  local client and temporarily allowlists your IP (public IP required). For application
  connections, prefer the Cloud SQL Auth Proxy or Private Service Connect.
- **Output shaping** — combine with global flags, e.g.
  `gcloud sql instances list --filter="region:us-central1" --format="table(name,databaseVersion,state)"`.

## beta / alpha

Most workflows run on the GA `gcloud sql` surface. A few capabilities are surfaced
under `beta`/`alpha`:

- `gcloud beta sql connect` — connects through the Cloud SQL proxy; recommended when
  connecting from an IPv6 address or under `restrictPublicIP`/`restrictAuthorizedNetworks`
  org policies (per the GA `connect` help text).
- `gcloud beta sql backups restore` — the recommended replacement for the deprecated
  `gcloud sql instances restore-backup`.
- `gcloud beta sql backups delete` — delete-by-ID variant referenced by the official
  backup how-to guides.

## Official documentation

- [Cloud SQL documentation](https://cloud.google.com/sql/docs) — product docs home: overviews, guides, and API reference.
- [gcloud sql CLI reference](https://cloud.google.com/sdk/gcloud/reference/sql) — full command/flag reference for this group.
- [Create a MySQL instance](https://cloud.google.com/sql/docs/mysql/create-instance) — gcloud/Console/Terraform create flow and key flags.
- [Create a PostgreSQL instance](https://cloud.google.com/sql/docs/postgres/create-instance) — PostgreSQL-specific create notes.
- [Create a SQL Server instance](https://cloud.google.com/sql/docs/sqlserver/create-instance) — SQL Server create flow (requires `--root-password`).
- [MySQL quickstart](https://cloud.google.com/sql/docs/mysql/quickstart) — enable the API, create an instance, and connect.
- [Connect with gcloud sql connect](https://cloud.google.com/sql/docs/mysql/connect-instance-cloud-shell) — opening a client session.
- [Backing up an instance](https://cloud.google.com/sql/docs/mysql/backup-recovery/backing-up) — on-demand and automated backup management.
- [Create read replicas](https://cloud.google.com/sql/docs/mysql/replication/create-replica) — read replica and cross-region options.
- [IAM roles for Cloud SQL](https://cloud.google.com/sql/docs/mysql/iam-roles) — predefined roles and recommended assignments.

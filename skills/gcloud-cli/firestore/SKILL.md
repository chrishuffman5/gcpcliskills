---
name: gcloud-firestore
description: >-
  Cloud Firestore via gcloud (`gcloud firestore`). Manage your Cloud Firestore resources — backups, databases, fields, indexes, locations, operations, user-creds.
---

# gcloud firestore — Cloud Firestore

## Overview
Cloud Firestore is a serverless, NoSQL document database built for automatic scaling and high availability. The `gcloud firestore` command group manages the database resources and admin operations — creating and configuring databases (Native or Datastore mode), exporting/importing data to Cloud Storage, scheduling backups and restoring from them, and managing composite indexes, field indexes, and TTL settings. Reach for it for control-plane and admin tasks; document reads/writes go through the client SDKs or REST/gRPC APIs, not gcloud.

## Quick reference — common workflows

### 1. Create a Firestore Native database
```bash
# One-time: enable the API
gcloud services enable firestore.googleapis.com

# See which locations are available
gcloud firestore locations list --format="table(locationId, displayName)"

# Create the (default) Native-mode database in a location
gcloud firestore databases create --location=nam5

# Create a named database with delete protection and PITR enabled
gcloud firestore databases create \
  --database=mydb \
  --location=us-central1 \
  --delete-protection \
  --enable-pitr

# Confirm it was created
gcloud firestore databases describe --database=mydb
```

### 2. Export and import data (to/from Cloud Storage)
```bash
# Export all collection groups to a GCS bucket prefix
gcloud firestore export gs://my-backup-bucket/firestore-export

# Export specific collection groups asynchronously
gcloud firestore export gs://my-backup-bucket/firestore-export \
  --collection-ids='users','orders' \
  --async

# Watch the operation, then import it back
gcloud firestore operations list
gcloud firestore import gs://my-backup-bucket/firestore-export \
  --collection-ids='users','orders'
```

### 3. Schedule backups and restore
```bash
# Daily backups with 7-day retention
gcloud firestore backups schedules create \
  --database=mydb \
  --retention=7d \
  --recurrence=daily

# Weekly backups on Mondays with 14-day retention
gcloud firestore backups schedules create \
  --database=mydb \
  --retention=14d \
  --recurrence=weekly \
  --day-of-week=MON

# List backups in a region, then restore one into a new database
gcloud firestore backups list --location=us-central1 \
  --format="table(name, database, state)"
gcloud firestore databases restore \
  --source-backup=projects/PROJECT_ID/locations/us-central1/backups/BACKUP_ID \
  --destination-database=mydb-restored
```

### 4. Manage composite and field indexes
```bash
# Create a composite index on the Events collection group
gcloud firestore indexes composite create \
  --collection-group=Events \
  --field-config=field-path=user-id,order=descending \
  --field-config=field-path=timestamp,order=descending

# List composite indexes, then describe / delete one by ID
gcloud firestore indexes composite list
gcloud firestore indexes composite describe INDEX_ID
gcloud firestore indexes composite delete INDEX_ID

# Disable all indexes on a single field (single-field exemption)
gcloud firestore indexes fields update timestamp \
  --collection-group=Events --disable-indexes
```

### 5. Bulk delete documents
```bash
# Delete all documents in all collection groups
gcloud firestore bulk-delete

# Delete specific collection groups asynchronously, then monitor
gcloud firestore bulk-delete \
  --collection-ids='sessions','temp-data' --async
gcloud firestore operations list
```

### 6. Manage multiple databases
```bash
# List databases (optionally including soft-deleted ones)
gcloud firestore databases list
gcloud firestore databases list --show-deleted

# Enable PITR on an existing database
gcloud firestore databases update --database=mydb --enable-pitr

# Clone a database to a new one at a past point in time
gcloud firestore databases clone \
  --source-database=projects/PROJECT_ID/databases/mydb \
  --snapshot-time=2026-05-01T10:00:00.00Z \
  --destination-database=mydb-clone

# Delete a database
gcloud firestore databases delete --database=mydb-clone
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `firestore backups` | [`backups.md`](backups.md) | 8 | Manage backups and backup schedules for Cloud Firestore |
| `firestore databases` | [`databases.md`](databases.md) | 9 | Create and manage Cloud Firestore databases (create, clone, restore, update, delete) |
| `firestore fields` | [`fields.md`](fields.md) | 2 | Manage field metadata — Time-to-live (TTL) configuration |
| `firestore indexes` | [`indexes.md`](indexes.md) | 7 | Manage composite indexes and single-field index settings |
| `firestore locations` | [`locations.md`](locations.md) | 1 | List locations available to Cloud Firestore |
| `firestore operations` | [`operations.md`](operations.md) | 4 | Manage long-running admin operations (list, describe, cancel, delete) |
| `firestore user-creds` | [`user-creds.md`](user-creds.md) | 7 | Manage MongoDB-compatible user credentials for a database |

Top-level commands (see [`_commands.md`](_commands.md)): `gcloud firestore bulk-delete`, `gcloud firestore export`, `gcloud firestore import`. The full one-line index of all 41 commands is in [`index.md`](index.md).

## Common flags & tips
- **`--database`** selects which database to act on. Most commands default to `(default)` (the project's first/unnamed database); pass `--database=NAME` for named databases. Backups schedules, `databases restore`, `databases delete`, and `user-creds` commands require it explicitly.
- **`--location`** is required for `databases create` and the `backups` list/describe/delete commands. Run `gcloud firestore locations list` to see valid IDs (regional like `us-central1`, or multi-region like `nam5`/`eur3`).
- **Long-running operations:** `export`, `import`, `bulk-delete`, `databases update`, and `indexes fields update` accept `--async` to return immediately. Track them with `gcloud firestore operations list` and `gcloud firestore operations describe NAME`.
- **Indexes by ID vs flags:** `indexes composite describe`/`delete` take the index ID as a positional argument; `indexes fields describe`/`update` take the field path as a positional plus `--collection-group`.
- **`--field-config`** (on `indexes composite create`) is repeatable — supply one per field, each with `field-path=` and exactly one of `order=` (`ascending`/`descending`), `array-config=contains`, or `vector-config=`.
- **Filtering/formatting:** list commands support standard `--filter` / `--format`, e.g. `gcloud firestore operations list --filter="done:true"` or `gcloud firestore indexes composite list --filter=COLLECTION_GROUP:Events`.
- **Data protection:** `--delete-protection` blocks deletion until disabled (`--no-delete-protection`); `--enable-pitr` turns on Point-in-Time Recovery. `databases delete` also accepts `--etag` for optimistic concurrency.

## beta / alpha
The `gcloud beta firestore` and `gcloud alpha firestore` surfaces mirror the GA command groups (backups, databases, fields, indexes, locations, operations, user-creds) and the same top-level commands; no command groups are exclusive to beta or alpha. Newer database-create capabilities — `--edition=enterprise`, MongoDB-compatible data access (`--enable-mongodb-compatible-data-access`, plus `databases connection-string` / `databases ping`), and CMEK (`--kms-key-name`) — may require allowlisting or beta/alpha promotion in some projects/regions. If a GA command fails on these, retry under `gcloud beta firestore`.

## Official documentation
- Cloud Firestore documentation (product docs home): https://cloud.google.com/firestore/docs
- gcloud firestore CLI reference: https://cloud.google.com/sdk/gcloud/reference/firestore
- Quickstart (server client library): https://cloud.google.com/firestore/docs/quickstart-servers
- Create and manage databases: https://cloud.google.com/firestore/docs/manage-databases
- Export and import data: https://cloud.google.com/firestore/docs/manage-data/export-import
- Back up and restore: https://cloud.google.com/firestore/docs/backups
- Manage indexes: https://cloud.google.com/firestore/docs/query-data/indexing
- Data model (collections, documents, subcollections): https://cloud.google.com/firestore/docs/data-model
- Available locations: https://cloud.google.com/firestore/docs/locations
- IAM roles and access control: https://cloud.google.com/firestore/docs/security/iam

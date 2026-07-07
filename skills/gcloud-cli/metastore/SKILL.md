---
name: gcloud-metastore
description: >-
  Dataproc Metastore via gcloud (`gcloud metastore`). Manage Dataproc Metastore resources — federations, locations, operations, services.
---

# gcloud metastore — Dataproc Metastore

## Overview

Dataproc Metastore is a fully managed, highly available Apache Hive metastore (HMS) on Google Cloud. It provides a centralized metadata repository (schemas, partitions, statistics) that is shared across data-processing engines such as Hive, Spark, and Presto, and integrates with Dataproc, BigQuery, and Data Catalog. Reach for `gcloud metastore` to create and manage metastore *services*, back up and restore their metadata, import/export metadata to Cloud Storage, and stitch multiple metastores together with *federations*.

## Quick reference — common workflows

### 1. Enable the API and create a service
```bash
gcloud services enable metastore.googleapis.com

# Create a service (defaults: port 9083, thrift endpoint, mysql backend, stable channel)
gcloud metastore services create my-metastore-service \
    --location=us-central1

# Create with a non-default port and a specific Hive metastore version
gcloud metastore services create my-metastore-service \
    --location=us-central1 \
    --port=9090 \
    --hive-metastore-version=3.1.2

# Verify, then list
gcloud metastore services describe my-metastore-service --location=us-central1
gcloud metastore services list --location=us-central1
```

### 2. Update a service — labels, autoscaling, scheduled backups
```bash
# Change port and add labels
gcloud metastore services update my-metastore-service \
    --location=us-central1 \
    --port=8080 \
    --update-labels=env=prod,team=data

# Enable autoscaling (defaults: min 0.1, max 6.0)
gcloud metastore services update my-metastore-service \
    --location=us-central1 \
    --autoscaling-enabled \
    --min-scaling-factor=0.5 \
    --max-scaling-factor=3.0

# Turn on scheduled backups
gcloud metastore services update my-metastore-service \
    --location=us-central1 \
    --enable-scheduled-backup \
    --scheduled-backup-cron="0 2 * * *" \
    --scheduled-backup-location=gs://my-bucket/backups
```

### 3. Back up and restore
```bash
# Create a manual backup
gcloud metastore services backups create my-backup \
    --service=my-metastore-service \
    --location=us-central1 \
    --description="pre-migration backup"

gcloud metastore services backups list --service=my-metastore-service --location=us-central1

# Restore (metadata-only is the default; use full for metadata + config)
gcloud metastore services restore my-metastore-service \
    --location=us-central1 \
    --backup=my-backup \
    --restore-type=full

# Or restore from raw backup artifacts in Cloud Storage
gcloud metastore services restore my-metastore-service \
    --location=us-central1 \
    --backup-location=gs://my-bucket/backups/my-backup
```

### 4. Export / import metadata via Cloud Storage
```bash
# Export (defaults to a MySQL dump; use --dump-type=avro for Avro)
gcloud metastore services export gcs my-metastore-service \
    --location=us-central1 \
    --destination-folder=gs://my-bucket/metadata-export

# Import a dump, then watch the long-running operation
gcloud metastore services import gcs my-metastore-service \
    --location=us-central1 \
    --import-id=my-import \
    --database-dump=gs://my-bucket/dump.sql \
    --dump-type=mysql

gcloud metastore operations list --location=us-central1
gcloud metastore operations wait OPERATION_ID --location=us-central1
```

### 5. Create and manage a federation
```bash
# Federate two backend metastores (RANK=BACKEND pairs; rank resolves name collisions)
gcloud metastore federations create my-federation \
    --location=us-central1 \
    --hive-metastore-version=3.1.2 \
    --backends=1=dpms:my-metastore-service,2=dpms:projects/my-project/locations/us-central1/services/other-service

gcloud metastore federations describe my-federation --location=us-central1

# Replace the backend set
gcloud metastore federations update my-federation \
    --location=us-central1 \
    --update-backends=1=dpms:my-metastore-service
```

### 6. Grant IAM access on a service
```bash
gcloud metastore services add-iam-policy-binding my-metastore-service \
    --location=us-central1 \
    --member='user:analyst@example.com' \
    --role='roles/metastore.editor'

gcloud metastore services get-iam-policy my-metastore-service --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `metastore federations` | [`federations.md`](federations.md) | 9 | manage Dataproc Metastore federations |
| `metastore locations` | [`locations.md`](locations.md) | 2 | get information about Dataproc Metastore locations |
| `metastore operations` | [`operations.md`](operations.md) | 5 | manage Dataproc Metastore operations |
| `metastore services` | [`services.md`](services.md) | 24 | manage services, backups, export & import |

See [`index.md`](index.md) for a one-line index of all 40 GA commands.

## Common flags & tips

- **Location is required almost everywhere.** Pass `--location=us-central1` (a Google Cloud region) or set a default with `gcloud config set metastore/location us-central1`. Most `list` commands accept `--location=-` to span all locations.
- **Resource scoping for backups.** `services backups *` commands need both `--service` and `--location` (or a fully qualified backup name).
- **Long-running operations.** `create`, `update`, `delete`, `restore`, `export`, `import`, and the metadata-mutation commands return an operation. Add `--async` to return immediately, then track it with `gcloud metastore operations describe|wait OPERATION_ID --location=...`.
- **Service creation knobs:** `--database-type` (`mysql` default / `spanner`), `--endpoint-protocol` (`thrift` default / `grpc`), `--release-channel` (`stable` default / `canary`), `--port` (default `9083`), `--deletion-protection`, and `--encryption-kms-key` for CMEK.
- **Sizing is mutually exclusive:** choose one of `--tier`, `--instance-size`, `--scaling-factor`, or the autoscaling pair `--min-scaling-factor` / `--max-scaling-factor` (with `--autoscaling-enabled`).
- **Metadata mutation commands** use underscore-style flags: `alter-metadata-resource-location` takes `--resource_name` + `--location_uri`; `move-table-to-database` takes `--table_name`, `--source_db_name`, `--destination_db_name`.
- **Ad hoc metadata queries:** `gcloud metastore services query-metadata my-metastore-service --location=us-central1 --query="show tables;"`.
- **Useful filters/formats:**
  - `gcloud metastore services list --location=us-central1 --filter="state=ACTIVE" --format="table(name, port, state)"`
  - `gcloud metastore operations list --location=us-central1 --filter="done=false" --limit=5`

## beta / alpha

`gcloud beta metastore` and `gcloud alpha metastore` expose the same four top-level groups as GA (`federations`, `locations`, `operations`, `services`), but `gcloud beta metastore services` adds subgroups not present in GA:

- `services databases` — manage databases within a service's metastore.
- `services imports` — manage metadata import jobs.
- `services migrations` — manage the Managed Migration workflow.

The GA `services` surface covers backups, export, and import (`services import gcs` / `services export gcs`) but not the `databases` or `migrations` subgroups. See the [gcloud beta metastore services reference](https://cloud.google.com/sdk/gcloud/reference/beta/metastore/services).

## Official documentation

- [Dataproc Metastore documentation home](https://cloud.google.com/dataproc-metastore/docs) — guides, reference, and resources for the product.
- [Dataproc Metastore overview](https://cloud.google.com/dataproc-metastore/docs/overview) — capabilities, versions, and integrations.
- [Create a service and connect a cluster (quickstart)](https://cloud.google.com/dataproc-metastore/docs/create-service-cluster) — end-to-end getting-started guide.
- [Create a Dataproc Metastore service](https://cloud.google.com/dataproc-metastore/docs/create-service) — how-to covering all service options.
- [IAM and access control](https://cloud.google.com/dataproc-metastore/docs/iam-and-access-control) — policy model for services, backups, and federations.
- [Predefined IAM roles](https://cloud.google.com/dataproc-metastore/docs/iam-roles) — the `roles/metastore.*` roles reference.
- [gcloud metastore CLI reference](https://cloud.google.com/sdk/gcloud/reference/metastore) — full command/flag reference (GA).
- [gcloud beta metastore CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/metastore) — beta surface, including `services databases`, `imports`, and `migrations` subgroups.

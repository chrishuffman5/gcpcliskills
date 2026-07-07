---
name: gcloud-datastore
description: >-
  Firestore in Datastore mode (Cloud Datastore) via gcloud (`gcloud datastore`). Manage your Cloud Datastore resources — indexes, operations.
---

# gcloud datastore — Firestore in Datastore mode (Cloud Datastore)

## Overview
`gcloud datastore` manages administrative operations for Firestore in Datastore mode — a serverless, highly-scalable NoSQL document database with automatic scaling and ACID transactions. The CLI does not read or write entity data; it handles bulk **export/import** to Cloud Storage, **composite index** definition (via a local `index.yaml`), and the **long-running operations** those tasks create. Reach for it when scripting backups/migrations, deploying index configuration, or monitoring and cancelling admin operations.

## Quick reference — common workflows

### 1. Enable the API
```bash
gcloud services enable datastore.googleapis.com
```

### 2. Export entities to Cloud Storage
```bash
# Export all namespaces and kinds in the current project (waits for completion)
gcloud datastore export gs://exampleBucket

# Export specific kinds from a specific namespace
gcloud datastore export gs://exampleBucket \
    --kinds='exampleKind','otherKind' --namespaces='exampleNs' \
    --project='exampleProject'

# Fire-and-forget, then track via operations
gcloud datastore export gs://exampleBucket --async
gcloud datastore operations list
```

### 3. Import entities from a previous export
```bash
# Import using the overall_export_metadata file produced by an export
gcloud datastore import \
    gs://exampleBucket/exampleExport/exampleExport.overall_export_metadata

# Import only one kind, without waiting
gcloud datastore import \
    gs://exampleBucket/exampleExport/exampleExport.overall_export_metadata \
    --kinds='exampleKind' --async
```

### 4. Deploy and inspect composite indexes
```bash
# Create indexes defined in a local index.yaml (default database)
gcloud datastore indexes create ~/myapp/index.yaml

# Target a non-default database
gcloud datastore indexes create ~/myapp/index.yaml --database='testdb'

# List indexes and inspect one
gcloud datastore indexes list
gcloud datastore indexes describe exampleIndexId
```

### 5. Remove unused indexes
```bash
# Delete any composite index NOT present in your local index.yaml
gcloud datastore indexes cleanup ~/myapp/index.yaml
```

### 6. Monitor and manage long-running operations
```bash
# List all, or filter to export operations / a specific kind / a label
gcloud datastore operations list
gcloud datastore operations list --filter='type:export_entities'
gcloud datastore operations list --filter='type:export_entities AND kind:MyKind'
gcloud datastore operations list --filter='labels.run = daily'

# Describe, cancel, or delete an operation by id
gcloud datastore operations describe exampleId
gcloud datastore operations cancel exampleId
gcloud datastore operations delete exampleId
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `datastore` (top-level) | [`_commands.md`](_commands.md) | 2 | `export` / `import` entities to and from Cloud Storage |
| `datastore indexes` | [`indexes.md`](indexes.md) | 4 | manage composite indexes from a local `index.yaml` |
| `datastore operations` | [`operations.md`](operations.md) | 4 | manage long-running admin operations |

See [`index.md`](index.md) for a one-line index of all 10 commands.

## Common flags & tips
- **Async pattern:** `export` and `import` block until the operation completes. Add `--async` to return immediately; then track progress with `gcloud datastore operations list` / `describe`.
- **Scoping export/import:** `--kinds='K1','K2'` and `--namespaces='N1','N2'` narrow the operation; omit them to include everything. Use the special token `'(default)'` to reference the default namespace, e.g. `--namespaces='(default)','customers'`.
- **Labeling:** tag operations with `--operation-labels=KEY=VALUE,...` for later filtering.
- **Import input:** `INPUT_URL` must be the `*.overall_export_metadata` file written by a prior export (the `output_url` shown in `operations describe`).
- **Multiple databases:** `indexes create` / `indexes cleanup` accept `--database='DBNAME'` to target a non-default database; without it, the `(default)` database is used.
- **Operation filters** (`operations list --filter=`) support the fields `kind`, `namespace`, `type`, and `labels.[KEY]`; `type` is `export_entities` or `import_entities`, and only `AND` is supported. Example: `--filter='type:export_entities AND kind:Customer'`.
- **Output shaping:** `indexes list` and `operations list` support `--limit`, `--page-size`, `--sort-by`, and `--uri`. Add `--format=json` to any command for scriptable output, e.g. `gcloud datastore export gs://exampleBucket --kinds='exampleKind' --format=json`.
- **IAM:** export/import needs `roles/datastore.importExportAdmin` plus Cloud Storage access (`roles/storage.objectAdmin` or `roles/storage.admin`) on the target bucket; index management needs `roles/datastore.indexAdmin`.

## beta / alpha
The `gcloud beta datastore` and `gcloud alpha datastore` surfaces mirror the GA command set (same `indexes` and `operations` subgroups and the same top-level `export` / `import` commands). No commands are exclusive to beta or alpha; the only difference is the pre-release designation, meaning behavior may change without notice.

- Beta reference: https://cloud.google.com/sdk/gcloud/reference/beta/datastore
- Alpha reference: https://cloud.google.com/sdk/gcloud/reference/alpha/datastore

## Official documentation
- [Firestore in Datastore mode — docs home](https://cloud.google.com/datastore/docs) — product overview, concepts, and how-to guides.
- [Exporting and importing entities](https://cloud.google.com/datastore/docs/export-import-entities) — full export/import workflow including the Cloud Storage metadata file.
- [Indexes](https://cloud.google.com/datastore/docs/concepts/indexes) — built-in vs. composite indexes and query requirements.
- [Index configuration (`index.yaml`)](https://cloud.google.com/datastore/docs/tools/indexconfig) — defining, creating, and monitoring composite indexes.
- [Access control with IAM](https://cloud.google.com/datastore/docs/access/iam) — roles and permissions for Datastore mode.
- [REST API reference](https://cloud.google.com/datastore/docs/reference/rest) — `datastore.googleapis.com` endpoint and resources.
- [gcloud datastore CLI reference](https://cloud.google.com/sdk/gcloud/reference/datastore) — authoritative command/flag reference.

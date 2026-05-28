# gcloud bq — BigQuery (Migration Service)

## Overview

> **Important:** `gcloud bq` is NOT the general-purpose BigQuery CLI. The full-featured
> BigQuery command-line tool — `query`, `load`, `extract`, `mk`, `rm`, `show`, etc. — is the
> **separate, standalone `bq` command** bundled with the Cloud SDK. It is entirely distinct
> from `gcloud bq` and is invoked as plain `bq ...` (e.g. `bq query`, `bq mk`), not `gcloud bq ...`.

The GA `gcloud bq` group is a small, focused surface that covers **only BigQuery Migration
Service workflows** via the `migration-workflows` subgroup (4 commands: create, delete,
describe, list). Reach for it when you are migrating an existing data warehouse (Redshift,
Teradata, Hive, Snowflake, etc.) to BigQuery and want to drive batch SQL translation and
migration tasks from a config file. For datasets, tables, jobs, and SQL translation via
gcloud, see the much broader `gcloud alpha bq` surface (see [beta / alpha](#beta--alpha)).

## Quick reference — common workflows

### 1. Enable the API (one-time)
```bash
# Projects created after 2022-02-15 have this enabled automatically.
gcloud services enable bigquerymigration.googleapis.com
```

### 2. Create a migration workflow from a config file
```bash
# Synchronously in EU (wait for completion)
gcloud bq migration-workflows create \
    --location=EU \
    --config-file=config_file.yaml \
    --no-async

# Asynchronously in US (return immediately)
gcloud bq migration-workflows create \
    --location=us \
    --config-file=config_file.yaml \
    --async
```

### 3. List workflows in a location
```bash
gcloud bq migration-workflows list --location=eu

# Sort by a field and cap the result count
gcloud bq migration-workflows list --location=us --sort-by=name --limit=20
```

### 4. Describe (inspect) a workflow
```bash
# Fully-qualified resource name
gcloud bq migration-workflows describe \
    projects/123/locations/eu/workflows/1234

# Or an ID plus an explicit location
gcloud bq migration-workflows describe 1234 --location=eu
```

### 5. Delete a workflow
```bash
# Fully-qualified resource name
gcloud bq migration-workflows delete \
    projects/123/locations/eu/workflows/1234

# Or an ID plus an explicit location
gcloud bq migration-workflows delete 1234 --location=eu
```

### 6. Full lifecycle — create, find, inspect, clean up
```bash
gcloud services enable bigquerymigration.googleapis.com

gcloud bq migration-workflows create \
    --location=us --config-file=my-migration-config.yaml --async

gcloud bq migration-workflows list --location=us

gcloud bq migration-workflows describe \
    projects/123/locations/us/workflows/WORKFLOW_ID

gcloud bq migration-workflows delete \
    projects/123/locations/us/workflows/WORKFLOW_ID
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `bq migration-workflows` | [`migration-workflows.md`](migration-workflows.md) | 4 | manage Migration Workflow resources |

See [`index.md`](index.md) for a one-line index of all 4 GA commands.

## Common flags & tips

- **`--location` is required** for every command. Use the BigQuery region/multi-region the
  workflow lives in (e.g. `us`, `eu`). The value is case-insensitive in the examples
  (`EU` and `eu` both appear in the official help).
- **Workflow identity (`describe` / `delete`):** pass either a fully-qualified resource name
  (`projects/PROJECT/locations/LOCATION/workflows/WORKFLOW_ID`) — which sets project and
  location implicitly — or a bare workflow ID together with `--location` (and `--project`
  or the `core/project` property for the project).
- **`--async` vs `--no-async` (`create` only):** `--async` returns immediately; `--no-async`
  (the default behaviour shown in the official example) blocks until the operation completes.
- **`--config-file` (`create` only):** path to the migration workflow YAML config that
  defines the translation/migration tasks. There is no inline alternative — the config file
  is required.
- **Listing:** `migration-workflows list` supports the standard gcloud paging/sorting flags
  `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri`.
- **Output shaping:** combine with global flags, e.g.
  `gcloud bq migration-workflows list --location=us --format="table(name, state)"` or
  `--format=json`. Use `--uri` to emit just the resource URIs for scripting.

## beta / alpha

- **`gcloud beta bq`** — same surface as GA: `migration-workflows` only (create, delete,
  describe, list). The beta variants exist for testing pre-GA behaviour.
- **`gcloud alpha bq`** — a significantly broader surface that is **not** in GA/beta:
  - `alpha bq datasets` — create, delete, describe, list, update, config export
  - `alpha bq tables` — copy, create, delete, describe, insert, list, show-rows, update, config export
  - `alpha bq jobs` — interact with and manage BigQuery jobs
  - `alpha bq migration-workflows` — create, delete, describe, list (same as GA)
  - `alpha bq translation` — translate SQL from a source dialect to GoogleSQL (invite-only early access)

  Run `gcloud alpha bq --help` to confirm current availability; alpha commands may change
  without notice.

## Official documentation

- [BigQuery docs home](https://cloud.google.com/bigquery/docs) — fully managed, petabyte-scale analytics data warehouse.
- [BigQuery Migration Service overview](https://cloud.google.com/bigquery/docs/migration-intro) — assessment, SQL translation, data transfer, and validation.
- [Batch SQL Translator](https://cloud.google.com/bigquery/docs/batch-sql-translator) — bulk conversion of SQL scripts (Redshift, Hive, Teradata, etc.) to GoogleSQL.
- [gcloud bq CLI reference](https://cloud.google.com/sdk/gcloud/reference/bq) — GA surface (migration-workflows only).
- [gcloud alpha bq reference](https://cloud.google.com/sdk/gcloud/reference/alpha/bq) — full surface: datasets, tables, jobs, translation, migration-workflows.

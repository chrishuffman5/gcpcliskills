---
name: bq-cli
description: >-
  BigQuery via the standalone `bq` CLI (plain `bq ...`, NOT `gcloud bq`). Queries, load/extract jobs, datasets, tables, views, streaming inserts, job control, and table/view IAM.
---

# bq — BigQuery command-line tool (standalone, not gcloud)

## Overview

`bq` is the Python-based, general-purpose BigQuery command-line tool bundled with the Google Cloud CLI (and preinstalled in Cloud Shell). It is a **standalone tool invoked as plain `bq ...`** — e.g. `bq query`, `bq load`, `bq mk` — **not** `gcloud bq ...`. It covers the day-to-day BigQuery surface: running queries, loading and extracting data, creating/updating/deleting datasets, tables, views and routines, inspecting jobs, streaming inserts, IAM policies, reservations, connections, and Data Transfer Service configs.

> **Do not confuse with `gcloud bq`.** The GA `gcloud bq` command group covers *only* BigQuery Migration Service workflows (`gcloud bq migration-workflows` — 4 commands). Everything else BigQuery on the CLI is this standalone `bq` tool. See [`../bq/SKILL.md`](../bq/SKILL.md) for the `gcloud bq` surface.

Command format: `bq [--global_flags] COMMAND [--command_flags] [ARGUMENTS]` — global flags go **before** the command name, command-specific flags after it. `bq` respects the active gcloud credentials and, by default, the gcloud config (`--use_gcloud_config=true`), so `gcloud config set project` / `gcloud auth login` (or service-account impersonation via `gcloud config set auth/impersonate_service_account`) carry over.

## Global flags

Usable with any command, where applicable (full list: `bq --help`):

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--project_id` | PROJECT | gcloud config | Default project to use for requests. |
| `--location` | LOCATION | | Region or multi-region (e.g. `US`, `EU`, `us-central1`). Required for `bq cancel` and `bq show -j`; optional for `query`, `cp`, `load`, `extract`, `partition`, `update`, `wait`, and for `mk`/`ls` with reservation/commitment/dataset flags. Ignored by other commands. |
| `--dataset_id` | PROJECT:DATASET or DATASET | | Default dataset for requests, so table args can be bare table names. Ignored when not applicable. |
| `--format` | `none`\|`json`\|`prettyjson`\|`csv`\|`sparse`\|`pretty` | per command | Output format. `pretty` (formatted table), `sparse` (simpler table), and `prettyjson` (readable JSON) are human-oriented; `json` (compact JSON) and `csv` are for passing to other programs. If unset, a format is chosen per command. |
| `-q`, `--quiet` | boolean | `false` | Suppress status updates while jobs run — use in scripts. |
| `--apilog` | file path, `stdout`, `stderr` | off | Log all API requests/responses to a file or stream (useful for debugging; `-` or `stdout` prints to console). |
| `--job_id` | JOB_ID | generated | Explicit job ID for job-launching commands (`cp`, `extract`, `load`, `query`). Use `--fingerprint_job_id=true` instead to derive the ID from the job config (prevents accidental duplicate runs). |
| `-sync`, `--synchronous_mode` | boolean | `true` | If `true`, wait for command completion and use the **job completion status** as the exit code. If `false` (`--nosync`), return immediately after job creation and use the success of **job creation** as the exit code. |
| `--headless` | boolean | `false` | Run without user interaction: never break into a debugger, less informational printing. Set in automated environments. |
| `--bigqueryrc` | PATH | `~/.bigqueryrc` | Path to the config file with default flag values. Resolution order: `--bigqueryrc` flag, `BIGQUERYRC` env var, `~/.bigqueryrc`. |
| `--api` | ENDPOINT | `https://bigquery.googleapis.com` | API endpoint to call. |
| `--job_property` | KEY:VALUE | | Extra key-value pair for the job configuration `properties` field (repeatable). |
| `--debug_mode` | boolean | `false` | Show tracebacks on Python exceptions. |
| `--httplib2_debuglevel` | integer | | Log HTTP requests/responses to stderr when > 0. |

## Resource naming

`bq` arguments use **`PROJECT:DATASET.TABLE`** — colon between project and dataset, period between dataset and table (e.g. `myProject:myDataset.myTable`). Omit the project to use the default project (`myDataset.myTable`). Inside GoogleSQL query text, use periods everywhere: `` `myProject.myDataset.myTable` ``. Quote identifiers with backticks if they contain characters other than letters/digits/underscores or reserved keywords. A trailing `:` or `.` on an identifier passed to `ls` marks it as a project or dataset. The equals sign in `--flag=value` is optional (`--flag value` also works).

## Quick reference — common workflows

### 1. Run a GoogleSQL query

```bash
# ALWAYS pass --nouse_legacy_sql (or --use_legacy_sql=false); bq defaults to legacy SQL
bq query --nouse_legacy_sql \
    'SELECT word, SUM(word_count) AS count
     FROM `bigquery-public-data.samples.shakespeare`
     GROUP BY word ORDER BY count DESC LIMIT 10'

# Machine-readable results, more rows
bq --format=prettyjson query --nouse_legacy_sql -n 1000 'SELECT ...'

# Query text can also come from stdin
echo 'SELECT 1' | bq query --nouse_legacy_sql
```

### 2. Parameterized query

```bash
bq query --nouse_legacy_sql \
    --parameter='min_count:INT64:100' \
    --parameter='corpus::hamlet' \
    'SELECT word FROM `bigquery-public-data.samples.shakespeare`
     WHERE corpus = @corpus AND word_count >= @min_count'
# --parameter is name:type:value; type omitted => STRING; empty name => positional
```

### 3. Dry run — estimate bytes billed without running

```bash
bq query --nouse_legacy_sql --dry_run \
    'SELECT * FROM `myproject.mydataset.mytable`'
# Prints "Query successfully validated. Assuming the tables are not modified,
# running this query will process N bytes of data."
```

### 4. Create a dataset and a table

```bash
# Dataset in a specific location, with defaults for table expiry
bq mk -d --data_location=EU --default_table_expiration=3600 \
    --description="Working dataset" mydataset

# Table with an inline schema
bq mk -t mydataset.mytable name:STRING,value:INTEGER,ts:TIMESTAMP

# Partitioned + clustered table
bq mk -t --time_partitioning_field=ts --time_partitioning_type=DAY \
    --clustering_fields=name mydataset.events name:STRING,ts:TIMESTAMP
```

### 5. Load data (CSV / JSON, schema or autodetect)

```bash
# CSV from GCS with an inline schema, skipping the header row
bq load --source_format=CSV --skip_leading_rows=1 \
    mydataset.mytable gs://mybucket/data.csv name:STRING,value:INTEGER

# Local newline-delimited JSON with schema autodetection
bq load --source_format=NEWLINE_DELIMITED_JSON --autodetect \
    mydataset.mytable ./data.json

# Replace table contents; JSON schema file
bq load --replace --source_format=CSV \
    mydataset.mytable gs://mybucket/data.csv ./schema.json
```

### 6. Extract a table to Cloud Storage

```bash
bq extract mydataset.mytable gs://mybucket/export/table.csv

# Compressed newline-delimited JSON
bq extract --destination_format=NEWLINE_DELIMITED_JSON --compression=GZIP \
    mydataset.mytable 'gs://mybucket/export/table_*.json.gz'
```

### 7. Copy tables

```bash
bq cp mydataset.mytable mydataset2.mytable_copy      # prompts unless -f
bq cp -a mydataset.src mydataset.dest                # append
bq cp --snapshot --expiration=86400 mydataset.t mydataset.t_snap  # snapshot
bq cp --clone mydataset.t mydataset.t_clone          # clone
```

### 8. List, show, and preview

```bash
bq ls                                  # datasets in default project
bq ls mydataset                        # tables in a dataset
bq ls -p -n 1000                       # projects
bq show mydataset.mytable              # table details
bq show --schema --format=prettyjson mydataset.mytable   # schema as JSON
bq head -n 10 mydataset.mytable        # first 10 rows
bq head -s 5 -n 10 -c 'name,value' mydataset.mytable     # skip 5, select fields
```

### 9. Stream rows into a table

```bash
bq insert mydataset.mytable ./rows.json        # newline-delimited JSON file
echo '{"name":"a","value":1}' | bq insert mydataset.mytable
```

### 10. Manage jobs

```bash
bq ls -j -n 20                                   # recent jobs in project
bq ls -j --filter='states:RUNNING,PENDING' proj  # running/pending jobs
bq show -j --location=US job_id                  # job details
bq wait --fail_on_error job_id 300               # wait up to 300s, exit 1 on failure
bq cancel job_id                                 # cancel and wait
bq --nosync cancel job_id                        # request cancel, return now
```

### 11. IAM on tables and views

```bash
bq get-iam-policy mydataset.mytable

bq add-iam-policy-binding \
    --member='user:someone@example.com' \
    --role='roles/bigquery.dataViewer' \
    mydataset.mytable

bq remove-iam-policy-binding \
    --member='user:someone@example.com' \
    --role='roles/bigquery.dataViewer' \
    mydataset.mytable

bq set-iam-policy mydataset.mytable policy.json   # full-policy replace (etag-checked)
```

### 12. External tables via mkdef

```bash
# Emit a JSON external-table definition, then create the table with it
bq mkdef --source_format=CSV --autodetect 'gs://mybucket/data/*.csv' > tabledef.json
bq mk --external_table_definition=tabledef.json mydataset.exttable

# Or inline: schema@format=uri
bq mk --external_table_definition='name:STRING@CSV=gs://mybucket/data.csv' \
    mydataset.exttable
```

## Commands

All 26 commands are documented in [`commands.md`](commands.md); see [`index.md`](index.md) for the one-line list. Core surface: `query`, `load`, `extract`, `cp`, `mk`, `mkdef`, `update`, `rm`, `show`, `ls`, `head`, `insert`, `wait`, `cancel`, `partition`, `truncate`, `undelete`, `get-iam-policy`, `set-iam-policy`, `add-iam-policy-binding`, `remove-iam-policy-binding`, `init`, `shell`, `info`, `version`, `help`.

## Common flags & tips

- **The legacy SQL default gotcha.** With no dialect prefix in the query text, `bq query` defaults to **legacy SQL**, not GoogleSQL. Always pass `--nouse_legacy_sql` (or `--use_legacy_sql=false`), or set it once in `.bigqueryrc` (see below). Note: the `--noFLAG` spelling is **not allowed inside `.bigqueryrc`** — use `--use_legacy_sql=false` there.
- **Boolean flags** accept four forms: `--flag` (true), `--flag=true`, `--flag=false`, `--noflag` (false). Short single-dash spellings from the help also work (`-q`, `-sync`, `-n`, `-j`, `-t`, `-d`, ...).
- **Machine-readable output:** `--format=prettyjson` (readable) or `--format=json` (compact) on any command; `--format=csv` for tabular data. `--format=prettyjson` on `show -j` exposes the `reason` property of errors — the first thing to check when troubleshooting.
- **Scripting:** use `--quiet` to suppress in-progress job status lines, keep `--synchronous_mode=true` (default) so the exit code reflects **job completion** status; with `--nosync` the exit code only reflects job **creation** and you must `bq wait --fail_on_error JOB_ID` yourself. Nonzero exit means failure.
- **`.bigqueryrc` config file** (`~/.bigqueryrc` by default, overridable with `BIGQUERYRC` or `--bigqueryrc`): global flags at the top without a header, command-specific flags under a `[command]` section header, one flag per line. Command-line flags override the file. Example:
  ```
  --location=US
  --format=prettyjson

  [query]
  --use_legacy_sql=false
  --maximum_bytes_billed=10000000
  ```
  (Creating `.bigqueryrc` via `bq init` is not recommended — write it with an editor.)
- **Cost guardrails:** `bq query --dry_run` to estimate scanned bytes; `--maximum_bytes_billed` to hard-cap a query.
- **Global flags come first:** `bq --location=us mk --reservation ...` works; `bq mk --location=us ...` places a global flag after the command and only works where the command tolerates it. Keep the documented order.
- **Getting help:** `bq help` (all commands), `bq help COMMAND` (one command's flags), `bq --help` (global flags), `bq version` (tool version).
- **Debugging:** `--apilog=stdout` logs the underlying REST calls; `--httplib2_debuglevel=1` adds HTTP wire logging; `--debug_mode=true` shows Python tracebacks.

## Official documentation

- **bq CLI reference:** https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference — syntax, global flags, and every command with flags and examples.
- **bq tool quickstart:** https://docs.cloud.google.com/bigquery/docs/quickstarts/load-data-bq — load and query data with the bq tool.
- **Specifying a JSON schema file:** https://cloud.google.com/bigquery/docs/schemas#specifying_a_json_schema_file — format used by `load`, `mk`, `mkdef`, and `update` schema arguments.
- **BigQuery docs home:** https://cloud.google.com/bigquery/docs — product documentation.
- **`gcloud bq` (Migration Service only):** [`../bq/SKILL.md`](../bq/SKILL.md) — the separate `gcloud bq migration-workflows` group.

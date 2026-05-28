# gcloud logging — Cloud Logging

## Overview

Cloud Logging is Google Cloud's fully managed service for storing, searching, analyzing, monitoring, and alerting on log data and events from Google Cloud and other sources. Use `gcloud logging` to read and write log entries, route logs to other destinations with sinks, manage log buckets / views / linked datasets, define logs-based metrics, and administer Logs Router settings. Reach for it when you need to query logs from the command line, configure log export pipelines, or script log retention and access control.

## Quick reference — common workflows

### Enable the API

```bash
gcloud services enable logging.googleapis.com
```

### 1. Read recent log entries

```bash
# ERROR-and-above entries from Compute Engine instances (last 1 day by default)
gcloud logging read "resource.type=gce_instance AND severity>=ERROR"

# Up to 50 entries in a time window, oldest first, as JSON
gcloud logging read \
    'timestamp>="2025-05-01T00:00:00Z" AND timestamp<="2025-05-01T23:59:59Z"' \
    --order=asc --limit=50 --format=json

# Read from a specific bucket + view
gcloud logging read "" \
    --bucket=my-bucket --location=global --view=_AllLogs --limit=20
```

### 2. Write a log entry (testing / simple ingestion)

```bash
# Plain-text entry
gcloud logging write my-app-log "Application started successfully" --severity=INFO

# Structured (JSON) entry
gcloud logging write my-app-log '{"event": "user_login", "user_id": "42"}' \
    --payload-type=json --severity=NOTICE

# Entry attached to a specific monitored-resource type
gcloud logging write my-app-log "Disk full warning" \
    --severity=WARNING \
    --monitored-resource-type=gce_instance \
    --monitored-resource-labels=zone=us-central1-a,instance_id=1234
```

### 3. Route logs to a destination with a sink

```bash
# Route all GCE logs to a BigQuery dataset (destination must already exist)
gcloud logging sinks create my-bq-sink \
    bigquery.googleapis.com/projects/my-project/datasets/my_dataset \
    --log-filter='resource.type="gce_instance"'

# Inspect the sink — note writerIdentity, then grant it write access on the destination
gcloud logging sinks describe my-bq-sink

# Tighten the sink's filter
gcloud logging sinks update my-bq-sink \
    --log-filter='resource.type="gce_instance" AND severity>=WARNING'

gcloud logging sinks list --limit=20
```

### 4. Create a custom log bucket and attach a scoped view

```bash
# Bucket with 365-day retention in us-central1
gcloud logging buckets create my-bucket \
    --location=us-central1 --retention-days=365 \
    --description="Long-term audit logs"

# Route audit logs into the new bucket
gcloud logging sinks create my-audit-sink \
    logging.googleapis.com/projects/my-project/locations/us-central1/buckets/my-bucket \
    --log-filter='logName:"cloudaudit.googleapis.com"'

# Expose only GCE logs from the bucket via a view, and grant access
gcloud logging views create gce-view \
    --bucket=my-bucket --location=us-central1 \
    --log-filter='resource.type="gce_instance"'
gcloud logging views add-iam-policy-binding gce-view \
    --bucket=my-bucket --location=us-central1 \
    --member='user:analyst@example.com' --role='roles/logging.viewAccessor'
```

### 5. Create and manage a logs-based metric

```bash
gcloud logging metrics create high_severity_count \
    --description="Count of high-severity log entries" \
    --log-filter="severity > WARNING"

gcloud logging metrics update high_severity_count --log-filter="severity >= ERROR"
gcloud logging metrics list --limit=10
gcloud logging metrics delete high_severity_count
```

### 6. Copy log entries to Cloud Storage (archival)

```bash
gcloud logging copy my-bucket \
    storage.googleapis.com/my-archive-bucket \
    --location=global \
    --log-filter='timestamp>="2025-01-01T00:00:00Z" AND timestamp<="2025-03-31T23:59:59Z"'

# Track the long-running copy operation (--operation-filter is required)
gcloud logging operations list --location=global \
    --operation-filter='request_type=CopyLogEntries'
gcloud logging operations describe OPERATION_ID --location=global
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `logging buckets` | [`buckets.md`](buckets.md) | 6 | Manage Cloud Logging log buckets (retention, CMEK, indexes, Log Analytics) |
| `logging links` | [`links.md`](links.md) | 4 | Manage linked BigQuery datasets on analytics buckets |
| `logging locations` | [`locations.md`](locations.md) | 2 | Query available Cloud Logging locations |
| `logging logs` | [`logs.md`](logs.md) | 2 | List and delete your project's logs |
| `logging metrics` | [`metrics.md`](metrics.md) | 5 | Manage logs-based metrics derived from log content |
| `logging operations` | [`operations.md`](operations.md) | 3 | Manage long-running operations (e.g. copy, bucket ops) |
| `logging resource-descriptors` | [`resource-descriptors.md`](resource-descriptors.md) | 1 | List monitored-resource descriptors used by Logging |
| `logging scopes` | [`scopes.md`](scopes.md) | 5 | Manage log scopes spanning multiple resources/views |
| `logging settings` | [`settings.md`](settings.md) | 2 | Manage org/folder Logs Router settings (CMEK, default sink) |
| `logging sinks` | [`sinks.md`](sinks.md) | 5 | Manage sinks that route logs to storage or export destinations |
| `logging views` | [`views.md`](views.md) | 9 | Manage log views on buckets, including their IAM policies |

Top-level commands (see [`_commands.md`](_commands.md)): `gcloud logging copy`, `gcloud logging read`, `gcloud logging write`. See [`index.md`](index.md) for the full one-line index of all 47 GA commands.

## Common flags & tips

- **Resource scope.** Most commands accept exactly one of `--project` / `--folder` / `--organization` / `--billing-account` to target the resource hierarchy level; the current project is assumed if none is given.
- **Filters use LQL.** `--log-filter` (sinks, views, metrics, copy), the `read` positional `LOG_FILTER`, and `--filter` on `list` commands all use the [Logging Query Language](https://cloud.google.com/logging/docs/view/logging-query-language). Quote filters and prefer single quotes around expressions that contain `=` or `"`.
- **`read` time window.** `read` defaults to `--freshness=1d` and `--order=desc`; widen with an explicit `timestamp>=`/`timestamp<=` filter. To read from a non-`_Default` bucket, pass `--bucket --location --view` together (or use `--resource-names`).
- **`write` is for testing only.** Production workloads should use the Logging agent or client libraries. Defaults: `--payload-type=text`, `--severity=DEFAULT`, `--monitored-resource-type=global`.
- **Sink destinations must pre-exist.** After `sinks create`, read the `writerIdentity` from `sinks describe` and grant it write permission on the destination (`roles/storage.objectCreator`, `roles/bigquery.dataEditor`, or `roles/pubsub.publisher`). Cross-project log-bucket destinations can use `--custom-writer-identity`.
- **Buckets are regional or `global`.** `--location` is required on most bucket/view/link/operation commands and cannot change after creation. `_Required` and `_Default` are built-in buckets. Use `--retention-days`, `--locked`, and `--enable-analytics` (one-way) on buckets.
- **Useful formatting.** `--format=json` (or `yaml`) on `read` for machine parsing; `--limit=N` to cap results; on `list` commands combine `--filter` and `--sort-by` to slice output, e.g. `gcloud logging buckets list --filter="retentionDays>30" --sort-by=name`.
- **Operations require a filter.** `operations list` requires `--location` and `--operation-filter` (e.g. `request_type=CopyLogEntries`); combine with `operation_state`, `operation_start_time`, `operation_finish_time`.

## beta / alpha

- **`gcloud beta logging tail`** (beta-only) streams newly received log entries in real time with an LQL filter — there is no GA `tail`:

  ```bash
  gcloud beta logging tail "resource.type=gce_instance" --format=json
  ```

  Supports `--buffer-window` to trade ordering accuracy for lower latency, plus the standard `--project` / `--folder` / `--organization` scope flags.
- `gcloud alpha logging` mirrors the same surface as beta (commands labeled "might change without notice"); no alpha-exclusive subgroups beyond what beta exposes. All other groups are GA.

## Official documentation

- [Cloud Logging documentation home](https://cloud.google.com/logging/docs) — product concepts, guides, and how-tos.
- [gcloud logging CLI reference](https://cloud.google.com/sdk/gcloud/reference/logging) — full GA command/flag reference (also `beta` and `alpha` variants).
- [Quickstart: write and read logs with gcloud](https://cloud.google.com/logging/docs/quickstart-sdk) — first commands for ingesting and querying logs.
- [Logging Query Language](https://cloud.google.com/logging/docs/view/logging-query-language) — filter syntax used across reads, sinks, views, and metrics.
- [Configure and manage sinks](https://cloud.google.com/logging/docs/export/configure_export_v2) — routing/exporting logs and destination authorization.
- [Manage log buckets](https://cloud.google.com/logging/docs/buckets) — `_Default` / `_Required` buckets, retention, and custom buckets.
- [Logs-based metrics](https://cloud.google.com/logging/docs/logs-based-metrics) — deriving Cloud Monitoring metrics from log content.
- [Log Analytics](https://cloud.google.com/logging/docs/log-analytics) — SQL-based aggregation over log data and linked BigQuery datasets.
- [Access control with IAM](https://cloud.google.com/logging/docs/access-control) — Logging roles and permissions reference.

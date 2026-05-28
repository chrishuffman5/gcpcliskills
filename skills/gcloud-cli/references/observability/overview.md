# gcloud observability — Google Cloud Observability scopes

## Overview

`gcloud observability` manages **Observability Scope** resources — project-level containers that pair a Cloud Monitoring metrics scope with an optional Cloud Logging log scope to give a unified view of telemetry across Google Cloud Observability (formerly Stackdriver: Monitoring, Logging, Trace, Error Reporting, Profiler). The GA surface is intentionally small: every project has exactly one scope named `Default` at location `global`, and you `describe` it or `update` it to attach/detach a log scope. Reach for this group when you want to wire a Cloud Logging LogScope into a project's observability view from the CLI. Broader observability management (log buckets, settings, trace scopes) lives under `gcloud beta observability` — see the beta section below.

## Quick reference — common workflows

### 1. Describe the project's Default observability scope
Every project has exactly one scope (`Default`) at location `global`.
```bash
# Fully qualified positional name
gcloud observability scopes describe \
  projects/MY_PROJECT/locations/global/scopes/Default

# Short scope ID plus the --location flag
gcloud observability scopes describe Default \
  --location=global \
  --project=MY_PROJECT
```

### 2. Attach a Cloud Logging log scope
Use `--log-scope` with the full resource name of a LogScope to associate it with the Default observability scope, enabling scoped log queries in the Observability UI. Enable the data-plane APIs first.
```bash
# Cloud Monitoring backs the metrics scope; Cloud Logging backs the log scope
gcloud services enable monitoring.googleapis.com --project=MY_PROJECT
gcloud services enable logging.googleapis.com --project=MY_PROJECT

gcloud observability scopes update Default \
  --location=global \
  --project=MY_PROJECT \
  --log-scope=//logging.googleapis.com/projects/MY_PROJECT/locations/global/logScopes/my-log-scope
```

### 3. Detach the log scope
Pass an empty string to `--log-scope` to clear the currently associated log scope.
```bash
gcloud observability scopes update Default \
  --location=global \
  --project=MY_PROJECT \
  --log-scope=""
```

### 4. Inspect just the attached log scope
```bash
# Surface only the log-scope field from the describe output
gcloud observability scopes describe Default \
  --location=global \
  --project=MY_PROJECT \
  --format='value(logScope)'
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `observability scopes` | [`scopes.md`](scopes.md) | 2 | manage Scope resources (describe, update) |

See [`index.md`](index.md) for a one-line index of all 2 commands.

## Common flags & tips

- **Scope is fixed.** The resource is always `projects/{project}/locations/{location}/scopes/{scope}` where `{location}` must be `global` and `{scope}` must be `Default`. There is no `list` or `create` — the single Default scope already exists per project.
- **Positional `SCOPE` vs. flags.** You may pass the fully qualified name positionally (`projects/.../scopes/Default`) or pass the short ID `Default` together with `--location=global`. If you give any of the resource-attribute arguments, the positional `SCOPE` must be supplied.
- **Project resolution.** Set the project via a fully qualified positional name, the `--project` flag, or the `core/project` config property.
- **`update` is a partial update.** Only `--log-scope` is configurable. Provide the full LogScope resource name (e.g. `//logging.googleapis.com/projects/MY_PROJECT/locations/global/logScopes/my-log-scope`); pass `''` to clear it.
- **IAM.** Reading typically needs `roles/monitoring.viewer` or `roles/monitoring.metricsScopesViewer`; updating typically needs `roles/monitoring.admin` or `roles/monitoring.metricsScopesAdmin`.
- **Formatting.** Use `--format` to trim output, e.g. `--format='value(name)'` or `--format='value(logScope)'`.

## beta / alpha

`gcloud beta observability` adds capabilities not present in the GA surface:

- **`buckets`** — manage Bucket resources (log buckets).
- **`settings`** — manage Observability settings.
- **`trace-scopes`** — manage Trace Scope resources.

`gcloud alpha observability` largely mirrors the GA `scopes` surface plus `trace-scopes`; `buckets` and `settings` are beta-only at the time of research. List the available beta groups with:
```bash
gcloud beta observability --help
```
These pre-GA features may change without notice.

## Official documentation

- [Google Cloud Observability product home](https://cloud.google.com/stackdriver/docs/) — Monitoring, Logging, Trace, Error Reporting, and Profiler overview.
- [Metrics scopes](https://cloud.google.com/monitoring/settings) — what time-series data a project can monitor (the metrics-scope half of an observability scope).
- [Cloud Monitoring access control](https://cloud.google.com/monitoring/access-control) — IAM roles including metrics-scope admin/viewer.
- [Enable the Cloud Monitoring API](https://cloud.google.com/monitoring/api/enable-api) — turning on `monitoring.googleapis.com`.
- [LogScope REST resource](https://cloud.google.com/logging/docs/reference/v2/rest/v2/projects.locations.logScopes) — the Cloud Logging LogScope referenced by `--log-scope`.
- [gcloud observability reference](https://cloud.google.com/sdk/gcloud/reference/observability) — full CLI command and flag reference.
- [gcloud observability scopes update reference](https://cloud.google.com/sdk/gcloud/reference/observability/scopes/update) — every `scopes update` flag in detail.

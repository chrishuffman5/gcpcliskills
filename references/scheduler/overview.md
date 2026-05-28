# gcloud scheduler — Cloud Scheduler

## Overview

Cloud Scheduler is a fully managed, enterprise-grade cron job scheduler. Use `gcloud scheduler` to create and manage jobs that fire on a recurring schedule against one of three target types: HTTP/S endpoints, Pub/Sub topics, or App Engine HTTP handlers. Jobs use the unix-cron 5-field schedule format, follow an at-least-once delivery model, and support configurable exponential-backoff retry. Reach for it when you need durable, time-driven triggers for batch jobs, cloud operations, or any periodic task without standing up your own cron infrastructure.

## Quick reference — common workflows

### 1. Enable the API and check available locations
```bash
gcloud services enable cloudscheduler.googleapis.com

# List the regions where Cloud Scheduler is available
gcloud scheduler locations list

# Inspect a specific location
gcloud scheduler locations describe us-central1
```

### 2. Create an HTTP job (GET every hour)
```bash
gcloud scheduler jobs create http hourly-ping \
    --location=us-central1 \
    --schedule="0 * * * *" \
    --uri="https://example.com/health" \
    --http-method=GET \
    --time-zone="America/New_York" \
    --description="Hourly health-check ping"
```

For an authenticated target (e.g. Cloud Run) using an OIDC token:
```bash
gcloud scheduler jobs create http invoke-cloud-run \
    --location=us-central1 \
    --schedule="0 */3 * * *" \
    --uri="https://my-service-xyz.a.run.app/task" \
    --http-method=POST \
    --oidc-service-account-email=scheduler-sa@PROJECT.iam.gserviceaccount.com \
    --oidc-token-audience="https://my-service-xyz.a.run.app"
```
The invoking service account also needs the right role on the target (e.g. `roles/run.invoker`).

### 3. Create a Pub/Sub job (publish every 5 minutes)
```bash
gcloud services enable cloudscheduler.googleapis.com pubsub.googleapis.com

gcloud scheduler jobs create pubsub every-5min-pubsub \
    --location=us-central1 \
    --schedule="*/5 * * * *" \
    --topic=my-topic \
    --message-body="trigger" \
    --time-zone="Etc/UTC"
```

### 4. Create an App Engine job (every 3 hours)
```bash
gcloud scheduler jobs create app-engine ae-cron-job \
    --schedule="0 */3 * * *" \
    --relative-url="/cron-handler" \
    --http-method=GET \
    --description="App Engine cron handler every 3 hours"
# --location defaults to the project's App Engine region
```

### 5. List, inspect, pause, and resume jobs
```bash
gcloud scheduler jobs list --location=us-central1
gcloud scheduler jobs describe hourly-ping --location=us-central1

# Pause stops future executions; resume restarts a paused job
gcloud scheduler jobs pause hourly-ping --location=us-central1
gcloud scheduler jobs resume hourly-ping --location=us-central1
```

### 6. Trigger on-demand, update, and delete
```bash
# Force an immediate execution (useful for testing)
gcloud scheduler jobs run hourly-ping --location=us-central1

# Update an HTTP job's schedule and retry behavior
gcloud scheduler jobs update http hourly-ping \
    --location=us-central1 \
    --schedule="0 */2 * * *" \
    --max-retry-attempts=3 \
    --min-backoff=10s \
    --max-backoff=600s

gcloud scheduler jobs delete hourly-ping --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `scheduler cmek-config` | [`cmek-config.md`](cmek-config.md) | 2 | manage CMEK configuration for Cloud Scheduler |
| `scheduler jobs` | [`jobs.md`](jobs.md) | 12 | manage Cloud Scheduler jobs (create/update for http, pubsub, app-engine; list, describe, run, pause, resume, delete) |
| `scheduler locations` | [`locations.md`](locations.md) | 2 | get information about Cloud Scheduler locations |
| `scheduler operations` | [`operations.md`](operations.md) | 1 | get information about Cloud Scheduler operations |

See [`index.md`](index.md) for a one-line index of all 17 commands.

## Common flags & tips

- **`--location`** — most `jobs` commands accept it to target a region (e.g. `us-central1`). If omitted, it defaults to the project's App Engine app location when an app exists. `jobs list` also accepts `--location` to scope results.
- **`--schedule`** — unix-cron 5-field syntax (`minute hour day-of-month month day-of-week`), e.g. `"0 */3 * * *"` for every 3 hours. Always quote it. See the cron format guide below.
- **`--time-zone`** — a tz database name such as `America/New_York`; defaults to `Etc/UTC`. DST rules follow the chosen zone.
- **Retry tuning** (on `create`/`update`): `--max-retry-attempts` (0–5), `--max-retry-duration`, `--min-backoff` (default `5s`), `--max-backoff` (default `3600s`), `--max-doublings` (default `5`). `--attempt-deadline` bounds a single attempt.
- **HTTP auth** — use `--oidc-service-account-email` + `--oidc-token-audience` for general endpoints (Cloud Run, Cloud Functions); use `--oauth-service-account-email` + `--oauth-token-scope` for Google APIs (`*.googleapis.com`). On `jobs update http`, `--clear-auth-token` removes auth.
- **Editing collections on update** — paired `--clear-*` / `--remove-*` / `--update-*` flags manage headers (`--update-headers`, `--remove-headers`, `--clear-headers`) and Pub/Sub attributes (`--update-attributes`, `--remove-attributes`, `--clear-attributes`).
- **Message bodies** — `--message-body` inline or `--message-body-from-file=PATH` for HTTP/App Engine/Pub/Sub payloads.
- **Filtering & formatting** — `jobs list` and `locations list` support `--filter`, `--limit`, `--sort-by`, and `--uri`. Example: list only paused jobs and show two columns:
  ```bash
  gcloud scheduler jobs list --location=us-central1 \
      --filter="state=PAUSED" \
      --format="table(name, schedule, state)"
  ```
- **Operations** — `gcloud scheduler operations describe --name=NAME` reports status using the full resource name `projects/{project}/locations/{location}/operations/{operation}`.

## beta / alpha

Both `gcloud beta scheduler` and `gcloud alpha scheduler` exist and expose the same command groups (`jobs`, `locations`) as GA, but commands "might change without notice." No beta/alpha-exclusive flags are documented; the GA surface covers the full job lifecycle, all three target types, and CMEK config. Use GA unless a specific preview feature is required.

## Official documentation

- [Cloud Scheduler docs home](https://cloud.google.com/scheduler/docs) — product landing page and how-to index.
- [Overview](https://cloud.google.com/scheduler/docs/overview) — concepts: target types, cron format, retry, at-least-once delivery.
- [Quickstart](https://cloud.google.com/scheduler/docs/quickstart) — enable APIs and create a Pub/Sub job.
- [Cron job schedule format](https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules) — unix-cron 5-field syntax and the groc (human-readable) alternative.
- [Retry jobs](https://cloud.google.com/scheduler/docs/configuring/retry-jobs) — retry attempts, backoff durations, and max doublings.
- [HTTP target authentication](https://cloud.google.com/scheduler/docs/http-target-auth) — OIDC tokens (general) vs OAuth2 tokens (Google APIs).
- [Access control (IAM)](https://cloud.google.com/scheduler/docs/access-control) — roles: Admin, Viewer, Job Runner, Service Agent.
- [gcloud scheduler CLI reference](https://cloud.google.com/sdk/gcloud/reference/scheduler) — full command and flag reference.

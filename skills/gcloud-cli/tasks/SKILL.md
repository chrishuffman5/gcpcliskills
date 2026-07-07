---
name: gcloud-tasks
description: >-
  Cloud Tasks via gcloud (`gcloud tasks`). Manage Cloud Tasks queues and tasks — cmek-config, locations, queues.
---

# gcloud tasks — Cloud Tasks

## Overview

Cloud Tasks is a fully managed service for asynchronously dispatching and delivering large numbers of distributed tasks. You enqueue work onto a **queue**, and Cloud Tasks dispatches each **task** to either an HTTP endpoint (Cloud Run, GKE, Compute Engine, or any reachable URL) or an App Engine handler, with per-queue rate limiting, retry/backoff, and scheduling. Reach for it to offload slow work from request handlers, smooth out traffic spikes, schedule deferred execution, or guarantee at-least-once delivery to a worker. Manage it with the `gcloud tasks` command group (subgroups: `queues`, `locations`, `cmek-config`).

## Quick reference — common workflows

### 1. Enable the API and create a queue

```bash
gcloud services enable cloudtasks.googleapis.com

# See where Cloud Tasks is available
gcloud tasks locations list

# Create a queue with rate limits and retry/backoff settings
gcloud tasks queues create my-queue \
  --location=us-central1 \
  --max-dispatches-per-second=100 \
  --max-concurrent-dispatches=10 \
  --max-attempts=5 \
  --min-backoff=1s \
  --max-backoff=30s \
  --max-doublings=4

gcloud tasks queues describe my-queue --location=us-central1
```

### 2. Create and inspect HTTP target tasks

```bash
# Auto-generated task ID; POST JSON to a worker URL
gcloud tasks create-http-task \
  --queue=my-queue \
  --location=us-central1 \
  --url=https://my-service.example.com/worker \
  --method=POST \
  --header="Content-Type:application/json" \
  --body-content='{"job":"process"}'

# Explicit task ID with OIDC auth (e.g. targeting a private Cloud Run service)
gcloud tasks create-http-task my-task-id \
  --queue=my-queue \
  --location=us-central1 \
  --url=https://my-cloudrun-service-abc.run.app/handler \
  --oidc-service-account-email=my-sa@my-project.iam.gserviceaccount.com \
  --oidc-token-audience=https://my-cloudrun-service-abc.run.app

# List and inspect
gcloud tasks list --queue=my-queue --location=us-central1
gcloud tasks describe my-task-id \
  --queue=my-queue \
  --location=us-central1 \
  --response-view=full
```

### 3. Create an App Engine target task

```bash
# Route to an App Engine service/handler, scheduled for a future time
gcloud tasks create-app-engine-task \
  --queue=my-queue \
  --location=us-central1 \
  --relative-uri=/process \
  --routing=service:worker \
  --method=POST \
  --schedule-time="2026-06-01T00:00:00Z"
```

### 4. Force-run, delete, and purge tasks

```bash
# Force a scheduled task to dispatch immediately
gcloud tasks run my-task-id --queue=my-queue --location=us-central1

# Delete a single task
gcloud tasks delete my-task-id --queue=my-queue --location=us-central1

# Delete ALL tasks from a queue (irreversible)
gcloud tasks queues purge my-queue --location=us-central1
```

### 5. Pause, resume, and update a queue

```bash
# Pause: tasks still accept but stop dispatching until resumed
gcloud tasks queues pause my-queue --location=us-central1
gcloud tasks queues resume my-queue --location=us-central1

# Tune rate limits in place
gcloud tasks queues update my-queue \
  --location=us-central1 \
  --max-dispatches-per-second=50 \
  --max-concurrent-dispatches=5

gcloud tasks queues delete my-queue --location=us-central1
```

### 6. Manage a queue's IAM policy

```bash
gcloud tasks queues get-iam-policy my-queue --location=us-central1

# Grant a service account enqueue-only access
gcloud tasks queues add-iam-policy-binding my-queue \
  --location=us-central1 \
  --member='serviceAccount:my-sa@my-project.iam.gserviceaccount.com' \
  --role='roles/cloudtasks.enqueuer'

gcloud tasks queues remove-iam-policy-binding my-queue \
  --location=us-central1 \
  --member='serviceAccount:my-sa@my-project.iam.gserviceaccount.com' \
  --role='roles/cloudtasks.enqueuer'
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `tasks cmek-config` | [`cmek-config.md`](cmek-config.md) | 2 | Get or change CMEK (customer-managed encryption key) configuration per location |
| `tasks locations` | [`locations.md`](locations.md) | 2 | Discover where Cloud Tasks is available |
| `tasks queues` | [`queues.md`](queues.md) | 12 | Create, configure, pause/resume, purge, delete queues and manage their IAM policy |

Top-level task commands (`buffer`, `create-app-engine-task`, `create-http-task`, `delete`, `describe`, `list`, `run`) are documented in [`_commands.md`](_commands.md). See [`index.md`](index.md) for the one-line index of all 23 commands.

## Common flags & tips

- **`--location` and `--queue` are pervasive.** Almost every task and queue command takes `--location` (the region, e.g. `us-central1`). Task-level commands also need `--queue`. If your project has an associated App Engine app, `--location` defaults to that app's region; otherwise specify it explicitly.
- **Task IDs are optional but enable de-duplication.** `create-http-task` and `create-app-engine-task` take an optional positional `TASK_ID`. Omit it for a random unique ID; supply it to dedupe (reusing a recently-used ID fails). Tasks created with explicit IDs have higher latency, so prefer hashed-string IDs.
- **Retry/backoff and rate-limit flags** (`--max-attempts`, `--min-backoff`, `--max-backoff`, `--max-doublings`, `--max-retry-duration`, `--max-dispatches-per-second`, `--max-concurrent-dispatches`) are settable on `queues create` and `queues update`. Backoff/duration values are strings ending in `s` (e.g. `5s`). On `queues update`, each setting has a paired `--clear-...` flag to reset it.
- **Queue-level routing overrides** force all tasks onto a target regardless of task settings: `--routing-override` (App Engine), or `--http-uri-override`, `--http-method-override`, `--http-header-override`, and the `--http-oidc-*-override` / `--http-oauth-*-override` flags (HTTP).
- **HTTP task auth:** use `--oidc-service-account-email` + `--oidc-token-audience` for OIDC (calling Cloud Run / Cloud Functions), or `--oauth-service-account-email` + `--oauth-token-scope` for OAuth (calling Google APIs).
- **Headers:** repeat `--header="Key:Value"` per header; repeated keys override.
- **`--response-view=full`** on `tasks describe` returns the full task payload (default is `basic`).
- **Useful `--format` / `--filter`:**
  - `gcloud tasks queues list --location=us-central1 --format="table(name, state, rateLimits.maxDispatchesPerSecond)"`
  - `gcloud tasks queues list --location=us-central1 --filter="state=PAUSED"`
  - `gcloud tasks list --queue=my-queue --location=us-central1 --format="table(name, scheduleTime, dispatchCount)"`
- **Purge is irreversible** and can take up to a minute to take effect; tasks may still dispatch during that window.

## beta / alpha

`gcloud beta tasks` and `gcloud alpha tasks` mirror the GA surface — the same subgroups (`cmek-config`, `locations`, `queues`) and the same top-level commands — and carry the standard "might change without notice" caveat. No commands are exclusive to the beta or alpha channels; all 23 commands documented here are GA, including CMEK configuration. Reach for the pre-GA channels only when you need a newly introduced flag before it lands in GA.

## Official documentation

- **Product docs home:** https://cloud.google.com/tasks/docs — Cloud Tasks documentation landing page (overview, guides, API references).
- **Quickstart:** https://docs.cloud.google.com/tasks/docs/quickstart — create a queue and add a task using gcloud.
- **Queue target types overview:** https://docs.cloud.google.com/tasks/docs/dual-overview — HTTP targets vs. App Engine targets.
- **Create queues:** https://docs.cloud.google.com/tasks/docs/creating-queues — create queues via Console, gcloud, or REST.
- **Create HTTP target tasks:** https://docs.cloud.google.com/tasks/docs/creating-http-target-tasks — `CreateTask` and `BufferTask` methods.
- **Create App Engine tasks:** https://docs.cloud.google.com/tasks/docs/creating-appengine-tasks — App Engine target tasks.
- **Configure queues:** https://docs.cloud.google.com/tasks/docs/configuring-queues — routing, rate limits, retry/backoff.
- **Access control (IAM):** https://docs.cloud.google.com/tasks/docs/access-control — predefined Cloud Tasks roles.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/tasks — full `gcloud tasks` command reference.

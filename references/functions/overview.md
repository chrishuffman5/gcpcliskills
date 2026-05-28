# gcloud functions — Cloud Run functions (Cloud Functions)

## Overview
`gcloud functions` deploys and manages serverless, event-driven functions that run single-purpose code without provisioning servers. Functions can be triggered by HTTP requests, Pub/Sub messages, Cloud Storage changes, and Eventarc events. Two generations exist: 1st gen (legacy) and 2nd gen (built on Cloud Run, now branded "Cloud Run functions" and recommended for new work). Reach for it when you want lightweight, autoscaling glue code — for full container control, use `gcloud run` instead.

## Quick reference — common workflows

### Deploy an HTTP function (2nd gen, recommended)
```bash
# Enable required APIs (2nd gen builds on Cloud Run + Cloud Build)
gcloud services enable cloudfunctions.googleapis.com run.googleapis.com cloudbuild.googleapis.com

gcloud functions deploy my-http-function \
    --gen2 \
    --runtime=nodejs20 \
    --region=us-central1 \
    --source=. \
    --entry-point=helloGET \
    --trigger-http \
    --allow-unauthenticated

gcloud functions describe my-http-function --region=us-central1
```

### Deploy an event-driven function (Pub/Sub)
```bash
gcloud functions deploy my-pubsub-function \
    --gen2 \
    --runtime=python311 \
    --region=us-central1 \
    --source=. \
    --entry-point=hello_pubsub \
    --trigger-topic=my-topic \
    --retry
```

### Tune resources and scaling on deploy
```bash
gcloud functions deploy my-http-function \
    --gen2 \
    --runtime=nodejs20 \
    --region=us-central1 \
    --source=. \
    --entry-point=helloGET \
    --trigger-http \
    --memory=512Mi \
    --timeout=120s \
    --max-instances=10 \
    --min-instances=1 \
    --concurrency=80 \
    --set-env-vars=NODE_ENV=production
```

### Test / call a deployed function
```bash
# HTTP or background function — pass JSON data
gcloud functions call my-http-function \
    --data='{"message": "Hello World!"}' \
    --region=us-central1

# 2nd gen CloudEvent function — pass a structured CloudEvent
gcloud functions call my-event-function \
    --cloud-event='{"specversion":"1.0","type":"google.cloud.pubsub.topic.v1.messagePublished","source":"//pubsub.googleapis.com/projects/my-project/topics/my-topic","id":"1234"}' \
    --region=us-central1
```

### View logs
```bash
# Default: 20 most recent entries
gcloud functions logs read my-http-function --region=us-central1

# More entries, filtered by minimum log level
gcloud functions logs read my-http-function \
    --region=us-central1 \
    --limit=50 \
    --min-log-level=error

# Restrict to a time range
gcloud functions logs read my-http-function \
    --region=us-central1 \
    --start-time=2024-01-01T00:00:00Z \
    --end-time=2024-01-02T00:00:00Z
```

### Manage invoker access (IAM)
```bash
# Make a function publicly invocable (2nd gen → Cloud Run Invoker, 1st gen → Functions Invoker)
gcloud functions add-invoker-policy-binding my-http-function \
    --region=us-central1 \
    --member=allUsers

# Grant a generic IAM role binding
gcloud functions add-iam-policy-binding my-http-function \
    --region=us-central1 \
    --member=user:dev@example.com \
    --role=roles/cloudfunctions.invoker

gcloud functions get-iam-policy my-http-function --region=us-central1

# Revoke public access
gcloud functions remove-invoker-policy-binding my-http-function \
    --region=us-central1 \
    --member=allUsers
```

### List, inspect, and delete
```bash
gcloud functions list                               # default region
gcloud functions list --regions=us-central1,us-east1
gcloud functions list --v2                           # 2nd gen in v2 format
gcloud functions describe my-http-function --region=us-central1
gcloud functions delete my-http-function --region=us-central1
gcloud functions runtimes list                       # available runtimes
gcloud functions regions list                        # available regions
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `functions` (top-level) | [`_commands.md`](_commands.md) | 12 | deploy, call, describe, detach, delete, list, and IAM/invoker policy commands |
| `functions event-types` | [`event-types.md`](event-types.md) | 1 | list event types that can trigger a function |
| `functions logs` | [`logs.md`](logs.md) | 1 | display log entries produced by functions |
| `functions regions` | [`regions.md`](regions.md) | 1 | list regions available to functions |
| `functions runtimes` | [`runtimes.md`](runtimes.md) | 1 | list runtimes available to functions |

See [`index.md`](index.md) for a one-line index of all 16 commands.

## Common flags & tips

- **Generation selection (`--gen2` vs gen1):** `gcloud functions deploy --gen2` deploys a 2nd gen (Cloud Run-backed) function; `--no-gen2` forces 1st gen. If neither is given, the value comes from the `functions/gen2` config property, and if that is unset the CLI looks up the existing function's generation. The same `--gen2` flag also drives `functions logs read`, `event-types list`, and `regions list`. For read-back, `describe --v2` and `list --v2` return results in the v2 API format (and override `--no-gen2`).
- **Generation differences:** `--timeout` allows up to `540s` for 1st gen but up to `3600s` for 2nd gen. `--concurrency` (requests per instance) and `--cpu` are 2nd gen concepts; 1st gen `--memory` is limited to fixed values (`128MB`…`8192MB`) while 2nd gen accepts units like `512Mi`, `2Gi`. Invoker bindings map to the **Cloud Functions Invoker** role on 1st gen and the **Cloud Run Invoker** role on the underlying Cloud Run service for 2nd gen.
- **Region is required for most commands.** Pass `--region=REGION` or set the default with `gcloud config set functions/region us-central1`. `functions list` uses the plural `--regions=` (comma-separated, default `-` = all).
- **Triggers (mutually exclusive on deploy):** `--trigger-http`, `--trigger-topic=TOPIC`, `--trigger-bucket=BUCKET`, `--trigger-event=EVENT_TYPE --trigger-resource=RESOURCE`, or Eventarc-style `--trigger-event-filters=` / `--trigger-event-filters-path-pattern=`. Run `gcloud functions event-types list` to discover valid 1st gen event types.
- **Env vars & secrets** use the standard set/update/remove/clear pattern: `--set-env-vars`, `--update-env-vars`, `--remove-env-vars`, `--clear-env-vars` (or `--env-vars-file`), and likewise `--set-secrets` / `--set-build-env-vars`.
- **Source** defaults to the current directory; it may also be a `gs://` bucket archive or a `https://source.developers.google.com/...` repo URL. Use `--ignore-file` to override `.gcloudignore`.
- **Useful `--format` / `--filter`:**
  ```bash
  gcloud functions list --v2 --format="table(name, state, updateTime)"
  gcloud functions list --regions=us-central1 --filter="name~http" --sort-by=name
  gcloud functions describe my-http-function --region=us-central1 \
      --format="value(serviceConfig.uri)"
  ```
- **`functions detach`** converts a 2nd gen function into a standalone native Cloud Run service (managed from then on with `gcloud run`).

## beta / alpha

- **`gcloud beta functions upgrade`** — staged migration of a 1st gen function to 2nd gen (Cloud Run functions). Workflow flags: `--setup-config`, `--redirect-traffic`, `--rollback-traffic`, `--commit`, `--abort`. Also available under `gcloud alpha functions upgrade`.
- **`gcloud alpha functions local`** — alpha-only group for local development: `local deploy`, `local call`, `local delete`.

## Official documentation

- [Cloud Run functions docs home](https://cloud.google.com/functions/docs) — product documentation hub for serverless functions.
- [Concepts overview](https://cloud.google.com/functions/docs/concepts/overview) — distinguishes Cloud Run functions (latest) from 1st gen.
- [2nd gen vs 1st gen](https://cloud.google.com/functions/docs/2nd-gen/overview) — timeout, concurrency, trigger, and configuration differences.
- [Deployment guide](https://cloud.google.com/functions/docs/deploy) — `gcloud functions deploy` flags and Cloud Run-native deploys.
- [Writing functions](https://cloud.google.com/functions/docs/writing) — Functions Framework across supported languages.
- [Calling / testing](https://cloud.google.com/functions/docs/running/calling) — `gcloud functions call` usage.
- [Managing IAM access](https://cloud.google.com/functions/docs/securing/managing-access-iam) — admin and invoker roles.
- [IAM roles reference](https://cloud.google.com/functions/docs/reference/iam/roles) — full predefined role list.
- [gcloud functions CLI reference](https://cloud.google.com/sdk/gcloud/reference/functions) — authoritative command/flag reference (GA surface).

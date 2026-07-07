---
name: gcloud-workflows
description: >-
  Workflows via gcloud (`gcloud workflows`). Manage your Cloud Workflows resources — executions.
---

# gcloud workflows — Workflows

## Overview
Cloud Workflows is a fully managed, serverless orchestration platform that runs a series of steps in a user-defined order. A workflow can call Google Cloud connectors, Cloud Run functions, Cloud Run services, and any HTTP-based API, with support for conditional branching, loops, parallel steps, retries with backoff, and state held for up to a year. Reach for `gcloud workflows` to deploy workflow definitions (YAML/JSON), execute them synchronously or asynchronously, and inspect or manage their executions.

## Quick reference — common workflows

### 1. Deploy a new workflow
```bash
# Enable the API (one-time per project)
gcloud services enable workflows.googleapis.com

# Create a dedicated identity and let it write execution logs
gcloud iam service-accounts create my-workflow-sa \
    --display-name="My Workflow SA"
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="serviceAccount:my-workflow-sa@PROJECT_ID.iam.gserviceaccount.com" \
    --role=roles/logging.logWriter

# Deploy the workflow definition
gcloud workflows deploy my-workflow \
    --source=myWorkflow.yaml \
    --service-account=my-workflow-sa@PROJECT_ID.iam.gserviceaccount.com \
    --location=us-central1
```

### 2. Run a workflow and wait for the result (synchronous)
```bash
gcloud workflows run my-workflow \
    --data='{"key": "value"}' \
    --location=us-central1
```

### 3. Execute asynchronously and monitor the execution
```bash
# Fire-and-forget; returns an execution resource
gcloud workflows execute my-workflow \
    --data='{"key": "value"}' \
    --location=us-central1

# List executions to find the ID
gcloud workflows executions list my-workflow --location=us-central1

# Inspect a specific execution
gcloud workflows executions describe EXECUTION_ID \
    --workflow=my-workflow --location=us-central1

# Block until a specific execution finishes
gcloud workflows executions wait EXECUTION_ID \
    --workflow=my-workflow --location=us-central1

# Or operate on the last cached execution from this machine
gcloud workflows executions describe-last
gcloud workflows executions wait-last
```

### 4. Inspect and update a deployed workflow
```bash
# List all workflows
gcloud workflows list

# Show metadata for the latest revision, or a specific one
gcloud workflows describe my-workflow --location=us-central1
gcloud workflows describe my-workflow \
    --revision-id=000001-dc1 --location=us-central1

# Redeploy with new source and turn on error-only call logging
gcloud workflows deploy my-workflow \
    --source=myWorkflow-v2.yaml \
    --call-log-level=log-errors-only \
    --location=us-central1
```

### 5. Cancel a running execution
```bash
gcloud workflows executions list my-workflow --location=us-central1
gcloud workflows executions cancel EXECUTION_ID \
    --workflow=my-workflow --location=us-central1
```

### 6. Delete a workflow
```bash
# Deletes the workflow and all of its executions
gcloud workflows delete my-workflow --location=us-central1

# Skip waiting for the delete operation to finish
gcloud workflows delete my-workflow --location=us-central1 --async
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `workflows` (top-level) | [`_commands.md`](_commands.md) | 6 | deploy, describe, list, delete workflows and execute/run them |
| `workflows executions` | [`executions.md`](executions.md) | 6 | manage your Cloud Workflow execution resources |

See [`index.md`](index.md) for a one-line index of all 12 GA commands.

## Common flags & tips
- **Location is required for most commands.** Pass `--location=LOCATION` (e.g. `us-central1`) or set it once with `gcloud config set workflows/location us-central1`. `gcloud workflows list` also accepts `--location`; omit it to list across the configured location.
- **`run` vs `execute`.** `gcloud workflows run` starts an execution and blocks until it completes (returning the result); `gcloud workflows execute` starts it and returns immediately. Both accept `--data='{...}'` to pass a JSON argument and `--labels=KEY=VALUE,...`.
- **`--source` on `deploy`** points at a local workflow definition file and is required on the first deployment; subsequent deploys can update other attributes without re-supplying source.
- **Logging & history.** `--call-log-level` accepts `log-all-calls`, `log-errors-only`, `log-none`, or `none`; `--execution-history-level` accepts `execution-history-basic`, `execution-history-detailed`, or `none`. Both are available on `deploy`, `execute`, and `run` (defaults are `none`).
- **`--async`** on `deploy` and `delete` returns without waiting for the long-running operation.
- **The "last" helpers** (`executions describe-last`, `executions wait-last`) act on the most recent execution cached locally by this gcloud install — handy right after `execute`.
- **Useful filters/formats:**
  ```bash
  # Show only failed executions, newest first
  gcloud workflows executions list my-workflow --location=us-central1 \
      --filter='state=FAILED' --sort-by=~startTime
  # Just the execution names (URIs)
  gcloud workflows executions list my-workflow --location=us-central1 --uri
  # Workflow names and update times as a table
  gcloud workflows list --format='table(name, updateTime, state)'
  ```

## beta / alpha
`gcloud beta workflows` mirrors the GA surface — the same commands and flags are available; the beta label signals the feature may change, not that it exposes different functionality. No beta- or alpha-exclusive commands or flags were identified, and `gcloud alpha workflows` is not documented in the official reference.

## Official documentation
- [Cloud Workflows documentation home](https://cloud.google.com/workflows/docs) — product docs landing page.
- [Workflows overview](https://cloud.google.com/workflows/docs/overview) — features, architecture, and the serverless orchestration model.
- [Quickstart: deploy and run with gcloud](https://cloud.google.com/workflows/docs/quickstart-gcloud) — end-to-end first workflow via the CLI.
- [Create and deploy a workflow (gcloud)](https://cloud.google.com/workflows/docs/create-workflow-gcloud) — authoring and deploying with gcloud.
- [Access control with IAM](https://cloud.google.com/workflows/docs/access-control) — predefined Workflows roles and permissions.
- [Schedule a workflow](https://cloud.google.com/workflows/docs/schedule-workflow) — trigger executions on a schedule with Cloud Scheduler.
- [gcloud workflows reference](https://cloud.google.com/sdk/gcloud/reference/workflows) — CLI reference for the command group.
- [gcloud workflows executions reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions) — CLI reference for execution commands.

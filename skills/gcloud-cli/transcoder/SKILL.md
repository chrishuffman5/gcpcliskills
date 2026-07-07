---
name: gcloud-transcoder
description: >-
  Transcoder API via gcloud (`gcloud transcoder`). Manage Transcoder jobs and job templates — jobs, templates.
---

# gcloud transcoder — Transcoder API

## Overview

The Transcoder API converts video files and packages them for optimized delivery to web, mobile, and connected-TV players. It is built for asynchronous, batch-style processing (not real-time/interactive streaming): you point a job at an input file in Cloud Storage, and it writes the transcoded renditions and manifests back to Cloud Storage. Use `gcloud transcoder` to submit and monitor transcode **jobs** and to manage reusable **job templates**. There are 8 GA commands across two groups: `jobs` and `templates`.

## Quick reference — common workflows

### 1. Enable the API and set a default location

```bash
gcloud services enable transcoder.googleapis.com

# Optional: avoid repeating --location on every command
gcloud config set transcoder/location us-central1
```

### 2. Create a job from an input/output URI (default config)

```bash
gcloud transcoder jobs create --location=us-central1 \
    --input-uri="gs://my-bucket/input.mp4" \
    --output-uri="gs://my-bucket/output/"
```

### 3. Create a job from a reusable template

```bash
# Create the template from a JSON config file
gcloud transcoder templates create my-template \
    --file="template-config.json" --location=us-central1

# Submit a job that references it
gcloud transcoder jobs create --location=us-central1 \
    --input-uri="gs://my-bucket/input.mp4" \
    --output-uri="gs://my-bucket/output/" \
    --template-id=my-template
```

### 4. Create a job from a custom JSON config

```bash
# From a config file
gcloud transcoder jobs create --location=us-central1 \
    --file="config.json"

# Or inline JSON
gcloud transcoder jobs create --location=us-central1 \
    --json="config: json-format"
```

### 5. Monitor and clean up a job

```bash
# Check job status
gcloud transcoder jobs describe JOB_NAME --location=us-central1

# List all jobs in a region
gcloud transcoder jobs list --location=us-central1

# Delete a finished job
gcloud transcoder jobs delete JOB_NAME --location=us-central1
```

### 6. Submit a batch-mode job with priority and labels

```bash
gcloud transcoder jobs create --location=us-central1 \
    --file="config.json" \
    --mode=PROCESSING_MODE_BATCH \
    --batch-mode-priority=3 \
    --labels=team=media
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `transcoder jobs` | [`jobs.md`](jobs.md) | 4 | Manage Cloud Transcoder jobs (create, delete, describe, list) |
| `transcoder templates` | [`templates.md`](templates.md) | 4 | Manage Cloud Transcoder job templates (create, delete, describe, list) |

See [`index.md`](index.md) for a one-line index of all 8 commands.

## Common flags & tips

- **Location is required.** Every command needs a region, set via `--location=us-central1`, by passing a fully qualified resource name, or by setting the `transcoder/location` config property (`gcloud config set transcoder/location us-central1`).
- **Job config sources are mutually exclusive.** On `jobs create`, supply exactly one of `--file` (path to a JSON config), `--json` (inline JSON), or `--template-id` (reference an existing template). Omitting all three uses the default config; `--input-uri` / `--output-uri` override the matching values in whichever config is used.
- **Templates need a config.** `templates create` requires exactly one of `--file` or `--json`; the template name is the positional `TEMPLATE_ID` (there is no `--template-id` flag on this command).
- **Processing mode** — `--mode` accepts `PROCESSING_MODE_INTERACTIVE` or `PROCESSING_MODE_BATCH`. Pair batch mode with `--batch-mode-priority` (higher runs sooner); both override values in the job config.
- **Optimization** — `--optimization` accepts `AUTODETECT` or `DISABLED`.
- **Labels** — `--labels=KEY=VALUE,...` on both `jobs create` and `templates create`; keys/values use lowercase letters, numbers, hyphens, and underscores only.
- **Filtering and formatting list output:**

  ```bash
  # Only jobs in the SUCCEEDED state
  gcloud transcoder jobs list --location=us-central1 \
      --filter="state=SUCCEEDED"

  # Compact, scriptable columns
  gcloud transcoder jobs list --location=us-central1 \
      --format="table(name, state, createTime)" --sort-by=createTime

  # Resource URIs only
  gcloud transcoder templates list --location=us-central1 --uri
  ```

## Official documentation

- [Transcoder API documentation home](https://cloud.google.com/transcoder/docs) — product overview and navigation hub.
- [Core concepts overview](https://cloud.google.com/transcoder/docs/concepts/overview) — jobs, templates, containers, codecs, adaptive bitrate, DRM, HDR, and edit lists.
- [Quickstart: transcode a video](https://cloud.google.com/transcoder/docs/quickstart) — end-to-end: enable the API, upload input, create a job, check status.
- [How-to: manage jobs](https://cloud.google.com/transcoder/docs/how-to/jobs) — creating and managing transcoder jobs with gcloud.
- [How-to: manage job templates](https://cloud.google.com/transcoder/docs/how-to/job-templates) — creating and managing job templates with gcloud.
- [gcloud transcoder CLI reference](https://cloud.google.com/sdk/gcloud/reference/transcoder) — full command and flag reference.

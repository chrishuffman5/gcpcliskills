# gcloud dataflow — Dataflow

## Overview

Google Cloud Dataflow is a fully managed service for running batch and streaming data-processing pipelines built with Apache Beam. Use `gcloud dataflow` to launch jobs from classic templates, Flex Templates, or Beam YAML; to list, inspect, drain, cancel, and archive jobs; to snapshot streaming jobs for backup/restore; and to adjust autoscaling on running Streaming Engine jobs. The CLI manages already-built pipelines and templates — you author and build pipelines with the Apache Beam SDK and (for Flex Templates) a container image.

## Quick reference — common workflows

### Enable the API (one-time per project)
```bash
gcloud services enable dataflow.googleapis.com
```

### List and inspect jobs
```bash
# List active jobs (defaults to us-central1 unless --region is given)
gcloud dataflow jobs list --status=active

# List jobs in a region, filtered by name
gcloud dataflow jobs list --region=us-central1 --filter="name=my-wordcount"

# List jobs created more than a week ago
gcloud dataflow jobs list --created-before=-P1W

# Short summary of a job
gcloud dataflow jobs show JOB_ID --region=us-central1

# Full Job object including environment and workflow steps
gcloud dataflow jobs describe JOB_ID --full --region=us-central1
```

### Run a job from a classic template
```bash
# Batch job from a Google-provided or custom GCS template
gcloud dataflow jobs run my-batch-job \
    --gcs-location=gs://YOUR_BUCKET/templates/MyTemplate \
    --region=us-central1 \
    --parameters=inputFile=gs://YOUR_BUCKET/input/data.txt,output=gs://YOUR_BUCKET/output/result

# Streaming job with Streaming Engine and worker bounds
gcloud dataflow jobs run my-streaming-job \
    --gcs-location=gs://YOUR_BUCKET/templates/MyStreamingTemplate \
    --region=us-central1 \
    --enable-streaming-engine \
    --num-workers=2 \
    --max-workers=10 \
    --parameters=topic=projects/MY_PROJECT/topics/my-topic
```

### Build and run a Flex Template
```bash
# Build the template spec from a prebuilt container image
gcloud dataflow flex-template build gs://MY_BUCKET/templates/my-flex-template.json \
    --image=gcr.io/MY_PROJECT/my-pipeline-image \
    --sdk-language=JAVA \
    --metadata-file=/local/path/to/metadata.json

# Run a job from the Flex Template
gcloud dataflow flex-template run my-flex-job \
    --template-file-gcs-location=gs://MY_BUCKET/templates/my-flex-template.json \
    --region=us-central1 \
    --parameters=input=gs://MY_BUCKET/input,output=gs://MY_BUCKET/output \
    --max-workers=5
```

### Stop a job — drain or cancel
```bash
# Drain a streaming job: stop accepting input, finish in-flight elements, then stop
gcloud dataflow jobs drain JOB_ID --region=us-central1

# Cancel immediately (batch or streaming)
gcloud dataflow jobs cancel JOB_ID --region=us-central1

# Force-cancel a stuck job (regular cancel must have been attempted 30+ min prior)
gcloud dataflow jobs cancel JOB_ID --force --region=us-central1

# Archive a job that is already in a terminal state
gcloud dataflow jobs archive JOB_ID --region=us-central1
```

### Snapshot a streaming job and adjust autoscaling
```bash
# Create a snapshot including Pub/Sub sources, with a 7-day TTL
gcloud dataflow snapshots create \
    --job-id=JOB_ID \
    --region=us-central1 \
    --snapshot-sources=true \
    --snapshot-ttl=7d

# List snapshots for a job, then describe one
gcloud dataflow snapshots list --job-id=JOB_ID --region=us-central1
gcloud dataflow snapshots describe SNAPSHOT_ID --region=us-central1

# Re-tune autoscaling bounds on a running Streaming Engine job
gcloud dataflow jobs update-options JOB_ID \
    --region=us-central1 \
    --min-num-workers=5 \
    --max-num-workers=20
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `dataflow flex-template` | [`flex-template.md`](flex-template.md) | 2 | Build and run Dataflow Flex Templates |
| `dataflow jobs` | [`jobs.md`](jobs.md) | 8 | Run, list, inspect, stop, archive, and re-tune Dataflow jobs |
| `dataflow snapshots` | [`snapshots.md`](snapshots.md) | 4 | Create, list, describe, and delete Cloud Dataflow snapshots |
| `dataflow yaml` | [`yaml.md`](yaml.md) | 1 | Launch Beam YAML pipelines on Dataflow |

See [`index.md`](index.md) for a one-line index of all 15 GA commands.

## Common flags & tips

- **Region is everything.** Almost every command takes `--region` (region ID of the job's regional endpoint), defaulting to `us-central1` for most job commands. `snapshots` commands *require* `--region`. `jobs list` is the exception: omit `--region` and it queries all available regions.
- **Job identity.** `jobs run`, `flex-template run`, and `yaml run` take a `JOB_NAME` positional you choose; all other `jobs` and `snapshots` commands take the server-generated `JOB_ID` / `SNAPSHOT_ID` (e.g. `2025-03-15_14_23_56-1234567890123456`).
- **Filtering jobs.** Use `--status` (one of `active`, `terminated`, `all`) plus the standard `--filter`, `--limit` (default 100), and `--sort-by`. Time filters `--created-after` / `--created-before` accept ISO timestamps or relative durations like `-P1W` (see `gcloud topic datetimes`).
```bash
# Show just job IDs and names of active jobs as a table
gcloud dataflow jobs list --status=active \
    --format="table(id, name, state)"

# Get the state of one job
gcloud dataflow jobs describe JOB_ID --region=us-central1 \
    --format="value(currentState)"
```
- **Worker / scaling flags** (`jobs run`, `flex-template *`): `--num-workers`, `--max-workers`, `--worker-machine-type`, `--enable-streaming-engine`, `--disable-public-ips`. Networking: `--network` / `--subnetwork` (and `--worker-region` / `--worker-zone` / `--zone` as a mutually exclusive group).
- **On-the-fly autoscaling** (`jobs update-options`) only works on Streaming Engine jobs: `--min-num-workers`, `--max-num-workers` (1–1000), and `--worker-utilization-hint` (0.1–0.9). Use `--unset-worker-utilization-hint` to revert to defaults — it cannot be combined with `--worker-utilization-hint`.
- **Security & encryption.** `--dataflow-kms-key` (CMEK on job resources) and `--service-account-email` (worker identity) are available on `jobs run` and both `flex-template` commands.
- **Streaming update.** `jobs run` and `flex-template run` support in-place pipeline replacement with `--update` plus `--transform-name-mappings`.
- **Staging.** `--staging-location` / `--temp-location` (Flex/build) and `--gcs-location` (classic template) must be `gs://` URLs. The job's worker service account needs Storage access (e.g. `roles/storage.objectAdmin`) to staging buckets.

## beta / alpha

- **`gcloud beta dataflow`** mirrors the GA groups; `flex-template` and `yaml` first shipped under beta before reaching GA. Use the beta track only when product docs direct you to.
- **`gcloud alpha dataflow`** adds commands not present in GA, including: `jobs config export`, `jobs export-steps`, `jobs resume-unsupported-sdk`, `logs list` (job logs), and `metrics list` (job metrics). Alpha commands may change or be removed without notice.

## Official documentation

- **Product docs home:** https://cloud.google.com/dataflow/docs — Dataflow overview, concepts, guides, and reference.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/dataflow — all `gcloud dataflow` command groups and flags.
- **Quickstarts:** https://cloud.google.com/dataflow/docs/quickstarts — get started via the Job Builder UI and predefined templates.
- **Dataflow templates (Classic vs. Flex):** https://cloud.google.com/dataflow/docs/concepts/dataflow-templates — how to package pipelines for reuse.
- **Running classic templates:** https://cloud.google.com/dataflow/docs/guides/templates/running-templates — how-to for `gcloud dataflow jobs run`.
- **Stopping a pipeline:** https://cloud.google.com/dataflow/docs/guides/stopping-a-pipeline — when to drain vs. cancel a running job.
- **Access control (IAM):** https://cloud.google.com/dataflow/docs/concepts/access-control — predefined roles (Admin, Developer, Viewer, Worker).
- **REST API reference:** https://cloud.google.com/dataflow/docs/reference/rest — API surface served by `dataflow.googleapis.com`.

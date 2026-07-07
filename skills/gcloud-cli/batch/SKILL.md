---
name: gcloud-batch
description: >-
  Batch via gcloud (`gcloud batch`). Manage Batch resources — jobs, tasks.
---

# gcloud batch — Batch

## Overview
Google Cloud Batch is a fully managed service that schedules, queues, and runs batch
computing workloads on Compute Engine VMs. You define a **job** containing one or more
**task groups** (currently a single group, `group0`), each holding identical **tasks** that
run a script or container runnable; Batch handles VM provisioning, autoscaling, retries, and
log routing for you. Reach for `gcloud batch` when you need to run fan-out, fault-tolerant, or
high-throughput compute jobs without managing the underlying cluster. There is no charge for
Batch itself beyond the Compute Engine resources it provisions.

## Quick reference — common workflows

### Enable the required APIs (one-time)
Batch provisions VMs and writes task logs, so enable all three APIs:
```bash
gcloud services enable batch.googleapis.com compute.googleapis.com logging.googleapis.com

# Optional: set a default location so you can omit --location on later commands
gcloud config set batch/location us-central1
```

### 1. Submit a script job from a config file
```bash
# hello.json defines taskGroups -> taskSpec -> runnables (script), taskCount, parallelism
gcloud batch jobs submit my-job \
    --location=us-central1 \
    --config=hello.json
```
The config file may be JSON or YAML; pass `--config=-` to read it from stdin or a HereDoc.

### 2. Submit a job inline without a config file
```bash
# Provide the runnable directly via --script-text (or --script-file-path for a local file)
gcloud batch jobs submit my-script-job \
    --location=us-central1 \
    --script-text='echo Hello from task ${BATCH_TASK_INDEX}' \
    --machine-type=e2-standard-4
```

### 3. Submit a container job on Spot VMs
```bash
gcloud batch jobs submit my-container-job \
    --location=us-central1 \
    --container-image-uri=gcr.io/google-containers/busybox \
    --container-entrypoint=sh \
    --container-commands-file=commands.txt \
    --provisioning-model=SPOT \
    --machine-type=e2-standard-4
```

### 4. Submit with an auto-generated, timestamped job ID
```bash
# Generates an ID like nightly-etl-20260527-140523 (prefix + %Y%m%d-%H%M%S)
gcloud batch jobs submit \
    --location=us-central1 \
    --job-prefix=nightly-etl \
    --config=job.yaml
```

### 5. List, inspect, and monitor jobs and tasks
```bash
# List all jobs across all locations for the default project
gcloud batch jobs list

# List jobs in a specific project/location
gcloud batch jobs list --project=my-project --location=us-central1

# Describe one job (short ID + --location, or a fully qualified name)
gcloud batch jobs describe my-job --location=us-central1

# List every task in group0 of a job
gcloud batch tasks list --job=my-job --location=us-central1

# Describe a single task by index
gcloud batch tasks describe 0 \
    --job=my-job \
    --location=us-central1 \
    --task_group=group0
```

### 6. Cancel and delete a job
```bash
# Cancel a running job (stops scheduling new tasks)
gcloud batch jobs cancel my-job --location=us-central1

# Delete a finished or cancelled job
gcloud batch jobs delete my-job --location=us-central1

# Fully qualified resource name needs no --location
gcloud batch jobs cancel projects/my-project/locations/us-central1/jobs/my-job
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `batch jobs` | [`jobs.md`](jobs.md) | 5 | Manage Batch job resources (submit, list, describe, cancel, delete) |
| `batch tasks` | [`tasks.md`](tasks.md) | 2 | Manage Batch task resources (list, describe) within a job's `group0` |

See [`index.md`](index.md) for a one-line index of all 7 GA commands.

## Common flags & tips
- **Location is everything.** Almost every command needs a `--location` (a Compute Engine
  region such as `us-central1`). Set `gcloud config set batch/location REGION` once, or pass a
  fully qualified resource name (`projects/PROJECT/locations/REGION/jobs/JOB`) and the location
  is inferred — no `--location` needed.
- **Job ID vs. prefix.** On `jobs submit`, give an explicit `JOB` positional ID, or omit it and
  use `--job-prefix` to auto-generate `prefix-%Y%m%d-%H%M%S`. You cannot specify both.
- **Runnable source (exactly one).** `jobs submit` requires one of `--config` (JSON/YAML file,
  `-` for stdin), `--script-text`, `--script-file-path`, or the container flags
  (`--container-image-uri` with `--container-entrypoint` / `--container-commands-file`).
- **Provisioning & sizing.** `--provisioning-model` accepts `SPOT` or `STANDARD`;
  `--machine-type` sets the VM (e.g. `e2-standard-4`); `--priority` takes `0`–`99` (0 lowest).
- **Networking.** Use `--network` together with `--subnetwork` (both required if either is set),
  and `--no-external-ip-address` when VMs should have no public IP.
- **Tasks live in `group0`.** Batch supports a single task group per job, so
  `tasks describe` uses `--task_group=group0` and `tasks list` only needs `--job`.
- **Filtering and sorting.** `jobs list` and `tasks list` support the standard
  `--filter`, `--limit`, `--page-size`, and `--sort-by` flags, e.g.
  `gcloud batch jobs list --location=us-central1 --filter="status.state=SUCCEEDED" --sort-by=~createTime`.

## beta / alpha
- **`gcloud beta batch`** mirrors the GA surface (same `jobs` and `tasks` groups and commands);
  no beta-exclusive features were identified.
- **`gcloud alpha batch`** adds a third command group,
  **`gcloud alpha batch resource-allowances`** (`create`, `delete`, `describe`, `list`,
  `update`), which manages resource-allowance objects that cap resource consumption across jobs
  in a project/location. This is invitation-only alpha and may change without notice.

## Official documentation
- [Batch documentation home](https://cloud.google.com/batch/docs) — product overview, quickstarts, and how-to guides.
- [Get started with Batch](https://cloud.google.com/batch/docs/get-started) — APIs to enable, IAM roles, and prerequisites.
- [Job creation and execution overview](https://cloud.google.com/batch/docs/jobs-overview) — jobs, task groups, and runnables explained.
- [Create and run a basic script job](https://cloud.google.com/batch/docs/create-run-job-basic-script) — end-to-end gcloud walkthrough.
- [Manage a job](https://cloud.google.com/batch/docs/manage-job) — list, describe, cancel, and delete jobs.
- [gcloud batch CLI reference](https://cloud.google.com/sdk/gcloud/reference/batch) — full command/flag reference (GA).
- [gcloud alpha batch CLI reference](https://cloud.google.com/sdk/gcloud/reference/alpha/batch) — alpha surface, including `resource-allowances`.

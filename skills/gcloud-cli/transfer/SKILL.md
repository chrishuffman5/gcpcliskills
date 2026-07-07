---
name: gcloud-transfer
description: >-
  Storage Transfer Service via gcloud (`gcloud transfer`). Manage Transfer Service jobs, operations, and agents — agent-pools, agents, jobs, operations.
---

# gcloud transfer — Storage Transfer Service

## Overview

Storage Transfer Service is a fully-managed service for moving large volumes of data between object stores and filesystems: Google Cloud Storage, Amazon S3 (and S3-compatible), Azure Blob/Data Lake Storage, on-premises POSIX filesystems, HDFS, and publicly-accessible URL lists. Reach for it when you need scheduled, recurring, or one-time bulk transfers (optimized for datasets larger than ~1 TiB), with object filtering, overwrite/delete policies, and metadata preservation. Cloud-to-cloud transfers are agentless; filesystem and HDFS transfers use agents grouped into agent pools.

## Quick reference — common workflows

### Enable the API and authorize the account
```bash
gcloud services enable storagetransfer.googleapis.com

# Print any Transfer Service IAM roles the current account is missing
gcloud transfer authorize

# Add the missing roles
gcloud transfer authorize --add-missing
```

### One-time GCS-to-GCS transfer
```bash
# Immediate, one-time transfer from bucket foo into folder baz/ of bucket bar
gcloud transfer jobs create gs://foo gs://bar/baz/

# Block the terminal until the initial operation completes
gcloud transfer jobs create gs://foo gs://bar/baz/ --no-async
```

### Recurring S3-to-GCS transfer (daily)
```bash
# Named job that repeats every day, with AWS credentials supplied via a creds file
gcloud transfer jobs create s3://my-s3-bucket gs://my-gcs-bucket \
    --name=my-s3-daily-job \
    --source-creds-file=/path/to/aws-creds.json \
    --schedule-repeats-every=1d

# Inspect configuration and latest operation
gcloud transfer jobs describe my-s3-daily-job

# List only enabled jobs
gcloud transfer jobs list --job-statuses=enabled
```

### POSIX filesystem to GCS (agent-based)
```bash
# 1. Create an agent pool (bandwidth limit in MB/s)
gcloud transfer agent-pools create my-pool \
    --display-name="on-prem backups" \
    --bandwidth-limit=100

# 2. Install an agent on the source machine (Docker required)
gcloud transfer agents install --pool=my-pool \
    --creds-file=/path/to/service-account.json \
    --mount-directories=/data/source

# 3. Create the transfer job pointing at the pool
gcloud transfer jobs create posix:///data/source/ gs://my-gcs-bucket \
    --source-agent-pool=my-pool

# 4. Track progress in real time for the job's latest operation
gcloud transfer jobs monitor my-s3-daily-job
```

### Filter objects and control overwrite/delete behavior
```bash
# Only objects with prefix "logs/" modified in the last 7 days; never overwrite
# the destination; delete each source object after it transfers
gcloud transfer jobs create gs://source-bucket gs://dest-bucket \
    --include-prefixes=logs/ \
    --include-modified-after-relative=7d \
    --overwrite-when=never \
    --delete-from=source-after-transfer
```

### Monitor and control a running operation
```bash
# Find the latest operation name from a job
gcloud transfer jobs describe JOB-NAME --format="json(latestOperationName)"

# Watch the operation, then pause / resume / cancel as needed
gcloud transfer operations monitor OPERATION-NAME
gcloud transfer operations pause OPERATION-NAME
gcloud transfer operations resume OPERATION-NAME
gcloud transfer operations cancel OPERATION-NAME
```

### Disable, re-enable, or delete a job
```bash
gcloud transfer jobs update JOB-NAME --status=disabled
gcloud transfer jobs update JOB-NAME --status=enabled

# Remove the schedule so the job runs only on demand
gcloud transfer jobs update JOB-NAME --clear-schedule

# Run an on-demand job, then delete it
gcloud transfer jobs run JOB-NAME
gcloud transfer jobs delete JOB-NAME
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `transfer agent-pools` | [`agent-pools.md`](agent-pools.md) | 5 | manage on-premise transfer agent pools |
| `transfer agents` | [`agents.md`](agents.md) | 2 | manage Transfer Service agents (installed locally in Docker) |
| `transfer jobs` | [`jobs.md`](jobs.md) | 7 | create, run, update, and manage transfer jobs |
| `transfer operations` | [`operations.md`](operations.md) | 6 | monitor and control individual transfer operations |

Top-level command (see [`_commands.md`](_commands.md)):

- `gcloud transfer authorize` — grant the account all Transfer Service roles (`--add-missing` to apply, `--creds-file` to check a service account)

See [`index.md`](index.md) for a one-line index of all 21 commands.

## Common flags & tips

- **Source / destination URIs:** `gs://` (Cloud Storage), `s3://` (Amazon S3), `http://…blob.core.windows.net/…` (Azure), `posix:///abs/path/` (filesystem), `hdfs:///abs/path/` (HDFS), or an `http://` URL pointing at a TSV list of public objects.
- **Credentials:** `--source-creds-file` supplies S3/Azure credentials on `jobs create`/`jobs update`; Cloud Storage sources need none. Agentless cloud-to-cloud transfers rely on the Google-managed service account, which needs object permissions on both buckets.
- **Scheduling:** `--schedule-repeats-every` (duration, e.g. `1d`, `1h30m`), `--schedule-starts`, `--schedule-repeats-until`; `--do-not-run` creates a job without running it immediately; `--clear-schedule` (on `jobs update`) makes a job on-demand only.
- **Object conditions:** `--include-prefixes` / `--exclude-prefixes`, `--match-glob`, and `--include-modified-{before,after}-{absolute,relative}` filter which objects move.
- **Transfer policy:** `--overwrite-when=different|always|never`, `--delete-from=destination-if-unique|source-after-transfer`, `--preserve-metadata=…`, `--custom-storage-class=…`.
- **Agents:** prefer `--mount-directories` over mounting the whole filesystem; `--count` installs multiple agents (8 GB RAM + 4 CPUs each); `--s3-compatible-mode` restricts an agent to S3-compatible sources.
- **Filtering output:** `gcloud transfer jobs list --job-statuses=enabled,disabled`, `gcloud transfer operations list --operation-statuses=failed --expand-table`, and `--format=json`/`--format=yaml` for full API fields (e.g. `--format="json(latestOperationName)"`).
- **Blocking vs async:** add `--no-async` to `jobs create`, `jobs run`, or `agent-pools create` to wait for completion instead of returning immediately.

## beta / alpha

- `gcloud beta transfer` — no distinct beta-only commands; the surface mirrors GA.
- `gcloud alpha transfer` — adds an **`appliances`** command group (`create`, `delete`, `describe`, `list`, `update`) for managing Transfer Appliance orders. Not present in GA or beta; alpha commands may change without notice.

## Official documentation

- [Storage Transfer Service overview](https://cloud.google.com/storage-transfer/docs/overview) — product overview, supported sources/sinks, and feature summary (product docs home).
- [Create and manage transfer jobs](https://cloud.google.com/storage-transfer/docs/create-manage-transfer-console) — creating and managing jobs via Console, gcloud, and the API.
- [On-premises setup](https://cloud.google.com/storage-transfer/docs/on-prem-set-up) — installing agents and configuring agent-based filesystem transfers.
- [Access control](https://cloud.google.com/storage-transfer/docs/access-control) — IAM roles and permissions reference.
- [gcloud transfer CLI reference](https://cloud.google.com/sdk/gcloud/reference/transfer) — full GA command reference.
- [gcloud alpha transfer reference](https://cloud.google.com/sdk/gcloud/reference/alpha/transfer) — alpha surface, including the `appliances` group.

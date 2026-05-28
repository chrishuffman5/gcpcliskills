# gcloud dataflow snapshots

a group of subcommands for working with Cloud Dataflow snapshots

### `gcloud dataflow snapshots create`

Creates a snapshot for a Cloud Dataflow job

Creates a snapshot for a Cloud Dataflow job.

**Synopsis:**
```
gcloud dataflow snapshots create --job-id=JOB_ID --region=REGION_ID
    [--snapshot-sources=SNAPSHOT_SOURCES]
    [--snapshot-ttl=DURATION; default="7d"] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job-id` | JOB_ID |  | The job ID to snapshot. |
| `--region` | REGION_ID |  | The region ID of the snapshot and job's regional endpoint. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshot-sources` | SNAPSHOT_SOURCES |  | If true, snapshots will also be created for the Cloud Pub/Sub sources of the Cloud Dataflow job. |
| `--snapshot-ttl` | DURATION | 7d | Time to live for the snapshot. |


**Examples:**
```bash
To create a Cloud Dataflow snapshot with sources for a running job, run:

    $ gcloud dataflow snapshots create --job-id=JOB_ID \
        --region=JOB_REGION --snapshot-sources=true --snapshot-ttl=7d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/snapshots/create)

---
### `gcloud dataflow snapshots delete`

Delete a Cloud Dataflow snapshot

Delete a Cloud Dataflow snapshot.

**Synopsis:**
```
gcloud dataflow snapshots delete SNAPSHOT_ID --region=REGION_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_ID
   ID of the Cloud Dataflow snapshot.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION_ID |  | Region ID of the snapshot regional endpoint. |


**Examples:**
```bash
To delete an existing Cloud Dataflow snapshot, run:

    $ gcloud dataflow snapshots delete SNAPSHOT_ID \
        --region=SNAPSHOT_REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/snapshots/delete)

---
### `gcloud dataflow snapshots describe`

Describe a Cloud Dataflow snapshot

Describe a Cloud Dataflow snapshot.

**Synopsis:**
```
gcloud dataflow snapshots describe SNAPSHOT_ID --region=REGION_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_ID
   ID of the Cloud Dataflow snapshot.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION_ID |  | Region ID of the snapshot regional endpoint. |


**Examples:**
```bash
To see details about a Cloud Dataflow snapshot, run:

    $ gcloud dataflow snapshots describe SNAPSHOT_ID \
        --region=SNAPSHOT_REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/snapshots/describe)

---
### `gcloud dataflow snapshots list`

List all Cloud Dataflow snapshots in a project in the specified region, optionally filtered by job ID

List all Cloud Dataflow snapshots in a project in the specified region,
optionally filtered by job ID.

**Synopsis:**
```
gcloud dataflow snapshots list --region=REGION_ID [--job-id=JOB_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION_ID |  | The region ID of the snapshot and job's regional endpoint. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job-id` | JOB_ID |  | The job ID to use to filter the snapshots list. |


**Examples:**
```bash
To list all Cloud Dataflow snapshots in the us-central1 region, run:

    $ gcloud dataflow snapshots list --region=us-central1

To list all Cloud Dataflow snapshots for a job, run:

    $ gcloud dataflow snapshots list --job-id=JOB_ID --region=JOB_REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/snapshots/list)

---
# gcloud dataflow jobs

a group of subcommands for working with Dataflow jobs

### `gcloud dataflow jobs archive`

Archives a job

Archives a single job. The job must be in a terminal state, otherwise the
request will be rejected.

This command will require confirmation to run.

**Synopsis:**
```
gcloud dataflow jobs archive JOB_ID [--region=REGION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_ID
   Job ID to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION_ID |  | Region ID of the job's regional endpoint. Defaults to 'us-central1'. |


**Examples:**
```bash
To archive job 2025-03-15_14_23_56-1234567890123456, run:

    $ gcloud dataflow jobs archive 2025-03-15_14_23_56-1234567890123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/archive)

---
### `gcloud dataflow jobs cancel`

Cancels all jobs that match the command line arguments

Cancels all jobs that match the command line arguments.

**Synopsis:**
```
gcloud dataflow jobs cancel JOB_ID [JOB_ID ...] [--force]
    [--region=REGION_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_ID [JOB_ID ...]
   Job IDs to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Forcibly cancels a Dataflow job. Regular cancel must have been attempted at least 30 minutes prior for a job to be force cancelled. |
| `--region` | REGION_ID |  | Region ID of the jobs' regional endpoint. Defaults to 'us-central1'. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/cancel)

---
### `gcloud dataflow jobs describe`

Outputs the Job object resulting from the Get API

By default this will display the Summary view which includes:
  o Project ID
  o Regional Endpoint
  o Job ID
  o Job Name
  o Job Type (Batch vs. Streaming)
  o Job Create Time
  o Job Status (Running, Done, Cancelled, Failed)
  o Job Status Time

Notable values that are only in the full view:
  o Environment (staging Jars, information about workers, etc.)
  o Steps from the workflow graph

**Synopsis:**
```
gcloud dataflow jobs describe JOB_ID [--full] [--region=REGION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_ID
   Job ID to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full` |  |  | Retrieve the full Job rather than the summary view |
| `--region` | REGION_ID |  | Region ID of the job's regional endpoint. Defaults to 'us-central1'. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/describe)

---
### `gcloud dataflow jobs drain`

Drains all jobs that match the command line arguments

Once Drain is triggered, the pipeline will stop accepting new inputs. The
input watermark will be advanced to infinity. Elements already in the
pipeline will continue to be processed. Drained jobs can safely be
cancelled.

**Synopsis:**
```
gcloud dataflow jobs drain JOB_ID [JOB_ID ...] [--region=REGION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_ID [JOB_ID ...]
   Job IDs to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION_ID |  | Region ID of the jobs' regional endpoint. Defaults to 'us-central1'. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/drain)

---
### `gcloud dataflow jobs list`

Lists all jobs in a particular project, optionally filtered by region

By default, 100 jobs in the current project are listed; this can be
overridden with the gcloud --project flag, and the --limit flag.

Using the --region flag will only list jobs from the given regional
endpoint.

**Synopsis:**
```
gcloud dataflow jobs list [--created-after=CREATED_AFTER]
    [--created-before=CREATED_BEFORE] [--region=REGION] [--status=STATUS]
    [--filter=EXPRESSION] [--limit=LIMIT; default=100]
    [--page-size=PAGE_SIZE; default=20] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--created-after` | CREATED_AFTER |  | Filter the jobs to those created after the given time. See $ gcloud topic datetimes for information on time formats. For example, 2018-01-01 is the first day of the year, and -P2W is 2 weeks ago. |
| `--created-before` | CREATED_BEFORE |  | Filter the jobs to those created before the given time. See $ gcloud topic datetimes for information on time formats. |
| `--region` | REGION |  | Only resources from the given region are queried. If not provided, an attempt will be made to query from all available regions. In the event of an outage, jobs from certain regions may not be available. |
| `--status` | one of: active Filters the jobs that are running ordered on the creation timestamp |  | Filter the jobs to those with the selected status. STATUS must be one of: active Filters the jobs that are running ordered on the creation timestamp. all Returns running jobs first, ordered on creation timestamp, then, returns all terminated jobs ordered on the termination timestamp. terminated Filters the jobs that have a terminated state, ordered on the termination timestamp. Example terminated states: Done, Updated, Cancelled, etc. |


**Examples:**
```bash
Filter jobs with the given name:

    $ gcloud dataflow jobs list --filter="name=my-wordcount"

List jobs with from a given region:

    $ gcloud dataflow jobs list --region="europe-west1"

List jobs created this year:

    $ gcloud dataflow jobs list --created-after=2018-01-01

List jobs created more than a week ago:

    $ gcloud dataflow jobs list --created-before=-P1W
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/list)

---
### `gcloud dataflow jobs run`

Runs a job from the specified path

Runs a job from the specified path.

**Synopsis:**
```
gcloud dataflow jobs run JOB_NAME --gcs-location=GCS_LOCATION
    [--additional-experiments=[ADDITIONAL_EXPERIMENTS,...]]
    [--additional-user-labels=[ADDITIONAL_USER_LABELS,...]]
    [--dataflow-kms-key=DATAFLOW_KMS_KEY] [--disable-public-ips]
    [--enable-streaming-engine] [--max-workers=MAX_WORKERS]
    [--network=NETWORK] [--num-workers=NUM_WORKERS]
    [--parameters=[PARAMETERS,...]] [--region=REGION_ID]
    [--service-account-email=SERVICE_ACCOUNT_EMAIL]
    [--staging-location=STAGING_LOCATION] [--subnetwork=SUBNETWORK]
    [--worker-machine-type=WORKER_MACHINE_TYPE]
    [[--[no-]update
      : --transform-name-mappings=[TRANSFORM_NAME_MAPPINGS,...]]]
    [--worker-region=WORKER_REGION | --worker-zone=WORKER_ZONE
      | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_NAME
   The unique name to assign to the job.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-location` | GCS_LOCATION |  | The Google Cloud Storage location of the job template to run. (Must be a URL beginning with 'gs://'.) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-experiments` | [ADDITIONAL_EXPERIMENTS,...] |  | Additional experiments to pass to the job. These experiments are appended to any experiments already set by the template. |
| `--additional-user-labels` | [ADDITIONAL_USER_LABELS,...] |  | Additional user labels to pass to the job. Example: --additional-user-labels='key1=value1,key2=value2' |
| `--dataflow-kms-key` | DATAFLOW_KMS_KEY |  | The Cloud KMS key to protect the job resources. |
| `--disable-public-ips` |  |  | The Cloud Dataflow workers must not use public IP addresses. Overrides the default dataflow/disable_public_ips property value for this command invocation. |
| `--enable-streaming-engine` |  |  | Enabling Streaming Engine for the streaming job. Overrides the default dataflow/enable_streaming_engine property value for this command invocation. |
| `--max-workers` | MAX_WORKERS |  | The maximum number of workers to run. |
| `--network` | NETWORK |  | The Compute Engine network for launching instances to run your pipeline. |
| `--num-workers` | NUM_WORKERS |  | The initial number of workers to use. |
| `--parameters` | [PARAMETERS,...] |  | The parameters to pass to the job. |
| `--region` | REGION_ID |  | Region ID of the job's regional endpoint. Defaults to 'us-central1'. |
| `--service-account-email` | SERVICE_ACCOUNT_EMAIL |  | The service account to run the workers as. |
| `--staging-location` | STAGING_LOCATION |  | The Google Cloud Storage location to stage temporary files. (Must be a URL beginning with 'gs://'.) |
| `--subnetwork` | SUBNETWORK |  | The Compute Engine subnetwork for launching instances to run your pipeline. |
| `--worker-machine-type` | WORKER_MACHINE_TYPE |  | The type of machine to use for workers. Defaults to server-specified. |
| `--[no-]update` |  |  | Set this to true for streaming update jobs. Use --update to enable and --no-update to disable. |
| `--transform-name-mappings` | [TRANSFORM_NAME_MAPPINGS,...] |  | Transform name mappings for the streaming update job. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/run)

---
### `gcloud dataflow jobs show`

Shows a short description of the given job

Shows a short description of the given job.

**Synopsis:**
```
gcloud dataflow jobs show JOB_ID [--environment] [--region=REGION_ID]
    [--steps] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_ID
   Job ID to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` |  |  | If present, the environment will be listed. |
| `--region` | REGION_ID |  | Region ID of the job's regional endpoint. Defaults to 'us-central1'. |
| `--steps` |  |  | If present, the steps will be listed. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/show)

---
### `gcloud dataflow jobs update-options`

Update pipeline options on-the-fly for running Dataflow jobs

This command can modify properties of running Dataflow jobs. Currently,
only updating autoscaling settings for Streaming Engine jobs is supported.

Adjust the autoscaling settings for Streaming Engine Dataflow jobs by
providing at-least one of --min-num-workers or --max-num-workers or
--worker-utilization-hint (or all 3), or --unset-worker-utilization-hint
(which cannot be run at the same time as --worker-utilization-hint but
works with the others). Allow a few minutes for the changes to take effect.

Note that autoscaling settings can only be modified on-the-fly for
Streaming Engine jobs. Attempts to modify batch job or Streaming Appliance
jobs will fail.

**Synopsis:**
```
gcloud dataflow jobs update-options JOB_ID
    [--max-num-workers=MAX_NUM_WORKERS] [--min-num-workers=MIN_NUM_WORKERS]
    [--region=REGION_ID] [--unset-worker-utilization-hint]
    [--worker-utilization-hint=WORKER_UTILIZATION_HINT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_ID
   Job ID to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-num-workers` | MAX_NUM_WORKERS |  | Upper-bound for autoscaling, between 1-1000. Only supported for streaming-engine jobs. |
| `--min-num-workers` | MIN_NUM_WORKERS |  | Lower-bound for autoscaling, between 1-1000. Only supported for streaming-engine jobs. |
| `--region` | REGION_ID |  | Region ID of the job's regional endpoint. Defaults to 'us-central1'. |
| `--unset-worker-utilization-hint` |  |  | Unset --worker-utilization-hint. This causes the job autoscaling to fall back to internal tunings if they exist, or otherwise use the default hint value. |
| `--worker-utilization-hint` | WORKER_UTILIZATION_HINT |  | Target CPU utilization for autoscaling, ranging from 0.1 to 0.9. Only supported for streaming-engine jobs with autoscaling enabled. |


**Examples:**
```bash
Modify autoscaling settings to scale between 5-10 workers:

    $ gcloud dataflow jobs update-options --min-num-workers=5 \
        --max-num-workers=10

Require a job to use at least 2 workers:

    $ gcloud dataflow jobs update-options --min-num-workers=2

Require a job to use at most 20 workers:

    $ gcloud dataflow jobs update-options --max-num-workers=20

Adjust the hint of target worker utilization to 70% for horizontal
autoscaling:

    $ gcloud dataflow jobs update-options --worker-utilization-hint=0.7

"Unset" worker utilization hint so that horizontal scaling will rely on its
default CPU utilization target:

    $ gcloud dataflow jobs update-options --unset-worker-utilization-hint
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/jobs/update-options)

---
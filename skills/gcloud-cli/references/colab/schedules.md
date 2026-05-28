# gcloud colab schedules

manage Colab Enterprise notebook execution schedules

### `gcloud colab schedules create`

Create a schedule

Create a schedule to run a Colab Enterprise notebook execution job.

**Synopsis:**
```
gcloud colab schedules create
    (--cron-schedule=CRON_SCHEDULE --display-name=DISPLAY_NAME
      (--execution-display-name=EXECUTION_DISPLAY_NAME
      --gcs-output-uri=GCS_OUTPUT_URI
      --notebook-runtime-template=NOTEBOOK_RUNTIME_TEMPLATE
      ([--dataform-repository-name=DATAFORM_REPOSITORY_NAME
      : --commit-sha=COMMIT_SHA] | [--gcs-notebook-uri=GCS_NOTEBOOK_URI
      : --generation=GENERATION]) (--service-account=SERVICE_ACCOUNT
      | --user-email=USER_EMAIL)
      : --execution-timeout=EXECUTION_TIMEOUT; default="24h")
      : --enable-queueing --end-time=END_TIME
      --max-concurrent-runs=MAX_CONCURRENT_RUNS;
      default=1 --max-runs=MAX_RUNS --start-time=START_TIME)
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cron-schedule` | CRON_SCHEDULE |  | _[This must be specified.]_ Cron schedule (https://en.wikipedia.org/wiki/Cron) to launch scheduled runs. To explicitly set a timezone to the cron tab, apply a prefix in the cron tab: "CRON_TZ=${IANA_TIME_ZONE}" or "TZ=${IANA_TIME_ZONE}". The ${IANA_TIME_ZONE} may only be a valid string from IANA time zone database. For example, "CRON_TZ=America/New_York 1 * * * ", or "TZ=America/New_York 1 * * * ". This flag argument must be specified if any of the other arguments in this group are specified. |
| `--display-name` | DISPLAY_NAME |  | _[This must be specified.]_ The display name of the schedule. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--enable-queueing` |  |  | _[This must be specified.]_ Enables new scheduled runs to be queued when max_concurrent_runs limit is reached. If set to true, new runs will be queued instead of skipped. |
| `--end-time` | END_TIME |  | _[This must be specified.]_ Timestamp after which no new runs can be scheduled. If specified, the schedule will be completed when either end_time is reached or when scheduled_run_count >= max_run_count. If neither end time nor max_run_count is specified, new runs will keep getting scheduled until this Schedule is paused or deleted. Must be in the RFC 3339 (https://www.rfc-editor.org/rfc/rfc3339.txt) format. E.g. "2026-01-01T00:00:00Z" or "2026-01-01T00:00:00-05:00" |
| `--max-concurrent-runs` | MAX_CONCURRENT_RUNS | 1 | _[This must be specified.]_ Maximum number of runs that can be started concurrently for this Schedule. This is the limit for starting the scheduled requests and not the execution of the notebook execution jobs created by the requests. |
| `--max-runs` | MAX_RUNS |  | _[This must be specified.]_ The max runs for the schedule. |
| `--start-time` | START_TIME |  | _[This must be specified.]_ The timestamp after which the first run can be scheduled. Defaults to the schedule creation time. Must be in the RFC 3339 (https://www.rfc-editor.org/rfc/rfc3339.txt) format. E.g. "2026-01-01T00:00:00Z" or "2026-01-01T00:00:00-05:00" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property colab/region. |


**Examples:**
```bash
To create a schedule in region us-central1 with the following schedule
properties:
  o display name: my-schedule,
  o cron schedule: TZ=America/Los_Angeles * * * * *,
  o maximum concurrent runs allowed: 1,
  o start time: 2025-01-01T00:00:00-06:00,

for a notebook execution job:
  o with display name my-execution,
  o running notebook file from Cloud Storage URI
    gs://my-bucket/my-notebook.ipynb,
  o compute configured from runtime template my-runtime-template-id,
  o running with service account
    my-service-account@my-project.iam.gserviceaccount.com,
  o with results uploaded to Cloud Storage bucket gs://my-bucket/results

Run the following command:        $ gcloud colab schedules create --region=us-central1 \
        --display-name=my-schedule \
        --cron-schedule='TZ=America/Los_Angeles * * * * *' \
        --max-concurrent-runs=1 --start-time=2025-01-01T00:00:00-06:00 \
        --execution-display-name=my-execution \
        --notebook-runtime-template=my-runtime-template-id \
        --gcs-notebook-uri=gs://my-bucket/my-notebook.ipynb \
        --service-account=my-service-account@my-project.iam.gserviceacco\
    unt.com --gcs-output-uri=gs://my-bucket/results
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/create)

---
### `gcloud colab schedules delete`

Delete a schedule

Delete a Colab Enterprise notebook execution schedule.

**Synopsis:**
```
gcloud colab schedules delete (SCHEDULE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schedule resource - Unique, system-generated resource name of the schedule
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schedule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEDULE
     ID of the schedule or fully qualified identifier for the schedule.

     To set the name attribute:
     + provide the argument schedule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the schedule.

     To set the region attribute:
     + provide the argument schedule on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a schedule with id my-schedule, in region us-central1, run:

    $ gcloud colab schedules delete my-schedule --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/delete)

---
### `gcloud colab schedules describe`

Describe a schedule

Describe a Colab Enterprise notebook execution schedule.

**Synopsis:**
```
gcloud colab schedules describe (SCHEDULE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schedule resource - Unique, system-generated resource name of the schedule
to describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schedule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEDULE
     ID of the schedule or fully qualified identifier for the schedule.

     To set the name attribute:
     + provide the argument schedule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the schedule.

     To set the region attribute:
     + provide the argument schedule on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Examples:**
```bash
To describe a schedule with id my-schedule in region us-central1, run:

    $ gcloud colab schedules describe my-schedule --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/describe)

---
### `gcloud colab schedules list`

List your Colab Enterprise notebook execution schedules

List your project's Colab Enterprise notebook execution schedules in a
given region.

**Synopsis:**
```
gcloud colab schedules list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property colab/region. |


**Examples:**
```bash
To list your schedules in region us-central1, run:

    $ gcloud colab schedules list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/list)

---
### `gcloud colab schedules pause`

Pause a schedule

Pause a Colab Enterprise notebook execution schedule.

**Synopsis:**
```
gcloud colab schedules pause (SCHEDULE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schedule resource - Unique, system-generated resource name of the schedule
to pause. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schedule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEDULE
     ID of the schedule or fully qualified identifier for the schedule.

     To set the name attribute:
     + provide the argument schedule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the schedule.

     To set the region attribute:
     + provide the argument schedule on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Examples:**
```bash
To pause a schedule with id my-schedule, in region us-central1, run:

    $ gcloud colab schedules pause my-schedule --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/pause)

---
### `gcloud colab schedules resume`

Resume a schedule

Resume a Colab Enterprise notebook execution schedule.

**Synopsis:**
```
gcloud colab schedules resume (SCHEDULE : --region=REGION)
    [--enable-catch-up] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schedule resource - Unique, system-generated resource name of the schedule
to resume. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schedule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEDULE
     ID of the schedule or fully qualified identifier for the schedule.

     To set the name attribute:
     + provide the argument schedule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the schedule.

     To set the region attribute:
     + provide the argument schedule on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-catch-up` |  |  | Enables backfilling missed runs when the schedule is resumed from PAUSED state. If enabled, all missed runs will be scheduled and new runs will be scheduled after the backfill is complete. |


**Examples:**
```bash
To resume a paused schedule with id my-schedule, in region us-central1,
run:

    $ gcloud colab schedules resume my-schedule --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/resume)

---
### `gcloud colab schedules update`

Update a schedule

Update a Colab Enterprise notebook execution schedule.

**Synopsis:**
```
gcloud colab schedules update (SCHEDULE : --region=REGION)
    (--cron-schedule=CRON_SCHEDULE --display-name=DISPLAY_NAME
      --enable-queueing --end-time=END_TIME
      --max-concurrent-runs=MAX_CONCURRENT_RUNS
      --max-runs=MAX_RUNS --start-time=START_TIME) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schedule resource - Unique, system-generated resource name of the schedule
to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schedule on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEDULE
     ID of the schedule or fully qualified identifier for the schedule.

     To set the name attribute:
     + provide the argument schedule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the schedule.

     To set the region attribute:
     + provide the argument schedule on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cron-schedule` | CRON_SCHEDULE |  | _[At least one of these must be specified:]_ Cron schedule (https://en.wikipedia.org/wiki/Cron) to launch scheduled runs. To explicitly set a timezone to the cron tab, apply a prefix in the cron tab: "CRON_TZ=${IANA_TIME_ZONE}" or "TZ=${IANA_TIME_ZONE}". The ${IANA_TIME_ZONE} may only be a valid string from IANA time zone database. For example, "CRON_TZ=America/New_York 1 * * * ", or "TZ=America/New_York 1 * * * ". |
| `--display-name` | DISPLAY_NAME |  | _[At least one of these must be specified:]_ The display name of the schedule. |
| `--enable-queueing` |  |  | _[At least one of these must be specified:]_ Enables new scheduled runs to be queued when max_concurrent_runs limit is reached. If set to true, new runs will be queued instead of skipped. |
| `--end-time` | END_TIME |  | _[At least one of these must be specified:]_ Timestamp after which no new runs can be scheduled. If specified, the schedule will be completed when either end_time is reached or when scheduled_run_count >= max_run_count. If neither end time nor max_run_count is specified, new runs will keep getting scheduled until this Schedule is paused or deleted. Must be in the RFC 3339 (https://www.rfc-editor.org/rfc/rfc3339.txt) format. E.g. "2026-01-01T00:00:00Z" or "2026-01-01T00:00:00-05:00" |
| `--max-concurrent-runs` | MAX_CONCURRENT_RUNS |  | _[At least one of these must be specified:]_ Maximum number of runs that can be started concurrently for this Schedule. This is the limit for starting the scheduled requests and not the execution of the notebook execution jobs created by the requests. |
| `--max-runs` | MAX_RUNS |  | _[At least one of these must be specified:]_ The max runs for the schedule. |
| `--start-time` | START_TIME |  | _[At least one of these must be specified:]_ The timestamp after which the first run can be scheduled. Defaults to the schedule creation time. Must be in the RFC 3339 (https://www.rfc-editor.org/rfc/rfc3339.txt) format. E.g. "2026-01-01T00:00:00Z" or "2026-01-01T00:00:00-05:00" |


**Examples:**
```bash
To update the cron schedule and max runs of a schedule with id my-schedule,
in region us-central1, run:

    $ gcloud colab schedules update my-schedule --region=us-central1 \
        --cron-schedule='TZ=America/Los_Angeles 0 0 * * 0' --max-runs=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/schedules/update)

---
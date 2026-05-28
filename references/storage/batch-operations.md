# gcloud storage batch-operations

manage Cloud Storage batch operations


## `gcloud storage batch-operations jobs` — manage Cloud Storage batch operations jobs
### `gcloud storage batch-operations jobs cancel`

Cancel a batch-operations job

Cancel the batch operation job.

**Synopsis:**
```
gcloud storage batch-operations jobs cancel BATCH_JOB
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch job resource - The batch job to cancel. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * The default is global.

This must be specified.

  BATCH_JOB
     ID of the batch-job or fully qualified identifier for the batch-job.

     To set the batch-job attribute:
     + provide the argument batch_job on the command line.
```

**Examples:**
```bash
To cancel a batch job with the name my-job in location us-central1:

    $ gcloud storage batch-operations jobs cancel my-job \
      --location=us-central1

To cancel the same batch job with fully specified name:

    $ gcloud storage batch-operations jobs cancel \
      projects/my-project/locations/us-central1/jobs/my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/batch-operations/jobs/cancel)

---
### `gcloud storage batch-operations jobs create`

Create a new batch operation job

Create a batch operation job, allowing you to perform operations such as
deletion, updating metadata, and more on objects in a serverless manner.

**Synopsis:**
```
gcloud storage batch-operations jobs create BATCH_JOB --bucket=BUCKET
    (--included-object-prefixes=[PREFIXES,...]
      | --manifest-location=MANIFEST_LOCATION)
    (--put-metadata=KEY=VALUE,[KEY=VALUE,...]
      | --rewrite-object=KEY=VALUE,[KEY=VALUE,...]
      | [--delete-object : --enable-permanent-object-deletion]
      | --[no-]put-object-event-based-hold
      --[no-]put-object-temporary-hold) [--description=DESCRIPTION]
    [--dry-run]
    [--log-actions=[LOG_ACTIONS,...]
      --log-action-states=[LOG_ACTION_STATES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch job resource - The batch job to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * The default is global.

This must be specified.

  BATCH_JOB
     ID of the batch-job or fully qualified identifier for the batch-job.

     To set the batch-job attribute:
     + provide the argument batch_job on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | Bucket containing the objects that the batch job will operate on. |
| `--manifest-location` | ``MANIFEST_LOCATION or |  | _[Source specifying objects to perform batch operations on. Must be one of]_ |
| `--included-object-prefixes` | ``COMMA_SEPARATED_PREFIXES |  | _[Source specifying objects to perform batch operations on. Must be one of]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description for the batch job. |
| `--dry-run` |  |  | If true, the job will run in dry run mode, returning the total object count and, if the object configuration is a prefix list, the bytes found from source. No transformations will be performed. |


**Examples:**
```bash
The following example command creates a batch job, named my-dry-run, that
performs a dry run of object deletion on bucket my-bucket for objects
specified in the manifest file gs://my-bucket/manifest.csv:

    $ gcloud storage batch-operations jobs create my-dry-run-job \
      --bucket=my-bucket \
      --manifest-location=gs://my-bucket/manifest.csv \
      --delete-object --dry-run

The following example command creates a batch job, named my-job, that
performs object deletion on bucket my-bucket for objects specified in the
manifest file gs://my-bucket/manifest.csv:

    $ gcloud storage batch-operations jobs create my-job \
      --bucket=my-bucket \
      --manifest-location=gs://my-bucket/manifest.csv --delete-object

The following example command creates a batch job, named my-job, that
updates object metadata Content-Disposition to inline, Content-Language to
en, and sets object retention mode to locked on bucket my-bucket for
objects with prefixes prefix1 or prefix2:

    $ gcloud storage batch-operations jobs create my-job \
      --bucket=my-bucket --included-object-prefixes=prefix1,prefix2 \
      --put-metadata=Content-Disposition=inline,Content-Language=en,\
    Retain-Until=2025-01-01T00:00:00Z,Retention-Mode=locked

The following example command creates a batch job, named my-job, that puts
object event based hold on objects in bucket my-bucket with logging config
enabled for corresponding transform action and succeeded and failed action
states:

    $ gcloud storage batch-operations jobs create my-job \
      --bucket=my-bucket --put-object-event-based-hold \
      --put-metadata=Content-Disposition=inline,Content-Language=en \
      --log-actions=transform --log-action-states=succeeded,failed
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/batch-operations/jobs/create)

---
### `gcloud storage batch-operations jobs delete`

Delete a batch-operations job

Delete the batch operation job.

**Synopsis:**
```
gcloud storage batch-operations jobs delete BATCH_JOB
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch job resource - The batch job to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * The default is global.

This must be specified.

  BATCH_JOB
     ID of the batch-job or fully qualified identifier for the batch-job.

     To set the batch-job attribute:
     + provide the argument batch_job on the command line.
```

**Examples:**
```bash
To delete a batch job with the name my-job in location us-central1:

    $ gcloud storage batch-operations jobs delete my-job \
      --location=us-central1

To delete the same batch job with fully specified name:

    $ gcloud storage batch-operations jobs delete \
      projects/my-project/locations/us-central1/jobs/my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/batch-operations/jobs/delete)

---
### `gcloud storage batch-operations jobs describe`

Describe a batch-operations job

Describe the batch operation job.

**Synopsis:**
```
gcloud storage batch-operations jobs describe BATCH_JOB
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch job resource - The batch job to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument batch_job on the command line with a fully
   specified name;
 * The default is global.

This must be specified.

  BATCH_JOB
     ID of the batch-job or fully qualified identifier for the batch-job.

     To set the batch-job attribute:
     + provide the argument batch_job on the command line.
```

**Examples:**
```bash
To describe a batch job with the name my-job:

    $ gcloud storage batch-operations jobs describe my-job

To describe the same batch job with fully specified name:

    $ gcloud storage batch-operations jobs describe \
      projects/my-project/locations/global/jobs/my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/batch-operations/jobs/describe)

---
### `gcloud storage batch-operations jobs list`

List batch-operations jobs

List batch operation jobs.

**Synopsis:**
```
gcloud storage batch-operations jobs list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all batch jobs:

    $ gcloud storage batch-operations jobs list

To list all batch jobs with a page size of 10:

    $ gcloud storage batch-operations jobs list --page-size=10

To list a limit of 20 batch jobs:

    $ gcloud storage batch-operations jobs list --limit=20

To list all batch jobs in JSON format:

    $ gcloud storage batch-operations jobs list --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/batch-operations/jobs/list)

---
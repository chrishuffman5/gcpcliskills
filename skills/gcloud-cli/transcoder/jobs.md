# gcloud transcoder jobs

manage Cloud Transcoder jobs

### `gcloud transcoder jobs create`

Create Transcoder jobs

Create Transcoder jobs.

**Synopsis:**
```
gcloud transcoder jobs create [--batch-mode-priority=BATCH_MODE_PRIORITY]
    [--input-uri=INPUT_URI] [--labels=[KEY=VALUE,...]]
    [--location=LOCATION] [--mode=MODE] [--optimization=OPTIMIZATION]
    [--output-uri=OUTPUT_URI]
    [--file=FILE | --json=JSON | --template-id=TEMPLATE_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--batch-mode-priority` | BATCH_MODE_PRIORITY |  | Processing priority of a batch mode transcoder job. This value will override batch mode priority in job config. |
| `--input-uri` | INPUT_URI |  | Google Cloud Storage URI. This value will override input URI in job config. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--mode` | one of: PROCESSING_MODE_INTERACTIVE, PROCESSING_MODE_BATCH |  | _[+ set the property transcoder/location.]_ Processing mode of transcode job. This value will override mode in job config. MODE must be one of: PROCESSING_MODE_INTERACTIVE, PROCESSING_MODE_BATCH. |
| `--optimization` | one of: AUTODETECT, DISABLED |  | _[+ set the property transcoder/location.]_ Optimization strategy of transcode job. This value will override optimization in job config. OPTIMIZATION must be one of: AUTODETECT, DISABLED. |
| `--output-uri` | OUTPUT_URI |  | _[+ set the property transcoder/location.]_ Google Cloud Storage directory URI (followed by a trailing forward slash). This value will override output URI in job config. |


**Examples:**
```bash
To create a transcoder job with default template, input URI, and output
URI:

    $ gcloud transcoder jobs create --location=us-central1 \
        --input-uri="gs://bucket/input.mp4" \
        --output-uri="gs://bucket/output/"

To create a transcoder job with template id, input URI, and output URI:

    $ gcloud transcoder jobs create --location=us-central1 \
        --input-uri="gs://bucket/input.mp4" \
        --output-uri="gs://bucket/output/" --template-id=my-template

To create a transcoder job with json format configuration:

    $ gcloud transcoder jobs create --location=us-central1 \
        --json="config: json-format"

To create a transcoder job with json format configuration file:

    $ gcloud transcoder jobs create --location=us-central1 \
        --file="config.json"

To create a transcoder job with labels:

    $ gcloud transcoder jobs create --location=us-central1 \
        --file="config.json" --labels=key=value

To create a transcoder job in batch mode:

    $ gcloud transcoder jobs create --location=us-central1 \
        --file="config.json" --mode=PROCESSING_MODE_BATCH

To create a transcoder job in batch mode with priority:

    $ gcloud transcoder jobs create --location=us-central1 \
        --file="config.json" --mode=PROCESSING_MODE_BATCH \
        --batch-mode-priority=3

To create a transcoder job with optimizations disabled:

    $ gcloud transcoder jobs create --location=us-central1 \
        --file="config.json" --optimization=DISABLED
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/jobs/create)

---
### `gcloud transcoder jobs delete`

Delete transcoder jobs

Delete transcoder jobs.

**Synopsis:**
```
gcloud transcoder jobs delete (JOB_NAME : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Transcoder Job name The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job_name on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB_NAME
     ID of the job or fully qualified identifier for the job.

     To set the job_name attribute:
     + provide the argument job_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Transcoder location for resources

     To set the location attribute:
     + provide the argument job_name on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property transcoder/location.
```

**Examples:**
```bash
To delete a transcoder job:

    $ gcloud transcoder jobs delete JOB_NAME --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/jobs/delete)

---
### `gcloud transcoder jobs describe`

Describe transcoder jobs

Describe transcoder jobs.

**Synopsis:**
```
gcloud transcoder jobs describe (JOB_NAME : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Transcoder Job name The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job_name on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB_NAME
     ID of the job or fully qualified identifier for the job.

     To set the job_name attribute:
     + provide the argument job_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Transcoder location for resources

     To set the location attribute:
     + provide the argument job_name on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property transcoder/location.
```

**Examples:**
```bash
To describe a transcoder job:

    $ gcloud transcoder jobs describe JOB_NAME --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/jobs/describe)

---
### `gcloud transcoder jobs list`

List transcoder jobs

List transcoder jobs.

**Synopsis:**
```
gcloud transcoder jobs list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property transcoder/location. |


**Examples:**
```bash
To list transcoder jobs in us-central1:

    $ gcloud transcoder jobs list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transcoder/jobs/list)

---
# gcloud ai model-monitoring-jobs

manage Vertex AI model monitoring jobs

### `gcloud ai model-monitoring-jobs create`

Create a new Vertex AI model monitoring job

Create a new Vertex AI model monitoring job.

**Synopsis:**
```
gcloud ai model-monitoring-jobs create --display-name=DISPLAY_NAME
    --emails=[EMAILS,...] --endpoint=ENDPOINT
    --prediction-sampling-rate=PREDICTION_SAMPLING_RATE
    [--analysis-instance-schema=ANALYSIS_INSTANCE_SCHEMA]
    [--[no-]anomaly-cloud-logging] [--labels=[KEY=VALUE,...]]
    [--log-ttl=LOG_TTL]
    [--monitoring-frequency=MONITORING_FREQUENCY; default=24]
    [--notification-channels=[NOTIFICATION_CHANNELS,...]]
    [--predict-instance-schema=PREDICT_INSTANCE_SCHEMA] [--region=REGION]
    [--sample-predict-request=SAMPLE_PREDICT_REQUEST]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--monitoring-config-from-file=MONITORING_CONFIG_FROM_FILE
      | --feature-attribution-thresholds=[KEY=VALUE,...]
      --feature-thresholds=[KEY=VALUE,...] --target-field=TARGET_FIELD
      --training-sampling-rate=TRAINING_SAMPLING_RATE;
      default=1.0 --bigquery-uri=BIGQUERY_URI | --dataset=DATASET
      | --data-format=DATA_FORMAT --gcs-uris=[GCS_URIS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the model deployment monitoring job. |
| `--emails` | [EMAILS,...] |  | Comma-separated email address list. e.g. --emails=a@gmail.com,b@gmail.com |
| `--endpoint` | ENDPOINT |  | Id of the endpoint. |
| `--prediction-sampling-rate` | PREDICTION_SAMPLING_RATE |  | Prediction sampling rate. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--analysis-instance-schema` | ANALYSIS_INSTANCE_SCHEMA |  | YAML schema file uri(Google Cloud Storage) describing the format of a single instance that you want Tensorflow Data Validation (TFDV) to analyze. |
| `--[no-]anomaly-cloud-logging` |  |  | If true, anomaly will be sent to Cloud Logging. Use --anomaly-cloud-logging to enable and --no-anomaly-cloud-logging to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--log-ttl` | LOG_TTL |  | TTL of BigQuery tables in user projects which stores logs(Day-based unit). |
| `--monitoring-frequency` | MONITORING_FREQUENCY | 24 | Monitoring frequency, unit is 1 hour. |
| `--notification-channels` | [NOTIFICATION_CHANNELS,...] |  | Comma-separated notification channel list. e.g. --notification-channels=projects/fake-project/notificationChannels/123,projects/fake-project/notificationChannels/456 |
| `--predict-instance-schema` | PREDICT_INSTANCE_SCHEMA |  | YAML schema file uri(Google Cloud Storage) describing the format of a single instance, which are given to format this Endpoint's prediction. If not set, predict schema will be generated from collected predict requests. |
| `--sample-predict-request` | SAMPLE_PREDICT_REQUEST |  | _[+ choose one from the prompted list of available regions.]_ Path to a local file containing the body of a JSON object. Same format as [PredictRequest.instances][], this can be set as a replacement of predict-instance-schema. If not set, predict schema will be generated from collected predict requests. An example of a JSON request: {"x": [1, 2], "y": [3, 4]} |


**Examples:**
```bash
To create a model deployment monitoring job under project example in region
us-central1 for endpoint 123, run:

    $ gcloud ai model-monitoring-jobs create --project=example \
        --region=us-central1 --display-name=my_monitoring_job \
        --emails=a@gmail.com,b@gmail.com --endpoint=123 \
        --prediction-sampling-rate=0.2

To create a model deployment monitoring job with drift detection for all
the deployed models under the endpoint 123, run:

    $ gcloud ai model-monitoring-jobs create --project=example \
        --region=us-central1 --display-name=my_monitoring_job \
        --emails=a@gmail.com,b@gmail.com --endpoint=123 \
        --prediction-sampling-rate=0.2 \
        --feature-thresholds=feat1=0.1,feat2=0.2,feat3=0.2,feat4=0.3

To create a model deployment monitoring job with skew detection for all the
deployed models under the endpoint 123, with training dataset from Google
Cloud Storage, run:

    $ gcloud ai model-monitoring-jobs create --project=example \
        --region=us-central1 --display-name=my_monitoring_job \
        --emails=a@gmail.com,b@gmail.com --endpoint=123 \
        --prediction-sampling-rate=0.2 \
        --feature-thresholds=feat1=0.1,feat2=0.2,feat3=0.2,feat4=0.3 \
        --target-field=price --data-format=csv \
        --gcs-uris=gs://test-bucket/dataset.csv

To create a model deployment monitoring job with skew detection for all the
deployed models under the endpoint 123, with training dataset from Vertex
AI dataset 456, run:

    $ gcloud ai model-monitoring-jobs create --project=example \
        --region=us-central1 --display-name=my_monitoring_job \
        --emails=a@gmail.com,b@gmail.com --endpoint=123 \
        --prediction-sampling-rate=0.2 \
        --feature-thresholds=feat1=0.1,feat2=0.2,feat3=0.2,feat4=0.3 \
        --target-field=price --dataset=456

To create a model deployment monitoring job with different drift detection
or skew detection for different deployed models, run:

    $ gcloud ai model-monitoring-jobs create --project=example \
        --region=us-central1 --display-name=my_monitoring_job \
        --emails=a@gmail.com,b@gmail.com --endpoint=123 \
        --prediction-sampling-rate=0.2 \
        --monitoring-config-from-file=your_objective_config.yaml

After creating the monitoring job, be sure to send some predict requests.
It will be used to generate some metadata for analysis purpose, like
predict and analysis instance schema.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/create)

---
### `gcloud ai model-monitoring-jobs delete`

Delete an existing Vertex AI model deployment monitoring job

Delete an existing Vertex AI model deployment monitoring job.

**Synopsis:**
```
gcloud ai model-monitoring-jobs delete (MONITORING_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Monitoring job resource - The model deployment monitoring job to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument monitoring_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MONITORING_JOB
     ID of the monitoring_job or fully qualified identifier for the
     monitoring_job.

     To set the name attribute:
     + provide the argument monitoring_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the monitoring_job.

     To set the region attribute:
     + provide the argument monitoring_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To delete a model deployment monitoring job 123 of project example in
region us-central1, run:

    $ gcloud ai model-monitoring-jobs delete 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/delete)

---
### `gcloud ai model-monitoring-jobs describe`

Get detailed model deployment monitoring job information about the given job id

Get detailed model deployment monitoring job information about the given
job id.

**Synopsis:**
```
gcloud ai model-monitoring-jobs describe (MONITORING_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Monitoring job resource - The model deployment monitoring job to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument monitoring_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MONITORING_JOB
     ID of the monitoring_job or fully qualified identifier for the
     monitoring_job.

     To set the name attribute:
     + provide the argument monitoring_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the monitoring_job.

     To set the region attribute:
     + provide the argument monitoring_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
Describe a model deployment monitoring job 123 of project example in region
us-central1, run:

    $ gcloud ai model-monitoring-jobs describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/describe)

---
### `gcloud ai model-monitoring-jobs list`

List the model deployment monitoring jobs of the given project and region

List the model deployment monitoring jobs of the given project and region.

**Synopsis:**
```
gcloud ai model-monitoring-jobs list [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
List the model deployment monitoring jobs of project example in region
us-central1, run:

    $ gcloud ai model-monitoring-jobs list --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/list)

---
### `gcloud ai model-monitoring-jobs pause`

Pause a running Vertex AI model deployment monitoring job

Pause a running Vertex AI model deployment monitoring job.

**Synopsis:**
```
gcloud ai model-monitoring-jobs pause (MONITORING_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Monitoring job resource - The model deployment monitoring job to pause.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument monitoring_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MONITORING_JOB
     ID of the monitoring_job or fully qualified identifier for the
     monitoring_job.

     To set the name attribute:
     + provide the argument monitoring_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the monitoring_job.

     To set the region attribute:
     + provide the argument monitoring_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To pause a model deployment monitoring job 123 of project example in region
us-central1, run:

    $ gcloud ai model-monitoring-jobs pause 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/pause)

---
### `gcloud ai model-monitoring-jobs resume`

Resume a paused Vertex AI model deployment monitoring job

Resume a paused Vertex AI model deployment monitoring job.

**Synopsis:**
```
gcloud ai model-monitoring-jobs resume (MONITORING_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Monitoring job resource - The model deployment monitoring job to resume.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument monitoring_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MONITORING_JOB
     ID of the monitoring_job or fully qualified identifier for the
     monitoring_job.

     To set the name attribute:
     + provide the argument monitoring_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the monitoring_job.

     To set the region attribute:
     + provide the argument monitoring_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To resume a model deployment monitoring job 123 of project example in
region us-central1, run:

    $ gcloud ai model-monitoring-jobs resume 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/resume)

---
### `gcloud ai model-monitoring-jobs update`

Update an Vertex AI model deployment monitoring job

Update an Vertex AI model deployment monitoring job.

**Synopsis:**
```
gcloud ai model-monitoring-jobs update (MONITORING_JOB : --region=REGION)
    [--analysis-instance-schema=ANALYSIS_INSTANCE_SCHEMA]
    [--[no-]anomaly-cloud-logging] [--display-name=DISPLAY_NAME]
    [--emails=[EMAILS,...]] [--log-ttl=LOG_TTL]
    [--monitoring-frequency=MONITORING_FREQUENCY]
    [--notification-channels=[NOTIFICATION_CHANNELS,...]]
    [--prediction-sampling-rate=PREDICTION_SAMPLING_RATE]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--monitoring-config-from-file=MONITORING_CONFIG_FROM_FILE
      | --feature-attribution-thresholds=[KEY=VALUE,...]
      --feature-thresholds=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Monitoring job resource - The model deployment monitoring job to update.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument monitoring_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MONITORING_JOB
     ID of the monitoring_job or fully qualified identifier for the
     monitoring_job.

     To set the name attribute:
     + provide the argument monitoring_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the monitoring_job.

     To set the region attribute:
     + provide the argument monitoring_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--analysis-instance-schema` | ANALYSIS_INSTANCE_SCHEMA |  | YAML schema file uri(Google Cloud Storage) describing the format of a single instance that you want Tensorflow Data Validation (TFDV) to analyze. |
| `--[no-]anomaly-cloud-logging` |  |  | If true, anomaly will be sent to Cloud Logging. Use --anomaly-cloud-logging to enable and --no-anomaly-cloud-logging to disable. |
| `--display-name` | DISPLAY_NAME |  | Display name of the model deployment monitoring job. |
| `--emails` | [EMAILS,...] |  | Comma-separated email address list. e.g. --emails=a@gmail.com,b@gmail.com |
| `--log-ttl` | LOG_TTL |  | TTL of BigQuery tables in user projects which stores logs(Day-based unit). |
| `--monitoring-frequency` | MONITORING_FREQUENCY |  | Monitoring frequency, unit is 1 hour. |
| `--notification-channels` | [NOTIFICATION_CHANNELS,...] |  | Comma-separated notification channel list. e.g. --notification-channels=projects/fake-project/notificationChannels/123,projects/fake-project/notificationChannels/456 |
| `--prediction-sampling-rate` | PREDICTION_SAMPLING_RATE |  | Prediction sampling rate. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update display name of model deployment monitoring job 123 under project
example in region us-central1, run:

    $ gcloud ai model-monitoring-jobs update 123 \
        --display-name=new-name --project=example --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-monitoring-jobs/update)

---
# gcloud ai hp-tuning-jobs

manage Vertex AI hyperparameter tuning jobs

### `gcloud ai hp-tuning-jobs cancel`

Cancel a running hyperparameter tuning job

If the job is already finished, the command will not perform any operation.

**Synopsis:**
```
gcloud ai hp-tuning-jobs cancel (HPTUNING_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hyperparameter tuning job resource - The hyperparameter tuning job to
cancel. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hptuning_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HPTUNING_JOB
     ID of the hyperparameter tuning job or fully qualified identifier for
     the hyperparameter tuning job.

     To set the name attribute:
     + provide the argument hptuning_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the hyperparameter tuning job.

     To set the region attribute:
     + provide the argument hptuning_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To cancel a job 123 under project example in region us-central1, run:

    $ gcloud ai hp-tuning-jobs cancel 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/hp-tuning-jobs/cancel)

---
### `gcloud ai hp-tuning-jobs create`

Create a hyperparameter tuning job

Create a hyperparameter tuning job.

**Synopsis:**
```
gcloud ai hp-tuning-jobs create --config=CONFIG --display-name=DISPLAY_NAME
    [--algorithm=ALGORITHM] [--enable-dashboard-access]
    [--enable-web-access] [--labels=[KEY=VALUE,...]]
    [--max-trial-count=MAX_TRIAL_COUNT] [--network=NETWORK]
    [--parallel-trial-count=PARALLEL_TRIAL_COUNT] [--region=REGION]
    [--service-account=SERVICE_ACCOUNT]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | Path to the job configuration file. This file should be a YAML document containing a HyperparameterTuningSpec. If an option is specified both in the configuration file **and** via command line arguments, the command line arguments override the configuration file. Example(YAML): displayName: TestHpTuningJob maxTrialCount: 1 parallelTrialCount: 1 studySpec: metrics: - metricId: x goal: MINIMIZE parameters: - parameterId: z integerValueSpec: minValue: 1 maxValue: 100 algorithm: RANDOM_SEARCH trialJobSpec: workerPoolSpecs: - machineSpec: machineType: n1-standard-4 replicaCount: 1 containerSpec: imageUri: gcr.io/ucaip-test/ucaip-training-test |
| `--display-name` | DISPLAY_NAME |  | Display name of the hyperparameter tuning job to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--algorithm` | one of: algorithm-unspecified, grid-search, random-search |  | Search algorithm specified for the given study. ALGORITHM must be one of: algorithm-unspecified, grid-search, random-search. |
| `--enable-dashboard-access` |  |  | Whether you want Vertex AI to enable dashboard built on the training containers. If set to true, you can access the dashboard at the URIs given by CustomJob.web_access_uris or Trial.web_access_uris (within HyperparameterTuningJob.trials). |
| `--enable-web-access` |  |  | Whether you want Vertex AI to enable interactive shell access (https://cloud.google.com/vertex-ai/docs/training/monitor-debug-interactive-shell) to training containers. If set to true, you can access interactive shells at the URIs given by CustomJob.web_access_uris or Trial.web_access_uris (within HyperparameterTuningJob.trials). |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-trial-count` | MAX_TRIAL_COUNT |  | Desired total number of trials. The default value is 1. |
| `--network` | NETWORK |  | Full name of the Google Compute Engine network to which the Job is peered with. Private services access must already have been configured. If unspecified, the Job is not peered with any network. |
| `--parallel-trial-count` | PARALLEL_TRIAL_COUNT |  | Desired number of Trials to run in parallel. The default value is 1. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ choose one from the prompted list of available regions.]_ The email address of a service account to use when running the training appplication. You must have the iam.serviceAccounts.actAs permission for the specified service account. |


**Examples:**
```bash
To create a job named test under project example in region us-central1,
run:

    $ gcloud ai hp-tuning-jobs create --region=us-central1 \
        --project=example --config=config.yaml --display-name=test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/hp-tuning-jobs/create)

---
### `gcloud ai hp-tuning-jobs describe`

Get detail information about the hyperparameter tuning job by given id

**Synopsis:**
```
gcloud ai hp-tuning-jobs describe (HPTUNING_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hyperparameter tuning job resource - The hyperparameter tuning job to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hptuning_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HPTUNING_JOB
     ID of the hyperparameter tuning job or fully qualified identifier for
     the hyperparameter tuning job.

     To set the name attribute:
     + provide the argument hptuning_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the hyperparameter tuning job.

     To set the region attribute:
     + provide the argument hptuning_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To get a job 123 under project example in region us-central1, run:

    $ gcloud ai hp-tuning-jobs describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/hp-tuning-jobs/describe)

---
### `gcloud ai hp-tuning-jobs list`

List existing hyperparameter tuning jobs

List existing hyperparameter tuning jobs.

**Synopsis:**
```
gcloud ai hp-tuning-jobs list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
To list the jobs of project example in region us-central1, run:

    $ gcloud ai hp-tuning-jobs list --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/hp-tuning-jobs/list)

---
### `gcloud ai hp-tuning-jobs stream-logs`

Stream logs from a running Vertex AI hyperparameter tuning job

**Synopsis:**
```
gcloud ai hp-tuning-jobs stream-logs (HPTUNING_JOB : --region=REGION)
    [--allow-multiline-logs]
    [--polling-interval=POLLING_INTERVAL; default=60]
    [--task-name=TASK_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hyperparameter tuning job resource - The hyperparameter tuning job to
fetch stream log. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hptuning_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HPTUNING_JOB
     ID of the hyperparameter tuning job or fully qualified identifier for
     the hyperparameter tuning job.

     To set the name attribute:
     + provide the argument hptuning_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the hyperparameter tuning job.

     To set the region attribute:
     + provide the argument hptuning_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-multiline-logs` |  |  | Output multiline log messages as single records. |
| `--polling-interval` | POLLING_INTERVAL | 60 | Number of seconds to wait between efforts to fetch the latest log messages. |
| `--task-name` | TASK_NAME |  | If set, display only the logs for this particular task. |


**Examples:**
```bash
To stream logs of a hyperparameter tuning job, run:

    $ gcloud ai hp-tuning-jobs stream-logs stream-logs HP_TUNING_JOB
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/hp-tuning-jobs/stream-logs)

---
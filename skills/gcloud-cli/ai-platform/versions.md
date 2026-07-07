# gcloud ai-platform versions

AI Platform Versions commands

### `gcloud ai-platform versions create`

Create a new AI Platform version

Creates a new version of an AI Platform model.

For more details on managing AI Platform models and versions see
https://cloud.google.com/ai-platform/prediction/docs/managing-models-jobs

**Synopsis:**
```
gcloud ai-platform versions create VERSION --model=MODEL
    [--accelerator=[count=COUNT],[type=TYPE]] [--async] [--config=CONFIG]
    [--description=DESCRIPTION] [--framework=FRAMEWORK]
    [--labels=[KEY=VALUE,...]] [--machine-type=MACHINE_TYPE]
    [--origin=ORIGIN] [--python-version=PYTHON_VERSION] [--region=REGION]
    [--runtime-version=RUNTIME_VERSION] [--staging-bucket=STAGING_BUCKET]
    [--max-nodes=MAX_NODES
      --metric-targets=[METRIC-NAME=TARGET,...] --min-nodes=MIN_NODES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the model version.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | Name of the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Manage the accelerator config for GPU serving. When deploying a model with Compute Engine Machine Types, a GPU accelerator may also be selected. type The type of the accelerator. Choices are 'nvidia-tesla-a100', 'nvidia-tesla-k80', 'nvidia-tesla-p100', 'nvidia-tesla-p4', 'nvidia-tesla-t4', 'nvidia-tesla-v100'. count The number of accelerators to attach to each machine running the job. If not specified, the default value is 1. Your model must be specially designed to accommodate more than 1 accelerator per machine. To configure how many replicas your model has, set the manualScaling or autoScaling parameters. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--config` | CONFIG |  | Path to a YAML configuration file containing configuration parameters for the Version (https://cloud.google.com/ai-platform/prediction/docs/reference/rest/v1/projects.models.versions) to create. The file is in YAML format. Note that not all attributes of a version are configurable; available attributes (with example values) are: description: A free-form description of the version. deploymentUri: gs://path/to/source runtimeVersion: '2.1' # Set only one of either manualScaling or autoScaling. manualScaling: nodes: 10 # The number of nodes to allocate for this model. autoScaling: minNodes: 0 # The minimum number of nodes to allocate for this model. labels: user-defined-key: user-defined-value The name of the version must always be specified via the required VERSION argument. Only one of manualScaling or autoScaling can be specified. If both are specified in same yaml file an error will be returned. If an option is specified both in the configuration file and via command-line arguments, the command-line arguments override the configuration file. |
| `--description` | DESCRIPTION |  | Description of the version. |
| `--framework` | one of: scikit-learn, tensorflow, xgboost |  | ML framework used to train this version of the model. If not specified, defaults to 'tensorflow'. FRAMEWORK must be one of: scikit-learn, tensorflow, xgboost. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--machine-type` | MACHINE_TYPE |  | Type of machine on which to serve the model. Currently only applies to online prediction. For available machine types, see https://cloud.google.com/ai-platform/prediction/docs/machine-types-online-prediction#available_machine_types. |
| `--origin` | ORIGIN |  | Location of model/ "directory" (see https://cloud.google.com/ai-platform/prediction/docs/deploying-models#upload-model). This overrides deploymentUri in the --config file. If this flag is not passed, deploymentUri must be specified in the file from --config. Can be a Cloud Storage (gs://) path or local file path (no prefix). In the latter case the files will be uploaded to Cloud Storage and a --staging-bucket argument is required. |
| `--python-version` | PYTHON_VERSION |  | Version of Python used when creating the version. Choices are 3.7, 3.5, and 2.7. However, this value must be compatible with the chosen runtime version for the job. Must be used with a compatible runtime version: * 3.7 is compatible with runtime versions 1.15 and later. * 3.5 is compatible with runtime versions 1.4 through 1.14. * 2.7 is compatible with runtime versions 1.15 and earlier. |
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |
| `--runtime-version` | RUNTIME_VERSION |  | AI Platform runtime version for this job. Must be specified unless --master-image-uri is specified instead. It is defined in documentation along with the list of supported versions: https://cloud.google.com/ai-platform/prediction/docs/runtime-version-list |
| `--staging-bucket` | STAGING_BUCKET |  | Bucket in which to stage training archives. Required only if a file upload is necessary (that is, other flags include local paths) and no other flags implicitly specify an upload path. |


**Examples:**
```bash
To create an AI Platform version model with the version ID 'versionId' and
with the name 'model-name', run:

    $ gcloud ai-platform versions create versionId --model=model-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/versions/create)

---
### `gcloud ai-platform versions delete`

Delete an existing AI Platform version

Delete an existing AI Platform version.

**Synopsis:**
```
gcloud ai-platform versions delete VERSION --model=MODEL [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the model version.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | Name of the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/versions/delete)

---
### `gcloud ai-platform versions describe`

Describe an existing AI Platform version

Describe an existing AI Platform version.

**Synopsis:**
```
gcloud ai-platform versions describe VERSION --model=MODEL
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the model version.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | Name of the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/versions/describe)

---
### `gcloud ai-platform versions list`

List existing AI Platform versions

List existing AI Platform versions.

**Synopsis:**
```
gcloud ai-platform versions list --model=MODEL [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | Name of the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/versions/list)

---
### `gcloud ai-platform versions set-default`

Sets an existing AI Platform version as the default for its model

Sets an existing AI Platform version as the default for its model.

gcloud ai-platform versions set-default sets an existing AI Platform
version as the default for its model. Only one version may be the default
for a given version.

**Synopsis:**
```
gcloud ai-platform versions set-default VERSION --model=MODEL
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the model version.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | Name of the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/versions/set-default)

---
### `gcloud ai-platform versions update`

Update an AI Platform version

Update an AI Platform version.

**Synopsis:**
```
gcloud ai-platform versions update (VERSION : --model=MODEL)
    [--config=YAML_FILE] [--description=DESCRIPTION] [--region=REGION]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The AI Platform model to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --model=MODEL
     Model for the version.

     To set the model attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --model on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | YAML_FILE |  | Path to a YAML configuration file containing configuration parameters for the version (https://cloud.google.com/ml/reference/rest/v1/projects.models.versions) to create. The file is in YAML format. Note that not all attributes of a version are configurable; available attributes (with example values) are: description: A free-form description of the version. manualScaling: nodes: 10 # The number of nodes to allocate for this model. autoScaling: minNodes: 0 # The minimum number of nodes to allocate for this model. maxNodes: 1 # The maxinum number of nodes to allocate for this model. requestLoggingconfig: bigqueryTableName: someTable # Fully qualified BigQuery table name. samplingPercentage: 0.5 # Percentage of requests to be logged. The name of the version must always be specified via the required VERSION argument. Only one of manualScaling or autoScaling can be specified. If both are specified in same yaml file, an error will be returned. Labels cannot currently be set in the config.yaml; please use the command-line flags to alter them. If an option is specified both in the configuration file and via command-line arguments, the command-line arguments override the configuration file. |
| `--description` | DESCRIPTION |  | Description of the version. |
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/versions/update)

---
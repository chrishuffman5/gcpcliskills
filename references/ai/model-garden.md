# gcloud ai model-garden

interact with and manage resources in Vertex Model Garden


## `gcloud ai model-garden models` — list and use Model Garden models
### `gcloud ai model-garden models deploy`

Deploy a model in Model Garden to a Vertex AI endpoint

**Synopsis:**
```
gcloud ai model-garden models deploy --model=MODEL
    [--accelerator-count=ACCELERATOR_COUNT]
    [--accelerator-type=ACCELERATOR_TYPE] [--accept-eula] [--asynchronous]
    [--container-args=[ARG,...]] [--container-command=[COMMAND,...]]
    [--container-deployment-timeout-seconds=CONTAINER_DEPLOYMENT_TIMEOUT_SECONDS]
    [--container-env-vars=[KEY=VALUE,...]]
    [--container-grpc-ports=[PORT,...]]
    [--container-health-probe-exec=[HEALTH_PROBE_EXEC,...]]
    [--container-health-probe-period-seconds=CONTAINER_HEALTH_PROBE_PERIOD_SECONDS]
    [--container-health-probe-timeout-seconds=CONTAINER_HEALTH_PROBE_TIMEOUT_SECONDS]
    [--container-health-route=CONTAINER_HEALTH_ROUTE]
    [--container-image-uri=CONTAINER_IMAGE_URI]
    [--container-ports=[PORT,...]]
    [--container-predict-route=CONTAINER_PREDICT_ROUTE]
    [--container-shared-memory-size-mb=CONTAINER_SHARED_MEMORY_SIZE_MB]
    [--container-startup-probe-exec=[STARTUP_PROBE_EXEC,...]]
    [--container-startup-probe-period-seconds=CONTAINER_STARTUP_PROBE_PERIOD_SECONDS]
    [--container-startup-probe-timeout-seconds=CONTAINER_STARTUP_PROBE_TIMEOUT_SECONDS]
    [--enable-fast-tryout] [--endpoint-display-name=ENDPOINT_DISPLAY_NAME]
    [--hugging-face-access-token=HUGGING_FACE_ACCESS_TOKEN]
    [--machine-type=MACHINE_TYPE] [--region=REGION]
    [--reservation-affinity=[key=KEY],
      [reservation-affinity-type=RESERVATION-AFFINITY-TYPE],
      [values=VALUES]] [--spot] [--use-dedicated-endpoint]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model to be deployed. If it is a Model Garden model, it should be in the format of {publisher_name}/{model_name}@{model_version_name}, e.g. google/gemma2@gemma-2-2b. If it is a Hugging Face model, it should be in the convention of Hugging Face models, e.g. meta-llama/Meta-Llama-3-8B. If it is a Custom Weights model, it should be in the format of gs://{gcs_bucket_uri}, e.g. gs://-model-garden-public-us/llama3.1/Meta-Llama-3.1-8B-Instruct. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator-count` | ACCELERATOR_COUNT |  | The accelerator count to serve the model. Accelerator count should be non-negative. |
| `--accelerator-type` | ACCELERATOR_TYPE |  | The accelerator type to serve the model. It should be a supported accelerator type from the verified deployment configurations of the model. Use gcloud ai model-garden models list-deployment-config to check the supported accelerator types. |
| `--accept-eula` |  |  | When set, the user accepts the End User License Agreement (EULA) of the model. |
| `--asynchronous` |  |  | If set to true, the command will terminate immediately and not keep polling the operation status. |
| `--container-args` | [ARG,...] |  | Comma-separated arguments passed to the command run by the container image. If not specified and no --command is provided, the container image's default command is used. |
| `--container-command` | [COMMAND,...] |  | Entrypoint for the container image. If not specified, the container image's default entrypoint is run. |
| `--container-deployment-timeout-seconds` | CONTAINER_DEPLOYMENT_TIMEOUT_SECONDS |  | Deployment timeout in seconds. |
| `--container-env-vars` | [KEY=VALUE,...] |  | List of key-value pairs to set as environment variables. |
| `--container-grpc-ports` | [PORT,...] |  | Container ports to receive grpc requests at. Must be a number between 1 and 65535, inclusive. |
| `--container-health-probe-exec` | [HEALTH_PROBE_EXEC,...] |  | Exec specifies the action to take. Used by health probe. An example of this argument would be ["cat", "/tmp/healthy"]. |
| `--container-health-probe-period-seconds` | CONTAINER_HEALTH_PROBE_PERIOD_SECONDS |  | How often (in seconds) to perform the health probe. Default to 10 seconds. Minimum value is 1. |
| `--container-health-probe-timeout-seconds` | CONTAINER_HEALTH_PROBE_TIMEOUT_SECONDS |  | Number of seconds after which the health probe times out. Defaults to 1 second. Minimum value is 1. |
| `--container-health-route` | CONTAINER_HEALTH_ROUTE |  | HTTP path to send health checks to inside the container. |
| `--container-image-uri` | CONTAINER_IMAGE_URI |  | URI of the Model serving container file in the Container Registry (e.g. gcr.io/myproject/server:latest). |
| `--container-ports` | [PORT,...] |  | Container ports to receive http requests at. Must be a number between 1 and 65535, inclusive. |
| `--container-predict-route` | CONTAINER_PREDICT_ROUTE |  | HTTP path to send prediction requests to inside the container. |
| `--container-shared-memory-size-mb` | CONTAINER_SHARED_MEMORY_SIZE_MB |  | The amount of the VM memory to reserve as the shared memory for the model in megabytes. |
| `--container-startup-probe-exec` | [STARTUP_PROBE_EXEC,...] |  | Exec specifies the action to take. Used by startup probe. An example of this argument would be ["cat", "/tmp/healthy"]. |
| `--container-startup-probe-period-seconds` | CONTAINER_STARTUP_PROBE_PERIOD_SECONDS |  | How often (in seconds) to perform the startup probe. Default to 10 seconds. Minimum value is 1. |
| `--container-startup-probe-timeout-seconds` | CONTAINER_STARTUP_PROBE_TIMEOUT_SECONDS |  | Number of seconds after which the startup probe times out. Defaults to 1 second. Minimum value is 1. |
| `--enable-fast-tryout` |  |  | If True, model will be deployed using faster deployment path. Useful for quick experiments. Not for production workloads. Only available for most popular models with certain machine types. |
| `--endpoint-display-name` | ENDPOINT_DISPLAY_NAME |  | Display name of the endpoint with the deployed model. |
| `--hugging-face-access-token` | HUGGING_FACE_ACCESS_TOKEN |  | The access token from Hugging Face needed to read the model artifacts of gated models. It is only needed when the Hugging Face model to deploy is gated. |
| `--machine-type` | MACHINE_TYPE |  | The machine type to deploy the model to. It should be a supported machine type from the deployment configurations of the model. Use gcloud ai model-garden models list-deployment-config to check the supported machine types. |
| `--reservation-affinity` | [key=KEY],[reservation-affinity-type=RESERVATION-AFFINITY-TYPE],[values=VALUES] |  | _[+ choose one from the prompted list of available regions.]_ A ReservationAffinity can be used to configure a Vertex AI resource (e.g., a DeployedModel) to draw its Compute Engine resources from a Shared Reservation, or exclusively from on-demand capacity. |
| `--spot` |  |  | _[+ choose one from the prompted list of available regions.]_ If true, schedule the deployment workload on Spot VM. |
| `--use-dedicated-endpoint` |  |  | _[+ choose one from the prompted list of available regions.]_ If true, the endpoint will be exposed through a dedicated DNS. Your request to the dedicated DNS will be isolated from other users' traffic and will have better performance and reliability. |


**Examples:**
```bash
To deploy a Model Garden model google/gemma2/gemma2-9b under project
example in region us-central1, run:

    $ gcloud ai model-garden models deploy \
        --model=google/gemma2@gemma-2-9b --project=example \
        --region=us-central1

To deploy a Hugging Face model meta-llama/Meta-Llama-3-8B under project
example in region us-central1, run:

    $ gcloud ai model-garden models deploy \
        --model=meta-llama/Meta-Llama-3-8B \
        --hugging-face-access-token={hf_token} --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-garden/models/deploy)

---
### `gcloud ai model-garden models list`

List the publisher models in Model Garden

This command lists either all models in Model Garden or all Hugging Face
models supported by Model Garden.

**Synopsis:**
```
gcloud ai model-garden models list [--can-deploy-hugging-face-models]
    [--full-resource-name] [--model-filter=MODEL_FILTER]
    [--filter=EXPRESSION] [--limit=LIMIT; default=1000]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--can-deploy-hugging-face-models` |  |  | Whether to only list Hugging Face models that can be deployed. |
| `--full-resource-name` |  |  | Whether to return the full resource name of the model. |
| `--model-filter` | MODEL_FILTER |  | Filter to apply to the model names or the display names of the list of models. |


**Examples:**
```bash
To list all models in Model Garden, run:

    $ gcloud ai model-garden models list

To list Hugging Face models that can be deployed in Model Garden, run:

    $ gcloud ai model-garden models list --can-deploy-hugging-face-models

To list models with gemma in their names, run:

    $ gcloud ai model-garden models list --model-filter=gemma

Note: Since the number of Hugging Face models is large, the default limit
is set to 500 with a page size of 100 when listing supported Hugging Face
models. To override the limit or page size, specify the --limit or
--page-size flags, respectively. To list all models in Model Garden, use
--limit=unlimited.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-garden/models/list)

---
### `gcloud ai model-garden models list-deployment-config`

List the machine specifications supported by and verified for a model in Model Garden

**Synopsis:**
```
gcloud ai model-garden models list-deployment-config --model=MODEL
    [--hugging-face-access-token=HUGGING_FACE_ACCESS_TOKEN]
    [--filter=EXPRESSION] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model to be deployed. If it is a Model Garden model, it should be in the format of {publisher_name}/{model_name}@{model_version_name}, e.g. google/gemma2@gemma-2-2b. If it is a Hugging Face model, it should be in the convention of Hugging Face models, e.g. meta-llama/Meta-Llama-3-8B. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hugging-face-access-token` | HUGGING_FACE_ACCESS_TOKEN |  | The access token from Hugging Face needed to read the model artifacts of gated models in order to generate the deployment configs. It is only needed when the Hugging Face model to deploy is gated and not verified by Model Garden. You can use the gcloud ai alpha/beta model-garden models list command to find out which ones are verified by Model Garden. |


**Examples:**
```bash
To list the supported machine specifications for google/gemma2@gemma-2-9b,
run:

    $ gcloud ai model-garden models list-deployment-config \
        --model=google/gemma2@gemma-2-9b

To list the supported machine specifications for a Hugging Face model
meta-llama/Meta-Llama-3-8B, run:

    $ gcloud ai model-garden models list-deployment-config \
        --model=meta-llama/Meta-Llama-3-8B
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/model-garden/models/list-deployment-config)

---
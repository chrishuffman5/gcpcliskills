# gcloud ai endpoints

manage Vertex AI endpoints

### `gcloud ai endpoints create`

Create a new Vertex AI endpoint

**Synopsis:**
```
gcloud ai endpoints create --display-name=DISPLAY_NAME
    [--description=DESCRIPTION]
    [--encryption-kms-key-name=ENCRYPTION_KMS_KEY_NAME]
    [--endpoint-id=ENDPOINT_ID] [--labels=[KEY=VALUE,...]]
    [--network=NETWORK] [--region=REGION]
    [--request-response-logging-rate=REQUEST_RESPONSE_LOGGING_RATE
      --request-response-logging-table=REQUEST_RESPONSE_LOGGING_TABLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the endpoint. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the endpoint. |
| `--encryption-kms-key-name` | ENCRYPTION_KMS_KEY_NAME |  | The Cloud KMS resource identifier of the customer managed encryption key used to protect a resource. Has the form: projects/my-project/locations/my-region/keyRings/my-kr/cryptoKeys/my-key. The key needs to be in the same region as where the compute resource is created. |
| `--endpoint-id` | ENDPOINT_ID |  | User-specified ID of the endpoint. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--network` | NETWORK |  | The full name of the Google Compute Engine network to which the endpoint should be peered. |
| `--request-response-logging-rate` | REQUEST_RESPONSE_LOGGING_RATE |  | _[+ choose one from the prompted list of available regions.]_ Prediction request & response sampling rate for logging to BigQuery table. |
| `--request-response-logging-table` | REQUEST_RESPONSE_LOGGING_TABLE |  | _[+ choose one from the prompted list of available regions.]_ BigQuery table uri for prediction request & response logging. You can provide table uri that does not exist, it will be created for you. Value should be provided in format: bq://PROJECT_ID/DATASET/TABLE |


**Examples:**
```bash
To create an endpoint under project example in region us-central1, run:

    $ gcloud ai endpoints create --project=example \
        --region=us-central1 --display-name=my_endpoint
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/create)

---
### `gcloud ai endpoints delete`

Delete an existing Vertex AI endpoint

**Synopsis:**
```
gcloud ai endpoints delete (ENDPOINT : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To delete an endpoint 123 under project example in region us-central1, run:

    $ gcloud ai endpoints delete 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/delete)

---
### `gcloud ai endpoints deploy-model`

Deploy a model to an existing Vertex AI endpoint

**Synopsis:**
```
gcloud ai endpoints deploy-model (ENDPOINT : --region=REGION)
    --display-name=DISPLAY_NAME --model=MODEL
    [--accelerator=[count=COUNT],[type=TYPE]]
    [--autoscaling-metric-specs=[METRIC-NAME=TARGET,...]]
    [--deployed-model-id=DEPLOYED_MODEL_ID] [--disable-container-logging]
    [--enable-access-logging] [--gpu-partition-size=GPU_PARTITION_SIZE]
    [--machine-type=MACHINE_TYPE] [--max-replica-count=MAX_REPLICA_COUNT]
    [--min-replica-count=MIN_REPLICA_COUNT]
    [--required-replica-count=REQUIRED_REPLICA_COUNT]
    [--reservation-affinity=[key=KEY],
      [reservation-affinity-type=RESERVATION-AFFINITY-TYPE],
      [values=VALUES]] [--service-account=SERVICE_ACCOUNT] [--spot]
    [--traffic-split=[DEPLOYED_MODEL_ID=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to deploy a model to. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the deployed model. |
| `--model` | MODEL |  | ID of the uploaded model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Manage the accelerator config for GPU serving. When deploying a model with Compute Engine Machine Types, a GPU accelerator may also be selected. type The type of the accelerator. Choices are 'nvidia-a100-80gb', 'nvidia-b200', 'nvidia-gb200', 'nvidia-h100-80gb', 'nvidia-h100-mega-80gb', 'nvidia-h200-141gb', 'nvidia-l4', 'nvidia-rtx-pro-6000', 'nvidia-tesla-a100', 'nvidia-tesla-k80', 'nvidia-tesla-p100', 'nvidia-tesla-p4', 'nvidia-tesla-t4', 'nvidia-tesla-v100'. count The number of accelerators to attach to each machine running the job. This is usually 1. If not specified, the default value is 1. For example: --accelerator=type=nvidia-tesla-k80,count=1 |
| `--autoscaling-metric-specs` | [METRIC-NAME=TARGET,...] |  | Metric specifications that control autoscaling behavior. At most one entry is allowed per metric. METRIC-NAME Resource metric name. Choices are 'cpu-usage', 'gpu-duty-cycle', 'request-counts-per-minute'. TARGET Target value for the given metric. For cpu-usage and gpu-duty-cycle, the target is the target resource utilization in percentage (1% - 100%). For request-counts-per-minute, the target is the number of requests per minute per replica. For example, to set target CPU usage to 70% and target requests to 600 per minute per replica: --autoscaling-metric-specs=cpu-usage=70,request-counts-per-minute=600 |
| `--deployed-model-id` | DEPLOYED_MODEL_ID |  | User-specified ID of the deployed-model. |
| `--disable-container-logging` |  |  | For custom-trained Models and AutoML Tabular Models, the container of the deployed model instances will send stderr and stdout streams to Cloud Logging by default. Please note that the logs incur cost, which are subject to Cloud Logging pricing (https://cloud.google.com/stackdriver/pricing). User can disable container logging by setting this flag to true. |
| `--enable-access-logging` |  |  | If true, online prediction access logs are sent to Cloud Logging. These logs are standard server access logs, containing information like timestamp and latency for each prediction request. |
| `--gpu-partition-size` | GPU_PARTITION_SIZE |  | The partition size of the GPU accelerator. This can be used to partition a single GPU into multiple smaller GPU instances. See https://cloud.google.com/kubernetes-engine/docs/how-to/gpus-multi#multi-instance_gpu_partitions for more details. |
| `--machine-type` | MACHINE_TYPE |  | The machine resources to be used for each node of this deployment. For available machine types, see https://cloud.google.com/ai-platform-unified/docs/predictions/machine-types. |
| `--max-replica-count` | MAX_REPLICA_COUNT |  | Maximum number of machine replicas for the deployment resources the model will be deployed on. |
| `--min-replica-count` | MIN_REPLICA_COUNT |  | Minimum number of machine replicas for the deployment resources the model will be deployed on. For normal deployments, the value must be equal to or larger than 1. If the value is 0, the deployment will be enrolled in the scale-to-zero feature. If not specified and the uploaded models use dedicated resources, the default value is 1. NOTE: DeploymentResourcePools (model-cohosting) is currently not supported for scale-to-zero deployments. |
| `--required-replica-count` | REQUIRED_REPLICA_COUNT |  | Required number of machine replicas for the deployment resources the model will be considered successfully deployed. This value must be greater than or equal to 1 and less than or equal to min-replica-count. |
| `--reservation-affinity` | [key=KEY],[reservation-affinity-type=RESERVATION-AFFINITY-TYPE],[values=VALUES] |  | A ReservationAffinity can be used to configure a Vertex AI resource (e.g., a DeployedModel) to draw its Compute Engine resources from a Shared Reservation, or exclusively from on-demand capacity. |
| `--service-account` | SERVICE_ACCOUNT |  | Service account that the deployed model's container runs as. Specify the email address of the service account. If this service account is not specified, the container runs as a service account that doesn't have access to the resource project. |
| `--spot` |  |  | If true, schedule the deployment workload on Spot VMs. |
| `--traffic-split` | [DEPLOYED_MODEL_ID=VALUE,...] |  | List of pairs of deployed model id and value to set as traffic split. |


**Examples:**
```bash
To deploy a model 456 to an endpoint 123 under project example in region
us-central1, run:

    $ gcloud ai endpoints deploy-model 123 --project=example \
        --region=us-central1 --model=456 \
        --display-name=my_deployed_model
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/deploy-model)

---
### `gcloud ai endpoints describe`

Describe an existing Vertex AI endpoint

**Synopsis:**
```
gcloud ai endpoints describe (ENDPOINT : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To describe an endpoint 123 under project example in region us-central1,
run:

    $ gcloud ai endpoints describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/describe)

---
### `gcloud ai endpoints direct-predict`

Run Vertex AI online direct prediction

gcloud ai endpoints direct-predict sends a direct prediction request to
Vertex AI endpoint for the given instances. The request limit is 10MB.

**Synopsis:**
```
gcloud ai endpoints direct-predict (ENDPOINT : --region=REGION)
    --json-request=JSON_REQUEST [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online direct prediction. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-request` | JSON_REQUEST |  | Path to a local file containing the body of a JSON request. An example of a JSON request: { "inputs": [ {"dtype": "STRING", shape: [1], "string_val": ["hello world"]}, {"dtype": "INT32", shape: [1], "int_val": [42]} ] } This flag accepts "-" for stdin. |


**Examples:**
```bash
To direct predict against an endpoint 123 under project example in region
us-central1, run:

    $ gcloud ai endpoints direct-predict 123 --project=example \
        --region=us-central1 --json-request=input.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/direct-predict)

---
### `gcloud ai endpoints direct-raw-predict`

Run Vertex AI online direct raw prediction

gcloud ai endpoints direct-raw-predict sends a direct raw prediction
request to Vertex AI endpoint for the given input. The request limit is
10MB.

**Synopsis:**
```
gcloud ai endpoints direct-raw-predict (ENDPOINT : --region=REGION)
    --json-request=JSON_REQUEST [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online direct raw prediction. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-request` | JSON_REQUEST |  | Path to a local file containing the body of a JSON request. An example of a JSON request: { "method_name": "my.method.Predict", "input": "my request bytes" } This flag accepts "-" for stdin. |


**Examples:**
```bash
To direct predict against an endpoint 123 under project example in region
us-central1, run:

    $ gcloud ai endpoints direct-raw-predict 123 --project=example \
        --region=us-central1 --json-request=input.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/direct-raw-predict)

---
### `gcloud ai endpoints explain`

Request an online explanation from an Vertex AI endpoint

gcloud ai endpoints explain sends an explanation request to the Vertex AI
endpoint for the given instances. This command reads up to 100 instances,
though the service itself accepts instances up to the payload limit size
(currently, 1.5MB).

**Synopsis:**
```
gcloud ai endpoints explain (ENDPOINT : --region=REGION)
    --json-request=JSON_REQUEST [--deployed-model-id=DEPLOYED_MODEL_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to request an online explanation. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-request` | JSON_REQUEST |  | Path to a local file containing the body of a JSON request. An example of a JSON request: { "instances": [ {"x": [1, 2], "y": [3, 4]}, {"x": [-1, -2], "y": [-3, -4]} ] } This flag accepts "-" for stdin. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployed-model-id` | DEPLOYED_MODEL_ID |  | Id of the deployed model. |


**Examples:**
```bash
To send an explanation request to the endpoint for the json file,
input.json, run:

    $ gcloud ai endpoints explain ENDPOINT_ID --region=us-central1 \
        --json-request=input.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/explain)

---
### `gcloud ai endpoints list`

List existing Vertex AI endpoints

**Synopsis:**
```
gcloud ai endpoints list [--list-model-garden-endpoints-only]
    [--region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--list-model-garden-endpoints-only` |  |  | Whether to only list endpoints related to Model Garden. |


**Examples:**
```bash
To list the endpoints under project example in region us-central1, run:

    $ gcloud ai endpoints list --project=example --region=us-central1

To list the endpoints under project example in region us-central1 that are
created from Model Garden, run:

    $ gcloud ai endpoints list --project=example --region=us-central1 \
        --list-model-garden-endpoints-only
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/list)

---
### `gcloud ai endpoints predict`

Run Vertex AI online prediction

gcloud ai endpoints predict sends a prediction request to Vertex AI
endpoint for the given instances. This command will read up to 100
instances, though the service itself will accept instances up to the
payload limit size (currently, 1.5MB).

**Synopsis:**
```
gcloud ai endpoints predict (ENDPOINT : --region=REGION)
    --json-request=JSON_REQUEST [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online prediction. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-request` | JSON_REQUEST |  | Path to a local file containing the body of a JSON request. An example of a JSON request: { "instances": [ {"x": [1, 2], "y": [3, 4]}, {"x": [-1, -2], "y": [-3, -4]} ] } This flag accepts "-" for stdin. |


**Examples:**
```bash
To predict against an endpoint 123 under project example in region
us-central1, run:

    $ gcloud ai endpoints predict 123 --project=example \
        --region=us-central1 --json-request=input.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/predict)

---
### `gcloud ai endpoints raw-predict`

Run Vertex AI online raw prediction

gcloud ai endpoints raw-predict sends a raw prediction request to a Vertex
AI endpoint. The request can be given on the command line or read from a
file or stdin.

**Synopsis:**
```
gcloud ai endpoints raw-predict (ENDPOINT : --region=REGION)
    --request=REQUEST [--http-headers=[HEADER=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online raw prediction. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request` | REQUEST |  | The request to send to the endpoint. If the request starts with the letter '@', the rest should be a file name to read the request from, or '@-' to read from stdin. If the request body actually starts with '@', it must be placed in a file. If required, the Content-Type header should also be set appropriately, particularly for binary data. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--http-headers` | [HEADER=VALUE,...] |  | List of header and value pairs to send as part of the request. For example, to set the Content-Type and X-Header: --http-headers=Content-Type="application/json",X-Header=Value |


**Examples:**
```bash
To predict against an endpoint 123 under project example in region
us-central1, reading the request from the command line, run:

    $ gcloud ai endpoints raw-predict 123 --project=example \
        --region=us-central1 --request='{
        "instances": [
          { "values": [1, 2, 3, 4], "key": 1 },
          { "values": [5, 6, 7, 8], "key": 2 }
        ]
      }'

If the request body was in the file input.json, run:

    $ gcloud ai endpoints raw-predict 123 --project=example \
        --region=us-central1 --request=@input.json

To send the image file image.jpeg and set the content type, run:

    $ gcloud ai endpoints raw-predict 123 --project=example \
        --region=us-central1 --http-headers=Content-Type=image/jpeg \
        --request=@image.jpeg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/raw-predict)

---
### `gcloud ai endpoints stream-direct-predict`

Run Vertex AI online stream direct prediction

gcloud ai endpoints stream-direct-predict sends a stream direct prediction
request to Vertex AI endpoint for the given inputs. The request limit is
10MB.

**Synopsis:**
```
gcloud ai endpoints stream-direct-predict (ENDPOINT : --region=REGION)
    --json-request=JSON_REQUEST [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online stream direct prediction.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-request` | JSON_REQUEST |  | Path to a local file containing the body of a JSON request. An example of a JSON request: { "inputs": [ {"dtype": "STRING", shape: [1], "string_val": ["hello world"]}, {"dtype": "INT32", shape: [1], "int_val": [42]} ] } This flag accepts "-" for stdin. |


**Examples:**
```bash
To stream direct predict against an endpoint 123 under project example in
region us-central1, run:

    $ gcloud ai endpoints stream-direct-predict 123 --project=example \
        --region=us-central1 --json-request=input.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/stream-direct-predict)

---
### `gcloud ai endpoints stream-direct-raw-predict`

Run Vertex AI online stream direct raw prediction

gcloud ai endpoints stream-direct-raw-predict sends a stream direct raw
prediction request to Vertex AI endpoint for the given input. The request
limit is 10MB.

**Synopsis:**
```
gcloud ai endpoints stream-direct-raw-predict (ENDPOINT : --region=REGION)
    --json-request=JSON_REQUEST [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online stream direct raw
prediction. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-request` | JSON_REQUEST |  | Path to a local file containing the body of a JSON request. An example of a JSON request: { "method_name": "my.method.Predict", "input": "my request bytes" } This flag accepts "-" for stdin. |


**Examples:**
```bash
To stream direct predict against an endpoint 123 under project example in
region us-central1, run:

    $ gcloud ai endpoints stream-direct-raw-predict 123 \
        --project=example --region=us-central1 --json-request=input.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/stream-direct-raw-predict)

---
### `gcloud ai endpoints stream-raw-predict`

Run Vertex AI online stream raw prediction

gcloud ai endpoints stream-raw-predict sends a stream raw prediction
request to a Vertex AI endpoint. The request can be given on the command
line or read from a file or stdin.

**Synopsis:**
```
gcloud ai endpoints stream-raw-predict (ENDPOINT : --region=REGION)
    --request=REQUEST [--http-headers=[HEADER=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to do online stream raw prediction. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--request` | REQUEST |  | The request to send to the endpoint. If the request starts with the letter '@', the rest should be a file name to read the request from, or '@-' to read from stdin. If the request body actually starts with '@', it must be placed in a file. If required, the Content-Type header should also be set appropriately, particularly for binary data. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--http-headers` | [HEADER=VALUE,...] |  | List of header and value pairs to send as part of the request. For example, to set the Content-Type and X-Header: --http-headers=Content-Type="application/json",X-Header=Value |


**Examples:**
```bash
To predict against an endpoint 123 under project example in region
us-central1, reading the request from the command line, run:

    $ gcloud ai endpoints stream-raw-predict 123 --project=example \
        --region=us-central1 --request='{
        "instances": [
          { "values": [1, 2, 3, 4], "key": 1 },
          { "values": [5, 6, 7, 8], "key": 2 }
        ]
      }'

If the request body was in the file input.json, run:

    $ gcloud ai endpoints stream-raw-predict 123 --project=example \
        --region=us-central1 --request=@input.json

To send the image file image.jpeg and set the content type, run:

    $ gcloud ai endpoints stream-raw-predict 123 --project=example \
        --region=us-central1 --http-headers=Content-Type=image/jpeg \
        --request=@image.jpeg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/stream-raw-predict)

---
### `gcloud ai endpoints undeploy-model`

Undeploy a model from an existing Vertex AI endpoint

**Synopsis:**
```
gcloud ai endpoints undeploy-model (ENDPOINT : --region=REGION)
    --deployed-model-id=DEPLOYED_MODEL_ID
    [--traffic-split=[DEPLOYED_MODEL_ID=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to undeploy a model from. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployed-model-id` | DEPLOYED_MODEL_ID |  | Id of the deployed model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--traffic-split` | [DEPLOYED_MODEL_ID=VALUE,...] |  | List of pairs of deployed model id and value to set as traffic split. |


**Examples:**
```bash
To undeploy a model 456 from an endpoint 123 under project example in
region us-central1, run:

    $ gcloud ai endpoints undeploy-model 123 --project=example \
        --region=us-central1 --deployed-model-id=456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/undeploy-model)

---
### `gcloud ai endpoints update`

Update an existing Vertex AI endpoint

**Synopsis:**
```
gcloud ai endpoints update (ENDPOINT : --region=REGION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-traffic-split | --traffic-split=[DEPLOYED_MODEL_ID=VALUE,...]]
    [--disable-request-response-logging
      | --request-response-logging-rate=REQUEST_RESPONSE_LOGGING_RATE
      --request-response-logging-table=REQUEST_RESPONSE_LOGGING_TABLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The endpoint to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the name attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the endpoint.

     To set the region attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the endpoint. |
| `--display-name` | DISPLAY_NAME |  | Display name of the endpoint. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update an endpoint 123 under project example in region us-central1, run:

    $ gcloud ai endpoints update 123 --project=example \
        --region=us-central1 --display-name=new_name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/endpoints/update)

---
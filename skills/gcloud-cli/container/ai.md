# gcloud container ai

manage AI related workloads for GKE


## `gcloud container ai profiles` — quickstart engine for GKE AI workloads
### `gcloud container ai profiles list`

List compatible accelerator profiles

This command lists all supported accelerators with their performance
details. By default, the supported accelerators are displayed in a table
format with select information for each accelerator. To see all details,
use --format=yaml or --format=csvprofile.

To get supported model, model servers, and model server versions, run
gcloud container ai profiles models list, gcloud container ai profiles
model-servers list, and gcloud container ai profiles model-server-versions
list.

**Synopsis:**
```
gcloud container ai profiles list [--format=FORMAT] [--model=MODEL]
    [--model-server=MODEL_SERVER]
    [--model-server-version=MODEL_SERVER_VERSION]
    [--pricing-model=PRICING_MODEL] [--serving-stack=SERVING_STACK]
    [--serving-stack-version=SERVING_STACK_VERSION]
    [--target-cost-per-million-input-tokens=TARGET_COST_PER_MILLION_INPUT_TOKENS]
    [--target-cost-per-million-output-tokens=TARGET_COST_PER_MILLION_OUTPUT_TOKENS]
    [--target-input-length=TARGET_INPUT_LENGTH]
    [--target-itl-milliseconds=TARGET_ITL_MILLISECONDS]
    [--target-ntpot-milliseconds=TARGET_NTPOT_MILLISECONDS]
    [--target-output-length=TARGET_OUTPUT_LENGTH]
    [--target-ttft-milliseconds=TARGET_TTFT_MILLISECONDS]
    [--use-case=USE_CASE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--format` | FORMAT |  | The output format. Default is profile, which displays the profile information in a table format, including cost conversions. csvprofile displays the profile information in a CSV format.Options include csvprofile, profile, and yaml. |
| `--model` | MODEL |  | The model. |
| `--model-server` | MODEL_SERVER |  | The model server version. Default is latest. Other options include the model server version of a profile, all which returns all versions. |
| `--model-server-version` | MODEL_SERVER_VERSION |  | The model server version. If not specified, this defaults to the latest version. |
| `--pricing-model` | PRICING_MODEL |  | The pricing model to use to calculate token cost. Currently, this supports on-demand, spot, 3-years-cud, 1-year-cud |
| `--serving-stack` | SERVING_STACK |  | The serving stack to filter profiles by. If not provided, profiles for all serving stacks that support the given model and model server will be returned. |
| `--serving-stack-version` | SERVING_STACK_VERSION |  | The serving stack version to filter profiles by. If not provided, profiles for all versions that support the given model and model server will be returned. |
| `--target-cost-per-million-input-tokens` | TARGET_COST_PER_MILLION_INPUT_TOKENS |  | The target cost per million input tokens to filter profiles by, unit is 1 USD up to 5 decimal places. |
| `--target-cost-per-million-output-tokens` | TARGET_COST_PER_MILLION_OUTPUT_TOKENS |  | The target cost per million output tokens to filter profiles by, unit is 1 USD up to 5 decimal places. |
| `--target-input-length` | TARGET_INPUT_LENGTH |  | If specified, results will only show profiles that have an input length within 20% of the specified one. Only works alongside output length. |
| `--target-itl-milliseconds` | TARGET_ITL_MILLISECONDS |  | If specified, results will only show profiles with instance types that can meet the latency target and will show their throughput performances at the target inter-token latency (ITL). |
| `--target-ntpot-milliseconds` | TARGET_NTPOT_MILLISECONDS |  | The target normalized time per output token (NTPOT) in milliseconds. NTPOT is measured as the request_latency / output_tokens. If this field is set, the command will only return accelerators that can meet the target ntpot milliseconds and display their throughput performance at the target latency. Otherwise, the command will return all accelerators and display their highest throughput performance. |
| `--target-output-length` | TARGET_OUTPUT_LENGTH |  | If specified, results will only show profiles that have an output length within 20% of the specified one. Only works alongside input length. |
| `--target-ttft-milliseconds` | TARGET_TTFT_MILLISECONDS |  | The target time to first token (TTFT) in milliseconds. TTFT is measured as the request_latency / output_tokens. If this field is set, the command will only return profiles that can meet the target ttft milliseconds and display their throughput performance at the target latency. Otherwise, the command will return all profiles and display their highest throughput performance. |
| `--use-case` | USE_CASE |  | If specified, results will only show profiles that match the provided use case. Options are: Advanced Customer Support, Code Completion, Text Summarization, Chatbot (ShareGPT), Text Generation, Deep Research |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/list)

---

## `gcloud container ai profiles benchmarks` — manage benchmarks for GKE Inference Quickstart
### `gcloud container ai profiles benchmarks list`

List benchmarks for a given model and model server

This command lists all benchmarking data for a given model and model
server. By default, the benchmarks are displayed in a CSV format.

For examples of visualizing the benchmarking data, see the accompanying
Colab notebook:
https://colab.research.google.com/github/GoogleCloudPlatform/kubernetes-engine-samples/blob/main/ai-ml/notebooks/giq_visualizations.ipynb

**Synopsis:**
```
gcloud container ai profiles benchmarks list --model=MODEL
    --model-server=MODEL_SERVER [--format=FORMAT]
    [--instance-type=INSTANCE_TYPE]
    [--model-server-version=MODEL_SERVER_VERSION]
    [--pricing-model=PRICING_MODEL] [--serving-stack=SERVING_STACK]
    [--serving-stack-version=SERVING_STACK_VERSION] [--use-case=USE_CASE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model. |
| `--model-server` | MODEL_SERVER |  | The model server. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--format` | FORMAT |  | The format to print the output in. Default is csvprofile, which displays the profile information in a CSV format, includingcost conversions. |
| `--instance-type` | INSTANCE_TYPE |  | The instance type. If not specified, this defaults to anyinstance type. |
| `--model-server-version` | MODEL_SERVER_VERSION |  | The model server version. Default is latest. Other options include the model server version of a profile, all which returns all versions. |
| `--pricing-model` | PRICING_MODEL |  | The pricing model to use to calculate token cost. Currently, this supports on-demand, spot, 3-years-cud, 1-year-cud |
| `--serving-stack` | SERVING_STACK |  | The serving stack to filter benchmarking data by. If not provided, benchmarking data for all serving stacks that support the given model and model server will be returned. |
| `--serving-stack-version` | SERVING_STACK_VERSION |  | The serving stack version to filter benchmarking data by. If not provided, benchmarking data for all versions that support the given model and model server will be returned. |
| `--use-case` | USE_CASE |  | If specified, results will only show profiles that match the provided use case. Options are: Advanced Customer Support, Code Completion, Text Summarization, Chatbot (ShareGPT), Code Generation, Deep Research. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/benchmarks/list)

---

## `gcloud container ai profiles manifests` — generate optimized Kubernetes manifests
### `gcloud container ai profiles manifests create`

Generate ready-to-deploy Kubernetes manifests with compute, load balancing, and autoscaling capabilities

To get supported model, model servers, and model server versions, run
gcloud alpha container ai profiles model-and-server-combinations list. To
get supported accelerators with their performance metrics, run gcloud alpha
container ai profiles accelerators list.

**Synopsis:**
```
gcloud container ai profiles manifests create
    --accelerator-type=ACCELERATOR_TYPE --model=MODEL
    --model-server=MODEL_SERVER [--model-bucket-uri=MODEL_BUCKET_URI]
    [--model-server-version=MODEL_SERVER_VERSION] [--namespace=NAMESPACE]
    [--output=OUTPUT; default="all"] [--output-path=OUTPUT_PATH]
    [--serving-stack=SERVING_STACK]
    [--serving-stack-version=SERVING_STACK_VERSION]
    [--target-itl-milliseconds=TARGET_ITL_MILLISECONDS]
    [--target-ntpot-milliseconds=TARGET_NTPOT_MILLISECONDS]
    [--target-ttft-milliseconds=TARGET_TTFT_MILLISECONDS]
    [--use-case=USE_CASE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator-type` | ACCELERATOR_TYPE |  | The accelerator type. |
| `--model` | MODEL |  | The model. |
| `--model-server` | MODEL_SERVER |  | The model server. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model-bucket-uri` | MODEL_BUCKET_URI |  | The Google Cloud Storage bucket URI to load the model from. This URI must point to the directory containing the model's config file (config.json) and model weights. If unspecified, defaults to loading the model from Hugging Face. |
| `--model-server-version` | MODEL_SERVER_VERSION |  | The model server version. If not specified, this defaults to the latest version. |
| `--namespace` | NAMESPACE |  | The namespace to deploy the manifests in. Default namespace is 'default'. |
| `--output` | one of: manifest, comments, all | all | The output to display. Default is all. OUTPUT must be one of: manifest, comments, all. |
| `--output-path` | OUTPUT_PATH |  | The path to save the output to. If not specified, output to the terminal. |
| `--serving-stack` | SERVING_STACK |  | The serving stack to filter manifests by. If not provided, manifests for all serving stacks that support the given model and model server will be considered. |
| `--serving-stack-version` | SERVING_STACK_VERSION |  | The serving stack version to filter manifests by. If not provided, manifests for all versions that support the given model and model server will be considered. |
| `--target-itl-milliseconds` | TARGET_ITL_MILLISECONDS |  | The target inter-token latency (ITL) in milliseconds. If this is set, the manifest will include Horizontal Pod Autoscaler (HPA) resources which automatically adjust the model server replica count in response to changes in model server load to keep p50 ITL below the specified threshold. If the provided target-itl-milliseconds is too low to achieve, the HPA manifest will not be generated. |
| `--target-ntpot-milliseconds` | TARGET_NTPOT_MILLISECONDS |  | The maximum normalized time per output token (NTPOT) in milliseconds. NTPOT is measured as the request_latency / output_tokens. If this is set, the manifests will include Horizontal Pod Autoscaler (HPA) resources which automatically adjust the model server replica count in response to changes in model server load to keep p50 NTPOT below the specified threshold. If the provided target-ntpot-milliseconds is too low to achieve, the HPA manifest will not be generated. |
| `--target-ttft-milliseconds` | TARGET_TTFT_MILLISECONDS |  | If specified, results will only show accelerators that can meet the latency target and will show their throughput performances at the target ttft target to achieve, the HPA manifest will not be generated. |
| `--use-case` | USE_CASE |  | The manifest will be optimized for this use case. Options are: Advanced Customer Support, Code Completion, Text Summarization, Chatbot (ShareGPT), Code Generation, Deep Research. Will default to Chatbot if not specified. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/manifests/create)

---

## `gcloud container ai profiles model-server-versions` — manage supported model server versions for GKE Inference Quickstart
### `gcloud container ai profiles model-server-versions list`

List supported model server versions

To get supported model and model servers, run gcloud container ai profiles
models list and gcloud container ai profiles model-servers list.

**Synopsis:**
```
gcloud container ai profiles model-server-versions list --model=MODEL
    --model-server=MODEL_SERVER [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model. |
| `--model-server` | MODEL_SERVER |  | The model server. If not specified, this defaults to any model server. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/model-server-versions/list)

---

## `gcloud container ai profiles model-servers` — manage supported model servers for GKE Inference Quickstart
### `gcloud container ai profiles model-servers list`

List supported model servers for a given model

To get supported models, run gcloud container ai profiles models list.

**Synopsis:**
```
gcloud container ai profiles model-servers list --model=MODEL
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/model-servers/list)

---

## `gcloud container ai profiles models` — manage supported models for GKE Inference Quickstart
### `gcloud container ai profiles models list`

List supported models

List supported models.

**Synopsis:**
```
gcloud container ai profiles models list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/models/list)

---

## `gcloud container ai profiles serving-stack-versions` — list supported serving stack versions for GKE Inference Quickstart
### `gcloud container ai profiles serving-stack-versions list`

List supported serving stack versions that were used to generate the inference profiles

List supported serving stack versions that were used to generate the
inference profiles.

**Synopsis:**
```
gcloud container ai profiles serving-stack-versions list
    --serving-stack=SERVING_STACK [--model=MODEL]
    [--model-server=MODEL_SERVER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--serving-stack` | SERVING_STACK |  | The serving stack to filter serving stack versions by. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model to filter serving stack versions by. |
| `--model-server` | MODEL_SERVER |  | The model server to filter serving stack versions by. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/serving-stack-versions/list)

---

## `gcloud container ai profiles serving-stacks` — list supported serving stacks for GKE Inference Quickstart
### `gcloud container ai profiles serving-stacks list`

List supported serving stacks that were used to generate the inference profiles

List supported serving stacks that were used to generate the inference
profiles.

**Synopsis:**
```
gcloud container ai profiles serving-stacks list [--model=MODEL]
    [--model-server=MODEL_SERVER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | The model to filter serving stacks by. |
| `--model-server` | MODEL_SERVER |  | The model server to filter serving stacks by. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/serving-stacks/list)

---

## `gcloud container ai profiles use-case` — list supported use cases for GKE Inference Quickstart
### `gcloud container ai profiles use-case list`

List supported use cases that were used to generate the inference profiles

List supported use cases that were used to generate the inference profiles.

**Synopsis:**
```
gcloud container ai profiles use-case list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/ai/profiles/use-case/list)

---
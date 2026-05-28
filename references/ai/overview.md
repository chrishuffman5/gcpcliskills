# gcloud ai — Vertex AI

## Overview

`gcloud ai` manages entities in **Vertex AI**, Google Cloud's unified platform for building, training, deploying, and serving ML and generative-AI models. Reach for it to run custom training and hyperparameter-tuning jobs, upload models and deploy them to endpoints for online prediction, deploy foundation models from Model Garden (including gated Hugging Face models), build and serve Vector Search indexes, and set up model-monitoring jobs, persistent training resources, and Tensorboards. All resources are regional, so nearly every command takes `--region` (or the `ai/region` property).

## Quick reference — common workflows

### Enable the API

```bash
gcloud services enable aiplatform.googleapis.com
```

### 1. Run a custom training job and watch it

```bash
# Create the job (it starts running immediately)
gcloud ai custom-jobs create \
  --region=us-central1 \
  --display-name=test \
  --worker-pool-spec=replica-count=1,machine-type=n1-highmem-2,container-image-uri=gcr.io/ucaip-test/ucaip-training-test \
  --project=example

# Stream logs from the running job (use the job ID from the create output)
gcloud ai custom-jobs stream-logs 123 --region=us-central1 --project=example

# Check status
gcloud ai custom-jobs describe 123 --region=us-central1 --project=example
```

### 2. Upload a model, deploy it to an endpoint, and predict

```bash
# Upload a custom-serving model
gcloud ai models upload \
  --display-name=my-model \
  --container-image-uri=gcr.io/example/my-image \
  --artifact-uri=gs://bucket/path \
  --region=us-central1 --project=example

# Create an endpoint
gcloud ai endpoints create --display-name=my_endpoint \
  --region=us-central1 --project=example

# Deploy the model (split 100% of traffic to it)
gcloud ai endpoints deploy-model 123 \
  --model=456 --display-name=my_deployed_model \
  --min-replica-count=1 --max-replica-count=3 \
  --traffic-split=0=100 \
  --region=us-central1 --project=example

# Send an online prediction request
gcloud ai endpoints predict 123 \
  --json-request=input.json \
  --region=us-central1 --project=example
```

### 3. Manage models and versions

```bash
# List / describe
gcloud ai models list --region=us-central1 --project=example
gcloud ai models describe 123 --region=us-central1 --project=example

# Versions: list, then delete a specific one (MODEL@VERSION)
gcloud ai models list-version 123 --region=us-central1 --project=example
gcloud ai models delete-version 123@1234 --region=us-central1 --project=example

# Undeploy from an endpoint before deleting the model
gcloud ai endpoints undeploy-model 123 \
  --deployed-model-id=456 --region=us-central1 --project=example
```

### 4. Create and deploy a Vector Search index

```bash
# Create a stream-update index from a metadata file
gcloud ai indexes create \
  --display-name=index \
  --metadata-file=path/to/metadata.json \
  --index-update-method=stream-update \
  --region=us-central1 --project=example

# Create a public index endpoint
gcloud ai index-endpoints create \
  --display-name=index-endpoint --public-endpoint-enabled \
  --region=us-central1 --project=example

# Deploy the index to the endpoint
gcloud ai index-endpoints deploy-index 456 \
  --index=345 --deployed-index-id=deployed-index-345 \
  --display-name=deployed-index-345 \
  --min-replica-count=2 --max-replica-count=10 \
  --region=us-central1 --project=example

# Stream-update: upsert datapoints from a local JSON file
gcloud ai indexes upsert-datapoints 123 \
  --datapoints-from-file=example.json \
  --region=us-central1 --project=example
```

### 5. Deploy a Model Garden (or Hugging Face) model

```bash
# Discover models, then check verified machine specs
gcloud ai model-garden models list --model-filter=gemma
gcloud ai model-garden models list-deployment-config \
  --model=google/gemma2@gemma-2-9b

# Deploy a Model Garden model (accept the EULA)
gcloud ai model-garden models deploy \
  --model=google/gemma2@gemma-2-9b --accept-eula \
  --region=us-central1 --project=example

# Deploy a gated Hugging Face model (token required)
gcloud ai model-garden models deploy \
  --model=meta-llama/Meta-Llama-3-8B \
  --hugging-face-access-token=HF_TOKEN \
  --region=us-central1 --project=example
```

### 6. Hyperparameter tuning job lifecycle

```bash
gcloud ai hp-tuning-jobs create \
  --display-name=test --config=config.yaml \
  --region=us-central1 --project=example

gcloud ai hp-tuning-jobs stream-logs 123 --region=us-central1 --project=example
gcloud ai hp-tuning-jobs describe 123 --region=us-central1 --project=example
gcloud ai hp-tuning-jobs cancel 123 --region=us-central1 --project=example
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `ai custom-jobs` | [`custom-jobs.md`](custom-jobs.md) | 6 | Manage Vertex AI custom (training) jobs |
| `ai endpoints` | [`endpoints.md`](endpoints.md) | 15 | Manage endpoints; deploy models; online/raw/stream prediction |
| `ai hp-tuning-jobs` | [`hp-tuning-jobs.md`](hp-tuning-jobs.md) | 5 | Manage hyperparameter tuning jobs |
| `ai index-endpoints` | [`index-endpoints.md`](index-endpoints.md) | 8 | Manage Vector Search index endpoints; deploy/undeploy indexes |
| `ai indexes` | [`indexes.md`](indexes.md) | 7 | Manage Vector Search indexes; upsert/remove datapoints |
| `ai model-garden` | [`model-garden.md`](model-garden.md) | 3 | List and deploy Model Garden / Hugging Face models |
| `ai model-monitoring-jobs` | [`model-monitoring-jobs.md`](model-monitoring-jobs.md) | 7 | Manage model deployment monitoring jobs (drift/skew) |
| `ai models` | [`models.md`](models.md) | 7 | Upload, copy, list, describe, and version models |
| `ai operations` | [`operations.md`](operations.md) | 1 | Describe long-running Vertex AI operations |
| `ai persistent-resources` | [`persistent-resources.md`](persistent-resources.md) | 5 | Create and manage persistent training resources |
| `ai tensorboards` | [`tensorboards.md`](tensorboards.md) | 5 | Manage Vertex AI Tensorboards |

See [`index.md`](index.md) for a one-line index of all 69 GA commands.

## Common flags & tips

- **Region is required almost everywhere.** Pass `--region=us-central1` per command, or set it once: `gcloud config set ai/region us-central1`. Most resources can instead be addressed by a fully qualified name (e.g. `projects/PROJECT/locations/REGION/models/123`), which sets project and region implicitly.
- **Resource IDs vs. versions.** Models support `MODEL@VERSION` syntax — e.g. `123@1234` for `delete-version`, `123@2` for `describe`. Plain `MODEL` targets the default version.
- **Listing.** `list` commands across groups support `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri`. Examples:
  - `gcloud ai models list --region=us-central1 --filter="displayName~prod" --sort-by=createTime`
  - `gcloud ai endpoints list --region=us-central1 --format="table(name, displayName)"`
  - `gcloud ai endpoints list --region=us-central1 --list-model-garden-endpoints-only`
- **Traffic splits** for `endpoints deploy-model` / `endpoints undeploy-model` use `--traffic-split=DEPLOYED_MODEL_ID=VALUE` pairs (e.g. `--traffic-split=0=100`).
- **Serving hardware.** `endpoints deploy-model` accepts `--machine-type`, `--accelerator=type=...,count=...`, `--min-replica-count`/`--max-replica-count`, and `--spot`. Setting `--min-replica-count=0` enrolls the deployment in scale-to-zero.
- **CMEK.** Many create commands accept customer-managed encryption keys — `--encryption-kms-key-name` (endpoints, indexes, index-endpoints) or the `--kms-key`/`--kms-keyring`/`--kms-location`/`--kms-project` group (custom-jobs, hp-tuning-jobs, tensorboards, persistent-resources).
- **Prediction inputs.** `predict`, `direct-predict`, `explain`, and the stream variants read a JSON body via `--json-request=FILE` (accepts `-` for stdin); `raw-predict` / `stream-raw-predict` use `--request=` (prefix `@` for a file, `@-` for stdin) plus optional `--http-headers`.
- **Local testing.** `gcloud ai custom-jobs local-run --executor-image-uri=... --script=task.py` packages and runs training code in a local Docker container before submitting a real job; add `--gpu` to use a local GPU.

## beta / alpha

Both `gcloud beta ai` and `gcloud alpha ai` mirror the GA surface and expose additional capabilities:

- **Tensorboard sub-resources** — `tensorboard-experiments`, `tensorboard-runs`, and `tensorboard-time-series` management is available only under `beta`/`alpha`.
- **Semantic governance** — `semantic-governance-policies` and `semantic-governance-policy-engine` subgroups appear under `beta`.
- Use `gcloud beta ai model-garden models list --can-deploy-hugging-face-models` for Hugging Face model discovery.

`alpha` shares the `beta` subgroup surface but is more experimental and may change without notice.

## Official documentation

- **Vertex AI documentation home** — https://cloud.google.com/vertex-ai/docs — product concepts, guides, and tutorials (the docs-home for this service).
- **gcloud ai CLI reference** — https://cloud.google.com/sdk/gcloud/reference/ai — every subgroup, command, and flag.
- **Set up Vertex AI (cloud environment)** — https://cloud.google.com/vertex-ai/docs/start/cloud-environment — enable the API and assign IAM roles.
- **Create a custom training job** — https://cloud.google.com/vertex-ai/docs/training/create-custom-job — how-to for `custom-jobs create`.
- **Custom training overview** — https://cloud.google.com/vertex-ai/docs/training/overview — concepts behind training jobs and worker pools.
- **Deploy a model & get online predictions** — https://cloud.google.com/vertex-ai/docs/predictions/deploy-model-api — how-to for `models upload` + `endpoints deploy-model` + `endpoints predict`.
- **Vector Search overview** — https://cloud.google.com/vertex-ai/docs/vector-search/overview — concepts for indexes and index endpoints.
- **Create & manage a Vector Search index** — https://cloud.google.com/vertex-ai/docs/vector-search/create-manage-index — how-to for `indexes` / `index-endpoints`.
- **Vertex AI IAM permissions** — https://cloud.google.com/vertex-ai/docs/general/iam-permissions — roles and permissions reference.

See [`sources.md`](sources.md) for the full citation list.

---
name: gcloud-ai-platform
description: >-
  AI Platform (legacy) via gcloud (`gcloud ai-platform`). Manage AI Platform jobs and models — jobs, local, models, operations, versions.
---

# gcloud ai-platform — AI Platform (legacy)

## Overview

`gcloud ai-platform` manages **AI Platform** (formerly Cloud ML Engine): a managed
service for training ML models and serving online/batch predictions for TensorFlow,
scikit-learn, XGBoost, and custom containers. **This is a legacy service that has
been largely superseded by Vertex AI (`gcloud ai`).** Google has consolidated
training and prediction into Vertex AI; existing AI Platform workloads continue to
run, but new projects should use Vertex AI. Reach for `gcloud ai-platform` only to
operate or migrate pre-existing AI Platform models, versions, and jobs — see the
[migration guide](https://cloud.google.com/vertex-ai/docs/start/migrating-to-vertex-ai).

The underlying API is `ml.googleapis.com`. Enable it once per project:

```bash
gcloud services enable ml.googleapis.com
```

## Quick reference — common workflows

### 1. Submit a custom training job and watch it

```bash
gcloud ai-platform jobs submit training my_training_job \
    --module-name trainer.task \
    --package-path ./trainer \
    --staging-bucket gs://my-bucket/staging \
    --region us-central1 \
    --runtime-version 2.11 \
    --python-version 3.7 \
    --scale-tier basic

# Stream logs while the job runs
gcloud ai-platform jobs stream-logs my_training_job

# Get a human-readable summary of the finished job
gcloud ai-platform jobs describe my_training_job --summarize
```

### 2. Submit a GPU training job (custom scale tier)

```bash
gcloud ai-platform jobs submit training my_gpu_job \
    --module-name trainer.task \
    --package-path ./trainer \
    --staging-bucket gs://my-bucket/staging \
    --region us-central1 \
    --runtime-version 2.11 \
    --python-version 3.7 \
    --scale-tier custom \
    --master-machine-type n1-standard-8 \
    --master-accelerator type=nvidia-tesla-v100,count=1
```

### 3. Deploy a model for online prediction

```bash
# Create the model resource
gcloud ai-platform models create my_model \
    --regions us-central1 \
    --enable-logging

# Create a version pointing to a SavedModel in Cloud Storage
gcloud ai-platform versions create v1 \
    --model my_model \
    --origin gs://my-bucket/model-dir \
    --runtime-version 2.11 \
    --python-version 3.7 \
    --framework tensorflow

# Promote it to the model's default version
gcloud ai-platform versions set-default v1 --model my_model

# Send an online prediction request
gcloud ai-platform predict \
    --model my_model \
    --version v1 \
    --json-instances instances.json \
    --region us-central1
```

### 4. Submit a batch prediction job

```bash
gcloud ai-platform jobs submit prediction my_batch_job \
    --model my_model \
    --version v1 \
    --data-format text \
    --input-paths gs://my-bucket/input/*.json \
    --output-path gs://my-bucket/output \
    --region us-central1 \
    --runtime-version 2.11

# Monitor it
gcloud ai-platform jobs describe my_batch_job
gcloud ai-platform jobs list --filter="state=RUNNING"
```

### 5. Test prediction and training locally (no cloud resources)

```bash
# Local online prediction against a SavedModel directory
gcloud ai-platform local predict \
    --model-dir ./model-dir \
    --json-instances instances.json \
    --framework tensorflow

# Local distributed training run
gcloud ai-platform local train \
    --module-name trainer.task \
    --package-path ./trainer \
    --distributed \
    --parameter-server-count 2 \
    --worker-count 4
```

### 6. Manage versions and job labels

```bash
# List and inspect versions of a model
gcloud ai-platform versions list --model my_model
gcloud ai-platform versions describe v1 --model my_model

# Update a version's description, then retire an old one
gcloud ai-platform versions update v1 --model my_model \
    --description "Production model v1"
gcloud ai-platform versions delete v1 --model my_model

# Label a job, then cancel it if needed
gcloud ai-platform jobs update my_training_job --update-labels env=prod,team=ml
gcloud ai-platform jobs cancel my_training_job
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `ai-platform jobs` | [`jobs.md`](jobs.md) | 7 | Submit, list, describe, update, cancel, and stream logs for training and batch-prediction jobs |
| `ai-platform local` | [`local.md`](local.md) | 2 | Run training and prediction locally for testing/debugging |
| `ai-platform models` | [`models.md`](models.md) | 9 | Create/list/describe/update/delete models and manage their IAM policy |
| `ai-platform operations` | [`operations.md`](operations.md) | 4 | Describe, list, wait on, and cancel long-running operations |
| `ai-platform versions` | [`versions.md`](versions.md) | 6 | Create, list, describe, update, delete, and set-default model versions |

Top-level command (see [`_commands.md`](_commands.md)):

- `gcloud ai-platform predict` — run an online prediction request (reads up to 100 instances; use batch prediction for more).

See [`index.md`](index.md) for a one-line index of all 29 GA commands.

## Common flags & tips

- **`--region`** — Models, versions, prediction, and operations accept a regional
  endpoint. For models/versions/predict, the choices are `global` plus
  `asia-east1`, `asia-northeast1`, `asia-southeast1`, `australia-southeast1`,
  `europe-west1/2/3/4`, `northamerica-northeast1`, `us-central1`, `us-east1`,
  `us-east4`, `us-west1`. For `operations` the same list applies but **without**
  `global` (omitting `--region` uses the global endpoint). Training jobs instead
  take a Compute Engine `--region` and respect `gcloud config set compute/region`.
- **`--runtime-version` / `--python-version`** — Required for most TensorFlow/
  scikit-learn/XGBoost work. They must be a compatible pair; the supported matrix
  lives at the [runtime-version list](https://cloud.google.com/ai-platform/prediction/docs/runtime-version-list).
- **`--scale-tier`** — Training tier; valid values are `basic`, `basic-gpu`,
  `basic-tpu`, `custom`, `premium-1`, `standard-1`. With `custom` you must set
  `--master-machine-type` (and may add `--worker-count` / `--parameter-server-count`
  and `--*-accelerator`).
- **`--framework`** — On `versions create` and `local predict`, one of
  `scikit-learn`, `tensorflow` (default), `xgboost`.
- **`--model` is required** on every `versions` subcommand and on `predict`.
- **Custom containers:** pass `--master-image-uri` (and optionally `--worker-image-uri`,
  `--parameter-server-image-uri`) to `jobs submit training` instead of
  `--runtime-version`.
- **Async vs. blocking:** `jobs submit training` defaults to async — add
  `--stream-logs` to follow it, or `--async` on `versions create` to return
  immediately. Use `operations wait OPERATION` to block on a long-running operation.
- **Filtering/formatting:** list commands support `--filter`, `--sort-by`, `--limit`,
  and `--uri`. Useful patterns:
  - `gcloud ai-platform jobs list --filter="state=RUNNING"`
  - `gcloud ai-platform models list --uri --filter='name ~ vision[0-9]+'` (pipe to
    `xargs gcloud ai-platform models delete` for bulk cleanup)

## beta / alpha

- **`gcloud beta ai-platform`** adds `explain` — run an explanation request (feature
  attributions via Explainable AI). All GA subgroups are also present in beta.
- **`gcloud alpha ai-platform`** adds both `explain` (as in beta) and `locations` —
  query AI Platform location/region capabilities (not available in GA or beta).

Use GA for all standard workflows; reach for `beta` only for `explain`, and `alpha`
only to query location capabilities via `locations`.

## Official documentation

- [AI Platform docs home](https://cloud.google.com/ai-platform/docs) — product
  landing page for legacy AI Platform (now redirects to Vertex AI, reflecting that
  it has been superseded).
- [Migrating to Vertex AI](https://cloud.google.com/vertex-ai/docs/start/migrating-to-vertex-ai)
  — official guide for moving AI Platform workloads to `gcloud ai`.
- [AI Platform Training overview](https://cloud.google.com/ai-platform/training/docs/overview)
  — concepts for submitting and configuring training jobs.
- [AI Platform Prediction overview](https://cloud.google.com/ai-platform/prediction/docs/overview)
  — concepts for online and batch prediction.
- [Deploying models](https://cloud.google.com/ai-platform/prediction/docs/deploying-models)
  — how to upload a SavedModel and create a serving version.
- [Managing models and jobs](https://cloud.google.com/ai-platform/prediction/docs/managing-models-jobs)
  — managing models/versions via gcloud and REST.
- [Runtime version list](https://cloud.google.com/ai-platform/prediction/docs/runtime-version-list)
  — supported runtime + Python compatibility matrix.
- [Regional endpoints](https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints)
  — the global and regional endpoints accepted by `--region`.
- [AI Platform IAM roles](https://cloud.google.com/iam/docs/roles-permissions/ml)
  — predefined `roles/ml.*` roles (admin, developer, viewer, jobOwner, modelOwner, …).
- [gcloud ai-platform CLI reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform)
  — full command/flag reference for all GA commands.

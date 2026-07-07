# gcloud ai-platform operations

manage AI Platform operations

### `gcloud ai-platform operations cancel`

Cancel an AI Platform operation

Cancel an AI Platform operation.

**Synopsis:**
```
gcloud ai-platform operations cancel OPERATION [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   Name of the operation.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. If unspecified, the command uses the global endpoint of the AI Platform Training and Prediction API. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/operations/cancel)

---
### `gcloud ai-platform operations describe`

Describe an AI Platform operation

Describe an AI Platform operation.

**Synopsis:**
```
gcloud ai-platform operations describe OPERATION [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   Name of the operation.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. If unspecified, the command uses the global endpoint of the AI Platform Training and Prediction API. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/operations/describe)

---
### `gcloud ai-platform operations list`

List existing AI Platform jobs

List existing AI Platform jobs.

**Synopsis:**
```
gcloud ai-platform operations list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. If unspecified, the command uses the global endpoint of the AI Platform Training and Prediction API. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/operations/list)

---
### `gcloud ai-platform operations wait`

Wait for an AI Platform operation to complete

Wait for an AI Platform operation to complete.

Given an operation ID, this command polls the operation and blocks until it
completes. At completion, the operation message is printed (which includes
the operation response).

**Synopsis:**
```
gcloud ai-platform operations wait OPERATION [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   Name of the operation.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. If unspecified, the command uses the global endpoint of the AI Platform Training and Prediction API. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/operations/wait)

---
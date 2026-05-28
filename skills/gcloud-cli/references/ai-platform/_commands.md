# gcloud ai-platform (top-level commands)

### `gcloud ai-platform predict`

Run AI Platform online prediction

gcloud ai-platform predict sends a prediction request to AI Platform for
the given instances. This command will read up to 100 instances, though the
service itself will accept instances up to the payload limit size
(currently, 1.5MB). If you are predicting on more instances, you should use
batch prediction via

    $ gcloud ai-platform jobs submit prediction.

**Synopsis:**
```
gcloud ai-platform predict --model=MODEL
    (--json-instances=JSON_INSTANCES | --json-request=JSON_REQUEST
      | --text-instances=TEXT_INSTANCES) [--region=REGION]
    [--signature-name=SIGNATURE_NAME] [--version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model` | MODEL |  | Name of the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1 |  | Google Cloud region of the regional endpoint to use for this command. For the global endpoint, the region needs to be specified as global. Learn more about regional endpoints and see a list of available regions: https://cloud.google.com/ai-platform/prediction/docs/regional-endpoints REGION must be one of: global, asia-east1, asia-northeast1, asia-southeast1, australia-southeast1, europe-west1, europe-west2, europe-west3, europe-west4, northamerica-northeast1, us-central1, us-east1, us-east4, us-west1. |
| `--signature-name` | SIGNATURE_NAME |  | Name of the signature defined in the SavedModel to use for this job. Defaults to DEFAULT_SERVING_SIGNATURE_DEF_KEY in https://www.tensorflow.org/api_docs/python/tf/compat/v1/saved_model/signature_constants, which is "serving_default". Only applies to TensorFlow models. |
| `--version` | VERSION |  | Model version to be used. If unspecified, the default version of the model will be used. To list model versions run $ gcloud ai-platform versions list |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/predict)

---
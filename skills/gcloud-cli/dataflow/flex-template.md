# gcloud dataflow flex-template

a group of subcommands for working with Dataflow flex template

### `gcloud dataflow flex-template build`

Builds a flex template file from the specified parameters

Builds a flex template file from the specified parameters.

**Synopsis:**
```
gcloud dataflow flex-template build TEMPLATE_FILE_GCS_PATH
    --sdk-language=SDK_LANGUAGE
    (--image=IMAGE | --env=[ENV,...]
      --flex-template-base-image=FLEX_TEMPLATE_BASE_IMAGE
      --image-gcr-path=IMAGE_GCR_PATH (--go-binary-path=GO_BINARY_PATH
      | --jar=[JAR,...] | --py-path=[PY_PATH,...])
      | [--yaml-pipeline-path=YAML_PIPELINE_PATH
      : --yaml-image=YAML_IMAGE])
    [--additional-experiments=[ADDITIONAL_EXPERIMENTS,...]]
    [--additional-user-labels=[ADDITIONAL_USER_LABELS,...]]
    [--cloud-build-service-account=CLOUD_BUILD_SERVICE_ACCOUNT]
    [--dataflow-kms-key=DATAFLOW_KMS_KEY] [--disable-public-ips]
    [--enable-streaming-engine] [--gcs-log-dir=GCS_LOG_DIR]
    [--image-repository-cert-path=IMAGE_REPOSITORY_CERT_PATH]
    [--image-repository-password-secret-id=IMAGE_REPOSITORY_PASSWORD_SECRET_ID]
    [--image-repository-username-secret-id=IMAGE_REPOSITORY_USERNAME_SECRET_ID]
    [--max-workers=MAX_WORKERS] [--metadata-file=PATH_TO_FILE]
    [--network=NETWORK] [--num-workers=NUM_WORKERS] [--print-only]
    [--service-account-email=SERVICE_ACCOUNT_EMAIL]
    [--staging-location=STAGING_LOCATION] [--subnetwork=SUBNETWORK]
    [--temp-location=TEMP_LOCATION]
    [--worker-machine-type=WORKER_MACHINE_TYPE]
    [--worker-region=WORKER_REGION | --worker-zone=WORKER_ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TEMPLATE_FILE_GCS_PATH
   The Google Cloud Storage location of the flex template file.Overrides
   if file already exists.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--sdk-language` | one of: JAVA, PYTHON, GO, YAML |  | SDK language of the flex template job. SDK_LANGUAGE must be one of: JAVA, PYTHON, GO, YAML. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-experiments` | [ADDITIONAL_EXPERIMENTS,...] |  | Default experiments to pass to the job. |
| `--additional-user-labels` | [ADDITIONAL_USER_LABELS,...] |  | Default user labels to pass to the job. Example: --additional-user-labels='{"key1":"value1"}' |
| `--cloud-build-service-account` | CLOUD_BUILD_SERVICE_ACCOUNT |  | Service account to run the Cloud Build in the format projects/{project}/serviceAccounts/{service_account}. Ensure that the account you are using to run 'gcloud dataflow flex-template build' has 'ServiceAccountUser' role on the specified Cloud Build service account you provide with the --cloud-build-service-account flag. The specified service account must have required permissions to build the image. If the specified service account is in a project that is different from the project where you are starting builds, see https://cloud.google.com/build/docs/securing-builds/configure-user-specified-service-accounts#cross-project_set_up to grant the necessary access. |
| `--dataflow-kms-key` | DATAFLOW_KMS_KEY |  | Default Cloud KMS key to protect the job resources. |
| `--disable-public-ips` |  |  | Cloud Dataflow workers must not use public IP addresses. Overrides the default dataflow/disable_public_ips property value for this command invocation. |
| `--enable-streaming-engine` |  |  | Enable Streaming Engine for the streaming job by default. Overrides the default dataflow/enable_streaming_engine property value for this command invocation. |
| `--gcs-log-dir` | GCS_LOG_DIR |  | Google Cloud Storage directory to save build logs.(Must be a URL beginning with 'gs://'.) |
| `--image-repository-cert-path` | IMAGE_REPOSITORY_CERT_PATH |  | The full URL to self-signed certificate of private registry in Cloud Storage. For example, gs://mybucket/mycerts/selfsigned.crt. The certificate provided in Cloud Storage must be DER-encoded and may be supplied in binary or printable (Base64) encoding. If the certificate is provided in Base64 encoding, it must be bounded at the beginning by -----BEGIN CERTIFICATE-----, and must be bounded at the end by -----END CERTIFICATE-----. If this parameter is provided, the docker daemon in the template launcher will be instructed to trust that certificate. |
| `--image-repository-password-secret-id` | IMAGE_REPOSITORY_PASSWORD_SECRET_ID |  | Secret Manager secret id for the password to authenticate to private registry. Should be in the format projects/{project}/secrets/{secret}/versions/{secret_version} or projects/{project}/secrets/{secret}. If the version is not provided latest version will be used. |
| `--image-repository-username-secret-id` | IMAGE_REPOSITORY_USERNAME_SECRET_ID |  | Secret Manager secret id for the username to authenticate to private registry. Should be in the format projects/{project}/secrets/{secret}/versions/{secret_version} or projects/{project}/secrets/{secret}. If the version is not provided latest version will be used. |
| `--max-workers` | MAX_WORKERS |  | Default maximum number of workers to run. |
| `--metadata-file` | PATH_TO_FILE |  | Local path to the metadata json file for the flex template. Use a full or relative path to a local file containing the value of metadata_file. |
| `--network` | NETWORK |  | Default Compute Engine network for launching instances to run your pipeline. |
| `--num-workers` | NUM_WORKERS |  | Initial number of workers to use by default. |
| `--print-only` |  |  | Prints the container spec to stdout. Does not save in Google Cloud Storage. Overrides the default dataflow/print_only property value for this command invocation. |
| `--service-account-email` | SERVICE_ACCOUNT_EMAIL |  | Default service account to run the workers as. |
| `--staging-location` | STAGING_LOCATION |  | Default Google Cloud Storage location to stage local files.(Must be a URL beginning with 'gs://'.) |
| `--subnetwork` | SUBNETWORK |  | Default Compute Engine subnetwork for launching instances to run your pipeline. |
| `--temp-location` | TEMP_LOCATION |  | Default Google Cloud Storage location to stage temporary files. If not set, defaults to the value for --staging-location.(Must be a URL beginning with 'gs://'.) |
| `--worker-machine-type` | WORKER_MACHINE_TYPE |  | Default type of machine to use for workers. Defaults to server-specified. |


**Examples:**
```bash
To build and store a flex template JSON file, run:

    $ gcloud dataflow flex-template build gs://template-file-gcs-path \
        --image=gcr://image-path \
        --metadata-file=/local/path/to/metadata.json --sdk-language=JAVA

If using prebuilt template image from private registry, run:

    $ gcloud dataflow flex-template build gs://template-file-gcs-path \
        --image=private.registry.com:3000/image-path \
        --image-repository-username-secret-id="projects/test-project/sec\
    rets/username-secret" \
        --image-repository-password-secret-id="projects/test-project/sec\
    rets/password-secret/versions/latest" \
        --metadata-file=metadata.json --sdk-language=JAVA

To build the template image and flex template JSON file, run:

    $ gcloud dataflow flex-template build gs://template-file-gcs-path \
        --image-gcr-path=gcr://path-to-store-image \
        --jar=path/to/pipeline.jar --jar=path/to/dependency.jar \
        --env=FLEX_TEMPLATE_JAVA_MAIN_CLASS=classpath \
        --flex-template-base-image=JAVA11 \
        --metadata-file=/local/path/to/metadata.json --sdk-language=JAVA
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/flex-template/build)

---
### `gcloud dataflow flex-template run`

Runs a job from the specified path

Runs a job from the specified flex template gcs path.

**Synopsis:**
```
gcloud dataflow flex-template run JOB_NAME
    --template-file-gcs-location=TEMPLATE_FILE_GCS_LOCATION
    [--additional-experiments=[ADDITIONAL_EXPERIMENTS,...]]
    [--additional-pipeline-options=[ADDITIONAL_PIPELINE_OPTIONS,...]]
    [--additional-user-labels=[ADDITIONAL_USER_LABELS,...]]
    [--dataflow-kms-key=DATAFLOW_KMS_KEY] [--disable-public-ips]
    [--enable-streaming-engine] [--flexrs-goal=FLEXRS_GOAL]
    [--launcher-machine-type=LAUNCHER_MACHINE_TYPE]
    [--max-workers=MAX_WORKERS] [--network=NETWORK]
    [--num-workers=NUM_WORKERS] [--parameters=[PARAMETERS,...]]
    [--region=REGION_ID] [--service-account-email=SERVICE_ACCOUNT_EMAIL]
    [--staging-location=STAGING_LOCATION] [--subnetwork=SUBNETWORK]
    [--temp-location=TEMP_LOCATION]
    [--worker-machine-type=WORKER_MACHINE_TYPE]
    [[--[no-]update
      : --transform-name-mappings=[TRANSFORM_NAME_MAPPINGS,...]]]
    [--worker-region=WORKER_REGION | --worker-zone=WORKER_ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB_NAME
   Unique name to assign to the job.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--template-file-gcs-location` | TEMPLATE_FILE_GCS_LOCATION |  | Google Cloud Storage location of the flex template to run. (Must be a URL beginning with 'gs://'.) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-experiments` | [ADDITIONAL_EXPERIMENTS,...] |  | Additional experiments to pass to the job. Example: --additional-experiments=experiment1,experiment2=value2 |
| `--additional-pipeline-options` | [ADDITIONAL_PIPELINE_OPTIONS,...] |  | Additional pipeline options to pass to the job. Example: --additional-pipeline-options=option1=value1,option2=value2 |
| `--additional-user-labels` | [ADDITIONAL_USER_LABELS,...] |  | Additional user labels to pass to the job. Example: --additional-user-labels='key1=value1,key2=value2' |
| `--dataflow-kms-key` | DATAFLOW_KMS_KEY |  | Cloud KMS key to protect the job resources. |
| `--disable-public-ips` |  |  | Cloud Dataflow workers must not use public IP addresses. Overrides the default dataflow/disable_public_ips property value for this command invocation. |
| `--enable-streaming-engine` |  |  | Enabling Streaming Engine for the streaming job. Overrides the default dataflow/enable_streaming_engine property value for this command invocation. |
| `--flexrs-goal` | one of: COST_OPTIMIZED, SPEED_OPTIMIZED |  | FlexRS goal for the flex template job. FLEXRS_GOAL must be one of: COST_OPTIMIZED, SPEED_OPTIMIZED. |
| `--launcher-machine-type` | LAUNCHER_MACHINE_TYPE |  | The machine type to use for launching the job. The default isn1-standard-1. |
| `--max-workers` | MAX_WORKERS |  | Maximum number of workers to run. |
| `--network` | NETWORK |  | Compute Engine network for launching instances to run your pipeline. |
| `--num-workers` | NUM_WORKERS |  | Initial number of workers to use. |
| `--parameters` | [PARAMETERS,...] |  | Parameters to pass to the job. |
| `--region` | REGION_ID |  | Region ID of the job's regional endpoint. Defaults to 'us-central1'. |
| `--service-account-email` | SERVICE_ACCOUNT_EMAIL |  | Service account to run the workers as. |
| `--staging-location` | STAGING_LOCATION |  | Default Google Cloud Storage location to stage local files.(Must be a URL beginning with 'gs://'.) |
| `--subnetwork` | SUBNETWORK |  | Compute Engine subnetwork for launching instances to run your pipeline. |
| `--temp-location` | TEMP_LOCATION |  | Default Google Cloud Storage location to stage temporary files. If not set, defaults to the value for --staging-location.(Must be a URL beginning with 'gs://'.) |
| `--worker-machine-type` | WORKER_MACHINE_TYPE |  | Type of machine to use for workers. Defaults to server-specified. |
| `--[no-]update` |  |  | Set this to true for streaming update jobs. Use --update to enable and --no-update to disable. |
| `--transform-name-mappings` | [TRANSFORM_NAME_MAPPINGS,...] |  | Transform name mappings for the streaming update job. |


**Examples:**
```bash
To run a job from the flex template, run:

    $ gcloud dataflow flex-template run my-job \
        --template-file-gcs-location=gs://flex-template-path \
        --region=europe-west1 \
        --parameters=input="gs://input",output="gs://output-path" \
        --max-workers=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataflow/flex-template/run)

---
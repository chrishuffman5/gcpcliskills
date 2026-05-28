# gcloud dataproc batches

submit Dataproc batch jobs

### `gcloud dataproc batches cancel`

Cancel a batch job without removing batch resources

Cancel a batch job without removing batch resources.

**Synopsis:**
```
gcloud dataproc batches cancel (BATCH : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch resource - ID of the batch job to cancel. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument batch on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BATCH
     ID of the batch or fully qualified identifier for the batch.

     To set the batch attribute:
     + provide the argument batch on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the batch. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument batch on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To cancel a batch job "my-batch-job" in the "us-central1" region, run:

    $ gcloud dataproc batches cancel my-batch-job --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/cancel)

---
### `gcloud dataproc batches delete`

Delete a batch job

Delete a batch job.

**Synopsis:**
```
gcloud dataproc batches delete (BATCH : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch resource - ID of the batch job to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument batch on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BATCH
     ID of the batch or fully qualified identifier for the batch.

     To set the batch attribute:
     + provide the argument batch on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the batch. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument batch on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a batch job, run:

    $ gcloud dataproc batches delete my-batch-job --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/delete)

---
### `gcloud dataproc batches describe`

Describe a batch job

Describe a batch job.

**Synopsis:**
```
gcloud dataproc batches describe (BATCH : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch resource - ID of the batch job to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument batch on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BATCH
     ID of the batch or fully qualified identifier for the batch.

     To set the batch attribute:
     + provide the argument batch on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the batch. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument batch on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To describe a batch job, run:

    $ gcloud dataproc batches describe EXAMPLE-JOB --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/describe)

---
### `gcloud dataproc batches list`

List batch jobs in a project

List batch jobs in a project. Page-size sets the maximum number of jobs
returned per page, and Page-token retrieves subsequent results.

**Synopsis:**
```
gcloud dataproc batches list [--region=REGION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
List batch jobs in the "us-central1" region:

    $ gcloud dataproc batches list --region="us-central1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/list)

---
### `gcloud dataproc batches wait`

View the output of a batch as it runs or after it completes

View the output of a batch as it runs or after it completes.

**Synopsis:**
```
gcloud dataproc batches wait (BATCH : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Batch resource - ID of the batch job to wait. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument batch on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BATCH
     ID of the batch or fully qualified identifier for the batch.

     To set the batch attribute:
     + provide the argument batch on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the batch. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument batch on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To see a list of all batches, run:

    $ gcloud dataproc batches list

To view the output of "my-batch-job" in "us-central1" as it runs, run:

    $ gcloud dataproc batches wait my-batch-job --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/wait)

---

## `gcloud dataproc batches submit` — submit a Dataproc batch job
### `gcloud dataproc batches submit pyspark`

Submit a PySpark batch job

Submit a PySpark batch job.

**Synopsis:**
```
gcloud dataproc batches submit pyspark MAIN_PYTHON_FILE
    [--archives=[ARCHIVE,...]] [--async] [--batch=BATCH]
    [--container-image=CONTAINER_IMAGE] [--deps-bucket=DEPS_BUCKET]
    [--files=[FILE,...]] [--history-server-cluster=HISTORY_SERVER_CLUSTER]
    [--jars=[JAR,...]] [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]]
    [--metastore-service=METASTORE_SERVICE]
    [--properties=[PROPERTY=VALUE,...]] [--py-files=[PY,...]]
    [--region=REGION] [--request-id=REQUEST_ID]
    [--service-account=SERVICE_ACCOUNT] [--staging-bucket=STAGING_BUCKET]
    [--tags=[TAGS,...]] [--ttl=TTL]
    [--user-workload-authentication-type=USER_WORKLOAD_AUTHENTICATION_TYPE]
    [--version=VERSION] [--network=NETWORK | --subnet=SUBNET]
    [GCLOUD_WIDE_FLAG ...] [-- JOB_ARG ...]
```

**Positional arguments:**
```
MAIN_PYTHON_FILE
   URI of the main Python file to use as the Spark driver. Must be a .py
   file.

[-- JOB_ARG ...]
   Arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARG on the right.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Archives to be extracted into the working directory. Supported file types: .jar, .tar, .tar.gz, .tgz, and .zip. |
| `--async` |  |  | Return immediately without waiting for the operation in progress to complete. |
| `--batch` | BATCH |  | The ID of the batch job to submit. The ID must contain only lowercase letters (a-z), numbers (0-9) and hyphens (-). The length of the name must be between 4 and 63 characters. If this argument is not provided, a random generated UUID will be used. |
| `--container-image` | CONTAINER_IMAGE |  | Optional custom container image to use for the batch/session runtime environment. If not specified, a default container image will be used. The value should follow the container image naming format: {registry}/{repository}/{name}:{tag}, for example, gcr.io/my-project/my-image:1.2.3 |
| `--deps-bucket` | DEPS_BUCKET |  | A Cloud Storage bucket to upload workload dependencies. |
| `--files` | [FILE,...] |  | Files to be placed in the working directory. |
| `--history-server-cluster` | HISTORY_SERVER_CLUSTER |  | Spark History Server configuration for the batch/session job. Resource name of an existing Dataproc cluster to act as a Spark History Server for the workload in the format: "projects/{project_id}/regions/{region}/clusters/{cluster_name}". |
| `--jars` | [JAR,...] |  | Comma-separated list of jar files to be provided to the classpaths. |
| `--kms-key` | KMS_KEY |  | Cloud KMS key to use for encryption. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--metastore-service` | METASTORE_SERVICE |  | Name of a Dataproc Metastore service to be used as an external metastore in the format: "projects/{project-id}/locations/{region}/services/{service-name}". |
| `--properties` | [PROPERTY=VALUE,...] |  | Specifies configuration properties for the workload. See Dataproc Serverless for Spark documentation (https://cloud.google.com/dataproc-serverless/docs/concepts/properties) for the list of supported properties. |
| `--py-files` | [PY,...] |  | Comma-separated list of Python scripts to be passed to the PySpark framework. Supported file types: .py, .egg and .zip. |
| `--request-id` | REQUEST_ID |  | _[+ set the property dataproc/region.]_ A unique ID that identifies the request. If the service receives two batch create requests with the same request_id, the second request is ignored and the operation that corresponds to the first batch created and stored in the backend is returned. Recommendation: Always set this value to a UUID. The value must contain only letters (a-z, A-Z), numbers (0-9), underscores (), and hyphens (-). The maximum length is 40 characters. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ set the property dataproc/region.]_ The IAM service account to be used for a batch/session job. |
| `--staging-bucket` | STAGING_BUCKET |  | _[+ set the property dataproc/region.]_ The Cloud Storage bucket to use to store job dependencies, config files, and job driver console output. If not specified, the default [staging bucket] (https://cloud.google.com/dataproc-serverless/docs/concepts/buckets) is used. |
| `--tags` | [TAGS,...] |  | _[+ set the property dataproc/region.]_ Network tags for traffic control. |
| `--ttl` | TTL |  | _[+ set the property dataproc/region.]_ The duration after the workload will be unconditionally terminated, for example, '20m' or '1h'. Run gcloud topic datetimes (https://cloud.google.com/sdk/gcloud/reference/topic/datetimes) for information on duration formats. |
| `--user-workload-authentication-type` | USER_WORKLOAD_AUTHENTICATION_TYPE |  | _[+ set the property dataproc/region.]_ Whether to use END_USER_CREDENTIALS or SERVICE_ACCOUNT to run the workload. |
| `--version` | VERSION |  | _[+ set the property dataproc/region.]_ Optional runtime version. If not specified, a default version will be used. |


**Examples:**
```bash
To submit a PySpark batch job called "my-batch" that runs "my-pyspark.py",
run:

    $ gcloud dataproc batches submit pyspark my-pyspark.py \
        --batch=my-batch --deps-bucket=gs://my-bucket \
        --region=us-central1 --py-files='path/to/my/python/script.py'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/submit/pyspark)

---
### `gcloud dataproc batches submit spark`

Submit a Spark batch job

Submit a Spark batch job.

**Synopsis:**
```
gcloud dataproc batches submit spark (--class=MAIN_CLASS | --jar=MAIN_JAR)
    [--archives=[ARCHIVE,...]] [--async] [--batch=BATCH]
    [--container-image=CONTAINER_IMAGE] [--deps-bucket=DEPS_BUCKET]
    [--files=[FILE,...]] [--history-server-cluster=HISTORY_SERVER_CLUSTER]
    [--jars=[JAR,...]] [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]]
    [--metastore-service=METASTORE_SERVICE]
    [--properties=[PROPERTY=VALUE,...]] [--region=REGION]
    [--request-id=REQUEST_ID] [--service-account=SERVICE_ACCOUNT]
    [--staging-bucket=STAGING_BUCKET] [--tags=[TAGS,...]] [--ttl=TTL]
    [--user-workload-authentication-type=USER_WORKLOAD_AUTHENTICATION_TYPE]
    [--version=VERSION] [--network=NETWORK | --subnet=SUBNET]
    [GCLOUD_WIDE_FLAG ...] [-- JOB_ARG ...]
```

**Positional arguments:**
```
[-- JOB_ARG ...]
   Arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARG on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--class` | MAIN_CLASS |  | _[Exactly one of these must be specified:]_ Class contains the main method of the job. The jar file that contains the class must be in the classpath or specified in jar_files. |
| `--jar` | MAIN_JAR |  | _[Exactly one of these must be specified:]_ URI of the main jar file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Archives to be extracted into the working directory. Supported file types: .jar, .tar, .tar.gz, .tgz, and .zip. |
| `--async` |  |  | Return immediately without waiting for the operation in progress to complete. |
| `--batch` | BATCH |  | The ID of the batch job to submit. The ID must contain only lowercase letters (a-z), numbers (0-9) and hyphens (-). The length of the name must be between 4 and 63 characters. If this argument is not provided, a random generated UUID will be used. |
| `--container-image` | CONTAINER_IMAGE |  | Optional custom container image to use for the batch/session runtime environment. If not specified, a default container image will be used. The value should follow the container image naming format: {registry}/{repository}/{name}:{tag}, for example, gcr.io/my-project/my-image:1.2.3 |
| `--deps-bucket` | DEPS_BUCKET |  | A Cloud Storage bucket to upload workload dependencies. |
| `--files` | [FILE,...] |  | Files to be placed in the working directory. |
| `--history-server-cluster` | HISTORY_SERVER_CLUSTER |  | Spark History Server configuration for the batch/session job. Resource name of an existing Dataproc cluster to act as a Spark History Server for the workload in the format: "projects/{project_id}/regions/{region}/clusters/{cluster_name}". |
| `--jars` | [JAR,...] |  | Comma-separated list of jar files to be provided to the classpaths. |
| `--kms-key` | KMS_KEY |  | Cloud KMS key to use for encryption. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--metastore-service` | METASTORE_SERVICE |  | Name of a Dataproc Metastore service to be used as an external metastore in the format: "projects/{project-id}/locations/{region}/services/{service-name}". |
| `--properties` | [PROPERTY=VALUE,...] |  | Specifies configuration properties for the workload. See Dataproc Serverless for Spark documentation (https://cloud.google.com/dataproc-serverless/docs/concepts/properties) for the list of supported properties. |
| `--request-id` | REQUEST_ID |  | _[+ set the property dataproc/region.]_ A unique ID that identifies the request. If the service receives two batch create requests with the same request_id, the second request is ignored and the operation that corresponds to the first batch created and stored in the backend is returned. Recommendation: Always set this value to a UUID. The value must contain only letters (a-z, A-Z), numbers (0-9), underscores (), and hyphens (-). The maximum length is 40 characters. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ set the property dataproc/region.]_ The IAM service account to be used for a batch/session job. |
| `--staging-bucket` | STAGING_BUCKET |  | _[+ set the property dataproc/region.]_ The Cloud Storage bucket to use to store job dependencies, config files, and job driver console output. If not specified, the default [staging bucket] (https://cloud.google.com/dataproc-serverless/docs/concepts/buckets) is used. |
| `--tags` | [TAGS,...] |  | _[+ set the property dataproc/region.]_ Network tags for traffic control. |
| `--ttl` | TTL |  | _[+ set the property dataproc/region.]_ The duration after the workload will be unconditionally terminated, for example, '20m' or '1h'. Run gcloud topic datetimes (https://cloud.google.com/sdk/gcloud/reference/topic/datetimes) for information on duration formats. |
| `--user-workload-authentication-type` | USER_WORKLOAD_AUTHENTICATION_TYPE |  | _[+ set the property dataproc/region.]_ Whether to use END_USER_CREDENTIALS or SERVICE_ACCOUNT to run the workload. |
| `--version` | VERSION |  | _[+ set the property dataproc/region.]_ Optional runtime version. If not specified, a default version will be used. |


**Examples:**
```bash
To submit a Spark job, run:

    $ gcloud dataproc batches submit spark --region=us-central1 \
        --jar=my_jar.jar --deps-bucket=gs://my-bucket -- ARG1 ARG2

To submit a Spark job that runs a specific class of a jar, run:

    $ gcloud dataproc batches submit spark --region=us-central1 \
        --class=org.my.main.Class --jars=my_jar1.jar,my_jar2.jar \
        --deps-bucket=gs://my-bucket -- ARG1 ARG2

To submit a Spark job that runs a jar installed on the cluster, run:

    $ gcloud dataproc batches submit spark --region=us-central1 \
        --class=org.apache.spark.examples.SparkPi \
        --deps-bucket=gs://my-bucket \
        --jars=file:///usr/lib/spark/examples/jars/spark-examples.jar \
        -- 15
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/submit/spark)

---
### `gcloud dataproc batches submit spark-r`

Submit a Spark R batch job

Submit a Spark R batch job.

**Synopsis:**
```
gcloud dataproc batches submit spark-r MAIN_R_FILE
    [--archives=[ARCHIVE,...]] [--async] [--batch=BATCH]
    [--container-image=CONTAINER_IMAGE] [--deps-bucket=DEPS_BUCKET]
    [--files=[FILE,...]] [--history-server-cluster=HISTORY_SERVER_CLUSTER]
    [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]]
    [--metastore-service=METASTORE_SERVICE]
    [--properties=[PROPERTY=VALUE,...]] [--region=REGION]
    [--request-id=REQUEST_ID] [--service-account=SERVICE_ACCOUNT]
    [--staging-bucket=STAGING_BUCKET] [--tags=[TAGS,...]] [--ttl=TTL]
    [--user-workload-authentication-type=USER_WORKLOAD_AUTHENTICATION_TYPE]
    [--version=VERSION] [--network=NETWORK | --subnet=SUBNET]
    [GCLOUD_WIDE_FLAG ...] [-- JOB_ARG ...]
```

**Positional arguments:**
```
MAIN_R_FILE
   URI of the main R file to use as the driver. Must be a ``.R'' or ``.r''
   file.

[-- JOB_ARG ...]
   Arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARG on the right.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Archives to be extracted into the working directory. Supported file types: .jar, .tar, .tar.gz, .tgz, and .zip. |
| `--async` |  |  | Return immediately without waiting for the operation in progress to complete. |
| `--batch` | BATCH |  | The ID of the batch job to submit. The ID must contain only lowercase letters (a-z), numbers (0-9) and hyphens (-). The length of the name must be between 4 and 63 characters. If this argument is not provided, a random generated UUID will be used. |
| `--container-image` | CONTAINER_IMAGE |  | Optional custom container image to use for the batch/session runtime environment. If not specified, a default container image will be used. The value should follow the container image naming format: {registry}/{repository}/{name}:{tag}, for example, gcr.io/my-project/my-image:1.2.3 |
| `--deps-bucket` | DEPS_BUCKET |  | A Cloud Storage bucket to upload workload dependencies. |
| `--files` | [FILE,...] |  | Files to be placed in the working directory. |
| `--history-server-cluster` | HISTORY_SERVER_CLUSTER |  | Spark History Server configuration for the batch/session job. Resource name of an existing Dataproc cluster to act as a Spark History Server for the workload in the format: "projects/{project_id}/regions/{region}/clusters/{cluster_name}". |
| `--kms-key` | KMS_KEY |  | Cloud KMS key to use for encryption. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--metastore-service` | METASTORE_SERVICE |  | Name of a Dataproc Metastore service to be used as an external metastore in the format: "projects/{project-id}/locations/{region}/services/{service-name}". |
| `--properties` | [PROPERTY=VALUE,...] |  | Specifies configuration properties for the workload. See Dataproc Serverless for Spark documentation (https://cloud.google.com/dataproc-serverless/docs/concepts/properties) for the list of supported properties. |
| `--request-id` | REQUEST_ID |  | _[+ set the property dataproc/region.]_ A unique ID that identifies the request. If the service receives two batch create requests with the same request_id, the second request is ignored and the operation that corresponds to the first batch created and stored in the backend is returned. Recommendation: Always set this value to a UUID. The value must contain only letters (a-z, A-Z), numbers (0-9), underscores (), and hyphens (-). The maximum length is 40 characters. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ set the property dataproc/region.]_ The IAM service account to be used for a batch/session job. |
| `--staging-bucket` | STAGING_BUCKET |  | _[+ set the property dataproc/region.]_ The Cloud Storage bucket to use to store job dependencies, config files, and job driver console output. If not specified, the default [staging bucket] (https://cloud.google.com/dataproc-serverless/docs/concepts/buckets) is used. |
| `--tags` | [TAGS,...] |  | _[+ set the property dataproc/region.]_ Network tags for traffic control. |
| `--ttl` | TTL |  | _[+ set the property dataproc/region.]_ The duration after the workload will be unconditionally terminated, for example, '20m' or '1h'. Run gcloud topic datetimes (https://cloud.google.com/sdk/gcloud/reference/topic/datetimes) for information on duration formats. |
| `--user-workload-authentication-type` | USER_WORKLOAD_AUTHENTICATION_TYPE |  | _[+ set the property dataproc/region.]_ Whether to use END_USER_CREDENTIALS or SERVICE_ACCOUNT to run the workload. |
| `--version` | VERSION |  | _[+ set the property dataproc/region.]_ Optional runtime version. If not specified, a default version will be used. |


**Examples:**
```bash
To submit a Spark R batch job running "my-main-r.r" script and upload it to
"gs://my-bucket", run:

    $ gcloud dataproc batches submit spark-r my-main-r.r \
        --deps-bucket=gs://my-bucket --region='us-central1' -- ARG1 ARG2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/submit/spark-r)

---
### `gcloud dataproc batches submit spark-sql`

Submit a Spark SQL batch job

Submit a Spark SQL batch job.

**Synopsis:**
```
gcloud dataproc batches submit spark-sql SQL_SCRIPT [--async]
    [--batch=BATCH] [--container-image=CONTAINER_IMAGE]
    [--deps-bucket=DEPS_BUCKET]
    [--history-server-cluster=HISTORY_SERVER_CLUSTER] [--jars=[JAR,...]]
    [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]]
    [--metastore-service=METASTORE_SERVICE]
    [--properties=[PROPERTY=VALUE,...]] [--region=REGION]
    [--request-id=REQUEST_ID] [--service-account=SERVICE_ACCOUNT]
    [--staging-bucket=STAGING_BUCKET] [--tags=[TAGS,...]] [--ttl=TTL]
    [--user-workload-authentication-type=USER_WORKLOAD_AUTHENTICATION_TYPE]
    [--vars=[NAME=VALUE,...]] [--version=VERSION]
    [--network=NETWORK | --subnet=SUBNET] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SQL_SCRIPT
   URI of the script that contains Spark SQL queries to execute.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately without waiting for the operation in progress to complete. |
| `--batch` | BATCH |  | The ID of the batch job to submit. The ID must contain only lowercase letters (a-z), numbers (0-9) and hyphens (-). The length of the name must be between 4 and 63 characters. If this argument is not provided, a random generated UUID will be used. |
| `--container-image` | CONTAINER_IMAGE |  | Optional custom container image to use for the batch/session runtime environment. If not specified, a default container image will be used. The value should follow the container image naming format: {registry}/{repository}/{name}:{tag}, for example, gcr.io/my-project/my-image:1.2.3 |
| `--deps-bucket` | DEPS_BUCKET |  | A Cloud Storage bucket to upload workload dependencies. |
| `--history-server-cluster` | HISTORY_SERVER_CLUSTER |  | Spark History Server configuration for the batch/session job. Resource name of an existing Dataproc cluster to act as a Spark History Server for the workload in the format: "projects/{project_id}/regions/{region}/clusters/{cluster_name}". |
| `--jars` | [JAR,...] |  | Comma-separated list of jar files to be provided to the classpaths. |
| `--kms-key` | KMS_KEY |  | Cloud KMS key to use for encryption. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--metastore-service` | METASTORE_SERVICE |  | Name of a Dataproc Metastore service to be used as an external metastore in the format: "projects/{project-id}/locations/{region}/services/{service-name}". |
| `--properties` | [PROPERTY=VALUE,...] |  | Specifies configuration properties for the workload. See Dataproc Serverless for Spark documentation (https://cloud.google.com/dataproc-serverless/docs/concepts/properties) for the list of supported properties. |
| `--request-id` | REQUEST_ID |  | _[+ set the property dataproc/region.]_ A unique ID that identifies the request. If the service receives two batch create requests with the same request_id, the second request is ignored and the operation that corresponds to the first batch created and stored in the backend is returned. Recommendation: Always set this value to a UUID. The value must contain only letters (a-z, A-Z), numbers (0-9), underscores (), and hyphens (-). The maximum length is 40 characters. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ set the property dataproc/region.]_ The IAM service account to be used for a batch/session job. |
| `--staging-bucket` | STAGING_BUCKET |  | _[+ set the property dataproc/region.]_ The Cloud Storage bucket to use to store job dependencies, config files, and job driver console output. If not specified, the default [staging bucket] (https://cloud.google.com/dataproc-serverless/docs/concepts/buckets) is used. |
| `--tags` | [TAGS,...] |  | _[+ set the property dataproc/region.]_ Network tags for traffic control. |
| `--ttl` | TTL |  | _[+ set the property dataproc/region.]_ The duration after the workload will be unconditionally terminated, for example, '20m' or '1h'. Run gcloud topic datetimes (https://cloud.google.com/sdk/gcloud/reference/topic/datetimes) for information on duration formats. |
| `--user-workload-authentication-type` | USER_WORKLOAD_AUTHENTICATION_TYPE |  | _[+ set the property dataproc/region.]_ Whether to use END_USER_CREDENTIALS or SERVICE_ACCOUNT to run the workload. |
| `--vars` | [NAME=VALUE,...] |  | _[+ set the property dataproc/region.]_ Mapping of query variable names to values (equivalent to the Spark SQL command: SET name="value";). |
| `--version` | VERSION |  | _[+ set the property dataproc/region.]_ Optional runtime version. If not specified, a default version will be used. |


**Examples:**
```bash
To submit a Spark SQL job running "my-sql-script.sql" and upload it to
"gs://my-bucket", run:

    $ gcloud dataproc batches submit spark-sql my-sql-script.sql \
        --deps-bucket=gs://my-bucket --region=us-central1 \
        --vars="NAME=VALUE,NAME2=VALUE2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/batches/submit/spark-sql)

---
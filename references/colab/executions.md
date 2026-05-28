# gcloud colab executions

manage Colab Enterprise notebook execution jobs

### `gcloud colab executions create`

Create an execution

Create a notebook execution to be used on a Colab Enterprise runtime.

**Synopsis:**
```
gcloud colab executions create
    (--display-name=DISPLAY_NAME --gcs-output-uri=GCS_OUTPUT_URI
      --notebook-runtime-template=NOTEBOOK_RUNTIME_TEMPLATE
      (--direct-content=DIRECT_CONTENT
      | [--dataform-repository-name=DATAFORM_REPOSITORY_NAME
      : --commit-sha=COMMIT_SHA] | [--gcs-notebook-uri=GCS_NOTEBOOK_URI
      : --generation=GENERATION]) (--service-account=SERVICE_ACCOUNT
      | --user-email=USER_EMAIL)
      : --execution-timeout=EXECUTION_TIMEOUT; default="24h") [--async]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | _[This must be specified.]_ The display name of the execution. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--gcs-output-uri` | GCS_OUTPUT_URI |  | _[This must be specified.]_ The Cloud Storage location to upload notebook execution results to. Format: gs://bucket-name. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--execution-timeout` | EXECUTION_TIMEOUT | 24h | _[line.]_ The max running time of the execution job, as a duration. See '$ gcloud topic datetimes' for details on formatting the input duration. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create an execution of a notebook file with Cloud Storage URI
gs://my-bucket/my-notebook.ipynb, with an execution job display name
my-execution, compute configured from runtime template
my-runtime-template-id, running with service account
my-service-account@my-project.iam.gserviceaccount.com, with results
uploaded to Cloud Storage bucket gs://my-bucket/results, and in region
us-central1 run:

    $ gcloud colab executions create --display-name=my-execution \
         --runtime-template=my-runtime-template-id \
         --gcs-notebook-uri=gs://my-bucket/my-notebook.ipynb \
         --service-account=my-service-account@my-project.iam.gserviceacco\
     unt.com --gcs-output-uri=gs://my-bucket/results --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/executions/create)

---
### `gcloud colab executions delete`

Delete an execution

Delete a Colab Enterprise notebook execution.

**Synopsis:**
```
gcloud colab executions delete (EXECUTION : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Notebook execution job resource - Unique resource name of the execution to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument execution on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the notebook execution job or fully qualified identifier for
     the notebook execution job.

     To set the name attribute:
     + provide the argument execution on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the notebook execution job.

     To set the region attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an execution with id my-execution, in region us-central1, run:

    $ gcloud colab executions delete my-execution --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/executions/delete)

---
### `gcloud colab executions describe`

Describe an execution

Describe a Colab Enterprise notebook execution.

**Synopsis:**
```
gcloud colab executions describe (EXECUTION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Notebook execution job resource - Unique resource name of the execution to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument execution on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the notebook execution job or fully qualified identifier for
     the notebook execution job.

     To set the name attribute:
     + provide the argument execution on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the notebook execution job.

     To set the region attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Examples:**
```bash
To describe a notebook execution with id my-execution in region
us-central1, run:

    $ gcloud colab executions describe my-execution --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/executions/describe)

---
### `gcloud colab executions list`

List your Colab Enterprise notebook execution jobs

List your project's Colab Enterprise notebook executions in a given region.

**Synopsis:**
```
gcloud colab executions list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property colab/region. |


**Examples:**
```bash
To list your executions in region us-central1, run:

    $ gcloud colab executions list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/executions/list)

---
# gcloud infra-manager previews

manage Preview resources

### `gcloud infra-manager previews create`

Create a preview

This command creates a preview.

**Synopsis:**
```
gcloud infra-manager previews create [PREVIEW]
    [--annotations=[KEY=VALUE,...]]
    [--artifacts-gcs-bucket=ARTIFACTS_GCS_BUCKET] [--async]
    [--deployment=DEPLOYMENT] [--labels=[KEY=VALUE,...]]
    [--location=LOCATION] [--preview-mode=PREVIEW_MODE]
    [--service-account=SERVICE_ACCOUNT]
    [--tf-version-constraint=TF_VERSION_CONSTRAINT]
    [--worker-pool=WORKER_POOL]
    [--gcs-source=GCS_SOURCE | --git-source-directory=GIT_SOURCE_DIRECTORY
      --git-source-ref=GIT_SOURCE_REF --git-source-repo=GIT_SOURCE_REPO
      | --ignore-file=IGNORE_FILE
      --local-source=LOCAL_SOURCE --input-values=[KEY=VALUE,...]
      | --inputs-file=INPUTS_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Preview resource - the preview to be used as parent. It is optional and
will be generated if not specified with a fully specified name. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument PREVIEW on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument PREVIEW on the command line with a fully
   specified name;
 * provide the argument --location on the command line;
 * set the property infra-manager/location.

  PREVIEW
     ID of the preview or fully qualified identifier for the preview.

     To set the preview attribute:
     + provide the argument PREVIEW on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Preview annotations cannot be updated after creation. |
| `--artifacts-gcs-bucket` | ARTIFACTS_GCS_BUCKET |  | user-defined location of Cloud Build logs, artifacts, and Terraform state files in Google Cloud Storage. Format: gs://{bucket}/{folder} A default bucket will be bootstrapped if the field is not set or empty |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--deployment` | DEPLOYMENT |  | Deployment reference for preview. |
| `--labels` | [KEY=VALUE,...] |  | Preview labels cannot be updated after creation. |
| `--preview-mode` | PREVIEW_MODE |  | _[+ set the property infra-manager/location.]_ Preview mode to set it to either default or delete. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ set the property infra-manager/location.]_ User-specified Service Account (SA) to be used as credential to manage resources. Format: projects/{projectID}/serviceAccounts/{serviceAccount} |
| `--tf-version-constraint` | TF_VERSION_CONSTRAINT |  | _[+ set the property infra-manager/location.]_ User-specified Terraform version constraint, for example "=1.3.10". |
| `--worker-pool` | WORKER_POOL |  | _[+ set the property infra-manager/location.]_ User-specified Worker Pool resource in which the Cloud Build job will execute. Format: projects/{project}/locations/{location}/workerPools/{workerPoolId} |


**Examples:**
```bash
Create a preview named my-preview from a storage my-bucket:

    $ gcloud infra-manager previews create \
        projects/p1/locations/us-central1/previews/my-preview \
        --gcs-source="gs://my-bucket" \
        --input-values="project=p1,region=us-central1"

Create a preview named my-preview from git repo
"https://github.com/examples/repository.git", "staging/compute" folder,
"mainline" branch:

    $ gcloud infra-manager previews create \
        projects/p1/locations/us-central1/previews/my-preview \
        --git-source-repo="https://github.com/examples/repository.git" \
        --git-source-directory="staging/compute" \
        --git-source-ref="mainline"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/previews/create)

---
### `gcloud infra-manager previews delete`

Delete previews

Delete a preview

**Synopsis:**
```
gcloud infra-manager previews delete (PREVIEW : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Preview resource - previews TBD The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument preview on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PREVIEW
     ID of the preview or fully qualified identifier for the preview.

     To set the preview attribute:
     + provide the argument preview on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument preview on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the preview example-preview at location us-central1, run:

    $ gcloud infra-manager previews delete \
        projects/example-project/locations/us-central1/previews/\
    example-preview
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/previews/delete)

---
### `gcloud infra-manager previews describe`

Describe previews

Describe a preview

**Synopsis:**
```
gcloud infra-manager previews describe (PREVIEW : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Preview resource - The preview to describe The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument preview on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PREVIEW
     ID of the preview or fully qualified identifier for the preview.

     To set the preview attribute:
     + provide the argument preview on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument preview on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Examples:**
```bash
To describe a preview example-preview in project p1 at location
us-central1, run:

    $ gcloud infra-manager previews describe \
        projects/p1/locations/us-central1/previews/example-preview
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/previews/describe)

---
### `gcloud infra-manager previews export`

Export preview results

This command generates a signed url to download a preview results.

**Synopsis:**
```
gcloud infra-manager previews export (PREVIEW : --location=LOCATION)
    [--file=FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Preview resource - the preview to be used as parent. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument PREVIEW on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PREVIEW
     ID of the preview or fully qualified identifier for the preview.

     To set the preview attribute:
     + provide the argument PREVIEW on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the preview.

     To set the location attribute:
     + provide the argument PREVIEW on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | File name for preview export artifacts. It is optional and it specifies the filename or complete path for the downloaded preview export artifacts. If only a file path is provided, the artifacts will be downloaded as "preview" within that directory. If a filename is included, the artifacts will be downloaded with that name. |


**Examples:**
```bash
Export preview results for my-preview:

    $ gcloud infra-manager previews export \
        projects/p1/locations/us-central1/previews/my-preview
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/previews/export)

---
### `gcloud infra-manager previews list`

List previews

**Synopsis:**
```
gcloud infra-manager previews list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To list all previews at location us-central1, run:

    $ gcloud infra-manager previews list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/previews/list)

---
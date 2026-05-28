# gcloud notebooks environments

notebooks Environments Command Group

### `gcloud notebooks environments create`

Request for creating environments

Request for creating environments.

**Synopsis:**
```
gcloud notebooks environments create (ENVIRONMENT : --location=LOCATION)
    ([--container-repository=CONTAINER_REPOSITORY
      : --container-tag=CONTAINER_TAG]
      | [(--vm-image-family=VM_IMAGE_FAMILY; default="common-cpu"
      | --vm-image-name=VM_IMAGE_NAME)
      : --vm-image-project=VM_IMAGE_PROJECT;
      default="deeplearning-platform-release"]) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--post-startup-script=POST_STARTUP_SCRIPT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - User-defined unique name of this environment. The
environment name must be 1 to 63 characters long and contain only
lowercase letters, numeric characters, and dashes. The first character
must be a lowercaseletter and the last character cannot be a dash. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--container-repository` | CONTAINER_REPOSITORY |  | _[Exactly one of these must be specified:]_ The path to the container image repository. For example: gcr.io/{project_id}/{image_name}. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--container-tag` | CONTAINER_TAG |  | _[Exactly one of these must be specified:]_ The tag of the container image. If not specified, this defaults to the latest tag. |
| `--vm-image-project` | VM_IMAGE_PROJECT | deeplearning-platform-release | _[Exactly one of these must be specified:]_ The ID of the Google Cloud project that this VM image belongs to.Format: projects/{project_id}. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A brief description of this environment. |
| `--display-name` | DISPLAY_NAME |  | Name to display on the UI. |
| `--post-startup-script` | POST_STARTUP_SCRIPT |  | Path to a Bash script that automatically runs after a notebook instance fully boots up. The path must be a URL or Cloud Storage path(gs://path-to-file/file-name). |


**Examples:**
```bash
To create an environment with id 'example-environment' in location
'us-central1-a' using a container repository, run:

    $ gcloud notebooks environments create example-environment \
        --location=us-central1-a \
        --container-repository=gcr.io/deeplearning-platform-release/\
    base-cpu --container-tag=test-tag --description=test-description \
        --post-startup-script=gs://path-to-file/file-name \
        --display-name=test-display-name --async

To create an environment with id 'example-environment' in location
'us-central1-a' using a VM Image Family, run:

    $ gcloud notebooks environments create example-environment \
        --vm-image-project=deeplearning-platform-release \
        --vm-image-family=caffe1-latest-cpu-experimental

To create an environment with id 'example-environment' in location
'us-central1-a' using a VM Image, run:

    $ gcloud notebooks environments create example-environment \
        --location=us-central1-a \
        --vm-image-project=deeplearning-platform-release \
        --vm-image-name=tf2-2-1-cu101-notebooks-20200110
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/environments/create)

---
### `gcloud notebooks environments delete`

Request for deleting environments

Request for deleting environments.

**Synopsis:**
```
gcloud notebooks environments delete (ENVIRONMENT : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - User-defined unique name of this environment. The
environment name must be 1 to 63 characters long and contain only
lowercase letters, numeric characters, and dashes. The first character
must be a lowercaseletter and the last character cannot be a dash. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete environment with id 'example-environment' in location
'us-central1-a', run:

    $ gcloud notebooks environments delete example-environment \
        --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/environments/delete)

---
### `gcloud notebooks environments describe`

Request for describing environments

Request for describing environments.

**Synopsis:**
```
gcloud notebooks environments describe (ENVIRONMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - User-defined unique name of this environment. The
environment name must be 1 to 63 characters long and contain only
lowercase letters, numeric characters, and dashes. The first character
must be a lowercaseletter and the last character cannot be a dash. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To describe an environment with id 'example-environment' in location
'us-central1-a', run:

    $ gcloud notebooks environments describe example-environment \
        --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/environments/describe)

---
### `gcloud notebooks environments list`

Request for listing environments

Request for listing environments.

**Synopsis:**
```
gcloud notebooks environments list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud location of this environment: https://cloud.google.com/compute/docs/regions-zones/#locations. |


**Examples:**
```bash
To list environments in location 'us-central1-a', run:

    $ gcloud notebooks environments list --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/environments/list)

---
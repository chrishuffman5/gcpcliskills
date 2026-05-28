# gcloud artifacts yum

manage Artifact Registry RPM packages

### `gcloud artifacts yum import`

Import one or more RPM packages into an artifact repository

gcloud artifacts yum import imports RPM packages from Google Cloud Storage
into the specified artifact repository.

**Synopsis:**
```
gcloud artifacts yum import [[REPOSITORY] --location=LOCATION]
    --gcs-source=[GCS_SOURCE,...] [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository. If not specified,
the current artifacts/repository is used. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * set the property artifacts/repository with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [REPOSITORY]
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line;
     + set the property artifacts/repository.

  --location=LOCATION
     Location of the repository.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + set the property artifacts/repository with a fully specified
       name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-source` | [GCS_SOURCE,...] |  | The Google Cloud Storage location of a package to import. To import multiple packages, use wildcards at the end of the path. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To import the package my-package.rpm from Google Cloud Storage into
my-repo, run:

    $ gcloud artifacts yum import my-repo --location=us-central1 \
        --gcs-source=gs://my-bucket/path/to/my-package.rpm

To import the packages my-package.rpm and other-package.rpm into my-repo,
run:

    $ gcloud artifacts yum import my-repo --location=us-central1 \
        --gcs-source=gs://my-bucket/path/to/my-package.rpm,gs://\
    my-bucket/path/to/other-package.rpm

To import all packages from my-directory into my-repo, run:

    $ gcloud artifacts yum import my-repo --location=us-central1 \
        --gcs-source=gs://my-bucket/my-directory/*

To import all packages in all subdirectories from a Google Cloud Storage
bucket into my-repo, run:

    $ gcloud artifacts yum import my-repo --location=us-central1 \
        --gcs-source=gs://my-bucket/**
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/yum/import)

---
### `gcloud artifacts yum upload`

Upload an RPM package to an artifact repository

gcloud artifacts yum upload uploads an RPM package to the specified
artifact repository.

**Synopsis:**
```
gcloud artifacts yum upload [[REPOSITORY] --location=LOCATION]
    --source=SOURCE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Repository resource - The Artifact Registry repository. If not specified,
the current artifacts/repository is used. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument repository on the command line with a fully
   specified name;
 * set the property artifacts/repository with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [REPOSITORY]
     ID of the repository or fully qualified identifier for the
     repository.

     To set the repository attribute:
     + provide the argument repository on the command line;
     + set the property artifacts/repository.

  --location=LOCATION
     Location of the repository.

     To set the location attribute:
     + provide the argument repository on the command line with a fully
       specified name;
     + set the property artifacts/repository with a fully specified
       name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | The path of a package to upload. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upload the package my-package.rpm to my-repo, run:

    $ gcloud artifacts yum upload my-repo --location=us-central1 \
        --source=my-package.rpm
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/yum/upload)

---
# gcloud artifacts attachments

manage Artifact Registry attachments

### `gcloud artifacts attachments create`

Creates an Artifact Registry attachment in a repository

Creates an Artifact Registry attachment in a repository.

**Synopsis:**
```
gcloud artifacts attachments create
    (ATTACHMENT : --location=LOCATION --repository=REPOSITORY)
    --attachment-type=ATTACHMENT_TYPE --files=[FILES,...] --target=TARGET
    [--attachment-namespace=ATTACHMENT_NAMESPACE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attachment resource - The Artifact Registry attachment name. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument attachment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTACHMENT
     ID of the attachment or fully qualified identifier for the
     attachment.

     To set the name attribute:
     + provide the argument attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the attachment.

     To set the location attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     Repository of the attachment.

     To set the repository attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-type` | ATTACHMENT_TYPE |  | Type of the attachment |
| `--files` | [FILES,...] |  | Comma-seperated list of files that are part of this attachment |
| `--target` | TARGET |  | Target of the attachment, should be fully qualified version name |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-namespace` | ATTACHMENT_NAMESPACE |  | Namespace of the attachment |


**Examples:**
```bash
To create an attachment for target
projects/myproject/locations/us-central1/packages/mypackage/versions/sha256:123
using a file located in /path/to/file/sbom.json:

    $ gcloud artifacts attachments create \
      --target=projects/myproject/locations/us-central1/packages/\
    mypackage/versions/sha256:123 --files=/path/to/file/sbom.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/attachments/create)

---
### `gcloud artifacts attachments delete`

Delete an Artifact Registry attachment

Delete an Artifact Registry attachment.

**Synopsis:**
```
gcloud artifacts attachments delete
    (ATTACHMENT : --location=LOCATION --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attachment resource - The Artifact Registry attachment to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument attachment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTACHMENT
     ID of the attachment or fully qualified identifier for the
     attachment.

     To set the attachment attribute:
     + provide the argument attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the attachment. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the attachment. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To delete an attachment my-attachment under the current project,
repository, and location, run:

    $ gcloud artifacts attachments delete my-attachment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/attachments/delete)

---
### `gcloud artifacts attachments describe`

Describe an Artifact Registry attachment

Describe an Artifact Registry attachment.

This command can fail for the following reasons:
  o The specified attachment does not exist.
  o The active account does not have permission to view attachments.

**Synopsis:**
```
gcloud artifacts attachments describe
    (ATTACHMENT : --location=LOCATION --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attachment resource - The Artifact Registry attachment to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument attachment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTACHMENT
     ID of the attachment or fully qualified identifier for the
     attachment.

     To set the attachment attribute:
     + provide the argument attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the attachment. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the attachment. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To describe an attachment named my-attachment under the current project,
repository, and location, run:

    $ gcloud artifacts attachments describe my-attachment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/attachments/describe)

---
### `gcloud artifacts attachments download`

Download an Artifact Registry attachment from a repository

Download an Artifact Registry attachment from a repository.

**Synopsis:**
```
gcloud artifacts attachments download
    [ATTACHMENT : --location=LOCATION --repository=REPOSITORY]
    --destination=DESTINATION [--chunk-size=CHUNK_SIZE]
    [--oci-version-name=OCI_VERSION_NAME] [--parallelism=PARALLELISM]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attachment resource - The Artifact Registry attachment name. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument attachment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  ATTACHMENT
     ID of the attachment or fully qualified identifier for the
     attachment.

     To set the name attribute:
     + provide the argument attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the attachment.

     To set the location attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     Repository of the attachment.

     To set the repository attribute:
     + provide the argument attachment on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path where you want to save the downloaded attachment files. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--chunk-size` | CHUNK_SIZE |  | If specified, the chunk size (bytes) to use for downloading the package. |
| `--oci-version-name` | OCI_VERSION_NAME |  | For Docker-format repositories only. The version name of the OCI artifact to download. |
| `--parallelism` | PARALLELISM |  | Specifies the number of threads to use for downloading the attachment files in parallel. |


**Examples:**
```bash
To download the attachment my-attachment to /path/to/destination/:

    $ gcloud artifacts attachments download my-attachment \
      --destination=/path/to/destination/

To download the attachment my-attachment in 8000 byte chunks to
/path/to/destination/:

    $ gcloud artifacts attachments download my-attachment \
      --destination=/path/to/destination/ --chunk-size=8000

To download the attachment my-attachment using parallel multipart download
with 4 threads:

    $ gcloud artifacts attachments download my-attachment \
      --destination=/path/to/destination/ --parallelism=4

For Docker-format repositories only: to download the attachment stored in
the OCI version
projects/my-project/locations/us/repositories/my-repo/packages/my-package/versions/sha256:123
to /path/to/destination/:

    $ gcloud artifacts attachments download \
      --oci-version-name=projects/my-project/locations/us/\
    repositories/my-repo/packages/my-package/versions/sha256:123 \
        --destination=/path/to/destination/

For Docker-format repositories only: to download the attachment stored in
the OCI version with URI
us-docker.pkg.dev/my-project/my-repo/my-package@sha256:123 to
/path/to/destination/:

    $ gcloud artifacts attachments download \
      --oci-version-name=us-docker.pkg.dev/my-project/my-repo/\
    my-package@sha256:123 --destination=/path/to/destination/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/attachments/download)

---
### `gcloud artifacts attachments list`

List Artifact Registry attachments

List all Artifact Registry attachments in the specified repository and
project.

To specify the maximum number of attachments to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts attachments list [--target=TARGET]
    [--location=LOCATION --repository=REPOSITORY] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target` | TARGET |  | Target for the list of attachments. |


**Examples:**
```bash
The following command lists a maximum of five attachments:

    $ gcloud artifacts attachments list --limit=5

The following command lists attachments with target
projects/my-project/locations/us/repositories/my-repo/packages/my-package/versions/sha256:123:

    $ gcloud artifacts attachments list \
      --target=projects/my-project/locations/us/repositories/my-repo/\
    packages/my-package/versions/sha256:123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/attachments/list)

---
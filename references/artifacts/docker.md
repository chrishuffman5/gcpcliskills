# gcloud artifacts docker

manage Artifact Registry container images and tags


## `gcloud artifacts docker images` — manage Artifact Registry container images
### `gcloud artifacts docker images delete`

Delete an Artifact Registry container image

A valid container image has the format of

    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE

A valid container image that can be referenced by tag or digest, has the
format of

    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest

This command can fail for the following reasons:
  o Trying to delete an image by digest when the image is still tagged.
    Add --delete-tags to delete the digest and the tags.
  o Trying to delete an image by tag when the image has other tags. Add
    --delete-tags to delete all tags.
  o A valid repository format was not provided.
  o The specified image does not exist.
  o The active account does not have permission to delete images.

**Synopsis:**
```
gcloud artifacts docker images delete IMAGE [--async] [--delete-tags]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE
   A container image.

   A valid container image has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE

   A valid container image that can be referenced by tag or digest, has
   the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--delete-tags` |  |  | If specified, all tags associated with the image are deleted. |


**Examples:**
```bash
To delete image busy-box in us-west1 and all of its digests and tags:

    $ gcloud artifacts docker images delete \
      us-west1-docker.pkg.dev/my-project/my-repository/busy-box

To delete image digest abcxyz under image busy-box:

    $ gcloud artifacts docker images delete \
      us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz

To delete image digest abcxyz under image busy-box while there're other
tags associate with the digest:

    $ gcloud artifacts docker images delete \
      us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz --delete-tags

To delete an image digest and its only tag my-tag under image busy-box:

    $ gcloud artifacts docker images delete \
      us-west1-docker.pkg.dev/my-project/my-repository/busy-box:my-tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/images/delete)

---
### `gcloud artifacts docker images describe`

Describe an Artifact Registry container image

Reference an image by tag or digest using the format:

    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest

This command can fail for the following reasons:
  o The repository format is invalid.
  o The specified image does not exist.
  o The active account does not have permission to run the command
    (roles/artifactregistry.reader, roles/containeranalysis.admin and
    roles/serviceusage.serviceUsageViewer).

**Synopsis:**
```
gcloud artifacts docker images describe IMAGE
    [--metadata-filter=METADATA_FILTER] [--show-all-metadata]
    [--show-build-details] [--show-deployment] [--show-image-basis]
    [--show-package-vulnerability] [--show-provenance]
    [--show-sbom-references] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE
   A container image.

   A valid container image has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE

   A valid container image that can be referenced by tag or digest, has
   the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--metadata-filter` | METADATA_FILTER |  | Additional filter to fetch metadata for a given qualified image reference. |
| `--show-all-metadata` |  |  | Include all metadata in the output. Metadata will be grouped by Grafeas kind, with an additional section for intoto provenance metadata. |
| `--show-build-details` |  |  | Include build metadata in the output. |
| `--show-deployment` |  |  | Include deployment metadata in the output. |
| `--show-image-basis` |  |  | Include base image metadata in the output. |
| `--show-package-vulnerability` |  |  | Include vulnerability metadata in the output. |
| `--show-provenance` |  |  | Include intoto provenance metadata in the output, in the provenance_summary section. To see all build metadata in the output, use --show-all-metadata or --show-build-details. |
| `--show-sbom-references` |  |  | Include SBOM metadata in the output. |


**Examples:**
```bash
To describe an image digest abcxyz under image busy-box:

    $ gcloud artifacts docker images describe \
      us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz

To describe an image busy-box with tag my-tag:

    $ gcloud artifacts docker images describe \
      us-west1-docker.pkg.dev/my-project/my-repository/busy-box:my-tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/images/describe)

---
### `gcloud artifacts docker images get-operation`

Get an On-Demand Scanning operation

Get an On-Demand Scanning operation.

**Synopsis:**
```
gcloud artifacts docker images get-operation
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The scan operation to get. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud multi-region.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command gets an On-Demand Scanning operation.

    $ gcloud artifacts docker images get-operation \
        projects/my-project/locations/europe/operations/\
    ddf40882-0d55-4214-a619-c1c36df5040c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/images/get-operation)

---
### `gcloud artifacts docker images list`

List Artifact Registry container images

List all Artifact Registry container images in the specified repository or
image path.

A valid Docker repository has the format of
LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID

A valid image has the format of
LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE_PATH

To specify the maximum number of images to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts docker images list [IMAGE_PATH] [--include-tags]
    [--occurrence-filter=OCCURRENCE_FILTER; default='kind="BUILD"
      OR kind="IMAGE" OR kind="DISCOVERY" OR kind="SBOM_REFERENCE"']
    [--show-occurrences]
    [--show-occurrences-from=SHOW_OCCURRENCES_FROM; default=10]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[IMAGE_PATH]
   An Artifact Registry repository or a container image. If not specified,
   default config values are used.

   A valid docker repository has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID

   A valid image has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE_PATH
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--include-tags` |  |  | If specified, tags associated with each image digest are displayed up to a maximum of 100 tags per version. |
| `--occurrence-filter` | OCCURRENCE_FILTER | 'kind= | A filter for the occurrences which will be summarized. |
| `--show-occurrences` |  |  | Show summaries of the various occurrence types. |
| `--show-occurrences-from` | SHOW_OCCURRENCES_FROM | 10 | The number of the most recent images for which to summarize occurrences. |


**Examples:**
```bash
To list images under the current project, repository, and location:

    $ gcloud artifacts docker images list

To list images with tags under the current project, repository, and
location:

    $ gcloud artifacts docker images list --include-tags

To list images under repository my-repo, project my-project, in
us-central1:

    $ gcloud artifacts docker images list \
      us-central1-docker.pkg.dev/my-project/my-repo

The following command lists a maximum of five images:

    $ gcloud artifacts docker images list \
      docker.pkg.dev/my-project/my-repo --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/images/list)

---
### `gcloud artifacts docker images list-vulnerabilities`

List On-Demand Scanning vulnerabilities

List On-Demand Scanning vulnerabilities from a completed scan.

**Synopsis:**
```
gcloud artifacts docker images list-vulnerabilities
    (SCAN : --location=LOCATION) [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scan resource - The scan resource to list vulnerabilites for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument scan on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCAN
     ID of the scan or fully qualified identifier for the scan.

     To set the scan attribute:
     + provide the argument scan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud multi-region.

     To set the location attribute:
     + provide the argument scan on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command lists vulnerabilities from a completed On-Demand
Scanning scan.

    $ gcloud artifacts docker images list-vulnerabilities \
        projects/my-project/locations/europe/scans/\
    fff66882-0z55-4333-l619-z1z00df6040c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/images/list-vulnerabilities)

---
### `gcloud artifacts docker images scan`

Perform a vulnerability scan on a container image

You can scan a container image in a Google Cloud registry (Artifact
Registry or Container Registry), or a local container image.

Reference an image by tag or digest using any of the formats:

    Artifact Registry:
      LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE[:tag]
      LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest

    Container Registry:
      [LOCATION.]gcr.io/PROJECT-ID/REPOSITORY-ID/IMAGE[:tag]
      [LOCATION.]gcr.io/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest

    Local:
      IMAGE[:tag]

**Synopsis:**
```
gcloud artifacts docker images scan RESOURCE_URI
    [--additional-package-types=[ADDITIONAL_PACKAGE_TYPES,...]] [--async]
    [--location=LOCATION; default="us"] [--remote]
    [--skip-package-types=[SKIP_PACKAGE_TYPES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_URI
   A container image in a Google Cloud registry (Artifact Registry or
   Container Registry), or a local container image.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-package-types` | one of: COMPOSER PHP Composer package |  | (DEPRECATED) A comma-separated list of package types to scan in addition to OS packages. This flag is deprecated as scanning for all package types is now the default. To skip scanning for specific package types, use --skip-package-types. ADDITIONAL_PACKAGE_TYPES must be one of: COMPOSER PHP Composer package. GO Go standard library and third party packages. MAVEN Maven package. NPM NPM package. NUGET NuGet package. PYTHON Python package. RUBYGEMS RubyGems package. RUST Rust package. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION | us | The API location in which to perform package analysis. Consider choosing a location closest to where you are located. Proximity to the container image does not affect response time. LOCATION must be one of: asia Perform analysis in Asia europe Perform analysis in Europe us Perform analysis in the US |
| `--remote` |  |  | Whether the container image is located remotely or on your local machine. |
| `--skip-package-types` | one of: COMPOSER PHP Composer package |  | A comma-separated list of package types to skip when scanning. SKIP_PACKAGE_TYPES must be one of: COMPOSER PHP Composer package. GO Go standard library and third party packages. MAVEN Maven package. NPM NPM package. NUGET NuGet package. PYTHON Python package. RUBYGEMS RubyGems package. RUST Rust package. |


**Examples:**
```bash
Start a scan of a container image stored in Artifact Registry:

    $ gcloud artifacts docker images scan \
      us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz --remote

Start a scan of a container image stored in the Container Registry, and
perform the analysis in Europe:

    $ gcloud artifacts docker images scan \
      eu.gcr.io/my-project/my-repository/my-image:latest --remote \
      --location=europe

Start a scan of a container image stored locally, and perform the analysis
in Asia:

    $ gcloud artifacts docker images scan ubuntu:latest --location=asia
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/images/scan)

---

## `gcloud artifacts docker tags` — manage Artifact Registry container image tags
### `gcloud artifacts docker tags add`

Add a tag to a container image in Artifact Registry

Create or update a tag for a container image in Artifact Registry.

A valid Docker tag has the format of

    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag

A valid container image that can be referenced by tag or digest, has the
format of

    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
    LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest

**Synopsis:**
```
gcloud artifacts docker tags add DOCKER_IMAGE DOCKER_TAG
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOCKER_IMAGE
   Docker image - The container image that you want to tag.

   A valid container image can be referenced by tag or digest, has the
   format of LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE@sha256:digest

DOCKER_TAG
   Image tag - The container image tag.

   A valid Docker tag has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
```

**Examples:**
```bash
To add tag my-tag to image busy-box referenced by digest abcxyz in
us-west1:

    $ gcloud artifacts docker tags add \
        us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz \
        us-west1-docker.pkg.dev/my-project/my-repository/busy-box:my-tag

To add tag my-tag to image busy-box referenced by tag latest in us-west1:

    $ gcloud artifacts docker tags add \
        us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box:latest \
        us-west1-docker.pkg.dev/my-project/my-repository/busy-box:my-tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/tags/add)

---
### `gcloud artifacts docker tags delete`

Delete a tag from a container image in Artifact Registry

A valid Docker tag has the format of

    [<location>-]docker.pkg.dev/PROJECT_ID/REPOSITORY-ID/IMAGE_PATH:tag

**Synopsis:**
```
gcloud artifacts docker tags delete DOCKER_TAG [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOCKER_TAG
   Image tag - The container image tag.

   A valid Docker tag has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE:tag
```

**Examples:**
```bash
To delete tag my-tag from image busy-box in us-west1:

    $ gcloud artifacts docker tags delete \
        us-west1-docker.pkg.dev/my-project/my-repository/busy-box:my-tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/tags/delete)

---
### `gcloud artifacts docker tags list`

List all tags associated with a container image in Artifact Registry

A valid Docker top layer image has the format of

    [<location>-]docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE_PATH

A valid container image can be referenced by tag or digest, has the format
of

    [<location>-]docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE_PATH:tag
    [<location>-]docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE_PATH@sha256:digest

To specify the maximum number of repositories to list, use the --limit
flag.

**Synopsis:**
```
gcloud artifacts docker tags list [IMAGE_PATH] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[IMAGE_PATH]
   An Artifact Registry repository or a container image. If not specified,
   default config values are used.

   A valid docker repository has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID

   A valid image has the format of
   LOCATION-docker.pkg.dev/PROJECT-ID/REPOSITORY-ID/IMAGE_PATH
```

**Examples:**
```bash
To list all tags under the current project, repository, and location:

    $ gcloud artifacts docker tags list

To list all tags under the my-project, my-repository, across all locations:

    $ gcloud artifacts docker tags list \
        docker.pkg.dev/my-project/my-repository

To list all tags in repository my-repository in us-west1:

    $ gcloud artifacts docker tags list \
        us-west1-docker.pkg.dev/my-project/my-repository

To list tags for image busy-box in us-west1:

    $ gcloud artifacts docker tags list \
        us-west1-docker.pkg.dev/my-project/my-repository/busy-box
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/tags/list)

---

## `gcloud artifacts docker upgrade` — commands to support Container Registry to Artifact Registry upgrade
### `gcloud artifacts docker upgrade migrate`

Migrate projects from Container Registry to Artifact Registry

**Synopsis:**
```
gcloud artifacts docker upgrade migrate [--canary-reads=PERCENT]
    [--copy-only] [--from-gcr=GCR_HOST/PROJECT_ID]
    [--input-iam-policy-dir=DIRECTORY] [--last-uploaded-versions=N]
    [--max-threads=MAX_THREADS; default=8]
    [--output-iam-policy-dir=DIRECTORY]
    [--pkg-dev-location=PKG_DEV_LOCATION] [--projects=PROJECTS]
    [--recent-images=NUM_DAYS] [--skip-iam-update] [--skip-pre-copy]
    [--to-pkg-dev=PROJECT_ID/REPOSITORY_ID] [--no-use-analyze-iam]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--canary-reads` | PERCENT |  | Send only a percent of reads to Artifact Registry. The rest of reads and all writes are sent to Container Registry. |
| `--copy-only` |  |  | Only perform image copying |
| `--from-gcr` | GCR_HOST/PROJECT_ID |  | Container Registry host + project to copy from. This flag is only used when migrating to pkg.dev repos. Example: gcr.io/my-project |
| `--input-iam-policy-dir` | DIRECTORY |  | During the IAM update step, the tool applies all iam policies in the given directory. |
| `--last-uploaded-versions` | N |  | Only copy the N most recently uploaded versions of each image. More than N images may be copied if new images are uploaded during migration. |
| `--max-threads` | MAX_THREADS | 8 | Max number of images to copy simultaneously. Consider quota usage when increasing this |
| `--output-iam-policy-dir` | DIRECTORY |  | Outputs Artifact Registry-equivalent bindings to this directory during IAM update step and then exits the tool. After any neccesary modifications are made, the tool can be rerun with --input-iam-policy-dir to continue migration with the generated bindings. |
| `--pkg-dev-location` | PKG_DEV_LOCATION |  | The location of the pkg-dev repository you are migrating to. If not specified, migration is always done to the same multi-region as GCR. Setting this flag can cause cross-regional copying and lead to billing charges. |
| `--projects` | PROJECTS |  | Comma seperated list of Container Registry projects to migrate to Artifact Registry gcr.io repositories. |
| `--recent-images` | NUM_DAYS |  | Only copy images pulled or pushed in the last NUM_DAYS days. NUM_DAYS must be between 30 and 90 inclusive. |
| `--skip-iam-update` |  |  | Migrate without changing iam-policy. Users without Artifact Registry permissions will not have access to migrated images. |
| `--skip-pre-copy` |  |  | Skip the initial copy of recent images before enabling redirection. |
| `--to-pkg-dev` | PROJECT_ID/REPOSITORY_ID |  | Artifact Registry pkg.dev project ID and repository ID to copy to. Example: my-project/my-repo |
| `--use-analyze-iam` |  |  | Use analyzeIAMPolicy to get IAM bindings. If false, tooling iterates through IAM bindings itself, which is slower, but doesn't require anlayzeIAMPolicy quota. Enabled by default, use --no-use-analyze-iam to disable. |


**Examples:**
```bash
To migrate a project my-project using gcr.io repositories:

    $ gcloud artifacts docker upgrade migrate --projects=my-project

To migrate several projects using gcr.io repositories:

    $ gcloud artifacts docker upgrade migrate \
       --projects=my-project1,my-project2,my-project3

To migrate a project using pkg.dev repositories:

    $ gcloud artifacts docker upgrade migrate \
       --from-gcr=gcr.io/project1 --to-pkg-dev=project2/repo_name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/docker/upgrade/migrate)

---
# gcloud container images

list and manipulate Google Container Registry images

### `gcloud container images add-tag`

Adds tags to existing image

The container images add-tag command adds the tag(s) specified in the
second (and following) tag parameter(s) to the image referenced in the
first tag parameter. Repositories must be hosted by the Google Container
Registry.

**Synopsis:**
```
gcloud container images add-tag SRC_IMAGE DEST_IMAGE [DEST_IMAGE ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SRC_IMAGE
   The fully qualified name(s) of image(s) to add tags for. The name(s)
   should be formatted as *.gcr.io/PROJECT_ID/IMAGE_PATH@sha256:DIGEST or
   *.gcr.io/PROJECT_ID/IMAGE_PATH:TAG.

DEST_IMAGE [DEST_IMAGE ...]
   The fully qualified name(s) of image(s) to be the new tags. The name(s)
   should be formatted as *.gcr.io/PROJECT_ID/IMAGE_PATH:TAG.
```

**Examples:**
```bash
Add a tag to another tag:

    $ gcloud container images add-tag gcr.io/myproject/myimage:mytag1 \
        gcr.io/myproject/myimage:mytag2

Add a tag to a digest

    $ gcloud container images add-tag \
        gcr.io/myproject/myimage@sha256:digest \
        gcr.io/myproject/myimage:mytag2

Add a tag to latest

    $ gcloud container images add-tag gcr.io/myproject/myimage \
        gcr.io/myproject/myimage:mytag2

Promote a tag to latest

    $ gcloud container images add-tag gcr.io/myproject/myimage:mytag1 \
        gcr.io/myproject/myimage:latest
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/add-tag)

---
### `gcloud container images delete`

Delete existing images

The container images delete command deletes the specified image from the
registry. All associated tags are also deleted.

**Synopsis:**
```
gcloud container images delete IMAGE_NAME [IMAGE_NAME ...]
    [--force-delete-tags] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME [IMAGE_NAME ...]
   The fully qualified name(s) of image(s) to delete. The name(s) should
   be formatted as *.gcr.io/PROJECT_ID/IMAGE_PATH@sha256:DIGEST or
   *.gcr.io/PROJECT_ID/IMAGE_PATH:TAG.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force-delete-tags` |  |  | If there are tags pointing to an image to be deleted then they must all be specified explicitly, or this flag must be specified, for the command to succeed. |


**Examples:**
```bash
Deletes the image as long as there aren't additional, unspecified tags
referencing it:

    $ gcloud container images delete <IMAGE_NAME>

Deletes the image (and tags) from the input IMAGE_NAME:

    $ gcloud container images delete <IMAGE_NAME> --force-delete-tags

Deletes the image (and tags) from the input IMAGE_NAME, without additional
prompting:

    $ gcloud container images delete <IMAGE_NAME> --force-delete-tags \
        --quiet

To easily identify and delete untagged images in a project, first filter
digests that lack tags:

    $ gcloud container images list-tags \
        [HOSTNAME]/[PROJECT-ID]/[IMAGE] --filter='-tags:*' \
        --format="get(digest)" --limit=$BIG_NUMBER

Then, delete these tagless images without prompting by running:

    $ gcloud container images delete \
        [HOSTNAME]/[PROJECT-ID]/[IMAGE]@DIGEST --quiet
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/delete)

---
### `gcloud container images describe`

Lists information about the specified image

**Synopsis:**
```
gcloud container images describe IMAGE_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   The fully qualified name(s) of image(s) to describe. The name(s) should
   be formatted as *.gcr.io/PROJECT_ID/IMAGE_PATH@sha256:DIGEST or
   *.gcr.io/PROJECT_ID/IMAGE_PATH:TAG.
```

**Examples:**
```bash
Describe the specified image:

    $ gcloud container images describe gcr.io/myproject/myimage@digest

    Or:

    $ gcloud container images describe gcr.io/myproject/myimage:tag

Find the digest for a tag:

    $ gcloud container images describe gcr.io/myproject/myimage:tag \
        --format="value(image_summary.digest)"

    Or:

    $ gcloud container images describe gcr.io/myproject/myimage:tag \
        --format="value(image_summary.fully_qualified_digest)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/describe)

---
### `gcloud container images list`

List existing images

The container images list command of gcloud lists metadata about existing
container images in a specified repository. Repositories must be hosted by
the Google Container Registry.

**Synopsis:**
```
gcloud container images list [--repository=REPOSITORY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--repository` | REPOSITORY |  | The name of the repository. Format: *.gcr.io/repository. Defaults to gcr.io/<project>, for the active project. |


**Examples:**
```bash
List the images in a specified repository:

    $ gcloud container images list --repository=gcr.io/myproject

List the images in the default repository:

    $ gcloud container images list

List images with names prefixed with 'test-project':

    $ gcloud container images list --filter="name:test-project"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/list)

---
### `gcloud container images list-gcr-usage`

List Container Registry usage

List Container Registry usage for all projects in the specified scope
(project/organization/folder). Caller must have
cloudasset.assets.searchAllResources permission on the requested scope and
storage.objects.list permission on the Cloud Storage buckets used by
Container Registry.

The tool returns the following lists of usage states:

ACTIVE: Container Registry usage has occurred in the last 30 days. The host
location and project are not redirected.

INACTIVE: No Container Registry usage has occurred in the last 30 days. The
host location and project are not redirected.

REDIRECTED: The project has been redirected to Artifact Registry but still
has Container Registry Cloud Storage buckets. This project will continue to
function after Container Registry is turned down and no further action is
required. You can reduce costs by deleting the Container Registry Cloud
Storage buckets.

REDIRECTION_INCOMPLETE: Requests are redirected to Artifact Registry, but
data is still being copied from Container Registry.

LEGACY: Container Registry usage is unknown. This state is caused by legacy
Container Registry projects that store container image metadata files in
Cloud Storage buckets. For more information on legacy Container Registry
projects, see
https://cloud.google.com/container-registry/docs/deprecations/feature-deprecations#container_image_metadata_storage_change.

**Synopsis:**
```
gcloud container images list-gcr-usage
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list Container Registry usage in a project:

    $ gcloud container images list-gcr-usage --project=my-proj

To list Container Registry usage in an organization:

    $ gcloud container images list-gcr-usage --organization=my-org

To list Container Registry usage in a folder:

    $ gcloud container images list-gcr-usage --folder=my-folder

To list all active Container Registry usage in an organization:

    $ gcloud container images list-gcr-usage --organization=my-org \
        --filter="usage=ACTIVE"

To list all projects that aren't redirected yet:

    $ gcloud container images list-gcr-usage --organization=my-org \
        --filter="usage!=REDIRECTED"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/list-gcr-usage)

---
### `gcloud container images list-tags`

List tags and digests for the specified image

The container images list-tags command of gcloud lists metadata about tags
and digests for the specified container image. Images must be hosted by the
Google Container Registry.

**Synopsis:**
```
gcloud container images list-tags IMAGE_NAME [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]; default="~timestamp"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   The name of the image to list tags for. The name format should be
   *.gcr.io/PROJECT_ID/IMAGE_PATH.
```

**Examples:**
```bash
List the tags in a specified image:

    $ gcloud container images list-tags gcr.io/myproject/myimage

To receive the full, JSON-formatted output (with untruncated digests):

    $ gcloud container images list-tags gcr.io/myproject/myimage \
        --format=json

To list digests without corresponding tags:

    $ gcloud container images list-tags gcr.io/myproject/myimage \
        --filter="NOT tags:*"

To list images that have a tag with the value '30e5504145':

    $ gcloud container images list-tags --filter="'tags:30e5504145'"

The last example encloses the filter expression in single quotes because
the value '30e5504145' could be interpreted as a number in scientific
notation.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/list-tags)

---
### `gcloud container images untag`

Remove existing image tags

The container images untag command removes the specified tag from the
image.

**Synopsis:**
```
gcloud container images untag IMAGE_NAME [IMAGE_NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME [IMAGE_NAME ...]
   The fully qualified name(s) of image(s) to untag. The name(s) should be
   formatted as *.gcr.io/PROJECT_ID/IMAGE_PATH:TAG.
```

**Examples:**
```bash
Removes the tag from the input IMAGE_NAME:

    $ gcloud container images untag <IMAGE_NAME>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/images/untag)

---
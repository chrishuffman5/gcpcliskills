# gcloud artifacts tags

manage Artifact Registry tags

### `gcloud artifacts tags create`

Create an Artifact Registry tag

Create a new Artifact Registry tag.

This command can fail for the following reasons:
  o A tag with the same name already exists.
  o The specified version or package does not exist.
  o The active account does not have permission to create tags.
  o The specified package format doesn't support tag operations (e.g.
    maven).

**Synopsis:**
```
gcloud artifacts tags create
    (TAG : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    --version=VERSION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag resource - The Artifact Registry tag to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG
     ID of the tag or fully qualified identifier for the tag.

     To set the tag attribute:
     + provide the argument tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     The package associated with the tag.

     To set the package attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     The repository associated with the tag. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | The version associated with the tag. |


**Examples:**
```bash
To create a tag with the name my-tag for version 1.0.0 of package my-pkg
under the current project, repository, and location, run:

    $ gcloud artifacts tags create my-tag --version=1.0.0 \
        --package=my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/tags/create)

---
### `gcloud artifacts tags delete`

Delete an Artifact Registry tag

Delete an Artifact Registry tag.

This command can fail for the following reasons:
  o The specified tag does not exist.
  o The specified version or package does not exist.
  o The active account does not have permission to delete tags.
  o The specified package format doesn't support tag operations (e.g.
    maven).

**Synopsis:**
```
gcloud artifacts tags delete
    (TAG : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag resource - The Artifact Registry tag to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG
     ID of the tag or fully qualified identifier for the tag.

     To set the tag attribute:
     + provide the argument tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     The package associated with the tag.

     To set the package attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     The repository associated with the tag. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To delete tag my-tag in package my-pkg under the current project,
repository, and location, run:

    $ gcloud artifacts tags delete my-tag --package=my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/tags/delete)

---
### `gcloud artifacts tags export`

Export an Artifact Registry package version by tag

Export files of an Artifact Registry package version by tag to a Google
Cloud Storage path.

**Synopsis:**
```
gcloud artifacts tags export
    (TAG : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    --gcs-destination=GCS_DESTINATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag resource - The Artifact Registry tag name. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG
     ID of the tag or fully qualified identifier for the tag.

     To set the name attribute:
     + provide the argument tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag.

     To set the location attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     Package of the tag.

     To set the package attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     Repository of the tag.

     To set the repository attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-destination` | GCS_DESTINATION |  | Google Cloud Storage path to export the artifact to. |


**Examples:**
```bash
To export by tag t1 of package my-pkg to a Google Cloud Storage path
gs://my-bucket/sub-folder under the current project, repository, and
location, run:

    $ gcloud artifacts tags export t1 --package=my-pkg \
      --gcs-destination=gs://my-bucket/sub-folder
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/tags/export)

---
### `gcloud artifacts tags list`

List Artifact Registry tags

List all Artifact Registry tags in the specified package.

This command can fail for the following reasons:
  o The specified version or package does not exist.
  o The active account does not have permission to list tags.
  o The specified package format doesn't support tag operations (e.g.
    maven).

To specify the maximum number of tags to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts tags list --package=PACKAGE
    [--location=LOCATION --repository=REPOSITORY] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--package` | PACKAGE |  | List all tags in a specified artifact, such as a container image or a language package. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location of the repository. To set the location attribute: + provide the argument --repository on the command line with a fully specified name; + set the property artifacts/repository with a fully specified name; + provide the argument --location on the command line; + set the property artifacts/location. |
| `--repository` | REPOSITORY |  | _[* set the property core/project.]_ ID of the repository or fully qualified identifier for the repository. To set the repository attribute: + provide the argument --repository on the command line; + set the property artifacts/repository. |


**Examples:**
```bash
To list tags for package my-package:

    $ gcloud artifacts tags list --package=my-package

The following command lists a maximum of five tags for package my-package:

    $ gcloud artifacts tags list --package=my-package --limit=5

To list tags of package my-package with name as my-tag:

    $ gcloud artifacts tags list --package=my-package \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my-package/tags/my-tag"'

To list tags of package my-package with a given partial name, use * to
match any character in name:

    $ gcloud artifacts tags list --package=my-package \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my-package/tags/my*"'

    $ gcloud artifacts tags list --package=my-package \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my-package/tags/*tag"'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/tags/list)

---
### `gcloud artifacts tags update`

Update an Artifact Registry tag

Update an Artifact Registry tag.

This command can fail for the following reasons:
  o The tag does not exist.
  o The specified version or package does not exist.
  o The active account does not have permission to update tags.
  o The specified package format doesn't support tag operations (e.g.
    maven).

**Synopsis:**
```
gcloud artifacts tags update
    (TAG : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    --version=VERSION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag resource - The Artifact Registry tag to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG
     ID of the tag or fully qualified identifier for the tag.

     To set the tag attribute:
     + provide the argument tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     The package associated with the tag.

     To set the package attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     The repository associated with the tag. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument tag on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | The version associated with the tag. |


**Examples:**
```bash
To update a tag with the name my-tag to version 1.0.0 of package my-pkg
from another version, run:

    $ gcloud artifacts tags update my-tag --version=1.0.0 \
        --package=my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/tags/update)

---
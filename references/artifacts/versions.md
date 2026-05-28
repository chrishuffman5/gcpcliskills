# gcloud artifacts versions

manage Artifact Registry package versions

### `gcloud artifacts versions delete`

Delete an Artifact Registry package version

Delete an Artifact Registry package version.

This command can fail for the following reasons:
  o The specified package version does not exist.
  o The active account does not have permission to delete package
    versions.

**Synopsis:**
```
gcloud artifacts versions delete
    (VERSION
      : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    [--async] [--delete-tags] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The Artifact Registry package version to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the version. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     The package associated with the version.

     To set the package attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     The repository associated with the version. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--delete-tags` |  |  | If specified, all tags associated with the version are deleted. |


**Examples:**
```bash
To delete version 1.0.0 of my-pkg under the current project, repository,
and location, run:

    $ gcloud artifacts versions delete 1.0.0 --package=my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/versions/delete)

---
### `gcloud artifacts versions describe`

Describe an Artifact Registry package version

Describe an Artifact Registry package version.

This command can fail for the following reasons:
  o The specified package version does not exist.
  o The active account does not have permission to describe package
    versions.

**Synopsis:**
```
gcloud artifacts versions describe
    (VERSION
      : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    [--show-package-vulnerability] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The Artifact Registry package version to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the version. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     The package associated with the version.

     To set the package attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     The repository associated with the version. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-package-vulnerability` |  |  | Include vulnerability metadata in the output. |


**Examples:**
```bash
To describe version 1.0.0 of my-pkg under the current project, repository,
and location, run:

    $ gcloud artifacts versions describe 1.0.0 --package=my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/versions/describe)

---
### `gcloud artifacts versions export`

Export an Artifact Registry package version

Export files of an Artifact Registry package version to a Google Cloud
Storage path.

**Synopsis:**
```
gcloud artifacts versions export
    (VERSION
      : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    --gcs-destination=GCS_DESTINATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The Artifact Registry version name. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the name attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the version.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     Package of the version.

     To set the package attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     Repository of the version.

     To set the repository attribute:
     + provide the argument version on the command line with a fully
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
To export version 1.0.0 of package my-pkg to a Google Cloud Storage path
gs://my-bucket/sub-folder under the current project, repository, and
location, run:

    $ gcloud artifacts versions export 1.0.0 --package=my-pkg \
      --gcs-destination=gs://my-bucket/sub-folder
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/versions/export)

---
### `gcloud artifacts versions list`

List Artifact Registry package versions

List all Artifact Registry versions in the specified package.

To specify the maximum number of versions to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts versions list --package=PACKAGE
    [--location=LOCATION --repository=REPOSITORY] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--package` | PACKAGE |  | List all versions in a specified artifact, such as a container image or a language package. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location of the repository. To set the location attribute: + provide the argument --repository on the command line with a fully specified name; + set the property artifacts/repository with a fully specified name; + provide the argument --location on the command line; + set the property artifacts/location. |
| `--repository` | REPOSITORY |  | _[* set the property core/project.]_ ID of the repository or fully qualified identifier for the repository. To set the repository attribute: + provide the argument --repository on the command line; + set the property artifacts/repository. |


**Examples:**
```bash
The following command lists a maximum of five packages versions:

    $ gcloud artifacts versions list --limit=5

To list versions of package my_pkg with name as 1.0-SNAPSHOT:

    $ gcloud artifacts versions list --package=my_pkg \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my_pkg/versions/1.0-SNAPSHOT"'

To list versions of package my_pkg with a given partial name, use * to
match any character in name:

    $ gcloud artifacts versions list --package=my_pkg \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my_pkg/versions/1.0*"'

    $ gcloud artifacts versions list --package=my_pkg \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my_pkg/versions/*SNAPSHOT"'

To list versions of package my_pkg that have annotations:

    $ gcloud artifacts versions list --package=my_pkg \
      --filter=annotations:*

To list versions of package my_pkg with annotations pair as
[annotation_key: annotation_value]:

    $ gcloud artifacts versions list --package=my_pkg \
      --filter='annotations.annotation_key:annotation_value'

To list versions of package my_pkg with annotations containing key as
my_key:

    $ gcloud artifacts versions list --package=my_pkg \
      --filter=annotations.my_key

    If the key or value contains special characters, such as `my.key` and `my.value`, backtick("`") is required:

    $ gcloud artifacts versions list --filter='annotations.`my.key`'

    $ gcloud artifacts versions list \
      --filter='annotations.`my.key`:`my.value`'

To list versions of package my_pkg with given partial annotation key or
value, use * to match any character:

    $ gcloud artifacts versions list \
      --filter='annotations.*key:`*.value`'

To list versions of package my_pkg ordered by create_time:

    $ gcloud artifacts versions list --package=my_pkg \
        --sort-by=create_time

To list versions of package my_pkg ordered by update_time reversely:

    $ gcloud artifacts versions list --package=my_pkg \
        --sort-by=~update_time
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/versions/list)

---
### `gcloud artifacts versions update`

Update annotations on an Artifact Registry package version

Update annotations on an Artifact Registry package version.

**Synopsis:**
```
gcloud artifacts versions update
    (VERSION
      : --location=LOCATION --package=PACKAGE --repository=REPOSITORY)
    [--annotations=[ANNOTATIONS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Version resource - The Artifact Registry package version to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument version on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VERSION
     ID of the version or fully qualified identifier for the version.

     To set the version attribute:
     + provide the argument version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the version. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --package=PACKAGE
     The package associated with the version.

     To set the package attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --package on the command line.

  --repository=REPOSITORY
     The repository associated with the version. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument version on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [ANNOTATIONS,...] |  | List of annotations in the format of KEY=VALUE pairs to add, update, or remove. Duplicate keys will be overwritten. For more details on annotations, see https://google.aip.dev/148#annotations. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --annotations=string=string JSON Example: --annotations='{"string": "string"}' File Example: --annotations=path_to_file.(yaml\|json) |


**Examples:**
```bash
To update annotations on version 1.0.0 of my-pkg when the project ID,
repository and location defaults are set, run the following command:

CAUTION: This command will overwrite any existing annotations on the
version.

    $ gcloud artifacts versions update 1.0.0 --package=my-pkg \
      --annotations=key1=value1,key2=value2

To clear all annotations on the version run the following command:

    $ gcloud artifacts versions update 1.0.0 --package=my-pkg \
      --annotations={}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/versions/update)

---
# gcloud artifacts packages

manage Artifact Registry packages

### `gcloud artifacts packages delete`

Delete an Artifact Registry package

Delete an Artifact Registry package.

This command can fail for the following reasons:
  o The specified package does not exist.
  o The active account does not have permission to delete packages.

**Synopsis:**
```
gcloud artifacts packages delete
    (PACKAGE : --location=LOCATION --repository=REPOSITORY) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Package resource - The Artifact Registry package to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument package on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PACKAGE
     ID of the package or fully qualified identifier for the package.

     To set the package attribute:
     + provide the argument package on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the package. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument package on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the package. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument package on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a package named my-pkg under the current project, repository, and
location, run:

    $ gcloud artifacts packages delete my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/packages/delete)

---
### `gcloud artifacts packages describe`

Describe an Artifact Registry package

Describe an Artifact Registry package.

This command can fail for the following reasons:
  o The specified package does not exist.
  o The active account does not have permission to view packages.

**Synopsis:**
```
gcloud artifacts packages describe
    (PACKAGE : --location=LOCATION --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Package resource - The Artifact Registry package to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument package on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PACKAGE
     ID of the package or fully qualified identifier for the package.

     To set the package attribute:
     + provide the argument package on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the package. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument package on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the package. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument package on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To describe a package named my-pkg under the current project, repository,
and location, run:

    $ gcloud artifacts packages describe my-pkg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/packages/describe)

---
### `gcloud artifacts packages list`

List Artifact Registry packages

List all Artifact Registry packages in the specified repository and
project.

To specify the maximum number of packages to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts packages list
    [--location=LOCATION --repository=REPOSITORY] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location of the repository. To set the location attribute: + provide the argument --repository on the command line with a fully specified name; + set the property artifacts/repository with a fully specified name; + provide the argument --location on the command line; + set the property artifacts/location. |
| `--repository` | REPOSITORY |  | _[* set the property core/project.]_ ID of the repository or fully qualified identifier for the repository. To set the repository attribute: + provide the argument --repository on the command line; + set the property artifacts/repository. |


**Examples:**
```bash
The following command lists a maximum of five packages:

    $ gcloud artifacts packages list --limit=5

To list packages with name as my-pkg:

    $ gcloud artifacts packages list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my-pkg"

To list packages with a given partial name, use * to match any character in
name:

    $ gcloud artifacts packages list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/*pkg"'

    $ gcloud artifacts packages list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/packages/my*"'

To list files that have annotations:

    $ gcloud artifacts packages list --filter=annotations:*

To list packages with annotations pair as [annotation_key:
annotation_value]:

    $ gcloud artifacts packages list \
      --filter='annotations.annotation_key:annotation_value'

To list packages with annotations containing key as my_key:

    $ gcloud artifacts packages list --filter='annotations.my_key'

    If the key or value contains special characters, such as `my.key` or `my.value`, backtick("`") is required:

    $ gcloud artifacts packages list --filter='annotations.`my.key`'

    $ gcloud artifacts packages list \
      --filter='annotations.`my.key`:`my.value`'

To list packages with given partial annotation key or value, use * to match
any character:

    $ gcloud artifacts packages list \
      --filter='annotations.my_*:`*.value`'

To list packages ordered by create_time:

    $ gcloud artifacts packages list --sort-by=create_time

To list packages ordered by update_time reversely:

    $ gcloud artifacts packages list --sort-by=~update_time
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/packages/list)

---
### `gcloud artifacts packages update`

Update annotations on an Artifact Registry package

Update annotations on an Artifact Registry package.

**Synopsis:**
```
gcloud artifacts packages update
    (PACKAGE : --location=LOCATION --repository=REPOSITORY)
    [--annotations=[ANNOTATIONS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Package resource - The Artifact Registry package to update. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument package on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PACKAGE
     ID of the package or fully qualified identifier for the package.

     To set the package attribute:
     + provide the argument package on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the package. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument package on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the package. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument package on the command line with a fully
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
To update annotations on a package named my-pkg when the project ID,
repository and location defaults are set, run the following command:

CAUTION: This command will overwrite any existing annotations on the
package.

    $ gcloud artifacts packages update my-pkg \
      --annotations=key1=value1,key2=value2

To clear all annotations on the package run the following command:

    $ gcloud artifacts packages update my-pkg --annotations={}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/packages/update)

---
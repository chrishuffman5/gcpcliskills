# gcloud artifacts files

manage Artifact Registry files

### `gcloud artifacts files delete`

Delete an Artifact Registry file

Delete an Artifact Registry file.

This command can fail for the following reasons:
  o The specified file does not exist.
  o The active account does not have permission to delete files.
  o The repository is not a Generic repository.

**Synopsis:**
```
gcloud artifacts files delete
    (FILE : --location=LOCATION --repository=REPOSITORY) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
File resource - The Artifact Registry file to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument file on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FILE
     ID of the file or fully qualified identifier for the file.

     To set the file attribute:
     + provide the argument file on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the file. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the file. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument file on the command line with a fully
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
To delete a file named pkg:1.0.0:file1.txt under the current project,
repository, and location, run:

    $ gcloud artifacts files delete pkg:v0.0.1:file1.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/files/delete)

---
### `gcloud artifacts files describe`

Describe an Artifact Registry file

Describe an Artifact Registry file.

The file hashes are displayed as hex strings.

This command can fail for the following reasons:
  o The specified file does not exist.
  o The active account does not have permission to view file.

**Synopsis:**
```
gcloud artifacts files describe
    (FILE : --location=LOCATION --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
File resource - The Artifact Registry file to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument file on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FILE
     ID of the file or fully qualified identifier for the file.

     To set the file attribute:
     + provide the argument file on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the file. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the file. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To describe a file named my-file.txt under the current project, repository,
and location, run:

    $ gcloud artifacts files describe my-file.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/files/describe)

---
### `gcloud artifacts files download`

Download an Artifact Registry file

Downloads an Artifact Registry file based on file name.

**Synopsis:**
```
gcloud artifacts files download
    (FILE : --location=LOCATION --repository=REPOSITORY)
    --destination=DESTINATION [--allow-overwrite]
    [--local-filename=LOCAL_FILENAME] [--parallelism=PARALLELISM]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
File resource - The Artifact Registry file name. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument file on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FILE
     ID of the file or fully qualified identifier for the file.

     To set the name attribute:
     + provide the argument file on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the file.

     To set the location attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     Repository of the file.

     To set the repository attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | The path where you want to download the file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-overwrite` |  |  | If specified, the command overwrites an existing file |
| `--local-filename` | LOCAL_FILENAME |  | If specified, the name of the downloaded file on the local system is set to the value you use for LOCAL_FILENAME. Otherwise the name of the downloaded file is based on the file name in the registry. |
| `--parallelism` | PARALLELISM |  | Specifies the number of threads to use for downloading the file in parallel. |


**Examples:**
```bash
To download a file named myfile in project my-project under repository
my-repo in us-central1 to the local path ~/:

    $ gcloud artifacts files download --location=us-central1 \
      --project=my-project --repository=my-repo --destination=~/ \
      myfile

To download a file named myfile in project my-project under repository
my-repo in us-central1 to the local path ~/ using parallel multipart
download with 4 threads:

    $ gcloud artifacts files download --location=us-central1 \
      --project=my-project --repository=my-repo --destination=~/ \
      --parallelism=4 myfile

To download a file named myfile in project my-project under repository
my-repo in us-central1 to the local path ~/ with file overwriting enabled:

    $ gcloud artifacts files download --location=us-central1 \
      --project=my-project --repository=my-repo --destination=~/ \
      myfile --allow-overwrite
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/files/download)

---
### `gcloud artifacts files list`

List Artifact Registry files

List all Artifact Registry files in the specified repository and location.

To specify the maximum number of files to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts files list [--package=PACKAGE] [--tag=TAG]
    [--version=VERSION] [--location=LOCATION --repository=REPOSITORY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--package` | PACKAGE |  | List all files in a specified artifact, such as a container image or a language package. If you do not use --tag or --version in the command, the command lists files in all versions of the artifact. |
| `--tag` | TAG |  | List all files in the artifact version with the specified tag. This flag only works with formats that use tags, such as container images. Use the --package flag to specify the artifact. |
| `--version` | VERSION |  | List all files in the specified artifact version. Use the --package flag to specify the artifact. |


**Examples:**
```bash
To list files in the current project under repository my-repo in us:

    $ gcloud artifacts files list --repository=my-repo --location=us

The following command lists a maximum of five files:

    $ gcloud artifacts files list --repository=my-repo --location=us \
      --limit=5

To list files in the current project under repository my-repo in us owned
by package my-package:

    $ gcloud artifacts files list --repository=my-repo --location=us \
      --package=my-package

To list files in the current project under repository my-repo in us owned
by package my-package and version 1.0.0:

    $ gcloud artifacts files list --repository=my-repo --location=us \
      --package=my-package --version=1.0.0

To list files in the current project under repository my-repo in us owned
by package my-package and tag name my-tag:

    $ gcloud artifacts files list --repository=my-repo --location=us \
      --package=my-package --tag=my-tag

To list files with name as my-file:

    $ gcloud artifacts files list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/files/my-file"'

To list files with a given partial name, use * to match any character in
name:

    $ gcloud artifacts files list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/files/*file"'

    $ gcloud artifacts files list \
      --filter='name="projects/my-project/locations/us/repositories/my\
    -repo/files/my-*"'

To list files that have annotations:

    $ gcloud artifacts files list --filter=annotations:*

To list files with annotations pair as [annotation_key: annotation_value]

    $ gcloud artifacts files list \
      --filter='annotations.annotation_key:annotation_value'

To list files with annotations containing key as my_key:

    $ gcloud artifacts files list --filter='annotations.my_key'

    If the key or value contains special characters, such as `my.key` and `my.value`, backtick("`") is required:

    $ gcloud artifacts files list --filter='annotations.`my.key`'

    $ gcloud artifacts files list \
      --filter='annotations.`my.key`:`my.value`'

To list files with given partial annotation key or value, use * to match
any character:

    $ gcloud artifacts files list --filter='annotations.*key:`*.value`'

To list files in the current project under repository my-repo in us,
ordering by create_time:

    $ gcloud artifacts files list --repository=my-repo --location=us \
      --sort-by=create_time

To list files in the current project under repository my-repo in us,
ordering by update_time reversely:

    $ gcloud artifacts files list --repository=my-repo --location=us \
      --sort-by=~update_time
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/files/list)

---
### `gcloud artifacts files update`

Update annotations on an Artifact Registry file

Update annotations on an Artifact Registry file.

**Synopsis:**
```
gcloud artifacts files update
    (FILE : --location=LOCATION --repository=REPOSITORY)
    [--annotations=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
File resource - The Artifact Registry file to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument file on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FILE
     ID of the file or fully qualified identifier for the file.

     To set the file attribute:
     + provide the argument file on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the file. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the file. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument file on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | List of annotations in the format of KEY=VALUE pairs to add, update, or remove. Duplicate keys will be overwritten. For more details on annotations, see https://google.aip.dev/148#annotations. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --annotations=string=string JSON Example: --annotations='{"string": "string"}' File Example: --annotations=path_to_file.(yaml\|json) |


**Examples:**
```bash
To update annotations on a file named my-file.txt when the project ID,
repository and location defaults are set, run the following command:

CAUTION: This command will overwrite any existing annotations on the file.

    $ gcloud artifacts files update my-file.txt \
      --annotations=key1=value1,key2=value2

To clear all annotations on the file run the following command:

    $ gcloud artifacts files update my-file.txt --annotations={}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/files/update)

---
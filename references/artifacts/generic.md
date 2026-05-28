# gcloud artifacts generic

manage Artifact Registry generic artifacts

### `gcloud artifacts generic download`

Download a generic artifact from a generic artifact repository

Download a generic artifact from a generic artifact repository.

**Synopsis:**
```
gcloud artifacts generic download --destination=DESTINATION
    --package=ARTIFACT --version=VERSION [--chunk-size=CHUNK_SIZE]
    [--name=NAME] [--parallelism=PARALLELISM]
    [--location=LOCATION --repository=REPOSITORY] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | The path where you want to save the downloaded file. |
| `--package` | ARTIFACT |  | The artifact to download. |
| `--version` | VERSION |  | The version of the artifact to download. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--chunk-size` | CHUNK_SIZE |  | If specified, the chunk size (bytes) to use for downloading the package. |
| `--name` | NAME |  | If specified, the file name within the artifact to download. |
| `--parallelism` | PARALLELISM |  | Specifies the number of threads to use for downloading the file in parallel. |


**Examples:**
```bash
To download version v0.1.0 of myfile.txt located in a repository in
"us-central1" to /path/to/destination/:

    $ gcloud artifacts generic download --location=us-central1 \
      --project=myproject --repository=myrepo --package=mypackage \
      --version=v0.1.0 --destination=/path/to/destination/ \
      --name=myfile.txt

To download version v0.1.0 of myfile.txt located in a repository in
"us-central1" to /path/to/destination/ using parallel multipart download
with 4 threads:

    $ gcloud artifacts generic download --location=us-central1 \
      --project=myproject --repository=myrepo --package=mypackage \
      --version=v0.1.0 --destination=/path/to/destination/ \
      --name=myfile.txt --parallelism=4

To download version v0.1.0 of myfile.txt in 8000 byte chunks located in a
repository in "us-central1" to /path/to/destination/:

    $ gcloud artifacts generic download --location=us-central1 \
      --project=myproject --repository=myrepo --package=mypackage \
      --version=v0.1.0 --destination=/path/to/destination/ \
      --name=myfile.txt --chunk-size=8000

To download all files of version v0.1.0 and package mypackage located in a
repository in "us-central1" to /path/to/destination/ while maintaining the
folder hierarchy:

    $ gcloud artifacts generic download --location=us-central1 \
      --project=myproject --repository=myrepo --package=mypackage \
      --version=v0.1.0 --destination=/path/to/destination/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/generic/download)

---
### `gcloud artifacts generic upload`

Uploads an artifact to a generic repository

Uploads an artifact to a generic repository.

**Synopsis:**
```
gcloud artifacts generic upload --package=PACKAGE --version=VERSION
    (--source=SOURCE | --source-directory=SOURCE_DIRECTORY) [--async]
    [--destination-path=DESTINATION_PATH] [--skip-existing]
    [--location=LOCATION --repository=REPOSITORY] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--package` | PACKAGE |  | The package to upload. |
| `--version` | VERSION |  | The version of the package. You cannot overwrite an existing version in the repository. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--destination-path` | DESTINATION_PATH |  | Use to specify the path to upload a generic artifact to within a folder structure. |
| `--skip-existing` |  |  | If specified, skip uploading files that already exist in the repository, and continue to upload the remaining files. |


**Examples:**
```bash
To upload version v0.1.0 of a generic artifact located in /path/to/file/ to
a repository in "us-central1":

    $ gcloud artifacts generic upload --location=us-central1 \
      --project=myproject --repository=myrepo --package=mypackage \
      --version=v0.1.0 --source=/path/to/file/

To upload version v0.1.0 of a generic artifact located in /path/to/file/ to
a repository in "us-central1" within a folder structure:

    $ gcloud artifacts generic upload --location=us-central1 \
      --project=myproject --repository=myrepo --package=mypackage \
      --version=v0.1.0 --source=/path/to/file/ \
      --destination-path=folder/file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/generic/upload)

---
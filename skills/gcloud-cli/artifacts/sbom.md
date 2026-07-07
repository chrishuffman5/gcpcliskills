# gcloud artifacts sbom

manage Artifact SBOMs

### `gcloud artifacts sbom export`

Export SBOM files to Google Cloud Storage

Export SBOM files to Google Cloud Storage.

**Synopsis:**
```
gcloud artifacts sbom export --uri=URI [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--uri` | URI |  | The URI of the Artifact Registry image the SBOM is exported for. A 'gcr.io' image can also be used if redirection is enabled in Artifact Registry. Make sure 'artifactregistry.projectsettings.get' permission is granted to the current gcloud user to verify the redirection status. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | If specified, all requests to Artifact Analysis for occurrences will go to location specified |


**Examples:**
```bash
To export an SBOM file for the Artifact Registry image with URI
"us-west1-docker.pkg.dev/my-project/my-repository/busy-box@sha256:abcxyz":

    $ gcloud artifacts sbom export \
        --uri=us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/sbom/export)

---
### `gcloud artifacts sbom list`

List SBOM file references

List SBOM file references.

**Synopsis:**
```
gcloud artifacts sbom list [--location=LOCATION]
    [--dependency=DEPENDENCY | --resource=RESOURCE
      | --resource-prefix=RESOURCE_PREFIX] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]; default="occ.create_time"]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | If specified, all requests to Artifact Analysis for occurrences will go to location specified |


**Examples:**
```bash
To list SBOM file references:

    $ gcloud artifacts sbom list

To list SBOM file references related to the image with the tag
"us-east1-docker.pkg.dev/project/repo/my-image:1.0":

    $ gcloud artifacts sbom list \
        --resource="us-east1-docker.pkg.dev/project/repo/my-image:1.0"

To list SBOM file references related to the image with the digest
"us-east1-docker.pkg.dev/project/repo/my-image@sha256:88b205d7995332e10e836514fbfd59ecaf8976fc15060cd66e85cdcebe7fb356":

    $ gcloud artifacts sbom list \
        --resource="us-east1-docker.pkg.dev/project/repo/my-image@sha256\
    :88b205d7995332e10e836514fbfd59ecaf8976fc15060cd66e85cdcebe7fb356"

To list SBOM file references related to the images with the resource path
prefix "us-east1-docker.pkg.dev/project/repo":

    $ gcloud artifacts sbom list \
        --resource-prefix="us-east1-docker.pkg.dev/project/repo"

To list SBOM file references generated when the images were pushed to
Artifact Registry and related to the installed package dependency "perl":

    $ gcloud artifacts sbom list --dependency="perl"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/sbom/list)

---
### `gcloud artifacts sbom load`

Upload an SBOM file and create a reference occurrence

Upload an SBOM file and create a reference occurrence.

**Synopsis:**
```
gcloud artifacts sbom load --source=SOURCE --uri=ARTIFACT_URI
    [--destination=DESTINATION] [--kms-key-version=KMS_KEY_VERSION]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | The SBOM file for uploading. |
| `--uri` | ARTIFACT_URI |  | The URI of the artifact the SBOM is generated from. The URI can be a Docker image from any Docker registries. A URI provided with a tag (e.g. [IMAGE]:[TAG]) will be resolved into a URI with a digest ([IMAGE]@sha256:[DIGEST]). When passing an image which is not from Artifact Registry or Container Registry with a tag, only public images can be resolved. Also, when passing an image which is not from Artifact Registry or Container Registry, the --destination flag is required. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | The storage path will be used to store the SBOM file. Currently only supports Cloud Storage paths start with 'gs://'. |
| `--kms-key-version` | KMS_KEY_VERSION |  | Cloud KMS key version to sign the SBOM reference. The key version provided should be the resource ID in the format of projects/[KEY_PROJECT_ID]/locations/[LOCATION]/keyRings/[RING_NAME]/cryptoKeys/[KEY_NAME]/cryptoKeyVersions/[KEY_VERSION]. |
| `--location` | LOCATION |  | If specified, all requests to Artifact Analysis for occurrences will go to location specified |


**Examples:**
```bash
To upload an SBOM file at /path/to/sbom.json for a Docker image in Artifact
Registry:

    $ gcloud artifacts sbom load --source=/path/to/sbom.json \
        --uri=us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz

To upload an SBOM file at /path/to/sbom.json for a Docker image with a KMS
key version to sign the created SBOM reference:

    $ gcloud artifacts sbom load --source=/path/to/sbom.json \
        --uri=us-west1-docker.pkg.dev/my-project/my-repository/\
    busy-box@sha256:abcxyz \
        --kms-key-version=projects/my-project/locations/us-west1/\
    keyRings/my-key-ring/cryptoKeys/my-key/cryptoKeyVersions/1

To upload an SBOM file at /path/to/sbom.json for a Docker image from a
Docker registry:

    $ gcloud artifacts sbom load --source=/path/to/sbom.json \
        --uri=my-docker-registry/my-image@sha256:abcxyz \
        --destination=gs://my-cloud-storage-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/sbom/load)

---
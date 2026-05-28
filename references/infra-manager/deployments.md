# gcloud infra-manager deployments

manage Deployment resources

### `gcloud infra-manager deployments apply`

Create or update a deployment

This command updates a deployment when it already exists, otherwise the
deployment will be created.

**Synopsis:**
```
gcloud infra-manager deployments apply (DEPLOYMENT : --location=LOCATION)
    [--annotations=[KEY=VALUE,...]]
    [--artifacts-gcs-bucket=ARTIFACTS_GCS_BUCKET] [--async]
    [--import-existing-resources] [--labels=[KEY=VALUE,...]]
    [--quota-validation=QUOTA_VALIDATION]
    [--service-account=SERVICE_ACCOUNT]
    [--tf-version-constraint=TF_VERSION_CONSTRAINT]
    [--worker-pool=WORKER_POOL]
    [--gcs-source=GCS_SOURCE | --git-source-directory=GIT_SOURCE_DIRECTORY
      --git-source-ref=GIT_SOURCE_REF --git-source-repo=GIT_SOURCE_REPO
      | --ignore-file=IGNORE_FILE
      --local-source=LOCAL_SOURCE --input-values=[KEY=VALUE,...]
      | --inputs-file=INPUTS_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - the deployment to create or update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument DEPLOYMENT on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the deployment.

     To set the location attribute:
     + provide the argument DEPLOYMENT on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations to apply to the deployment. Existing values are overwritten. To retain the existing annotations on a deployment, do not specify this flag. Examples: Update annotations for an existing deployment: $ gcloud infra-manager deployments apply \ projects/p1/locations/us-central1/deployments/my-deployment \ --gcs-source="gs://my-bucket" \ --annotations="env=prod,team=finance" Clear annotations for an existing deployment: $ gcloud infra-manager deployments apply \ projects/p1/locations/us-central1/deployments/my-deployment \ --gcs-source="gs://my-bucket" --annotations="" Add an annotation to an existing deployment: First, fetch the current annotations using the `describe` command, then follow the preceding example for updating annotations. |
| `--artifacts-gcs-bucket` | ARTIFACTS_GCS_BUCKET |  | user-defined location of Cloud Build logs, artifacts, and Terraform state files in Google Cloud Storage. Format: gs://{bucket}/{folder} A default bucket will be bootstrapped if the field is not set or empty |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--import-existing-resources` |  |  | By default, Infrastructure Manager will return a failure when Terraform encounters a 409 code (resource conflict error) during actuation. If this flag is set to true, Infrastructure Manager will instead attempt to automatically import the resource into the Terraform state (for supported resource types) and continue actuation. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the deployment. Existing values are overwritten. To retain the existing labels on a deployment, do not specify this flag. Examples: Update labels for an existing deployment: $ gcloud infra-manager deployments apply \ projects/p1/locations/us-central1/deployments/my-deployment \ --gcs-source="gs://my-bucket" --labels="env=prod,team=finance" Clear labels for an existing deployment: $ gcloud infra-manager deployments apply \ projects/p1/locations/us-central1/deployments/my-deployment \ --gcs-source="gs://my-bucket" --labels="" Add a label to an existing deployment: First, fetch the current labels using the `describe` command, then follow the preceding example for updating labels. |
| `--quota-validation` | QUOTA_VALIDATION |  | Input to control quota checks for resources in terraform configuration files. There are limited resources on which quota validation applies. Supported values are QUOTA_VALIDATION_UNSPECIFIED, ENABLED, ENFORCED |
| `--service-account` | SERVICE_ACCOUNT |  | User-specified Service Account (SA) to be used as credential to manage resources. Format: projects/{projectID}/serviceAccounts/{serviceAccount} |
| `--tf-version-constraint` | TF_VERSION_CONSTRAINT |  | User-specified Terraform version constraint, for example "=1.3.10". |
| `--worker-pool` | WORKER_POOL |  | User-specified Worker Pool resource in which the Cloud Build job will execute. Format: projects/{project}/locations/{location}/workerPools/{workerPoolId} |


**Examples:**
```bash
Create a deployment named my-deployment from a storage my-bucket:

    $ gcloud infra-manager deployments apply \
        projects/p1/locations/us-central1/deployments/my-deployment \
        --gcs-source="gs://my-bucket" \
        --input-values="project=p1,region=us-central1"

Create a deployment named my-deployment from git repo
"https://github.com/examples/repository.git", "staging/compute" folder,
"mainline" branch:

    $ gcloud infra-manager deployments apply \
        projects/p1/locations/us-central1/deployments/my-deployment \
        --git-source-repo="https://github.com/examples/repository.git" \
        --git-source-directory="staging/compute" \
        --git-source-ref="mainline"

Update a deployment's labels:

    $ gcloud infra-manager deployments apply \
        projects/p1/locations/us-central1/deployments/my-deployment \
        --git-source-repo="https://github.com/examples/repository.git" \
        --git-source-directory="staging/compute" \
        --git-source-ref="mainline" --labels="env=prod,team=finance"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/apply)

---
### `gcloud infra-manager deployments delete`

Delete deployments

Delete a deployment

**Synopsis:**
```
gcloud infra-manager deployments delete (DEPLOYMENT : --location=LOCATION)
    [--async] [--delete-policy=DELETE_POLICY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - deployments TBD The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument deployment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--delete-policy` | one of: abandon, delete, delete-policy-unspecified |  | Policy on how resources actuated by the deployment should be deleted. The accepted values are DELETE, ABANDON. DELETE = Delete resources actuated by the deployment. ABANDON = Abandon resources and only delete deployment metadata. DELETE_POLICY must be one of: abandon, delete, delete-policy-unspecified. |


**Examples:**
```bash
To delete the deployment example-deployment at location us-central1, run:

    $ gcloud infra-manager deployments delete \
        projects/example-project/locations/us-central1/deployments/\
    example-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/delete)

---
### `gcloud infra-manager deployments describe`

Describe deployments

Describe a deployment

**Synopsis:**
```
gcloud infra-manager deployments describe
    (DEPLOYMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - The deployment to describe The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument deployment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument deployment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument deployment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Examples:**
```bash
To describe a deployment example-deployment in project p1 at location
us-central1, run:

    $ gcloud infra-manager deployments describe \
        projects/p1/locations/us-central1/deployments/example-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/describe)

---
### `gcloud infra-manager deployments export-lock`

Exports lock info of a deployment

This command exports lock info of a deployment.

**Synopsis:**
```
gcloud infra-manager deployments export-lock
    (DEPLOYMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - the deployment to be used as parent. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument DEPLOYMENT on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the deployment.

     To set the location attribute:
     + provide the argument DEPLOYMENT on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Examples:**
```bash
Export lock info for deployment
projects/p1/locations/us-central1/deployments/my-deployment:

    $ gcloud infra-manager deployments export-lock \
        projects/p1/locations/us-central1/deployments/my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/export-lock)

---
### `gcloud infra-manager deployments export-statefile`

Export a terraform state file

This command generates a signed url to download a terraform state file.

**Synopsis:**
```
gcloud infra-manager deployments export-statefile
    (DEPLOYMENT : --location=LOCATION) [--draft] [--file=FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - the deployment to be used as parent. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument DEPLOYMENT on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the deployment.

     To set the location attribute:
     + provide the argument DEPLOYMENT on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--draft` |  |  | If this flag is set to true, the exported deployment state file will be the draft state |
| `--file` | FILE |  | File name for statefile. It is optional and it specifies the filename or complete path for the downloaded statefile. If only a file path is provided, the statefile will be downloaded as "statefile" within that directory. If a filename is included, the statefile will be downloaded with that name. |


**Examples:**
```bash
Export state file for my-deployment:

    $ gcloud infra-manager deployments export-statefile \
        projects/p1/locations/us-central1/deployments/my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/export-statefile)

---
### `gcloud infra-manager deployments import-statefile`

Import a terraform state file

This command generates a signed url to upload a terraform state file.

**Synopsis:**
```
gcloud infra-manager deployments import-statefile
    (DEPLOYMENT : --location=LOCATION) --lock-id=LOCK_ID [--file=FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - the deployment to be used as parent. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument DEPLOYMENT on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the deployment.

     To set the location attribute:
     + provide the argument DEPLOYMENT on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lock-id` | LOCK_ID |  | Lock ID of the lock file to verify person importing owns lock. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | File path for importing statefile into a deployment. It specifies the local file path of an existing Terraform statefile to directly upload for a deployment. |


**Examples:**
```bash
Import state file for my-deployment with lock-id 1658343229583347:

    $ gcloud infra-manager deployments import-statefile \
        projects/p1/locations/us-central1/deployments/my-deployment \
        --lock-id=1658343229583347
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/import-statefile)

---
### `gcloud infra-manager deployments list`

List deployments

**Synopsis:**
```
gcloud infra-manager deployments list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To list all deployments at location us-central1, run:

    $ gcloud infra-manager deployments list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/list)

---
### `gcloud infra-manager deployments lock`

Locks the deployment

This command locks the deployment and generates a lockId.

**Synopsis:**
```
gcloud infra-manager deployments lock (DEPLOYMENT : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - the deployment to be used as parent. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument DEPLOYMENT on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the deployment.

     To set the location attribute:
     + provide the argument DEPLOYMENT on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
Lock deployment my-deployment under project p1 and location us-central1:

    $ gcloud infra-manager deployments lock \
        projects/p1/locations/us-central1/deployments/my-deployment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/lock)

---
### `gcloud infra-manager deployments unlock`

Unlocks the deployment

This command releases the lock on deployment.

**Synopsis:**
```
gcloud infra-manager deployments unlock (DEPLOYMENT : --location=LOCATION)
    --lock-id=LOCK_ID [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deployment resource - the deployment to be used as parent. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument DEPLOYMENT on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOYMENT
     ID of the deployment or fully qualified identifier for the
     deployment.

     To set the deployment attribute:
     + provide the argument DEPLOYMENT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the deployment.

     To set the location attribute:
     + provide the argument DEPLOYMENT on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lock-id` | LOCK_ID |  | Lock ID of the lock file to verify person importing owns lock. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
Unlock deployment my-deployment under project p1 and location us-central1
with lock-id 1234:

    $ gcloud infra-manager deployments unlock \
        projects/p1/locations/us-central1/deployments/my-deployment \
        --lock-id=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/deployments/unlock)

---
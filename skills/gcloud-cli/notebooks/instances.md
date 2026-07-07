# gcloud notebooks instances

notebooks Instances command group

### `gcloud notebooks instances add-iam-policy-binding`

Add IAM policy binding for an instance

Adds a policy binding to the IAM policy of an instance, given an instance
ID and the binding.

**Synopsis:**
```
gcloud notebooks instances add-iam-policy-binding
    (INSTANCE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The ID of the instance to add the IAM binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the notebook instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/notebooks.admin for the
user 'test-user@gmail.com' on the instance 'instance-id', run:

    $ gcloud notebooks instances add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/notebooks.admin' example-instance \
        --location=us-central1-a

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/add-iam-policy-binding)

---
### `gcloud notebooks instances create`

Request for creating an instance

Request for creating notebook instances.

**Synopsis:**
```
gcloud notebooks instances create (INSTANCE : --location=LOCATION)
    [--async] [--instance-owners=INSTANCE_OWNERS]
    [--labels=[KEY=VALUE,...]]
    [--machine-type=MACHINE_TYPE; default="n1-standard-1"]
    [--metadata=[KEY=VALUE,...]]
    [--post-startup-script=POST_STARTUP_SCRIPT]
    [--service-account=SERVICE_ACCOUNT]
    [--no-shielded-integrity-monitoring] [--shielded-secure-boot]
    [--no-shielded-vtpm] [--tags=[TAGS,...]]
    [--accelerator-core-count=ACCELERATOR_CORE_COUNT
      --accelerator-type=ACCELERATOR_TYPE]
    [--boot-disk-size=BOOT_DISK_SIZE --boot-disk-type=BOOT_DISK_TYPE]
    [[--container-repository=CONTAINER_REPOSITORY
      : --container-tag=CONTAINER_TAG] | [--environment=ENVIRONMENT
      : --environment-location=ENVIRONMENT_LOCATION]
      | --vm-image-project=VM_IMAGE_PROJECT;
      default="deeplearning-platform-release"
      --vm-image-family=VM_IMAGE_FAMILY; default="common-cpu"
      | --vm-image-name=VM_IMAGE_NAME]
    [--custom-gpu-driver-path=CUSTOM_GPU_DRIVER_PATH --install-gpu-driver]
    [--data-disk-size=DATA_DISK_SIZE
      --data-disk-type=DATA_DISK_TYPE --no-remove-data-disk]
    [--disk-encryption=DISK_ENCRYPTION [--kms-key=KMS_KEY
      : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]]
    [--network=NETWORK --no-proxy-access --no-public-ip [--subnet=SUBNET
      : --subnet-region=SUBNET_REGION]]
    [--reservation=RESERVATION --reservation-affinity=RESERVATION_AFFINITY;
      default="TYPE_UNSPECIFIED"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--instance-owners` | INSTANCE_OWNERS |  | The owners of this instance after creation. Format:alias@example.com. Currently supports one owner only.If not specified, all of the service account users of the VM instance's service account can use the instance. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to this instance. These can be later modified by the setLabels method. |
| `--machine-type` | MACHINE_TYPE | n1-standard-1 | The Compute Engine machine type (https://cloud.google.com/sdk/gcloud/reference/compute/machine-types) of this instance. |
| `--metadata` | [KEY=VALUE,...] |  | Custom metadata to apply to this instance. For example, to specify a Cloud Storage bucket for automatic backup, you can use the gcs-data-bucket metadata tag. Format: "--metadata=gcs-data-bucket=BUCKET". |
| `--post-startup-script` | POST_STARTUP_SCRIPT |  | Path to a Bash script that automatically runs after a notebook instance fully boots up. The path must be a URL or Cloud Storage path (gs://path-to-file/file-name). |
| `--service-account` | SERVICE_ACCOUNT |  | The service account on this instance, giving access to other Google Cloud services. You can use any service account within the same project, but you must have the service account user permission to use the instance. If not specified, the Compute Engine default service account is used. |
| `--shielded-integrity-monitoring` |  |  | Enable monitoring of the boot integrity of the instance. Enabled by default, use --no-shielded-integrity-monitoring to disable. |
| `--shielded-secure-boot` |  |  | Boot instance with secure boot enabled. Disabled by default. |
| `--shielded-vtpm` |  |  | Boot instance with TPM (Trusted Platform Module) enabled. Enabled by default, use --no-shielded-vtpm to disable. |
| `--tags` | [TAGS,...] |  | Tags to apply to this instance. |


**Examples:**
```bash
To create an instance from an environment, run:

    $ gcloud notebooks instances create example-instance \
        --environment=example-env --environment-location=us-central1-a \
        --machine-type=n1-standard-4 --location=us-central1-b

To create an instance from a VmImage family, run:

    $ gcloud notebooks instances create example-instance \
        --vm-image-project=deeplearning-platform-release \
        --vm-image-family=caffe1-latest-cpu-experimental \
        --machine-type=n1-standard-4 --location=us-central1-b

To create an instance from a VmImage name, run:

    $ gcloud notebooks instances create example-instance \
        --vm-image-project=deeplearning-platform-release \
        --vm-image-name=tf2-2-1-cu101-notebooks-20200110 \
        --machine-type=n1-standard-4 --location=us-central1-b

To create an instance from a Container Repository, run:

    $ gcloud notebooks instances create example-instance \
        --container-repository=gcr.io/deeplearning-platform-release/\
    base-cpu --container-tag=test-tag --machine-type=n1-standard-4 \
        --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/create)

---
### `gcloud notebooks instances delete`

Request for deleting instances

Request for deleting notebook instances.

**Synopsis:**
```
gcloud notebooks instances delete (INSTANCE : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an instance, run:

    $ gcloud notebooks instances delete example-instance \
      --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/delete)

---
### `gcloud notebooks instances describe`

Request for describing instances

Request for describing notebook instances.

**Synopsis:**
```
gcloud notebooks instances describe (INSTANCE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To describe an instance, run:

    $ gcloud notebooks instances describe example-instance \
      --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/describe)

---
### `gcloud notebooks instances diagnose`

Request for diagnose instances

Request for diagnose notebook instances.

**Synopsis:**
```
gcloud notebooks instances diagnose (INSTANCE : --location=LOCATION)
    --gcs-bucket=GCS_BUCKET [--async] [--enable-copy-home-files]
    [--enable-packet-capture] [--enable-repair]
    [--relative-path=RELATIVE_PATH] [--timeout-minutes=TIMEOUT_MINUTES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-bucket` | GCS_BUCKET |  | The Cloud Storage bucket where the log files generated from the diagnose command will be stored. storage.buckets.writer permissions must be given to project's service account or user credential. Format: gs://{gcs_bucket} |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-copy-home-files` |  |  | Enables flag to copy all /home/jupyter folder contents |
| `--enable-packet-capture` |  |  | Enables flag to capture packets from the instance for 30 seconds |
| `--enable-repair` |  |  | Enables flag to repair service for instance |
| `--relative-path` | RELATIVE_PATH |  | Defines the relative storage path in the Cloud Storage bucket where the diagnostic logs will be written. Default path will be the root directory of the Cloud Storage bucketFormat of full path: gs://{gcs_bucket}/{relative_path}/ |
| `--timeout-minutes` | TIMEOUT_MINUTES |  | Maximum amount of time in minutes before the operation times out |


**Examples:**
```bash
To diagnose an instance, run:

    $ gcloud notebooks instances diagnose example-instance \
      --location=us-west1-b --gcs-bucket=gs://example-bucket

To diagnose an instance with a relative path:

    $ gcloud notebooks instances diagnose example-instance \
      --location=us-west1-b --gcs-bucket=gs://example-bucket \
      --relative-path=logs

To diagnose an instance, with packet capture:

    $ gcloud notebooks instances diagnose example-instance \
      --location=us-west1-b --gcs-bucket=gs://example-bucket \
      --enable-packet-capture
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/diagnose)

---
### `gcloud notebooks instances get-health`

Request for checking if a notebook instance is healthy

Request for checking if a notebook instance is healthy.

**Synopsis:**
```
gcloud notebooks instances get-health (INSTANCE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To check if an instance is healthy, run:

    $ gcloud notebooks instances get-health example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/get-health)

---
### `gcloud notebooks instances get-iam-policy`

Get IAM policy for an instance

gcloud notebooks instances get-iam-policy displays the IAM policy
associated with an instance. If formatted as JSON, the output can be edited
and used as a policy file for set-iam-policy. The output includes an "etag"
field identifying the version emitted and allowing detection of concurrent
policy updates; see $ {parent} set-iam-policy for additional details.

**Synopsis:**
```
gcloud notebooks instances get-iam-policy (INSTANCE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The ID of the instance for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the notebook instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To print the IAM policy for a given folder, run:

    $ gcloud notebooks instances get-iam-policy my-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/get-iam-policy)

---
### `gcloud notebooks instances is-upgradeable`

Request for checking if a notebook instance is upgradeable

Request for checking if a notebook instance is upgradeable.

**Synopsis:**
```
gcloud notebooks instances is-upgradeable (INSTANCE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To check if an instance can be upgraded, run:

    $ gcloud notebooks instances is-upgradeable example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/is-upgradeable)

---
### `gcloud notebooks instances list`

Request for listing instances

Request for listing instances.

**Synopsis:**
```
gcloud notebooks instances list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud location of this environment https://cloud.google.com/compute/docs/regions-zones/#locations. |


**Examples:**
```bash
To list instances in a particular location, run:

    $ gcloud notebooks instances list --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/list)

---
### `gcloud notebooks instances migrate`

Request for migrating instances

Request for migrating notebook instances.

**Synopsis:**
```
gcloud notebooks instances migrate (INSTANCE : --location=LOCATION)
    [--async]
    [--post-startup-script-option=POST_STARTUP_SCRIPT_OPTION;
      default="POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--post-startup-script-option` | one of: POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED, POST_STARTUP_SCRIPT_OPTION_SKIP, POST_STARTUP_SCRIPT_OPTION_RERUN | POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED | // Specifies the behavior of post startup script during migration. POST_STARTUP_SCRIPT_OPTION must be one of: POST_STARTUP_SCRIPT_OPTION_UNSPECIFIED, POST_STARTUP_SCRIPT_OPTION_SKIP, POST_STARTUP_SCRIPT_OPTION_RERUN. |


**Examples:**
```bash
To migrate an instance, run:

    $ gcloud notebooks instances migrate example-instance \
      --location=us-central1

To migrate an instance and reuse the post-startup script, run:

    $ gcloud notebooks instances migrate example-instance \
      --location=us-central1 \
      --post-startup-script-option=POST_STARTUP_SCRIPT_OPTION_RERUN
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/migrate)

---
### `gcloud notebooks instances register`

Request for registering instances

Request for registering notebook instances.

**Synopsis:**
```
gcloud notebooks instances register (INSTANCE : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To register an old type instance, run:

    $ gcloud notebooks instances register example-instance \
      --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/register)

---
### `gcloud notebooks instances remove-iam-policy-binding`

Remove IAM policy binding for an instance

Removes a policy binding to the IAM policy of an instance, given an
instance ID and the binding.

**Synopsis:**
```
gcloud notebooks instances remove-iam-policy-binding
    (INSTANCE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The ID of the instance to remove the IAM binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the notebook instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of roles/editor for the user
'test-user@gmail.com' on the instance 'instance-id', run:

    $ gcloud notebooks instances remove-iam-policy-binding \
        example-instance --member='user:test-user@gmail.com' \
        --role='roles/editor' --location=us-central1-a

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/remove-iam-policy-binding)

---
### `gcloud notebooks instances reset`

Request for resetting instances

Request for reseting notebook instances.

**Synopsis:**
```
gcloud notebooks instances reset (INSTANCE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To reset an instance, run:

    $ gcloud notebooks instances reset example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/reset)

---
### `gcloud notebooks instances rollback`

Request for rolling back instances

Request for rolling back notebook instances.

**Synopsis:**
```
gcloud notebooks instances rollback (INSTANCE : --location=LOCATION)
    --target-snapshot=TARGET_SNAPSHOT [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-snapshot` | TARGET_SNAPSHOT |  | The saved snapshot to rollback to |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To rollback an instance, run:

    $ gcloud notebooks instances rollback example-instance \
      target-snapshot=projects/example-project/global/snapshots/\
    aorlbjvpavvf --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/rollback)

---
### `gcloud notebooks instances set-iam-policy`

Set the IAM policy for an Instance

gcloud notebooks instances set-iam-policy sets the IAM policy for a
Notebook instance given an instance ID and a JSON or YAML file that
describes the IAM policy.

Note: Setting the IAM policy for an Instance replaces existing IAM bindings
for that account.

**Synopsis:**
```
gcloud notebooks instances set-iam-policy (INSTANCE : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The ID of the instance for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the notebook instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in the JSON file
policy.json and sets it for Instance ID my_instance at the specified
locaiton:

    $ gcloud notebooks instances set-iam-policy my_instance \
        --location=us-central1-a policy.json

See https://cloud.google.com/iam/docs/managing-policies for policy file
format and content details.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/set-iam-policy)

---
### `gcloud notebooks instances start`

Request for starting instances

Request for starting notebook instances.

**Synopsis:**
```
gcloud notebooks instances start (INSTANCE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start an instance, run:

    $ gcloud notebooks instances start example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/start)

---
### `gcloud notebooks instances stop`

Request for stopping instances

Request for stopping notebook instances.

**Synopsis:**
```
gcloud notebooks instances stop (INSTANCE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop an instance, run:

    $ gcloud notebooks instances stop example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/stop)

---
### `gcloud notebooks instances update`

Request for updating instances

Request for updating notebook instances.

**Synopsis:**
```
gcloud notebooks instances update (INSTANCE : --location=LOCATION)
    (--accelerator-core-count=ACCELERATOR_CORE_COUNT
      --accelerator-type=ACCELERATOR_TYPE
      --labels=[KEY=VALUE,...] --machine-type=MACHINE_TYPE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator-core-count` | ACCELERATOR_CORE_COUNT |  | _[At least one of these must be specified:]_ Count of cores of this accelerator. |
| `--accelerator-type` | one of: NVIDIA_TESLA_A100, NVIDIA_TESLA_K80, NVIDIA_TESLA_P100, NVIDIA_TESLA_V100, NVIDIA_TESLA_P4, NVIDIA_TESLA_T4, NVIDIA_TESLA_T4_VWS, NVIDIA_TESLA_P100_VWS, NVIDIA_TESLA_P4_VWS, TPU_V2, TPU_V3, NVIDIA_L4, NVIDIA_H100_80GB, NVIDIA_H100_MEGA_80GB |  | _[At least one of these must be specified:]_ Type of this accelerator. ACCELERATOR_TYPE must be one of: NVIDIA_TESLA_A100, NVIDIA_TESLA_K80, NVIDIA_TESLA_P100, NVIDIA_TESLA_V100, NVIDIA_TESLA_P4, NVIDIA_TESLA_T4, NVIDIA_TESLA_T4_VWS, NVIDIA_TESLA_P100_VWS, NVIDIA_TESLA_P4_VWS, TPU_V2, TPU_V3, NVIDIA_L4, NVIDIA_H100_80GB, NVIDIA_H100_MEGA_80GB. |
| `--labels` | [KEY=VALUE,...] |  | _[At least one of these must be specified:]_ Labels to apply to this instance. These can be later modified by the setLabels method. |
| `--machine-type` | MACHINE_TYPE |  | _[At least one of these must be specified:]_ The Compute Engine machine type. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update machine type for an instance, run:

    $ gcloud notebooks instances update example-instance \
      --machine-type=n1-standard-8 --location=us-central1-a

To update labels for an instance, run:

    $ gcloud notebooks instances update example-instance \
      --labels=k1=v1,k2=v2 --location=us-central1-a

To update labels and accelerator cores, run:

    $ gcloud notebooks instances update example-instance \
      --labels=k1=v1,k2=v2 --accelerator-core-count=2 \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/update)

---
### `gcloud notebooks instances upgrade`

Request for upgrading instances

Request for upgrading notebook instances.

**Synopsis:**
```
gcloud notebooks instances upgrade (INSTANCE : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - User-defined unique name of this instance. The
instance name must be 1 to 63 characters long and contain only lowercase
letters, numeric characters, and dashes. The first character must be a
lowercase letter and the last character cannot be a dash. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location of this environment
     https://cloud.google.com/compute/docs/regions-zones/#locations.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upgrade an instance, run:

    $ gcloud notebooks instances upgrade example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/notebooks/instances/upgrade)

---
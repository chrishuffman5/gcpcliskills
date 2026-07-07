# gcloud workbench instances

workbench Instances command group

### `gcloud workbench instances add-iam-policy-binding`

Adds IAM policy binding for a workbench instance

Adds a policy binding to the IAM policy of an instance, given an instance
ID and the binding.

**Synopsis:**
```
gcloud workbench instances add-iam-policy-binding
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
     The location of the workbench instance.

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

    $ gcloud workbench instances add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/notebooks.admin' example-instance \
        --location=us-central1-a

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/add-iam-policy-binding)

---
### `gcloud workbench instances check-instance-upgradability`

Checks if a workbench instance is upgradeable

Checks if a workbench instance is upgradeable.

**Synopsis:**
```
gcloud workbench instances check-instance-upgradability
    (INSTANCE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
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

    $ gcloud workbench instances check-instance-upgradability \
      example-instance --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/check-instance-upgradability)

---
### `gcloud workbench instances create`

Creates a workbench instance

Creates a workbench instance.

**Synopsis:**
```
gcloud workbench instances create (INSTANCE : --location=LOCATION)
    [--async] [--disable-proxy-access] [--enable-managed-euc]
    [--enable-third-party-identity] [--instance-owners=INSTANCE_OWNERS]
    [--labels=[KEY=VALUE,...]]
    [--confidential-compute-type=CONFIDENTIAL_COMPUTE_TYPE
      --disable-public-ip --enable-ip-forwarding
      --machine-type=MACHINE_TYPE; default="n1-standard-4"
      --metadata=[KEY=VALUE,...] --min-cpu-platform=MIN_CPU_PLATFORM
      --service-account-email=SERVICE_ACCOUNT_EMAIL --tags=[TAGS,...]
      --accelerator-core-count=ACCELERATOR_CORE_COUNT
      --accelerator-type=ACCELERATOR_TYPE
      --boot-disk-encryption=BOOT_DISK_ENCRYPTION
      --boot-disk-size=BOOT_DISK_SIZE --boot-disk-type=BOOT_DISK_TYPE
      [--boot-disk-kms-key=BOOT_DISK_KMS_KEY
      : --boot-disk-encryption-key-keyring=BOOT_DISK_ENCRYPTION_KEY_KEYRING
      --boot-disk-encryption-key-location=BOOT_DISK_ENCRYPTION_KEY_LOCATION
      --boot-disk-encryption-key-project=BOOT_DISK_ENCRYPTION_KEY_PROJECT]
      [--container-repository=CONTAINER_REPOSITORY
      : --container-tag=CONTAINER_TAG]
      | [(--vm-image-family=VM_IMAGE_FAMILY
      | --vm-image-name=VM_IMAGE_NAME)
      : --vm-image-project=VM_IMAGE_PROJECT;
      default="cloud-notebooks-managed"]
      --custom-gpu-driver-path=CUSTOM_GPU_DRIVER_PATH --install-gpu-driver
      --data-disk-encryption=DATA_DISK_ENCRYPTION
      --data-disk-resource-policies=[RESOURCE_POLICIES,...]
      --data-disk-size=DATA_DISK_SIZE --data-disk-type=DATA_DISK_TYPE
      [--data-disk-kms-key=DATA_DISK_KMS_KEY
      : --data-disk-encryption-key-keyring=DATA_DISK_ENCRYPTION_KEY_KEYRING
      --data-disk-encryption-key-location=DATA_DISK_ENCRYPTION_KEY_LOCATION
      --data-disk-encryption-key-project=DATA_DISK_ENCRYPTION_KEY_PROJECT]
      --network=NETWORK --nic-type=NIC_TYPE [--subnet=SUBNET
      : --subnet-region=SUBNET_REGION] --reservation-key=RESERVATION_KEY
      --reservation-type=RESERVATION_TYPE; default="any"
      --reservation-values=[VALUES,...]
      --shielded-integrity-monitoring=SHIELDED_INTEGRITY_MONITORING
      --shielded-secure-boot=SHIELDED_SECURE_BOOT
      --shielded-vtpm=SHIELDED_VTPM] [GCLOUD_WIDE_FLAG ...]
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
| `--disable-proxy-access` |  |  | If true, the notebook instance will not register with the proxy. |
| `--enable-managed-euc` |  |  | If true, the notebook instance will be created with managed end user credentials enabled. |
| `--enable-third-party-identity` |  |  | If true, the notebook instance provide a proxy endpoint which allows for third party identity. |
| `--instance-owners` | INSTANCE_OWNERS |  | The owners of this instance after creation. Format: alias@example.com. Currently supports one owner only. If not specified, all of the service account users of the VM instance's service account can use the instance. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to this instance. These can be later modified by the setLabels method. |


**Examples:**
```bash
To create an instance from a VmImage family, run:

    $ gcloud workbench instances create example-instance \
        --vm-image-project=cloud-notebooks-managed \
        --vm-image-family=workbench-instances \
        --machine-type=n1-standard-4 --location=us-central1-b

To create an instance from a VmImage name, run:

    $ gcloud workbench instances create example-instance \
        --vm-image-project=cloud-notebooks-managed \
        --vm-image-name=workbench-instances-v20230925-debian-11-py310 \
        --machine-type=n1-standard-4 --location=us-central1-b

To create an instance from a Container Repository, run:

    $ gcloud workbench instances create example-instance \
        --container-repository=gcr.io/deeplearning-platform-release/\
    base-cpu --container-tag=latest --machine-type=n1-standard-4 \
        --location=us-central1-b

To create an instance with shielded-secure-boot, shielded-vtpm and
shielded-integrity-monitoring disabled, run:

    $ gcloud workbench instances create example-instance \
        --shielded-integrity-monitoring=false \
        --shielded-secure-boot=false --shielded-vtpm=false \
        --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/create)

---
### `gcloud workbench instances delete`

Deletes a workbench instance

Deletes a workbench instance.

**Synopsis:**
```
gcloud workbench instances delete (INSTANCE : --location=LOCATION)
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

    $ gcloud workbench instances delete example-instance \
      --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/delete)

---
### `gcloud workbench instances describe`

Describes a workbench instance

Describes a workbench instance.

**Synopsis:**
```
gcloud workbench instances describe (INSTANCE : --location=LOCATION)
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

    $ gcloud workbench instances describe example-instance \
      --location=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/describe)

---
### `gcloud workbench instances diagnose`

Diagnoses a workbench instance

Diagnoses a workbench instance.

**Synopsis:**
```
gcloud workbench instances diagnose (INSTANCE : --location=LOCATION)
    --gcs-bucket=GCS_BUCKET [--async] [--enable-copy-home-files]
    [--enable-packet-capture] [--enable-repair]
    [--relative-path=RELATIVE_PATH] [GCLOUD_WIDE_FLAG ...]
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


**Examples:**
```bash
To diagnose an instance, run:

    $ gcloud workbench instances diagnose example-instance \
      --location=us-west1-b --gcs-bucket=gs://example-bucket

To diagnose an instance with a relative path:

    $ gcloud workbench instances diagnose example-instance \
      --location=us-west1-b --gcs-bucket=gs://example-bucket \
      --relative-path=logs

To diagnose an instance, with packet capture:

    $ gcloud workbench instances diagnose example-instance \
      --location=us-west1-b --gcs-bucket=gs://example-bucket \
      --enable-packet-capture
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/diagnose)

---
### `gcloud workbench instances get-config`

Describes the valid configurations for workbench instances

Describes the valid configurations for workbench instances.

**Synopsis:**
```
gcloud workbench instances get-config [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud location of this environment https://cloud.google.com/compute/docs/regions-zones/#locations. |


**Examples:**
```bash
For valid configurations, run:

    $ gcloud workbench instances get-config --location=us-west1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/get-config)

---
### `gcloud workbench instances get-iam-policy`

Gets IAM policy for a workbench instance

gcloud workbench instances get-iam-policy displays the IAM policy
associated with an instance. If formatted as JSON, the output can be edited
and used as a policy file for set-iam-policy. The output includes an "etag"
field identifying the version emitted and allowing detection of concurrent
policy updates; see $ {parent} set-iam-policy for additional details.

**Synopsis:**
```
gcloud workbench instances get-iam-policy (INSTANCE : --location=LOCATION)
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
     The location of the workbench instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property notebooks/location.
```

**Examples:**
```bash
To print the IAM policy for a given instance, run:

    $ gcloud workbench instances get-iam-policy my-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/get-iam-policy)

---
### `gcloud workbench instances list`

Lists workbench instances

Lists workbench instances.

**Synopsis:**
```
gcloud workbench instances list [--location=LOCATION] [--filter=EXPRESSION]
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

    $ gcloud workbench instances list --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/list)

---
### `gcloud workbench instances remove-iam-policy-binding`

Removes IAM policy binding for a workbench instance

Removes a policy binding to the IAM policy of an instance, given an
instance ID and the binding.

**Synopsis:**
```
gcloud workbench instances remove-iam-policy-binding
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
     The location of the workbench instance.

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

    $ gcloud workbench instances remove-iam-policy-binding \
        example-instance --member='user:test-user@gmail.com' \
        --role='roles/editor' --location=us-central1-a

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/remove-iam-policy-binding)

---
### `gcloud workbench instances reset`

Resets a workbench instance

Resets a workbench instance.

**Synopsis:**
```
gcloud workbench instances reset (INSTANCE : --location=LOCATION) [--async]
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

    $ gcloud workbench instances reset example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/reset)

---
### `gcloud workbench instances resize-disk`

Resizes the workbench instance's disk

Resizes the workbench instance's disk.

**Synopsis:**
```
gcloud workbench instances resize-disk (INSTANCE : --location=LOCATION)
    (--boot-disk-size=BOOT_DISK_SIZE | --data-disk-size=DATA_DISK_SIZE)
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

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--boot-disk-size` | BOOT_DISK_SIZE |  | _[Exactly one of these must be specified:]_ Size of boot disk in GB attached to this instance, up to a maximum of 64000 GB (64 TB). |
| `--data-disk-size` | DATA_DISK_SIZE |  | _[Exactly one of these must be specified:]_ Size of data disk in GB attached to this instance, up to a maximum of 64000 GB (64 TB). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To increase the boot disk size for an instance, run:

    $ gcloud workbench instances resize-disk example-instance \
      --boot-disk-size=200 --location=us-central1-a

To increase the data disk size for an instance, run:

    $ gcloud workbench instances resize-disk example-instance \
      --data-disk-size=200 --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/resize-disk)

---
### `gcloud workbench instances restore`

Restores the workbench instance to a snapshot state

Restores the workbench instance to a snapshot state.

**Synopsis:**
```
gcloud workbench instances restore (INSTANCE : --location=LOCATION)
    (--snapshot=SNAPSHOT --snapshot-project=SNAPSHOT_PROJECT) [--async]
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
| `--snapshot` | SNAPSHOT |  | _[This must be specified.]_ The snapshot name to be restored from. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--snapshot-project` | SNAPSHOT_PROJECT |  | _[This must be specified.]_ The project id of the snapshot to be restored from. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
For valid configurations, run:

    $ gcloud workbench instances restore example-instance \
      --snapshot-project=example-project --snapshot=example-snapshot \
      --location=us-west1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/restore)

---
### `gcloud workbench instances rollback`

Rolls back a workbench instance

Rolls back a workbench instance.

**Synopsis:**
```
gcloud workbench instances rollback (INSTANCE : --location=LOCATION)
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
| `--target-snapshot` | TARGET_SNAPSHOT |  | The saved snapshot to rollback to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To rollback an instance, run:

    $ gcloud workbench instances rollback example-instance \
      target-snapshot=projects/example-project/global/snapshots/\
    aorlbjvpavvf --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/rollback)

---
### `gcloud workbench instances set-iam-policy`

Sets the IAM policy for a workbench instance

gcloud workbench instances set-iam-policy sets the IAM policy for a
Notebook instance given an instance ID and a JSON or YAML file that
describes the IAM policy.

Note: Setting the IAM policy for an Instance replaces existing IAM bindings
for that account.

**Synopsis:**
```
gcloud workbench instances set-iam-policy (INSTANCE : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The ID of the instance for which to set the IAM
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
     The location of the workbench instance.

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
location:

    $ gcloud workbench instances set-iam-policy my_instance \
        --location=us-central1-a policy.json

See https://cloud.google.com/iam/docs/managing-policies for policy file
format and content details.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/set-iam-policy)

---
### `gcloud workbench instances start`

Starts a workbench instance

Starts a workbench instance.

**Synopsis:**
```
gcloud workbench instances start (INSTANCE : --location=LOCATION) [--async]
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

    $ gcloud workbench instances start example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/start)

---
### `gcloud workbench instances stop`

Stops a workbench instance

Stops a workbench instance.

**Synopsis:**
```
gcloud workbench instances stop (INSTANCE : --location=LOCATION) [--async]
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

    $ gcloud workbench instances stop example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/stop)

---
### `gcloud workbench instances update`

Updates a workbench instance

Updates a workbench instance.

**Synopsis:**
```
gcloud workbench instances update (INSTANCE : --location=LOCATION)
    [--async] [--labels=[KEY=VALUE,...]]
    [--machine-type=MACHINE_TYPE --metadata=[KEY=VALUE,...]
      --tags=[TAGS,...] --accelerator-core-count=ACCELERATOR_CORE_COUNT
      --accelerator-type=ACCELERATOR_TYPE
      [--container-repository=CONTAINER_REPOSITORY
      : --container-tag=CONTAINER_TAG]
      --custom-gpu-driver-path=CUSTOM_GPU_DRIVER_PATH --install-gpu-driver
      --shielded-integrity-monitoring=SHIELDED_INTEGRITY_MONITORING
      --shielded-secure-boot=SHIELDED_SECURE_BOOT
      --shielded-vtpm=SHIELDED_VTPM] [GCLOUD_WIDE_FLAG ...]
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
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to this instance. These can be later modified by the setLabels method. |


**Examples:**
```bash
To update machine type for an instance, run:

    $ gcloud workbench instances update example-instance \
      --machine-type=n1-standard-8 --location=us-central1-a

To update labels for an instance, run:

    $ gcloud workbench instances update example-instance \
      --labels=k1=v1,k2=v2 --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/update)

---
### `gcloud workbench instances upgrade`

Upgrades a workbench instance

Upgrades a workbench instance.

**Synopsis:**
```
gcloud workbench instances upgrade (INSTANCE : --location=LOCATION)
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

    $ gcloud workbench instances upgrade example-instance \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workbench/instances/upgrade)

---
# gcloud compute disks

read and manipulate Compute Engine disks

### `gcloud compute disks add-iam-policy-binding`

Add IAM policy binding to a Compute Engine disk

Add an IAM policy binding to the IAM policy of a Compute Engine disk. One
binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud compute disks add-iam-policy-binding (DISK : --zone=ZONE)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Disk resource - The disk for which to add IAM policy binding to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument disk on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISK
     ID of the disk or fully qualified identifier for the disk.

     To set the disk attribute:
     + provide the argument disk on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument disk on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/compute.securityAdmin'
for the user 'test-user@gmail.com' with disk 'my-disk' and zone 'ZONE',
run:

    $ gcloud compute disks add-iam-policy-binding my-disk --zone=ZONE \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with disk 'my-disk' and zone 'ZONE', run:

    $ gcloud compute disks add-iam-policy-binding my-disk --zone=ZONE \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/add-iam-policy-binding)

---
### `gcloud compute disks add-labels`

Add labels to Google Compute Engine persistent disks

gcloud compute disks add-labels adds labels to a Google Compute Engine
persistent disk.

**Synopsis:**
```
gcloud compute disks add-labels DISK_NAME --labels=[KEY=VALUE,...]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | A list of labels to add. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add key-value pairs k0=v0 and k1=v1 to 'example-disk'

    $ gcloud compute disks add-labels example-disk --labels=k0=v0,k1=v1

Labels can be used to identify the disk and to filter them. To find a disk
labeled with key-value pair k1, v2

    $ gcloud compute disks list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute disks describe example-disk \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/add-labels)

---
### `gcloud compute disks add-resource-policies`

Add resource policies to a Compute Engine disk

Add resource policies to a Compute Engine disk.

gcloud compute disks add-resource-policies adds resource policies to a
Compute Engine disk. These policies define a schedule for taking snapshots
and a retention period for these snapshots.

For information on how to create resource policies, see: $ gcloud beta
compute resource-policies create --help

**Synopsis:**
```
gcloud compute disks add-resource-policies DISK_NAME
    --resource-policies=[RESOURCE_POLICY,...]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to add resource policies to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be added to the disk. The policies must exist in the same region as the disk. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to add resource policies to. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to add resource policies to. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
The following command adds two resource policies to a Compute Engine disk.

    $ gcloud compute disks add-resource-policies my-disk --zone=ZONE \
        --resource-policies=policy-1,policy-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/add-resource-policies)

---
### `gcloud compute disks convert`

Convert a Compute Engine Persistent Disk volume to a Hyperdisk volume

Convert Compute Engine Persistent Disk volumes to Hyperdisk volumes.

gcloud compute disks convert converts a Compute Engine Persistent Disk
volume to a Hyperdisk volume. For a comprehensive guide, refer to:
https://cloud.google.com/sdk/gcloud/reference/compute/disks/convert.

**Synopsis:**
```
gcloud compute disks convert DISK_NAME --target-disk-type=TARGET_DISK_TYPE
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-disk-type` | TARGET_DISK_TYPE |  | Specifies the type of Hyperdisk to convert to, for example, to convert a Hyperdisk Balanced volume, specify hyperdisk-balanced. To get a list of available disk types, run gcloud compute disk-types list. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--kms-key` | KMS_KEY |  | _[resource.]_ ID of the key or fully qualified identifier for the key. To set the kms-key attribute: + provide the argument --kms-key on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--kms-keyring` | KMS_KEYRING |  | _[resource.]_ The KMS keyring of the key. To set the kms-keyring attribute: + provide the argument --kms-key on the command line with a fully specified name; + provide the argument --kms-keyring on the command line. |
| `--kms-location` | KMS_LOCATION |  | _[resource.]_ The Google Cloud location for the key. To set the kms-location attribute: + provide the argument --kms-key on the command line with a fully specified name; + provide the argument --kms-location on the command line; + provide the argument --region on the command line. |
| `--kms-project` | KMS_PROJECT |  | _[resource.]_ The Google Cloud project for the key. To set the kms-project attribute: + provide the argument --kms-key on the command line with a fully specified name; + provide the argument --kms-project on the command line; + set the property core/project. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
The following command converts a Persistent Disk volume to a Hyperdisk
Balanced volume:

    $ gcloud compute disks convert my-disk-1 --zone=ZONE \
    --target-disk-type=hyperdisk-balanced
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/convert)

---
### `gcloud compute disks create`

Create Compute Engine persistent disks

gcloud compute disks create creates one or more Compute Engine persistent
disks. When creating virtual machine instances, disks can be attached to
the instances through the gcloud compute instances create command. Disks
can also be attached to instances that are already running using gcloud
compute instances attach-disk.

Disks are zonal resources, so they reside in a particular zone for their
entire lifetime. The contents of a disk can be moved to a different zone by
snapshotting the disk (using gcloud compute disks snapshot) and creating a
new disk using --source-snapshot in the desired zone. The contents of a
disk can also be moved across project or zone by creating an image (using
gcloud compute images create) and creating a new disk using --image in the
desired project and/or zone.

For a comprehensive guide, including details on minimum and maximum disk
size, refer to: https://cloud.google.com/compute/docs/disks

**Synopsis:**
```
gcloud compute disks create DISK_NAME [DISK_NAME ...]
    [--access-mode=ACCESS_MODE] [--architecture=ARCHITECTURE]
    [--confidential-compute] [--csek-key-file=FILE]
    [--description=DESCRIPTION]
    [--guest-os-features=[GUEST_OS_FEATURE,...]] [--labels=[KEY=VALUE,...]]
    [--licenses=[LICENSE,...]]
    [--primary-disk-project=PRIMARY_DISK_PROJECT]
    [--provisioned-iops=PROVISIONED_IOPS]
    [--provisioned-throughput=PROVISIONED_THROUGHPUT]
    [--replica-zones=ZONE,ZONE] [--no-require-csek-key-create]
    [--resource-policies=[RESOURCE_POLICY,...]] [--size=SIZE]
    [--storage-pool=STORAGE_POOL] [--type=TYPE]
    [--image-family-scope=IMAGE_FAMILY_SCOPE
      --image-project=IMAGE_PROJECT --image=IMAGE
      | --image-family=IMAGE_FAMILY | --primary-disk=PRIMARY_DISK
      | --source-disk=SOURCE_DISK
      | --source-instant-snapshot=SOURCE_INSTANT_SNAPSHOT
      | --source-snapshot=SOURCE_SNAPSHOT]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--primary-disk-region=PRIMARY_DISK_REGION
      | --primary-disk-zone=PRIMARY_DISK_ZONE]
    [--region=REGION | --zone=ZONE]
    [--source-disk-region=SOURCE_DISK_REGION
      | --source-disk-zone=SOURCE_DISK_ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME [DISK_NAME ...]
   Names of the disks to create. For details on the naming convention for
   this resource, refer to:
   https://cloud.google.com/compute/docs/naming-resources
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-mode` | one of: READ_ONLY_MANY, READ_WRITE_MANY, READ_WRITE_SINGLE |  | Specifies how VMs attached to the disk can access the data on the disk. To grant read-only access to multiple VMs attached to the disk, set access-mode to READ_ONLY_MANY. To grant read-write access to only one VM attached to the disk, use READ_WRITE_SINGLE. READ_WRITE_SINGLE is used if omitted. ACCESS_MODE must be one of: READ_ONLY_MANY, READ_WRITE_MANY, READ_WRITE_SINGLE. |
| `--architecture` | one of: ARM64, X86_64 |  | Specifies the architecture or processor type that this disk can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. ARCHITECTURE must be one of: ARM64, X86_64. |
| `--confidential-compute` |  |  | Creates the disk with confidential compute mode enabled. Encryption with a Cloud KMS key is required to enable this option. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine resources to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--description` | DESCRIPTION |  | An optional, textual description for the disks being created. |
| `--guest-os-features` | one of: BARE_METAL_LINUX_COMPATIBLE, GVNIC, IDPF, MULTI_IP_SUBNET, SEV_CAPABLE, SEV_LIVE_MIGRATABLE, SEV_LIVE_MIGRATABLE_V2, SEV_SNP_CAPABLE, SNP_SVSM_CAPABLE, TDX_CAPABLE, UEFI_COMPATIBLE, VIRTIO_SCSI_MULTIQUEUE, WINDOWS |  | Enables one or more features for VM instances that use the image for their boot disks. See the descriptions of supported features at: https://cloud.google.com/compute/docs/images/create-delete-deprecate-private-images#guest-os-features. GUEST_OS_FEATURE must be one of: BARE_METAL_LINUX_COMPATIBLE, GVNIC, IDPF, MULTI_IP_SUBNET, SEV_CAPABLE, SEV_LIVE_MIGRATABLE, SEV_LIVE_MIGRATABLE_V2, SEV_SNP_CAPABLE, SNP_SVSM_CAPABLE, TDX_CAPABLE, UEFI_COMPATIBLE, VIRTIO_SCSI_MULTIQUEUE, WINDOWS. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--licenses` | [LICENSE,...] |  | A list of URIs to license resources. The provided licenses will be added onto the created disks to indicate the licensing and billing policies. |
| `--primary-disk-project` | PRIMARY_DISK_PROJECT |  | Project of the primary disk for asynchronous replication. |
| `--provisioned-iops` | PROVISIONED_IOPS |  | Provisioned IOPS of disk to create. Only for use with disks of type pd-extreme and hyperdisk-extreme. |
| `--provisioned-throughput` | PROVISIONED_THROUGHPUT |  | Provisioned throughput of disk to create. The throughput unit is MB per sec. Only for use with disks of type hyperdisk-throughput. |
| `--replica-zones` | ZONE,ZONE |  | A comma-separated list of exactly 2 zones that a regional disk will be replicated to. Required when creating regional disk. The zones must be in the same region as specified in the --region flag. See available zones with gcloud compute zones list. |
| `--require-csek-key-create` |  |  | Refuse to create resources not protected by a user managed key in the key file when --csek-key-file is given. This behavior is enabled by default to prevent incorrect gcloud invocations from accidentally creating resources with no user managed key. Disabling the check allows creation of some resources without a matching Customer-Supplied Encryption Key in the supplied --csek-key-file. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. Enabled by default, use --no-require-csek-key-create to disable. |
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be added to the disk. The policies must exist in the same region as the disk. |
| `--size` | SIZE |  | Size of the disks. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. For example, 10GB will produce 10 gigabyte disks. Disk size must be a multiple of 1 GB. If disk size is not specified, the default size of 500GB for pd-standard disks, 100GB for pd-balanced disks, 100GB for pd-ssd disks, and 1000GB for pd-extreme will be used. For details about disk size limits, refer to: https://cloud.google.com/compute/docs/disks |
| `--storage-pool` | STORAGE_POOL |  | Specifies the URI of the storage pool in which the disk is created. |
| `--type` | TYPE |  | Specifies the type of disk to create. To get a list of available disk types, run gcloud compute disk-types list. The default disk type is pd-standard. |
| `--image-family-scope` | one of: zonal, global |  | Sets the scope for the --image-family flag. By default, when specifying an image family in a public image project, the zonal image family scope is used. All other projects default to the global image. Use this flag to override this behavior. IMAGE_FAMILY_SCOPE must be one of: zonal, global. |
| `--image-project` | IMAGE_PROJECT |  | The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available projects can be generated by running gcloud projects list. * If specifying one of our public images, image-project must be provided. * If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. * If not specified and either image or image-family is provided, the current default project is used. |


**Examples:**
```bash
When creating disks, be sure to include the --zone option. To create disks
'my-disk-1' and 'my-disk-2' in zone us-east1-a:

    $ gcloud compute disks create my-disk-1 my-disk-2 --zone=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/create)

---
### `gcloud compute disks delete`

Delete a Compute Engine disk

gcloud compute disks delete deletes a Compute Engine disk. A disk can be
deleted only if it is not attached to any virtual machine instances.

**Synopsis:**
```
gcloud compute disks delete DISK_NAME [DISK_NAME ...]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME [DISK_NAME ...]
   Names of the disks to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disks to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disks to delete. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To delete the disk 'my-disk' in zone 'us-east1-a', run:

    $ gcloud compute disks delete my-disk --zone=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/delete)

---
### `gcloud compute disks describe`

Describe a Compute Engine disk

gcloud compute disks describe displays all data associated with a Compute
Engine disk in a project.

**Synopsis:**
```
gcloud compute disks describe DISK_NAME [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe the disk 'my-disk' in zone 'us-east1-a', run:

    $ gcloud compute disks describe my-disk --zone=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/describe)

---
### `gcloud compute disks get-iam-policy`

Get the IAM policy for a Compute Engine disk

gcloud compute disks get-iam-policy displays the IAM policy associated with
a Compute Engine disk in a project. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy. The output includes an
"etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ {parent} set-iam-policy for additional
details.

**Synopsis:**
```
gcloud compute disks get-iam-policy (DISK : --zone=ZONE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Disk resource - The disk to display the IAM policy for. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument disk on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISK
     ID of the disk or fully qualified identifier for the disk.

     To set the disk attribute:
     + provide the argument disk on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument disk on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To print the IAM policy for a given disk, run:

    $ gcloud compute disks get-iam-policy my-disk --zone=my-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/get-iam-policy)

---
### `gcloud compute disks list`

List Google Compute Engine disks

gcloud compute disks list displays all Google Compute Engine disks in a
project.

By default, disks from all regions and disks from all zones are listed. The
results can be narrowed down by providing the --regions or --zones flag.

**Synopsis:**
```
gcloud compute disks list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--regions=[REGION,...] | --zones=[ZONE,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all disks in a project in table form, run:

    $ gcloud compute disks list

To list the URIs of all disks in a project, run:

    $ gcloud compute disks list --uri

To list all disks in the us-central1 and europe-west1 regions, given they
are regional resources, run:

    $ gcloud compute disks list \
        --filter="region:( europe-west1 us-central1 )"

To list all disks in zones us-central1-b and europe-west1-d, given they are
zonal resources, run:

    $ gcloud compute disks list \
        --filter="zone:( europe-west1-d us-central1-b )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/list)

---
### `gcloud compute disks move`

Move a disk between zones

gcloud compute disks move facilitates moving a Compute Engine disk volume
from one zone to another. You cannot move a disk if it is attached to a
running or stopped instance; use the gcloud compute instances move command
instead.

The gcloud compute disks move command does not support regional persistent
disks. See
https://cloud.google.com/compute/docs/disks/regional-persistent-disk for
more details.

**Synopsis:**
```
gcloud compute disks move DISK_NAME --destination-zone=DESTINATION_ZONE
    [--async] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-zone` | DESTINATION_ZONE |  | The zone to move the disk to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--zone` | ZONE |  | Zone of the disk to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To move the disk called example-disk-1 from us-central1-b to us-central1-f,
run:

    $ gcloud compute disks move example-disk-1 --zone=us-central1-b \
        --destination-zone=us-central1-f
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/move)

---
### `gcloud compute disks remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine disk

Remove an IAM policy binding from the IAM policy of a Compute Engine disk.
One binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud compute disks remove-iam-policy-binding (DISK : --zone=ZONE)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Disk resource - The disk for which to remove IAM policy binding from. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument disk on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISK
     ID of the disk or fully qualified identifier for the disk.

     To set the disk attribute:
     + provide the argument disk on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument disk on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/compute.securityAdmin' for the user 'test-user@gmail.com' with disk
'my-disk' and zone 'ZONE', run:

    $ gcloud compute disks remove-iam-policy-binding my-disk \
        --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with disk 'my-disk' and zone 'ZONE', run:

    $ gcloud compute disks remove-iam-policy-binding my-disk \
        --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/remove-iam-policy-binding)

---
### `gcloud compute disks remove-labels`

Remove labels from Google Compute Engine persistent disks

gcloud compute disks remove-labels removes labels from a Google Compute
Engine persistent disk.

**Synopsis:**
```
gcloud compute disks remove-labels DISK_NAME
    (--all | --labels=KEY,[KEY,...]) [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[Exactly one of these must be specified:]_ Remove all labels from the resource. |
| `--labels` | KEY,[KEY,...] |  | _[Exactly one of these must be specified:]_ A comma-separated list of label keys to remove from the resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To remove existing labels with key k0 and k1 from 'example-disk'

    $ gcloud compute disks remove-labels example-disk --labels=k0,k1

Labels can be used to identify the disk and to filter them. To find a disk
labeled with key-value pair k1, v2

    $ gcloud compute disks list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute disks describe example-disk \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/remove-labels)

---
### `gcloud compute disks remove-resource-policies`

Remove resource policies from a Compute Engine disk

Remove resource policies from a Compute Engine disk.

gcloud compute disks remove-resource-policies removes resource policies
from a Compute Engine disk.

**Synopsis:**
```
gcloud compute disks remove-resource-policies DISK_NAME
    --resource-policies=[RESOURCE_POLICY,...]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to remove resource policies from.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be removed from the disk. The policies must exist in the same region as the disk. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to remove resource policies from. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to remove resource policies from. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
The following command removes one resource policy from a Compute Engine
disk.

    $ gcloud compute disks remove-resource-policies my-disk \
        --zone=ZONE --resource-policies=POLICY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/remove-resource-policies)

---
### `gcloud compute disks resize`

Resize a disk or disks

gcloud compute disks resize resizes a Compute Engine disk(s).

Only increasing disk size is supported. Disks can be resized regardless of
whether they are attached.

**Synopsis:**
```
gcloud compute disks resize DISK_NAME [DISK_NAME ...] --size=SIZE
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME [DISK_NAME ...]
   Names of the disks to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--size` | SIZE |  | Indicates the new size of the disks. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. For example, 10GB will produce 10 gigabyte disks. Disk size must be a multiple of 1 GB. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disks to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disks to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To resize a disk called example-disk-1 to new size 6TB, run:

    $ gcloud compute disks resize example-disk-1 --size=6TB

To resize two disks called example-disk-2 and example-disk-3 to new size
6TB, run:

    $ gcloud compute disks resize example-disk-2 example-disk-3 \
       --size=6TB

This assumes that original size of each of these disks is 6TB or less.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/resize)

---
### `gcloud compute disks set-iam-policy`

Set the IAM policy for a Compute Engine disk

Sets the IAM policy for the given disk as defined in a JSON or YAML file.

**Synopsis:**
```
gcloud compute disks set-iam-policy (DISK : --zone=ZONE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Disk resource - The disk to set the IAM policy for. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument disk on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISK
     ID of the disk or fully qualified identifier for the disk.

     To set the disk attribute:
     + provide the argument disk on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument disk on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the disk my-disk:

    $ gcloud compute disks set-iam-policy my-disk --zone=ZONE policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/set-iam-policy)

---
### `gcloud compute disks snapshot`

Create snapshots of Compute Engine persistent disks

gcloud compute disks snapshot creates snapshots of persistent disks.
Snapshots are useful for backing up data, copying a persistent disk, and
even, creating a custom image. Snapshots can be created from persistent
disks even while they are attached to running instances. Once created,
snapshots may be managed (listed, deleted, etc.) via gcloud compute
snapshots.

Refer to the Snapshot best practices guide.
https://cloud.google.com/compute/docs/disks/snapshot-best-practices

gcloud compute disks snapshot waits until the operation returns a status of
READY or FAILED, or reaches the maximum timeout, and returns the last known
details of the snapshot.

Note: To create snapshots, the following IAM permissions are necessary
compute.disks.createSnapshot, compute.snapshots.create,
compute.snapshots.get, and compute.zoneOperations.get.

**Synopsis:**
```
gcloud compute disks snapshot DISK_NAME [DISK_NAME ...] [--async]
    [--chain-name=CHAIN_NAME] [--csek-key-file=FILE]
    [--description=DESCRIPTION] [--guest-flush] [--labels=[KEY=VALUE,...]]
    [--snapshot-names=SNAPSHOT_NAME,[...]] [--storage-location=LOCATION]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME [DISK_NAME ...]
   Names of the disks to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--chain-name` | CHAIN_NAME |  | Create the new snapshot in the snapshot chain labeled with the specified name. The chain name must be 1-63 characters long and comply with RFC1035. Use this flag only if you are an advanced service owner who needs to create separate snapshot chains, for example, for chargeback tracking. When you describe your snapshot resource, this field is visible only if it has a non-empty value. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine resources to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--description` | DESCRIPTION |  | Text to describe the snapshots being created. |
| `--guest-flush` |  |  | Create an application-consistent snapshot by informing the OS to prepare for the snapshot process. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--snapshot-names` | SNAPSHOT_NAME,[...] |  | Names to assign to the created snapshots. Without this option, the name of each snapshot will be a random 12-character alphanumeric string that starts with a letter. The values of this option run parallel to the disks specified. For example, gcloud compute disks snapshot my-disk-1 my-disk-2 my-disk-3 --snapshot-names snapshot-1,snapshot-2,snapshot-3 will result in my-disk-1 being snapshotted as snapshot-1, my-disk-2 as snapshot-2, and so on. The name must match the (?:[a-z](?:[-a-z0-9]{0,61}[a-z0-9])?) regular expression, which means it must start with an alphabetic character followed by one or more alphanumeric characters or dashes. The name must not exceed 63 characters and must not contain special symbols. All characters must be lowercase. |
| `--storage-location` | LOCATION |  | Google Cloud Storage location, either regional or multi-regional, where snapshot content is to be stored. If absent, a nearby regional or multi-regional location is chosen automatically. |


**Examples:**
```bash
To create a snapshot named snapshot-test of a persistent disk named test in
zone us-central1-a, run:

    $ gcloud compute disks snapshot test --zone=us-central1-a \
        --snapshot-names=snapshot-test \
        --description="This is an example snapshot"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/snapshot)

---
### `gcloud compute disks start-async-replication`

Start asynchronous replication on a Compute Engine persistent disk

gcloud compute disks start-async-replication starts async replication on a
Compute Engine persistent disk. This command must be invoked on the primary
disk and --secondary-disk must be provided.

**Synopsis:**
```
gcloud compute disks start-async-replication DISK_NAME
    --secondary-disk=SECONDARY_DISK (--region=REGION | --zone=ZONE)
    (--secondary-disk-region=SECONDARY_DISK_REGION
      | --secondary-disk-zone=SECONDARY_DISK_ZONE)
    [--secondary-disk-project=SECONDARY_DISK_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--secondary-disk` | SECONDARY_DISK |  | Secondary disk for asynchronous replication. This flag is required when starting replication. |


**Examples:**
```bash
Start replication from the primary disk 'my-disk-1' in zone us-east1-a to
the secondary disk 'my-disk-2' in zone us-west1-a:

    $ gcloud compute disks start-async-replication my-disk-1 \
        --zone=us-east1-a --secondary-disk=my-disk-2 \
        --secondary-disk-zone=us-west1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/start-async-replication)

---
### `gcloud compute disks stop-async-replication`

Stop async replication on a Compute Engine persistent disk

gcloud compute disks stop-async-replication stops async replication on a
Compute Engine persistent disk. This command can be invoked either on the
primary or on the secondary disk.

**Synopsis:**
```
gcloud compute disks stop-async-replication DISK_NAME
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to stop async replication.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the disk to stop async replication. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the disk to stop async replication. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
Stop replication on the primary disk 'my-disk-1' in zone us-east1-a:

    $ gcloud compute disks stop-async-replication my-disk-1 \
        --zone=us-east1-a

Stop replication on the secondary disk 'my-disk-2' in zone us-west1-a:

    $ gcloud compute disks stop-async-replication my-disk-2 \
        --zone=us-west1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/stop-async-replication)

---
### `gcloud compute disks stop-group-async-replication`

Consistently stops a group of asynchronously replicating disks

gcloud compute disks stop-group-async-replication consistently stops a
group of asynchronously replicating disks. This command can be invoked in
either in the primary or secondary scope of the replicating disks.

**Synopsis:**
```
gcloud compute disks stop-group-async-replication
    DISK_CONSISTENCY_GROUP_POLICY [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_CONSISTENCY_GROUP_POLICY
   URL of the disk consistency group resource policy. The resourcepolicy
   is always in the region of the primary disks.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the consistency group's primary or secondary disks. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the consistency group's primary or secondary disks. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To stop group replication in the primary scope, include the zone or region
of the primary disks. The URL of the disk consistency group resource policy
always uses the region of the primary disks:

    $ gcloud compute disks stop-group-async-replication \
        projects/my-project/regions/us-west1/resourcePolicies/\
    my-policy --zone=us-west1-a

Alternatively, you can stop replication in the secondary scope. Include the
region or zone of the secondary disks. The URL of the disk consistency
group resource policy always uses the region of the primary disks:

    $ gcloud compute disks stop-group-async-replication \
        projects/my-project/regions/us-west1/resourcePolicies/\
    my-policy --zone=us-west2-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/stop-group-async-replication)

---
### `gcloud compute disks update`

Update a Compute Engine persistent disk

gcloud compute disks update updates a Compute Engine persistent disk.

**Synopsis:**
```
gcloud compute disks update DISK_NAME [--access-mode=ACCESS_MODE]
    [--provisioned-iops=PROVISIONED_IOPS]
    [--provisioned-throughput=PROVISIONED_THROUGHPUT] [--size=SIZE]
    [--update-labels=[KEY=VALUE,...]]
    [--append-licenses=LICENSE,[LICENSE,...]
      --remove-licenses=LICENSE,[LICENSE,...]
      --replace-license=LICENSE,LICENSE]
    [--clear-architecture | --update-architecture=UPDATE_ARCHITECTURE]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DISK_NAME
   Name of the disk to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-mode` | one of: READ_ONLY_MANY, READ_WRITE_MANY, READ_WRITE_SINGLE |  | Specifies how VMs attached to the disk can access the data on the disk. To grant read-only access to multiple VMs attached to the disk, set access-mode to READ_ONLY_MANY. To grant read-write access to only one VM attached to the disk, use READ_WRITE_SINGLE. READ_WRITE_SINGLE is used if omitted. ACCESS_MODE must be one of: READ_ONLY_MANY, READ_WRITE_MANY, READ_WRITE_SINGLE. |
| `--provisioned-iops` | PROVISIONED_IOPS |  | Provisioned IOPS of disk to update. Only for use with disks of type hyperdisk-extreme. |
| `--provisioned-throughput` | PROVISIONED_THROUGHPUT |  | Provisioned throughput of disk to update. The throughput unit is MB per sec. |
| `--size` | SIZE |  | Size of the disks. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. For details about disk size limits, refer to: https://cloud.google.com/compute/docs/disks |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--append-licenses` | LICENSE,[LICENSE,...] |  | "A list of license URIs or license codes. These licenses will be appended to the existing licenses on the disk. Provided licenses can be either license URIs or license codes but not a mix of both. |
| `--remove-licenses` | LICENSE,[LICENSE,...] |  | A list of license URIs or license codes. If present in the set of existing licenses, these licenses will be removed. If not present, this is a no-op. Provided licenses can be either license URIs or license codes but not a mix of both. |
| `--replace-license` | LICENSE,LICENSE |  | A list of license URIs or license codes. The first license is the license to be replaced and the second license is the replacement license. Provided licenses can be either license URIs or license codes but not a mix of both. |


**Examples:**
```bash
To update labels 'k0' and 'k1' and remove label 'k3' of a disk, run:

    $ gcloud compute disks update example-disk --zone=us-central1-a \
      --update-labels=k0=value1,k1=value2 --remove-labels=k3

    `_k0_` and `_k1_` are added as new labels if not already present.

Labels can be used to identify the disk. To list disks with the 'k1:value2'
label, run:

    $ gcloud compute disks list --filter='labels.k1:value2'

To list only the labels when describing a resource, use --format to filter
the result:

    $ gcloud compute disks describe example-disk \
      --format="default(labels)"

To append licenses to the disk, run:

    $ gcloud compute disks update example-disk --zone=us-central1-a \
      --append-licenses=projects/license-project/global/licenses/\
    license-1,projects/license-project/global/licenses/license-2

To remove licenses from the disk, run:

    $ gcloud compute disks update example-disk --zone=us-central1-a \
      --replace-licenses=projects/license-project/global/licenses/\
    license-1,projects/license-project/global/licenses/license-2

To replace a license on the disk, run:

    $ gcloud compute disks update example-disk --zone=us-central1-a \
      --replace-license=projects/license-project/global/licenses/\
    old-license,projects/license-project/global/licenses/new-license
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/update)

---

## `gcloud compute disks bulk` — manipulate multiple Compute Engine disks with single command executions
### `gcloud compute disks bulk create`

Create multiple Compute Engine disks

gcloud compute disks bulk create facilitates the creation of multiple
Compute Engine disks with a single command. This includes cloning a set of
Async PD secondary disks with the same consistency group policy.

**Synopsis:**
```
gcloud compute disks bulk create
    --source-consistency-group-policy=SOURCE_CONSISTENCY_GROUP_POLICY
    (--region=REGION | --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-consistency-group-policy` | SOURCE_CONSISTENCY_GROUP_POLICY |  | URL of the source consistency group resource policy. The resource policy is always the same region as the source disks. |


**Examples:**
```bash
To consistently clone secondary disks with the same consistency group
policy
'projects/example-project/regions/us-central1/resourcePolicies/example-group-policy'
to target zone 'us-central1-a', run:

    $ gcloud compute disks bulk create \
        --source-consistency-group-policy=projects/example-project/\
    regions/us-central1/resourcePolicies/example-group-policy \
        --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/disks/bulk/create)

---
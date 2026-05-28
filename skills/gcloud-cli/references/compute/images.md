# gcloud compute images

list, create, and delete Compute Engine images

### `gcloud compute images add-iam-policy-binding`

Add IAM policy binding to a Compute Engine image

Add an IAM policy binding to the IAM policy of a Compute Engine image. One
binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud compute images add-iam-policy-binding IMAGE --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image resource - The image for which to add IAM policy binding to. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument image on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE
     ID of the image or fully qualified identifier for the image.

     To set the image attribute:
     + provide the argument image on the command line.
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
for the user 'test-user@gmail.com' with image 'my-image', run:

    $ gcloud compute images add-iam-policy-binding my-image \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with image 'my-image', run:

    $ gcloud compute images add-iam-policy-binding my-image \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/add-iam-policy-binding)

---
### `gcloud compute images add-labels`

Add labels to Google Compute Engine images

gcloud compute images add-labels adds labels to a Google Compute Engine
image.

**Synopsis:**
```
gcloud compute images add-labels IMAGE_NAME --labels=[KEY=VALUE,...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | A list of labels to add. |


**Examples:**
```bash
To add key-value pairs k0=v0 and k1=v1 to 'example-image'

    $ gcloud compute images add-labels example-image --labels=k0=v0,k1=v1

Labels can be used to identify the image and to filter them. To find a
image labeled with key-value pair k1, v2

    $ gcloud compute images list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute images describe example-image \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/add-labels)

---
### `gcloud compute images create`

Create Compute Engine images

gcloud compute images create is used to create custom disk images. The
resulting image can be provided during instance or disk creation so that
the instance attached to the resulting disks has access to a known set of
software or files from the image.

Images can be created from gzipped compressed tarball containing raw disk
data, existing disks in any zone, existing images, and existing snapshots
inside the same project.

Images are global resources, so they can be used across zones and projects.

To learn more about creating image tarballs, visit
https://cloud.google.com/compute/docs/creating-custom-image.

**Synopsis:**
```
gcloud compute images create IMAGE_NAME
    (--source-disk=SOURCE_DISK | --source-image=SOURCE_IMAGE
      | --source-image-family=SOURCE_IMAGE_FAMILY
      | --source-snapshot=SOURCE_SNAPSHOT | --source-uri=SOURCE_URI)
    [--architecture=ARCHITECTURE] [--csek-key-file=FILE]
    [--description=DESCRIPTION] [--family=FAMILY]
    [--forbidden-database-file=[DBX_VALUE,...]] [--force]
    [--guest-os-features=[GUEST_OS_FEATURE,...]]
    [--key-exchange-key-file=[KEK_VALUE,...]] [--labels=[KEY=VALUE,...]]
    [--licenses=[LICENSES,...]] [--platform-key-file=PLATFORM_KEY_FILE]
    [--no-require-csek-key-create]
    [--signature-database-file=[DB_VALUE,...]]
    [--source-disk-project=SOURCE_DISK_PROJECT]
    [--source-disk-zone=SOURCE_DISK_ZONE]
    [--source-image-project=SOURCE_IMAGE_PROJECT]
    [--storage-location=LOCATION]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-disk` | SOURCE_DISK |  | _[Exactly one of these must be specified:]_ A source disk to create the image from. The value for this option can be the name of a disk with the zone specified via --source-disk-zone flag. |
| `--source-image` | SOURCE_IMAGE |  | _[Exactly one of these must be specified:]_ The name of an image to clone. May be used with --source-image-project to clone an image in a different project. |
| `--source-image-family` | SOURCE_IMAGE_FAMILY |  | _[Exactly one of these must be specified:]_ The family of the source image. This will cause the latest non- deprecated image in the family to be used as the source image. May be used with --source-image-project to refer to an image family in a different project. |
| `--source-snapshot` | SOURCE_SNAPSHOT |  | _[Exactly one of these must be specified:]_ A source snapshot to create the image from. The value for this option can be the name of a snapshot within the same project as the destination image. |
| `--source-uri` | SOURCE_URI |  | _[Exactly one of these must be specified:]_ The full Cloud Storage URI where the disk image is stored. This file must be a gzip-compressed tarball whose name ends in .tar.gz. For more information about Cloud Storage URIs, see https://cloud.google.com/storage/docs/request-endpoints#json-api. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--architecture` | one of: ARM64, X86_64 |  | Specifies the architecture or processor type that this image can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. ARCHITECTURE must be one of: ARM64, X86_64. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine images to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--description` | DESCRIPTION |  | An optional, textual description for the image being created. |
| `--family` | FAMILY |  | The family of the image. When creating an instance or disk, specifying a family will cause the latest non-deprecated image in the family to be used. |
| `--forbidden-database-file` | [DBX_VALUE,...] |  | Comma-separated list of file paths that point to revoked X.509 certificates in DER format or raw binary files. When you create a Shielded VM instance from this image, these certificates or files are added to the forbidden signature database (dbx). |
| `--force` |  |  | By default, image creation fails when it is created from a disk that is attached to a running instance. When this flag is used, image creation from disk will proceed even if the disk is in use. |
| `--guest-os-features` | one of: BARE_METAL_LINUX_COMPATIBLE, GVNIC, IDPF, MULTI_IP_SUBNET, SEV_CAPABLE, SEV_LIVE_MIGRATABLE, SEV_LIVE_MIGRATABLE_V2, SEV_SNP_CAPABLE, SNP_SVSM_CAPABLE, TDX_CAPABLE, UEFI_COMPATIBLE, VIRTIO_SCSI_MULTIQUEUE, WINDOWS |  | Enables one or more features for VM instances that use the image for their boot disks. See the descriptions of supported features at: https://cloud.google.com/compute/docs/images/create-delete-deprecate-private-images#guest-os-features. GUEST_OS_FEATURE must be one of: BARE_METAL_LINUX_COMPATIBLE, GVNIC, IDPF, MULTI_IP_SUBNET, SEV_CAPABLE, SEV_LIVE_MIGRATABLE, SEV_LIVE_MIGRATABLE_V2, SEV_SNP_CAPABLE, SNP_SVSM_CAPABLE, TDX_CAPABLE, UEFI_COMPATIBLE, VIRTIO_SCSI_MULTIQUEUE, WINDOWS. |
| `--key-exchange-key-file` | [KEK_VALUE,...] |  | Comma-separated list of file paths that point to X.509 certificates in DER format or raw binary files. When you create a Shielded VM instance from this image, these certificates or files are used as key exchange keys (KEK). |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--licenses` | [LICENSES,...] |  | Comma-separated list of URIs to license resources. |
| `--platform-key-file` | PLATFORM_KEY_FILE |  | File path that points to an X.509 certificate in DER format or raw binary file. When you create a Shielded VM instance from this image, this certificate or raw binary file is used as the platform key (PK). |
| `--require-csek-key-create` |  |  | Refuse to create images not protected by a user managed key in the key file when --csek-key-file is given. This behavior is enabled by default to prevent incorrect gcloud invocations from accidentally creating images with no user managed key. Disabling the check allows creation of some images without a matching Customer-Supplied Encryption Key in the supplied --csek-key-file. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. Enabled by default, use --no-require-csek-key-create to disable. |
| `--signature-database-file` | [DB_VALUE,...] |  | Comma-separated list of file paths that point to valid X.509 certificates in DER format or raw binary files. When you create a Shielded VM instance from this image, these certificates or files are added to the signature database (db). |
| `--source-disk-project` | SOURCE_DISK_PROJECT |  | Project name of the source disk. Must also specify --source-disk when using this flag. |
| `--source-disk-zone` | SOURCE_DISK_ZONE |  | Zone of the source disk to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--source-image-project` | SOURCE_IMAGE_PROJECT |  | The project name of the source image. Must also specify either --source-image or --source-image-family when using this flag. |
| `--storage-location` | LOCATION |  | Specifies a Cloud Storage location, either regional or multi-regional, where image content is to be stored. If not specified, the multi-region location closest to the source is chosen automatically. |


**Examples:**
```bash
To create an image 'my-image' from a disk 'my-disk' in zone 'us-east1-a',
run:

    $ gcloud compute images create my-image --source-disk=my-disk \
      --source-disk-zone=us-east1-a

To create an image 'my-image' from a disk 'my-disk' in zone 'us-east1-a'
with source disk project 'source-disk-project' run:

    $ gcloud compute images create my-image --source-disk=my-disk \
      --source-disk-zone=us-east1-a \
      --source-disk-project=source-disk-project

To create an image 'my-image' from another image 'source-image' with source
image project 'source-image-project', run:

    $ gcloud compute images create my-image \
      --source-image=source-image \
      --source-image-project=source-image-project

To create an image 'my-image' from the latest non-deprecated image in the
family 'source-image-family' with source image project
'source-image-project', run:

    $ gcloud compute images create my-image \
      --source-image-family=source-image-family \
      --source-image-project=source-image-project

To create an image 'my-image' from a snapshot 'source-snapshot', run:

    $ gcloud compute images create my-image \
      --source-snapshot=source-snapshot
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/create)

---
### `gcloud compute images delete`

Delete Compute Engine images

gcloud compute images delete deletes one or more Compute Engine images.

**Synopsis:**
```
gcloud compute images delete IMAGE_NAME [IMAGE_NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME [IMAGE_NAME ...]
   Names of the disk images to delete.
```

**Examples:**
```bash
To delete images 'my-image1' and 'my-image2', run:

    $ gcloud compute images delete my-image1 my-image2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/delete)

---
### `gcloud compute images deprecate`

Manage deprecation status of Compute Engine images

gcloud compute images deprecate is used to deprecate images.

**Synopsis:**
```
gcloud compute images deprecate IMAGE_NAME --state=STATE
    [--replacement=REPLACEMENT]
    [--delete-in=DELETE_IN | --delete-on=DELETE_ON]
    [--deprecate-in=DEPRECATE_IN | --deprecate-on=DEPRECATE_ON]
    [--obsolete-in=OBSOLETE_IN | --obsolete-on=OBSOLETE_ON]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--state` | one of: ACTIVE The image is currently supported |  | The deprecation state to set on the image. STATE must be one of: ACTIVE The image is currently supported. DELETED New uses result in an error. Setting this state will not automatically delete the image. You must still make a request to delete the image to remove it from the image list. DEPRECATED Operations which create a new DEPRECATED resource return successfully, but with a warning indicating that the image is deprecated and recommending its replacement. OBSOLETE New uses result in an error. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--replacement` | REPLACEMENT |  | Specifies a Compute Engine image as a replacement for the image being phased out. Users of the deprecated image will be advised to switch to this replacement. For example, --replacement example-image or --replacement projects/google/global/images/example-image. This flag value is purely informational and is not validated in any way. |


**Examples:**
```bash
To deprecate an image called 'IMAGE' immediately, mark it as obsolete in
one day, and mark it as deleted in two days, use:

    $ gcloud compute images deprecate IMAGE --state=DEPRECATED \
        --obsolete-in=1d --delete-in=2d

To un-deprecate an image called 'IMAGE' and clear times for deprecated,
obsoleted, and deleted, use:

    $ gcloud compute images deprecate IMAGE --state=ACTIVE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/deprecate)

---
### `gcloud compute images describe`

Describe a Compute Engine image

gcloud compute images describe displays all data associated with a Compute
Engine image in a project.

**Synopsis:**
```
gcloud compute images describe IMAGE_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/describe)

---
### `gcloud compute images describe-from-family`

Describe the latest image from an image family

gcloud compute images describe-from-family looks up the latest image from
an image family and runs a describe on it. If the image is not in the
default project, you need to specify a value for --project.

**Synopsis:**
```
gcloud compute images describe-from-family IMAGE_NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone to query. Returns the latest image available in the image family for the specified zone. If not specified, returns the latest globally available image. |


**Examples:**
```bash
To view the description for the latest debian-9 image from the debian-cloud
project, run:

    $ gcloud compute images describe-from-family debian-9 \
        --project=debian-cloud
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/describe-from-family)

---
### `gcloud compute images export`

Export a Compute Engine image

gcloud compute images export exports virtual disk images from Compute
Engine.

By default, images are exported in the Compute Engine format, which is a
disk.raw file that is tarred and gzipped.

The --export-format flag exports the image to a format supported by QEMU
using qemu-img. Valid formats include vmdk, vhdx, vpc, vdi, and qcow2.

Before exporting an image, set up access to Cloud Storage and grant
required roles to the user accounts and service accounts. For more
information, see
https://cloud.google.com/compute/docs/import/requirements-export-import-images.

**Synopsis:**
```
gcloud compute images export --destination-uri=DESTINATION_URI
    (--image=IMAGE | --image-family=IMAGE_FAMILY) [--async]
    [--cloudbuild-service-account=CLOUDBUILD_SERVICE_ACCOUNT]
    [--compute-service-account=COMPUTE_SERVICE_ACCOUNT]
    [--export-format=EXPORT_FORMAT] [--image-project=IMAGE_PROJECT]
    [--log-location=LOG_LOCATION] [--network=NETWORK] [--subnet=SUBNET]
    [--timeout=TIMEOUT; default="2h"] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-uri` | DESTINATION_URI |  | The Cloud Storage URI destination for the exported virtual disk file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cloudbuild-service-account` | CLOUDBUILD_SERVICE_ACCOUNT |  | Image import and export tools use Cloud Build to import and export images to and from your project. Cloud Build uses a specific service account to execute builds on your behalf. The Cloud Build service account generates an access token for other service accounts and it is also used for authentication when building the artifacts for the image import tool. Use this flag to to specify a user-managed service account for image import and export. If you don't specify this flag, Cloud Build runs using your project's default Cloud Build service account. To set this option, specify the email address of the desired user-managed service account. Note: You must specify the --logs-location flag when you set a user-managed service account. At minimum, the specified user-managed service account needs to have the following roles assigned: * roles/compute.admin * roles/iam.serviceAccountTokenCreator * roles/iam.serviceAccountUser |
| `--compute-service-account` | COMPUTE_SERVICE_ACCOUNT |  | A temporary virtual machine instance is created in your project during image export. Image export tooling on this temporary instance must be authenticated. A Compute Engine service account is an identity attached to an instance. Its access tokens can be accessed through the instance metadata server and can be used to authenticate image export tooling on the instance. To set this option, specify the email address corresponding to the required Compute Engine service account. If not provided, the image export on the temporary instance uses the project's default Compute Engine service account. At a minimum, you need to grant the following roles to the specified Cloud Build service account: * roles/compute.storageAdmin * roles/storage.objectAdmin |
| `--export-format` | EXPORT_FORMAT |  | Specify the format to export to, such as vmdk, vhdx, vpc, or qcow2. |
| `--image-project` | IMAGE_PROJECT |  | The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available projects can be generated by running gcloud projects list. * If specifying one of our public images, image-project must be provided. * If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. * If not specified and either image or image-family is provided, the current default project is used. |
| `--log-location` | LOG_LOCATION |  | Directory in Cloud Storage to hold build logs. If not set, gs://<project num>.cloudbuild-logs.googleusercontent.com/ is created and used. |
| `--network` | NETWORK |  | The name of the network in your project to use for the image export. When you export an image, the export tool creates and uses temporary VMs in your project for the export process. Use this flag to specify the network to use for these temporary VMs. |
| `--subnet` | SUBNET |  | Name of the subnetwork in your project to use for the image export. When you export an image, the export tool creates and uses temporary VMs in your project for the export process. Use this flag to specify the subnetwork to use for these temporary VMs. * If the network resource is in legacy mode, do not provide this property. * If the network is in auto subnet mode, specifying the subnetwork is optional. * If the network is in custom subnet mode, then this field must be specified. |
| `--timeout` | TIMEOUT | 2h | Maximum time an export can last before it fails as "TIMEOUT". For example, if you specify 2h, the process fails after 2 hours. See $ gcloud topic datetimes for information about duration formats. This timeout option has a maximum value of 24 hours. If you are exporting a large image that takes longer than 24 hours to export, either use the RAW disk format to reduce the time needed for converting the image, or split the data into several smaller images. |
| `--zone` | ZONE |  | The zone to use when exporting the image. When you export an image, the export tool creates and uses temporary VMs in your project for the export process. Use this flag to specify the zone to use for these temporary VMs. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To export a VMDK file my-image from a project my-project to a Cloud Storage
bucket my-bucket, run:

    $ gcloud compute images export --image=my-image \
        --destination-uri=gs://my-bucket/my-image.vmdk \
        --export-format=vmdk --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/export)

---
### `gcloud compute images get-iam-policy`

Get the IAM policy for a Compute Engine image

gcloud compute images get-iam-policy displays the IAM policy associated
with a Compute Engine image in a project. If formatted as JSON, the output
can be edited and used as a policy file for set-iam-policy. The output
includes an "etag" field identifying the version emitted and allowing
detection of concurrent policy updates; see $ {parent} set-iam-policy for
additional details.

**Synopsis:**
```
gcloud compute images get-iam-policy IMAGE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image resource - The image to display the IAM policy for. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument image on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE
     ID of the image or fully qualified identifier for the image.

     To set the image attribute:
     + provide the argument image on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given image, run:

    $ gcloud compute images get-iam-policy my-image
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/get-iam-policy)

---
### `gcloud compute images import`

Import an image into Compute Engine

(DEPRECATED) This command is being deprecated. Instead, use the gcloud
migration vms image-imports command. For more information, see
https://cloud.google.com/migrate/virtual-machines/docs/5.0/migrate/image_import.

gcloud compute images import imports Virtual Disk images, such as VMWare
VMDK files and VHD files, into Compute Engine.

Importing images involves four steps:
  o Upload the virtual disk file to Cloud Storage.
  o Import the image to Compute Engine.
  o Detect the OS and bootloader contained on the disk.
  o Translate the image to make a bootable image. This command performs
    all four of these steps as required, depending on the input arguments
    specified.

Before importing an image, set up access to Cloud Storage and grant
required roles to the user accounts and service accounts. For more
information, see
https://cloud.google.com/compute/docs/import/requirements-export-import-images.

To override the detected OS, specify the --os flag. You can omit the
translation step using the --data-disk flag.

If you exported your disk from Compute Engine then you don't need to
re-import it. Instead, use gcloud compute images create to create more
images from the disk.

Files stored on Cloud Storage and images in Compute Engine incur charges.
See
https://cloud.google.com/compute/docs/images/importing-virtual-disks#resource_cleanup.

Troubleshooting: Image import/export tools rely on CloudBuild default
behavior. They has been using the default CloudBuild service account in
order to import/export images to/from Google Cloud Platform. However, Cloud
Build has changed this default behavior and in new projects a custom user
managed service account may need to be provided to perform the builds. If
you get a CloudBuild service account related error, run gcloud with
--cloudbuild-service-account=<custom service account>. See gcloud compute
images import --help for details.

**Synopsis:**
```
gcloud compute images import IMAGE_NAME --cmd-deprecated
    (--source-file=SOURCE_FILE | --source-image=SOURCE_IMAGE
      | --aws-access-key-id=AWS_ACCESS_KEY_ID --aws-region=AWS_REGION
      --aws-secret-access-key=AWS_SECRET_ACCESS_KEY
      --aws-session-token=AWS_SESSION_TOKEN
      (--aws-source-ami-file-path=AWS_SOURCE_AMI_FILE_PATH
      | --aws-ami-export-location=AWS_AMI_EXPORT_LOCATION
      --aws-ami-id=AWS_AMI_ID)) [--no-address] [--async]
    [--cloudbuild-service-account=CLOUDBUILD_SERVICE_ACCOUNT]
    [--compute-service-account=COMPUTE_SERVICE_ACCOUNT]
    [--description=DESCRIPTION] [--family=FAMILY] [--no-guest-environment]
    [--guest-os-features=[GUEST_OS_FEATURE,...]]
    [--log-location=LOG_LOCATION] [--network=NETWORK]
    [--storage-location=STORAGE_LOCATION] [--subnet=SUBNET]
    [--timeout=TIMEOUT; default="2h"] [--zone=ZONE]
    [--data-disk | --byol --os=OS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cmd-deprecated` |  |  | The command you're using is deprecated and will be removed by December 31, 2025. We recommend using gcloud compute migration image-imports instead. See our official documentation for more information. https://cloud.google.com/migrate/virtual-machines/docs/5.0/migrate/image_import. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-address` |  |  | Temporary VMs are created in your project during image import. Set this flag so that these temporary VMs are not assigned external IP addresses. Note: The image import process requires package managers to be installed on the operating system for the virtual disk. These package managers might need to make requests to package repositories that are outside Google Cloud. To allow access for these updates, you need to configure Cloud NAT and Private Google Access. For more information, see https://cloud.google.com/compute/docs/import/importing-virtual-disks#no-external-ip. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cloudbuild-service-account` | CLOUDBUILD_SERVICE_ACCOUNT |  | Image import and export tools use Cloud Build to import and export images to and from your project. Cloud Build uses a specific service account to execute builds on your behalf. The Cloud Build service account generates an access token for other service accounts and it is also used for authentication when building the artifacts for the image import tool. Use this flag to to specify a user-managed service account for image import and export. If you don't specify this flag, Cloud Build runs using your project's default Cloud Build service account. To set this option, specify the email address of the desired user-managed service account. Note: You must specify the --logs-location flag when you set a user-managed service account. At minimum, the specified user-managed service account needs to have the following roles assigned: * roles/compute.admin * roles/iam.serviceAccountTokenCreator * roles/iam.serviceAccountUser |
| `--compute-service-account` | COMPUTE_SERVICE_ACCOUNT |  | A temporary virtual machine instance is created in your project during image import. Image import tooling on this temporary instance must be authenticated. A Compute Engine service account is an identity attached to an instance. Its access tokens can be accessed through the instance metadata server and can be used to authenticate image import tooling on the instance. To set this option, specify the email address corresponding to the required Compute Engine service account. If not provided, the image import on the temporary instance uses the project's default Compute Engine service account. At a minimum, you need to grant the following roles to the specified Cloud Build service account: * roles/compute.storageAdmin * roles/storage.objectViewer |
| `--description` | DESCRIPTION |  | Description to set for the imported image. |
| `--family` | FAMILY |  | Family to set for the imported image. |
| `--guest-environment` |  |  | Installs the guest environment on the image. See https://cloud.google.com/compute/docs/images/guest-environment. Enabled by default, use --no-guest-environment to disable. |
| `--guest-os-features` | [GUEST_OS_FEATURE,...] |  | Enables one or more features for VM instances that use the image for their boot disks. See the descriptions of supported features at: https://cloud.google.com/compute/docs/images/create-delete-deprecate-private-images#guest-os-features. GUEST_OS_FEATURE must be (only one value is supported): UEFI_COMPATIBLE. |
| `--log-location` | LOG_LOCATION |  | Directory in Cloud Storage to hold build logs. If not set, gs://<project num>.cloudbuild-logs.googleusercontent.com/ is created and used. |
| `--network` | NETWORK |  | Name of the network in your project to use for the image import. When you import an image, the import tool creates and uses temporary VMs in your project for the import process. Use this flag to specify the network to use for these temporary VMs. |
| `--storage-location` | STORAGE_LOCATION |  | Specifies a Cloud Storage location, either regional or multi-regional, where image content is to be stored. If not specified, the multi-region location closest to the source is chosen automatically. |
| `--subnet` | SUBNET |  | Name of the subnetwork in your project to use for the image import. When you import an image, the import tool creates and uses temporary VMs in your project for the import process. Use this flag to specify the subnetwork to use for these temporary VMs. * If the network resource is in legacy mode, do not provide this property. * If the network is in auto subnet mode, specifying the subnetwork is optional. * If the network is in custom subnet mode, then this field must be specified. |
| `--timeout` | TIMEOUT | 2h | Maximum time an import can last before it fails as "TIMEOUT". For example, if you specify 2h, the process fails after 2 hours. See $ gcloud topic datetimes for information about duration formats. This timeout option has a maximum value of 24 hours. If you are importing a large image that takes longer than 24 hours to import, either use the RAW disk format to reduce the time needed for converting the image, or split the data into several smaller images. |
| `--zone` | ZONE |  | Zone to use when importing the image. When you import an image, the import tool creates and uses temporary VMs in your project for the import process. Use this flag to specify the zone to use for these temporary VMs. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To import a centos-7 VMDK file, run:

    $ gcloud compute images import myimage-name --os=centos-7 \
        --source-file=mysourcefile

To import a data disk without operating system, run:

    $ gcloud compute images import myimage-name --data-disk \
        --source-file=mysourcefile
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/import)

---
### `gcloud compute images list`

List Google Compute Engine images

gcloud compute images list displays all Google Compute Engine images in a
project.

**Synopsis:**
```
gcloud compute images list [NAME ...] [--preview-images]
    [--regexp=REGEXP, -r REGEXP] [--show-deprecated] [--no-standard-images]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
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
| `--preview-images` |  |  | Show images that are in limited preview. The preview image projects are: (none) |
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--show-deprecated` |  |  | If provided, deprecated images are shown. |
| `--standard-images` |  |  | List images from public image projects. The public image projects that are available include the following: cos-cloud, debian-cloud, rocky-linux-cloud, ubuntu-os-cloud, centos-cloud, fedora-coreos-cloud, opensuse-cloud, oracle-linux-cloud, rhel-cloud, rhel-sap-cloud, rocky-linux-accelerator-cloud, suse-cloud, suse-sap-cloud, ubuntu-os-accelerator-images, ubuntu-os-pro-cloud, windows-cloud, windows-sql-cloud. Enabled by default, use --no-standard-images to disable. |


**Examples:**
```bash
To list all images in a project in table form, run:

    $ gcloud compute images list

To list the URIs of all images in a project, run:

    $ gcloud compute images list --uri

To list the names of images older than one year from oldest to newest (-P1Y
is an ISO8601 duration (https://en.wikipedia.org/wiki/ISO_8601)):

    $ gcloud compute images list --format="value(NAME)" \
        --filter="creationTimestamp < -P1Y"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/list)

---
### `gcloud compute images remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine image

Remove an IAM policy binding from the IAM policy of a Compute Engine image.
One binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud compute images remove-iam-policy-binding IMAGE --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image resource - The image for which to remove IAM policy binding from.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument image on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE
     ID of the image or fully qualified identifier for the image.

     To set the image attribute:
     + provide the argument image on the command line.
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
'roles/compute.securityAdmin' for the user 'test-user@gmail.com' with image
'my-image', run:

    $ gcloud compute images remove-iam-policy-binding my-image \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with image 'my-image', run:

    $ gcloud compute images remove-iam-policy-binding my-image \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/remove-iam-policy-binding)

---
### `gcloud compute images remove-labels`

Remove labels from Google Compute Engine images

gcloud compute images remove-labels removes labels from a Google Compute
Engine image.

**Synopsis:**
```
gcloud compute images remove-labels IMAGE_NAME
    (--all | --labels=KEY,[KEY,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[Exactly one of these must be specified:]_ Remove all labels from the resource. |
| `--labels` | KEY,[KEY,...] |  | _[Exactly one of these must be specified:]_ A comma-separated list of label keys to remove from the resource. |


**Examples:**
```bash
To remove existing labels with key k0 and k1 from 'example-image'

    $ gcloud compute images remove-labels example-image --labels=k0,k1

Labels can be used to identify the image and to filter them. To find a
image labeled with key-value pair k1, v2

    $ gcloud compute images list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute images describe example-image \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/remove-labels)

---
### `gcloud compute images set-iam-policy`

Set the IAM policy for a Compute Engine image

Sets the IAM policy for the given image as defined in a JSON or YAML file.

**Synopsis:**
```
gcloud compute images set-iam-policy IMAGE POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image resource - The image to set IAM policy for. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument image on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE
     ID of the image or fully qualified identifier for the image.

     To set the image attribute:
     + provide the argument image on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the image my-image:

    $ gcloud compute images set-iam-policy my-image policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/set-iam-policy)

---
### `gcloud compute images update`

Update a Compute Engine image

gcloud compute images update updates labels for a Compute Engine image.

**Synopsis:**
```
gcloud compute images update IMAGE_NAME [--architecture=ARCHITECTURE]
    [--description=DESCRIPTION] [--family=FAMILY]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_NAME
   Name of the disk image to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--architecture` | one of: ARM64, X86_64 |  | Specifies the architecture or processor type that this image can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. ARCHITECTURE must be one of: ARM64, X86_64. |
| `--description` | DESCRIPTION |  | An optional text description for the image. |
| `--family` | FAMILY |  | Name of the image family to use. If an image family is specified when you create an instance or disk, the latest non-deprecated image in the family is used. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k0 and k1 and remove labels with key k3, run:

    $ gcloud compute images update example-image \
        --update-labels=k0=value1,k1=value2 --remove-labels=k3

    k0 and k1 will be added as new labels if not already present.

Labels can be used to identify the image and to filter them like:

    $ gcloud compute images list --filter='labels.k1:value2'

To list only the labels when describing a resource, use --format:

    $ gcloud compute images describe example-image \
        --format="default(labels)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/images/update)

---
# gcloud compute migration

provides Migrate to Virtual Machines (VM migration) service functionality


## `gcloud compute migration image-imports` — imports images to Google Compute Engine from Google Cloud Storage
### `gcloud compute migration image-imports create`

Import Virtual Disk images to Google Compute Engine

gcloud compute migration image-imports create imports images such as VMWare
VMDK files and VHD files, from a Google Cloud Storage file (gs://...) to
Google Compute Engine, using the Migrate to Virtual Machines service API.
This command creates an Image Import resource with a nested Image Import
Job resource. The Image Import Job resource tracks the image import
progress. To use this command, you must enable VM Migration API in your
project.

**Synopsis:**
```
gcloud compute migration image-imports create
    (IMAGE_IMPORT_NAME : --location=LOCATION) --source-file=SOURCE_FILE
    [--additional-licenses=[ADDITIONAL_LICENSES,...]]
    [--description=DESCRIPTION] [--family-name=FAMILY_NAME]
    [--image-name=IMAGE_NAME] [--kms-key=KMS_KEY]
    [--labels=[KEY=VALUE,...]] [--single-region-storage]
    [--target-project=TARGET_PROJECT]
    [--adaptation-modifiers=ADAPTATION_MODIFIERS
      --boot-conversion=BOOT_CONVERSION
      --generalize --license-type=LICENSE_TYPE --rootfs-uuid=ROOTFS_UUID
      | [--skip-os-adaptation
      : --guest-os-features=[GUEST_OS_FEATURES,...]]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image import resource - The Image Import resource you want to create. This
would be the image name if --image-name is not given. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument image_import_name on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE_IMPORT_NAME
     ID of the image_import or fully qualified identifier for the
     image_import.

     To set the image_import_name attribute:
     + provide the argument image_import_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Resource location.

     To set the location attribute:
     + provide the argument image_import_name on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-file` | SOURCE_FILE |  | The path to the Google Cloud Storage file from which the image should be imported. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-licenses` | [ADDITIONAL_LICENSES,...] |  | Comma-separated list of the additional licenses to assign to the image. |
| `--description` | DESCRIPTION |  | A description of the image. |
| `--family-name` | FAMILY_NAME |  | The name of the image family to which the new image belongs. |
| `--image-name` | IMAGE_NAME |  | The name of the image that will be imported to Google Compute Engine. Default is the Image Import name. |
| `--kms-key` | KMS_KEY |  | Fully qualified identifier for the Cloud KMS (Key Management Service) cryptokey that will be used to protect the image. |
| `--labels` | [KEY=VALUE,...] |  | A map of labels to associate with the image. |
| `--single-region-storage` |  |  | If true, the location of the imported image will be the region of the import job. Otherwise the closest multi-region is selected. Default is false. |
| `--target-project` | TARGET_PROJECT |  | The target project resource path to which the image will be imported. Default is the customer project. To get a list of the target projects run the gcloud alpha migration vms target-projects list command. |


**Examples:**
```bash
To import my-ubuntu22.04.vmdk from my-images-bucket to my-target-project in
us-central1, create my-image-import resource in my-project in us-central1.
Run:        $ gcloud compute migration image-imports create my-image-import \
        --source-file=gs://my-images-bucket/my-ubuntu22.04.vmdk \
        --image-name=my-ubuntu-image --location=us-central1 \
        --target-project=projects/my-project/locations/global/\
    targetProjects/my-target-project --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/image-imports/create)

---
### `gcloud compute migration image-imports delete`

Delete an Image Import resource

gcloud compute migration image-imports delete deletes an Image Import
resource. To use this command, you must enable VM Migration API in your
project.

This command does not delete any images imported to Google Compute Engine.

**Synopsis:**
```
gcloud compute migration image-imports delete
    (IMAGE_IMPORT_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image import resource - The Image Import resource you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument image_import_name on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE_IMPORT_NAME
     ID of the image_import or fully qualified identifier for the
     image_import.

     To set the image_import_name attribute:
     + provide the argument image_import_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Resource location.

     To set the location attribute:
     + provide the argument image_import_name on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To delete my-image-import resource in us-central1 in the default project,
run:        $ gcloud compute migration image-imports delete my-image-import \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/image-imports/delete)

---
### `gcloud compute migration image-imports describe`

Describe an Image Import

gcloud compute migration image-imports describe describes an Image Import
resource with a nested Image Import Job. The Image Import Job resource
tracks the image import progress. To use this command, you must enable VM
Migration API in your project.

**Synopsis:**
```
gcloud compute migration image-imports describe
    (IMAGE_IMPORT_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image import resource - The Image Import you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument image_import_name on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE_IMPORT_NAME
     ID of the image_import or fully qualified identifier for the
     image_import.

     To set the image_import_name attribute:
     + provide the argument image_import_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Resource location.

     To set the location attribute:
     + provide the argument image_import_name on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To describe my-image-import resource in us-central1 in the default project,
run:        $ gcloud compute migration image-imports describe my-image-import \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/image-imports/describe)

---
### `gcloud compute migration image-imports list`

List Image Imports

gcloud compute migration image-imports list prints a detailed list of Image
Import resources. To use this command, you must enable VM Migration API in
your project.

**Synopsis:**
```
gcloud compute migration image-imports list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/region. |


**Examples:**
```bash
To list the Image Import resources in us-central1 in the default project,
run:        $ gcloud compute migration image-imports list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/image-imports/list)

---

## `gcloud compute migration machine-image-imports` — imports machine images to Google Compute Engine from Google Cloud Storage
### `gcloud compute migration machine-image-imports create`

Import machine images to Google Compute Engine

gcloud compute migration machine-image-imports create Imports machine
images such as OVA and OVF files, from a Google Cloud Storage file
(gs://...) to Google Compute Engine, using the Migrate to Virtual Machines
service API. This command creates an Image Import resource with a nested
Image Import Job resource. The Image Import Job resource tracks the image
import progress. To use this command, you must enable VM Migration API in
your project.

**Synopsis:**
```
gcloud compute migration machine-image-imports create
    (IMAGE_IMPORT_NAME : --location=LOCATION) --source-file=SOURCE_FILE
    [--additional-licenses=[ADDITIONAL_LICENSES,...]]
    [--description=DESCRIPTION] [--kms-key=KMS_KEY]
    [--labels=[KEY=VALUE,...]] [--machine-image-name=MACHINE_IMAGE_NAME]
    [--machine-type=MACHINE_TYPE]
    [--network-interface=[network=NETWORK],
      [networkTier=NETWORKTIER],[subnetwork=SUBNETWORK]]
    [--single-region-storage] [--tags=[TAGS,...]]
    [--target-project=TARGET_PROJECT]
    [--enable-integrity-monitoring --enable-vtpm --secure-boot=SECURE_BOOT]
    [--scopes=[SCOPES,...] --service-account=SERVICE_ACCOUNT]
    [--skip-os-adaptation | --adaptation-modifiers=ADAPTATION_MODIFIERS
      --boot-conversion=BOOT_CONVERSION
      --generalize --license-type=LICENSE_TYPE --rootfs-uuid=ROOTFS_UUID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image import resource - The Image Import resource you want to create. This
would be the machine image name if --machine-image-name is not given. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument image_import_name on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE_IMPORT_NAME
     ID of the image_import or fully qualified identifier for the
     image_import.

     To set the image_import_name attribute:
     + provide the argument image_import_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Resource location.

     To set the location attribute:
     + provide the argument image_import_name on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-file` | SOURCE_FILE |  | The path to the Google Cloud Storage file from which the image should be imported. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-licenses` | [ADDITIONAL_LICENSES,...] |  | Comma-separated list of the additional licenses to assign to the machine image. |
| `--description` | DESCRIPTION |  | A description of the machine image. |
| `--kms-key` | KMS_KEY |  | Fully qualified identifier for the Cloud KMS (Key Management Service) cryptokey that will be used to protect the image. |
| `--labels` | [KEY=VALUE,...] |  | A map of labels to associate with the machine image. |
| `--machine-image-name` | MACHINE_IMAGE_NAME |  | The name of the machine image that will be imported to Google Compute Engine. Default is the Image Import name. |
| `--machine-type` | MACHINE_TYPE |  | The machine type to create the machine image with. If not provided, the service will choose a relevant machine type series based on the information from the source image. |
| `--network-interface` | [network=NETWORK],[networkTier=NETWORKTIER],[subnetwork=SUBNETWORK] |  | The network interface to use for the instance created by the machine image. This is a dicionary with the following keys: * network: The network to use for this network interface. * subnetwork: The subnetwork to use for this network interface. * network-tier: The network tier to use for this network interface. This argument can be specified multiple times in case of multiple nics. |
| `--single-region-storage` |  |  | If true, the location of the imported machine image will be the region of the import job. Otherwise the closest multi-region is selected. Default is false. |
| `--tags` | [TAGS,...] |  | The tags to apply to the instance created by the machine image. |
| `--target-project` | TARGET_PROJECT |  | The target project resource path to which the machine image will be imported. Default is the host project. To get a list of the target projects run the gcloud alpha migration vms target-projects list command. |


**Examples:**
```bash
To import ub-14.04.5.ova from my-images-bucket to my-target-project in
us-central1, create my-image-import resource in my-project in us-central1.
Run:        $ gcloud compute migration machine-image-imports create \
        my-machine-image-import \
        --source-file=gs://my-images-bucket/ub-14.04.5.ova \
        --image-name=my-ubuntu-machine-image --location=us-central1 \
        --target-project=projects/my-project/locations/global/\
    targetProjects/my-target-project --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/machine-image-imports/create)

---
### `gcloud compute migration machine-image-imports delete`

Delete an Image Import resource

gcloud compute migration machine-image-imports delete deletes an Image
Import resource. To use this command, you must enable VM Migration API in
your project.

This command does not delete any machine images imported to Google Compute
Engine.

**Synopsis:**
```
gcloud compute migration machine-image-imports delete
    (IMAGE_IMPORT_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image import resource - The Image Import resource you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument image_import_name on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE_IMPORT_NAME
     ID of the image_import or fully qualified identifier for the
     image_import.

     To set the image_import_name attribute:
     + provide the argument image_import_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Resource location.

     To set the location attribute:
     + provide the argument image_import_name on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To delete my-image-import resource in us-central1 in the default project,
run:        $ gcloud compute migration machine-image-imports delete \
        my-image-import --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/machine-image-imports/delete)

---
### `gcloud compute migration machine-image-imports describe`

Describe an Image Import

gcloud compute migration machine-image-imports describe describes an Image
Import resource with a nested Image Import Job. The Image Import Job
resource tracks the image import progress. To use this command, you must
enable VM Migration API in your project.

**Synopsis:**
```
gcloud compute migration machine-image-imports describe
    (IMAGE_IMPORT_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Image import resource - The Image Import you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument image_import_name on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IMAGE_IMPORT_NAME
     ID of the image_import or fully qualified identifier for the
     image_import.

     To set the image_import_name attribute:
     + provide the argument image_import_name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Resource location.

     To set the location attribute:
     + provide the argument image_import_name on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To describe my-image-import resource in us-central1 in the default project,
run:        $ gcloud compute migration machine-image-imports describe \
        my-image-import --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/machine-image-imports/describe)

---
### `gcloud compute migration machine-image-imports list`

List Image Imports

gcloud compute migration machine-image-imports list prints a detailed list
of Image Import resources. To use this command, you must enable VM
Migration API in your project.

**Synopsis:**
```
gcloud compute migration machine-image-imports list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/region. |


**Examples:**
```bash
To list the Image Import resources in us-central1 in the default project,
run:        $ gcloud compute migration machine-image-imports list \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/machine-image-imports/list)

---

## `gcloud compute migration target-projects` — manage Target Projects
### `gcloud compute migration target-projects list`

List Target Projects

gcloud compute migration target-projects list lists Target Project
resources, which are required for setting the target project for migration.
Target projects are defined for each customer project in the global
location. To use this command, you must enable VM Migration API in your
project.

**Synopsis:**
```
gcloud compute migration target-projects list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the Target Project resources in the global location in the default
project, run:        $ gcloud compute migration target-projects list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/migration/target-projects/list)

---
# gcloud compute instances

read and manipulate Compute Engine virtual machine instances

### `gcloud compute instances add-access-config`

Create a Compute Engine virtual machine access configuration

gcloud compute instances add-access-config is used to create access
configurations for network interfaces of Compute Engine virtual machines.
This allows you to assign a public, external IP to a virtual machine.

**Synopsis:**
```
gcloud compute instances add-access-config INSTANCE_NAME
    [--access-config-name=ACCESS_CONFIG_NAME; default="external-nat"]
    [--address=ADDRESS]
    [--network-interface=NETWORK_INTERFACE; default="nic0"]
    [--network-tier=NETWORK_TIER] [--zone=ZONE]
    [--public-ptr | --no-public-ptr]
    [--public-ptr-domain=PUBLIC_PTR_DOMAIN | --no-public-ptr-domain]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-config-name` | ACCESS_CONFIG_NAME | external-nat | Specifies the name of the new access configuration. external-nat is used as the default if this flag is not provided. Since ONE_TO_ONE_NAT is currently the only access-config type, it is not recommended that you change this value. |
| `--address` | ADDRESS |  | Specifies the external IP address of the new access configuration. If this is not specified, then the service will choose an available ephemeral IP address. If an explicit IP address is given, then that IP address must be reserved by the project and not be in use by another resource. |
| `--network-interface` | NETWORK_INTERFACE | nic0 | Specifies the name of the network interface which contains the access configuration. If this is not provided, then "nic0" is used as the default. |
| `--network-tier` | one of: PREMIUM, STANDARD |  | Specifies the network tier of the access configuration. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To assign an public, externally accessible IP to a virtual machine named
example-instance in zone us-central1-a, run:

    $ gcloud compute instances add-access-config example-instance \
        --zone=us-central1-a

To assign the specific, reserved public IP address 123.456.789.123 to the
virtual machine, run:

    $ gcloud compute instances add-access-config example-instance \
        --zone=us-central1-a --address=123.456.789.123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-access-config)

---
### `gcloud compute instances add-iam-policy-binding`

Add IAM policy binding to a Compute Engine instance

Add an IAM policy binding to the IAM policy of a Compute Engine instance.
One binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud compute instances add-iam-policy-binding (INSTANCE : --zone=ZONE)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance for which to add IAM policy binding to.
The arguments in this group can be used to specify the attributes of this
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

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
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
for the user 'test-user@gmail.com' with instance 'my-instance' and zone
'ZONE', run:

    $ gcloud compute instances add-iam-policy-binding my-instance \
        --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with instance 'my-instance' and zone 'ZONE', run:

    $ gcloud compute instances add-iam-policy-binding my-instance \
        --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-iam-policy-binding)

---
### `gcloud compute instances add-labels`

Add labels to Google Compute Engine virtual machine instances

gcloud compute instances add-labels adds labels to a Google Compute Engine
virtual machine instance.

**Synopsis:**
```
gcloud compute instances add-labels INSTANCE_NAME --labels=[KEY=VALUE,...]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | A list of labels to add. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add key-value pairs k0=v0 and k1=v1 to 'example-instance'

    $ gcloud compute instances add-labels example-instance \
        --labels=k0=v0,k1=v1

Labels can be used to identify the instance and to filter them. To find a
instance labeled with key-value pair k1, v2

    $ gcloud compute instances list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute instances describe example-instance \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-labels)

---
### `gcloud compute instances add-metadata`

Add or update instance metadata

gcloud compute instances add-metadata can be used to add or update the
metadata of a virtual machine instance. Every instance has access to a
metadata server that can be used to query metadata that has been set
through this tool. For information on metadata, see
https://cloud.google.com/compute/docs/metadata

Only metadata keys that are provided are mutated. Existing metadata entries
will remain unaffected.

In order to retrieve custom metadata, run:

    $ gcloud compute instances describe example-instance --zone
    us-central1-a --format="value(metadata)"

where example-instance is the name of the virtual machine instance you're
querying custom metadata from. For more information about querying custom
instance or project metadata through the Cloud Platform Console or the API,
see
https://cloud.google.com/compute/docs/storing-retrieving-metadata#querying_custom_metadata.

If you are using this command to manage SSH keys for your project, please
note the risks
(https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys#risks)
of manual SSH key management as well as the required format for SSH key
metadata, available at
https://cloud.google.com/compute/docs/instances/adding-removing-ssh-keys.

**Synopsis:**
```
gcloud compute instances add-metadata INSTANCE_NAME
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to set metadata on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. Each metadata key must be unique and have a max of 128 bytes in length. Each value must have a max of 256 KB in length. Multiple arguments can be passed to this flag, e.g., --metadata key-1=value-1,key-2=value-2,key-3=value-3. The combined total size for all metadata entries is 512 KB. In images that have Compute Engine tools installed on them, such as the official images (https://cloud.google.com/compute/docs/images), the following metadata keys have special meanings: startup-script Specifies a script that will be executed by the instances once they start running. For convenience, --metadata-from-file can be used to pull the value from a file. startup-script-url Same as startup-script except that the script contents are pulled from a publicly-accessible location on the web. For startup scripts on Windows instances, the following metadata keys have special meanings: windows-startup-script-url, windows-startup-script-cmd, windows-startup-script-bat, windows-startup-script-ps1, sysprep-specialize-script-url, sysprep-specialize-script-cmd, sysprep-specialize-script-bat, and sysprep-specialize-script-ps1. For more information, see Running startup scripts (https://cloud.google.com/compute/docs/startupscript). At least one of [--metadata] or [--metadata-from-file] is required. |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | Same as --metadata except that the value for the entry will be read from a local file. This is useful for values that are too large such as startup-script contents. At least one of [--metadata] or [--metadata-from-file] is required. |
| `--zone` | ZONE |  | Zone of the instance to set metadata on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add metadata under key important-data to an instance named
test-instance, run:

    $ gcloud compute instances add-metadata test-instance \
        --metadata=important-data="2 plus 2 equals 4"

To add multiple key-value pairs at once, separate them with commas:

    $ gcloud compute instances add-metadata test-instance \
        --metadata=important-data="2 plus 2 equals \
    4",unimportant-data=zero
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-metadata)

---
### `gcloud compute instances add-resource-policies`

Add resource policies to Compute Engine VM instances

gcloud compute instances add-resource-policies adds resource policies to
Compute Engine virtual instances. These policies define time windows in
which live migrations take place.

**Synopsis:**
```
gcloud compute instances add-resource-policies INSTANCE_NAME
    --resource-policies=[RESOURCE_POLICY,...] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to add resource policies to. For details on valid
   instance names, refer to the criteria documented under the field 'name'
   at: https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be added to the instance. The policies must exist in the same region as the instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to add resource policies to. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add resource policy pol1 to instance inst1, run this:

    $ gcloud compute instances add-resource-policies inst1 \
        --resource-policies=pol1

For information on how to create resource policies, see:

    $ gcloud compute resource-policies create --help
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-resource-policies)

---
### `gcloud compute instances add-tags`

Add tags to Compute Engine virtual machine instances

gcloud compute instances add-tags is used to add tags to Compute Engine
virtual machine instances.

Tags can be used to identify the instances when adding network firewall
rules. Tags can also be used to get firewall rules that already exist to be
applied to the instance. See gcloud compute firewall-rules create(1) for
more details.

To list instances with their respective status and tags, run:

    $ gcloud compute instances list \
        --format="table(name,status,tags.list())"

To list instances tagged with a specific tag, tag1, run:

    $ gcloud compute instances list --filter='tags:tag1'

**Synopsis:**
```
gcloud compute instances add-tags INSTANCE_NAME --tags=TAG,[TAG,...]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to set tags on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tags` | TAG,[TAG,...] |  | Specifies strings to be attached to the instance for later identifying the instance when adding network firewall rules. Multiple tags can be attached by repeating this flag. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to set tags on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add tags tag-1 and tag-2 to an instance named test-instance, run:

    $ gcloud compute instances add-tags test-instance --tags=tag-1,tag-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/add-tags)

---
### `gcloud compute instances attach-disk`

Attach a disk to an instance

gcloud compute instances attach-disk is used to attach a disk to an
instance. For example,

    $ gcloud compute instances attach-disk example-instance \
        --disk DISK --zone us-central1-a

attaches the disk named 'DISK' to the instance named 'example-instance' in
zone us-central1-a.

After you create and attach a new disk to an instance, you must format and
mount
(https://cloud.google.com/compute/docs/disks/add-persistent-disk#formatting)
the disk so that the operating system can use the available storage space.
You can attach an existing non-boot disk to more than one instance. For
more information, see Share a disk between VMs.

**Synopsis:**
```
gcloud compute instances attach-disk INSTANCE_NAME --disk=DISK [--boot]
    [--csek-key-file=FILE] [--device-name=DEVICE_NAME]
    [--disk-scope=DISK_SCOPE; default="zonal"] [--force-attach]
    [--interface=INTERFACE] [--mode=MODE; default="rw"] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disk` | DISK |  | The name of the disk to attach to the instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--boot` |  |  | Attach the disk to the instance as a boot disk. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine resources to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--device-name` | DEVICE_NAME |  | An optional name that indicates the disk name the guest operating system will see. (Note: Device name does not correspond to mounted volume name). Must match the disk name if the disk is going to be mounted to a container with --container-mount-disk (alpha feature). |
| `--disk-scope` | one of: regional The disk specified in --disk is interpreted as a regional disk in the same region as the instance | zonal | The scope of the disk. DISK_SCOPE must be one of: regional The disk specified in --disk is interpreted as a regional disk in the same region as the instance. Ignored if a full URI is provided to the --disk flag. zonal The disk specified in --disk is interpreted as a zonal disk in the same zone as the instance. Ignored if a full URI is provided to the --disk flag. |
| `--force-attach` |  |  | Attach the disk to the instance even if it is currently attached to another instance. The attachment will succeed even if detaching from the previous instance fails at first. The server will continue trying to detach the disk from the previous instance in the background. |
| `--interface` | INTERFACE |  | The interface of the disk. INTERFACE must be one of: NVME NVME SCSI SCSI |
| `--mode` | one of: ro Read-only | rw | Specifies the mode of the disk. MODE must be one of: ro Read-only. rw Read-write. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To attach a disk named 'my-disk' as a boot disk to an instance named
'my-instance', run:

    $ gcloud compute instances attach-disk my-instance --disk=my-disk \
        --boot

To attach a device named 'my-device' for read-only access to an instance
named 'my-instance', run:

    $ gcloud compute instances attach-disk my-instance \
        --device-name=my-device --mode=ro
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/attach-disk)

---
### `gcloud compute instances create`

Create Compute Engine virtual machine instances

gcloud compute instances create facilitates the creation of Compute Engine
virtual machines.

When an instance is in RUNNING state and the system begins to boot, the
instance creation is considered finished, and the command returns with a
list of new virtual machines. Note that you usually cannot log into a new
instance until it finishes booting. Check the progress of an instance using
gcloud compute instances get-serial-port-output.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute instances create INSTANCE_NAMES [INSTANCE_NAMES ...]
    [--accelerator=[count=COUNT],[type=TYPE]] [--async]
    [--availability-domain=AVAILABILITY_DOMAIN]
    [--no-boot-disk-auto-delete]
    [--boot-disk-device-name=BOOT_DISK_DEVICE_NAME]
    [--boot-disk-interface=BOOT_DISK_INTERFACE]
    [--boot-disk-provisioned-iops=BOOT_DISK_PROVISIONED_IOPS]
    [--boot-disk-provisioned-throughput=BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--boot-disk-size=BOOT_DISK_SIZE] [--boot-disk-type=BOOT_DISK_TYPE]
    [--can-ip-forward] [--create-disk=[PROPERTY=VALUE,...]]
    [--csek-key-file=FILE] [--deletion-protection]
    [--description=DESCRIPTION]
    [--discard-local-ssds-at-termination-timestamp=DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP]
    [--disk=[auto-delete=AUTO-DELETE],[boot=BOOT],[device-name=DEVICE-NAME],
      [force-attach=FORCE-ATTACH],
      [interface=INTERFACE],[mode=MODE],[name=NAME],[scope=SCOPE]]
    [--enable-display-device] [--[no-]enable-nested-virtualization]
    [--[no-]enable-uefi-networking] [--erase-windows-vss-signature]
    [--external-ipv6-address=EXTERNAL_IPV6_ADDRESS]
    [--external-ipv6-prefix-length=EXTERNAL_IPV6_PREFIX_LENGTH]
    [--host-error-timeout-seconds=HOST_ERROR_TIMEOUT_SECONDS]
    [--hostname=HOSTNAME]
    [--instance-termination-action=INSTANCE_TERMINATION_ACTION]
    [--internal-ipv6-address=INTERNAL_IPV6_ADDRESS]
    [--internal-ipv6-prefix-length=INTERNAL_IPV6_PREFIX_LENGTH]
    [--ipv6-network-tier=IPV6_NETWORK_TIER]
    [--ipv6-public-ptr-domain=IPV6_PUBLIC_PTR_DOMAIN]
    [--key-revocation-action-type=POLICY] [--labels=[KEY=VALUE,...]]
    [--local-ssd=[device-name=DEVICE-NAME],
      [interface=INTERFACE],[size=SIZE]]
    [--local-ssd-recovery-timeout=LOCAL_SSD_RECOVERY_TIMEOUT]
    [--machine-type=MACHINE_TYPE] [--maintenance-policy=MAINTENANCE_POLICY]
    [--max-run-duration=MAX_RUN_DURATION]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]]
    [--min-cpu-platform=PLATFORM] [--min-node-cpu=MIN_NODE_CPU]
    [--network=NETWORK] [--network-interface=[PROPERTY=VALUE,...]]
    [--network-performance-configs=[PROPERTY=VALUE,...]]
    [--network-tier=NETWORK_TIER] [--node-project=NODE_PROJECT]
    [--performance-monitoring-unit=PERFORMANCE_MONITORING_UNIT]
    [--preemptible]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--private-network-ip=PRIVATE_NETWORK_IP]
    [--provisioning-model=PROVISIONING_MODEL]
    [--request-valid-for-duration=REQUEST_VALID_FOR_DURATION]
    [--no-require-csek-key-create]
    [--resource-manager-tags=[KEY=VALUE,...]]
    [--resource-policies=[RESOURCE_POLICY,...]] [--no-restart-on-failure]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--[no-]skip-guest-os-shutdown]
    [--source-instance-template=SOURCE_INSTANCE_TEMPLATE]
    [--source-machine-image=SOURCE_MACHINE_IMAGE]
    [--source-machine-image-csek-key-file=FILE] [--stack-type=STACK_TYPE]
    [--subnet=SUBNET] [--tags=TAG,[TAG,...]]
    [--termination-time=TERMINATION_TIME]
    [--threads-per-core=THREADS_PER_CORE] [--turbo-mode=TURBO_MODE]
    [--visible-core-count=VISIBLE_CORE_COUNT] [--zone=ZONE]
    [--address=ADDRESS | --no-address]
    [--boot-disk-kms-key=BOOT_DISK_KMS_KEY
      : --boot-disk-kms-keyring=BOOT_DISK_KMS_KEYRING
      --boot-disk-kms-location=BOOT_DISK_KMS_LOCATION
      --boot-disk-kms-project=BOOT_DISK_KMS_PROJECT]
    [--confidential-compute
      | --confidential-compute-type=CONFIDENTIAL_COMPUTE_TYPE]
    [--custom-cpu=CUSTOM_CPU --custom-memory=CUSTOM_MEMORY
      : --custom-extensions --custom-vm-type=CUSTOM_VM_TYPE]
    [--image-family-scope=IMAGE_FAMILY_SCOPE
      --image-project=IMAGE_PROJECT --image=IMAGE
      | --image-family=IMAGE_FAMILY | --source-snapshot=SOURCE_SNAPSHOT]
    [--instance-kms-key=INSTANCE_KMS_KEY
      : --instance-kms-keyring=INSTANCE_KMS_KEYRING
      --instance-kms-location=INSTANCE_KMS_LOCATION
      --instance-kms-project=INSTANCE_KMS_PROJECT]
    [--node=NODE | --node-affinity-file=PATH_TO_FILE
      | --node-group=NODE_GROUP] [--public-ptr | --no-public-ptr]
    [--public-ptr-domain=PUBLIC_PTR_DOMAIN | --no-public-ptr-domain]
    [--reservation=RESERVATION
      --reservation-affinity=RESERVATION_AFFINITY; default="any"]
    [--scopes=[SCOPE,...] | --no-scopes]
    [--service-account=SERVICE_ACCOUNT | --no-service-account]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to create. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Attaches accelerators (e.g. GPUs) to the instances. type The specific type (e.g. nvidia-tesla-t4 for NVIDIA T4) of accelerator to attach to the instances. Use 'gcloud compute accelerator-types list' to learn about all available accelerator types. count Number of accelerators to attach to each instance. The default value is 1. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--availability-domain` | AVAILABILITY_DOMAIN |  | Specifies the availability domain that this VM instance should be scheduled on. The number of availability domains that a VM can be scheduled on is specified when you create the spread placement policy. Specify a value from 1 to the number of domains that are available in your placement policy. |
| `--boot-disk-auto-delete` |  |  | Automatically delete boot disks when their instances are deleted. Enabled by default, use --no-boot-disk-auto-delete to disable. |
| `--boot-disk-device-name` | BOOT_DISK_DEVICE_NAME |  | The name the guest operating system will see for the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). |
| `--boot-disk-interface` | BOOT_DISK_INTERFACE |  | Indicates the interface to use for the boot disk. The value must be one of the following: * SCSI * NVME |
| `--boot-disk-provisioned-iops` | BOOT_DISK_PROVISIONED_IOPS |  | Indicates how many IOPS to provision for the disk. This sets the number of I/O operations per second that the disk can handle. |
| `--boot-disk-provisioned-throughput` | BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates how much throughput to provision for the disk. This sets the number of throughput mb per second that the disk can handle. |
| `--boot-disk-size` | BOOT_DISK_SIZE |  | The size of the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. Disk size must be a multiple of 1 GB. Default size unit is GB. |
| `--boot-disk-type` | BOOT_DISK_TYPE |  | The type of the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). To get a list of available disk types, run $ gcloud compute disk-types list. |
| `--can-ip-forward` |  |  | If provided, allows the instances to send and receive packets with non-matching destination or source IP addresses. |
| `--create-disk` | [PROPERTY=VALUE,...] |  | Creates and attaches persistent disks to the instances. name Specifies the name of the disk. This option cannot be specified if more than one instance is being created. description Optional textual description for the disk being created. mode Specifies the mode of the disk. Supported options are ro for read-only and rw for read-write. If omitted, rw is used as a default. image Specifies the name of the image that the disk will be initialized with. A new disk will be created based on the given image. To view a list of public images and projects, run $ gcloud compute images list. It is best practice to use image when a specific version of an image is needed. If both image and image-family flags are omitted a blank disk will be created. image-family The image family for the operating system that the boot disk will be initialized with. Compute Engine offers multiple Linux distributions, some of which are available as both regular and Shielded VM images. When a family is specified instead of an image, the latest non-deprecated image associated with that family is used. It is best practice to use --image-family when the latest version of an image is needed. image-project The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available image projects can be generated by running gcloud compute images list. + If specifying one of our public images, image-project must be provided. + If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. + If not specified and either image or image-family is provided, the current default project is used. size The size of the disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. Disk size must be a multiple of 1 GB. If not specified, the default image size will be used for the new disk. type The type of the disk. To get a list of available disk types, run $ gcloud compute disk-types list. The default disk type is pd-standard. device-name An optional name to display the disk name in the guest operating system. If omitted, a device name of the form persistent-disk-N is used. provisioned-iops Indicates how many IOPS to provision for the disk. This sets the number of I/O operations per second that the disk can handle. Value must be between 10,000 and 120,000. provisioned-throughput Indicates how much throughput to provision for the disk. This sets the number of throughput mb per second that the disk can handle. disk-resource-policy Resource policy to apply to the disk. Specify a full or partial URL. For example: + https://www.googleapis.com/compute/v1/projects/my-project/regions/us-central1/resourcePolicies/my-resource-policy + projects/my-project/regions/us-central1/resourcePolicies/my-resource-policy For more information, see the following docs: + https://cloud.google.com/sdk/gcloud/reference/beta/compute/resource-policies/ + https://cloud.google.com/compute/docs/disks/scheduled-snapshots auto-delete If yes, this persistent disk will be automatically deleted when the instance is deleted. However, if the disk is later detached from the instance, this option won't apply. The default value for this is yes. architecture Specifies the architecture or processor type that this disk can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. storage-pool The name of the storage pool in which the new disk is created. The new disk and the storage pool must be in the same location. interface The interface to use with the disk. The value must be one of the following: + SCSI + NVME boot If yes, indicates that this is a boot disk. The instance will use the first partition of the disk for its root file system. The default value for this is no. kms-key Fully qualified Cloud KMS cryptokey name that will protect the disk. This can either be the fully qualified path or the name. The fully qualified Cloud KMS cryptokey name format is: projects/<kms-project>/locations/<kms-location>/keyRings/<kms-keyring>/ cryptoKeys/<key-name>. If the value is not fully qualified then kms-location, kms-keyring, and optionally kms-project are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. kms-project Project that contains the Cloud KMS cryptokey that will protect the disk. If the project is not specified then the project where the disk is being created will be used. If this flag is set then key-location, kms-keyring, and kms-key are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. kms-location Location of the Cloud KMS cryptokey to be used for protecting the disk. All Cloud KMS cryptokeys are reside in a 'location'. To get a list of possible locations run 'gcloud kms locations list'. If this flag is set then kms-keyring and kms-key are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. kms-keyring The keyring which contains the Cloud KMS cryptokey that will protect the disk. If this flag is set then kms-location and kms-key are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. source-snapshot The source disk snapshot that will be used to create the disk. You can provide this as a full URL to the snapshot or just the snapshot name. For example, the following are valid values: + https://compute.googleapis.com/compute/v1/projects/myproject/global/snapshots/snapshot + snapshot confidential-compute If yes, the disk is created in confidential mode. The default value is no. Encryption with a Cloud KMS key is required to enable this option. replica-zones Required for each regional disk associated with the instance. Specify the URLs of the zones where the disk should be replicated to. You must provide exactly two replica zones, and one zone must be the same as the instance zone. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine resources to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--deletion-protection` |  |  | Enables deletion protection for the instance. |
| `--description` | DESCRIPTION |  | Specifies a textual description of the instances. |
| `--discard-local-ssds-at-termination-timestamp` | DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP |  | Required to be set to true and only allowed for VMs that have one or more local SSDs, use --instance-termination-action=STOP, and use either --max-run-duration or --termination-time. This flag indicates the value that you want Compute Engine to use for the --discard-local-ssd flag in the automatic gcloud compute instances stop command. This flag only supports the true value, which discards local SSD data when automatically stopping this VM during its terminationTimestamp. For more information about the --discard-local-ssd flag, see https://cloud.google.com/compute/docs/disks/local-ssd#stop_instance. |
| `--disk` | [auto-delete=AUTO-DELETE],[boot=BOOT],[device-name=DEVICE-NAME],[force-attach=FORCE-ATTACH],[interface=INTERFACE],[mode=MODE],[name=NAME],[scope=SCOPE] |  | Attaches an existing disk to the instances. name The disk to attach to the instances. If you create more than one instance, you can only attach a disk in read-only mode. By default, you attach a zonal disk located in the same zone of the instance. If you want to attach a regional disk, you must specify the disk using its URI; for example, projects/myproject/regions/us-central1/disks/my-regional-disk. mode The mode of the disk. Supported options are ro for read-only mode and rw for read-write mode. If omitted, rw is used as a default value. If you use rw when creating more than one instance, you encounter errors. boot If set to yes, you attach a boot disk. The virtual machine then uses the first partition of the disk for the root file systems. The default value for this is no. device-name An optional name to display the disk name in the guest operating system. If omitted, a device name of the form persistent-disk-N is used. auto-delete If set to yes, the persistent disk is automatically deleted when the instance is deleted. However, if you detach the disk from the instance, deleting the instance doesn't delete the disk. The default value is yes. interface The interface to use for the disk. The value must be one of the following: + SCSI + NVME scope Can be zonal or regional. If zonal, the disk is interpreted as a zonal disk in the same zone as the instance (default). If regional, the disk is interpreted as a regional disk in the same region as the instance. The default value for this is zonal. force-attach If yes, this persistent disk will force-attached to the instance even it is already attached to another instance. The default value is 'no'. |
| `--enable-display-device` |  |  | Enable a display device on VM instances. Disabled by default. |
| `--[no-]enable-nested-virtualization` |  |  | If set to true, enables nested virtualization for the instance. Use --enable-nested-virtualization to enable and --no-enable-nested-virtualization to disable. |
| `--[no-]enable-uefi-networking` |  |  | If set to true, enables UEFI networking for the instance creation. Use --enable-uefi-networking to enable and --no-enable-uefi-networking to disable. |
| `--erase-windows-vss-signature` |  |  | Specifies whether the disk restored from source snapshots or source machine image should erase Windows specific VSS signature. See https://cloud.google.com/sdk/gcloud/reference/compute/disks/snapshot#--guest-flush |
| `--external-ipv6-address` | EXTERNAL_IPV6_ADDRESS |  | Assigns the given external IPv6 address to the instance that is created. The address must be the first IP address in the range. This option can be used only when creating a single instance. |
| `--external-ipv6-prefix-length` | EXTERNAL_IPV6_PREFIX_LENGTH |  | The prefix length of the external IPv6 address range. This field should be used together with --external-ipv6-address. Only the /96 IP address range is supported, and the default value is 96. |
| `--host-error-timeout-seconds` | HOST_ERROR_TIMEOUT_SECONDS |  | The timeout in seconds for host error detection. The value must be set with 30 second increments, with a range of 90 to 330 seconds. If unset, the default behavior of the host error recovery is used. |
| `--hostname` | HOSTNAME |  | Specify the hostname of the instance to be created. The specified hostname must be RFC1035 compliant. If hostname is not specified, the default hostname is [INSTANCE_NAME].c.[PROJECT_ID].internal when using the global DNS, and [INSTANCE_NAME].[ZONE].c.[PROJECT_ID].internal when using zonal DNS. |
| `--instance-termination-action` | one of: DELETE Permanently delete the VM |  | Specifies the termination action that will be taken upon VM preemption (--provisioning-model=SPOT) or automatic instance termination (--max-run-duration or --termination-time). INSTANCE_TERMINATION_ACTION must be one of: DELETE Permanently delete the VM. STOP Default only for Spot VMs. Stop the VM without preserving memory. The VM can be restarted later. |
| `--internal-ipv6-address` | INTERNAL_IPV6_ADDRESS |  | Assigns the given internal IPv6 address or range to the instance that is created. The address must be the first IP address in the range or from a /96 IP address range. This option can be used only when creating a single instance. |
| `--internal-ipv6-prefix-length` | INTERNAL_IPV6_PREFIX_LENGTH |  | Optional field that indicates the prefix length of the internal IPv6 address range. It should be used together with --internal-ipv6-address. Only /96 IP address range is supported and the default value is 96. If not set, either the prefix length from --internal-ipv6-address will be used or the default value of 96 will be assigned. |
| `--ipv6-network-tier` | IPV6_NETWORK_TIER |  | Specifies the IPv6 network tier that will be used to configure the instance network interface IPv6 access config. IPV6_NETWORK_TIER must be (only one value is supported): PREMIUM High quality, Google-grade network tier. |
| `--ipv6-public-ptr-domain` | IPV6_PUBLIC_PTR_DOMAIN |  | Assigns a custom PTR domain for the external IPv6 in the IPv6 access configuration of instance. If unspecified or specified to be an empty string, the default PTR record will be used. This option can only be specified for the default network interface, nic0. |
| `--key-revocation-action-type` | one of: none No operation is performed |  | Specifies the behavior of the instance when the KMS key of one of its attached disks is revoked. The default is none. POLICY must be one of: none No operation is performed. stop The instance is stopped when the KMS key of one of its attached disks is revoked. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--local-ssd` | [device-name=DEVICE-NAME],[interface=INTERFACE],[size=SIZE] |  | Attaches a local SSD to the instances. device-name Optional. A name that indicates the disk name the guest operating system will see. Can only be specified if interface is SCSI. If omitted, a device name of the form local-ssd-N will be used. interface Optional. The kind of disk interface exposed to the VM for this SSD. Valid values are SCSI and NVME. SCSI is the default and is supported by more guest operating systems. NVME might provide higher performance. size Optional. The only valid value is 375GB. Specify the --local-ssd flag multiple times if you need multiple 375GB local SSD partitions. You can specify a maximum of 24 local SSDs for a maximum of 9TB attached to an instance. |
| `--local-ssd-recovery-timeout` | LOCAL_SSD_RECOVERY_TIMEOUT |  | Specifies the maximum amount of time a Local Ssd Vm should wait while recovery of the Local Ssd state is attempted. Its value should be in between 0 and 168 hours with hour granularity and the default value being 1 hour. |
| `--machine-type` | MACHINE_TYPE |  | Specifies the machine type used for the instances. To get a list of available machine types, run 'gcloud compute machine-types list'. If unspecified, the default type is n1-standard-1. |
| `--maintenance-policy` | one of: MIGRATE The instances should be migrated to a new host |  | Specifies the behavior of the VMs when their host machines undergo maintenance. The default is MIGRATE. For more information, see https://cloud.google.com/compute/docs/instances/host-maintenance-options. MAINTENANCE_POLICY must be one of: MIGRATE The instances should be migrated to a new host. This will temporarily impact the performance of instances during a migration event. TERMINATE The instances should be terminated. |
| `--max-run-duration` | MAX_RUN_DURATION |  | Limits how long this VM instance can run, specified as a duration relative to the last time when the VM began running. Format the duration, MAX_RUN_DURATION, as the number of days, hours, minutes, and seconds followed by d, h, m, and s respectively. For example, specify 30m for a duration of 30 minutes or specify 1d2h3m4s for a duration of 1 day, 2 hours, 3 minutes, and 4 seconds. Alternatively, to specify a timestamp, use --termination-time instead. If neither --max-run-duration nor --termination-time is specified (default), the VM instance runs until prompted by a user action or system event. If either is specified, the VM instance is scheduled to be automatically terminated at the VM's termination timestamp (terminationTimestamp) using the action specified by --instance-termination-action. Note: The terminationTimestamp is removed whenever the VM is stopped or suspended and redefined whenever the VM is rerun. For --max-run-duration specifically, the terminationTimestamp is the sum of MAX_RUN_DURATION and the time when the VM last entered the RUNNING state, which changes whenever the VM is rerun. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. Each metadata key must be unique and have a max of 128 bytes in length. Each value must have a max of 256 KB in length. Multiple arguments can be passed to this flag, e.g., --metadata key-1=value-1,key-2=value-2,key-3=value-3. The combined total size for all metadata entries is 512 KB. In images that have Compute Engine tools installed on them, such as the official images (https://cloud.google.com/compute/docs/images), the following metadata keys have special meanings: startup-script Specifies a script that will be executed by the instances once they start running. For convenience, --metadata-from-file can be used to pull the value from a file. startup-script-url Same as startup-script except that the script contents are pulled from a publicly-accessible location on the web. For startup scripts on Windows instances, the following metadata keys have special meanings: windows-startup-script-url, windows-startup-script-cmd, windows-startup-script-bat, windows-startup-script-ps1, sysprep-specialize-script-url, sysprep-specialize-script-cmd, sysprep-specialize-script-bat, and sysprep-specialize-script-ps1. For more information, see Running startup scripts (https://cloud.google.com/compute/docs/startupscript). |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | Same as --metadata except that the value for the entry will be read from a local file. This is useful for values that are too large such as startup-script contents. |
| `--min-cpu-platform` | PLATFORM |  | When specified, the VM will be scheduled on host with specified CPU architecture or a newer one. To list available CPU platforms in given zone, run: $ gcloud compute zones describe ZONE \ --format="value(availableCpuPlatforms)" Default setting is "AUTOMATIC". CPU platform selection is available only in selected zones. You can find more information on-line: https://cloud.google.com/compute/docs/instances/specify-min-cpu-platform |
| `--min-node-cpu` | MIN_NODE_CPU |  | Minimum number of virtual CPUs this instance will consume when running on a sole-tenant node. |
| `--network` | NETWORK |  | Specifies the network that the VM instances are a part of. If --subnet is also specified, subnet must be a subnetwork of the network specified by this --network flag. If neither is specified, the default network is used. |
| `--network-interface` | one of: PREMIUM, STANDARD |  | Adds a network interface to the instance. Mutually exclusive with any of these flags: --address, --network, --network-tier, --subnet, --private-network-ip, --stack-type, --ipv6-network-tier, --internal-ipv6-address, --internal-ipv6-prefix-length, --ipv6-address, --ipv6-prefix-length, --external-ipv6-address, --external-ipv6-prefix-length, --ipv6-public-ptr-domain. This flag can be repeated to specify multiple network interfaces. The following keys are allowed: address Assigns the given external address to the instance that is created. Specifying an empty string will assign an ephemeral IP. Mutually exclusive with no-address. If neither key is present the instance will get an ephemeral IP. network Specifies the network that the interface will be part of. If subnet is also specified it must be subnetwork of this network. If neither is specified, this defaults to the "default" network. no-address If specified the interface will have no external IP. Mutually exclusive with address. If neither key is present the instance will get an ephemeral IP. network-tier Specifies the network tier of the interface. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. private-network-ip Assigns the given RFC1918 IP address to the interface. subnet Specifies the subnet that the interface will be part of. If network key is also specified this must be a subnetwork of the specified network. nic-type Specifies the Network Interface Controller (NIC) type for the interface. NIC_TYPE must be one of: GVNIC, VIRTIO_NET. queue-count Specifies the networking queue count for this interface. Both Rx and Tx queues will be set to this number. If it's not specified, a default queue count will be assigned. See https://cloud.google.com/compute/docs/network-bandwidth#rx-tx for more details. stack-type Specifies whether IPv6 is enabled on the interface. STACK_TYPE must be one of: IPV4_ONLY, IPV4_IPV6, IPV6_ONLY. The default value is IPV4_ONLY. ipv6-network-tier Specifies the IPv6 network tier that will be used to configure the instance network interface IPv6 access config. IPV6_NETWORK_TIER must be PREMIUM (currently only one value is supported). internal-ipv6-address Assigns the given internal IPv6 address or range to the instance that is created. The address must be the first IP address in the range or from a /96 IP address range. This option can be used only when creating a single instance. internal-ipv6-prefix-length Optional field that indicates the prefix length of the internal IPv6 address range. It should be used together with internal-ipv6-address. Only /96 IP address range is supported and the default value is 96. If not set, either the prefix length from --internal-ipv6-address will be used or the default value of 96 will be assigned. external-ipv6-address Assigns the given external IPv6 address to the instance that is created. The address must be the first IP address in the range. This option can be used only when creating a single instance. external-ipv6-prefix-length The prefix length of the external IPv6 address range. This field should be used together with external-ipv6-address. Only the /96 IP address range is supported, and the default value is 96. ipv6-public-ptr-domain Assigns a custom PTR domain for the external IPv6 in the IPv6 access configuration of instance. If its value is not specified, the default PTR record will be used. This option can only be specified for the default network interface, nic0. aliases Specifies the IP alias ranges to allocate for this interface. If there are multiple IP alias ranges, they are separated by semicolons. For example: --aliases="10.128.1.0/24;range1:/32" Each IP alias range consists of a range name and an IP range separated by a colon, or just the IP range. The range name is the name of the range within the network interface's subnet from which to allocate an IP alias range. If unspecified, it defaults to the primary IP range of the subnet. The IP range can be a CIDR range (e.g. 192.168.100.0/24), a single IP address (e.g. 192.168.100.1), or a netmask in CIDR format (e.g. /24). If the IP range is specified by CIDR range or single IP address, it must belong to the CIDR range specified by the range name on the subnet. If the IP range is specified by netmask, the IP allocator will pick an available range with the specified netmask and allocate it to this network interface. network-attachment Specifies the network attachment that this interface should connect to. Mutually exclusive with --network and --subnet flags. vlan VLAN ID of a Dynamic Network Interface, must be an integer in the range from 2 to 255 inclusively. igmp-query Determines if the Compute Engine Instance can receive and respond to IGMP query packets on the specified network interface. IGMP_QUERY must be one of: IGMP_QUERY_V2, IGMP_QUERY_DISABLED. It is disabled by default. |
| `--network-performance-configs` | [PROPERTY=VALUE,...] |  | Configures network performance settings for the instance. If this flag is not specified, the instance will be created with its default network performance configuration. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [DEFAULT,TIER_1] |
| `--network-tier` | one of: PREMIUM, STANDARD |  | Specifies the network tier that will be used to configure the instance. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. |
| `--node-project` | NODE_PROJECT |  | The name of the project with shared sole tenant node groups to create an instance in. |
| `--performance-monitoring-unit` | one of: architectural This enables architecturally defined non-last level cache (LLC) events |  | The type of performance monitoring counters (PMCs) to enable in the instance. PERFORMANCE_MONITORING_UNIT must be one of: architectural This enables architecturally defined non-last level cache (LLC) events. enhanced This enables most documented core/L2 and LLC events. standard This enables most documented core/L2 events. |
| `--preemptible` |  |  | If provided, instances will be preemptible and time-limited. Instances might be preempted to free up resources for standard VM instances, and will only be able to run for a limited amount of time. Preemptible instances can not be restarted and will not migrate. |
| `--private-ipv6-google-access-type` | one of: enable-bidirectional-access, enable-outbound-vm-access, inherit-subnetwork |  | The private IPv6 Google access type for the VM. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: enable-bidirectional-access, enable-outbound-vm-access, inherit-subnetwork. |
| `--private-network-ip` | PRIVATE_NETWORK_IP |  | Specifies the RFC1918 IP to assign to the instance. The IP should be in the subnet or legacy network IP range. |
| `--provisioning-model` | one of: FLEX_START The VM instance is provisioned using the Flex Start provisioning model and has a limited runtime |  | Specifies the provisioning model for your VM instances. This choice affects the price, availability, and how long your VM instances can run. PROVISIONING_MODEL must be one of: FLEX_START The VM instance is provisioned using the Flex Start provisioning model and has a limited runtime. RESERVATION_BOUND The VM instances run for the entire duration of their associated reservation. You can only specify this provisioning model if you want your VM instances to consume a specific reservation with either a calendar reservation mode or a dense deployment type. SPOT Compute Engine may stop a Spot VM instance whenever it needs capacity. Because Spot VM instances don't have a guaranteed runtime, they come at a discounted price. STANDARD The default option. The STANDARD provisioning model gives you full control over your VM instances' runtime. |
| `--request-valid-for-duration` | REQUEST_VALID_FOR_DURATION |  | When you create an instance by using the FLEX_START provisioning model, you can specify the duration to wait for available resources. If the instance creation request is still pending after this duration, then the request fails. You specify a duration by using numbers followed by h, m, and s for hours, minutes, and seconds, respectively. For example, specify 30m for a duration of 30 minutes, or 1h2m3s for 1 hour, 2 minutes, and 3 seconds. Longer durations give you higher chances that your instance creation request succeeds when resources are in high demand. |
| `--require-csek-key-create` |  |  | Refuse to create resources not protected by a user managed key in the key file when --csek-key-file is given. This behavior is enabled by default to prevent incorrect gcloud invocations from accidentally creating resources with no user managed key. Disabling the check allows creation of some resources without a matching Customer-Supplied Encryption Key in the supplied --csek-key-file. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. Enabled by default, use --no-require-csek-key-create to disable. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | Specifies a list of resource manager tags to apply to the instance. |
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be added to the instance. The policies must exist in the same region as the instance. |
| `--restart-on-failure` |  |  | The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. Enabled by default, use --no-restart-on-failure to disable. |
| `--shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. This baseline can be updated by using gcloud compute instances update --shielded-learn-integrity-policy. On Shielded VM instances, integrity monitoring is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. For information about monitoring integrity on Shielded VM instances, see https://cloud.google.com/compute/docs/instances/integrity-monitoring." |
| `--shielded-secure-boot` |  |  | The instance boots with secure boot enabled. On Shielded VM instances, Secure Boot is not enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. |
| `--shielded-vtpm` |  |  | The instance boots with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations such as remote attestation, encryption, and sealing of keys. On Shielded VM instances, vTPM is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. |
| `--[no-]skip-guest-os-shutdown` |  |  | If enabled, then, when the instance is stopped or deleted, the instance is immediately stopped without giving time to the guest OS to cleanly shut down. Use --skip-guest-os-shutdown to enable and --no-skip-guest-os-shutdown to disable. |
| `--source-instance-template` | SOURCE_INSTANCE_TEMPLATE |  | The name of the instance template that the instance will be created from. An instance template can be a global/regional resource. Users can override instance properties using other flags. |
| `--source-machine-image` | SOURCE_MACHINE_IMAGE |  | The name of the machine image that the instance will be created from. |
| `--source-machine-image-csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file, mapping resources to user managed keys which were used to encrypt the source machine-image. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--stack-type` | STACK_TYPE |  | Specifies whether IPv6 is enabled on the default network interface. If not specified, IPV4_ONLY will be used. STACK_TYPE must be one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses IPV4_ONLY The network interface will be assigned IPv4 addresses IPV6_ONLY The network interface will be assigned IPv6 addresses |
| `--subnet` | SUBNET |  | Specifies the subnet that the VM instances are a part of. If --network is also specified, subnet must be a subnetwork of the network specified by the --network flag. |
| `--tags` | TAG,[TAG,...] |  | Specifies a list of tags to apply to the instance. These tags allow network firewall rules and routes to be applied to specified VM instances. See gcloud compute firewall-rules create(1) for more details. To read more about configuring network tags, read this guide: https://cloud.google.com/vpc/docs/add-remove-network-tags To list instances with their respective status and tags, run: $ gcloud compute instances list \ --format='table(name,status,tags.list())' To list instances tagged with a specific tag, tag1, run: $ gcloud compute instances list --filter='tags:tag1' |
| `--termination-time` | TERMINATION_TIME |  | Limits how long this VM instance can run, specified as a time. Format the time, TERMINATION_TIME, as a RFC 3339 timestamp. For more information, see https://tools.ietf.org/html/rfc3339. Alternatively, to specify a duration, use --max-run-duration instead. If neither --termination-time nor --max-run-duration is specified (default), the VM instance runs until prompted by a user action or system event. If either is specified, the VM instance is scheduled to be automatically terminated at the VM's termination timestamp (terminationTimestamp) using the action specified by --instance-termination-action. Note: The terminationTimestamp is removed whenever the VM is stopped or suspended and redefined whenever the VM is rerun. For --termination-time specifically, the terminationTimestamp remains the same whenever the VM is rerun, but any requests to rerun the VM fail if the specified timestamp is in the past. |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of visible threads per physical core. To disable simultaneous multithreading (SMT) set this to 1. Valid values are: 1 or 2. For more information about configuring SMT, see: https://cloud.google.com/compute/docs/instances/configuring-simultaneous-multithreading. |
| `--turbo-mode` | TURBO_MODE |  | Turbo mode to use for the instance. Supported modes include: * ALL_CORE_MAX To achieve all-core-turbo frequency for more consistent CPU performance, set the field to ALL_CORE_MAX. The field is unset by default, which results in maximum performance single-core boosting. |
| `--visible-core-count` | VISIBLE_CORE_COUNT |  | The number of physical cores to expose to the instance's guest operating system. The number of virtual CPUs visible to the instance's guest operating system is this number of cores multiplied by the instance's count of visible threads per physical core. |
| `--zone` | ZONE |  | Zone of the instances to create. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--image-family-scope` | one of: zonal, global |  | _[https://cloud.google.com/compute/docs/general-purpose-machines#custom_machine_types]_ Sets the scope for the --image-family flag. By default, when specifying an image family in a public image project, the zonal image family scope is used. All other projects default to the global image. Use this flag to override this behavior. IMAGE_FAMILY_SCOPE must be one of: zonal, global. |
| `--image-project` | IMAGE_PROJECT |  | _[https://cloud.google.com/compute/docs/general-purpose-machines#custom_machine_types]_ The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available projects can be generated by running gcloud projects list. * If specifying one of our public images, image-project must be provided. * If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. * If not specified and either image or image-family is provided, the current default project is used. |


**Examples:**
```bash
To create an instance with the latest 'Red Hat Enterprise Linux 8' image
available, run:

    $ gcloud compute instances create example-instance \
        --image-family=rhel-8 --image-project=rhel-cloud \
        --zone=us-central1-a

To create instances called 'example-instance-1', 'example-instance-2', and
'example-instance-3' in the 'us-central1-a' zone, run:

    $ gcloud compute instances create example-instance-1 \
        example-instance-2 example-instance-3 --zone=us-central1-a

To create an instance called 'instance-1' from a source snapshot called
'instance-snapshot' in zone 'us-central1-a' and attached regional disk
'disk-1', run:

    $ gcloud compute instances create instance-1 \
        --source-snapshot=https://compute.googleapis.com/compute/v1/\
    projects/myproject/global/snapshots/instance-snapshot \
        --zone=us-central1-a --disk=name=disk1,scope=regional

To create an instance called instance-1 as a Shielded VM instance with
Secure Boot, virtual trusted platform module (vTPM) enabled and integrity
monitoring, run:

    $ gcloud compute instances create instance-1 --zone=us-central1-a \
        --shielded-secure-boot --shielded-vtpm \
        --shielded-integrity-monitoring

To create a preemptible instance called 'instance-1', run:

    $ gcloud compute instances create instance-1 \
        --machine-type=n1-standard-1 --zone=us-central1-b \
        --preemptible --no-restart-on-failure \
        --maintenance-policy=terminate
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create)

---
### `gcloud compute instances create-with-container`

Creates Compute Engine virtual machine instances running container images

(DEPRECATED) The option to deploy a container during VM creation using the
container startup agent is deprecated. Use alternative services to run
containers on your VMs. Learn more at
https://cloud.google.com/compute/docs/containers/migrate-containers.

gcloud compute instances create-with-container creates Compute Engine
virtual machines that runs a Docker image. For example:

    $ gcloud compute instances create-with-container instance-1 \
        --zone us-central1-a             \
        --container-image=gcr.io/google-containers/busybox

creates an instance called instance-1, in the us-central1-a zone, running
the 'busybox' image.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute instances create-with-container INSTANCE_NAMES
    [INSTANCE_NAMES ...] [--accelerator=[count=COUNT],[type=TYPE]]
    [--no-boot-disk-auto-delete]
    [--boot-disk-device-name=BOOT_DISK_DEVICE_NAME]
    [--boot-disk-interface=BOOT_DISK_INTERFACE]
    [--boot-disk-provisioned-iops=BOOT_DISK_PROVISIONED_IOPS]
    [--boot-disk-provisioned-throughput=BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--boot-disk-size=BOOT_DISK_SIZE] [--boot-disk-type=BOOT_DISK_TYPE]
    [--can-ip-forward] [--container-arg=CONTAINER_ARG]
    [--container-command=CONTAINER_COMMAND]
    [--container-env=[KEY=VALUE, ...,...]]
    [--container-env-file=CONTAINER_ENV_FILE]
    [--container-image=CONTAINER_IMAGE]
    [--container-mount-disk=[mode=MODE],
      [mount-path=MOUNT-PATH],[name=NAME],[partition=PARTITION]]
    [--container-mount-host-path=[host-path=HOSTPATH,
      mount-path=MOUNTPATH[,mode=MODE],...]]
    [--container-mount-tmpfs=[mount-path=MOUNTPATH,...]]
    [--container-privileged]
    [--container-restart-policy=POLICY; default="always"]
    [--container-stdin] [--container-tty]
    [--create-disk=[PROPERTY=VALUE,...]] [--description=DESCRIPTION]
    [--discard-local-ssds-at-termination-timestamp=DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP]
    [--disk=[auto-delete=AUTO-DELETE],[boot=BOOT],[device-name=DEVICE-NAME],
      [force-attach=FORCE-ATTACH],
      [interface=INTERFACE],[mode=MODE],[name=NAME],[scope=SCOPE]]
    [--[no-]enable-nested-virtualization]
    [--external-ipv6-address=EXTERNAL_IPV6_ADDRESS]
    [--external-ipv6-prefix-length=EXTERNAL_IPV6_PREFIX_LENGTH]
    [--host-error-timeout-seconds=HOST_ERROR_TIMEOUT_SECONDS]
    [--instance-termination-action=INSTANCE_TERMINATION_ACTION]
    [--internal-ipv6-address=INTERNAL_IPV6_ADDRESS]
    [--internal-ipv6-prefix-length=INTERNAL_IPV6_PREFIX_LENGTH]
    [--ipv6-network-tier=IPV6_NETWORK_TIER] [--labels=[KEY=VALUE,...]]
    [--local-ssd-recovery-timeout=LOCAL_SSD_RECOVERY_TIMEOUT]
    [--machine-type=MACHINE_TYPE] [--maintenance-policy=MAINTENANCE_POLICY]
    [--max-run-duration=MAX_RUN_DURATION]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]]
    [--min-cpu-platform=PLATFORM] [--network=NETWORK]
    [--network-interface=[PROPERTY=VALUE,...]]
    [--network-performance-configs=[PROPERTY=VALUE,...]]
    [--network-tier=NETWORK_TIER] [--preemptible]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--private-network-ip=PRIVATE_NETWORK_IP]
    [--provisioning-model=PROVISIONING_MODEL]
    [--request-valid-for-duration=REQUEST_VALID_FOR_DURATION]
    [--resource-policies=[RESOURCE_POLICY,...]] [--no-restart-on-failure]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--[no-]skip-guest-os-shutdown]
    [--source-instance-template=SOURCE_INSTANCE_TEMPLATE]
    [--stack-type=STACK_TYPE] [--subnet=SUBNET] [--tags=TAG,[TAG,...]]
    [--termination-time=TERMINATION_TIME]
    [--threads-per-core=THREADS_PER_CORE]
    [--visible-core-count=VISIBLE_CORE_COUNT] [--zone=ZONE]
    [--address=ADDRESS | --no-address]
    [--confidential-compute
      | --confidential-compute-type=CONFIDENTIAL_COMPUTE_TYPE]
    [--custom-cpu=CUSTOM_CPU --custom-memory=CUSTOM_MEMORY
      : --custom-extensions --custom-vm-type=CUSTOM_VM_TYPE]
    [--image-project=IMAGE_PROJECT --image=IMAGE
      | --image-family=IMAGE_FAMILY] [--public-ptr | --no-public-ptr]
    [--public-ptr-domain=PUBLIC_PTR_DOMAIN | --no-public-ptr-domain]
    [--reservation=RESERVATION
      --reservation-affinity=RESERVATION_AFFINITY; default="any"]
    [--scopes=[SCOPE,...] | --no-scopes]
    [--service-account=SERVICE_ACCOUNT | --no-service-account]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to create. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Attaches accelerators (e.g. GPUs) to the instances. type The specific type (e.g. nvidia-tesla-t4 for NVIDIA T4) of accelerator to attach to the instances. Use 'gcloud compute accelerator-types list' to learn about all available accelerator types. count Number of accelerators to attach to each instance. The default value is 1. |
| `--boot-disk-auto-delete` |  |  | Automatically delete boot disks when their instances are deleted. Enabled by default, use --no-boot-disk-auto-delete to disable. |
| `--boot-disk-device-name` | BOOT_DISK_DEVICE_NAME |  | The name the guest operating system will see for the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). |
| `--boot-disk-interface` | BOOT_DISK_INTERFACE |  | Indicates the interface to use for the boot disk. The value must be one of the following: * SCSI * NVME |
| `--boot-disk-provisioned-iops` | BOOT_DISK_PROVISIONED_IOPS |  | Indicates how many IOPS to provision for the disk. This sets the number of I/O operations per second that the disk can handle. |
| `--boot-disk-provisioned-throughput` | BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates how much throughput to provision for the disk. This sets the number of throughput mb per second that the disk can handle. |
| `--boot-disk-size` | BOOT_DISK_SIZE |  | The size of the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. Disk size must be a multiple of 1 GB. Default size unit is GB. |
| `--boot-disk-type` | BOOT_DISK_TYPE |  | The type of the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). To get a list of available disk types, run $ gcloud compute disk-types list. |
| `--can-ip-forward` |  |  | If provided, allows the instances to send and receive packets with non-matching destination or source IP addresses. |
| `--container-arg` | CONTAINER_ARG |  | Argument to append to container entrypoint or to override container CMD. Each argument must have a separate flag. Arguments are appended in the order of flags. Example: Assuming the default entry point of the container (or an entry point overridden with --container-command flag) is a Bourne shell-compatible executable, in order to execute 'ls -l' command in the container, the user could use: --container-arg="-c" --container-arg="ls -l" Caveat: due to the nature of the argument parsing, it's impossible to provide the flag value that starts with a dash (-) without the = sign (that is, --container-arg "-c" will not work correctly). Default: None. (no arguments appended) |
| `--container-command` | CONTAINER_COMMAND |  | Specifies what executable to run when the container starts (overrides default entrypoint), eg. nc. Default: None (default container entrypoint is used) |
| `--container-env` | [KEY=VALUE, ...,...] |  | Declare environment variables KEY with value VALUE passed to container. Only the last value of KEY is taken when KEY is repeated more than once. Values, declared with --container-env flag override those with the same KEY from file, provided in --container-env-file. |
| `--container-env-file` | CONTAINER_ENV_FILE |  | Declare environment variables in a file. Values, declared with --container-env flag override those with the same KEY from file. File with environment variables in format used by docker (almost). This means: * Lines are in format KEY=VALUE. * Values must contain equality signs. * Variables without values are not supported (this is different from docker format). * If # is first non-whitespace character in a line the line is ignored as a comment. * Lines with nothing but whitespace are ignored. |
| `--container-image` | CONTAINER_IMAGE |  | Full container image name, which should be pulled onto VM instance, eg. docker.io/tomcat. |
| `--container-mount-disk` | [mode=MODE],[mount-path=MOUNT-PATH],[name=NAME],[partition=PARTITION] |  | Mounts a disk to the specified mount path in the container. Multiple ' flags are allowed. Must be used with --disk or --create-disk. name Name of the disk. If exactly one additional disk is attached to the instance using --disk or --create-disk, specifying disk name here is optional. The name of the single additional disk will be used by default. mount-path Path on container to mount to. Mount paths with spaces and commas (and other special characters) are not supported by this command. partition Optional. The partition of the disk to mount. Multiple partitions of a disk can be mounted. Can't be used with --create-disk. mode Volume mount mode: rw (read/write) or ro (read-only). Defaults to rw. Fails if the disk mode is ro and volume mount mode is rw. |
| `--container-mount-host-path` | [host-path=HOSTPATH,mount-path=MOUNTPATH[,mode=MODE],...] |  | Mounts a volume by using host-path. host-path Path on host to mount from. mount-path Path on container to mount to. Mount paths with spaces and commas (and other special characters) are not supported by this command. mode Volume mount mode: rw (read/write) or ro (read-only). Default: rw. |
| `--container-mount-tmpfs` | [mount-path=MOUNTPATH,...] |  | Mounts empty tmpfs into container at MOUNTPATH. mount-path Path on container to mount to. Mount paths with spaces and commas (and other special characters) are not supported by this command. |
| `--container-privileged` |  |  | Specify whether to run container in privileged mode. Default: --no-container-privileged. |
| `--container-restart-policy` | one of: never, on-failure, always | always | Specify whether to restart a container on exit. POLICY must be one of: never, on-failure, always. |
| `--container-stdin` |  |  | Keep container STDIN open even if not attached. Default: --no-container-stdin. |
| `--container-tty` |  |  | Allocate a pseudo-TTY for the container. Default: --no-container-tty. |
| `--create-disk` | [PROPERTY=VALUE,...] |  | Creates and attaches persistent disks to the instances. name Specifies the name of the disk. This option cannot be specified if more than one instance is being created. Must specify this option if attaching the disk to a container with --container-mount-disk. description Optional textual description for the disk being created. mode Specifies the mode of the disk. Supported options are ro for read-only and rw for read-write. If omitted, rw is used as a default. It is an error to create a disk in ro mode if attaching it to a container with --container-mount-disk. image Specifies the name of the image that the disk will be initialized with. A new disk will be created based on the given image. To view a list of public images and projects, run $ gcloud compute images list. It is best practice to use image when a specific version of an image is needed. If both image and image-family flags are omitted a blank disk will be created. image-family The image family for the operating system that the boot disk will be initialized with. Compute Engine offers multiple Linux distributions, some of which are available as both regular and Shielded VM images. When a family is specified instead of an image, the latest non-deprecated image associated with that family is used. It is best practice to use --image-family when the latest version of an image is needed. image-project The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available image projects can be generated by running gcloud compute images list. + If specifying one of our public images, image-project must be provided. + If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. + If not specified and either image or image-family is provided, the current default project is used. size The size of the disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. Disk size must be a multiple of 1 GB. If not specified, the default image size will be used for the new disk. type The type of the disk. To get a list of available disk types, run $ gcloud compute disk-types list. The default disk type is pd-standard. device-name An optional name to display the disk name in the guest operating system. Must be the same as name if used with --container-mount-disk. If omitted, a device name of the form persistent-disk-N is used. If omitted and used with --container-mount-disk (where the name of the container mount disk is the same as in this flag), a device name equal to disk name is used. provisioned-iops Indicates how many IOPS to provision for the disk. This sets the number of I/O operations per second that the disk can handle. Value must be between 10,000 and 120,000. provisioned-throughput Indicates how much throughput to provision for the disk. This sets the number of throughput mb per second that the disk can handle. disk-resource-policy Resource policy to apply to the disk. Specify a full or partial URL. For example: + https://www.googleapis.com/compute/v1/projects/my-project/regions/us-central1/resourcePolicies/my-resource-policy + projects/my-project/regions/us-central1/resourcePolicies/my-resource-policy For more information, see the following docs: + https://cloud.google.com/sdk/gcloud/reference/beta/compute/resource-policies/ + https://cloud.google.com/compute/docs/disks/scheduled-snapshots auto-delete If yes, this persistent disk will be automatically deleted when the instance is deleted. However, if the disk is later detached from the instance, this option won't apply. The default value for this is yes. architecture Specifies the architecture or processor type that this disk can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. storage-pool The name of the storage pool in which the new disk is created. The new disk and the storage pool must be in the same location. interface The interface to use with the disk. The value must be one of the following: + SCSI + NVME replica-zones Required for each regional disk associated with the instance. Specify the URLs of the zones where the disk should be replicated to. You must provide exactly two replica zones, and one zone must be the same as the instance zone. |
| `--description` | DESCRIPTION |  | Specifies a textual description of the instances. |
| `--discard-local-ssds-at-termination-timestamp` | DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP |  | Required to be set to true and only allowed for VMs that have one or more local SSDs, use --instance-termination-action=STOP, and use either --max-run-duration or --termination-time. This flag indicates the value that you want Compute Engine to use for the --discard-local-ssd flag in the automatic gcloud compute instances stop command. This flag only supports the true value, which discards local SSD data when automatically stopping this VM during its terminationTimestamp. For more information about the --discard-local-ssd flag, see https://cloud.google.com/compute/docs/disks/local-ssd#stop_instance. |
| `--disk` | [auto-delete=AUTO-DELETE],[boot=BOOT],[device-name=DEVICE-NAME],[force-attach=FORCE-ATTACH],[interface=INTERFACE],[mode=MODE],[name=NAME],[scope=SCOPE] |  | Attaches an existing disk to the instances. name The disk to attach to the instances. If you create more than one instance, you can only attach a disk in read-only mode. By default, you attach a zonal disk located in the same zone of the instance. If you want to attach a regional disk, you must specify the disk using its URI; for example, projects/myproject/regions/us-central1/disks/my-regional-disk. mode The mode of the disk. Supported options are ro for read-only mode and rw for read-write mode. If omitted, rw is used as a default value. If you use rw when creating more than one instance, you encounter errors. boot If set to yes, you attach a boot disk. The virtual machine then uses the first partition of the disk for the root file systems. The default value for this is no. device-name An optional name to display the disk name in the guest operating system. Must be the same as name if used with --container-mount-disk. If omitted, a device name of the form persistent-disk-N is used. If omitted and used with --container-mount-disk (where the name of the container mount disk is the same as in this flag), a device name equal to disk name is used. auto-delete If set to yes, the persistent disk is automatically deleted when the instance is deleted. However, if you detach the disk from the instance, deleting the instance doesn't delete the disk. The default value is yes. interface The interface to use for the disk. The value must be one of the following: + SCSI + NVME scope Can be zonal or regional. If zonal, the disk is interpreted as a zonal disk in the same zone as the instance (default). If regional, the disk is interpreted as a regional disk in the same region as the instance. The default value for this is zonal. force-attach If yes, this persistent disk will force-attached to the instance even it is already attached to another instance. The default value is 'no'. |
| `--[no-]enable-nested-virtualization` |  |  | If set to true, enables nested virtualization for the instance. Use --enable-nested-virtualization to enable and --no-enable-nested-virtualization to disable. |
| `--external-ipv6-address` | EXTERNAL_IPV6_ADDRESS |  | Assigns the given external IPv6 address to the instance that is created. The address must be the first IP address in the range. This option can be used only when creating a single instance. |
| `--external-ipv6-prefix-length` | EXTERNAL_IPV6_PREFIX_LENGTH |  | The prefix length of the external IPv6 address range. This field should be used together with --external-ipv6-address. Only the /96 IP address range is supported, and the default value is 96. |
| `--host-error-timeout-seconds` | HOST_ERROR_TIMEOUT_SECONDS |  | The timeout in seconds for host error detection. The value must be set with 30 second increments, with a range of 90 to 330 seconds. If unset, the default behavior of the host error recovery is used. |
| `--instance-termination-action` | one of: DELETE Permanently delete the VM |  | Specifies the termination action that will be taken upon VM preemption (--provisioning-model=SPOT) or automatic instance termination (--max-run-duration or --termination-time). INSTANCE_TERMINATION_ACTION must be one of: DELETE Permanently delete the VM. STOP Default only for Spot VMs. Stop the VM without preserving memory. The VM can be restarted later. |
| `--internal-ipv6-address` | INTERNAL_IPV6_ADDRESS |  | Assigns the given internal IPv6 address or range to the instance that is created. The address must be the first IP address in the range or from a /96 IP address range. This option can be used only when creating a single instance. |
| `--internal-ipv6-prefix-length` | INTERNAL_IPV6_PREFIX_LENGTH |  | Optional field that indicates the prefix length of the internal IPv6 address range. It should be used together with --internal-ipv6-address. Only /96 IP address range is supported and the default value is 96. If not set, either the prefix length from --internal-ipv6-address will be used or the default value of 96 will be assigned. |
| `--ipv6-network-tier` | IPV6_NETWORK_TIER |  | Specifies the IPv6 network tier that will be used to configure the instance network interface IPv6 access config. IPV6_NETWORK_TIER must be (only one value is supported): PREMIUM High quality, Google-grade network tier. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--local-ssd-recovery-timeout` | LOCAL_SSD_RECOVERY_TIMEOUT |  | Specifies the maximum amount of time a Local Ssd Vm should wait while recovery of the Local Ssd state is attempted. Its value should be in between 0 and 168 hours with hour granularity and the default value being 1 hour. |
| `--machine-type` | MACHINE_TYPE |  | Specifies the machine type used for the instances. To get a list of available machine types, run 'gcloud compute machine-types list'. If unspecified, the default type is n1-standard-1. |
| `--maintenance-policy` | one of: MIGRATE The instances should be migrated to a new host |  | Specifies the behavior of the VMs when their host machines undergo maintenance. The default is MIGRATE. For more information, see https://cloud.google.com/compute/docs/instances/host-maintenance-options. MAINTENANCE_POLICY must be one of: MIGRATE The instances should be migrated to a new host. This will temporarily impact the performance of instances during a migration event. TERMINATE The instances should be terminated. |
| `--max-run-duration` | MAX_RUN_DURATION |  | Limits how long this VM instance can run, specified as a duration relative to the last time when the VM began running. Format the duration, MAX_RUN_DURATION, as the number of days, hours, minutes, and seconds followed by d, h, m, and s respectively. For example, specify 30m for a duration of 30 minutes or specify 1d2h3m4s for a duration of 1 day, 2 hours, 3 minutes, and 4 seconds. Alternatively, to specify a timestamp, use --termination-time instead. If neither --max-run-duration nor --termination-time is specified (default), the VM instance runs until prompted by a user action or system event. If either is specified, the VM instance is scheduled to be automatically terminated at the VM's termination timestamp (terminationTimestamp) using the action specified by --instance-termination-action. Note: The terminationTimestamp is removed whenever the VM is stopped or suspended and redefined whenever the VM is rerun. For --max-run-duration specifically, the terminationTimestamp is the sum of MAX_RUN_DURATION and the time when the VM last entered the RUNNING state, which changes whenever the VM is rerun. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. Each metadata key must be unique and have a max of 128 bytes in length. Each value must have a max of 256 KB in length. Multiple arguments can be passed to this flag, e.g., --metadata key-1=value-1,key-2=value-2,key-3=value-3. The combined total size for all metadata entries is 512 KB. In images that have Compute Engine tools installed on them, such as the official images (https://cloud.google.com/compute/docs/images), the following metadata keys have special meanings: startup-script Specifies a script that will be executed by the instances once they start running. For convenience, --metadata-from-file can be used to pull the value from a file. startup-script-url Same as startup-script except that the script contents are pulled from a publicly-accessible location on the web. For startup scripts on Windows instances, the following metadata keys have special meanings: windows-startup-script-url, windows-startup-script-cmd, windows-startup-script-bat, windows-startup-script-ps1, sysprep-specialize-script-url, sysprep-specialize-script-cmd, sysprep-specialize-script-bat, and sysprep-specialize-script-ps1. For more information, see Running startup scripts (https://cloud.google.com/compute/docs/startupscript). |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | Same as --metadata except that the value for the entry will be read from a local file. This is useful for values that are too large such as startup-script contents. |
| `--min-cpu-platform` | PLATFORM |  | When specified, the VM will be scheduled on host with specified CPU architecture or a newer one. To list available CPU platforms in given zone, run: $ gcloud compute zones describe ZONE \ --format="value(availableCpuPlatforms)" Default setting is "AUTOMATIC". CPU platform selection is available only in selected zones. You can find more information on-line: https://cloud.google.com/compute/docs/instances/specify-min-cpu-platform |
| `--network` | NETWORK |  | Specifies the network that the VM instances are a part of. If --subnet is also specified, subnet must be a subnetwork of the network specified by this --network flag. If neither is specified, the default network is used. |
| `--network-interface` | one of: PREMIUM, STANDARD |  | Adds a network interface to the instance. Mutually exclusive with any of these flags: --address, --network, --network-tier, --subnet, --private-network-ip, --stack-type, --ipv6-network-tier, --internal-ipv6-address, --internal-ipv6-prefix-length, --ipv6-address, --ipv6-prefix-length, --external-ipv6-address, --external-ipv6-prefix-length. This flag can be repeated to specify multiple network interfaces. The following keys are allowed: address Assigns the given external address to the instance that is created. Specifying an empty string will assign an ephemeral IP. Mutually exclusive with no-address. If neither key is present the instance will get an ephemeral IP. network Specifies the network that the interface will be part of. If subnet is also specified it must be subnetwork of this network. If neither is specified, this defaults to the "default" network. no-address If specified the interface will have no external IP. Mutually exclusive with address. If neither key is present the instance will get an ephemeral IP. network-tier Specifies the network tier of the interface. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. private-network-ip Assigns the given RFC1918 IP address to the interface. subnet Specifies the subnet that the interface will be part of. If network key is also specified this must be a subnetwork of the specified network. nic-type Specifies the Network Interface Controller (NIC) type for the interface. NIC_TYPE must be one of: GVNIC, VIRTIO_NET. stack-type Specifies whether IPv6 is enabled on the interface. STACK_TYPE must be one of: IPV4_ONLY, IPV4_IPV6, IPV6_ONLY. The default value is IPV4_ONLY. ipv6-network-tier Specifies the IPv6 network tier that will be used to configure the instance network interface IPv6 access config. IPV6_NETWORK_TIER must be PREMIUM (currently only one value is supported). internal-ipv6-address Assigns the given internal IPv6 address or range to the instance that is created. The address must be the first IP address in the range or from a /96 IP address range. This option can be used only when creating a single instance. internal-ipv6-prefix-length Optional field that indicates the prefix length of the internal IPv6 address range. It should be used together with internal-ipv6-address. Only /96 IP address range is supported and the default value is 96. If not set, either the prefix length from --internal-ipv6-address will be used or the default value of 96 will be assigned. external-ipv6-address Assigns the given external IPv6 address to the instance that is created. The address must be the first IP address in the range. This option can be used only when creating a single instance. external-ipv6-prefix-length The prefix length of the external IPv6 address range. This field should be used together with external-ipv6-address. Only the /96 IP address range is supported, and the default value is 96. aliases Specifies the IP alias ranges to allocate for this interface. If there are multiple IP alias ranges, they are separated by semicolons. For example: --aliases="10.128.1.0/24;range1:/32" Each IP alias range consists of a range name and an IP range separated by a colon, or just the IP range. The range name is the name of the range within the network interface's subnet from which to allocate an IP alias range. If unspecified, it defaults to the primary IP range of the subnet. The IP range can be a CIDR range (e.g. 192.168.100.0/24), a single IP address (e.g. 192.168.100.1), or a netmask in CIDR format (e.g. /24). If the IP range is specified by CIDR range or single IP address, it must belong to the CIDR range specified by the range name on the subnet. If the IP range is specified by netmask, the IP allocator will pick an available range with the specified netmask and allocate it to this network interface. network-attachment Specifies the network attachment that this interface should connect to. Mutually exclusive with --network and --subnet flags. vlan VLAN ID of a Dynamic Network Interface, must be an integer in the range from 2 to 255 inclusively. |
| `--network-performance-configs` | [PROPERTY=VALUE,...] |  | Configures network performance settings for the instance. If this flag is not specified, the instance will be created with its default network performance configuration. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [DEFAULT,TIER_1] |
| `--network-tier` | one of: PREMIUM, STANDARD |  | Specifies the network tier that will be used to configure the instance. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. |
| `--preemptible` |  |  | If provided, instances will be preemptible and time-limited. Instances might be preempted to free up resources for standard VM instances, and will only be able to run for a limited amount of time. Preemptible instances can not be restarted and will not migrate. |
| `--private-ipv6-google-access-type` | one of: enable-bidirectional-access, enable-outbound-vm-access, inherit-subnetwork |  | The private IPv6 Google access type for the VM. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: enable-bidirectional-access, enable-outbound-vm-access, inherit-subnetwork. |
| `--private-network-ip` | PRIVATE_NETWORK_IP |  | Specifies the RFC1918 IP to assign to the instance. The IP should be in the subnet or legacy network IP range. |
| `--provisioning-model` | one of: FLEX_START The VM instance is provisioned using the Flex Start provisioning model and has a limited runtime |  | Specifies the provisioning model for your VM instances. This choice affects the price, availability, and how long your VM instances can run. PROVISIONING_MODEL must be one of: FLEX_START The VM instance is provisioned using the Flex Start provisioning model and has a limited runtime. RESERVATION_BOUND The VM instances run for the entire duration of their associated reservation. You can only specify this provisioning model if you want your VM instances to consume a specific reservation with either a calendar reservation mode or a dense deployment type. SPOT Compute Engine may stop a Spot VM instance whenever it needs capacity. Because Spot VM instances don't have a guaranteed runtime, they come at a discounted price. STANDARD The default option. The STANDARD provisioning model gives you full control over your VM instances' runtime. |
| `--request-valid-for-duration` | REQUEST_VALID_FOR_DURATION |  | When you create an instance by using the FLEX_START provisioning model, you can specify the duration to wait for available resources. If the instance creation request is still pending after this duration, then the request fails. You specify a duration by using numbers followed by h, m, and s for hours, minutes, and seconds, respectively. For example, specify 30m for a duration of 30 minutes, or 1h2m3s for 1 hour, 2 minutes, and 3 seconds. Longer durations give you higher chances that your instance creation request succeeds when resources are in high demand. |
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be added to the instance. The policies must exist in the same region as the instance. |
| `--restart-on-failure` |  |  | The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. Enabled by default, use --no-restart-on-failure to disable. |
| `--shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. This baseline can be updated by using gcloud compute instances update-container --shielded-learn-integrity-policy. On Shielded VM instances, integrity monitoring is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. For information about monitoring integrity on Shielded VM instances, see https://cloud.google.com/compute/docs/instances/integrity-monitoring." |
| `--shielded-secure-boot` |  |  | The instance boots with secure boot enabled. On Shielded VM instances, Secure Boot is not enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. |
| `--shielded-vtpm` |  |  | The instance boots with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations such as remote attestation, encryption, and sealing of keys. On Shielded VM instances, vTPM is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. |
| `--[no-]skip-guest-os-shutdown` |  |  | If enabled, then, when the instance is stopped or deleted, the instance is immediately stopped without giving time to the guest OS to cleanly shut down. Use --skip-guest-os-shutdown to enable and --no-skip-guest-os-shutdown to disable. |
| `--source-instance-template` | SOURCE_INSTANCE_TEMPLATE |  | The name of the instance template that the instance will be created from. An instance template can be a global/regional resource. Users can override instance properties using other flags. |
| `--stack-type` | STACK_TYPE |  | Specifies whether IPv6 is enabled on the default network interface. If not specified, IPV4_ONLY will be used. STACK_TYPE must be one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses IPV4_ONLY The network interface will be assigned IPv4 addresses IPV6_ONLY The network interface will be assigned IPv6 addresses |
| `--subnet` | SUBNET |  | Specifies the subnet that the VM instances are a part of. If --network is also specified, subnet must be a subnetwork of the network specified by the --network flag. |
| `--tags` | TAG,[TAG,...] |  | Specifies a list of tags to apply to the instance. These tags allow network firewall rules and routes to be applied to specified VM instances. See gcloud compute firewall-rules create(1) for more details. To read more about configuring network tags, read this guide: https://cloud.google.com/vpc/docs/add-remove-network-tags To list instances with their respective status and tags, run: $ gcloud compute instances list \ --format='table(name,status,tags.list())' To list instances tagged with a specific tag, tag1, run: $ gcloud compute instances list --filter='tags:tag1' |
| `--termination-time` | TERMINATION_TIME |  | Limits how long this VM instance can run, specified as a time. Format the time, TERMINATION_TIME, as a RFC 3339 timestamp. For more information, see https://tools.ietf.org/html/rfc3339. Alternatively, to specify a duration, use --max-run-duration instead. If neither --termination-time nor --max-run-duration is specified (default), the VM instance runs until prompted by a user action or system event. If either is specified, the VM instance is scheduled to be automatically terminated at the VM's termination timestamp (terminationTimestamp) using the action specified by --instance-termination-action. Note: The terminationTimestamp is removed whenever the VM is stopped or suspended and redefined whenever the VM is rerun. For --termination-time specifically, the terminationTimestamp remains the same whenever the VM is rerun, but any requests to rerun the VM fail if the specified timestamp is in the past. |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of visible threads per physical core. To disable simultaneous multithreading (SMT) set this to 1. Valid values are: 1 or 2. For more information about configuring SMT, see: https://cloud.google.com/compute/docs/instances/configuring-simultaneous-multithreading. |
| `--visible-core-count` | VISIBLE_CORE_COUNT |  | The number of physical cores to expose to the instance's guest operating system. The number of virtual CPUs visible to the instance's guest operating system is this number of cores multiplied by the instance's count of visible threads per physical core. |
| `--zone` | ZONE |  | Zone of the instances to create. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--image-project` | IMAGE_PROJECT |  | _[https://cloud.google.com/compute/docs/general-purpose-machines#custom_machine_types]_ The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available projects can be generated by running gcloud projects list. * If specifying one of our public images, image-project must be provided. * If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. * If not specified and either image or image-family is provided, the current default project is used. |


**Examples:**
```bash
To run the gcr.io/google-containers/busybox image on an instance named
'instance-1' that executes 'echo "Hello world"' as a run command, run:

    $ gcloud compute instances create-with-container instance-1 \
        --container-image=gcr.io/google-containers/busybox \
        --container-command='echo "Hello world"'

To run the gcr.io/google-containers/busybox image in privileged mode, run:

    $ gcloud compute instances create-with-container instance-1 \
        --container-image=gcr.io/google-containers/busybox \
        --container-privileged
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/create-with-container)

---
### `gcloud compute instances delete`

Delete Compute Engine virtual machine instances

gcloud compute instances delete deletes one or more Compute Engine virtual
machine instances.

**Synopsis:**
```
gcloud compute instances delete INSTANCE_NAMES [INSTANCE_NAMES ...]
    [--zone=ZONE] [--delete-disks=DISK_TYPE | --keep-disks=DISK_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to delete. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instances to delete. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To delete an instance called 'instance-1' in the zone 'us-central-2-a',
run:

    $ gcloud compute instances delete instance-1 --zone=us-central2-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/delete)

---
### `gcloud compute instances delete-access-config`

Delete an access configuration from a virtual machine network interface

gcloud compute instances delete-access-config is used to delete access
configurations from network interfaces of Compute Engine virtual machines.
Access configurations let you assign a public, external IP to a virtual
machine. The delete-access-config operation removes external IP from the
instance interface. If there is traffic routed to the external IP, after
deleting the access config operation, traffic to the external IP will not
reach the VM anymore.

**Synopsis:**
```
gcloud compute instances delete-access-config INSTANCE_NAME
    [--access-config-name=ACCESS_CONFIG_NAME; default="external-nat"]
    [--network-interface=NETWORK_INTERFACE; default="nic0"] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-config-name` | ACCESS_CONFIG_NAME | external-nat | Specifies the name of the access configuration to delete. external-nat is used as the default if this flag is not provided. |
| `--network-interface` | NETWORK_INTERFACE | nic0 | Specifies the name of the network interface from which to delete the access configuration. If this is not provided, then nic0 is used as the default. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To remove the externally accessible IP from a virtual machine named
example-instance in zone us-central1-a, run:

    $ gcloud compute instances delete-access-config example-instance \
        --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/delete-access-config)

---
### `gcloud compute instances describe`

Describe a virtual machine instance

gcloud compute instances describe displays all data associated with a
Compute Engine virtual machine instance.

It's possible to limit the the scope of the description by using the
'--format' flag. For details, see Filtering and formatting fun with gcloud
(https://cloud.google.com/blog/products/gcp/filtering-and-formatting-fun-with).

**Synopsis:**
```
gcloud compute instances describe INSTANCE_NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to describe. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to describe. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe an instance named test-instance, run:

    $ gcloud compute instances describe test-instance

To output only a set of fields from the available information, specify it
using the '--format' flag:

    $ gcloud compute instances describe test-instance \
        --format="yaml(name,status,disks)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/describe)

---
### `gcloud compute instances detach-disk`

Detach disks from Compute Engine virtual machine instances

gcloud compute instances detach-disk is used to detach disks from virtual
machines.

Detaching a disk without first unmounting it may result in incomplete I/O
operations and data corruption. To unmount a persistent disk on a
Linux-based image, ssh into the instance and run:

    $ sudo umount /dev/disk/by-id/google-DEVICE_NAME

**Synopsis:**
```
gcloud compute instances detach-disk INSTANCE_NAME
    (--device-name=DEVICE_NAME | --disk=DISK)
    [--disk-scope=DISK_SCOPE; default="zonal"] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--device-name` | DEVICE_NAME |  | _[Exactly one of these must be specified:]_ Specifies a disk to detach by its device name, which is the name that the guest operating system sees. The device name is set at the time that the disk is attached to the instance, and needs not be the same as the persistent disk name. If the disk's device name is specified, then its persistent disk name must not be specified using the --disk flag. |
| `--disk` | DISK |  | _[Exactly one of these must be specified:]_ Specifies a disk to detach by its resource name. If you specify a disk to remove by persistent disk name, then you must not specify its device name using the --device-name flag. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disk-scope` | one of: regional The disk specified in --disk is interpreted as a regional disk in the same region as the instance | zonal | The scope of the disk. DISK_SCOPE must be one of: regional The disk specified in --disk is interpreted as a regional disk in the same region as the instance. Ignored if a full URI is provided to the --disk flag. zonal The disk specified in --disk is interpreted as a zonal disk in the same zone as the instance. Ignored if a full URI is provided to the --disk flag. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To detach a disk named 'my-disk' from an instance named 'my-instance', run:

    $ gcloud compute instances detach-disk my-instance --disk=my-disk

To detach a device named 'my-device' from an instance named 'my-instance',
run:

    $ gcloud compute instances detach-disk my-instance \
        --device-name=my-device
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/detach-disk)

---
### `gcloud compute instances export`

Export a Compute Engine virtual machine instance's configuration to a file

Export a Compute Engine virtual machine instance's configuration to a file.

**Synopsis:**
```
gcloud compute instances export (INSTANCE : --zone=ZONE)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Name of the instance to export. For details on valid
instance names, refer to the criteria documented under the field 'name'
at: https://cloud.google.com/compute/docs/reference/rest/v1/instances The
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

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
A virtual machine can be exported by running:

    $ gcloud compute instances export my-instance \
        --destination=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/export)

---
### `gcloud compute instances get-guest-attributes`

Get the Guest Attributes for a compute instance

Get the Guest Attributes for a compute instance.

**Synopsis:**
```
gcloud compute instances get-guest-attributes (INSTANCE : --zone=ZONE)
    [--query-path=QUERY_PATH] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to get the Guest Attributes for. The
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

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--query-path` | QUERY_PATH |  | Attribute path to query. Can be empty string or of the form <namespace>/ or <namespace>/<key>. Default is the empty string. |


**Examples:**
```bash
To get the guest attributes for instance 'my-instance' in zone 'ZONE' with
query path 'query/path', run:

    $ gcloud compute instances get-guest-attributes my-instance \
        --query-path=query/path --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-guest-attributes)

---
### `gcloud compute instances get-iam-policy`

Get the IAM policy for a Compute Engine instance

gcloud compute instances get-iam-policy displays the IAM policy associated
with a Compute Engine instance in a project. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute instances get-iam-policy (INSTANCE : --zone=ZONE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance for which to display the IAM policy. The
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

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To print the IAM policy for a given instance, run:

    $ gcloud compute instances get-iam-policy my-instance --zone=my-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-iam-policy)

---
### `gcloud compute instances get-screenshot`

Capture a screenshot (JPEG image) of the virtual machine instance's display

Capture a screenshot (JPEG image) of the virtual machine instance's
display.

**Synopsis:**
```
gcloud compute instances get-screenshot INSTANCE_NAME
    [--destination=DESTINATION] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to get a screenshot from. For details on valid
   instance names, refer to the criteria documented under the field 'name'
   at: https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Filename, including the path, to save the screenshot (JPEG image). |
| `--zone` | ZONE |  | Zone of the instance to get a screenshot from. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To get a screenshot from an instance named test-instance, run:

    $ gcloud compute instances get-screenshot test-instance \
        --destination=output.jpg
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-screenshot)

---
### `gcloud compute instances get-serial-port-output`

Read output from a virtual machine instance's serial port

gcloud compute instances get-serial-port-output is used to get the output
from a Compute Engine virtual machine's serial port. The serial port output
from the virtual machine will be printed to standard output. This
information can be useful for diagnostic purposes.

**Synopsis:**
```
gcloud compute instances get-serial-port-output INSTANCE_NAME [--port=PORT]
    [--start=START] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--port` | PORT |  | Instances can support up to four serial port outputs, numbered 1 through 4. By default, this command will return the output of the first serial port. Setting this flag will return the output of the requested serial port. |
| `--start` | START |  | Specifies the byte index (zero-based) of the first byte you want returned. Use this flag if you want to continue getting the output from a previous request that was too long to return in one attempt. The last byte returned in a request will be reported on STDERR. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To get the output from instance's serial port, run:

    $ gcloud compute instances get-serial-port-output example-instance \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-serial-port-output)

---
### `gcloud compute instances get-shielded-identity`

Get the Shielded identity for a Compute Engine instance

gcloud compute instances get-shielded-identity displays the Shielded
identity associated with a Compute Engine instance in a project.

**Synopsis:**
```
gcloud compute instances get-shielded-identity INSTANCE_NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to describe the Shielded identity of. For details
   on valid instance names, refer to the criteria documented under the
   field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to describe the Shielded identity of. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To get the shielded identity for an instance, run:

    $ gcloud compute instances get-shielded-identity example-instance \
        --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/get-shielded-identity)

---
### `gcloud compute instances import`

Create Compute Engine virtual machine instances from virtual appliance in OVA/OVF format

gcloud compute instances import creates Compute Engine virtual machine
instances from virtual appliance in OVA/OVF format.

Importing OVF involves:
  o Unpacking OVF package (if in OVA format) to Cloud Storage.
  o Import disks from OVF to Compute Engine.
  o Translate the boot disk to make it bootable in Compute Engine.
  o Create a VM instance using OVF metadata and imported disks and boot
    it.

OVF import tool requires Cloud Build to be enabled. See
https://cloud.google.com/compute/docs/import/import-ovf-files#enable-cloud-build
Virtual machine instances, images and disks in Compute engine and files
stored on Cloud Storage incur charges. See
https://cloud.google.com/compute/docs/images/importing-virtual-disks#resource_cleanup.

**Synopsis:**
```
gcloud compute instances import INSTANCE_NAME --source-uri=SOURCE_URI
    [--no-address] [--async] [--byol] [--can-ip-forward]
    [--cloudbuild-service-account=CLOUDBUILD_SERVICE_ACCOUNT]
    [--compute-service-account=COMPUTE_SERVICE_ACCOUNT]
    [--deletion-protection] [--description=DESCRIPTION]
    [--no-guest-environment] [--guest-os-features=[GUEST_OS_FEATURE,...]]
    [--hostname=HOSTNAME] [--labels=[KEY=VALUE,...]]
    [--log-location=LOG_LOCATION] [--machine-type=MACHINE_TYPE]
    [--network=NETWORK] [--network-tier=NETWORK_TIER] [--os=OS]
    [--private-network-ip=PRIVATE_NETWORK_IP] [--no-restart-on-failure]
    [--subnet=SUBNET] [--tags=TAG,[TAG,...]]
    [--timeout=TIMEOUT; default="2h"] [--zone=ZONE]
    [--custom-cpu=CUSTOM_CPU --custom-memory=CUSTOM_MEMORY
      : --custom-extensions --custom-vm-type=CUSTOM_VM_TYPE]
    [--node=NODE | --node-affinity-file=PATH_TO_FILE
      | --node-group=NODE_GROUP] [--scopes=[SCOPE,...] | --no-scopes]
    [--service-account=SERVICE_ACCOUNT | --no-service-account]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to import. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-uri` | SOURCE_URI |  | Cloud Storage path to one of: OVF descriptor OVA file Directory with OVF package. For more information about Cloud Storage URIs, see https://cloud.google.com/storage/docs/request-endpoints#json-api. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-address` |  |  | If provided, the instances are not assigned external IP addresses. To pull container images, you must configure private Google access if using Container Registry or configure Cloud NAT for instances to access container images directly. For more information, see: * https://cloud.google.com/vpc/docs/configure-private-google-access * https://cloud.google.com/nat/docs/using-nat |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--byol` |  |  | Specifies that you want to import an image with an existing license. Importing an image with an existing license is known as bring your own license (BYOL). --byol can be specified in any of the following ways: + `--byol --os=rhel-8`: imports a RHEL 8 image with an existing license. + `--os=rhel-8-byol`: imports a RHEL 8 image with an existing license. + `--byol`: detects the OS contained on the disk, and imports the image with an existing license. For more information about BYOL, see: https://cloud.google.com/compute/docs/nodes/bringing-your-own-licenses |
| `--can-ip-forward` |  |  | If provided, allows the instances to send and receive packets with non-matching destination or source IP addresses. |
| `--cloudbuild-service-account` | CLOUDBUILD_SERVICE_ACCOUNT |  | Image import and export tools use Cloud Build to import and export images to and from your project. Cloud Build uses a specific service account to execute builds on your behalf. The Cloud Build service account generates an access token for other service accounts and it is also used for authentication when building the artifacts for the image import tool. Use this flag to to specify a user-managed service account for image import and export. If you don't specify this flag, Cloud Build runs using your project's default Cloud Build service account. To set this option, specify the email address of the desired user-managed service account. Note: You must specify the --logs-location flag when you set a user-managed service account. At minimum, the specified user-managed service account needs to have the following roles assigned: * roles/compute.admin * roles/iam.serviceAccountTokenCreator * roles/iam.serviceAccountUser |
| `--compute-service-account` | COMPUTE_SERVICE_ACCOUNT |  | A temporary virtual machine instance is created in your project during instance import. Instance import tooling on this temporary instance must be authenticated. A Compute Engine service account is an identity attached to an instance. Its access tokens can be accessed through the instance metadata server and can be used to authenticate instance import tooling on the instance. To set this option, specify the email address corresponding to the required Compute Engine service account. If not provided, the instance import on the temporary instance uses the project's default Compute Engine service account. At a minimum, you need to grant the following roles to the specified Cloud Build service account: * roles/compute.storageAdmin * roles/storage.objectViewer |
| `--deletion-protection` |  |  | Enables deletion protection for the instance. |
| `--description` | DESCRIPTION |  | Specifies a textual description of the VM instances. |
| `--guest-environment` |  |  | The guest environment will be installed on the instance. Enabled by default, use --no-guest-environment to disable. |
| `--guest-os-features` | [GUEST_OS_FEATURE,...] |  | Enables one or more features for VM instances that use the image for their boot disks. See the descriptions of supported features at: https://cloud.google.com/compute/docs/images/create-delete-deprecate-private-images#guest-os-features. GUEST_OS_FEATURE must be (only one value is supported): UEFI_COMPATIBLE. |
| `--hostname` | HOSTNAME |  | Specify the hostname of the VM instance to be imported. The specified hostname must be RFC1035 compliant. If hostname is not specified, the default hostname is [INSTANCE_NAME].c.[PROJECT_ID].internal when using the global DNS, and [INSTANCE_NAME].[ZONE].c.[PROJECT_ID].internal when using zonal DNS. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--log-location` | LOG_LOCATION |  | Directory in Cloud Storage to hold build logs. If not set, gs://<project num>.cloudbuild-logs.googleusercontent.com/ is created and used. |
| `--machine-type` | MACHINE_TYPE |  | Specifies the machine type used for the instances. To get a list of available machine types, run 'gcloud compute machine-types list'. If unspecified, the default type is n1-standard-1. |
| `--network` | NETWORK |  | Specifies the network that the VM instances are a part of. If --subnet is also specified, subnet must be a subnetwork of the network specified by this --network flag. If neither is specified, the default network is used. |
| `--network-tier` | one of: PREMIUM, STANDARD |  | Specifies the network tier that will be used to configure the instance. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. |
| `--os` | one of: centos-7, centos-stream-8, centos-stream-9, debian-10, debian-11, debian-8, debian-9, opensuse-15, rhel-6, rhel-6-byol, rhel-7, rhel-7-byol, rhel-8, rhel-8-byol, rhel-9, rhel-9-byol, rocky-8, rocky-9, sles-12, sles-12-byol, sles-15, sles-15-byol, sles-sap-12, sles-sap-12-byol, sles-sap-15, sles-sap-15-byol, ubuntu-1404, ubuntu-1604, ubuntu-1804, ubuntu-2004, ubuntu-2204, windows-10-x64-byol, windows-10-x86-byol, windows-11-x64-byol, windows-2008r2, windows-2008r2-byol, windows-2012, windows-2012-byol, windows-2012r2, windows-2012r2-byol, windows-2016, windows-2016-byol, windows-2019, windows-2019-byol, windows-2022, windows-2022-byol, windows-7-x64-byol, windows-7-x86-byol, windows-8-x64-byol, windows-8-x86-byol |  | Specifies the OS of the image being imported. OS must be one of: centos-7, centos-stream-8, centos-stream-9, debian-10, debian-11, debian-8, debian-9, opensuse-15, rhel-6, rhel-6-byol, rhel-7, rhel-7-byol, rhel-8, rhel-8-byol, rhel-9, rhel-9-byol, rocky-8, rocky-9, sles-12, sles-12-byol, sles-15, sles-15-byol, sles-sap-12, sles-sap-12-byol, sles-sap-15, sles-sap-15-byol, ubuntu-1404, ubuntu-1604, ubuntu-1804, ubuntu-2004, ubuntu-2204, windows-10-x64-byol, windows-10-x86-byol, windows-11-x64-byol, windows-2008r2, windows-2008r2-byol, windows-2012, windows-2012-byol, windows-2012r2, windows-2012r2-byol, windows-2016, windows-2016-byol, windows-2019, windows-2019-byol, windows-2022, windows-2022-byol, windows-7-x64-byol, windows-7-x86-byol, windows-8-x64-byol, windows-8-x86-byol. |
| `--private-network-ip` | PRIVATE_NETWORK_IP |  | Specifies the RFC1918 IP to assign to the instance. The IP should be in the subnet or legacy network IP range. |
| `--restart-on-failure` |  |  | The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. Enabled by default, use --no-restart-on-failure to disable. |
| `--subnet` | SUBNET |  | Specifies the subnet that the VM instances are a part of. If --network is also specified, subnet must be a subnetwork of the network specified by the --network flag. |
| `--tags` | TAG,[TAG,...] |  | Specifies a list of tags to apply to the instance. These tags allow network firewall rules and routes to be applied to specified VM instances. See gcloud compute firewall-rules create(1) for more details. To read more about configuring network tags, read this guide: https://cloud.google.com/vpc/docs/add-remove-network-tags To list instances with their respective status and tags, run: $ gcloud compute instances list \ --format='table(name,status,tags.list())' To list instances tagged with a specific tag, tag1, run: $ gcloud compute instances list --filter='tags:tag1' |
| `--timeout` | TIMEOUT | 2h | Maximum time an import can last before it fails as "TIMEOUT". For example, if you specify 2h, the process fails after 2 hours. See $ gcloud topic datetimes for information about duration formats. This timeout option has a maximum value of 24 hours. |
| `--zone` | ZONE |  | Zone of the instance to import. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To import an OVF package from Cloud Storage into a VM named my-instance,
run:

    $ gcloud compute instances import my-instance \
        --source-uri=gs://my-bucket/my-dir
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/import)

---
### `gcloud compute instances list`

List Compute Engine instances

gcloud compute instances list displays all Compute Engine instances in a
project.

**Synopsis:**
```
gcloud compute instances list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--zones=ZONE,[ZONE,...]] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
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
| `--zones` | ZONE,[ZONE,...] |  | If provided, only resources from the given zones are queried. |


**Examples:**
```bash
To list all instances in a project in table form, run:

    $ gcloud compute instances list

To list the URIs of all instances in a project, run:

    $ gcloud compute instances list --uri

To list the IPv6 info of all instances in a project, run:

    $ gcloud compute instances list --format="table(
    name,
    zone.basename(),
    networkInterfaces[].stackType.notnull().list(),
    networkInterfaces[].ipv6AccessConfigs[0].externalIpv6.notnull().list():label=EXTERNAL_IPV6,
    networkInterfaces[].ipv6Address.notnull().list():label=INTERNAL_IPV6)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/list)

---
### `gcloud compute instances perform-maintenance`

Perform maintenance of Google Compute Engine instance

Perform maintenance of Google Compute Engine instance.

**Synopsis:**
```
gcloud compute instances perform-maintenance INSTANCE_NAMES
    [INSTANCE_NAMES ...] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To perform customer-triggered maintenance on an instance named
test-instance located in zone us-east1-d, run:

    $ gcloud compute instances perform-maintenance test-instance \
        --zone=us-east1-d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/perform-maintenance)

---
### `gcloud compute instances remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine instance

Remove an IAM policy binding from the IAM policy of a Compute Engine
instance. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud compute instances remove-iam-policy-binding (INSTANCE : --zone=ZONE)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance for which to remove IAM policy binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
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

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
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
'roles/compute.securityAdmin' for the user 'test-user@gmail.com' with
instance 'my-instance' and zone 'ZONE', run:

    $ gcloud compute instances remove-iam-policy-binding my-instance \
        --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with instance 'my-instance' and zone 'ZONE', run:

    $ gcloud compute instances remove-iam-policy-binding my-instance \
        --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/remove-iam-policy-binding)

---
### `gcloud compute instances remove-labels`

Remove labels from Google Compute Engine virtual machine instances

gcloud compute instances remove-labels removes labels from a Google Compute
Engine virtual machine instance.

**Synopsis:**
```
gcloud compute instances remove-labels INSTANCE_NAME
    (--all | --labels=KEY,[KEY,...]) [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[Exactly one of these must be specified:]_ Remove all labels from the resource. |
| `--labels` | KEY,[KEY,...] |  | _[Exactly one of these must be specified:]_ A comma-separated list of label keys to remove from the resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To remove existing labels with key k0 and k1 from 'example-instance'

    $ gcloud compute instances remove-labels example-instance \
        --labels=k0,k1

Labels can be used to identify the instance and to filter them. To find a
instance labeled with key-value pair k1, v2

    $ gcloud compute instances list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute instances describe example-instance \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/remove-labels)

---
### `gcloud compute instances remove-metadata`

Remove instance metadata

gcloud compute instances remove-metadata can be used to remove instance
metadata entries.

**Synopsis:**
```
gcloud compute instances remove-metadata INSTANCE_NAME [--zone=ZONE]
    [--all | --keys=KEY,[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to set metadata on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to set metadata on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To remove metadata keys important-data and useless-data along with their
data from an instance named test-instance, run:

    $ gcloud compute instances remove-metadata test-instance \
        --keys=important-data,useless-data
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/remove-metadata)

---
### `gcloud compute instances remove-resource-policies`

Remove resource policies from Compute Engine VM instances

gcloud compute instances remove-resource-policies removes resource policies
from Compute Engine virtual instances.

**Synopsis:**
```
gcloud compute instances remove-resource-policies INSTANCE_NAME
    --resource-policies=[RESOURCE_POLICY,...] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to remove resource policies from. For details on
   valid instance names, refer to the criteria documented under the field
   'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be removed from the instance. The policies must exist in the same region as the instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to remove resource policies from. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To remove resource policy pol1 from instance inst1, run this:

    $ gcloud compute instances remove-resource-policies inst1 \
        --resource-policies=pol1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/remove-resource-policies)

---
### `gcloud compute instances remove-tags`

Remove tags from Compute Engine virtual machine instances

gcloud compute instances remove-tags is used to remove tags from Compute
Engine virtual machine instances.

**Synopsis:**
```
gcloud compute instances remove-tags INSTANCE_NAME
    (--all | --tags=TAG,[TAG,...]) [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to set tags on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[Exactly one of these must be specified:]_ Remove all tags from the instance. |
| `--tags` | TAG,[TAG,...] |  | _[Exactly one of these must be specified:]_ Specifies strings to be removed from the instance tags. Multiple tags can be removed by repeating this flag. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to set tags on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To remove tags tag-1 and tag-2 from an instance named test-instance, run:

    $ gcloud compute instances remove-tags test-instance \
        --tags=tag-1,tag-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/remove-tags)

---
### `gcloud compute instances report-host-as-faulty`

Report a host as faulty to start the repair process

gcloud compute instances report-host-as-faulty is used to report a host as
faulty to start the repair process.

**Synopsis:**
```
gcloud compute instances report-host-as-faulty INSTANCE_NAME
    --disruption-schedule=DISRUPTION_SCHEDULE
    --fault-reasons=[behavior=BEHAVIOR],[description=DESCRIPTION] [--async]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disruption-schedule` | one of: IMMEDIATE, FUTURE |  | Specifies the timing for initiating the fault reporting process. The default value is IMMEDIATE which initiates the process right away. DISRUPTION_SCHEDULE must be one of: IMMEDIATE, FUTURE. |
| `--fault-reasons` | [behavior=BEHAVIOR],[description=DESCRIPTION] |  | Specified and can include one or more of the following types: ['BEHAVIOR_UNSPECIFIED', 'PERFORMANCE', 'SILENT_DATA_CORRUPTION', 'UNRECOVERABLE_GPU_ERROR']. This helps categorize the nature of the fault being reported. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To report a host as faulty for an instance named test-instance, run:

    $ gcloud compute instances report-host-as-faulty test-instance \
        --fault-reasons=behavior=SILENT_DATA_CORRUPTION,\
    description="affecting our ML job" --disruption-schedule=IMMEDIATE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/report-host-as-faulty)

---
### `gcloud compute instances reset`

Reset a virtual machine instance

gcloud compute instances reset is used to perform a hard reset on a Compute
Engine virtual machine.

This will not perform a clean shutdown of the guest OS on the instance.

**Synopsis:**
```
gcloud compute instances reset INSTANCE_NAMES [INSTANCE_NAMES ...]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To reset an instance named test-instance, run:

    $ gcloud compute instances reset test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/reset)

---
### `gcloud compute instances resume`

Resume a virtual machine instance

gcloud compute instances resume is used to resume a previously suspended
Compute Engine virtual machine.

**Synopsis:**
```
gcloud compute instances resume INSTANCE_NAMES [INSTANCE_NAMES ...]
    [--async] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To resume an instance named test-instance, run:

    $ gcloud compute instances resume test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/resume)

---
### `gcloud compute instances send-diagnostic-interrupt`

Send a diagnostic interrupt to a virtual machine instance

gcloud compute instances send-diagnostic-interrupt is used to send a
diagnostic interrupt to a running instance, which triggers special
interrupt handling logic inside VM.

For instances with Intel or AMD processors, the guest OS on the instance
will receive a non-maskable interrupt (NMI).

**Synopsis:**
```
gcloud compute instances send-diagnostic-interrupt INSTANCE_NAME
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To send a diagnostic interrupt to an instance named test-instance, run:

    $ gcloud compute instances send-diagnostic-interrupt test-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/send-diagnostic-interrupt)

---
### `gcloud compute instances set-disk-auto-delete`

Set auto-delete behavior for disks

$gcloud compute instances set-disk-auto-delete is used to configure the
auto-delete behavior for disks attached to Compute Engine virtual machines.
When auto-delete is on, the persistent disk is deleted when the instance it
is attached to is deleted.

**Synopsis:**
```
gcloud compute instances set-disk-auto-delete INSTANCE_NAME
    (--device-name=DEVICE_NAME | --disk=DISK) [--no-auto-delete]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--device-name` | DEVICE_NAME |  | _[Exactly one of these must be specified:]_ Specifies a disk to set auto-delete for by its device name, which is the name that the guest operating system sees. The device name is set at the time that the disk is attached to the instance, and need not be the same as the persistent disk name. If the disk's device name is specified, then its persistent disk name must not be specified using the --disk flag. |
| `--disk` | DISK |  | _[Exactly one of these must be specified:]_ Specifies a disk to set auto-delete for by its resource name. If you specify a disk to set auto-delete for by persistent disk name, then you must not specify its device name using the --device-name flag. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-delete` |  |  | Enables auto-delete for the given disk. Enabled by default, use --no-auto-delete to disable. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To enable auto-delete for a disk named 'my-disk' on an instance named
'my-instance', run:

    $ gcloud compute instances set-disk-auto-delete my-instance \
        --auto-delete --disk=my-disk

To enable auto-delete for a device named 'my-device' on an instance named
'my-instance', run:

    $ gcloud compute instances set-disk-auto-delete my-instance \
        --auto-delete --device-name=my-device
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-disk-auto-delete)

---
### `gcloud compute instances set-iam-policy`

Set IAM policy for a Compute Engine instance

Set IAM policy for a Compute Engine instance.

**Synopsis:**
```
gcloud compute instances set-iam-policy (INSTANCE : --zone=ZONE)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to set the IAM policy of. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

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

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
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
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for the instance 'my-instance' and zone 'ZONE':

    $ gcloud compute instances set-iam-policy my-instance --zone=ZONE \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-iam-policy)

---
### `gcloud compute instances set-machine-type`

Set machine type for Compute Engine virtual machines

gcloud compute instances set-machine-type lets you change the machine type
of a virtual machine in the TERMINATED state (that is, a virtual machine
instance that has been stopped).

For example, if example-instance is a g1-small virtual machine currently in
the TERMINATED state, running:

    $ gcloud compute instances set-machine-type example-instance \
        --zone us-central1-b --machine-type n1-standard-4

will change the machine type to n1-standard-4, so that when you next start
example-instance, it will be provisioned as an n1-standard-4 instead of a
g1-small.

See https://cloud.google.com/compute/docs/machine-types for more
information on machine types.

**Synopsis:**
```
gcloud compute instances set-machine-type INSTANCE_NAME
    [--machine-type=MACHINE_TYPE] [--zone=ZONE]
    [--custom-cpu=CUSTOM_CPU --custom-memory=CUSTOM_MEMORY
      : --custom-extensions --custom-vm-type=CUSTOM_VM_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--machine-type` | MACHINE_TYPE |  | Specifies the machine type used for the instances. To get a list of available machine types, run 'gcloud compute machine-types list'. Either this flag, --custom-cpu, or --custom-memory must be specified. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To change the machine type of a VM to n1-standard-4, run:

    $ gcloud compute instances set-machine-type example-instance \
        --zone=us-central1-b --machine-type=n1-standard-4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-machine-type)

---
### `gcloud compute instances set-name`

Set the name of a Compute Engine virtual machine

gcloud compute instances set-name lets you change the name of a virtual
machine.

**Synopsis:**
```
gcloud compute instances set-name INSTANCE_NAME --new-name=NEW_NAME
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-name` | NEW_NAME |  | Specifies the new name of the instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To change the name of instance-1 to instance-2:

    $ gcloud compute instances set-name instance-1 --new-name=instance-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-name)

---
### `gcloud compute instances set-scheduling`

Set scheduling options for Compute Engine virtual machines

$gcloud compute instances set-scheduling is used to update scheduling
options for VM instances. You can only call this method on a VM instance
that is stopped (a VM instance in a TERMINATED state).

**Synopsis:**
```
gcloud compute instances set-scheduling INSTANCE_NAME
    [--clear-min-node-cpu]
    [--host-error-timeout-seconds=HOST_ERROR_TIMEOUT_SECONDS]
    [--local-ssd-recovery-timeout=LOCAL_SSD_RECOVERY_TIMEOUT]
    [--maintenance-policy=MAINTENANCE_POLICY] [--min-node-cpu=MIN_NODE_CPU]
    [--[no-]preemptible] [--provisioning-model=PROVISIONING_MODEL]
    [--[no-]restart-on-failure] [--[no-]skip-guest-os-shutdown]
    [--zone=ZONE]
    [--clear-discard-local-ssds-at-termination-timestamp
      | --discard-local-ssds-at-termination-timestamp=DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP]
    [--clear-instance-termination-action
      | --instance-termination-action=INSTANCE_TERMINATION_ACTION]
    [--clear-max-run-duration | --max-run-duration=MAX_RUN_DURATION]
    [--clear-node-affinities | --node=NODE
      | --node-affinity-file=PATH_TO_FILE | --node-group=NODE_GROUP]
    [--clear-termination-time | --termination-time=TERMINATION_TIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clear-min-node-cpu` |  |  | Removes the min-node-cpu field from the instance. If specified, the instance min-node-cpu will be cleared. The instance will not be overcommitted and utilize the full CPU count assigned. |
| `--host-error-timeout-seconds` | HOST_ERROR_TIMEOUT_SECONDS |  | The timeout in seconds for host error detection. The value must be set with 30 second increments, with a range of 90 to 330 seconds. If unset, the default behavior of the host error recovery is used. |
| `--local-ssd-recovery-timeout` | LOCAL_SSD_RECOVERY_TIMEOUT |  | Specifies the maximum amount of time a Local Ssd Vm should wait while recovery of the Local Ssd state is attempted. Its value should be in between 0 and 168 hours with hour granularity and the default value being 1 hour. |
| `--maintenance-policy` | one of: MIGRATE The instances should be migrated to a new host |  | Specifies the behavior of the VMs when their host machines undergo maintenance. The default is MIGRATE. For more information, see https://cloud.google.com/compute/docs/instances/host-maintenance-options. MAINTENANCE_POLICY must be one of: MIGRATE The instances should be migrated to a new host. This will temporarily impact the performance of instances during a migration event. TERMINATE The instances should be terminated. |
| `--min-node-cpu` | MIN_NODE_CPU |  | Minimum number of virtual CPUs this instance will consume when running on a sole-tenant node. |
| `--[no-]preemptible` |  |  | If provided, instances will be preemptible and time-limited. Instances might be preempted to free up resources for standard VM instances, and will only be able to run for a limited amount of time. Preemptible instances can not be restarted and will not migrate. Use --preemptible to enable and --no-preemptible to disable. |
| `--provisioning-model` | one of: RESERVATION_BOUND The VM instances run for the entire duration of their associated reservation |  | Specifies the provisioning model for your VM instances. This choice affects the price, availability, and how long your VM instances can run. PROVISIONING_MODEL must be one of: RESERVATION_BOUND The VM instances run for the entire duration of their associated reservation. You can only specify this provisioning model if you want your VM instances to consume a specific reservation with either a calendar reservation mode or a dense deployment type. SPOT Compute Engine may stop a Spot VM instance whenever it needs capacity. Because Spot VM instances don't have a guaranteed runtime, they come at a discounted price. STANDARD The default option. The STANDARD provisioning model gives you full control over your VM instances' runtime. |
| `--[no-]restart-on-failure` |  |  | The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. This option is mutually exclusive with --preemptible. Use --restart-on-failure to enable and --no-restart-on-failure to disable. |
| `--[no-]skip-guest-os-shutdown` |  |  | If enabled, then, when the instance is stopped or deleted, the instance is immediately stopped without giving time to the guest OS to cleanly shut down. Use --skip-guest-os-shutdown to enable and --no-skip-guest-os-shutdown to disable. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To set instance to be terminated during maintenance, run:

    $ gcloud compute instances set-scheduling example-instance \
        --maintenance-policy=TERMINATE --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-scheduling)

---
### `gcloud compute instances set-service-account`

Set a service account and access scopes for a Compute Engine VM instance

gcloud compute instances set-service-account lets you configure a service
account and access scopes for a Compute Engine VM instance.

As a best practice, grant the cloud-platform access scope on your VM
instance. Then, to restrict resource access, grant only the required IAM
roles to the VM instance's service account. For more information, see
https://cloud.google.com/compute/docs/access/create-enable-service-accounts-for-instances#changeserviceaccountandscopes#best_practices.

**Synopsis:**
```
gcloud compute instances set-service-account INSTANCE_NAME [--zone=ZONE]
    [--scopes=[SCOPE,...] | --no-scopes]
    [--service-account=SERVICE_ACCOUNT | --no-service-account]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To set a service account with the cloud-platform scope, run:

    $ gcloud compute instances set-service-account example-instance \
        --scopes=cloud-platform --zone=us-central1-b \
        --service-account=example-account
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/set-service-account)

---
### `gcloud compute instances simulate-maintenance-event`

Simulate host maintenance of VM instances

gcloud compute instances simulate-maintenance-event simulates a host
maintenance event on a Compute Engine VM. For more information, see
https://cloud.google.com/compute/docs/instances/simulating-host-maintenance.

**Synopsis:**
```
gcloud compute instances simulate-maintenance-event INSTANCE_NAMES
    [INSTANCE_NAMES ...] [--async]
    [--with-extended-notifications=WITH_EXTENDED_NOTIFICATIONS]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--with-extended-notifications` | WITH_EXTENDED_NOTIFICATIONS |  | Send an extended notification before simulating a host maintenance event on a Compute Engine VM. |
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To simulate a maintenance event on an instance named test-instance located
in zone us-east1-d, run:

    $ gcloud compute instances simulate-maintenance-event \
        test-instance --zone=us-east1-d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/simulate-maintenance-event)

---
### `gcloud compute instances start`

Start a stopped virtual machine instance

gcloud compute instances start is used to start a stopped Compute Engine
virtual machine. Only a stopped virtual machine can be started.

**Synopsis:**
```
gcloud compute instances start INSTANCE_NAMES [INSTANCE_NAMES ...]
    [--async] [--csek-key-file=FILE] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine resources to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To start a stopped instance named 'example-instance' in zone us-central1-a,
run:

    $ gcloud compute instances start example-instance \
        --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/start)

---
### `gcloud compute instances stop`

Stop a virtual machine instance

gcloud compute instances stop is used to stop a Compute Engine virtual
machine. Stopping a VM performs a clean shutdown, much like invoking the
shutdown functionality of a workstation or laptop.

If a VM has any attached Local SSD disks, you must use the
--discard-local-ssd flag to indicate whether or not the Local SSD data
should be discarded. To stop the VM and preserve the Local SSD data when
you stop the VM by setting --discard-local-ssd=False.

To stop the VM and discard the Local SSD data, specify
--discard-local-ssd=True.

Preserving the Local SSD disk data incurs costs and is subject to
limitations. See
https://cloud.google.com/compute/docs/disks/local-ssd#stop_instance for
more information.

Stopping a VM which is already stopped will return without errors.

**Synopsis:**
```
gcloud compute instances stop INSTANCE_NAMES [INSTANCE_NAMES ...] [--async]
    [--discard-local-ssd[=DISCARD_LOCAL_SSD]] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--discard-local-ssd` | DISCARD_LOCAL_SSD] |  | If set to true, local SSD data is discarded. |
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To stop an instance named test-instance, run:

    $ gcloud compute instances stop test-instance

To stop an instance named test-instance that has a Local SSD, run:

    $ gcloud compute instances stop test-instance \
        --discard-local-ssd=True

Using '--discard-local-ssd' without a value defaults to True.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/stop)

---
### `gcloud compute instances suspend`

Suspend a virtual machine instance

gcloud compute instances suspend is used to suspend a Compute Engine
virtual machine. Suspending a VM is the equivalent of sleep or standby
mode: the guest receives an ACPI S3 suspend signal, after which all VM
state is saved to temporary storage. An instance can only be suspended
while it is in the RUNNING state. A suspended instance will be put in
SUSPENDED state.

Note: A suspended instance can be resumed by running the gcloud compute
instances resume command.

If a VM has any attached Local SSD disks, you can preserve the Local SSD
data when you suspend the VM by setting --discard-local-ssd=False.
Preserving the Local SSD disk data incurs costs and is subject to
limitations.

Limitations:

  o Limitations for suspending a VM:
    https://cloud.google.com/compute/docs/instances/suspend-resume-instance#limitations
  o Limitations for preserving Local SSD data:
    https://cloud.google.com/compute/docs/disks/local-ssd#stop_instance

**Synopsis:**
```
gcloud compute instances suspend INSTANCE_NAMES [INSTANCE_NAMES ...]
    [--async] [--discard-local-ssd[=DISCARD_LOCAL_SSD]] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAMES [INSTANCE_NAMES ...]
   Names of the instances to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--discard-local-ssd` | DISCARD_LOCAL_SSD] |  | If set to true, local SSD data is discarded. |
| `--zone` | ZONE |  | Zone of the instances to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To suspend an instance named test-instance, run:

    $ gcloud compute instances suspend test-instance

To suspend an instance named test-instance that has a Local SSD, run:

    $ gcloud compute instances suspend test-instance \
        --discard-local-ssd=True

Using --discard-local-ssd without a value defaults to True.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/suspend)

---
### `gcloud compute instances tail-serial-port-output`

Periodically fetch new output from a virtual machine instance's serial port and display it as it becomes available

gcloud compute instances tail-serial-port-output is used to tail the output
from a Compute Engine virtual machine instance's serial port. The serial
port output from the instance will be printed to standard output. This
information can be useful for diagnostic purposes.

**Synopsis:**
```
gcloud compute instances tail-serial-port-output INSTANCE_NAME
    [--port=PORT] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--port` | PORT |  | Instances can support up to four serial port outputs, numbered 1 through 4. By default, this command will return the output of the first serial port. Setting this flag will return the output of the requested serial port. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To fetch new output from instance's serial port and display it, run:

    $ gcloud compute instances tail-serial-port-output \
        example-instance --zone=us-central1-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/tail-serial-port-output)

---
### `gcloud compute instances update`

Update a Compute Engine virtual machine

gcloud compute instances update updates labels and requested CPU Platform
for a Compute Engine virtual machine.

**Synopsis:**
```
gcloud compute instances update INSTANCE_NAME [--[no-]deletion-protection]
    [--[no-]enable-display-device] [--min-cpu-platform=PLATFORM]
    [--[no-]shielded-integrity-monitoring]
    [--shielded-learn-integrity-policy] [--[no-]shielded-secure-boot]
    [--[no-]shielded-vtpm] [--update-labels=[KEY=VALUE,...]] [--zone=ZONE]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-node-affinities | --node=NODE
      | --node-affinity-file=PATH_TO_FILE | --node-group=NODE_GROUP]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to update. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]deletion-protection` |  |  | Enables deletion protection for the instance. Use --deletion-protection to enable and --no-deletion-protection to disable. |
| `--[no-]enable-display-device` |  |  | Enable a display device on VM instances. Use --enable-display-device to enable and --no-enable-display-device to disable. |
| `--min-cpu-platform` | PLATFORM |  | When specified, the VM will be scheduled on host with specified CPU architecture or a newer one. To list available CPU platforms in given zone, run: $ gcloud compute zones describe ZONE \ --format="value(availableCpuPlatforms)" Default setting is "AUTOMATIC". CPU platform selection is available only in selected zones. You can find more information on-line: https://cloud.google.com/compute/docs/instances/specify-min-cpu-platform |
| `--[no-]shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. This baseline can be updated by using gcloud compute instances update --shielded-learn-integrity-policy. On Shielded VM instances, integrity monitoring is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. For information about monitoring integrity on Shielded VM instances, see https://cloud.google.com/compute/docs/instances/integrity-monitoring." Changes to this setting with the update command only take effect after stopping and starting the instance. Use --shielded-integrity-monitoring to enable and --no-shielded-integrity-monitoring to disable. |
| `--shielded-learn-integrity-policy` |  |  | Causes the instance to re-learn the integrity policy baseline using the current instance configuration. Use this flag after any planned boot-specific changes in the instance configuration, like kernel updates or kernel driver installation. |
| `--[no-]shielded-secure-boot` |  |  | The instance boots with secure boot enabled. On Shielded VM instances, Secure Boot is not enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. Changes to this setting with the update command only take effect after stopping and starting the instance. Use --shielded-secure-boot to enable and --no-shielded-secure-boot to disable. |
| `--[no-]shielded-vtpm` |  |  | The instance boots with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations such as remote attestation, encryption, and sealing of keys. On Shielded VM instances, vTPM is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. Changes to this setting with the update command only take effect after stopping and starting the instance. Use --shielded-vtpm to enable and --no-shielded-vtpm to disable. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--zone` | ZONE |  | Zone of the instance to update. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To modify the instance 'example-instance' in 'us-central1-a' by adding
labels 'k0', with value 'value1' and label 'k1' with value 'value2' and
removing labels with key 'k3', run:

    $ gcloud compute instances update example-instance \
        --zone=us-central1-a --update-labels=k0=value1,k1=value2 \
        --remove-labels=k3

Labels can be used to identify the instance. To list instances with the
'k1:value2' label, run:

    $ gcloud compute instances list --filter='labels.k1:value2'

To list only the labels when describing a resource, use --format to filter
the result:

    $ gcloud compute instances describe example-instance \
        --format="default(labels)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update)

---
### `gcloud compute instances update-access-config`

Update a Compute Engine virtual machine access configuration

gcloud compute instances update-access-config is used to update access
configurations for network interfaces of Compute Engine virtual machines.
IPv4 and IPv6 access configurations cannot be updated together.

**Synopsis:**
```
gcloud compute instances update-access-config INSTANCE_NAME
    [--network-interface=NETWORK_INTERFACE; default="nic0"] [--zone=ZONE]
    [--no-ipv6-public-ptr
      | --ipv6-public-ptr-domain=IPV6_PUBLIC_PTR_DOMAIN]
    [--public-ptr | --no-public-ptr]
    [--public-ptr-domain=PUBLIC_PTR_DOMAIN | --no-public-ptr-domain]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network-interface` | NETWORK_INTERFACE | nic0 | Specifies the name of the network interface which contains the access configuration. If this is not provided, then "nic0" is used as the default. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To update public PTR record in IPv4 access config in network interface
'nic0' of an instance, run:

    $ gcloud compute instances update-access-config example-instance \
        --network-interface=nic0 --zone=us-central1-b --public-ptr \
        --public-ptr-domain=exampledomain.com.

To update public PTR record in IPv6 access config in default network
interface 'nic0' of an instance, run:

    $ gcloud compute instances update-access-config example-instance \
        --zone=us-central1-b --ipv6-public-ptr-domain=exampledomain.com.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update-access-config)

---
### `gcloud compute instances update-container`

Updates Compute Engine virtual machine instances running container images

(DEPRECATED) The option to deploy a container during VM creation using the
container startup agent is deprecated. Use alternative services to run
containers on your VMs. Learn more at
https://cloud.google.com/compute/docs/containers/migrate-containers.

gcloud compute instances update-container updates Compute Engine virtual
machines that runs a Docker image. For example:

    $ gcloud compute instances update-container instance-1 \
        --zone us-central1-a         \
        --container-image=gcr.io/google-containers/busybox

updates an instance called instance-1, in the us-central1-a zone, to run
the 'busybox' image.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute instances update-container INSTANCE_NAME
    [--container-image=CONTAINER_IMAGE]
    [--container-mount-disk=[mode=MODE],
      [mount-path=MOUNT-PATH],[name=NAME],[partition=PARTITION]]
    [--container-privileged] [--container-restart-policy=POLICY]
    [--container-stdin] [--container-tty]
    [--[no-]shielded-integrity-monitoring]
    [--shielded-learn-integrity-policy] [--[no-]shielded-secure-boot]
    [--[no-]shielded-vtpm] [--zone=ZONE]
    [--clear-container-args | --container-arg=CONTAINER_ARG]
    [--clear-container-command | --container-command=CONTAINER_COMMAND]
    [--container-env=[KEY=VALUE, ...,...]
      --container-env-file=CONTAINER_ENV_FILE
      --remove-container-env=[KEY,...]]
    [--container-mount-host-path=[host-path=HOSTPATH,
      mount-path=MOUNTPATH[,mode=MODE],...]
      --container-mount-tmpfs=[mount-path=MOUNTPATH,...]
      --remove-container-mounts=[MOUNTPATH[,MOUNTPATH,...],...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to update. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--container-image` | CONTAINER_IMAGE |  | Sets container image in the declaration to the specified value. Empty string is not allowed. |
| `--container-mount-disk` | [mode=MODE],[mount-path=MOUNT-PATH],[name=NAME],[partition=PARTITION] |  | Mounts a disk to the container by using mount-path or updates how the volume is mounted if the same mount path has already been declared. The disk must already be attached to the instance with a device-name that matches the disk name. Multiple flags are allowed. name Name of the disk. Can be omitted if exactly one additional disk is attached to the instance. The name of the single additional disk will be used by default. mount-path Path on container to mount to. Mount paths with spaces and commas (and other special characters) are not supported by this command. partition Optional. The partition of the disk to mount. Multiple partitions of a disk can be mounted. mode Volume mount mode: rw (read/write) or ro (read-only). Defaults to rw. Fails if the disk mode is ro and volume mount mode is rw. |
| `--container-privileged` |  |  | Sets permission to run container to the specified value. |
| `--container-restart-policy` | one of: never, on-failure, always |  | Sets container restart policy to the specified value. POLICY must be one of: never, on-failure, always. |
| `--container-stdin` |  |  | Sets configuration whether to keep container STDIN always open to the specified value. |
| `--container-tty` |  |  | Sets configuration whether to allocate a pseudo-TTY for the container to the specified value. |
| `--[no-]shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. This baseline can be updated by using gcloud compute instances update-container --shielded-learn-integrity-policy. On Shielded VM instances, integrity monitoring is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. For information about monitoring integrity on Shielded VM instances, see https://cloud.google.com/compute/docs/instances/integrity-monitoring." Changes to this setting with the update command only take effect after stopping and starting the instance. Use --shielded-integrity-monitoring to enable and --no-shielded-integrity-monitoring to disable. |
| `--shielded-learn-integrity-policy` |  |  | Causes the instance to re-learn the integrity policy baseline using the current instance configuration. Use this flag after any planned boot-specific changes in the instance configuration, like kernel updates or kernel driver installation. |
| `--[no-]shielded-secure-boot` |  |  | The instance boots with secure boot enabled. On Shielded VM instances, Secure Boot is not enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. Changes to this setting with the update command only take effect after stopping and starting the instance. Use --shielded-secure-boot to enable and --no-shielded-secure-boot to disable. |
| `--[no-]shielded-vtpm` |  |  | The instance boots with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations such as remote attestation, encryption, and sealing of keys. On Shielded VM instances, vTPM is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. Changes to this setting with the update command only take effect after stopping and starting the instance. Use --shielded-vtpm to enable and --no-shielded-vtpm to disable. |
| `--zone` | ZONE |  | Zone of the instance to update. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--container-env` | [KEY=VALUE, ...,...] |  | _[Cannot be used in the same command with --clear-container-command.]_ Update environment variables KEY with value VALUE passed to container. * Sets KEY to the specified value. * Adds KEY = VALUE, if KEY is not yet declared. * Only the last value of KEY is taken when KEY is repeated more than once. Values, declared with --container-env flag override those with the same KEY from file, provided in --container-env-file. |
| `--container-env-file` | CONTAINER_ENV_FILE |  | _[Cannot be used in the same command with --clear-container-command.]_ Update environment variables from a file. Same update rules as for --container-env apply. Values, declared with --container-env flag override those with the same KEY from file. File with environment variables declarations in format used by docker (almost). This means: * Lines are in format KEY=VALUE * Values must contain equality signs. * Variables without values are not supported (this is different from docker format). * If # is first non-whitespace character in a line the line is ignored as a comment. |
| `--remove-container-env` | [KEY,...] |  | _[Cannot be used in the same command with --clear-container-command.]_ Removes environment variables KEY from container declaration Does nothing, if a variable is not present. |
| `--container-mount-host-path` | [host-path=HOSTPATH,mount-path=MOUNTPATH[,mode=MODE],...] |  | _[Cannot be used in the same command with --clear-container-command.]_ Mounts a volume by using host-path. * Adds a volume, if mount-path is not yet declared. * Replaces a volume, if mount-path is declared. All parameters (host-path, mount-path, mode) are completely replaced. host-path Path on host to mount from. mount-path Path on container to mount to. Mount paths with spaces and commas (and other special characters) are not supported by this command. mode Volume mount mode: rw (read/write) or ro (read-only). Default: rw. |
| `--container-mount-tmpfs` | [mount-path=MOUNTPATH,...] |  | _[Cannot be used in the same command with --clear-container-command.]_ Mounts empty tmpfs into container at MOUNTPATH. mount-path Path on container to mount to. Mount paths with spaces and commas (and other special characters) are not supported by this command. |
| `--remove-container-mounts` | [MOUNTPATH[,MOUNTPATH,...],...] |  | _[Cannot be used in the same command with --clear-container-command.]_ Removes volume mounts (host-path, tmpfs, disk) with mountPath: MOUNTPATH from container declaration. Does nothing, if a volume mount is not declared. |


**Examples:**
```bash
To run the gcr.io/google-containers/busybox image on an instance named
'instance-1' that executes 'echo "Hello world"' as a run command, run:

    $ gcloud compute instances update-container instance-1 \
        --container-image=gcr.io/google-containers/busybox \
        --container-command='echo "Hello world"'

To run the gcr.io/google-containers/busybox image in privileged mode, run:

    $ gcloud compute instances update-container instance-1 \
        --container-image=gcr.io/google-containers/busybox \
        --container-privileged
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update-container)

---
### `gcloud compute instances update-from-file`

Update a Compute Engine virtual machine instance using a configuration file

Update a Compute Engine virtual machine instance using a configuration
file. For more information, see
https://cloud.google.com/compute/docs/instances/update-instance-properties.

**Synopsis:**
```
gcloud compute instances update-from-file INSTANCE_NAME
    [--minimal-action=MINIMAL_ACTION]
    [--most-disruptive-allowed-action=MOST_DISRUPTIVE_ALLOWED_ACTION]
    [--source=SOURCE] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to update. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--minimal-action` | MINIMAL_ACTION |  | If specified, this action or higher level action is performed on the instance irrespective of what action is required for the update to take effect. If not specified, then Compute Engine acts based on the minimum action required. |
| `--most-disruptive-allowed-action` | MOST_DISRUPTIVE_ALLOWED_ACTION |  | If specified, Compute Engine returns an error if the update requires a higher action to be applied to the instance. If not specified, the default will be REFRESH. |
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\Instance.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |
| `--zone` | ZONE |  | Zone of the instance to update. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
A virtual machine instance can be updated by running:

    $ gcloud compute instances update-from-file my-instance \
        --source=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/update-from-file)

---

## `gcloud compute instances bulk` — manipulate multiple Compute Engine virtual machines with single command executions
### `gcloud compute instances bulk create`

Create multiple Compute Engine virtual machines

gcloud compute instances bulk create facilitates the creation of multiple
Compute Engine virtual machines with a single command. They offer a number
of advantages compared to the single instance creation command. This
includes the ability to automatically pick a zone in which to create
instances based on resource availability, the ability to specify that the
request be atomic or best-effort, and a faster rate of instance creation.

**Synopsis:**
```
gcloud compute instances bulk create
    (--name-pattern=NAME_PATTERN | --predefined-names=[INSTANCE_NAME,...])
    (--region=REGION | --zone=ZONE)
    [--accelerator=[count=COUNT],[type=TYPE]] [--no-address] [--async]
    [--no-boot-disk-auto-delete]
    [--boot-disk-device-name=BOOT_DISK_DEVICE_NAME]
    [--boot-disk-interface=BOOT_DISK_INTERFACE]
    [--boot-disk-provisioned-iops=BOOT_DISK_PROVISIONED_IOPS]
    [--boot-disk-provisioned-throughput=BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--boot-disk-size=BOOT_DISK_SIZE] [--boot-disk-type=BOOT_DISK_TYPE]
    [--can-ip-forward] [--count=COUNT] [--create-disk=[PROPERTY=VALUE,...]]
    [--description=DESCRIPTION]
    [--discard-local-ssds-at-termination-timestamp=DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP]
    [--disk=[boot=BOOT],
      [device-name=DEVICE-NAME],[name=NAME],[scope=SCOPE]]
    [--[no-]enable-nested-virtualization] [--[no-]enable-uefi-networking]
    [--erase-windows-vss-signature]
    [--host-error-timeout-seconds=HOST_ERROR_TIMEOUT_SECONDS]
    [--instance-termination-action=INSTANCE_TERMINATION_ACTION]
    [--labels=[KEY=VALUE,...]]
    [--local-ssd=[device-name=DEVICE-NAME],
      [interface=INTERFACE],[size=SIZE]]
    [--local-ssd-recovery-timeout=LOCAL_SSD_RECOVERY_TIMEOUT]
    [--location-policy=[ZONE=POLICY,...]] [--machine-type=MACHINE_TYPE]
    [--max-count-per-zone=[ZONE=MAX_COUNT_PER_ZONE,...]]
    [--max-run-duration=MAX_RUN_DURATION]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]]
    [--metadata-from-file=KEY=LOCAL_FILE_PATH,[...]]
    [--min-count=MIN_COUNT] [--min-cpu-platform=PLATFORM]
    [--min-node-cpu=MIN_NODE_CPU] [--network=NETWORK]
    [--network-interface=[PROPERTY=VALUE,...]]
    [--network-performance-configs=[PROPERTY=VALUE,...]]
    [--network-tier=NETWORK_TIER]
    [--performance-monitoring-unit=PERFORMANCE_MONITORING_UNIT]
    [--post-key-revocation-action-type=POLICY] [--preemptible]
    [--provisioning-model=PROVISIONING_MODEL]
    [--resource-manager-tags=[KEY=VALUE,...]]
    [--resource-policies=[RESOURCE_POLICY,...]] [--no-restart-on-failure]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--[no-]skip-guest-os-shutdown]
    [--source-instance-template=SOURCE_INSTANCE_TEMPLATE]
    [--stack-type=STACK_TYPE] [--subnet=SUBNET] [--tags=TAG,[TAG,...]]
    [--target-distribution-shape=SHAPE]
    [--termination-time=TERMINATION_TIME]
    [--threads-per-core=THREADS_PER_CORE] [--turbo-mode=TURBO_MODE]
    [--visible-core-count=VISIBLE_CORE_COUNT]
    [--boot-disk-kms-key=BOOT_DISK_KMS_KEY
      : --boot-disk-kms-keyring=BOOT_DISK_KMS_KEYRING
      --boot-disk-kms-location=BOOT_DISK_KMS_LOCATION
      --boot-disk-kms-project=BOOT_DISK_KMS_PROJECT]
    [--confidential-compute
      | --confidential-compute-type=CONFIDENTIAL_COMPUTE_TYPE]
    [--custom-cpu=CUSTOM_CPU --custom-memory=CUSTOM_MEMORY
      : --custom-extensions --custom-vm-type=CUSTOM_VM_TYPE]
    [--image-project=IMAGE_PROJECT --image=IMAGE
      | --image-family=IMAGE_FAMILY | --source-snapshot=SOURCE_SNAPSHOT]
    [--maintenance-policy=MAINTENANCE_POLICY
      | --on-host-maintenance=MAINTENANCE_POLICY]
    [--public-dns | --no-public-dns]
    [--reservation=RESERVATION
      --reservation-affinity=RESERVATION_AFFINITY; default="any"]
    [--scopes=[SCOPE,...] | --no-scopes]
    [--service-account=SERVICE_ACCOUNT | --no-service-account]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name-pattern` | NAME_PATTERN |  | _[Exactly one of these must be specified:]_ Name pattern for generating instance names. Specify a pattern with a single sequence of hash (#) characters that will be replaced with generated sequential numbers of instances. E.g. name pattern of 'instance-###' will generate instance names 'instance-001', 'instance-002', and so on, until the number of virtual machines specified using --count is reached. If instances matching name pattern exist, the new instances will be assigned names to avoid clashing with the existing ones. E.g. if there exists instance-123, the new instances will start at instance-124 and increment from there. |
| `--predefined-names` | [INSTANCE_NAME,...] |  | _[Exactly one of these must be specified:]_ List of predefined names for the Compute Engine virtual machines being created. If --count is specified alongside this flag, provided count must equal the amount of names provided to this flag. If --count is not specified, the number of virtual machines created will equal the number of names provided. |
| `--region` | REGION |  | _[Exactly one of these must be specified:]_ Region in which to create the Compute Engine virtual machines. Compute Engine will select a zone in which to create all virtual machines. |
| `--zone` | ZONE |  | _[Exactly one of these must be specified:]_ Zone in which to create the Compute Engine virtual machines. A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Attaches accelerators (e.g. GPUs) to the instances. type The specific type (e.g. nvidia-tesla-t4 for NVIDIA T4) of accelerator to attach to the instances. Use 'gcloud compute accelerator-types list' to learn about all available accelerator types. count Number of accelerators to attach to each instance. The default value is 1. |
| `--no-address` |  |  | If provided, the instances are not assigned external IP addresses. To pull container images, you must configure private Google access if using Container Registry or configure Cloud NAT for instances to access container images directly. For more information, see: * https://cloud.google.com/vpc/docs/configure-private-google-access * https://cloud.google.com/nat/docs/using-nat |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--boot-disk-auto-delete` |  |  | Automatically delete boot disks when their instances are deleted. Enabled by default, use --no-boot-disk-auto-delete to disable. |
| `--boot-disk-device-name` | BOOT_DISK_DEVICE_NAME |  | The name the guest operating system will see for the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). |
| `--boot-disk-interface` | BOOT_DISK_INTERFACE |  | Indicates the interface to use for the boot disk. The value must be one of the following: * SCSI * NVME |
| `--boot-disk-provisioned-iops` | BOOT_DISK_PROVISIONED_IOPS |  | Indicates how many IOPS to provision for the disk. This sets the number of I/O operations per second that the disk can handle. |
| `--boot-disk-provisioned-throughput` | BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates how much throughput to provision for the disk. This sets the number of throughput mb per second that the disk can handle. |
| `--boot-disk-size` | BOOT_DISK_SIZE |  | The size of the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. Disk size must be a multiple of 1 GB. Default size unit is GB. |
| `--boot-disk-type` | BOOT_DISK_TYPE |  | The type of the boot disk. This option can only be specified if a new boot disk is being created (as opposed to mounting an existing persistent disk). To get a list of available disk types, run $ gcloud compute disk-types list. |
| `--can-ip-forward` |  |  | If provided, allows the instances to send and receive packets with non-matching destination or source IP addresses. |
| `--count` | COUNT |  | Number of Compute Engine virtual machines to create. If specified, and --predefined-names is specified, count must equal the amount of names provided to --predefined-names. If not specified, the number of virtual machines created will equal the number of names provided to --predefined-names. |
| `--create-disk` | [PROPERTY=VALUE,...] |  | Creates and attaches persistent disks to the instances. name Specifies the name of the disk. This option cannot be specified if more than one instance is being created. description Optional textual description for the disk being created. mode Specifies the mode of the disk. Supported options are ro for read-only and rw for read-write. If omitted, rw is used as a default. image Specifies the name of the image that the disk will be initialized with. A new disk will be created based on the given image. To view a list of public images and projects, run $ gcloud compute images list. It is best practice to use image when a specific version of an image is needed. If both image and image-family flags are omitted a blank disk will be created. image-family The image family for the operating system that the boot disk will be initialized with. Compute Engine offers multiple Linux distributions, some of which are available as both regular and Shielded VM images. When a family is specified instead of an image, the latest non-deprecated image associated with that family is used. It is best practice to use --image-family when the latest version of an image is needed. image-project The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available image projects can be generated by running gcloud compute images list. + If specifying one of our public images, image-project must be provided. + If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. + If not specified and either image or image-family is provided, the current default project is used. size The size of the disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. Disk size must be a multiple of 1 GB. If not specified, the default image size will be used for the new disk. type The type of the disk. To get a list of available disk types, run $ gcloud compute disk-types list. The default disk type is pd-standard. device-name An optional name to display the disk name in the guest operating system. If omitted, a device name of the form persistent-disk-N is used. provisioned-iops Indicates how many IOPS to provision for the disk. This sets the number of I/O operations per second that the disk can handle. Value must be between 10,000 and 120,000. provisioned-throughput Indicates how much throughput to provision for the disk. This sets the number of throughput mb per second that the disk can handle. disk-resource-policy Resource policy to apply to the disk. Specify a full or partial URL. For example: + https://www.googleapis.com/compute/v1/projects/my-project/regions/us-central1/resourcePolicies/my-resource-policy + projects/my-project/regions/us-central1/resourcePolicies/my-resource-policy For more information, see the following docs: + https://cloud.google.com/sdk/gcloud/reference/beta/compute/resource-policies/ + https://cloud.google.com/compute/docs/disks/scheduled-snapshots auto-delete If yes, this persistent disk will be automatically deleted when the instance is deleted. However, if the disk is later detached from the instance, this option won't apply. The default value for this is yes. architecture Specifies the architecture or processor type that this disk can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. storage-pool The name of the storage pool in which the new disk is created. The new disk and the storage pool must be in the same location. interface The interface to use with the disk. The value must be one of the following: + SCSI + NVME boot If yes, indicates that this is a boot disk. The instance will use the first partition of the disk for its root file system. The default value for this is no. kms-key Fully qualified Cloud KMS cryptokey name that will protect the disk. This can either be the fully qualified path or the name. The fully qualified Cloud KMS cryptokey name format is: projects/<kms-project>/locations/<kms-location>/keyRings/<kms-keyring>/ cryptoKeys/<key-name>. If the value is not fully qualified then kms-location, kms-keyring, and optionally kms-project are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. kms-project Project that contains the Cloud KMS cryptokey that will protect the disk. If the project is not specified then the project where the disk is being created will be used. If this flag is set then key-location, kms-keyring, and kms-key are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. kms-location Location of the Cloud KMS cryptokey to be used for protecting the disk. All Cloud KMS cryptokeys are reside in a 'location'. To get a list of possible locations run 'gcloud kms locations list'. If this flag is set then kms-keyring and kms-key are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. kms-keyring The keyring which contains the Cloud KMS cryptokey that will protect the disk. If this flag is set then kms-location and kms-key are required. See https://cloud.google.com/compute/docs/disks/customer-managed-encryption for more details. source-snapshot The source disk snapshot that will be used to create the disk. You can provide this as a full URL to the snapshot or just the snapshot name. For example, the following are valid values: + https://compute.googleapis.com/compute/v1/projects/myproject/global/snapshots/snapshot + snapshot image-csek-required Specifies the name of the CSK protected image that the disk will be initialized with. A new disk will be created based on the given image. To view a list of public images and projects, run $ gcloud compute images list. It is best practice to use image when a specific version of an image is needed. If both image and image-family flags are omitted a blank disk will be created. Must be specified with image-csek-key-file. image-csek-key-file Path to a Customer-Supplied Encryption Key (CSEK) key file for the image. Must be specified with image-csek-required. replica-zones Required for each regional disk associated with the instance. Specify the URLs of the zones where the disk should be replicated to. You must provide exactly two replica zones, and one zone must be the same as the instance zone. |
| `--description` | DESCRIPTION |  | Specifies a textual description of the instances. |
| `--discard-local-ssds-at-termination-timestamp` | DISCARD_LOCAL_SSDS_AT_TERMINATION_TIMESTAMP |  | Required to be set to true and only allowed for VMs that have one or more local SSDs, use --instance-termination-action=STOP, and use either --max-run-duration or --termination-time. This flag indicates the value that you want Compute Engine to use for the --discard-local-ssd flag in the automatic gcloud compute instances stop command. This flag only supports the true value, which discards local SSD data when automatically stopping this VM during its terminationTimestamp. For more information about the --discard-local-ssd flag, see https://cloud.google.com/compute/docs/disks/local-ssd#stop_instance. |
| `--disk` | [boot=BOOT],[device-name=DEVICE-NAME],[name=NAME],[scope=SCOPE] |  | Attaches persistent disks to the instances. The disks specified must already exist. name The disk to attach to the instances. boot If yes, indicates that this is a boot disk. The virtual machines will use the first partition of the disk for their root file systems. The default value for this is no. device-name An optional name to display the disk name in the guest operating system. If omitted, a device name of the form persistent-disk-N is used. scope Can be zonal or regional. If zonal, the disk is interpreted as a zonal disk in the same zone as the instance (default). If regional, the disk is interpreted as a regional disk in the same region as the instance. The default value for this is zonal. |
| `--[no-]enable-nested-virtualization` |  |  | If set to true, enables nested virtualization for the instance. Use --enable-nested-virtualization to enable and --no-enable-nested-virtualization to disable. |
| `--[no-]enable-uefi-networking` |  |  | If set to true, enables UEFI networking for the instance creation. Use --enable-uefi-networking to enable and --no-enable-uefi-networking to disable. |
| `--erase-windows-vss-signature` |  |  | Specifies whether the disk restored from source snapshots or source machine image should erase Windows specific VSS signature. See https://cloud.google.com/sdk/gcloud/reference/compute/disks/snapshot#--guest-flush |
| `--host-error-timeout-seconds` | HOST_ERROR_TIMEOUT_SECONDS |  | The timeout in seconds for host error detection. The value must be set with 30 second increments, with a range of 90 to 330 seconds. If unset, the default behavior of the host error recovery is used. |
| `--instance-termination-action` | one of: DELETE Permanently delete the VM |  | Specifies the termination action that will be taken upon VM preemption (--provisioning-model=SPOT) or automatic instance termination (--max-run-duration or --termination-time). INSTANCE_TERMINATION_ACTION must be one of: DELETE Permanently delete the VM. STOP Default only for Spot VMs. Stop the VM without preserving memory. The VM can be restarted later. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--local-ssd` | [device-name=DEVICE-NAME],[interface=INTERFACE],[size=SIZE] |  | Attaches a local SSD to the instances. device-name Optional. A name that indicates the disk name the guest operating system will see. Can only be specified if interface is SCSI. If omitted, a device name of the form local-ssd-N will be used. interface Optional. The kind of disk interface exposed to the VM for this SSD. Valid values are SCSI and NVME. SCSI is the default and is supported by more guest operating systems. NVME might provide higher performance. size Optional. The only valid value is 375GB. Specify the --local-ssd flag multiple times if you need multiple 375GB local SSD partitions. You can specify a maximum of 24 local SSDs for a maximum of 9TB attached to an instance. |
| `--local-ssd-recovery-timeout` | LOCAL_SSD_RECOVERY_TIMEOUT |  | Specifies the maximum amount of time a Local Ssd Vm should wait while recovery of the Local Ssd state is attempted. Its value should be in between 0 and 168 hours with hour granularity and the default value being 1 hour. |
| `--location-policy` | [ZONE=POLICY,...] |  | Policy for which zones to include or exclude during bulk instance creation within a region. Policy is defined as a list of key-value pairs, with the key being the zone name, and value being the applied policy. Available policies are allow and deny. Default for zones if left unspecified is allow. Example: gcloud compute instances bulk create --name-pattern=example-### --count=5 --region=us-east1 --location-policy=us-east1-b=allow,us-east1-c=deny |
| `--machine-type` | MACHINE_TYPE |  | Specifies the machine type used for the instances. To get a list of available machine types, run 'gcloud compute machine-types list'. If unspecified, the default type is n1-standard-1. |
| `--max-count-per-zone` | [ZONE=MAX_COUNT_PER_ZONE,...] |  | Maximum number of instances per zone specified as key-value pairs. The zone name is the key and the max count per zone is the value in that zone. Example: gcloud compute instances bulk create --name-pattern=example-### --count=5 --region=us-east1 --max-count-per-zone=us-east1-b=2,us-east-1-c=1 |
| `--max-run-duration` | MAX_RUN_DURATION |  | Limits how long this VM instance can run, specified as a duration relative to the last time when the VM began running. Format the duration, MAX_RUN_DURATION, as the number of days, hours, minutes, and seconds followed by d, h, m, and s respectively. For example, specify 30m for a duration of 30 minutes or specify 1d2h3m4s for a duration of 1 day, 2 hours, 3 minutes, and 4 seconds. Alternatively, to specify a timestamp, use --termination-time instead. If neither --max-run-duration nor --termination-time is specified (default), the VM instance runs until prompted by a user action or system event. If either is specified, the VM instance is scheduled to be automatically terminated at the VM's termination timestamp (terminationTimestamp) using the action specified by --instance-termination-action. Note: The terminationTimestamp is removed whenever the VM is stopped or suspended and redefined whenever the VM is rerun. For --max-run-duration specifically, the terminationTimestamp is the sum of MAX_RUN_DURATION and the time when the VM last entered the RUNNING state, which changes whenever the VM is rerun. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. Each metadata key must be unique and have a max of 128 bytes in length. Each value must have a max of 256 KB in length. Multiple arguments can be passed to this flag, e.g., --metadata key-1=value-1,key-2=value-2,key-3=value-3. The combined total size for all metadata entries is 512 KB. In images that have Compute Engine tools installed on them, such as the official images (https://cloud.google.com/compute/docs/images), the following metadata keys have special meanings: startup-script Specifies a script that will be executed by the instances once they start running. For convenience, --metadata-from-file can be used to pull the value from a file. startup-script-url Same as startup-script except that the script contents are pulled from a publicly-accessible location on the web. For startup scripts on Windows instances, the following metadata keys have special meanings: windows-startup-script-url, windows-startup-script-cmd, windows-startup-script-bat, windows-startup-script-ps1, sysprep-specialize-script-url, sysprep-specialize-script-cmd, sysprep-specialize-script-bat, and sysprep-specialize-script-ps1. For more information, see Running startup scripts (https://cloud.google.com/compute/docs/startupscript). |
| `--metadata-from-file` | KEY=LOCAL_FILE_PATH,[...] |  | Same as --metadata except that the value for the entry will be read from a local file. This is useful for values that are too large such as startup-script contents. |
| `--min-count` | MIN_COUNT |  | The minimum number of Compute Engine virtual machines that must be successfully created for the operation to be considered a success. If the operation successfully creates as many virtual machines as specified here they will be persisted, otherwise the operation rolls back and deletes all created virtual machines. If not specified, this value is equal to --count. |
| `--min-cpu-platform` | PLATFORM |  | When specified, the VM will be scheduled on host with specified CPU architecture or a newer one. To list available CPU platforms in given zone, run: $ gcloud compute zones describe ZONE \ --format="value(availableCpuPlatforms)" Default setting is "AUTOMATIC". CPU platform selection is available only in selected zones. You can find more information on-line: https://cloud.google.com/compute/docs/instances/specify-min-cpu-platform |
| `--min-node-cpu` | MIN_NODE_CPU |  | Minimum number of virtual CPUs this instance will consume when running on a sole-tenant node. |
| `--network` | NETWORK |  | Specifies the network that the VM instances are a part of. If --subnet is also specified, subnet must be a subnetwork of the network specified by this --network flag. If neither is specified, the default network is used. |
| `--network-interface` | one of: `PREMIUM`, `STANDARD` |  | Adds a network interface to the instance. Mutually exclusive with any of these flags: --network, --network-tier, --no-address, --subnet, --stack-type. This flag can be repeated to specify multiple network interfaces. *network*::: Specifies the network that the interface will be part of. If subnet is also specified it must be subnetwork of this network. If neither is specified, this defaults to the "default" network. *network-tier*::: Specifies the network tier of the interface. `_NETWORK_TIER_` must be one of: `PREMIUM`, `STANDARD`. The default value is `PREMIUM`. *subnet*::: Specifies the subnet that the interface will be part of. If network key is also specified this must be a subnetwork of the specified network. *nic-type*::: Specifies the Network Interface Controller (NIC) type for the interface. `_NIC_TYPE_` must be one of: `GVNIC`, `VIRTIO_NET`. no-address If specified the interface will have no external IP. If not specified instances will get ephemeral IPs. queue-count Specifies the networking queue count for this interface. Both Rx and Tx queues will be set to this number. If it's not specified, a default queue count will be assigned. See https://cloud.google.com/compute/docs/network-bandwidth#rx-tx for more details. stack-type Specifies whether IPv6 is enabled on the interface. STACK_TYPE must be one of: IPV4_ONLY, IPV4_IPV6, IPV6_ONLY. The default value is IPV4_ONLY. |
| `--network-performance-configs` | [PROPERTY=VALUE,...] |  | Configures network performance settings for the instance. If this flag is not specified, the instance will be created with its default network performance configuration. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [DEFAULT,TIER_1] |
| `--network-tier` | one of: PREMIUM, STANDARD |  | Specifies the network tier that will be used to configure the instance. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. |
| `--performance-monitoring-unit` | one of: architectural This enables architecturally defined non-last level cache (LLC) events |  | The type of performance monitoring counters (PMCs) to enable in the instance. PERFORMANCE_MONITORING_UNIT must be one of: architectural This enables architecturally defined non-last level cache (LLC) events. enhanced This enables most documented core/L2 and LLC events. standard This enables most documented core/L2 events. |
| `--post-key-revocation-action-type` | one of: noop No operation is performed |  | Specifies the behavior of the instance when the KMS key of one of its attached disks is revoked. The default is noop. POLICY must be one of: noop No operation is performed. shutdown The instance is shut down when the KMS key of one of its attached disks is revoked. |
| `--preemptible` |  |  | If provided, instances will be preemptible and time-limited. Instances might be preempted to free up resources for standard VM instances, and will only be able to run for a limited amount of time. Preemptible instances can not be restarted and will not migrate. |
| `--provisioning-model` | one of: RESERVATION_BOUND The VM instances run for the entire duration of their associated reservation |  | Specifies the provisioning model for your VM instances. This choice affects the price, availability, and how long your VM instances can run. PROVISIONING_MODEL must be one of: RESERVATION_BOUND The VM instances run for the entire duration of their associated reservation. You can only specify this provisioning model if you want your VM instances to consume a specific reservation with either a calendar reservation mode or a dense deployment type. SPOT Compute Engine may stop a Spot VM instance whenever it needs capacity. Because Spot VM instances don't have a guaranteed runtime, they come at a discounted price. STANDARD The default option. The STANDARD provisioning model gives you full control over your VM instances' runtime. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | Specifies a list of resource manager tags to apply to the instance. |
| `--resource-policies` | [RESOURCE_POLICY,...] |  | A list of resource policy names to be added to the instance. The policies must exist in the same region as the instance. |
| `--restart-on-failure` |  |  | The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. Enabled by default, use --no-restart-on-failure to disable. |
| `--shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the instance. The attestation is performed against the integrity policy baseline. This baseline is initially derived from the implicitly trusted boot image when the instance is created. This baseline can be updated by using gcloud compute instances update --shielded-learn-integrity-policy. On Shielded VM instances, integrity monitoring is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. For information about monitoring integrity on Shielded VM instances, see https://cloud.google.com/compute/docs/instances/integrity-monitoring." |
| `--shielded-secure-boot` |  |  | The instance boots with secure boot enabled. On Shielded VM instances, Secure Boot is not enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. |
| `--shielded-vtpm` |  |  | The instance boots with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations such as remote attestation, encryption, and sealing of keys. On Shielded VM instances, vTPM is enabled by default. For information about how to modify Shielded VM options, see https://cloud.google.com/compute/docs/instances/modifying-shielded-vm. |
| `--[no-]skip-guest-os-shutdown` |  |  | If enabled, then, when the instance is stopped or deleted, the instance is immediately stopped without giving time to the guest OS to cleanly shut down. Use --skip-guest-os-shutdown to enable and --no-skip-guest-os-shutdown to disable. |
| `--source-instance-template` | SOURCE_INSTANCE_TEMPLATE |  | The name of the instance template that the instance will be created from. Users can override fields by specifying other flags. |
| `--stack-type` | STACK_TYPE |  | Specifies whether IPv6 is enabled on the default network interface. If not specified, IPV4_ONLY will be used. STACK_TYPE must be one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses IPV4_ONLY The network interface will be assigned IPv4 addresses IPV6_ONLY The network interface will be assigned IPv6 addresses |
| `--subnet` | SUBNET |  | Specifies the subnet that the VM instances are a part of. If --network is also specified, subnet must be a subnetwork of the network specified by the --network flag. |
| `--tags` | TAG,[TAG,...] |  | Specifies a list of tags to apply to the instance. These tags allow network firewall rules and routes to be applied to specified VM instances. See gcloud compute firewall-rules create(1) for more details. To read more about configuring network tags, read this guide: https://cloud.google.com/vpc/docs/add-remove-network-tags To list instances with their respective status and tags, run: $ gcloud compute instances list \ --format='table(name,status,tags.list())' To list instances tagged with a specific tag, tag1, run: $ gcloud compute instances list --filter='tags:tag1' |
| `--target-distribution-shape` | one of: ANY Allows creating VMs in multiple zones if one zone cannot accommodate all the requested VMs |  | Specifies whether and how to distribute VMs across multiple zones in a region or to enforce placement of VMs in a single zone. The default shape is ANY_SINGLE_ZONE. SHAPE must be one of: ANY Allows creating VMs in multiple zones if one zone cannot accommodate all the requested VMs. The resulting distribution shapes can vary. ANY_SINGLE_ZONE Enforces VM placement in one allowed zone. Use this to avoid cross-zone network egress or to reduce network latency. This is the default value. BALANCED Allows distribution of VMs in zones where resources are available while distributing VMs as evenly as possible across selected zones to minimize the impact of zonal failures. Recommended for highly available serving or batch workloads. |
| `--termination-time` | TERMINATION_TIME |  | Limits how long this VM instance can run, specified as a time. Format the time, TERMINATION_TIME, as a RFC 3339 timestamp. For more information, see https://tools.ietf.org/html/rfc3339. Alternatively, to specify a duration, use --max-run-duration instead. If neither --termination-time nor --max-run-duration is specified (default), the VM instance runs until prompted by a user action or system event. If either is specified, the VM instance is scheduled to be automatically terminated at the VM's termination timestamp (terminationTimestamp) using the action specified by --instance-termination-action. Note: The terminationTimestamp is removed whenever the VM is stopped or suspended and redefined whenever the VM is rerun. For --termination-time specifically, the terminationTimestamp remains the same whenever the VM is rerun, but any requests to rerun the VM fail if the specified timestamp is in the past. |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of visible threads per physical core. To disable simultaneous multithreading (SMT) set this to 1. Valid values are: 1 or 2. For more information about configuring SMT, see: https://cloud.google.com/compute/docs/instances/configuring-simultaneous-multithreading. |
| `--turbo-mode` | TURBO_MODE |  | Turbo mode to use for the instance. Supported modes include: * ALL_CORE_MAX To achieve all-core-turbo frequency for more consistent CPU performance, set the field to ALL_CORE_MAX. The field is unset by default, which results in maximum performance single-core boosting. |
| `--visible-core-count` | VISIBLE_CORE_COUNT |  | The number of physical cores to expose to the instance's guest operating system. The number of virtual CPUs visible to the instance's guest operating system is this number of cores multiplied by the instance's count of visible threads per physical core. |
| `--image-project` | IMAGE_PROJECT |  | _[https://cloud.google.com/compute/docs/general-purpose-machines#custom_machine_types]_ The Google Cloud project against which all image and image family references will be resolved. It is best practice to define image-project. A full list of available projects can be generated by running gcloud projects list. * If specifying one of our public images, image-project must be provided. * If there are several of the same image-family value in multiple projects, image-project must be specified to clarify the image to be used. * If not specified and either image or image-family is provided, the current default project is used. |


**Examples:**
```bash
To create instances called 'example-instance-1', 'example-instance-2', and
'example-instance-3' in the 'us-central1-a' zone, run:

    $ gcloud compute instances bulk create \
        --predefined-names=example-instance-1,example-instance-2,\
    example-instance-3 --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/bulk/create)

---

## `gcloud compute instances network-interfaces` — read and manipulate Compute Engine instance network interfaces
### `gcloud compute instances network-interfaces add`

Add a Dynamic Network Interface to a Compute Engine instance

gcloud compute instances network-interfaces add adds a Dynamic Network
Interface to a Compute Engine instance.

**Synopsis:**
```
gcloud compute instances network-interfaces add INSTANCE_NAME
    [--aliases=ALIASES] [--external-ipv6-address=EXTERNAL_IPV6_ADDRESS]
    [--external-ipv6-prefix-length=EXTERNAL_IPV6_PREFIX_LENGTH]
    [--internal-ipv6-address=INTERNAL_IPV6_ADDRESS]
    [--internal-ipv6-prefix-length=INTERNAL_IPV6_PREFIX_LENGTH]
    [--ipv6-network-tier=IPV6_NETWORK_TIER] [--network=NETWORK]
    [--network-attachment=NETWORK_ATTACHMENT] [--network-tier=NETWORK_TIER]
    [--parent-nic-name=PARENT_NIC_NAME]
    [--private-network-ip=PRIVATE_NETWORK_IP] [--stack-type=STACK_TYPE]
    [--subnetwork=SUBNETWORK] [--vlan=VLAN] [--zone=ZONE]
    [--address=ADDRESS | --no-address] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aliases` | ALIASES |  | The IP alias ranges to allocate for this interface. If there are multiple IP alias ranges, they are separated by semicolons. For example: --aliases="10.128.1.0/24;range1:/32" Each IP alias range consists of a range name and an IP range separated by a colon, or just the IP range. The range name is the name of the range within the network interface's subnet from which to allocate an IP alias range. If unspecified, it defaults to the primary IP range of the subnet. The IP range can be a CIDR range (e.g. 192.168.100.0/24), a single IP address (e.g. 192.168.100.1), or a netmask in CIDR format (e.g. /24). If the IP range is specified by CIDR range or single IP address, it must belong to the CIDR range specified by the range name on the subnet. If the IP range is specified by netmask, the IP allocator will pick an available range with the specified netmask and allocate it to this network interface. |
| `--external-ipv6-address` | EXTERNAL_IPV6_ADDRESS |  | Assigns the given external IPv6 address to an instance. The address must be the first IP in the range. This option is not applicable to instances with stack-type=IPV4_ONLY. |
| `--external-ipv6-prefix-length` | EXTERNAL_IPV6_PREFIX_LENGTH |  | The prefix length of the external IPv6 address range. This flag should be used together with --external-ipv6-address. Currently only /96 is supported and the default value is 96. |
| `--internal-ipv6-address` | INTERNAL_IPV6_ADDRESS |  | Assigns the given internal IPv6 address or range to an instance. The address must be the first IP address in the range or a /96 IP address range. This option can only be used on a dual stack instance network interface. |
| `--internal-ipv6-prefix-length` | INTERNAL_IPV6_PREFIX_LENGTH |  | Optional field that indicates the prefix length of the internal IPv6 address range, should be used together with --internal-ipv6-address=fd20::. Only /96 IP address range is supported and the default value is 96. If not set, then either the prefix length from --internal-ipv6-address=fd20::/96 will be used or the default value of 96 will be assigned. |
| `--ipv6-network-tier` | IPV6_NETWORK_TIER |  | Specifies the IPv6 network tier that will be used to configure the instance network interface IPv6 access config. IPV6_NETWORK_TIER must be (only one value is supported): PREMIUM High quality, Google-grade network tier. |
| `--network` | NETWORK |  | Specifies the network this network interface belongs to. |
| `--network-attachment` | NETWORK_ATTACHMENT |  | The network attachment URL this network interface should connect to. |
| `--network-tier` | one of: PREMIUM, STANDARD, FIXED_STANDARD |  | Specifies the network tier that will be used to configure the instance network interface. NETWORK_TIER must be one of: PREMIUM, STANDARD, FIXED_STANDARD. The default value is PREMIUM. NETWORK_TIER must be one of: FIXED_STANDARD Public internet quality with fixed bandwidth. PREMIUM High quality, Google-grade network tier. STANDARD Public internet quality. |
| `--parent-nic-name` | PARENT_NIC_NAME |  | Name of the parent network interface of a dynamic network interface. |
| `--private-network-ip` | PRIVATE_NETWORK_IP |  | Specifies the RFC1918 IP to assign to the network interface. The IP should be in the subnet IP range. |
| `--stack-type` | one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses |  | The stack type for the network interface. Determines if IPv6 is enabled on the network interface. STACK_TYPE must be one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses. IPV4_ONLY The network interface will be assigned IPv4 addresses. IPV6_ONLY The network interface will be assigned IPv6 addresses. |
| `--subnetwork` | SUBNETWORK |  | Specifies the subnetwork this network interface belongs to. |
| `--vlan` | VLAN |  | VLAN tag of a dynamic network interface, must be an integer in the range from 2 to 255 inclusively. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add a Dynamic Network Interface to a Compute Engine instance, run:        $ gcloud compute instances network-interfaces add instance-name \
        --parent-nic-name=nic1 --vlan=2 --network=network-1 \
        --subnetwork=subnetwork-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/network-interfaces/add)

---
### `gcloud compute instances network-interfaces delete`

Delete a Dynamic Network Interface from a Compute Engine instance

gcloud compute instances network-interfaces delete deletes a Dynamic
Network Interface from a Compute Engine instance.

**Synopsis:**
```
gcloud compute instances network-interfaces delete INSTANCE_NAME
    --network-interface=NETWORK_INTERFACE [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network-interface` | NETWORK_INTERFACE |  | The name of the network interface to delete, e.g. nic1.2 |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To delete a Dynamic Network Interface from a Compute Engine instance, run:        $ gcloud compute instances network-interfaces delete instance-name \
        --network-interface=nic1.2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/network-interfaces/delete)

---
### `gcloud compute instances network-interfaces get-effective-firewalls`

Get the effective firewalls for a Compute Engine virtual machine network interface

gcloud compute instances network-interfaces get-effective-firewalls is used
to get the effective firewalls applied to the network interfaces of a
Compute Engine virtual machine.

**Synopsis:**
```
gcloud compute instances network-interfaces get-effective-firewalls
    INSTANCE_NAME [NAME ...]
    [--network-interface=NETWORK_INTERFACE; default="nic0"]
    [--regexp=REGEXP, -r REGEXP] [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances

[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network-interface` | NETWORK_INTERFACE | nic0 | The name of the network interface to get the effective firewalls for. |
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To get the effective firewalls of instance with name example-instance, run:

    $ gcloud compute instances network-interfaces \
        get-effective-firewalls example-instance

To show all fields of the firewall rules, please show in JSON format with
option --format=json

To see more firewall rule fields in table format, run the following for
"example-instance":

    $ gcloud compute instances network-interfaces \
        get-effective-firewalls example-instance --format="table(
      type,
      firewall_policy_name,
      rule_type,
      priority,
      action,
      direction,
      ip_ranges.list():label=IP_RANGES,
      target_svc_acct,
      enableLogging,
      description,
      name,
      disabled,
      target_tags,
      src_svc_acct,
      src_tags,
      ruleTupleCount,
      targetResources:label=TARGET_RESOURCES)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/network-interfaces/get-effective-firewalls)

---
### `gcloud compute instances network-interfaces update`

Update a Compute Engine virtual machine network interface

gcloud compute instances network-interfaces update updates network
interfaces of a Compute Engine virtual machine. For example:

    $ gcloud compute instances network-interfaces update \
        example-instance --zone us-central1-a --aliases r1:172.16.0.1/32

sets 172.16.0.1/32 from range r1 of the default interface's subnetwork as
the interface's alias IP.

**Synopsis:**
```
gcloud compute instances network-interfaces update INSTANCE_NAME
    [--aliases=ALIASES] [--external-ipv6-address=EXTERNAL_IPV6_ADDRESS]
    [--external-ipv6-prefix-length=EXTERNAL_IPV6_PREFIX_LENGTH]
    [--igmp-query=IGMP_QUERY]
    [--internal-ipv6-address=INTERNAL_IPV6_ADDRESS]
    [--internal-ipv6-prefix-length=INTERNAL_IPV6_PREFIX_LENGTH]
    [--ipv6-network-tier=IPV6_NETWORK_TIER] [--network=NETWORK]
    [--network-interface=NETWORK_INTERFACE; default="nic0"]
    [--private-network-ip=PRIVATE_NETWORK_IP]
    [--security-policy=SECURITY_POLICY]
    [--security-policy-region=SECURITY_POLICY_REGION]
    [--stack-type=STACK_TYPE] [--subnetwork=SUBNETWORK] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aliases` | ALIASES |  | The IP alias ranges to allocate for this interface. If there are multiple IP alias ranges, they are separated by semicolons. Can be specified together with --network and/or --subnetwork to choose IP alias ranges in the new subnetwork. If unspecified, then the previous IP alias ranges will be allocated in the new subnetwork. If the previous IP alias ranges are not available in the new subnetwork, then other available IP alias ranges of the same size will be allocated in the new subnetwork. For example: --aliases="10.128.1.0/24;r1:/32" |
| `--external-ipv6-address` | EXTERNAL_IPV6_ADDRESS |  | Assigns the given external IPv6 address to an instance. The address must be the first IP in the range. This option is not applicable to instances with stack-type=IPV4_ONLY. |
| `--external-ipv6-prefix-length` | EXTERNAL_IPV6_PREFIX_LENGTH |  | The prefix length of the external IPv6 address range. This flag should be used together with --external-ipv6-address. Currently only /96 is supported and the default value is 96. |
| `--igmp-query` | one of: IGMP_QUERY_DISABLED IGMP Query on the network interface is disabled |  | Determines if the Compute Engine instance can receive and respond to IGMP query packets on the specified network interface. IGMP_QUERY must be one of: IGMP_QUERY_DISABLED IGMP Query on the network interface is disabled. IGMP_QUERY_V2 IGMP Query V2 on the network interface is enabled. |
| `--internal-ipv6-address` | INTERNAL_IPV6_ADDRESS |  | Assigns the given internal IPv6 address or range to an instance. The address must be the first IP address in the range or a /96 IP address range. This option can only be used on a dual stack instance network interface. |
| `--internal-ipv6-prefix-length` | INTERNAL_IPV6_PREFIX_LENGTH |  | Optional field that indicates the prefix length of the internal IPv6 address range, should be used together with --internal-ipv6-address=fd20::. Only /96 IP address range is supported and the default value is 96. If not set, then either the prefix length from --internal-ipv6-address=fd20::/96 will be used or the default value of 96 will be assigned. |
| `--ipv6-network-tier` | IPV6_NETWORK_TIER |  | Specifies the IPv6 network tier that will be used to configure the instance network interface IPv6 access config. IPV6_NETWORK_TIER must be (only one value is supported): PREMIUM High quality, Google-grade network tier. |
| `--network` | NETWORK |  | Specifies the network this network interface belongs to. |
| `--network-interface` | NETWORK_INTERFACE | nic0 | The name of the network interface to update. |
| `--private-network-ip` | PRIVATE_NETWORK_IP |  | Assign the given IP address to the interface. Can be specified only together with --network and/or --subnetwork to choose the IP address in the new subnetwork. If unspecified, then the previous IP address will be allocated in the new subnetwork. If the previous IP address is not available in the new subnetwork, then another available IP address will be allocated automatically from the new subnetwork CIDR range. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that will be set for this instance network interface. To remove the policy from this instance network interface set the policy to an empty string. |
| `--security-policy-region` | SECURITY_POLICY_REGION |  | Region of the security policy to operate on. Overrides the default compute/region property value for this command invocation. |
| `--stack-type` | one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses |  | The stack type for the network interface. Determines if IPv6 is enabled on the network interface. STACK_TYPE must be one of: IPV4_IPV6 The network interface can have both IPv4 and IPv6 addresses. IPV4_ONLY The network interface will be assigned IPv4 addresses. IPV6_ONLY The network interface will be assigned IPv6 addresses. |
| `--subnetwork` | SUBNETWORK |  | Specifies the subnetwork this network interface belongs to. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/network-interfaces/update)

---

## `gcloud compute instances ops-agents` — manage Google Cloud Observability agents for Compute Engine VM instances

## `gcloud compute instances ops-agents policies` — manage Google Cloud Observability agents policies that install, update, and uninstall agents for Compute Engine VM instances
### `gcloud compute instances ops-agents policies create`

Create a Google Cloud Observability agents policy for the Ops Agent

gcloud compute instances ops-agents policies create creates a policy that
facilitates agent management across Compute Engine instances based on user
specified instance filters. This policy installs, specifies versioning, and
removes Ops Agents.

The command returns the content of the created policy or an error
indicating why the creation fails. The created policy takes effect
asynchronously. It can take 10-15 minutes for the VMs to enforce the newly
created policy.

**Synopsis:**
```
gcloud compute instances ops-agents policies create POLICY_ID --file=FILE
    --zone=ZONE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   ID of the policy.

   This ID must contain only lowercase letters, numbers, and hyphens, end
   with a number or a letter, be between 1-63 characters, and be unique
   within the project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | YAML file with agents policy to create. For information about the agents policy format, see https://cloud.google.com/stackdriver/docs/solutions/agents/ops-agent/agent-policies#config-files. |
| `--zone` | ZONE |  | Zone in which to create the agents policy. |


**Examples:**
```bash
To create a Google Cloud Observability agents policy, run:        $ gcloud compute instances ops-agents policies create agent-policy \
        --project=PROJECT --zone=ZONE --file=config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/ops-agents/policies/create)

---
### `gcloud compute instances ops-agents policies delete`

Delete a Google Cloud Observability agents policy for the Ops Agent

gcloud compute instances ops-agents policies delete deletes a policy that
facilitates agent management across Compute Engine instances based on user
specified instance filters.

The command returns a response indicating whether the deletion succeeded.
After a policy is deleted, it takes 10-15 minutes to be wiped from the
applicable instances. Deleting a policy does not delete any existing agents
managed by that policy, but the agents become unmanaged by any policies. To
remove the agents from the instances, first update the policy to set the
agent packageState to removed, wait for the policy to take effect, then
delete the policy.

The command returns the content of the deleted policy. For instance:

    agentsRule:
      packageState: installed
      version: latest
    instanceFilter:
      inclusionLabels:
      - labels:
          env: prod

If no policies are found, or the policy is not an agents policy, then the
command returns a NOT_FOUND error.

**Synopsis:**
```
gcloud compute instances ops-agents policies delete POLICY_ID --zone=ZONE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   ID of the policy.

   This ID must contain only lowercase letters, numbers, and hyphens, end
   with a number or a letter, be between 1-63 characters, and be unique
   within the project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the agents policy you want to delete. |


**Examples:**
```bash
To delete an agents policy named ops-agents-test-policy in the current
project, run:

    $ gcloud compute instances ops-agents policies delete \
        ops-agents-test-policy --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/ops-agents/policies/delete)

---
### `gcloud compute instances ops-agents policies describe`

Describe a Google Cloud Observability agents policy for the Ops Agent

gcloud compute instances ops-agents policies describe describes a policy
that facilitates agent management across Compute Engine instances based on
user specified instance filters. This policy installs, specifies
versioning, and removes Ops Agents.

The command returns the content of one policy. For instance:

    agentsRule:
      packageState: installed
      version: latest
    instanceFilter:
      inclusionLabels:
      - labels:
          env: prod

If no policies are found, then the command returns a NOT_FOUND error.

**Synopsis:**
```
gcloud compute instances ops-agents policies describe POLICY_ID --zone=ZONE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   ID of the policy.

   This ID must contain only lowercase letters, numbers, and hyphens, end
   with a number or a letter, be between 1-63 characters, and be unique
   within the project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the agents policy. |


**Examples:**
```bash
To describe an agents policy named ops-agents-test-policy in the current
project, run:

    $ gcloud compute instances ops-agents policies describe \
        ops-agents-test-policy --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/ops-agents/policies/describe)

---
### `gcloud compute instances ops-agents policies list`

List a Google Cloud Observability agents policy for the Ops Agent

gcloud compute instances ops-agents policies list lists policies that
facilitate agent management across Compute Engine instances based on user
specified instance filters. These policies install, specify versioning, and
remove agents.

The command returns a list of policies, including the POLICY_ID,
ROLLOUT_STATE, and UPDATE_TIME for each policy. If no policies are found,
then the command returns an empty list. If policies were found but they
don't match as agents policies, then those policies won't be shown in the
list.

**Synopsis:**
```
gcloud compute instances ops-agents policies list --zone=ZONE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone for which you want to list agent policies. |


**Examples:**
```bash
To list agents policies in the current project, run:

    $ gcloud compute instances ops-agents policies list --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/ops-agents/policies/list)

---
### `gcloud compute instances ops-agents policies update`

Update a Google Cloud Observability agents policy for the Ops Agent

gcloud compute instances ops-agents policies update modifies a policy that
facilitates agent management across Compute Engine instances based on user
specified instance filters. This policy installs, specifies versioning, and
removes Ops Agents.

The command returns the content of the modified policy or an error
indicating why the modification fails. The modified policy takes effect
asynchronously. It can take 10-15 minutes for the VMs to enforce the newly
modified policy.

**Synopsis:**
```
gcloud compute instances ops-agents policies update POLICY_ID --file=FILE
    --zone=ZONE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   ID of the policy.

   This ID must contain only lowercase letters, numbers, and hyphens, end
   with a number or a letter, be between 1-63 characters, and be unique
   within the project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | YAML file with a subset of agents policy fields you wish to update. For information about the agents policy format, see https://cloud.google.com/stackdriver/docs/solutions/agents/ops-agent/agent-policies#config-files. |
| `--zone` | ZONE |  | Zone where the agents policy is located. |


**Examples:**
```bash
To update a Google Cloud Observability agents policy, run:        $ gcloud compute instances ops-agents policies update agent-policy \
        --project=PROJECT --zone=ZONE --file=config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/ops-agents/policies/update)

---

## `gcloud compute instances os-inventory` — read Compute Engine OS Inventory Data and Related Resources
### `gcloud compute instances os-inventory describe`

Describe a Compute Engine virtual instance's OS inventory data

gcloud compute instances os-inventory describe displays all OS inventory
data associated with a Compute Engine virtual machine instance.

**Synopsis:**
```
gcloud compute instances os-inventory describe INSTANCE_NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to describe. For details on valid instance names,
   refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to describe. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To see OS inventory of an instance named my-instance, run:

    $ gcloud compute instances os-inventory describe my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/os-inventory/describe)

---
### `gcloud compute instances os-inventory list-instances`

List instances with specific OS inventory data values

gcloud compute instances os-inventory list-instances displays all Compute
Engine instances in a project matching an inventory filter. Run $ gcloud
topic filters to see the supported filter syntax.

**Synopsis:**
```
gcloud compute instances os-inventory list-instances
    [--inventory-filter=INVENTORY_FILTER]
    [--kernel-version=KERNEL_VERSION --os-shortname=OS_SHORTNAME
      --os-version=OS_VERSION
      --package-name=PACKAGE_NAME --package-version=PACKAGE_VERSION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--inventory-filter` | INVENTORY_FILTER |  | Filter expression for matching against OS inventory criteria |


**Examples:**
```bash
To list all instances with OS inventory data in a project in table form,
run:

    $ gcloud compute instances os-inventory list-instances

To list the URIs of all instances whose OS short name contains rhel, run:

    $ gcloud compute instances os-inventory list-instances \
    --inventory-filter="ShortName:rhel" --uri

To list the URIs of all instances whose OS short name is equal to rhel,
run:

    $ gcloud compute instances os-inventory list-instances \
    --os-shortname="rhel" --uri

To list all instances with package google-cloud-sdk of version 235.0.0-0
installed, run:

    $ gcloud compute instances os-inventory list-instances \
    --package-name="google-cloud-sdk" --package-version="235.0.0-0"

To list all instances with package name matching a regex ^google-cloud
available for update through apt, run:

    $ gcloud compute instances os-inventory list-instances \
    --inventory-filter="PackageUpdates.apt[].Name~^google-cloud*"

To list all instances with package update google-cloud-sdk of version
greater than or equal to 235.0.0-0 available through apt, run:

    $ gcloud compute instances os-inventory list-instances \
    --inventory-filter="PackageUpdates.apt[].['google-cloud-sdk'].Ve\
    rsion>=235.0.0-0"

To list all instances missing the Stackdriver monitoring package
stackdriver-agent, run:

    $ gcloud compute instances os-inventory list-instances \
    --inventory-filter="NOT(InstalledPackages:stackdriver-agent)"

To list all Windows instances with an installed qfe hotfix whose ID equals
KB4462930, run:

    $ gcloud compute instances os-inventory list-instances \
    --inventory-filter="InstalledPackages.qfe[].HotFixID=KB4462930"

To list all Windows instances with a wua update whose description contains
the word Security, run:

    $ gcloud compute instances os-inventory list-instances \
    --inventory-filter="InstalledPackages.wua[].Description:Security\
    "
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instances/os-inventory/list-instances)

---
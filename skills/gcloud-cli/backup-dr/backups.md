# gcloud backup-dr backups

manage Backup and DR backups

### `gcloud backup-dr backups delete`

Delete the specified Backup

Delete the specified Backup.

**Synopsis:**
```
gcloud backup-dr backups delete
    (BACKUP : --backup-vault=BACKUP_VAULT
      --data-source=DATA_SOURCE --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the backup to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the Backup or fully qualified identifier for the Backup.

     To set the name attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-vault=BACKUP_VAULT
     The ID of the Backup Vault.

     To set the backup-vault attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-vault on the command line.

  --data-source=DATA_SOURCE
     The ID of the Data Source.

     To set the data-source attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --data-source on the command line.

  --location=LOCATION
     The location of the Backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a backup sample-backup in backup vault sample-vault, data source
sample-ds, project sample-project and location us-central1 , run:

    $ gcloud backup-dr backups delete sample-backup \
        --backup-vault=sample-vault --data-source=sample-ds \
        --project=sample-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/delete)

---
### `gcloud backup-dr backups describe`

Show details of the backup

Show all data associated with the specified backup.

**Synopsis:**
```
gcloud backup-dr backups describe
    (BACKUP : --backup-vault=BACKUP_VAULT
      --data-source=DATA_SOURCE --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the backup to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-vault=BACKUP_VAULT
     The ID of the Backup Vault.

     To set the backup-vault attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-vault on the command line.

  --data-source=DATA_SOURCE
     The ID of the Data Source.

     To set the data-source attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --data-source on the command line.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for backup 'BACKUP', run:

    $ gcloud backup-dr backups describe BACKUP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/describe)

---
### `gcloud backup-dr backups fetch-for-resource-type`

Fetch Backups for a given resource type and location

Fetch Backups for a given resource type and location. List backups for the
specified resource type for a data source.

**Synopsis:**
```
gcloud backup-dr backups fetch-for-resource-type RESOURCE_TYPE
    (--data-source=DATA_SOURCE
      : --backup-vault=BACKUP_VAULT --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_TYPE
   Resource type for which backup plan associations should be fetched.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-source` | DATA_SOURCE |  | _[This must be specified.]_ ID of the Data Source or fully qualified identifier for the Data Source. To set the data-source attribute: + provide the argument --data-source on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--backup-vault` | BACKUP_VAULT |  | _[This must be specified.]_ The ID of the Backup Vault. To set the backup-vault attribute: + provide the argument --data-source on the command line with a fully specified name; + provide the argument --backup-vault on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location of the Data Source. To set the location attribute: + provide the argument --data-source on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list backups for Cloud SQL instance resources for data source
my-data-source with location us-central1 under backup vault, my-vault.

    $ gcloud backup-dr backups fetch-for-resource-type \
        sqladmin.googleapis.com/Instance --data-source=my-data-source \
        --backup-vault=my-vault --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/fetch-for-resource-type)

---
### `gcloud backup-dr backups list`

List Backups

Displays all backups in a project.

**Synopsis:**
```
gcloud backup-dr backups list
    [--backup-vault=BACKUP_VAULT
      --data-source=DATA_SOURCE --location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-vault` | BACKUP_VAULT |  | _[* set the property core/project.]_ The ID of the Backup Vault. To set the backup-vault attribute: + provide the argument --data-source on the command line with a fully specified name; + default is all data sources with a fully specified name; + provide the argument --backup-vault on the command line; + default is all backup vaults . |
| `--data-source` | DATA_SOURCE |  | _[* set the property core/project.]_ ID of the dataSource or fully qualified identifier for the dataSource. To set the data-source attribute: + provide the argument --data-source on the command line; + default is all data sources . |
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location ID of the resource. To set the location attribute: + provide the argument --data-source on the command line with a fully specified name; + default is all data sources with a fully specified name; + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list backups for all data sources, backup vaults and locations, run:

    $ gcloud backup-dr backups list

To list all backups for a data source my-data-source and a backup vault
my-vault in a location my-location, run:

    $ gcloud backup-dr backups list --data-source=my-data-source \
        --backup-vault=my-vault --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/list)

---
### `gcloud backup-dr backups update`

Update the specified Backup

Update the specified Backup.

**Synopsis:**
```
gcloud backup-dr backups update
    (BACKUP : --backup-vault=BACKUP_VAULT
      --data-source=DATA_SOURCE --location=LOCATION)
    (--enforced-retention-end-time=ENFORCED_RETENTION_END_TIME
      --expire-time=EXPIRE_TIME) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Name of the backup to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the Backup or fully qualified identifier for the Backup.

     To set the name attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-vault=BACKUP_VAULT
     The ID of the Backup Vault.

     To set the backup-vault attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-vault on the command line.

  --data-source=DATA_SOURCE
     The ID of the Data Source.

     To set the data-source attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --data-source on the command line.

  --location=LOCATION
     The location of the Backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enforced-retention-end-time` | ENFORCED_RETENTION_END_TIME |  | _[At least one of these must be specified:]_ Backups cannot be deleted until this time or later. This period can be extended, but not shortened. It should be specified in the format of "YYYY-MM-DD". + For backup configured with a backup appliance, there are additional restrictions: 1. Enforced retention cannot be extended past the expiry time. 2. Enforced retention can only be updated for finalized backups. |
| `--expire-time` | EXPIRE_TIME |  | _[At least one of these must be specified:]_ The date when this backup is automatically expired. This date can be extended, but not shortened. It should be specified in the format of "YYYY-MM-DD". |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To update the enforced retention of a backup sample-backup in backup vault
sample-vault, data source sample-ds, project sample-project and location
us-central1, run:

    $ gcloud backup-dr backups update sample-backup \
        --backup-vault=sample-vault --data-source=sample-ds \
        --project=sample-project --location=us-central1 \
        --enforced-retention-end-time="2025-02-14T01:10:20Z"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/update)

---

## `gcloud backup-dr backups restore` — manage restore operations for resources
### `gcloud backup-dr backups restore compute`

Restores a Compute Engine VM Backup

Restores a Compute Engine VM Backup.

**Synopsis:**
```
gcloud backup-dr backups restore compute
    (BACKUP : --backup-vault=BACKUP_VAULT
      --data-source=DATA_SOURCE --location=LOCATION) --name=NAME
    --target-project=TARGET_PROJECT --target-zone=TARGET_ZONE
    [--accelerator=[count=COUNT],[type=TYPE]] [--async]
    [--[no-]can-ip-forward] [--confidential-compute]
    [--create-disk=[PROPERTY=VALUE,...]] [--[no-]deletion-protection]
    [--description=DESCRIPTION] [--[no-]enable-display-device]
    [--[no-]enable-uefi-networking] [--hostname=HOSTNAME]
    [--instance-kms-key=INSTANCE_KMS_KEY]
    [--instance-termination-action=INSTANCE_TERMINATION_ACTION]
    [--key-revocation-action-type=POLICY] [--labels=[KEY=VALUE,...]]
    [--local-ssd-recovery-timeout=LOCAL_SSD_RECOVERY_TIMEOUT]
    [--machine-type=MACHINE_TYPE] [--maintenance-policy=MAINTENANCE_POLICY]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]] [--min-cpu-platform=PLATFORM]
    [--min-node-cpu=MIN_NODE_CPU]
    [--network-interface=[PROPERTY=VALUE,...]]
    [--network-performance-configs=[PROPERTY=VALUE,...]]
    [--[no-]preemptible]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--provisioning-model=PROVISIONING_MODEL]
    [--resource-manager-tags=[KEY=VALUE,...]]
    [--resource-policies=RESOURCE_POLICY,[...]] [--[no-]restart-on-failure]
    [--service-account=SERVICE_ACCOUNT] [--tags=TAG,[TAG,...]]
    [--threads-per-core=THREADS_PER_CORE]
    [--visible-core-count=VISIBLE_CORE_COUNT]
    [--reservation=RESERVATION --reservation-affinity=RESERVATION_AFFINITY]
    [--scopes=[SCOPE,...] | --no-scopes] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The backup of a resource to be restored. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the Backup or fully qualified identifier for the Backup.

     To set the name attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-vault=BACKUP_VAULT
     The ID of the Backup Vault.

     To set the backup-vault attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-vault on the command line.

  --data-source=DATA_SOURCE
     The ID of the Data Source.

     To set the data-source attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --data-source on the command line.

  --location=LOCATION
     The location of the Backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | Name of the restored Compute Instance. |
| `--target-project` | TARGET_PROJECT |  | Project where the restore should happen. |
| `--target-zone` | TARGET_ZONE |  | Zone where the target instance is restored. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--accelerator` | [count=COUNT],[type=TYPE] |  | Attaches accelerators (e.g. GPUs) to the instances. type The specific type (e.g. nvidia-tesla-k80 for nVidia Tesla K80) of accelerator to attach to the instances. Use 'gcloud compute accelerator-types list' to learn about all available accelerator types. count Number of accelerators to attach to each instance. The default value is 1. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--[no-]can-ip-forward` |  |  | If provided, allows the restored instances to send and receive packets with non-matching destination or source IP addresses. Use --can-ip-forward to enable and --no-can-ip-forward to disable. |
| `--confidential-compute` |  |  | The restored instance boots with Confidential Computing enabled. Confidential Computing is based on Secure Encrypted Virtualization (SEV), an AMD virtualization feature for running confidential instances. |
| `--create-disk` | [PROPERTY=VALUE,...] |  | Creates and attaches persistent disks to the instances. name: Specifies the name of the disk. replica-zones: Required for each regional disk associated with the instance. Specify the URLs of the zones where the disk should be replicated to. You must provide exactly two replica zones, and one zone must be the same as the instance zone. device-name: Device name of the disk from the source instance. |
| `--[no-]deletion-protection` |  |  | Enables deletion protection for the restored instance. Use --deletion-protection to enable and --no-deletion-protection to disable. |
| `--description` | DESCRIPTION |  | Specifies a textual description of the restored instance. |
| `--[no-]enable-display-device` |  |  | Enable a display device on the restored VM instances. Disabled by default. Use --enable-display-device to enable and --no-enable-display-device to disable. |
| `--[no-]enable-uefi-networking` |  |  | If set to true, enables UEFI networking for the instance creation. Use --enable-uefi-networking to enable and --no-enable-uefi-networking to disable. |
| `--hostname` | HOSTNAME |  | Specify the hostname of the restore instance to be created. The specified hostname must be RFC1035 compliant. If hostname is not specified, the default hostname is [INSTANCE_NAME].c.[TARGET_PROJECT_ID].internal when using the global DNS, and [INSTANCE_NAME].[ZONE].c.[TARGET_PROJECT_ID].internal when using zonal DNS. |
| `--instance-kms-key` | INSTANCE_KMS_KEY |  | The Cloud KMS (Key Management Service) cryptokey that will be used to protect the restored instance. Provide the full resource name of the cryptokey in the format: projects/<project>/locations/<location>/keyRings/<key-ring>/cryptoKeys/<key> |
| `--instance-termination-action` | one of: DELETE Permanently delete the VM |  | Specifies the termination action that will be taken upon VM preemption (--provisioning-model=SPOT) or automatic instance termination (--max-run-duration or --termination-time). INSTANCE_TERMINATION_ACTION must be one of: DELETE Permanently delete the VM. STOP Default only for Spot VMs. Stop the VM without preserving memory. The VM can be restarted later. |
| `--key-revocation-action-type` | one of: * none No operation is performed |  | Specifies the behavior of the instance when the KMS key of one of its attached disks is revoked. The default is none. POLICY must be one of: * none No operation is performed. * stop The instance is stopped when the KMS key of one of its attached disks is revoked. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (), lowercase characters, and numbers. |
| `--local-ssd-recovery-timeout` | LOCAL_SSD_RECOVERY_TIMEOUT |  | Specifies the maximum amount of time a Local SSD VM should wait while recovery of the Local SSD state is attempted. Its value should be in between 0 and 168 hours with hour granularity and the default value being 1 hour. |
| `--machine-type` | MACHINE_TYPE |  | Specifies the machine type used for the restored instance. To get a list of available machine types, run 'gcloud compute machine-types list'. If unspecified, the default type will be based on the source instance. This can either be the fully qualified path or the name. For example: * --machine-type=projects/my-project/zones/us-central1-a/machineTypes/n1-standard-1 * --machine-type=n1-standard-1 |
| `--maintenance-policy` | one of: MIGRATE The instances should be migrated to a new host |  | Specifies the behavior of the VMs when their host machines undergo maintenance. The default is MIGRATE. For more information, see https://cloud.google.com/compute/docs/instances/host-maintenance-options. MAINTENANCE_POLICY must be one of: MIGRATE The instances should be migrated to a new host. This will temporarily impact the performance of instances during a migration event. TERMINATE The instances should be terminated. |
| `--metadata` | KEY=VALUE,[KEY=VALUE,...] |  | Metadata to be made available to the guest operating system running on the instances. Each metadata entry is a key/value pair separated by an equals sign. Each metadata key must be unique and have a max of 128 bytes in length. Each value must have a max of 256 KB in length. Multiple arguments can be passed to this flag, e.g., --metadata key-1=value-1,key-2=value-2,key-3=value-3. The combined total size for all metadata entries is 512 KB. In images that have Compute Engine tools installed on them, such as the official images (https://cloud.google.com/compute/docs/images), the following metadata keys have special meanings: startup-script Specifies a script that will be executed by the instances once they start running. startup-script-url Same as startup-script except that the script contents are pulled from a publicly-accessible location on the web. For startup scripts on Windows instances, the following metadata keys have special meanings: windows-startup-script-url, windows-startup-script-cmd, windows-startup-script-bat, windows-startup-script-ps1, sysprep-specialize-script-url, sysprep-specialize-script-cmd, sysprep-specialize-script-bat, and sysprep-specialize-script-ps1. For more information, see Running startup scripts (https://cloud.google.com/compute/docs/startupscript). |
| `--min-cpu-platform` | PLATFORM |  | When specified, the VM will be scheduled on host with specified CPU architecture or a newer one. To list available CPU platforms in given zone, run: $ gcloud compute zones describe ZONE \ --format="value(availableCpuPlatforms)" Default setting is "AUTOMATIC". CPU platform selection is available only in selected zones. You can find more information on-line: https://cloud.google.com/compute/docs/instances/specify-min-cpu-platform |
| `--min-node-cpu` | MIN_NODE_CPU |  | Minimum number of virtual CPUs this instance will consume when running on a sole-tenant node. |
| `--network-interface` | [PROPERTY=VALUE,...] |  | Adds a network interface to the instance. This flag can be repeated to specify multiple network interfaces. The following keys are allowed: network, subnet, private-network-ip, internal-ipv6-address, internal-ipv6-prefix-length, address, external-ipv6-address, external-ipv6-prefix-length, network-tier, aliases, stack-type, queue-count, nic-type, network-attachment |
| `--network-performance-configs` | [PROPERTY=VALUE,...] |  | Configures network performance settings for the restored instance. If this flag is not specified, the restored instance will be created with its source instance's network performance configuration. total-egress-bandwidth-tier Total egress bandwidth is the available outbound bandwidth from a VM, regardless of whether the traffic is going to internal IP or external IP destinations. The following tier values are allowed: [DEFAULT, TIER_1] |
| `--[no-]preemptible` |  |  | If provided, instances will be preemptible and time-limited. Instances might be preempted to free up resources for standard VM instances, and will only be able to run for a limited amount of time. Preemptible instances can not be restarted and will not migrate. Use --preemptible to enable and --no-preemptible to disable. |
| `--private-ipv6-google-access-type` | PRIVATE_IPV6_GOOGLE_ACCESS_TYPE |  | The private IPv6 Google access type for the restored VM. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: inherit-subnetwork, enable-bidirectional-access, enable-outbound-vm-access |
| `--provisioning-model` | one of: SPOT Spot VMs are spare capacity; Spot VMs are discounted to have much lower prices than standard VMs but have no guaranteed runtime |  | Specifies provisioning model, which determines price, obtainability, and runtime for the restored VM instance. PROVISIONING_MODEL must be one of: SPOT Spot VMs are spare capacity; Spot VMs are discounted to have much lower prices than standard VMs but have no guaranteed runtime. Spot VMs are the new version of preemptible VM instances, except Spot VMs do not have a 24-hour maximum runtime. STANDARD Default. Standard provisioning model for VM instances, which has user-controlled runtime but no Spot discounts. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | Specifies a list of resource manager tags to apply to the instance. |
| `--resource-policies` | RESOURCE_POLICY,[...] |  | A list of resource policy names to be added to the instance. The policies must exist in the same region as the instance. |
| `--[no-]restart-on-failure` |  |  | The instances will be restarted if they are terminated by Compute Engine. This does not affect terminations performed by the user. Use --restart-on-failure to enable and --no-restart-on-failure to disable. |
| `--service-account` | SERVICE_ACCOUNT |  | A service account is an identity attached to the instance. Its access tokens can be accessed through the instance metadata server and are used to authenticate applications on the instance. The account can be set using an email address corresponding to the required service account. If not provided, the instance will use the project's default service account. |
| `--tags` | TAG,[TAG,...] |  | Specifies a list of tags to apply to the instance. These tags allow network firewall rules and routes to be applied to specified VM instances. See gcloud compute firewall-rules create(1) for more details. |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of visible threads per physical core. To disable simultaneous multithreading (SMT) set this to 1. Valid values are: 1 or 2. For more information about configuring SMT, see: https://cloud.google.com/compute/docs/instances/configuring-simultaneous-multithreading. |
| `--visible-core-count` | VISIBLE_CORE_COUNT |  | The number of physical cores to expose to the instance's guest operating system. The number of virtual CPUs visible to the instance's guest operating system is this number of cores multiplied by the instance's count of visible threads per physical core. |


**Examples:**
```bash
To restore a backup sample-backup in project sample-project and location
us-central1, with sample-data-store and sample-backup-vault, and additional
target properties, run:

    $ gcloud backup-dr backups restore compute sample-backup \
        --project=sample-project --location=us-central1 \
        --backup-vault=sample-backup-vault \
        --data-source=sample-data-source --<target-properties>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/restore/compute)

---
### `gcloud backup-dr backups restore disk`

Restores a Compute Disk Backup

Restores a Compute Disk Backup.

**Synopsis:**
```
gcloud backup-dr backups restore disk
    (BACKUP : --backup-vault=BACKUP_VAULT
      --data-source=DATA_SOURCE --location=LOCATION) --name=NAME
    --target-project=TARGET_PROJECT [--access-mode=ACCESS_MODE]
    [--architecture=ARCHITECTURE] [--async] [--clear-encryption-key]
    [--confidential-compute] [--description=DESCRIPTION]
    [--guest-os-features=[GUEST_OS_FEATURES,...]] [--kms-key=KMS_KEY]
    [--labels=[KEY=VALUE,...]] [--licenses=LICENSE,[LICENSE,...]]
    [--provisioned-iops=PROVISIONED_IOPS]
    [--provisioned-throughput=PROVISIONED_THROUGHPUT]
    [--replica-zones=ZONE,ZONE] [--resource-policies=RESOURCE_POLICY,[...]]
    [--size=SIZE] [--storage-pool=STORAGE_POOL]
    [--target-region=TARGET_REGION] [--target-zone=TARGET_ZONE]
    [--type=TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The backup of a resource to be restored. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the Backup or fully qualified identifier for the Backup.

     To set the name attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-vault=BACKUP_VAULT
     The ID of the Backup Vault.

     To set the backup-vault attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-vault on the command line.

  --data-source=DATA_SOURCE
     The ID of the Data Source.

     To set the data-source attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --data-source on the command line.

  --location=LOCATION
     The location of the Backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | Name of the restored Disk. |
| `--target-project` | TARGET_PROJECT |  | Project where the restore should happen. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-mode` | one of: READ_ONLY_MANY, READ_WRITE_MANY, READ_WRITE_SINGLE |  | Specifies how VMs attached to the disk can access the data on the disk. To grant read-only access to multiple VMs attached to the disk, set access-mode to READ_ONLY_MANY. To grant read-write access to only one VM attached to the disk, use READ_WRITE_SINGLE. READ_WRITE_SINGLE is used if omitted. ACCESS_MODE must be one of: READ_ONLY_MANY, READ_WRITE_MANY, READ_WRITE_SINGLE. ACCESS_MODE must be one of: READ_ONLY_MANY The AccessMode means the disk can be attached to multiple instances in RW mode. READ_WRITE_MANY The AccessMode means the disk can be attached to multiple instances in RO mode. READ_WRITE_SINGLE The default AccessMode, means the disk can be attached to single instance in RW mode. |
| `--architecture` | one of: ARM64, X86_64 |  | Specifies the architecture or processor type that this disk can support. For available processor types on Compute Engine, see https://cloud.google.com/compute/docs/cpu-platforms. ARCHITECTURE must be one of: ARM64, X86_64. ARCHITECTURE must be one of: ARM64 The disk can only be used with ARM64 machines. X86_64 The disk can only be used with x86_64 machines. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--clear-encryption-key` |  |  | The restored disk reverts to GMEK (CMEK is disabled). |
| `--confidential-compute` |  |  | Creates the disk with confidential compute mode enabled. Encryption with a Cloud KMS key is required to enable this option. |
| `--description` | DESCRIPTION |  | Specifies a textual description of the restored disk. |
| `--guest-os-features` | one of: VIRTIO_SCSI_MULTIQUEUE, WINDOWS, MULTI_IP_SUBNET, UEFI_COMPATIBLE, SEV_CAPABLE, SEV_LIVE_MIGRATABLE, SEV_LIVE_MIGRATABLE_V2, SEV_SNP_CAPABLE, GVNIC, IDPF, TDX_CAPABLE, SUSPEND_RESUME_COMPATIBLE |  | Enables one or more features for VM instances that use the image for their boot disks. See the descriptions of supported features at: https://cloud.google.com/compute/docs/images/create-delete-deprecate-private-images#guest-os-features. GUEST_OS_FEATURE must be one of: VIRTIO_SCSI_MULTIQUEUE, WINDOWS, MULTI_IP_SUBNET, UEFI_COMPATIBLE, SEV_CAPABLE, SEV_LIVE_MIGRATABLE, SEV_LIVE_MIGRATABLE_V2, SEV_SNP_CAPABLE, GVNIC, IDPF, TDX_CAPABLE, SUSPEND_RESUME_COMPATIBLE. |
| `--kms-key` | KMS_KEY |  | The Cloud KMS (Key Management Service) cryptokey that will be used to protect the disk Provide the full resource name of the cryptokey in the format: projects/<project>/locations/<location>/keyRings/<key-ring>/cryptoKeys/<key> |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (), lowercase characters, and numbers. |
| `--licenses` | LICENSE,[LICENSE,...] |  | A list of URIs to license resources. The provided licenses will be added onto the created disks to indicate the licensing and billing policies. |
| `--provisioned-iops` | PROVISIONED_IOPS |  | Provisioned IOPS of disk to create. Only for use with disks of type pd-extreme and hyperdisk-extreme. |
| `--provisioned-throughput` | PROVISIONED_THROUGHPUT |  | Provisioned throughput of disk to create. The throughput unit is MB per sec. Only for use with disks of type hyperdisk-throughput. |
| `--replica-zones` | ZONE,ZONE |  | A comma-separated list of exactly 2 URLs of the zones where the disk should be replicated to. Required when restoring to a regional disk. The zones must be in the same region as specified in the --target-region flag. See available zones with gcloud compute zones list. |
| `--resource-policies` | RESOURCE_POLICY,[...] |  | A list of resource policy names to be added to the disk. The policies must exist in the same region as the disk. |
| `--size` | SIZE |  | Size of the disk in GB. Disk size must be a multiple of 1 GB. If disk size is not specified, the default size of 500GB for pd-standard disks, 100GB for pd-balanced disks, 100GB for pd-ssd disks, and 1000GB for pd-extreme disks will be used. For details about disk size limits, refer to: https://cloud.google.com/compute/docs/disks |
| `--storage-pool` | STORAGE_POOL |  | Specifies the URI of the storage pool in which the disk is created. |
| `--target-region` | TARGET_REGION |  | Region where the target disk is restored. This flag is mutually exclusive with --target-zone. |
| `--target-zone` | TARGET_ZONE |  | Zone where the target disk is restored. This flag is mutually exclusive with --target-region. |
| `--type` | TYPE |  | URL of the disk type describing which disk type to use to restore the disk. For example: projects/project/zones/zone/diskTypes/pd-ssd. To get a list of available disk types, run gcloud compute disk-types list. The default disk type is pd-standard. |


**Examples:**
```bash
To restore a backup sample-backup in project sample-project and location
us-central1, with sample-data-store and sample-backup-vault, and additional
target properties, run:

    $ gcloud backup-dr backups restore disk sample-backup \
        --project=sample-project --location=us-central1 \
        --backup-vault=sample-backup-vault \
        --data-source=sample-data-source --<target-properties>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backups/restore/disk)

---
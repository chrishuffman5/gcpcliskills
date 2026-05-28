# gcloud filestore instances

create and manage Filestore instances

### `gcloud filestore instances create`

Create a Filestore instance

Create a Filestore instance.

**Synopsis:**
```
gcloud filestore instances create (INSTANCE : --zone=ZONE)
    --file-share=[capacity=CAPACITY],[name=NAME],
      [nfs-export-options=NFS-EXPORT-OPTIONS],[source-backup=SOURCE-BACKUP],
      [source-backup-region=SOURCE-BACKUP-REGION],
      [source-backupdr-backup=SOURCE-BACKUPDR-BACKUP]
    --network=[address-mode=ADDRESS-MODE],[connect-mode=CONNECT-MODE],
      [name=NAME],[psc-endpoint-project=PSC-ENDPOINT-PROJECT],
      [reserved-ip-range=RESERVED-IP-RANGE] [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--location=LOCATION]
    [--performance=[max-iops=MAX-IOPS],[max-iops-per-tb=MAX-IOPS-PER-TB]]
    [--protocol=PROTOCOL; default="NFS_V3"] [--region=REGION]
    [--source-instance=SOURCE_INSTANCE] [--tags=[KEY=VALUE,...]]
    [--tier=TIER; default="BASIC_HDD"]
    [--deletion-protection
      : --deletion-protection-reason=DELETION_PROTECTION_REASON]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     The zone of the instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument region on the command line;
     + provide the argument location on the command line;
     + set the property filestore/zone;
     + set the property filestore/region;
     + set the property filestore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-share` | [capacity=CAPACITY],[name=NAME],[nfs-export-options=NFS-EXPORT-OPTIONS],[source-backup=SOURCE-BACKUP],[source-backup-region=SOURCE-BACKUP-REGION],[source-backupdr-backup=SOURCE-BACKUPDR-BACKUP] |  | File share configuration for an instance. Specifying both name and capacity is required. capacity The desired capacity of the volume in GB or TB units. If no capacity unit is specified, GB is assumed. Acceptable instance capacities for each tier are as follows: + BASIC_HDD: 1TB-63.9TB in 1GB increments or its multiples. + BASIC_SSD: 2.5TB-63.9TB in 1GB increments or its multiples. + HIGH_SCALE_SSD: 10TB-100TB in 2.5TB increments or its multiples. + ZONAL: 1TB-100TB: - 1TB-9.75TB in 256GB increments or its multiples. - 10TB-100TB in 2.5TB increments or its multiples. + ENTERPRISE: 1TB-10TB in 256GB increments or its multiples. + REGIONAL: 1TB-100TB: - 1TB-9.75TB in 256GB increments or its multiples. - 10TB-100TB in 2.5TB increments or its multiples. name The desired logical name of the volume. nfs-export-options The NfsExportOptions for the Cloud Filestore instance file share. Configuring NfsExportOptions is optional and can only be set using flags-file. Use the --flags-file flag to specify the path to a JSON or YAML configuration file that contains the required NfsExportOptions flags. ip-ranges A list of IPv4 addresses or CIDR ranges that are allowed to mount the file share. IPv4 addresses format: {octet 1}.{octet 2}.{octet 3}.{octet 4}. CIDR range format: {octet 1}.{octet 2}.{octet 3}.{octet 4}/{mask size}. Overlapping IP ranges are allowed for all tiers other than BASIC_HDD and BASIC_SSD. The limit of IP ranges/addresses for each FileShareConfig among all NfsExportOptions is 64 per instance. access-mode The type of access allowed for the specified IP-addresses or CIDR ranges. READ_ONLY: Allows only read requests on the exported file share. READ_WRITE: Allows both read and write requests on the exported file share. The default setting is READ_WRITE. squash-mode Enables or disables root squash for the specified IP addresses or CIDR ranges. NO_ROOT_SQUASH: Disables root squash to allow root access on the exported file share. ROOT_SQUASH. Enables root squash to remove root access on the exported file share. The default setting is NO_ROOT_SQUASH. anon_uid An integer that represents the user ID of anonymous users. Anon_uid may only be set when squash_mode is set to ROOT_SQUASH. If NO_ROOT_SQUASH is specified, an error will be returned. The default value is 65534. anon_gid An integer that represents the group ID of anonymous groups. Anon_gid may only be set when squash_mode is set to ROOT_SQUASH. If NO_ROOT_SQUASH is specified, an error will be returned. The default value is 65534. source-backup The name of the backup to restore from. source-backup-region The region of the source backup. |
| `--network` | one of: DIRECT_PEERING, PRIVATE_SERVICE_ACCESS or PRIVATE_SERVICE_CONNECT |  | Network configuration for a Cloud Filestore instance. Specifying reserved-ip-range, address-mode and connect-mode is optional. name The name of the Google Compute Engine VPC network to which the instance is connected. reserved-ip-range The reserved-ip-range can have one of the following two types of values: a CIDR range value when using DIRECT_PEERING connect mode or an allocated IP address range (https://cloud.google.com/compute/docs/ip-addresses/reserve-static-internal-ip-address) when using PRIVATE_SERVICE_ACCESS connect mode. When the name of an allocated IP address range is specified, it must be one of the ranges associated with the private service access connection. When specified as a direct CIDR value, it must be a /29 CIDR block for Basic tier or a /24 CIDR block for High Scale, Zonal, Enterprise or Regional tier in one of the internal IP address ranges (https://www.arin.net/knowledge/address_filters.html) that identifies the range of IP addresses reserved for this instance. For example, 10.0.0.0/29 or 192.168.0.0/24. The range you specify can't overlap with either existing subnets or assigned IP address ranges for other Cloud Filestore instances in the selected VPC network. connect-mode Network connection mode used by instances. CONNECT_MODE must be one of: DIRECT_PEERING, PRIVATE_SERVICE_ACCESS or PRIVATE_SERVICE_CONNECT. address-mode Internet protocol version for which the instance has IP address assigned. psc-endpoint-project Consumer service project in which the psc endpoint would be set up. This is optional, and only relevant in case the network is a shared VPC. If this is not specified, the psc endpoint would be setup in the VPC host project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud Filestore instance. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |
| `--performance` | [max-iops=MAX-IOPS],[max-iops-per-tb=MAX-IOPS-PER-TB] |  | Performance configuration for the instance. This flag is used to configure the read IOPS provisioned for the instance. The instance's write IOPS and read/write throughputs will be derived from the configured read IOPS. For more information about the derived performance limits and default performance see: https://cloud.google.com/filestore/docs/performance. Must be one of: max-iops The number of IOPS to provision for the instance. MAX-IOPS must be in multiple of 1000 and in the supported IOPS range for the current capacity of the instance. For more details, see: https://cloud.google.com/filestore/docs/performance. max-iops-per-tb Is used for setting the max IOPS of the instance by specifying the IOPS per TB. When this parameter is used, the max IOPS are derived from the instance capacity: The instance max IOPS will be calculated by multiplying the capacity of the instance (TB) by MAX-IOPS-PER-TB, and rounding to the nearest 1000. The max IOPS will be changed dynamically based on the instance capacity. MAX-IOPS-PER-TB must be in the supported range of the instance. For more details, see: https://cloud.google.com/filestore/docs/performance. Examples: Configure an instance with max-iops performance: $ gcloud filestore instances create example-cluster \ --performance=max-iops=17000 Configure an instance with max-iops-per-tb performance: $ gcloud filestore instances create example-cluster \ --performance=max-iops-per-tb=17000 |
| `--protocol` | one of: nfs-v3 NFSv3 protocol | NFS_V3 | The service protocol for the Cloud Filestore instance. PROTOCOL must be one of: nfs-v3 NFSv3 protocol. nfs-v4-1 NFSv4.1 protocol. |
| `--region` | REGION |  | Region of the Cloud Filestore instance. |
| `--source-instance` | SOURCE_INSTANCE |  | The replication source instance of the Cloud Filestore instance. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |
| `--tier` | one of: basic-hdd Performant NFS storage system using HDD | BASIC_HDD | The service tier for the Cloud Filestore instance. For more details, see: https://cloud.google.com/filestore/docs/instance-tiers TIER must be one of: basic-hdd Performant NFS storage system using HDD. basic-ssd Performant NFS storage system using SSD. enterprise Enterprise instance. Use REGIONAL instead whenever possible. high-scale-ssd High Scale SSD instance, an alias for ZONAL. Use ZONAL instead whenever possible. premium Premium Filestore instance, An alias for BASIC_SSD. Use BASIC_SSD instead whenever possible. regional Regional instances offer the features and availability needed for mission-critical workloads. standard Standard Filestore instance, An alias for BASIC_HDD. Use BASIC_HDD instead whenever possible. zonal Zonal instances offer NFS storage system suitable for high performance computing application requirements. It offers fast performance that scales with capacity and allows you to grow and shrink capacity. |


**Examples:**
```bash
To create a Basic HDD instance named my-instance in zone us-central1-c with
a 1TB volume named my_vol on the default network, run:

    $ gcloud filestore instances create my-instance \
      --zone=us-central1-c --tier=BASIC_HDD \
      --file-share=name=my_vol,capacity=1TB --network=name=default

    To create an Enterprise instance named `my-ent-instance` in region `us-central1` with a 2TB volume named `my_vol` on network `my-network`, run:

    $ gcloud filestore instances create my-ent-instance \
      --zone=us-central1 --tier=ENTERPRISE \
      --file-share=name=my_vol,capacity=2TB --network=name=my-network

    To create an instance with specific NFS export options, you can use a JSON configuration file with `--flags-file`. For example, create a file named `config.json` with the following content:
{ "--file-share": {        "capacity": "1024",
    "name": "my_vol",
    "nfs-export-options": [
      {
        "access-mode": "READ_WRITE",
        "ip-ranges": [
          "10.0.0.0/8"
        ],
        "squash-mode": "NO_ROOT_SQUASH"
      },
       {
        "access-mode": "READ_ONLY",
        "ip-ranges": [
          "192.168.0.0/24"
        ],
        "squash-mode": "ROOT_SQUASH",
        "anon_uid": 1003,
        "anon_gid": 1003
      }
    ]
} }

    To create a Basic SSD instance named `my-nfs-instance` using the above configuration file, run:
      $ gcloud filestore instances create my-nfs-instance \
        --zone=us-central1-c --tier=BASIC_SSD --network=name=default \
        --flags-file=config.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/create)

---
### `gcloud filestore instances delete`

Delete a Filestore instance

Delete a Filestore instance.

**Synopsis:**
```
gcloud filestore instances delete (INSTANCE : --zone=ZONE) [--async]
    [--force] [--location=LOCATION] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     The zone of the instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument region on the command line;
     + provide the argument location on the command line;
     + set the property filestore/zone;
     + set the property filestore/region;
     + set the property filestore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | Forces the deletion of an instance and its child resources, such as snapshots. |
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |
| `--region` | REGION |  | Region of the Cloud Filestore instance. |


**Examples:**
```bash
To delete a Filestore instance named NAME in us-central1-c:

    $ gcloud filestore instances delete NAME --zone=us-central1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/delete)

---
### `gcloud filestore instances describe`

Show metadata for a Filestore instance

Show metadata for a Filestore instance.

**Synopsis:**
```
gcloud filestore instances describe (INSTANCE : --zone=ZONE)
    [--location=LOCATION] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     The zone of the instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument region on the command line;
     + provide the argument location on the command line;
     + set the property filestore/zone;
     + set the property filestore/region;
     + set the property filestore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |
| `--region` | REGION |  | Region of the Cloud Filestore instance. |


**Examples:**
```bash
The following command shows the metadata for the Filestore instance named
NAME in us-central1-c.

    $ gcloud filestore instances describe NAME --location=us-central1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/describe)

---
### `gcloud filestore instances list`

List Filestore instances

**Synopsis:**
```
gcloud filestore instances list [--location=LOCATION] [--region=REGION]
    [--zone=ZONE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |
| `--region` | REGION |  | Region of the Cloud Filestore instance. |


**Examples:**
```bash
The following command lists a maximum of five Filestore instances sorted
alphabetically by name in descending order:

    $ gcloud filestore instances list --limit=5 --sort-by=~name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/list)

---
### `gcloud filestore instances pause-replica`

Pause a Filestore replica instance

Pause a Filestore replica instance. This command can be called only on a
standby instance. After calling the command, the NFS file system of the
standby instance becomes writeable. Any data changed on the standby
instance while it is paused will be lost when the replica is resumed or
promoted.

**Synopsis:**
```
gcloud filestore instances pause-replica (INSTANCE : --zone=ZONE) [--async]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Filestore
instance to pause. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
     The zone of the Filestore instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument --location on the command line;
     + set the property filestore/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | Location of the Filestore instance to pause. |


**Examples:**
```bash
To pause a replica instance with the name my-replica-instance located in
us-central1-c, run:

    $ gcloud filestore instances pause-replica my-replica-instance \
        --zone=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/pause-replica)

---
### `gcloud filestore instances promote-replica`

Promote a Filestore standby replication instance

Promote a Filestore standby replication instance to a regular instance.
This command can be called directly on the standby instance or on the
active instance with the standby peer instance parameter. When used on the
standby instance promotes the standby instance to a regular instance even
if the active instance is unavailable. When used on the active instance
detaches the standby instance from the active instance even if the standby
instance is unavailable.

This command can fail for the following reasons:
  o The target instance does not exist.
  o The instance is not a standby replication member.
  o The instance is an active instance and the peer instance parameter is
    missing or invalid.

**Synopsis:**
```
gcloud filestore instances promote-replica (INSTANCE : --zone=ZONE)
    [--async] [--location=LOCATION] [--peer-instance=PEER_INSTANCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Filestore
instance to promote. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
     The zone of the Filestore instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument --location on the command line;
     + set the property filestore/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | Location of the Filestore instance to promote. |
| `--peer-instance` | PEER_INSTANCE |  | The name of the standby peer instance to promote. |


**Examples:**
```bash
To promote a standby instance with the name my-replica-instance located in
us-central1, run:

    $ gcloud filestore instances promote-replica my-replica-instance \
        --zone=us-central1

To promote a standby instance with the name my-replica-instance located in
us-central1, attached to the active peer instance my-active-instance
located in us-west1, run:

    $ gcloud filestore instances promote-replica my-active-instance \
        --zone=us-west1 \
        --peer-instance=projects/my-project/locations/us-central1/\
    instances/my-replica-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/promote-replica)

---
### `gcloud filestore instances restore`

Restore a Filestore instance from a backup

Restore an existing Filestore instance from an existing backup.

**Synopsis:**
```
gcloud filestore instances restore (INSTANCE : --zone=ZONE)
    --file-share=FILE_SHARE --source-backup=SOURCE_BACKUP
    --source-backup-region=SOURCE_BACKUP_REGION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Filestore
instance to restore. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
     The zone of the Filestore instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property filestore/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-share` | FILE_SHARE |  | File share to restore from the backup. |
| `--source-backup` | SOURCE_BACKUP |  | Name of the Filestore backup to restore from. |
| `--source-backup-region` | SOURCE_BACKUP_REGION |  | Region of the Filestore backup to restore from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command restores an instance named 'my-instance' with a
fileshare named 'vol1' in the zone europe-west3-a from a backup named
'my-backup' in the region europe-west3.

    $ gcloud filestore instances restore my-instance \
        --zone=europe-west3-a --file-share=vol1 \
        --source-backup=my-backup --source-backup-region=europe-west3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/restore)

---
### `gcloud filestore instances resume-replica`

Resume a Filestore replica instance

Resume a Filestore replica instance. This command can be called only on a
paused standby instance. Any data written to the standby instance while
being paused will be lost when the replica is resumed. The NFS file system
of the standby instance becomes inaccessible and replication is resumed.

**Synopsis:**
```
gcloud filestore instances resume-replica (INSTANCE : --zone=ZONE)
    [--async] [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Filestore
instance to resume. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
     The zone of the Filestore instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument --location on the command line;
     + set the property filestore/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | Location of the Filestore instance to resume. |


**Examples:**
```bash
To resume a replica instance with the name my-replica-instance located in
us-central1-c , run:

    $ gcloud filestore instances resume-replica my-replica-instance \
        --zone=us-central1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/resume-replica)

---
### `gcloud filestore instances revert`

Revert a Filestore instance

Revert a Filestore instance to the target snapshot.

This command can fail for the following reasons:
  o The target snapshot does not exist.
  o The active account does not have permission to revert the instance.
  o The service tier of the instance does not support the operation.

**Synopsis:**
```
gcloud filestore instances revert (INSTANCE : --location=LOCATION)
    --target-snapshot=TARGET_SNAPSHOT [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Filestore
instance to revert. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
     The location of the Filestore instance.

     To set the location attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property filestore/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-snapshot` | TARGET_SNAPSHOT |  | Name of the Filestore snapshot to revert to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To revert an instance with the name my-instance that's located in
us-central1 to the target snapshot named my-snapshot , run:

    $ gcloud filestore instances revert my-instance \
        --target-snapshot=my-snapshot --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/revert)

---
### `gcloud filestore instances update`

Update a Filestore instance

Update a Filestore instance.

**Synopsis:**
```
gcloud filestore instances update (INSTANCE : --zone=ZONE) [--async]
    [--description=DESCRIPTION] [--location=LOCATION]
    [--performance=[max-iops=MAX-IOPS],[max-iops-per-tb=MAX-IOPS-PER-TB]]
    [--region=REGION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [[--file-share=[capacity=CAPACITY],
      [name=NAME],[nfs-export-options=NFS-EXPORT-OPTIONS]
      : --clear-nfs-export-options]]
    [--[no-]deletion-protection
      --deletion-protection-reason=DELETION_PROTECTION_REASON]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     The zone of the instance.

     To set the zone attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument region on the command line;
     + provide the argument location on the command line;
     + set the property filestore/zone;
     + set the property filestore/region;
     + set the property filestore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud Filestore instance. |
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |
| `--performance` | [max-iops=MAX-IOPS],[max-iops-per-tb=MAX-IOPS-PER-TB] |  | Performance configuration for the instance. This flag is used to configure the read IOPS provisioned for the instance. The instance's write IOPS and read/write throughputs will be derived from the configured read IOPS. For more information about the derived performance limits and default performance see: https://cloud.google.com/filestore/docs/performance. Must be one of: max-iops The number of IOPS to provision for the instance. MAX-IOPS must be in multiple of 1000 and in the supported IOPS range for the current capacity of the instance. For more details, see: https://cloud.google.com/filestore/docs/performance. max-iops-per-tb Is used for setting the max IOPS of the instance by specifying the IOPS per TB. When this parameter is used, the max IOPS are derived from the instance capacity: The instance max IOPS will be calculated by multiplying the capacity of the instance (TB) by MAX-IOPS-PER-TB, and rounding to the nearest 1000. The max IOPS will be changed dynamically based on the instance capacity. MAX-IOPS-PER-TB must be in the supported range of the instance. For more details, see: https://cloud.google.com/filestore/docs/performance. Examples: Configure an instance with max-iops performance: $ gcloud filestore instances update example-cluster \ --performance=max-iops=17000 Configure an instance with max-iops-per-tb performance: $ gcloud filestore instances update example-cluster \ --performance=max-iops-per-tb=17000 |
| `--region` | REGION |  | Region of the Cloud Filestore instance. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates the Filestore instance NAME to change the
description to "A new description."

    $ gcloud filestore instances update NAME \
        --description="A new description."

The following command updates a Filestore instance named NAME to add the
label "key1=value1" and remove any metadata with the label "key2".

    $ gcloud filestore instances update NAME \
        --update-labels=key1=value1 --remove-labels=key2

    $ gcloud filestore instances update NAME --zone=ZONE \
        --flags-file=FILE_PATH

Example json configuration file:        {
    "--file-share":
    {
      "capacity": "102400",
      "name": "my_vol",
      "nfs-export-options": [
        {
          "access-mode": "READ_WRITE",
          "ip-ranges": [
            "10.0.0.0/29",
            "10.2.0.0/29"
          ],
          "squash-mode": "ROOT_SQUASH",
          "anon_uid": 1003,
          "anon_gid": 1003
        }
      ]
    }
    }

The following command updates a Filestore instance named NAME to change the
capacity to CAPACITY.

    $ gcloud filestore instances update NAME --project=PROJECT_ID \
        --zone=ZONE --file-share=name=VOLUME_NAME,capacity=CAPACITY

The following command updates a Filestore instance named NAME to configure
the max-iops-per-tb to MAX-IOPS-PER-TB.

    $ gcloud filestore instances update NAME --project=PROJECT_ID \
        --zone=ZONE --performance=max-iops-per-tb=MAX-IOPS-PER-TB
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/update)

---

## `gcloud filestore instances snapshots` — create and manage Filestore snapshots
### `gcloud filestore instances snapshots create`

Create a Filestore snapshot

Create a Filestore snapshot of an instance.

This command can fail for the following reasons:
  o A snapshot with the same name already exists.
  o The active account does not have permission to create snapshots.
  o Maximum number of snapshots for the instance has been reached.
  o The service tier of the instance does not support snapshots.

**Synopsis:**
```
gcloud filestore instances snapshots create SNAPSHOT --instance=INSTANCE
    (--instance-location=INSTANCE_LOCATION
      | --instance-region=INSTANCE_REGION) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT
   Name of the Filestore snapshot to be created.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the Filestore instance that you want to create a snapshot of. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the snapshot. Limit: 2048 characters. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |


**Examples:**
```bash
To create a snapshot with the name my-snapshot for an instance named
my-instance that's located in us-central1, run:

    $ gcloud filestore instances snapshots create my-snapshot \
        --instance=my-instance --instance-region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/snapshots/create)

---
### `gcloud filestore instances snapshots delete`

Delete a Filestore snapshot

Delete a Filestore snapshot.

This command can fail for the following reasons:
  o The snapshot or instance specified does not exist.
  o The active account does not have permission to delete the given
    snapshot.

**Synopsis:**
```
gcloud filestore instances snapshots delete SNAPSHOT --instance=INSTANCE
    (--instance-location=INSTANCE_LOCATION
      | --instance-region=INSTANCE_REGION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT
   Name of the Filestore snapshot to be deleted.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the Filestore instance the snapshot belongs to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a snapshot named my-snapshot for the instance my-instance from
us-central1, run:

    $ gcloud filestore instances snapshots delete my-snapshot \
        --instance=my-instance --instance-region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/snapshots/delete)

---
### `gcloud filestore instances snapshots describe`

Display information about a Filestore snapshot

Displays information about a Filestore snapshot given a valid snapshot
name, as well as instance name and instance region.

This command can fail for the following reasons:
  o The snapshot or instance specified does not exist.
  o The active account does not have permission to access the given
    snapshot.

**Synopsis:**
```
gcloud filestore instances snapshots describe SNAPSHOT --instance=INSTANCE
    (--instance-location=INSTANCE_LOCATION
      | --instance-region=INSTANCE_REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT
   Name of the Filestore snapshot to display information about.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the Filestore instance the snapshot belongs to. |


**Examples:**
```bash
To display all information associated with a snapshot of the name
my-snapshot for the instance my-instance from us-central1, run:

    $ gcloud filestore instances snapshots describe my-snapshot \
        --instance=my-instance --instance-region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/snapshots/describe)

---
### `gcloud filestore instances snapshots list`

List Filestore snapshots

List all Filestore snapshots for the specified instance.

To limit the number of snapshots to list, use the --limit flag.

This command can fail for the following reasons:
  o Specified instance does not exist.
  o The active account does not have permission to list snapshots for the
    given instance.
  o The service tier of the instance does not support snapshots.

**Synopsis:**
```
gcloud filestore instances snapshots list --instance=INSTANCE
    (--instance-location=INSTANCE_LOCATION
      | --instance-region=INSTANCE_REGION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the Filestore instance the snapshot belongs to. |


**Examples:**
```bash
To list up to five snapshots for the instance my-instance from us-central1,
run:

    $ gcloud filestore instances snapshots list --instance=my-instance \
      --instance-region=us-central1 --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/snapshots/list)

---
### `gcloud filestore instances snapshots update`

Update the description or labels of a Filestore snapshot

Update the metadata of a Filestore snapshot.

This command can fail for the following reasons:
  o The snapshot or instance specified does not exist.
  o The active account does not have permission to update the given
    snapshot.

**Synopsis:**
```
gcloud filestore instances snapshots update SNAPSHOT --instance=INSTANCE
    (--instance-location=INSTANCE_LOCATION
      | --instance-region=INSTANCE_REGION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT
   Name of the Filestore snapshot to be updated.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | Name of the Filestore instance the snapshot belongs to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the snapshot. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a snapshot named my-snapshot for the instance
my-instance from us-central1, run:

    $ gcloud filestore instances snapshots update my-snapshot \
        --instance=my-instance --instance-region=us-central1 \
        --description="A new description."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/instances/snapshots/update)

---
# gcloud netapp storage-pools

create and manage Cloud NetApp Storage Pools

### `gcloud netapp storage-pools create`

Create a Cloud NetApp Storage Pool

Creates a Storage Pool to contain Volumes with a specified Service Level
and capacity.

**Synopsis:**
```
gcloud netapp storage-pools create (STORAGE_POOL : --location=LOCATION)
    --capacity=CAPACITY --network=[name=NAME],[psa-range=PSA-RANGE]
    --service-level=SERVICE_LEVEL [--active-directory=ACTIVE_DIRECTORY]
    [--allow-auto-tiering=ALLOW_AUTO_TIERING] [--async]
    [--custom-performance-enabled=CUSTOM_PERFORMANCE_ENABLED]
    [--description=DESCRIPTION] [--enable-ldap=ENABLE_LDAP]
    [--kms-config=KMS_CONFIG] [--labels=[KEY=VALUE,...]]
    [--qos-type=QOS_TYPE] [--replica-zone=REPLICA_ZONE]
    [--total-iops=TOTAL_IOPS] [--total-throughput=TOTAL_THROUGHPUT]
    [--type=TYPE] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The Storage Pool to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage_pool or fully qualified identifier for the
     storage_pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the storage_pool.

     To set the location attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--capacity` | CAPACITY |  | The desired capacity of the Storage Pool in GiB or TiB units.If no capacity unit is specified, GiB is assumed. |
| `--network` | [name=NAME],[psa-range=PSA-RANGE] |  | Network configuration for a Cloud NetApp Files Storage Pool. Specifying psa-range is optional. name The name of the Google Compute Engine VPC network to which the volume is connected. Short-form (VPC network ID) or long-form (full VPC network name: projects/PROJECT/locations/LOCATION/networks/NETWORK) are both accepted, but please use the long-form when attempting to create a Storage Pool using a shared VPC. psa-range This field is not implemented. The values provided in this field are ignored. |
| `--service-level` | one of: extreme Extreme Service Level for Cloud NetApp Storage Pool |  | The service level for the Cloud NetApp Storage Pool. For more details, see: https://cloud.google.com/netapp/volumes/docs/configure-and-use/storage-pools/overview#service_levels SERVICE_LEVEL must be one of: extreme Extreme Service Level for Cloud NetApp Storage Pool. The Extreme Service Level has a throughput per GiB of allocated volume size of 128 KiB/s. flex Flex Service Level for Cloud NetApp Storage Pool. The Flex Service Level has a throughput per GiB of allocated volume size of 16 KiB/s. premium Premium Service Level for Cloud NetApp Storage Pool. The Premium Service Level has a throughput per GiB of allocated volume size of 64 KiB/s. standard Standard Service Level for Cloud NetApp Storage Pool. The Standard Service Level has a throughput per GiB of allocated volume size of 16 KiB/s. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--active-directory` | ACTIVE_DIRECTORY |  | _[* set the property netapp/location.]_ ID of the active_directory or fully qualified identifier for the active_directory. To set the active_directory attribute: + provide the argument --active-directory on the command line. |
| `--allow-auto-tiering` | ALLOW_AUTO_TIERING |  | _[* set the property netapp/location.]_ Boolean flag indicating whether Storage Pool is allowed to use auto-tiering |
| `--async` |  |  | _[* set the property netapp/location.]_ Return immediately, without waiting for the operation in progress to complete. |
| `--custom-performance-enabled` | CUSTOM_PERFORMANCE_ENABLED |  | _[* set the property netapp/location.]_ Boolean flag indicating whether Storage Pool is a custom performance Storage Pool or not |
| `--description` | DESCRIPTION |  | _[* set the property netapp/location.]_ A description of the Cloud NetApp Storage Pool |
| `--enable-ldap` | ENABLE_LDAP |  | _[* set the property netapp/location.]_ Boolean flag indicating whether Storage Pool is a NFS LDAP Storage Pool or not |
| `--kms-config` | KMS_CONFIG |  | _[* set the property netapp/location.]_ ID of the kms_config or fully qualified identifier for the kms_config. To set the kms_config attribute: + provide the argument --kms-config on the command line. |
| `--labels` | [KEY=VALUE,...] |  | _[* set the property netapp/location.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--qos-type` | one of: auto, manual, qos-type-unspecified |  | _[* set the property netapp/location.]_ Quality of service (QoS) type for the Storage Pool. QOS_TYPE must be one of: auto, manual, qos-type-unspecified. |
| `--replica-zone` | REPLICA_ZONE |  | _[* set the property netapp/location.]_ String indicating replica zone for the Storage Pool |
| `--total-iops` | TOTAL_IOPS |  | _[* set the property netapp/location.]_ Integer indicating total IOPS of the Storage Pool |
| `--total-throughput` | TOTAL_THROUGHPUT |  | _[* set the property netapp/location.]_ The total throughput of the Storage Pool in MiB/s or GiB/s units. If no throughput unit is specified, MiB/s is assumed. |
| `--type` | one of: file File-based volumes only (default) |  | _[* set the property netapp/location.]_ The type of the Storage Pool. FILE pools support file-based volumes only. UNIFIED pools support both file and block volumes. TYPE must be one of: file File-based volumes only (default). unified Both file and block volumes. |
| `--zone` | ZONE |  | _[* set the property netapp/location.]_ String indicating active zone of the Storage Pool |


**Examples:**
```bash
The following command creates a Storage Pool named NAME using all possible
arguments with a VPC network in the same project

    $ gcloud netapp storage-pools create NAME --location=us-central1 \
      --service-level=standard --capacity=2048 \
      --network=name=default --active-directory=ad1 \
      --kms-config=kms-config1 --enable-ldap=true \
      --description="example description"

The following command creates a Storage pool named NAME using all possible
arguments with a shared VPC network in a separate project called
VPC_PROJECT

    $ gcloud netapp storage-pools create NAME --location=us-central1 \
      --service-level=standard --capacity=2048 \
      --network=name=projects/VPC_PROJECT/locations/us-central1/\
    networks/default --active-directory=ad1 --kms-config=kms-config1 \
        --enable-ldap=true --description="example description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/create)

---
### `gcloud netapp storage-pools delete`

Delete a Cloud NetApp Storage Pool

Delete a Storage Pool

**Synopsis:**
```
gcloud netapp storage-pools delete (STORAGE_POOL : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The Storage Pool to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage_pool or fully qualified identifier for the
     storage_pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the storage_pool.

     To set the location attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a Storage Pool named NAME in the given
location

    $ gcloud netapp storage-pools delete NAME --location=us-central1

To delete a Storage Pool asynchronously, run the following command:

    $ gcloud netapp storage-pools delete NAME --location=us-central1 \
      --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/delete)

---
### `gcloud netapp storage-pools describe`

Show metadata for a Cloud NetApp Storage Pool

Describe a Storage Pool

**Synopsis:**
```
gcloud netapp storage-pools describe (STORAGE_POOL : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The Storage Pool to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage_pool or fully qualified identifier for the
     storage_pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the storage_pool.

     To set the location attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command describes a Storage Pool named NAME in the given
location

    $ gcloud netapp storage-pools describe NAME --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/describe)

---
### `gcloud netapp storage-pools list`

List Cloud NetApp Storage Pools

Lists Storage Pools

**Synopsis:**
```
gcloud netapp storage-pools list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists Storage Pools in the given location

    $ gcloud netapp storage-pools list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/list)

---
### `gcloud netapp storage-pools switch`

Switch a Regional Cloud NetApp Flex Storage Pool zone

Switch a Regional Cloud NetApp Flex Storage Pool zone.

**Synopsis:**
```
gcloud netapp storage-pools switch (STORAGE_POOL : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The Storage Pool to switch. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage_pool or fully qualified identifier for the
     storage_pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the storage_pool.

     To set the location attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command switches zone of a Storage Pool named NAME using the
required arguments:

    $ gcloud netapp storage-pools switch NAME --location=us-central1

To switch zone of a Storage Pool named NAME asynchronously, run the
following command:

    $ gcloud netapp storage-pools switch NAME --location=us-central1 \
      --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/switch)

---
### `gcloud netapp storage-pools update`

Update a Cloud NetApp Storage Pool

Updates a Storage Pool with given arguments

**Synopsis:**
```
gcloud netapp storage-pools update (STORAGE_POOL : --location=LOCATION)
    [--active-directory=ACTIVE_DIRECTORY]
    [--allow-auto-tiering=ALLOW_AUTO_TIERING] [--async]
    [--capacity=CAPACITY] [--description=DESCRIPTION] [--qos-type=QOS_TYPE]
    [--replica-zone=REPLICA_ZONE] [--total-iops=TOTAL_IOPS]
    [--total-throughput=TOTAL_THROUGHPUT] [--update-labels=[KEY=VALUE,...]]
    [--zone=ZONE] [--clear-labels | --remove-labels=[KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The Storage Pool to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage_pool or fully qualified identifier for the
     storage_pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the storage_pool.

     To set the location attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--active-directory` | ACTIVE_DIRECTORY |  | _[* set the property netapp/location.]_ ID of the active_directory or fully qualified identifier for the active_directory. To set the active_directory attribute: + provide the argument --active-directory on the command line. |
| `--allow-auto-tiering` | ALLOW_AUTO_TIERING |  | _[* set the property netapp/location.]_ Boolean flag indicating whether Storage Pool is allowed to use auto-tiering |
| `--async` |  |  | _[* set the property netapp/location.]_ Return immediately, without waiting for the operation in progress to complete. |
| `--capacity` | CAPACITY |  | _[* set the property netapp/location.]_ The desired capacity of the Storage Pool in GiB or TiB units.If no capacity unit is specified, GiB is assumed. |
| `--description` | DESCRIPTION |  | _[* set the property netapp/location.]_ A description of the Cloud NetApp Storage Pool |
| `--qos-type` | one of: auto, manual, qos-type-unspecified |  | _[* set the property netapp/location.]_ Quality of service (QoS) type for the Storage Pool. QOS_TYPE must be one of: auto, manual, qos-type-unspecified. |
| `--replica-zone` | REPLICA_ZONE |  | _[* set the property netapp/location.]_ String indicating replica zone for the Storage Pool |
| `--total-iops` | TOTAL_IOPS |  | _[* set the property netapp/location.]_ Integer indicating total IOPS of the Storage Pool |
| `--total-throughput` | TOTAL_THROUGHPUT |  | _[* set the property netapp/location.]_ The total throughput of the Storage Pool in MiB/s or GiB/s units. If no throughput unit is specified, MiB/s is assumed. |
| `--update-labels` | [KEY=VALUE,...] |  | _[* set the property netapp/location.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--zone` | ZONE |  | _[* set the property netapp/location.]_ String indicating active zone of the Storage Pool |
| `--clear-labels` |  |  | _[At most one of these can be specified:]_ Remove all labels. If --update-labels is also specified then --clear-labels is applied first. For example, to remove all labels: $ gcloud netapp storage-pools update --clear-labels To remove all existing labels and create two new labels, foo and baz: $ gcloud netapp storage-pools update --clear-labels \ --update-labels foo=bar,baz=qux |
| `--remove-labels` | [KEY,...] |  | _[At most one of these can be specified:]_ List of label keys to remove. If a label does not exist it is silently ignored. If --update-labels is also specified then --update-labels is applied first. |


**Examples:**
```bash
The following command updates a Storage Pool named NAME in the given
location

    $ gcloud netapp storage-pools update NAME --location=us-central1 \
      --capacity=4096 --active-directory=ad-2 \
      --description="new description" --update-labels=key1=val1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/update)

---
### `gcloud netapp storage-pools validate-directory-service`

Validate directory service for a Cloud Netapp storage pool

Validate the directory service for a Cloud Netapp storage pool.

**Synopsis:**
```
gcloud netapp storage-pools validate-directory-service
    (STORAGE_POOL : --location=LOCATION) [--async]
    [--directory-service-type=DIRECTORY_SERVICE_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The Storage Pool to validate. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage_pool or fully qualified identifier for the
     storage_pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the storage_pool.

     To set the location attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--directory-service-type` | DIRECTORY_SERVICE_TYPE |  | String indicating directory service type for the Storage Pool |


**Examples:**
```bash
The following command validates the directory service of type
ACTIVE_DIRECTORY for a storage pool named NAME:

    $ gcloud netapp storage-pools validate-directory-service NAME \
      --location=us-central1 --directory-service-type=ACTIVE_DIRECTORY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/storage-pools/validate-directory-service)

---
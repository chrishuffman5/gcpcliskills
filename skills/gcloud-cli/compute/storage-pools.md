# gcloud compute storage-pools

read and manipulate storage pools

### `gcloud compute storage-pools create`

Create a storage pool

Create a storage pool.

**Synopsis:**
```
gcloud compute storage-pools create STORAGE_POOL
    --provisioned-capacity=PROVISIONED_CAPACITY
    --storage-pool-type=STORAGE_POOL_TYPE [--async]
    [--capacity-provisioning-type=CAPACITY_PROVISIONING_TYPE]
    [--description=DESCRIPTION]
    [--performance-provisioning-type=PERFORMANCE_PROVISIONING_TYPE]
    [--provisioned-iops=PROVISIONED_IOPS]
    [--provisioned-throughput=PROVISIONED_THROUGHPUT] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - The name of the storage pool you want to create.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the zone attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --zone on the command line;
 * set the property compute/zone.

This must be specified.

  STORAGE_POOL
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--provisioned-capacity` | PROVISIONED_CAPACITY |  | Provisioned capacity of the storage pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--capacity-provisioning-type` | one of: advanced, standard |  | Capacity provisioning type. CAPACITY_PROVISIONING_TYPE must be one of: advanced, standard. |
| `--description` | DESCRIPTION |  | Description of the storage pool. |
| `--performance-provisioning-type` | one of: advanced, standard |  | Performance provisioning type. PERFORMANCE_PROVISIONING_TYPE must be one of: advanced, standard. |
| `--provisioned-iops` | PROVISIONED_IOPS |  | IOPS with which to provision the pool. |
| `--provisioned-throughput` | PROVISIONED_THROUGHPUT |  | Throughput in MB/s with which to provision the pool. |
| `--zone` | ZONE |  | For resources [storage-pool-type, storage_pool], provides fallback value for resource zone attribute. When the resource's full URI path is not provided, zone will fallback to this flag value. |


**Examples:**
```bash
To create a new storage pool named my-storage-pool, run the following
command:

    $ gcloud compute storage-pools create my-storage-pool \
        --storage-pool-type=hyperdisk-throughput \
        --provisioned-capacity=10TB --provisioned-throughput=200
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/create)

---
### `gcloud compute storage-pools delete`

Delete a storage pool

Deleta a storage pool.

**Synopsis:**
```
gcloud compute storage-pools delete (STORAGE_POOL : --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - Name of the storage pool you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a single storage pool named my-storage-pool, run the following
command:

    $ gcloud compute storage-pools delete my-storage-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/delete)

---
### `gcloud compute storage-pools describe`

Describe a storage pool

Describe a storage pool.

**Synopsis:**
```
gcloud compute storage-pools describe (STORAGE_POOL : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - Name of the storage pool you want to inspect. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To retrieve a single storage pool and print its properties, run the
following command:

    $ gcloud compute storage-pools describe my-storage-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/describe)

---
### `gcloud compute storage-pools get-iam-policy`

Get the IAM policy of a storage pool

Get the IAM policy of a storage pool.

**Synopsis:**
```
gcloud compute storage-pools get-iam-policy (STORAGE_POOL : --zone=ZONE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - Storage pool you want to get the IAM permissions
of. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
The following command retrieves the IAM configuration of the specified
storage pool.

    $ gcloud compute storage-pools get-iam-policy my-storage-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/get-iam-policy)

---
### `gcloud compute storage-pools list`

View storage pools

View storage pools.

The compact, default output format is explained below:

The type column contains all three types -- storage pool type, capacity and
performance. For example, the value

> "Hdb/Adv/Std"

means the storage pool type is "hyperdisk-balanced", its capacity type is
"advanced", and its performance type is "standard."

The list of storage pool abbreviations is as follows:

  o HdB: Hyperdisk Balanced
  o HdT: Hyperdisk Throughput

The list of capacity/performance abbreviations is as follows:

  o Adv: Advanced
  o Std: Standard

The capacity column, and standard-performance iops and throughput columns
describe the used, provisioned, and the utilization rate. For example, the
following value for capacity:

40 / 50 (80%)

means 40 TB of it is used, 50 TB provisioned, and its utilization rate is
80%. The utilization rate is equivalent to used capacity divided by
provisioned capacity.

For advanced-performance storage pools, the iops and throughput columns
will simply show the provisioned values.

**Synopsis:**
```
gcloud compute storage-pools list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To display all storage pools in all regions and zones, run the following
command:

    $ gcloud compute storage-pools list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/list)

---
### `gcloud compute storage-pools list-disks`

View the disks that are in a storage pool

View the disks that are in a given storage pool.

**Synopsis:**
```
gcloud compute storage-pools list-disks (STORAGE_POOL : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - Name of the storage pool you want to inspect. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
The following command retrieves all disks belonging to a storage pool and
lists them:

    $ gcloud compute storage-pools list-disks my-storage-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/list-disks)

---
### `gcloud compute storage-pools set-iam-policy`

Set the IAM policy of the given storage pool

Set the IAM policy of the given storage pool.

**Synopsis:**
```
gcloud compute storage-pools set-iam-policy (STORAGE_POOL : --zone=ZONE)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - Storage pool you want to get the IAM permissions
of. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
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
The following command sets the IAM configuration of the specified storage
pool with the specified policy file.

    $ gcloud compute storage-pools set-iam-policy my-storage-pool \
        policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/set-iam-policy)

---
### `gcloud compute storage-pools update`

Update a storage pool

Update a storage pool.

**Synopsis:**
```
gcloud compute storage-pools update (STORAGE_POOL : --zone=ZONE) [--async]
    [--description=DESCRIPTION]
    [--provisioned-capacity=PROVISIONED_CAPACITY]
    [--provisioned-iops=PROVISIONED_IOPS]
    [--provisioned-throughput=PROVISIONED_THROUGHPUT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool resource - Storage pool you want to update. The arguments in
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
     ID of the storage pool or fully qualified identifier for the storage
     pool.

     To set the storage_pool attribute:
     + provide the argument storage_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the storage pool. |
| `--provisioned-capacity` | PROVISIONED_CAPACITY |  | Provisioned capacity of the storage pool. |
| `--provisioned-iops` | PROVISIONED_IOPS |  | IOPS to provision the pool with. |
| `--provisioned-throughput` | PROVISIONED_THROUGHPUT |  | Throughput in MB/s provision the pool with. |


**Examples:**
```bash
To update the size of a storage pool named 'my-storage-pool', run th
following command:

    $ gcloud compute storage-pools update my-storage-pool \
        --provisioned-capacity=20TB
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pools/update)

---
# gcloud redis instances

manage Cloud Memorystore Redis instances

### `gcloud redis instances create`

Create a Memorystore Redis instance

Create a new Redis instance.

This command can fail for the following reasons:
  o An instance with the same name already exists.
  o The active account does not have permission to create instances.

**Synopsis:**
```
gcloud redis instances create (INSTANCE : --region=REGION)
    [--alternative-zone=ALTERNATIVE_ZONE] [--async]
    [--connect-mode=CONNECT_MODE]
    [--customer-managed-key=CUSTOMER_MANAGED_KEY]
    [--display-name=DISPLAY_NAME] [--enable-auth]
    [--labels=[KEY=VALUE,...]]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY]
    [--maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [--network=NETWORK; default="default"]
    [--persistence-mode=PERSISTENCE_MODE]
    [--rdb-snapshot-period=RDB_SNAPSHOT_PERIOD]
    [--rdb-snapshot-start-time=RDB_SNAPSHOT_START_TIME]
    [--read-replicas-mode=READ_REPLICAS_MODE]
    [--redis-config=[KEY=VALUE,...]] [--redis-version=VERSION]
    [--replica-count=REPLICA_COUNT] [--reserved-ip-range=RESERVED_IP_RANGE]
    [--size=SIZE; default=1] [--tier=TIER; default="basic"]
    [--transit-encryption-mode=TRANSIT_ENCRYPTION_MODE] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--alternative-zone` | ALTERNATIVE_ZONE |  | A secondary zone for the Redis instance. Only applicable to the standard tier. This protects the instance against zonal failures by provisioning it across two zones. If provided, alternative zone must be a different zone from the one provided through --zone. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--connect-mode` | one of: connect-mode-unspecified, direct-peering, private-service-access |  | Network connection mode used by instances. CONNECT_MODE must be one of: connect-mode-unspecified, direct-peering, private-service-access. |
| `--customer-managed-key` | CUSTOMER_MANAGED_KEY |  | The KMS key reference that you want to use to encrypt the data at rest for this Redis instance. If this is provided, CMEK is enabled. |
| `--display-name` | DISPLAY_NAME |  | A human-readable name for the instance. |
| `--enable-auth` |  |  | Enables Redis AUTH for the instance. If omitted AUTH is disabled. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--maintenance-window-day` | one of: SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY |  | Day of week for maintenance window, in UTC time zone. MAINTENANCE_WINDOW_DAY must be one of: SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY. MAINTENANCE_WINDOW_DAY must be one of: day-of-week-unspecified, friday, monday, saturday, sunday, thursday, tuesday, wednesday. |
| `--maintenance-window-hour` | MAINTENANCE_WINDOW_HOUR |  | Hour of day (0 to 23) for maintenance window, in UTC time zone. |
| `--network` | NETWORK | default | The name of the Google Compute Engine network to which the instance will be connected. If left unspecified, the default network will be used. |
| `--persistence-mode` | PERSISTENCE_MODE |  | Operation mode for automated persistence. PERSISTENCE_MODE must be one of: disabled RDB mode is disabled rdb Automatic RDB persistence |
| `--rdb-snapshot-period` | RDB_SNAPSHOT_PERIOD |  | Attempted period between RDB snapshots. RDB_SNAPSHOT_PERIOD must be one of: 12h 12 hours 1h 1 hour 24h 24 hours 6h 6 hours |
| `--rdb-snapshot-start-time` | RDB_SNAPSHOT_START_TIME |  | Date and time of the first snapshot in the ISO 1801 format, and alignment time for future snapshots. For example, 2022-11-02T03:00:00Z. |
| `--read-replicas-mode` | one of: read-replicas-disabled Read replica is disabled for the instance |  | Read replicas mode used by the instance. Only works against standard tier instances with 5GB and above provisioned capacity. READ_REPLICAS_MODE must be one of: read-replicas-disabled Read replica is disabled for the instance. Read endpoint will not be provided and the instance cannot scale up or down the number of replicas. read-replicas-enabled Read replica is enabled for the instance. Read endpoint will be provided and the instance can scale up and down the number of replicas. |
| `--redis-config` | [KEY=VALUE,...] |  | A list of Redis config KEY=VALUE pairs to set on the instance according to http://redis.io/topics/config. Currently, the only supported parameters are: Redis version 3.2 and newer: maxmemory-policy, notify-keyspace-events, timeout, databases. Redis version 4.0 and newer: activedefrag, lfu-decay-time, lfu-log-factor, maxmemory-gb. Redis version 5.0 and newer: stream-node-max-bytes, stream-node-max-entries. |
| `--redis-version` | VERSION |  | The version of Redis software. VERSION must be one of: redis_3_2 Redis 3.2 compatibility redis_4_0 Redis 4.0 compatibility redis_5_0 Redis 5.0 compatibility redis_6_x Redis 6.x compatibility redis_7_0 Redis 7.0 compatibility redis_7_2 Redis 7.2 compatibility |
| `--replica-count` | REPLICA_COUNT |  | The replica count of the instance. |
| `--reserved-ip-range` | RESERVED_IP_RANGE |  | For DIRECT_PEERING mode, the CIDR range of internal addresses that are reserved for this instance. Range must be unique and non-overlapping with existing subnets in an authorized network. For PRIVATE_SERVICE_ACCESS mode, the name of an IP address range allocated for the private service access connection. If not provided, the service will choose an unused /29 block, for example, 10.0.0.0/29 or 192.168.0.0/29. If READ_REPLICAS_ENABLED is used for the --read-replicas-mode flag, then the block size required for this flag is /28. |
| `--size` | SIZE | 1 | The memory size of the instance in GiB. If not provided, size of 1 GiB will be used. |
| `--tier` | TIER | basic | The service tier of the instance. TIER must be one of: basic Basic Redis instance with no replication standard Standard high-availability Redis instance with replication |
| `--transit-encryption-mode` | one of: disabled Transit encryption is disabled for the instance |  | Transit encryption mode used by the instance. TRANSIT_ENCRYPTION_MODE must be one of: disabled Transit encryption is disabled for the instance. server-authentication Client to Server traffic encryption enabled with server authentication. |
| `--zone` | ZONE |  | The zone of the Redis instance. If not provided the service will pick a random zone in the region. For the standard tier, instances will be created across two zones for protection against zonal failures. So if --alternative-zone is also provided, it must be different from --zone. |


**Examples:**
```bash
To create a basic tier instance with the name my-redis-instance in region
us-central-1 with memory size of 5 GiB, run:

    $ gcloud redis instances create my-redis-instance \
        --region=us-central1 --size=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/create)

---
### `gcloud redis instances delete`

Delete a Redis instance

Delete a Memorystore Redis instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud redis instances delete (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an instance with the name my-redis-instance in your default
region, run:

    $ gcloud redis instances delete my-redis-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/delete)

---
### `gcloud redis instances describe`

Show metadata for a Memorystore Redis instance

Show metadata for a Memorystore Redis instance.

Displays all metadata associated with a Redis instance given a valid
instance name.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud redis instances describe (INSTANCE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to describe. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To display the metadata for an instance with the name my-redis-instance in
the default region, run:

    $ gcloud redis instances describe my-redis-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/describe)

---
### `gcloud redis instances export`

Export data from a Memorystore Redis instance to Google Cloud Storage

Export data from a Memorystore Redis instance to Google Cloud Storage.

**Synopsis:**
```
gcloud redis instances export DESTINATION (INSTANCE : --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DESTINATION
   The Cloud Storage object path to export the instance to. Must have the
   redis DB file extension *.rdb.

Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to export. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To export the instance with the name my-redis-instance in region
us-central1 to Cloud Storage object gs://my-bucket/my-redis-instance.rdb
run:

    $ gcloud redis instances export \
        gs://my-bucket/my-redis-instance.rdb my-redis-instance \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/export)

---
### `gcloud redis instances failover`

Failover a standard tier Cloud Memorystore for Redis instance from the master node to its replica

Failover a standard tier Cloud Memorystore for Redis instance from the
master node to its replica.

**Synopsis:**
```
gcloud redis instances failover (INSTANCE : --region=REGION) [--async]
    [--data-protection-mode=DATA_PROTECTION_MODE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the standard tier
Cloud Memorystore for Redis instance you want to failover. The arguments
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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--data-protection-mode` | one of: force-data-loss Failover without data loss protection |  | Data protection mode to use for the failover. If not specified, defaults to 'limited-data-loss'. DATA_PROTECTION_MODE must be one of: force-data-loss Failover without data loss protection. Can cause significant data loss. limited-data-loss Failover with data loss protection that ensures loss is within system thresholds. |


**Examples:**
```bash
To failover an instance with the name 'my-redis-instance' in region
'us-central-1', run:

    $ gcloud redis instances failover my-redis-instance \
        --region=us-central1

To failover an instance with the name 'my-redis-instance' in region
'us-central-1' without attempting to limit data loss, run:

    $ gcloud redis instances failover my-redis-instance \
        --region=us-central1 --data-protection-mode=force-data-loss
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/failover)

---
### `gcloud redis instances get-auth-string`

Show AUTH string for a Memorystore Redis instance

Show AUTH string for a Memorystore Redis instance.

Result is empty if AUTH is disabled for the instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to view the AUTH string

**Synopsis:**
```
gcloud redis instances get-auth-string (INSTANCE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to view the AUTH string for. The arguments in this group
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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To display the AUTH string for an instance with the name my-redis-instance
in the default region, run:

    $ gcloud redis instances get-auth-string my-redis-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/get-auth-string)

---
### `gcloud redis instances import`

Import data to a Memorystore Redis instance from Google Cloud Storage

Import data to a Memorystore Redis instance from Google Cloud Storage.

**Synopsis:**
```
gcloud redis instances import SOURCE (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SOURCE
   The Cloud Storage object path to import the instance from. Must have
   the redis DB file extension *.rdb.

Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to import to. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To import to the instance with the name my-redis-instance in region
us-central1 from Cloud Storage object gs://my-bucket/my-redis-instance.rdb
run:

    $ gcloud redis instances import \
        gs://my-bucket/my-redis-instance.rdb my-redis-instance \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/import)

---
### `gcloud redis instances list`

List Memorystore Redis instances

List all Redis instances under the specified project and region.

To specify the maximum number of instances to list, use the --limit flag.

**Synopsis:**
```
gcloud redis instances list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property redis/region. |


**Examples:**
```bash
To list up to five instances, run:

    $ gcloud redis instances list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/list)

---
### `gcloud redis instances reschedule-maintenance`

Reschedule maintenance window for a Redis instance

Reschedule maintenance window for a Redis instance.

**Synopsis:**
```
gcloud redis instances reschedule-maintenance (INSTANCE : --region=REGION)
    --reschedule-type=RESCHEDULE_TYPE [--async]
    [--schedule-time=SCHEDULE_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Cloud Memorystore
for Redis instance you want to reschedule maintenance window. The
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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reschedule-type` | one of: IMMEDIATE, NEXT-AVAILABLE-WINDOW, or SPECIFIC-TIME |  | Reschedule type to use for the reschedule maintenance window. Reschedule Type must be one of:IMMEDIATE, NEXT-AVAILABLE-WINDOW, or SPECIFIC-TIME. RESCHEDULE_TYPE must be one of: immediate Reschedule the maintenance window to perform now. next-available-window Reschedule the maintenance window to the next available window. specific-time Reschedule the maintenance window to a specific time. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--schedule-time` | SCHEDULE_TIME |  | Time in RFC3339 format, for example: 2012-11-15T16:19:00.094Z |


**Examples:**
```bash
To reschedule maintenance window for an instance with the name
'my-redis-instance' in region 'us-central-1' with next available window,
run:

    $ gcloud redis instances reschedule-maintenance my-redis-instance \
        --region=us-central1 --reschedule-type=next-available-window
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/reschedule-maintenance)

---
### `gcloud redis instances update`

Update Memorystore Redis instances

Update the metadata and/or configuration parameters of a Redis instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to update the given
    instance.

**Synopsis:**
```
gcloud redis instances update (INSTANCE : --region=REGION) [--async]
    [--display-name=DISPLAY_NAME] [--enable-auth]
    [--maintenance-version=MAINTENANCE_VERSION]
    [--persistence-mode=PERSISTENCE_MODE]
    [--rdb-snapshot-period=RDB_SNAPSHOT_PERIOD]
    [--rdb-snapshot-start-time=RDB_SNAPSHOT_START_TIME]
    [--read-replicas-mode=READ_REPLICAS_MODE]
    [--remove-redis-config=[KEY,...]] [--replica-count=REPLICA_COUNT]
    [--secondary-ip-range=SECONDARY_IP_RANGE] [--size=SIZE]
    [--update-labels=[KEY=VALUE,...]] [--update-redis-config=KEY=VALUE]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--maintenance-window-any
      | --maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore Redis
instance you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | A human-readable name for the instance. |
| `--enable-auth` |  |  | Enables Redis AUTH for the instance. |
| `--maintenance-version` | MAINTENANCE_VERSION |  | Specifies which maintenance version to apply to your instance during self-service maintenance. To view the available maintenance versions for your instance, run gcloud redis instances describe [INSTANCE_ID]. Acceptable values for this flag are either current_default or one of the specific versions listed by the describe command. If you pass the value current_default, the Memorystore updates to the most recent available maintenance version during self service maintenance. |
| `--persistence-mode` | PERSISTENCE_MODE |  | Operation mode for automated persistence. PERSISTENCE_MODE must be one of: disabled RDB mode is disabled rdb Automatic RDB persistence |
| `--rdb-snapshot-period` | RDB_SNAPSHOT_PERIOD |  | The attempted period between RDB snapshots. RDB_SNAPSHOT_PERIOD must be one of: 12h 12 hours 1h 1 hour 24h 24 hours 6h 6 hours |
| `--rdb-snapshot-start-time` | RDB_SNAPSHOT_START_TIME |  | Date and time of the first snapshot in the ISO 1801 format, and alignment time for future snapshots. For example, 2022-11-02T03:00:00Z. |
| `--read-replicas-mode` | one of: read-replicas-disabled If read replica is not enabled on the instance, no changes are done |  | Read replicas mode used by the instance. Only works against standard tier instances with 5GB and above provisioned capacity and Redis version 5.0 and above. This is an irreversible update i.e. Read replicas can not be disabled for the instance once it is enabled. Also this update is exclusive and cannot be clubbed with other update operations. READ_REPLICAS_MODE must be one of: read-replicas-disabled If read replica is not enabled on the instance, no changes are done. If read replica is enabled for the instance, update operation fails read-replicas-enabled Read replica is enabled for the instance if not already enabled. Read endpoint will be provided and the instance can scale up and down the number of replicas. |
| `--remove-redis-config` | [KEY,...] |  | A list of Redis config parameters to remove. Removing a non-existent config parameter is silently ignored. |
| `--replica-count` | REPLICA_COUNT |  | The replica count of the instance. Valid from 0 to 5. |
| `--secondary-ip-range` | SECONDARY_IP_RANGE |  | Required only when read-replicas-mode is enabled on the instance. The CIDR range of internal addresses that are reserved for this instance. For example, 10.0.0.0/28 or 192.168.0.0/28. Range must be unique and non-overlapping with existing ranges in the network. If value 'auto' passed, the service will automatically pick an available range. |
| `--size` | SIZE |  | The memory size of the instance in GiB. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--update-redis-config` | KEY=VALUE |  | A list of Redis config KEY=VALUE pairs to update according to http://cloud.google.com/memorystore/docs/reference/redis-configs. If a config parameter is already set, its value is modified; otherwise a new Redis config parameter is added. Currently, the only supported parameters are: Redis version 3.2 and newer: maxmemory-policy, notify-keyspace-events, timeout. Redis version 4.0 and newer: activedefrag, lfu-decay-time, lfu-log-factor, maxmemory-gb. Redis version 5.0 and newer: stream-node-max-bytes, stream-node-max-entries. Redis version 7.0 and newer: maxmemory-clients, lazyfree-lazy-eviction, lazyfree-lazy-expire, lazyfree-lazy-user-del, lazyfree-lazy-user-flush. |


**Examples:**
```bash
To update a Redis instance with the name my-redis-instance to have the
display name "Cache for Foo Service", and add the two labels, env and
service, run:

    $ gcloud redis instances update my-redis-instance \
        --display-name="Cache for Foo Service" \
        --update-labels=env=test,service=foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/update)

---
### `gcloud redis instances upgrade`

Upgrade a Memorystore for Redis instance to a specified Redis version

Upgrade a Memorystore for Redis instance to a specified Redis version.

**Synopsis:**
```
gcloud redis instances upgrade (INSTANCE : --region=REGION)
    --redis-version=VERSION [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore for
Redis instance you want to upgrade. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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

  --region=REGION
     The name of the Redis region of the instance. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--redis-version` | VERSION |  | Target version of Redis software. VERSION must be one of: redis_4_0 Redis 4.0 compatibility redis_5_0 Redis 5.0 compatibility redis_6_x Redis 6.x compatibility redis_7_0 Redis 7.0 compatibility redis_7_2 Redis 7.2 compatibility |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upgrade an instance with the name my-redis-instance in region
us-central1 to Redis version 4.0 run:

    $ gcloud redis instances upgrade my-redis-instance \
        --region=us-central1 --redis-version=redis_4_0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/instances/upgrade)

---
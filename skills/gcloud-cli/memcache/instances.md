# gcloud memcache instances

manage Cloud Memorystore Memcached instances

### `gcloud memcache instances apply-parameters`

Apply parameter update to nodes in a Memorystore Memcached instance

Apply a parameter update to nodes in a Memcached instance from the current
configuration parameters staged in the instance metadata.

Applying a parameter update to a node causes a full cache flush on that
node.

**Synopsis:**
```
gcloud memcache instances apply-parameters (INSTANCE : --region=REGION)
    (--apply-all | --node-ids=[NODE_IDS,...]) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memcached
instance on which to apply parameter update. The arguments in this group
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
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--apply-all` |  |  | _[Exactly one of these must be specified:]_ Apply the parameter update onto all nodes. |
| `--node-ids` | [NODE_IDS,...] |  | _[Exactly one of these must be specified:]_ Nodes on which to apply the parameter update. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To apply parameter update to nodes 'node-1' and 'node-2' of a Memcached
instance named 'my-memcache-instance' in region 'us-central1', run:

    $ gcloud memcache instances apply-parameters my-memcache-instance \
        --node-ids=node-1,node-2 --region=us-central1

To apply parameter update to all nodes of a Memcached instance named
'my-memcache-instance' in region 'us-central1', run:

    $ gcloud memcache instances apply-parameters my-memcache-instance \
        --apply-all --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/apply-parameters)

---
### `gcloud memcache instances create`

Create a Memorystore Memcached instance

Create a new Memorystore Memcached instance.

This command can fail for the following reasons:
  o An instance with the same name already exists.
  o The active account does not have the necessary permissions to create
    instances.

**Synopsis:**
```
gcloud memcache instances create (INSTANCE : --region=REGION)
    --node-count=NODE_COUNT --node-cpu=NODE_CPU --node-memory=NODE_MEMORY
    [--async] [--authorized-network=AUTHORIZED_NETWORK]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY]
    [--maintenance-window-duration=MAINTENANCE_WINDOW_DURATION]
    [--maintenance-window-start-time=MAINTENANCE_WINDOW_START_TIME]
    [--memcached-version=MEMCACHED_VERSION] [--parameters=KEY=VALUE]
    [--reserved-ip-range-id=[RESERVED_IP_RANGE_ID,...]]
    [--zones=[ZONES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memcached
instance to create. The arguments in this group can be used to specify the
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

  --region=REGION
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-count` | NODE_COUNT |  | Number of memcache nodes in this instance. Valid values range from 1 to 20. |
| `--node-cpu` | NODE_CPU |  | Number of cpus per node in this instance. Valid values are 1 or even number between 2-32. Value of 1 is not supported in all regions. |
| `--node-memory` | NODE_MEMORY |  | Amount of memory allocated per node in this instance. The value must be a whole number followed by a size unit of 'MB' for megabyte, or 'GB' for gigabyte, ie '3072MB' or '9GB'. The value must be between 1024MB and 307200MB. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--authorized-network` | AUTHORIZED_NETWORK |  | Full name of the Google Compute Engine network to which the instance is connected. If unspecified, the default network will be used. |
| `--display-name` | DISPLAY_NAME |  | An arbitrary and optional user provided name for the instance. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--maintenance-window-day` | one of: friday, monday, saturday, sunday, thursday, tuesday, wednesday |  | The day of week when the window starts, e.g. sunday. MAINTENANCE_WINDOW_DAY must be one of: friday, monday, saturday, sunday, thursday, tuesday, wednesday. |
| `--maintenance-window-duration` | MAINTENANCE_WINDOW_DURATION |  | Duration in integer hours (3 to 8) of the maintenance window. |
| `--maintenance-window-start-time` | MAINTENANCE_WINDOW_START_TIME |  | Hour of day (0 to 23) for the start of maintenance window, in UTC time zone. |
| `--memcached-version` | MEMCACHED_VERSION |  | Optional major version of Memcached software to use with the instance. If not provided, default of "1.5" will be used. MEMCACHED_VERSION must be one of: 1.5 Memcached major version 1.5 1.6.15 Memcached version 1.6.15 |
| `--parameters` | KEY=VALUE |  | User defined parameters to apply to the memcached process on each node. Possible attributes include: listen-backlog The backlog queue limit for the instance. disable-flush-all If enabled, flush_all command will be disabled. Applicable to 1.4.24 and higher. max-item-size Max bytes of the instnace. Must at least be equal to slab_chunk_max (which defaults to 524288 bytes) and less than 134217728 bytes. Additionally it must be a multiple of slab_chunk_max. slab-min-size This is an integer in the range [1, 1024]. slab-growth-factor This is a float in the range [1.01, 100]. protocol This is an enum with acceptable values of ["ascii", "auto"]. disable-cas This is a boolean value. disable-evictions This is a boolean value. max-reqs-per-event This is an integer in the range [1, 1000]. track-sizes This is a boolean value. worker-logbuf-size This is an integer in the range [48, 524288]. watcher-logbuf-size This is an integer in the range [0, 2097151]. lru-crawler This is a boolean value. idle-timeout This is an integer in the range [1,86400]. lru-maintainer This is a boolean value. maxconns-fast This is a boolean value. hash-algorithm This is an enum with accepted values of ["jenkins", "murmur3"]. |
| `--reserved-ip-range-id` | [RESERVED_IP_RANGE_ID,...] |  | Contains the name of allocated IP address ranges associated with the private service access connection for example, "test-default" associated with IP range 10.0.0.0/29. |
| `--zones` | [ZONES,...] |  | List of zones for the memcache nodes. The nodes will be divided equally across the given zones up to --node-count value. If not provided, the service will by default create nodes in all zones in the region specified by --region flag. |


**Examples:**
```bash
To create a Memcached instance named 'my-memcache-instance' in region
'us-central1' with 3 nodes, each with 2 CPUs and 2GB of memory, run:

    $ gcloud memcache instances create my-memcache-instance \
        --region=us-central1 --node-count=3 --node-cpu=2 \
        --node-memory=2GB
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/create)

---
### `gcloud memcache instances delete`

Delete a Memorystore Memcached instance

Delete a Memorystore Memcached instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud memcache instances delete (INSTANCE : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memcached
instance to delete. The arguments in this group can be used to specify the
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

  --region=REGION
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an instance named my-memcache-instance in region us-central1,
run:

    $ gcloud memcache instances delete my-memcache-instance \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/delete)

---
### `gcloud memcache instances describe`

Display metadata for a Memorystore Memcached instance

Displays all metadata associated with a Memcached instance given a valid
instance name.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud memcache instances describe (INSTANCE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memcached
instance to describe. The arguments in this group can be used to specify
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

  --region=REGION
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Examples:**
```bash
To display the metadata for an instance named my-memcache-instance in
region us-central1, run:

    $ gcloud memcache instances describe my-memcache-instance \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/describe)

---
### `gcloud memcache instances list`

List Memorystore Memcached instances

List all Memcached instances under the specified project and region.

Specify the maximum number of instances to list using the --limit flag.

**Synopsis:**
```
gcloud memcache instances list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property memcache/region. |


**Examples:**
```bash
To list all Memcached instances in region us-central1, run:

    $ gcloud memcache instances list --region=us-central1

To list up to five Memcached instances in region us-central1, run:

    $ gcloud memcache instances list --limit=5 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/list)

---
### `gcloud memcache instances reschedule-maintenance`

Reschedule maintenance window for a Memcache instance

Reschedule maintenance window for a Memcache instance.

**Synopsis:**
```
gcloud memcache instances reschedule-maintenance
    (INSTANCE : --region=REGION) --reschedule-type=RESCHEDULE_TYPE
    [--async] [--schedule-time=SCHEDULE_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Cloud Memorystore
for Memcache instance you want to reschedule maintenance window. The
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
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reschedule-type` | one of: immediate Reschedule the maintenance to perform now |  | Reschedule type to use for the reschedule maintenance window. RESCHEDULE_TYPE must be one of: immediate Reschedule the maintenance to perform now. next-available-window Reschedule the maintenance to the next available window. specific-time Reschedule the maintenance to a specific time. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--schedule-time` | SCHEDULE_TIME |  | Time in RFC3339 format, for example: 2012-11-15T16:19:00.094Z |


**Examples:**
```bash
To reschedule maintenance window for an instance with the name
'my-memcache-instance' in region 'us-central-1' with next available window,
run:

    $ gcloud memcache instances reschedule-maintenance \
        my-memcache-instance --region=us-central1 \
        --reschedule-type=next-available-window
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/reschedule-maintenance)

---
### `gcloud memcache instances update`

Update a Memorystore Memcached instance

Update a Memcached instance with one or more of the following actions:
  o Scale up or down the number of nodes in the instance.
  o Stage an update to instance configuration parameters.
  o Update the instance metadata (display name, labels).

Updating parameters cannot be combined with any other update actions in the
same call. All other update actions can be combined in the same call.

**Synopsis:**
```
gcloud memcache instances update (INSTANCE : --region=REGION)
    (--parameters=KEY=VALUE | --display-name=DISPLAY_NAME
      --labels=[KEY=VALUE,...]
      --node-count=NODE_COUNT --maintenance-window-any
      | --maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-duration=MAINTENANCE_WINDOW_DURATION
      --maintenance-window-start-time=MAINTENANCE_WINDOW_START_TIME)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memcached
instance to update. The arguments in this group can be used to specify the
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

  --region=REGION
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parameters` | KEY=VALUE |  | _[Exactly one of these must be specified:]_ User defined parameters to apply to the memcached process on each node. Possible attributes include: listen-backlog The backlog queue limit for the instance. disable-flush-all If enabled, flush_all command will be disabled. Applicable to 1.4.24 and higher. max-item-size Max bytes of the instnace. Must at least be equal to slab_chunk_max (which defaults to 524288 bytes) and less than 134217728 bytes. Additionally it must be a multiple of slab_chunk_max. slab-min-size This is an integer in the range [1, 1024]. slab-growth-factor This is a float in the range [1.01, 100]. protocol This is an enum with acceptable values of ["ascii", "auto"]. disable-cas This is a boolean value. disable-evictions This is a boolean value. max-reqs-per-event This is an integer in the range [1, 1000]. track-sizes This is a boolean value. worker-logbuf-size This is an integer in the range [48, 524288]. watcher-logbuf-size This is an integer in the range [0, 2097151]. lru-crawler This is a boolean value. idle-timeout This is an integer in the range [1,86400]. lru-maintainer This is a boolean value. maxconns-fast This is a boolean value. hash-algorithm This is an enum with accepted values of ["jenkins", "murmur3"]. |
| `--display-name` | DISPLAY_NAME |  | _[Exactly one of these must be specified:]_ An arbitrary and optional user provided name for the instance. |
| `--labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. |
| `--node-count` | NODE_COUNT |  | _[Exactly one of these must be specified:]_ Number of memcache nodes in this instance. Valid values range from 1 to 20. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To scale a Memcached instance named 'my-memcache-instance' in region
'us-central1' to have 3 nodes, run:

    $ gcloud memcache instances update my-memcache-instance \
        --node-count=3 --region=us-central1

To stage an update to the parameters 'protocol' and 'track-sizes' for a
Memcached instance named 'my-memcache-instance' in region 'us-central1',
run:

    $ gcloud memcache instances update my-memcache-instance \
        --parameters="protocol=ascii,track-sizes=true" \
        --region=us-central1

To update a Memcached instance named 'my-memcache-instance' in region
'us-central1' to have the display name "Foo Cache Service" and the labels
'env' and 'service', run:

    $ gcloud memcache instances update my-memcache-instance \
        --display-name="Foo Cache Service" \
        --labels="env=test,service=foo"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/update)

---
### `gcloud memcache instances upgrade`

Upgrade memcache instance to a newer memcached version

Upgrade memcahce instance to a newer memcached version.

**Synopsis:**
```
gcloud memcache instances upgrade (INSTANCE : --region=REGION)
    --memcached-version=MEMCACHED_VERSION [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - Arguments and flags that specify the Memorystore for
Memcached instance you want to upgrade. The arguments in this group can be
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
     The name of the Memcached region of the instance. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument instance on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--memcached-version` | MEMCACHED_VERSION |  | Memcached engine version to which instance should be upgraded to. MEMCACHED_VERSION must be (only one value is supported): 1.6.15 Memcached engine version 1.6.15 |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upgrade memcache version of an instance with the name
'my-memcache-instance' in region 'us-central-1' to MEMCACHE_1_6_15

    $ gcloud memcache instances upgrade my-memcache-instance \
        --region=us-central1 --memcached-version="1.6.15"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/instances/upgrade)

---
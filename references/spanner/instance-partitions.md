# gcloud spanner instance-partitions

manage Spanner instance partitions

### `gcloud spanner instance-partitions create`

Create a Spanner instance partition

Create a Spanner instance partition.

**Synopsis:**
```
gcloud spanner instance-partitions create
    (INSTANCE_PARTITION : --instance=INSTANCE) --config=CONFIG
    --description=DESCRIPTION [--async]
    [--nodes=NODES | --processing-units=PROCESSING_UNITS
      | --autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET
      (--autoscaling-high-priority-cpu-target=AUTOSCALING_HIGH_PRIORITY_CPU_TARGET --autoscaling-total-cpu-target=AUTOSCALING_TOTAL_CPU_TARGET) (--autoscaling-max-nodes=AUTOSCALING_MAX_NODES --autoscaling-min-nodes=AUTOSCALING_MIN_NODES | --autoscaling-max-processing-units=AUTOSCALING_MAX_PROCESSING_UNITS --autoscaling-min-processing-units=AUTOSCALING_MIN_PROCESSING_UNITS)]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance partition resource - The Spanner instance partition to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance_partition on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE_PARTITION
     ID of the instance partition or fully qualified identifier for the
     instance partition.

     To set the instance partition attribute:
     + provide the argument instance_partition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the instance partition.

     To set the instance attribute:
     + provide the argument instance_partition on the command line with
       a fully specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | Instance configuration defines the geographic placement and replication used by the instance partition. Available configurations can be found by running "gcloud spanner instance-configs list" |
| `--description` | DESCRIPTION |  | Description of the instance partition. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a Spanner instance partition, run:

    $ gcloud spanner instance-partitions create \
        my-instance-partition-id --instance=my-instance-id \
        --config=regional-us-east1 \
        --description=my-instance-display-name --nodes=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-partitions/create)

---
### `gcloud spanner instance-partitions delete`

Delete a Spanner instance partition. You can't delete the default instance partition using this command

Delete a Spanner instance partition. You can't delete the default instance
partition using this command.

**Synopsis:**
```
gcloud spanner instance-partitions delete
    (INSTANCE_PARTITION : --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance partition resource - The Spanner instance partition to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance_partition on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE_PARTITION
     ID of the instance partition or fully qualified identifier for the
     instance partition.

     To set the instance partition attribute:
     + provide the argument instance_partition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the instance partition.

     To set the instance attribute:
     + provide the argument instance_partition on the command line with
       a fully specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To delete a Spanner instance partition, run:

    $ gcloud spanner instance-partitions delete \
        my-instance-partition-id --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-partitions/delete)

---
### `gcloud spanner instance-partitions describe`

Describe a Spanner instance partition

Describe a Spanner instance partition.

**Synopsis:**
```
gcloud spanner instance-partitions describe
    (INSTANCE_PARTITION : --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance partition resource - The Spanner instance partition to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance_partition on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE_PARTITION
     ID of the instance partition or fully qualified identifier for the
     instance partition.

     To set the instance partition attribute:
     + provide the argument instance_partition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the instance partition.

     To set the instance attribute:
     + provide the argument instance_partition on the command line with
       a fully specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To describe a Spanner instance partition, run:

    $ gcloud spanner instance-partitions describe \
        my-instance-partition-id --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-partitions/describe)

---
### `gcloud spanner instance-partitions list`

List the Spanner instance partitions contained within the given instance

List the Spanner instance partitions contained within the given instance.

**Synopsis:**
```
gcloud spanner instance-partitions list [--instance=INSTANCE]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[* set the property core/project.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line; + set the property spanner/instance. |


**Examples:**
```bash
To list all Spanner instances partitions in an instance, run:

    $ gcloud spanner instance-partitions list --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-partitions/list)

---
### `gcloud spanner instance-partitions update`

Update a Spanner instance partition. You can't update the default instance partition using this command

Update a Spanner instance partition. You can't update the default instance
partition using this command.

**Synopsis:**
```
gcloud spanner instance-partitions update
    (INSTANCE_PARTITION : --instance=INSTANCE) [--async]
    [--description=DESCRIPTION]
    [--nodes=NODES | --processing-units=PROCESSING_UNITS
      | --autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET
      --autoscaling-high-priority-cpu-target=AUTOSCALING_HIGH_PRIORITY_CPU_TARGET --autoscaling-total-cpu-target=AUTOSCALING_TOTAL_CPU_TARGET --autoscaling-max-nodes=AUTOSCALING_MAX_NODES --autoscaling-min-nodes=AUTOSCALING_MIN_NODES | --autoscaling-max-processing-units=AUTOSCALING_MAX_PROCESSING_UNITS --autoscaling-min-processing-units=AUTOSCALING_MIN_PROCESSING_UNITS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance partition resource - The Spanner instance partition to update.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance_partition on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE_PARTITION
     ID of the instance partition or fully qualified identifier for the
     instance partition.

     To set the instance partition attribute:
     + provide the argument instance_partition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the instance partition.

     To set the instance attribute:
     + provide the argument instance_partition on the command line with
       a fully specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the instance partition. |


**Examples:**
```bash
To update the display name of a Spanner instance partition, run:

    $ gcloud spanner instance-partitions update \
        my-instance-partition-id --instance=my-instance-id \
        --description=my-new-display-name

To update the node count of a Spanner instance partition, run:

    $ gcloud spanner instance-partitions update \
        my-instance-partition-id --instance=my-instance-id --nodes=1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-partitions/update)

---
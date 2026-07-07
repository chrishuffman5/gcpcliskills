# gcloud bigtable clusters

manage Cloud Bigtable clusters

### `gcloud bigtable clusters create`

Create a bigtable cluster

Create a bigtable cluster.

**Synopsis:**
```
gcloud bigtable clusters create (CLUSTER : --instance=INSTANCE) --zone=ZONE
    [--async]
    [--node-scaling-factor=NODE_SCALING_FACTOR;
      default="node-scaling-factor-1x"]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--num-nodes=NUM_NODES; default=3
      | [--autoscaling-cpu-target=AUTOSCALING_CPU_TARGET
      --autoscaling-max-nodes=AUTOSCALING_MAX_NODES
      --autoscaling-min-nodes=AUTOSCALING_MIN_NODES
      : --autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The cluster to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the cluster.

     To set the instance attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | ID of the zone where the cluster is located. Supported zones are listed at https://cloud.google.com/bigtable/docs/locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--node-scaling-factor` | one of: node-scaling-factor-1x, node-scaling-factor-2x | node-scaling-factor-1x | Node scaling factor for the cluster. NODE_SCALING_FACTOR must be one of: node-scaling-factor-1x, node-scaling-factor-2x. |


**Examples:**
```bash
To add a cluster in zone us-east1-c to the instance with id my-instance-id,
run:

    $ gcloud bigtable clusters create my-cluster-id \
        --instance=my-instance-id --zone=us-east1-c

To add a cluster with 10 nodes, run:

    $ gcloud bigtable clusters create my-cluster-id \
        --instance=my-instance-id --zone=us-east1-c --num-nodes=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters/create)

---
### `gcloud bigtable clusters delete`

Delete a bigtable cluster

Delete a bigtable cluster.

**Synopsis:**
```
gcloud bigtable clusters delete (CLUSTER : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The cluster to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the cluster.

     To set the instance attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To delete a cluster, run:

    $ gcloud bigtable clusters delete my-cluster-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters/delete)

---
### `gcloud bigtable clusters describe`

Describe an existing Bigtable cluster

Describe an existing Bigtable cluster.

**Synopsis:**
```
gcloud bigtable clusters describe (CLUSTER : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The cluster to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the cluster.

     To set the instance attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To view a cluster's description, run:

    $ gcloud bigtable clusters describe my-cluster-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters/describe)

---
### `gcloud bigtable clusters list`

List existing Bigtable clusters

List existing Bigtable clusters.

**Synopsis:**
```
gcloud bigtable clusters list [--instances=[INSTANCES,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | [INSTANCES,...] |  | _[* set the property core/project.]_ IDs of the instances or fully qualified identifiers for the instances. To set the instance attribute: + provide the argument --instances on the command line. |


**Examples:**
```bash
To list all clusters in an instance, run:

    $ gcloud bigtable clusters list --instances=my-instance-id

To list all clusters in multiple instances, run:

    $ gcloud bigtable clusters list \
        --instances=my-instance-id,my-other-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters/list)

---
### `gcloud bigtable clusters update`

Update a Bigtable cluster's number of nodes

Update a Bigtable cluster's number of nodes.

**Synopsis:**
```
gcloud bigtable clusters update (CLUSTER : --instance=INSTANCE)
    (--autoscaling-cpu-target=AUTOSCALING_CPU_TARGET
      --autoscaling-max-nodes=AUTOSCALING_MAX_NODES
      --autoscaling-min-nodes=AUTOSCALING_MIN_NODES
      --autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET
      | [--num-nodes=NUM_NODES : --disable-autoscaling]) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The cluster to update. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the cluster.

     To set the instance attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--autoscaling-cpu-target` | AUTOSCALING_CPU_TARGET |  | _[Autoscaling]_ The target CPU utilization percentage for autoscaling. Accepted values are from 10 to 80. |
| `--autoscaling-max-nodes` | AUTOSCALING_MAX_NODES |  | _[Autoscaling]_ The maximum number of nodes for autoscaling. |
| `--autoscaling-min-nodes` | AUTOSCALING_MIN_NODES |  | _[Autoscaling]_ The minimum number of nodes for autoscaling. |
| `--autoscaling-storage-target` | AUTOSCALING_STORAGE_TARGET |  | _[Autoscaling]_ The target storage utilization gibibytes per node for autoscaling. Accepted values are from 2560 to 5120 for SSD clusters and 8192 to 16384 for HDD clusters. |
| `--num-nodes` | NUM_NODES |  | _[Manual Scaling]_ Number of nodes to serve. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--disable-autoscaling` |  |  | _[Manual Scaling]_ Set this flag and --num-nodes to disable autoscaling. If autoscaling is currently not enabled, setting this flag does nothing. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update a cluster to 10 nodes, run:

    $ gcloud bigtable clusters update my-cluster-id \
        --instance=my-instance-id --num-nodes=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/clusters/update)

---
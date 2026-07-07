# gcloud dataproc node-groups

manage Dataproc node groups

### `gcloud dataproc node-groups describe`

Describe the node group

Describe the node group.

**Synopsis:**
```
gcloud dataproc node-groups describe
    (NODE_GROUP : --cluster=CLUSTER --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node group resource - ID of the node group to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument node_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_GROUP
     ID of the node_group or fully qualified identifier for the
     node_group.

     To set the node_group attribute:
     + provide the argument node_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The Cluster name.

     To set the cluster attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --region=REGION
     Dataproc region for the node_group. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To describe a node group, run:

    $ gcloud dataproc node-groups describe my-node-group-id \
        --region=us-central1 --cluster=my-cluster-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/node-groups/describe)

---
### `gcloud dataproc node-groups resize`

Resize the number of nodes in the node group

Resize the number of nodes in the node group.

**Synopsis:**
```
gcloud dataproc node-groups resize
    (NODE_GROUP : --cluster=CLUSTER --region=REGION) --size=SIZE
    [--graceful-decommission-timeout=GRACEFUL_DECOMMISSION_TIMEOUT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node group resource - ID of the node group to resize. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument node_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_GROUP
     ID of the node_group or fully qualified identifier for the
     node_group.

     To set the node_group attribute:
     + provide the argument node_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The Cluster name.

     To set the cluster attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --region=REGION
     Dataproc region for the node_group. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument node_group on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--size` | SIZE |  | New size for a node group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--graceful-decommission-timeout` | GRACEFUL_DECOMMISSION_TIMEOUT |  | Graceful decommission timeout for a node group scale-down resize. |


**Examples:**
```bash
To resize a node group, run:

    $ gcloud dataproc node-groups resize my-node-group-id \
        --region=us-central1 --cluster=my-cluster-name --size=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/node-groups/resize)

---
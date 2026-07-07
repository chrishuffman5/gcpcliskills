# gcloud workstations clusters

manage Cloud Workstations cluster resources

### `gcloud workstations clusters create`

Create a workstation cluster

Create a workstation cluster.

**Synopsis:**
```
gcloud workstations clusters create (CLUSTER : --region=REGION) [--async]
    [--domain=DOMAIN] [--enable-private-endpoint]
    [--labels=[KEY=VALUE,...]] [--network=NETWORK]
    [--subnetwork=SUBNETWORK] [--tags=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Arguments and flags that specify the cluster to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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

  --region=REGION
     The name of the region of the cluster.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--domain` | DOMAIN |  | Domain used by Workstations for HTTP ingress. |
| `--enable-private-endpoint` |  |  | Default is false. If specified, the cluster will be assigned an internal IP address to the Cluster Gateway. This isolates the cluster's workstations from public networks, but requires additional configuration. Learn more: https://cloud.google.com/workstations/docs. |
| `--labels` | [KEY=VALUE,...] |  | Labels that are applied to the cluster and propagated to the underlying Compute Engine resources. |
| `--network` | NETWORK |  | Fully specified network path for instances created in this cluster. |
| `--subnetwork` | SUBNETWORK |  | Fully specified subnetwork path for instances created in this cluster. |
| `--tags` | [KEY=VALUE,...] |  | Resource manager tags to be bound to this cluster. For example: "123/environment=production" "123/costCenter=marketing" |


**Examples:**
```bash
To create a public cluster my-cluster in region us-central1, run:

    $ gcloud workstations clusters create my-cluster --region=us-central1

To create a private cluster 'my-private-cluster' associated with network
'my-network' and subnetwork 'my-subnetwork'. run:

    $ gcloud workstations clusters create my-private-cluster \
        --region=us-central1 --enable-private-endpoint \
        --network='my-network' --subnetwork='my-subnetwork'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/clusters/create)

---
### `gcloud workstations clusters delete`

Delete a workstation cluster

Delete a workstation cluster.

**Synopsis:**
```
gcloud workstations clusters delete (CLUSTER : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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

  --region=REGION
     The name of the region of the cluster.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a cluster, run:

    $ gcloud workstations clusters delete WORKSTATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/clusters/delete)

---
### `gcloud workstations clusters describe`

Describe a cluster

Describe a cluster.

**Synopsis:**
```
gcloud workstations clusters describe (CLUSTER : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The name of the cluster to display. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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

  --region=REGION
     The name of the region of the cluster.

     To set the region attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property workstations/region.
```

**Examples:**
```bash
To describe a cluster, run:

    $ gcloud workstations clusters describe CLUSTER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/clusters/describe)

---
### `gcloud workstations clusters list`

List workstation clusters

List all workstation clusters under the specified project and region.

**Synopsis:**
```
gcloud workstations clusters list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property workstations/region; + default is all regions . |


**Examples:**
```bash
To list workstation clusters, run:

    $ gcloud workstations clusters list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workstations/clusters/list)

---
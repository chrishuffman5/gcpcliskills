# gcloud vmware private-clouds

manage private clouds in Google Cloud VMware Engine

### `gcloud vmware private-clouds create`

Create a VMware Engine private cloud

Create a VMware Engine private cloud. Private cloud creation is considered
finished when the private cloud is in READY state. Check the progress of a
private cloud using gcloud vmware private-clouds list.

**Synopsis:**
```
gcloud vmware private-clouds create (PRIVATE_CLOUD : --location=LOCATION)
    --cluster=CLUSTER --management-range=MANAGEMENT_RANGE
    --node-type-config=[count=COUNT],
      [custom-core-count=CUSTOM-CORE-COUNT],[type=TYPE]
    --vmware-engine-network=VMWARE_ENGINE_NETWORK [--async]
    [--description=DESCRIPTION] [--preferred-zone=PREFERRED_ZONE]
    [--secondary-zone=SECONDARY_ZONE] [--type=TYPE; default="STANDARD"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private cloud resource - private_cloud. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_cloud on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CLOUD
     ID of the private cloud or fully qualified identifier for the private
     cloud.

     To set the private-cloud attribute:
     + provide the argument private_cloud on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument private_cloud on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. |
| `--management-range` | MANAGEMENT_RANGE |  | _[This must be specified.]_ IP address range in the private cloud to use for management appliances, in CIDR format. Use an IP address range that meets the VMware Engine networking requirements (https://cloud.google.com/vmware-engine/docs/quickstart-networking-requirements). |
| `--node-type-config` | [count=COUNT],[custom-core-count=CUSTOM-CORE-COUNT],[type=TYPE] |  | _[This must be specified.]_ Information about the type and number of nodes associated with the cluster. type (required): canonical identifier of the node type. count (required): number of nodes of this type in the cluster. custom-core-count (optional): customized number of cores available to each node of the type. To get a list of valid values for your node type, run the gcloud vmware node-types describe command and reference the availableCustomCoreCounts field in the output. |
| `--vmware-engine-network` | VMWARE_ENGINE_NETWORK |  | _[This must be specified.]_ Resource ID of the VMware Engine network attached to the private cloud. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the private cloud. |
| `--preferred-zone` | PREFERRED_ZONE |  | Zone that will remain operational when connection between the two zones is lost. Specify the resource name of a zone that belongs to the region of the private cloud. |
| `--secondary-zone` | SECONDARY_ZONE |  | Additional zone for a higher level of availability and load balancing. Specify the resource name of a zone that belongs to the region of the private cloud. |
| `--type` | one of: STANDARD Standard private is a zonal resource, with 3 or more nodes nodes | STANDARD | Type of the private cloud. TYPE must be one of: STANDARD Standard private is a zonal resource, with 3 or more nodes nodes. Default type. STRETCHED Stretched private cloud is a regional resource with redundancy, with a minimum of 6 nodes, nodes count has to be even. TIME_LIMITED Time limited private cloud is a zonal resource, can have only 1 node and has limited life span. Will be deleted after defined period of time, can be converted into standard private cloud by expanding it up to 3 or more nodes. |


**Examples:**
```bash
To create a private cloud in the us-west2-a zone using standard-72 nodes
that connects to the my-network VMware Engine network, run:

    $ gcloud vmware private-clouds create my-private-cloud \
        --location=us-west2-a --project=my-project \
        --cluster=my-management-cluster \
        --node-type-config=type=standard-72,count=3 \
        --management-range=192.168.0.0/24 \
        --vmware-engine-network=my-network

Or:

    $ gcloud vmware private-clouds create my-private-cloud \
        --cluster=my-management-cluster \
        --node-type-config=type=standard-72,count=3 \
        --management-range=192.168.0.0/24 \
        --vmware-engine-network=my-network

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.

To create a stretched private cloud in the us-west2 region using us-west2-a
zone as preferred and us-west2-b zone as secondary

    $ gcloud vmware private-clouds create my-private-cloud \
        --project=sample-project --location=us-west2 \
        --cluster=my-management-cluster \
        --node-type-config=type=standard-72,count=6 \
        --management-range=192.168.0.0/24 \
        --vmware-engine-network=my-network --type=STRETCHED \
        --preferred-zone=us-west2-a --secondary-zone=us-west2-b

The project is taken from gcloud properties core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/create)

---
### `gcloud vmware private-clouds delete`

Delete a Google Cloud VMware Engine private cloud

Marks a VMware Engine private cloud for deletion. The resource is deleted 3
hours after being marked for deletion. This process can be reversed by
using gcloud vmware private-clouds undelete.

**Synopsis:**
```
gcloud vmware private-clouds delete (PRIVATE_CLOUD : --location=LOCATION)
    [--async] [--delay-hours=DELAY_HOURS; default=3] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private cloud resource - private_cloud. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_cloud on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CLOUD
     ID of the private cloud or fully qualified identifier for the private
     cloud.

     To set the private-cloud attribute:
     + provide the argument private_cloud on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument private_cloud on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--delay-hours` | one of: 0, 1, 2, 3, 4, 5, 6, 7, 8 | 3 | Number of hours to wait before deleting the private cloud. Specifying a value of 0 for this field begins the deletion process immediately. DELAY_HOURS must be one of: 0, 1, 2, 3, 4, 5, 6, 7, 8. |


**Examples:**
```bash
To mark a private cloud called my-private-cloud for deletion, run:

    $ gcloud vmware private-clouds delete my-private-cloud \
        --location=us-west2-a --project=my-project

Or:

    $ gcloud vmware private-clouds delete my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/delete)

---
### `gcloud vmware private-clouds delete-now`

Permanent deletion of a Google Cloud VMware Engine private cloud currently in soft-deleted state

Permanently delete a private cloud that is currently in soft deletion.

**Synopsis:**
```
gcloud vmware private-clouds delete-now
    (PRIVATE_CLOUD : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private cloud resource - private_cloud. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_cloud on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CLOUD
     ID of the private cloud or fully qualified identifier for the private
     cloud.

     To set the private-cloud attribute:
     + provide the argument private_cloud on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument private_cloud on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To permanently delete a private cloud called my-private-cloud currently in
soft-deleted state, run:

    $ gcloud vmware private-clouds delete-now my-private-cloud \
        --location=us-west2-a --project=my-project

Or:

    $ gcloud vmware private-clouds delete-now my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/delete-now)

---
### `gcloud vmware private-clouds describe`

Describe a Google Cloud VMware Engine private cloud

Describe a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds describe (PRIVATE_CLOUD : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private cloud resource - private_cloud. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_cloud on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CLOUD
     ID of the private cloud or fully qualified identifier for the private
     cloud.

     To set the private-cloud attribute:
     + provide the argument private_cloud on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument private_cloud on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To get a description of a private cloud called my-private-cloud in project
my-project and zone us-west2-a, run:

    $ gcloud vmware private-clouds describe my-private-cloud \
        --location=us-west2-a --project=my-project

Or:

    $ gcloud vmware private-clouds describe my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/describe)

---
### `gcloud vmware private-clouds list`

List Google Cloud VMware Engine private clouds

List VMware Engine private clouds.

**Synopsis:**
```
gcloud vmware private-clouds list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list VMware Engine operations in the location us-west2-a, run:

    $ gcloud vmware private-clouds list --location=us-west2-a

Or:

    $ gcloud vmware private-clouds list

In the second example, the location is taken from gcloud properties
compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/list)

---
### `gcloud vmware private-clouds undelete`

Cancel deletion of a Google Cloud VMware Engine private cloud

Unmark a VMware Engine private cloud that was previously marked for
deletion by gcloud vmware private-clouds delete.

**Synopsis:**
```
gcloud vmware private-clouds undelete (PRIVATE_CLOUD : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private cloud resource - private_cloud. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_cloud on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CLOUD
     ID of the private cloud or fully qualified identifier for the private
     cloud.

     To set the private-cloud attribute:
     + provide the argument private_cloud on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument private_cloud on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To unmark a private cloud called my-private-cloud for deletion, run:

    $ gcloud vmware private-clouds undelete my-private-cloud \
        --location=us-west2-a --project=my-project

Or:

    $ gcloud vmware private-clouds undelete my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/undelete)

---
### `gcloud vmware private-clouds update`

Update a Google Cloud VMware Engine private cloud

Update a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds update (PRIVATE_CLOUD : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private cloud resource - private_cloud. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_cloud on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CLOUD
     ID of the private cloud or fully qualified identifier for the private
     cloud.

     To set the private-cloud attribute:
     + provide the argument private_cloud on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument private_cloud on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the private cloud |


**Examples:**
```bash
To update a private cloud named my-private-cloud by changing its
description to Example description run:

    $ gcloud vmware private-clouds update my-private-cloud \
        --location=us-west2-a --project=my-project \
        --description='Example description'

Or:

    $ gcloud vmware private-clouds update my-private-cloud \
        --description='Example description'

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/update)

---

## `gcloud vmware private-clouds clusters` — manage clusters in Google Cloud VMware Engine
### `gcloud vmware private-clouds clusters create`

Create a Google Cloud VMware Engine cluster

Create a cluster in a VMware Engine private cloud. Successful creation of a
cluster results in a cluster in READY state. Check the progress of a
cluster using gcloud vmware private-clouds clusters list.

**Synopsis:**
```
gcloud vmware private-clouds clusters create
    (CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --node-type-config=[count=COUNT],
      [custom-core-count=CUSTOM-CORE-COUNT],[type=TYPE] [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-type-config` | [count=COUNT],[custom-core-count=CUSTOM-CORE-COUNT],[type=TYPE] |  | Information about the type and number of nodes associated with the cluster. type (required): canonical identifier of the node type. count (required): number of nodes of this type in the cluster. custom-core-count (optional): customized number of cores available to each node of the type. To get a list of valid values for your node type, run the gcloud vmware node-types describe command and reference the availableCustomCoreCounts field in the output. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To create a cluster called my-cluster in private cloud my-private-cloud,
with 3 initial standard-72 nodes in zone us-west2-a, run:

    $ gcloud vmware private-clouds clusters create my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --node-type-config=type=standard-72,count=3

    Or:

    $ gcloud vmware private-clouds clusters create my-cluster \
        --private-cloud=my-private-cloud \
        --node-type-config=type=standard-72,count=3

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/create)

---
### `gcloud vmware private-clouds clusters delete`

Delete a Google Cloud VMware Engine cluster

Delete a cluster in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds clusters delete
    (CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a cluster called my-cluster in private cloud my-private-cloud and
zone us-west2-a, run:

    $ gcloud vmware private-clouds clusters delete my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds clusters delete my-cluster \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/delete)

---
### `gcloud vmware private-clouds clusters describe`

Describe a Google Cloud VMware Engine cluster

Display data associated with a VMware Engine cluster, such as its node
count, node type, and status.

**Synopsis:**
```
gcloud vmware private-clouds clusters describe
    (CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To describe a cluster called my-cluster in private cloud my-private-cloud
and zone us-west2-a, run:

    $ gcloud vmware private-clouds clusters describe my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds clusters describe my-cluster \
        --private-cloud=my-private-cloud

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/describe)

---
### `gcloud vmware private-clouds clusters list`

List clusters in a Google Cloud VMware Engine private cloud

List clusters in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds clusters list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list clusters in the my-private-cloud private cloud run:

    $ gcloud vmware private-clouds clusters list --location=us-west2-a \
        --project=my-project --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds clusters list \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/list)

---
### `gcloud vmware private-clouds clusters mount-datastore`

Mount a datastore to a Google Cloud VMware Engine cluster

Mount a datastore to a cluster in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds clusters mount-datastore
    (CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --datastore=DATASTORE
    (--datastore-network=PATH_TO_FILE
      | [--subnet=SUBNET : --connection-count=CONNECTION_COUNT --mtu=MTU])
    [--access-mode=ACCESS_MODE] [--async] [--ignore-colocation]
    [--nfs-version=NFS_VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--datastore` | DATASTORE |  | The datastore resource name to mount. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-mode` | one of: READ_WRITE, READ_ONLY |  | Access mode for the datastore. ACCESS_MODE must be one of: READ_WRITE, READ_ONLY. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--ignore-colocation` |  |  | If set, ignore colocation checks. |
| `--nfs-version` | one of: NFS_V3, NFS_V4 |  | NFS version for the datastore. NFS_VERSION must be one of: NFS_V3, NFS_V4. |


**Examples:**
```bash
To mount a datastore my-datastore to cluster my-cluster in private cloud
my-private-cloud in zone us-west2-a, providing subnet, run:

    $ gcloud vmware private-clouds clusters mount-datastore my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --datastore=projects/my-project/locations/us-west2-a/\
    datastores/my-datastore --subnet=my-subnet

    Or:

    $ gcloud vmware private-clouds clusters mount-datastore my-cluster \
        --private-cloud=my-private-cloud \
        --datastore=projects/my-project/locations/us-west2-a/\
    datastores/my-datastore --subnet=my-subnet

To mount a datastore my-datastore to cluster my-cluster in private cloud
my-private-cloud in zone us-west2-a, providing a json file for datastore
network, run:

    $ gcloud vmware private-clouds clusters mount-datastore my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --datastore=projects/my-project/locations/us-west2-a/\
    datastores/my-datastore --datastore-network=network-config.json

    Where `network-config.json` contains:
    {
      "subnet": "my-subnet",
      "mtu": 1500,
      "connection-count": 4
    }

    In the examples without location and project, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/mount-datastore)

---
### `gcloud vmware private-clouds clusters unmount-datastore`

Unmount a datastore from a Google Cloud VMware Engine cluster

Unmount a datastore from a cluster in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds clusters unmount-datastore
    (CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --datastore=DATASTORE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--datastore` | DATASTORE |  | The datastore resource name to unmount. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To unmount a datastore my-datastore from cluster my-cluster in private
cloud my-private-cloud in zone us-west2-a, run:

    $ gcloud vmware private-clouds clusters unmount-datastore \
        my-cluster --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --datastore=projects/my-project/locations/us-west2-a/\
    datastores/my-datastore

    Or:

    $ gcloud vmware private-clouds clusters unmount-datastore \
        my-cluster --private-cloud=my-private-cloud \
        --datastore=projects/my-project/locations/us-west2-a/\
    datastores/my-datastore

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/unmount-datastore)

---
### `gcloud vmware private-clouds clusters update`

Update a Google Cloud VMware Engine cluster

Adjust the number of nodes in the VMware Engine cluster. Successful
addition or removal of a node results in a cluster in READY state. Check
the progress of a cluster using gcloud vmware private-clouds clusters list.

**Synopsis:**
```
gcloud vmware private-clouds clusters update
    (CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD) [--async]
    [--node-type-config=[[count=COUNT],[type=TYPE],...]]
    [--remove-autoscaling-policy=NAME] [--remove-nodes-config=TYPE]
    [--update-nodes-config=[count=COUNT],[type=TYPE]]
    [--autoscaling-settings-from-file=AUTOSCALING_SETTINGS_FROM_FILE
      | --autoscaling-cool-down-period=AUTOSCALING_COOL_DOWN_PERIOD
      --autoscaling-max-cluster-node-count=AUTOSCALING_MAX_CLUSTER_NODE_COUNT --autoscaling-min-cluster-node-count=AUTOSCALING_MIN_CLUSTER_NODE_COUNT --update-autoscaling-policy=[consumed-memory-thresholds-scale-in=CONSUMED-MEMORY-THRESHOLDS-SCALE-IN],
      [consumed-memory-thresholds-scale-out=CONSUMED-MEMORY-THRESHOLDS-SCALE-OUT],
      [cpu-thresholds-scale-in=CPU-THRESHOLDS-SCALE-IN],
      [cpu-thresholds-scale-out=CPU-THRESHOLDS-SCALE-OUT],
      [granted-memory-thresholds-scale-in=GRANTED-MEMORY-THRESHOLDS-SCALE-IN],
      [granted-memory-thresholds-scale-out=GRANTED-MEMORY-THRESHOLDS-SCALE-OUT],
      [max-node-count=MAX-NODE-COUNT],[min-node-count=MIN-NODE-COUNT],
      [name=NAME],[node-type-id=NODE-TYPE-ID],
      [scale-out-size=SCALE-OUT-SIZE],
      [storage-thresholds-scale-in=STORAGE-THRESHOLDS-SCALE-IN],
      [storage-thresholds-scale-out=STORAGE-THRESHOLDS-SCALE-OUT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--node-type-config` | [[count=COUNT],[type=TYPE],...] |  | (DEPRECATED) Information about the type and number of nodes associated with the cluster. type (required): canonical identifier of the node type. count (required): number of nodes of this type in the cluster. custom_core_count: can be passed, but the value will be ignored. Updating custom core count is not supported. The --node-type-config option is deprecated; please use --update-nodes-config and --remove-nodes-config instead. |
| `--remove-autoscaling-policy` | NAME |  | Names of autoscaling policies that should be removed from the cluster |
| `--remove-nodes-config` | TYPE |  | Type of node that should be removed from the cluster |
| `--update-nodes-config` | [count=COUNT],[type=TYPE] |  | Information about the type and number of nodes associated with the cluster. type (required): canonical identifier of the node type. count (required): number of nodes of this type in the cluster. |


**Examples:**
```bash
To resize a cluster called my-cluster in private cloud my-private-cloud and
zone us-west2-a to have 3 nodes of type standard-72, run:

    $ gcloud vmware private-clouds clusters update my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --update-nodes-config=type=standard-72,count=3

    Or:

    $ gcloud vmware private-clouds clusters update my-cluster \
        --private-cloud=my-private-cloud \
        --update-nodes-config=type=standard-72,count=3

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.

To enable autoscale in a cluster called my-cluster in private cloud
my-private-cloud and zone us-west2-a, run:

    $ gcloud vmware private-clouds clusters update my-cluster \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --autoscaling-min-cluster-node-count=3 \
        --autoscaling-max-cluster-node-count=5 \
        --update-autoscaling-policy=name=custom-policy,\
    node-type-id=standard-72,scale-out-size=1,\
    storage-thresholds-scale-in=10,storage-thresholds-scale-out=80
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/update)

---

## `gcloud vmware private-clouds clusters nodes` — manage nodes in Google Cloud VMware Engine
### `gcloud vmware private-clouds clusters nodes describe`

Describe a Google Cloud VMware Engine node

Display data associated with a VMware Engine node, such as its name, state,
node type, ip, fqdn.

**Synopsis:**
```
gcloud vmware private-clouds clusters nodes describe
    (NODE : --cluster=CLUSTER
      --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node resource - node. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE
     ID of the node or fully qualified identifier for the node.

     To set the node attribute:
     + provide the argument node on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     Resource ID of the cluster

     To set the cluster attribute:
     + provide the argument node on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument node on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument node on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To describe a node called my-node in private cloud my-private-cloud cluster
my-cluster and zone us-west2-a, run:

    $ gcloud vmware private-clouds clusters nodes describe my-node \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud --cluster=my-cluster

    Or:

    $ gcloud vmware private-clouds clusters nodes describe my-node \
        --private-cloud=my-private-cloud --cluster=my-cluster

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/nodes/describe)

---
### `gcloud vmware private-clouds clusters nodes list`

List nodes in a Google Cloud VMware Engine private cloud's cluster

List nodes in a VMware Engine private cloud's cluster.

**Synopsis:**
```
gcloud vmware private-clouds clusters nodes list
    (--cluster=CLUSTER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ VMware Engine private cloud. To set the private-cloud attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --private-cloud on the command line. |


**Examples:**
```bash
To list nodes in the my-private-cloud private cloud and my-cluster cluster:

    $ gcloud vmware private-clouds clusters nodes list \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud --cluster=my-cluster

    Or:

    $ gcloud vmware private-clouds clusters nodes list \
        --private-cloud=my-private-cloud --cluster=my-cluster

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/clusters/nodes/list)

---

## `gcloud vmware private-clouds dns-forwarding` — manage dns-forwarding in Google Cloud VMware Engine
### `gcloud vmware private-clouds dns-forwarding describe`

Describe a Google Cloud VMware Engine dns-forwarding

Display data associated with a VMware Engine DNS forwarding, such as the
domains and their respective name servers.

**Synopsis:**
```
gcloud vmware private-clouds dns-forwarding describe
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To describe a DNS forwarding config in private cloud my-private-cloud and
zone us-west2-a, run:

    $ gcloud vmware private-clouds dns-forwarding describe \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds dns-forwarding describe \
        --private-cloud=my-private-cloud

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/dns-forwarding/describe)

---
### `gcloud vmware private-clouds dns-forwarding update`

Update a Google Cloud VMware Engine dns-forwarding

Update DNS forwarding.

**Synopsis:**
```
gcloud vmware private-clouds dns-forwarding update
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION) [--async]
    [--rule=[domain=DOMAIN,
      name-servers="NAME_SERVER1;NAME_SERVER2[;NAME_SERVER3]",...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--rule` | [domain=DOMAIN,name-servers="NAME_SERVER1;NAME_SERVER2[;NAME_SERVER3]",...] |  | Domain name and the name servers used to resolve DNS requests for this domain. |


**Examples:**
```bash
To update a DNS forwarding config in private cloud my-private-cloud and
zone us-west2-a to forward DNS requests for domain activedirectory.my.corp
to name servers 192.168.20.15 and 192.168.20.16 and for domain
proxy.my.corp to nameservers 192.168.30.15 and 192.168.30.16, run:

    $ gcloud vmware private-clouds dns-forwarding update \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud \
        --rule=domain=activedirectory.my.corp,\
    name-servers=192.168.20.15;192.168.20.16 \
        --rule=domain=proxy.my.corp,name-servers=192.168.30.15;\
    192.168.30.16

    Or:

    $ gcloud vmware private-clouds dns-forwarding update \
        --private-cloud=my-private-cloud \
        --rule=domain=activedirectory.my.corp,\
    name-servers=192.168.20.15;192.168.20.16 \
        --rule=domain=proxy.my.corp,name-servers=192.168.30.15;\
    192.168.30.16

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/dns-forwarding/update)

---

## `gcloud vmware private-clouds external-addresses` — manage external IP addresses in Google Cloud VMware Engine
### `gcloud vmware private-clouds external-addresses create`

Create an external IP address

Create an external IP address that represents an allocated external IP
address and its corresponding internal IP address in the private cloud.

**Synopsis:**
```
gcloud vmware private-clouds external-addresses create
    (EXTERNAL_ADDRESS : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --internal-ip=INTERNAL_IP [--async] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
External address resource - external_address. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument external_address on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ADDRESS
     ID of the external address or fully qualified identifier for the
     external address.

     To set the external-address attribute:
     + provide the argument external_address on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--internal-ip` | INTERNAL_IP |  | internal ip address to which external address will be linked |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the external address |


**Examples:**
```bash
To create an external IP address called myip that corresponds to the
internal IP address 165.87.54.14 that belongs to the private cloud
my-private-cloud in project my-project and location us-east2-b, run:

    $ gcloud vmware private-clouds external-addresses create myip \
        --project=my-project --private-cloud=my-private-cloud \
        --location=us-east2-b --internal-ip=165.87.54.14 \
        --description="A short description for the new external address"

Or:

    $ gcloud vmware private-clouds external-addresses create myip \
        --private-cloud=my-private-cloud --internal-ip=165.87.54.14 \
        --description="A short description for the new external address"

In the second example, the project and region are taken from gcloud
properties core/project and vmware/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/external-addresses/create)

---
### `gcloud vmware private-clouds external-addresses delete`

Delete external IP address from a VMware Engine private cloud

Delete external IP address from a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds external-addresses delete
    (EXTERNAL_ADDRESS : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
External address resource - external_address. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument external_address on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ADDRESS
     ID of the external address or fully qualified identifier for the
     external address.

     To set the external-address attribute:
     + provide the argument external_address on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete an external IP address called first-ip in private cloud
my-privatecloud and location us-east2-b, run:

    $ gcloud vmware private-clouds external-addresses delete first-ip \
        --private-cloud=my-privatecloud --location=us-east2-b \
        --project=my-project

Or:

    $ gcloud vmware private-clouds external-addresses delete first-ip \
        --private-cloud=my-privatecloud

In the second example, the project and region are taken from gcloud
properties core/project and vmware/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/external-addresses/delete)

---
### `gcloud vmware private-clouds external-addresses describe`

Describe an external IP address in a VMware Engine private cloud

Describe an external IP address in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds external-addresses describe
    (EXTERNAL_ADDRESS : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
External address resource - external_address. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument external_address on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ADDRESS
     ID of the external address or fully qualified identifier for the
     external address.

     To set the external-address attribute:
     + provide the argument external_address on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To get a description of an address called first-ip in the my-privatecloud
private cloud in the us-east2-b location, run:

    $ gcloud vmware private-clouds external-addresses describe \
        first-ip --private-cloud=my-privatecloud --location=us-east2-b \
        --project=my-project

Or:

    $ gcloud vmware private-clouds external-addresses describe \
        first-ip --private-cloud=my-privatecloud

In the second example, the project and region are taken from gcloud
properties core/project and vmware/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/external-addresses/describe)

---
### `gcloud vmware private-clouds external-addresses list`

List external IP addresses in a VMware Engine private cloud

List external IP addresses in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds external-addresses list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list external IP addresses in the my-privatecloud private cloud, run:

    $ gcloud vmware private-clouds external-addresses list \
        --private-cloud=my-privatecloud --project=my-project \
        --location=us-east2-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/external-addresses/list)

---
### `gcloud vmware private-clouds external-addresses update`

Update an external IP address in a VMware Engine private cloud

Updates an external IP address in a VMware Engine private cloud. Only
description and internal-ip can be updated.

**Synopsis:**
```
gcloud vmware private-clouds external-addresses update
    (EXTERNAL_ADDRESS : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [--async] [--description=DESCRIPTION] [--internal-ip=INTERNAL_IP]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
External address resource - external_address. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument external_address on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXTERNAL_ADDRESS
     ID of the external address or fully qualified identifier for the
     external address.

     To set the external-address attribute:
     + provide the argument external_address on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument external_address on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Updated description for this external address |
| `--internal-ip` | INTERNAL_IP |  | Updated internal ip address for this external address |


**Examples:**
```bash
To update an external IP address called myip that belongs to the private
cloud my-private-cloud in project my-project and location us-west1-a by
changing its description to "Updated description for the external IP
address" and internal-ip to 165.87.54.14, run:

    $ gcloud vmware private-clouds external-addresses update myip \
        --project=my-project --private-cloud=my-private-cloud \
        --location=us-west1-a --internal-ip=165.87.54.14 \
        --description="Updated description for the external IP address"

Or:

    $ gcloud vmware private-clouds external-addresses update myip \
        --private-cloud=my-private-cloud --internal-ip=165.87.54.14 \
        --description="Updated description for the external IP address"

In the second example, the project and region are taken from gcloud
properties core/project and vmware/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/external-addresses/update)

---

## `gcloud vmware private-clouds hcx` — manage HCX using Google Cloud VMware Engine

## `gcloud vmware private-clouds hcx activationkeys` — manage VMware HCX activation keys using Google Cloud VMware Engine
### `gcloud vmware private-clouds hcx activationkeys create`

Create a Google Cloud VMware HCX activation key

Create a HCX activation key in a VMware Engine private cloud. Successful
creation of a HCX activation key results in a HCX activation key in
AVAILABLE state. Check the progress of a HCX activation key using gcloud
vmware private-clouds hcx activationkeys list.

**Synopsis:**
```
gcloud vmware private-clouds hcx activationkeys create
    (HCX_ACTIVATION_KEY
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
HCX activation key resource - hcxactivationkey. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument hcx_activation_key on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HCX_ACTIVATION_KEY
     ID of the HCX activation key or fully qualified identifier for the
     HCX activation key.

     To set the hcx-activation-key attribute:
     + provide the argument hcx_activation_key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument hcx_activation_key on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument hcx_activation_key on the command line with
       a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To create a HCX activation key called key1 in private cloud
my-private-cloud in zone us-west2-a, run:

    $ gcloud vmware private-clouds hcx activationkeys create key1 \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds hcx activationkeys create \
        my-cluster --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/hcx/activationkeys/create)

---
### `gcloud vmware private-clouds hcx activationkeys describe`

Describe a Google Cloud VMware HCX activation key

Display data associated with an HCX activation key, such as the key itself,
its resource name, and when it was created.

**Synopsis:**
```
gcloud vmware private-clouds hcx activationkeys describe
    (HCX_ACTIVATION_KEY
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
HCX activation key resource - hcxactivationkey. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument hcx_activation_key on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HCX_ACTIVATION_KEY
     ID of the HCX activation key or fully qualified identifier for the
     HCX activation key.

     To set the hcx-activation-key attribute:
     + provide the argument hcx_activation_key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument hcx_activation_key on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument hcx_activation_key on the command line with
       a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To describe a HCX activation key called key1 in private cloud
my-private-cloud in zone us-west2-a, run:

    $ gcloud vmware private-clouds hcx activationkeys describe key1 \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds hcx activationkeys describe key1 \
        --private-cloud=my-private-cloud

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/hcx/activationkeys/describe)

---
### `gcloud vmware private-clouds hcx activationkeys list`

List HCX activation keys in a Google Cloud VMware Engine private cloud

List HCX activation keys in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds hcx activationkeys list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list HCX activation keys in the my-private-cloud private cloud run:

    $ gcloud vmware private-clouds hcx activationkeys list \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds hcx activationkeys list \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/hcx/activationkeys/list)

---

## `gcloud vmware private-clouds logging-servers` — manage logging-server in Google Cloud VMware Engine
### `gcloud vmware private-clouds logging-servers create`

Create a Google Cloud VMware Engine logging-server

Create a logging-server in a VMware Engine private cloud to forward VCSA or
ESXI logs to it.

**Synopsis:**
```
gcloud vmware private-clouds logging-servers create
    (LOGGING_SERVER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --hostname=HOSTNAME --port=PORT --protocol=PROTOCOL
    --source-type=SOURCE_TYPE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Logging Server resource - logging_server. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument logging_server on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SERVER
     ID of the Logging Server or fully qualified identifier for the
     Logging Server.

     To set the logging-server attribute:
     + provide the argument logging_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hostname` | HOSTNAME |  | Fully-qualified domain name (FQDN) or IP Address of the logging server. |
| `--port` | PORT |  | Port number at which the logging server receives logs. |
| `--protocol` | one of: UDP, TCP, TLS, SSL, RELP |  | Defines possible protocols used to send logs to a logging server. PROTOCOL must be one of: UDP, TCP, TLS, SSL, RELP. |
| `--source-type` | one of: VCSA, ESXI |  | The type of component that produces logs that will be forwarded to this logging server. SOURCE_TYPE must be one of: VCSA, ESXI. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To create a logging-server called my-logging-server in private cloud
my-private-cloud, with source type ESXI, host name 192.168.0.30, protocol
UDP and port 514, run:

    $ gcloud vmware private-clouds logging-servers create \
        my-logging-server --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud --source-type=ESXI \
        --hostname=192.168.0.30 --protocol=UDP --port=514

    Or:

    $ gcloud vmware private-clouds logging-servers create \
        my-logging-server --private-cloud=my-private-cloud \
        --source-type=ESXI --hostname=192.168.0.30 --protocol=UDP \
        --port=514

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/logging-servers/create)

---
### `gcloud vmware private-clouds logging-servers delete`

Delete logging-server from a VMware Engine private cloud

Delete logging-server from a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds logging-servers delete
    (LOGGING_SERVER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Logging Server resource - logging_server. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument logging_server on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SERVER
     ID of the Logging Server or fully qualified identifier for the
     Logging Server.

     To set the logging-server attribute:
     + provide the argument logging_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete an logging-server called my-logging-server in private cloud
my-private-cloud and location us-east2-b, run:

    $ gcloud vmware private-clouds logging-servers delete \
        my-logging-server --private-cloud=my-private-cloud \
        --location=us-east2-b --project=my-project

Or:

    $ gcloud vmware private-clouds logging-servers delete \
        my-logging-server --private-cloud=my-private-cloud

In the second example, the project and region are taken from gcloud
properties core/project and vmware/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/logging-servers/delete)

---
### `gcloud vmware private-clouds logging-servers describe`

Describe a Google Cloud VMware Engine logging-server

Display data associated with a VMware Engine logging-server, such as its
host name, port, protocol, and source type.

**Synopsis:**
```
gcloud vmware private-clouds logging-servers describe
    (LOGGING_SERVER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Logging Server resource - logging_server. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument logging_server on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SERVER
     ID of the Logging Server or fully qualified identifier for the
     Logging Server.

     To set the logging-server attribute:
     + provide the argument logging_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To describe a logging-server called my-logging-server in private cloud
my-private-cloud and zone us-west2-a, run:

    $ gcloud vmware private-clouds logging-servers describe \
        my-logging-server --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds logging-servers describe \
        my-logging-server --private-cloud=my-private-cloud

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/logging-servers/describe)

---
### `gcloud vmware private-clouds logging-servers list`

List logging-server in a Google Cloud VMware Engine private cloud

List logging-server in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds logging-servers list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list logger-server in the my-private-cloud private cloud run:

    $ gcloud vmware private-clouds logging-servers list \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds logging-servers list \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/logging-servers/list)

---
### `gcloud vmware private-clouds logging-servers update`

Update a Google Cloud VMware Engine logging-server

Update a Logging Server. Only source_type, hostname, protocol, port can be
updated.

**Synopsis:**
```
gcloud vmware private-clouds logging-servers update
    (LOGGING_SERVER : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [--async] [--hostname=HOSTNAME] [--port=PORT] [--protocol=PROTOCOL]
    [--source-type=SOURCE_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Logging Server resource - logging_server. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument logging_server on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOGGING_SERVER
     ID of the Logging Server or fully qualified identifier for the
     Logging Server.

     To set the logging-server attribute:
     + provide the argument logging_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument logging_server on the command line with a
       fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--hostname` | HOSTNAME |  | Fully-qualified domain name (FQDN) or IP Address of the logging server. |
| `--port` | PORT |  | Port number at which the logging server receives logs. |
| `--protocol` | one of: UDP, TCP, TLS, RELP, SSL |  | Defines possible protocols used to send logs to a logging server. PROTOCOL must be one of: UDP, TCP, TLS, RELP, SSL. |
| `--source-type` | one of: VCSA, ESXI |  | The type of component that produces logs that will be forwarded to this logging server. SOURCE_TYPE must be one of: VCSA, ESXI. |


**Examples:**
```bash
To update a logging-server called my-logging-server in private cloud
my-private-cloud and zone us-west2-a to change ESXI source_type,
192.168.20.15 hostname UDP protocol and 514 port, run:

    $ gcloud vmware private-clouds logging-servers update \
        my-logging-server --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud --source-type=ESXI \
        --hostname=192.168.20.15 --protocol=UDP --port=514

    Or:

    $ gcloud vmware private-clouds logging-servers update \
        my-logging-server --private-cloud=my-private-cloud \
        --source-type=ESXI --hostname=192.168.20.15 --protocol=UDP \
        --port=514

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/logging-servers/update)

---

## `gcloud vmware private-clouds management-dns-zone-bindings` — manage Management DNS zone bindings in Google Cloud VMware Engine
### `gcloud vmware private-clouds management-dns-zone-bindings create`

Create a management DNS zone binding

Create a management DNS zone binding.

**Synopsis:**
```
gcloud vmware private-clouds management-dns-zone-bindings create
    (MANAGEMENT_DNS_ZONE_BINDING
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    (--vmware-engine-network=VMWARE_ENGINE_NETWORK
      | --vpc-network=VPC_NETWORK) [--async] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management DNS zone binding resource - management_dns_zone_binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_dns_zone_binding on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_DNS_ZONE_BINDING
     ID of the management DNS zone binding or fully qualified identifier
     for the management DNS zone binding.

     To set the management-dns-zone-binding attribute:
     + provide the argument management_dns_zone_binding on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vmware-engine-network` | VMWARE_ENGINE_NETWORK |  | _[Exactly one of these must be specified:]_ Resource name of VMware Engine network to bind to the management DNS zone of the private cloud. |
| `--vpc-network` | VPC_NETWORK |  | _[Exactly one of these must be specified:]_ Resource name of the Google Cloud VPC network to bind to the management DNS zone of the private cloud. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the binding resource that represents the network getting bound to the management DNS zone. |


**Examples:**
```bash
To create a management DNS zone binding called my-mgmt-dns-zone-binding
that corresponds to the vmware engine network sample-vmware-engine-network
in private cloud my-private-cloud, in location us-east2-b, run:

    $ gcloud vmware private-clouds management-dns-zone-bindings create \
        my-mgmt-dns-zone-binding --project=my-project \
        --private-cloud=my-private-cloud --location=us-east2-b \
        --vmware-engine-network=sample-vmware-engine-network

Or:

    $ gcloud vmware private-clouds management-dns-zone-bindings create \
        my-mgmt-dns-zone-binding --private-cloud=my-private-cloud \
        --vmware-engine-network=sample-vmware-engine-network

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/management-dns-zone-bindings/create)

---
### `gcloud vmware private-clouds management-dns-zone-bindings delete`

Delete a management DNS zone binding

Delete a management DNS zone binding.

**Synopsis:**
```
gcloud vmware private-clouds management-dns-zone-bindings delete
    (MANAGEMENT_DNS_ZONE_BINDING
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management DNS zone binding resource - management_dns_zone_binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_dns_zone_binding on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_DNS_ZONE_BINDING
     ID of the management DNS zone binding or fully qualified identifier
     for the management DNS zone binding.

     To set the management-dns-zone-binding attribute:
     + provide the argument management_dns_zone_binding on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a management DNS zone binding called my-mgmt-dns-zone-binding in
private cloud my-private-cloud, in location us-east2-b, run:

    $ gcloud vmware private-clouds management-dns-zone-bindings delete \
        my-mgmt-dns-zone-binding --project=my-project \
        --private-cloud=my-private-cloud --location=us-east2-b

Or:

    $ gcloud vmware private-clouds management-dns-zone-bindings delete \
        my-mgmt-dns-zone-binding --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/management-dns-zone-bindings/delete)

---
### `gcloud vmware private-clouds management-dns-zone-bindings describe`

Describe a management DNS zone binding

Describe a management DNS zone binding.

**Synopsis:**
```
gcloud vmware private-clouds management-dns-zone-bindings describe
    (MANAGEMENT_DNS_ZONE_BINDING
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management DNS zone binding resource - management_dns_zone_binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_dns_zone_binding on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_DNS_ZONE_BINDING
     ID of the management DNS zone binding or fully qualified identifier
     for the management DNS zone binding.

     To set the management-dns-zone-binding attribute:
     + provide the argument management_dns_zone_binding on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To get a description of a management DNS zone binding called
my-mgmt-dns-zone-binding that corresponds to the vmware engine network
sample-vmware-engine-network in private cloud my-private-cloud, in location
us-east2-b, run:

    $ gcloud vmware private-clouds management-dns-zone-bindings \
        describe my-mgmt-dns-zone-binding --project=my-project \
        --private-cloud=my-private-cloud --location=us-east2-b

Or:

    $ gcloud vmware private-clouds management-dns-zone-bindings \
        describe my-mgmt-dns-zone-binding \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/management-dns-zone-bindings/describe)

---
### `gcloud vmware private-clouds management-dns-zone-bindings list`

List management DNS zone bindings in a VMware Engine private cloud

List management DNS zone bindings in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds management-dns-zone-bindings list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list management DNS zone bindings in the my-private-cloud private cloud,
run:

    $ gcloud vmware private-clouds management-dns-zone-bindings list \
        --private-cloud=my-private-cloud --project=my-project \
        --location=us-east2-b
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/management-dns-zone-bindings/list)

---
### `gcloud vmware private-clouds management-dns-zone-bindings repair`

Repair a management DNS zone binding

Repair a management DNS zone binding.

**Synopsis:**
```
gcloud vmware private-clouds management-dns-zone-bindings repair
    (MANAGEMENT_DNS_ZONE_BINDING
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management DNS zone binding resource - management_dns_zone_binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_dns_zone_binding on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_DNS_ZONE_BINDING
     ID of the management DNS zone binding or fully qualified identifier
     for the management DNS zone binding.

     To set the management-dns-zone-binding attribute:
     + provide the argument management_dns_zone_binding on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To repair a management DNS zone binding called my-mgmt-dns-zone-binding in
private cloud my-private-cloud, in project my-project, in location
us-east2-b, run:

    $ gcloud vmware private-clouds management-dns-zone-bindings repair \
        my-mgmt-dns-zone-binding --project=my-project \
        --private-cloud=my-private-cloud --location=us-east2-b

Or:

    $ gcloud vmware private-clouds management-dns-zone-bindings repair \
        my-mgmt-dns-zone-binding --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/management-dns-zone-bindings/repair)

---
### `gcloud vmware private-clouds management-dns-zone-bindings update`

Update a management DNS zone binding

Update a management DNS zone binding.

**Synopsis:**
```
gcloud vmware private-clouds management-dns-zone-bindings update
    (MANAGEMENT_DNS_ZONE_BINDING
      : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --description=DESCRIPTION [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management DNS zone binding resource - management_dns_zone_binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_dns_zone_binding on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_DNS_ZONE_BINDING
     ID of the management DNS zone binding or fully qualified identifier
     for the management DNS zone binding.

     To set the management-dns-zone-binding attribute:
     + provide the argument management_dns_zone_binding on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument management_dns_zone_binding on the command
       line with a fully specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Text describing the binding resource that represents the network getting bound to the management DNS zone. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To update a management DNS zone binding called my-mgmt-dns-zone-binding in
private cloud my-private-cloud and zone us-west2-a with description New
Description, run:

    $ gcloud vmware private-clouds management-dns-zone-bindings update \
        my-mgmt-dns-zone-binding --project=my-project \
        --private-cloud=my-private-cloud --location=us-east2-b \
        --description="New Description"

    Or:

    $ gcloud vmware private-clouds management-dns-zone-bindings update \
        my-mgmt-dns-zone-binding --private-cloud=my-private-cloud \
        --description="New Description"

    In the second example, the project and location are taken from gcloud properties `core/project` and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/management-dns-zone-bindings/update)

---

## `gcloud vmware private-clouds nsx` — manage NSX using Google Cloud VMware Engine

## `gcloud vmware private-clouds nsx credentials` — manage VMware NSX credentials using Google Cloud VMware Engine
### `gcloud vmware private-clouds nsx credentials describe`

Retrieve VMware NSX sign-in credentials associated with a Google Cloud VMware Engine private cloud

Retrieve VMware NSX sign-in credentials associated with a VMware Engine
private cloud.

**Synopsis:**
```
gcloud vmware private-clouds nsx credentials describe
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To get sign-in credentials for NSX in private cloud my-private-cloud, run:

    $ gcloud vmware private-clouds nsx credentials describe \
        --private-cloud=my-private-cloud --location=us-west2-a \
        --project=my-project

Or:

    $ gcloud vmware private-clouds nsx credentials describe \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/nsx/credentials/describe)

---
### `gcloud vmware private-clouds nsx credentials reset`

Reset VMware NSX sign-in credentials associated with a Google Cloud VMware Engine private cloud

Reset VMware NSX sign-in credentials associated with a VMware Engine
private cloud.

**Synopsis:**
```
gcloud vmware private-clouds nsx credentials reset
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To reset sign-in credentials for NSX in private cloud my-private-cloud,
run:

    $ gcloud vmware private-clouds nsx credentials reset \
        --private-cloud=my-private-cloud --location=us-west2-a \
        --project=my-project

Or:

    $ gcloud vmware private-clouds nsx credentials reset \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/nsx/credentials/reset)

---

## `gcloud vmware private-clouds subnets` — manage vmware subnets in Google Cloud VMware Engine
### `gcloud vmware private-clouds subnets describe`

Describe a subnet in a VMware Engine private cloud

Describe a Subnet by its resource name. It contains details of the subnet,
such as ip_cidr_range, gateway_ip, state, and type.

**Synopsis:**
```
gcloud vmware private-clouds subnets describe
    (SUBNET : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnet resource - subnet. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNET
     ID of the subnet or fully qualified identifier for the subnet.

     To set the subnet attribute:
     + provide the argument subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To get the information about a subnet resource called my-subnet, that
belongs to the private cloud my-private-cloud in project my-project and
zone us-west1-a, run:

    $ gcloud vmware private-clouds subnets describe my-subnet \
        --private-cloud=my-private-cloud --location=us-west1-a \
        --project=my-project

Or:

    $ gcloud vmware private-clouds subnets describe my-subnet \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone, respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/subnets/describe)

---
### `gcloud vmware private-clouds subnets list`

List subnets in a VMware Engine private cloud

List subnets in a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds subnets list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list subnets that belong to the private cloud my-privatecloud in project
my-project and zone us-east2-b, run:

    $ gcloud vmware private-clouds subnets list \
        --private-cloud=my-privatecloud --location=us-east2-b \
        --project=my-project

Or:

    $ gcloud vmware private-clouds subnets list \
        --private-cloud=my-privatecloud

In the above example, the project and the location are taken from gcloud
properties core/project and compute/zone, respectively.

To list subnets that belong to all the private clouds in project my-project
and zone us-east2-b, run:

    $ gcloud vmware private-clouds subnets list --private-cloud=- \
        --location=us-east2-b --project=my-project

Or:

    $ gcloud vmware private-clouds subnets list --private-cloud=-

In the above example, the project and the location are taken from gcloud
properties core/project and compute/zone, respectively.

To list subnets for all private clouds in all locations in project
my-project, run:

    $ gcloud vmware private-clouds subnets list --private-cloud=- \
        --location=- --project=my-project

Or:

    $ gcloud vmware private-clouds subnets list --private-cloud=- \
        --location=-

In the last example, the project is taken from gcloud properties
core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/subnets/list)

---
### `gcloud vmware private-clouds subnets update`

Update a subnet

Update a Subnet. Only ip-cidr-range can be updated. This is a synchronous
command and doesn't support --async and --no-async flags.

**Synopsis:**
```
gcloud vmware private-clouds subnets update
    (SUBNET : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    --ip-cidr-range=IP_CIDR_RANGE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnet resource - subnet. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNET
     ID of the subnet or fully qualified identifier for the subnet.

     To set the subnet attribute:
     + provide the argument subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ip-cidr-range` | IP_CIDR_RANGE |  | Updated IP CIDR range for this subnet. |


**Examples:**
```bash
To update a subnet named my-subnet, that belongs to the private cloud
my-private-cloud in project my-project and zone us-west1-a by changing its
ip-cidr-range to 10.0.0.0/24, run:

    $ gcloud vmware private-clouds subnets update my-subnet \
        --private-cloud=my-private-cloud --location=us-west1 \
        --project=my-project --ip-cidr-range=10.0.0.0/24

Or:

    $ gcloud vmware private-clouds subnets update my-subnet \
        --private-cloud=my-private-cloud --ip-cidr-range=10.0.0.0/24

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone, respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/subnets/update)

---

## `gcloud vmware private-clouds upgrades` — manage upgrades in Google Cloud VMware Engine
### `gcloud vmware private-clouds upgrades describe`

Describe a Google Cloud VMware Engine upgrades

Display data associated with a VMware Engine upgrade, such as its schdule,
and status.

**Synopsis:**
```
gcloud vmware private-clouds upgrades describe
    (UPGRADE : --location=LOCATION --private-cloud=PRIVATE_CLOUD)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Upgrade resource - upgrade. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument upgrade on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  UPGRADE
     ID of the upgrade or fully qualified identifier for the upgrade.

     To set the upgrade attribute:
     + provide the argument upgrade on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument upgrade on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --private-cloud=PRIVATE_CLOUD
     VMware Engine private cloud.

     To set the private-cloud attribute:
     + provide the argument upgrade on the command line with a fully
       specified name;
     + provide the argument --private-cloud on the command line.
```

**Examples:**
```bash
To describe a upgrade called my-upgrade for a private cloud
my-private-cloud and zone us-west2-a, run:

    $ gcloud vmware private-clouds upgrades describe my-upgrade \
        --location=us-west2-a --project=my-project \
        --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds upgrades describe my-upgrade \
        --private-cloud=my-private-cloud

    In the second example, the project and location are taken from gcloud properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/upgrades/describe)

---
### `gcloud vmware private-clouds upgrades list`

List upgrades for a Google Cloud VMware Engine private cloud

List upgrades for a VMware Engine private cloud.

**Synopsis:**
```
gcloud vmware private-clouds upgrades list
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list upgrades for the my-private-cloud private cloud run:

    $ gcloud vmware private-clouds upgrades list --location=us-west2-a \
        --project=my-project --private-cloud=my-private-cloud

    Or:

    $ gcloud vmware private-clouds upgrades list \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/upgrades/list)

---

## `gcloud vmware private-clouds vcenter` — manage vCenter resources in Google Cloud VMware Engine

## `gcloud vmware private-clouds vcenter credentials` — manage VMware vCenter credentials using Google Cloud VMware Engine
### `gcloud vmware private-clouds vcenter credentials describe`

Describe Google Cloud VMware Engine vCenter credentials

Retrieve VMware vCenter sign-in credentials associated with a VMware Engine
private cloud.

**Synopsis:**
```
gcloud vmware private-clouds vcenter credentials describe
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To get sign-in credentials for vCenter in private cloud my-private-cloud,
run:

    $ gcloud vmware private-clouds vcenter credentials describe \
        --private-cloud=my-private-cloud --location=us-west2-a \
        --project=my-project

Or:

    $ gcloud vmware private-clouds vcenter credentials describe \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/vcenter/credentials/describe)

---
### `gcloud vmware private-clouds vcenter credentials reset`

Reset VMware vCenter sign-in credentials associated with a Google Cloud VMware Engine private cloud

Reset VMware vCenter sign-in credentials associated with a VMware Engine
private cloud.

**Synopsis:**
```
gcloud vmware private-clouds vcenter credentials reset
    (--private-cloud=PRIVATE_CLOUD : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-cloud` | PRIVATE_CLOUD |  | _[This must be specified.]_ ID of the private cloud or fully qualified identifier for the private cloud. To set the private-cloud attribute: + provide the argument --private-cloud on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the private cloud or cluster. To set the location attribute: + provide the argument --private-cloud on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/zone. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To reset sign-in credentials for vCenter in private cloud my-private-cloud,
run:

    $ gcloud vmware private-clouds vcenter credentials reset \
        --private-cloud=my-private-cloud --location=us-west2-a \
        --project=my-project

Or:

    $ gcloud vmware private-clouds vcenter credentials reset \
        --private-cloud=my-private-cloud

In the second example, the project and location are taken from gcloud
properties core/project and compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-clouds/vcenter/credentials/reset)

---
# gcloud telco-automation orchestration-cluster

manage telco automation orchestration cluster instances

### `gcloud telco-automation orchestration-cluster create`

Create a telco automation orchestration cluster

Create a new telco automation orchestration cluster.

**Synopsis:**
```
gcloud telco-automation orchestration-cluster create
    (ORCHESTRATION_CLUSTER : --location=LOCATION) [--async]
    [--cidr-blocks=[cidr-block=CIDR-BLOCK],[display-name=DISPLAY-NAME]]
    [--cluster-cidr-block=CLUSTER_CIDR_BLOCK]
    [--cluster-named-range=CLUSTER_NAMED_RANGE] [--full-management-config]
    [--master-ipv4-cidr-block=MASTER_IPV4_CIDR_BLOCK]
    [--services-cidr-block=SERVICES_CIDR_BLOCK]
    [--services-named-range=SERVICES_NAMED_RANGE]
    [--network=NETWORK : --subnet=SUBNET] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Orchestration Cluster resource - Telco automation orchestration cluster to
create. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument orchestration_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ORCHESTRATION_CLUSTER
     ID of the Orchestration Cluster or fully qualified identifier for the
     Orchestration Cluster.

     To set the orchestration_cluster attribute:
     + provide the argument orchestration_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument orchestration_cluster on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cidr-blocks` | [cidr-block=CIDR-BLOCK],[display-name=DISPLAY-NAME] |  | Master Authorized Network that supports multiple CIDR blocks. Allows access to the k8s master from multiple blocks. |
| `--cluster-cidr-block` | CLUSTER_CIDR_BLOCK |  | IP address range for the cluster pod IPs. Set to blank to have a range chosen with the default size. Set to /netmask (e.g. /14) to have a range chosen with a specific netmask. Set to a CIDR notation (e.g. 10.96.0.0/14) from the RFC-1918 private networks (e.g. 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) to pick a specific range to use. |
| `--cluster-named-range` | CLUSTER_NAMED_RANGE |  | Name of the existing secondary range in the cluster's subnetwork to use for pod IP addresses. Alternatively, cluster_cidr_block can be used to automatically create a GKE-managed one. |
| `--full-management-config` |  |  | This parameter is to marked true only if the management configuration arguments which are provided, belong to full (Autopilot) cluster management. |
| `--master-ipv4-cidr-block` | MASTER_IPV4_CIDR_BLOCK |  | /28 network that the control plane will use. |
| `--services-cidr-block` | SERVICES_CIDR_BLOCK |  | IP address range for the cluster service IPs. Set to blank to have a range chosen with the default size. Set to /netmask (e.g. /14) to have a range chosen with a specific netmask. Set to a CIDR notation (e.g. 10.96.0.0/14) from the RFC-1918 private networks (e.g. 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) to pick a specific range to use. |
| `--services-named-range` | SERVICES_NAMED_RANGE |  | Name of the existing secondary range in the cluster's subnetwork to use for service ClusterIPs. Alternatively, services_cidr_block can be used to automatically create a GKE-managed one. |
| `--network` | NETWORK |  | Name of the VPC Network to put the GKE cluster and nodes in. The VPC will be created if it doesn't exist. |
| `--subnet` | SUBNET |  | Specifies the subnet that the interface will be part of. Network key must be specified and the subnet must be a subnetwork of the specified network. |


**Examples:**
```bash
To create an orchestration cluster called test-orchestrationCluster in
location us-central1, run:

    $ gcloud telco-automation orchestration-cluster create \
        test-orchestrationCluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation/orchestration-cluster/create)

---
### `gcloud telco-automation orchestration-cluster delete`

Delete a telco automation orchestration cluster

Delete a telco automation orchestration cluster.

**Synopsis:**
```
gcloud telco-automation orchestration-cluster delete
    (ORCHESTRATION_CLUSTER : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Orchestration Cluster resource - Telco automation orchestration cluster to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument orchestration_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ORCHESTRATION_CLUSTER
     ID of the Orchestration Cluster or fully qualified identifier for the
     Orchestration Cluster.

     To set the orchestration_cluster attribute:
     + provide the argument orchestration_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument orchestration_cluster on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an orchestration cluster called test-cluster in region
us-central1, run:

    $ gcloud telco-automation orchestration-cluster delete \
        test-cluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation/orchestration-cluster/delete)

---
### `gcloud telco-automation orchestration-cluster describe`

Show details about the orchestration cluster

Show details about the orchestration cluster.

**Synopsis:**
```
gcloud telco-automation orchestration-cluster describe
    (ORCHESTRATION_CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Orchestration Cluster resource - The orchestration cluster you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument orchestration_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ORCHESTRATION_CLUSTER
     ID of the Orchestration Cluster or fully qualified identifier for the
     Orchestration Cluster.

     To set the orchestration_cluster attribute:
     + provide the argument orchestration_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument orchestration_cluster on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about an orchestration cluster called test-cluster in
region us-central1, run:

    $ gcloud telco-automation orchestration-cluster describe \
        test-cluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation/orchestration-cluster/describe)

---
### `gcloud telco-automation orchestration-cluster list`

List telco automation orchestration clusters

List telco automation orchestration clusters.

**Synopsis:**
```
gcloud telco-automation orchestration-cluster list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all orchestration clusters in region us-central1, run:

    $ gcloud telco-automation orchestration-cluster list \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation/orchestration-cluster/list)

---
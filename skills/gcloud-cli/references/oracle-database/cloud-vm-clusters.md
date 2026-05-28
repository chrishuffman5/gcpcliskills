# gcloud oracle-database cloud-vm-clusters

manage Cloud Vm Cluster resources

### `gcloud oracle-database cloud-vm-clusters create`

Create a new CloudVmCluster

Create a new CloudVmCluster.

**Synopsis:**
```
gcloud oracle-database cloud-vm-clusters create CLOUD_VM_CLUSTER
    --exadata-infrastructure=EXADATA_INFRASTRUCTURE [--async]
    [--backup-odb-subnet=BACKUP_ODB_SUBNET]
    [--backup-subnet-cidr=BACKUP_SUBNET_CIDR] [--cidr=CIDR]
    [--display-name=DISPLAY_NAME] [--labels=[LABELS,...]]
    [--location=LOCATION] [--network=NETWORK] [--odb-network=ODB_NETWORK]
    [--odb-subnet=ODB_SUBNET] [--request-id=REQUEST_ID]
    [[--properties-cpu-core-count=PROPERTIES_CPU_CORE_COUNT
      --properties-license-type=PROPERTIES_LICENSE_TYPE
      : --properties-cluster-name=PROPERTIES_CLUSTER_NAME
      --properties-data-storage-size-tb=PROPERTIES_DATA_STORAGE_SIZE_TB
      --properties-db-node-storage-size-gb=PROPERTIES_DB_NODE_STORAGE_SIZE_GB --properties-db-server-ocids=[PROPERTIES_DB_SERVER_OCIDS,
      ...] --properties-disk-redundancy=PROPERTIES_DISK_REDUNDANCY
      --properties-gi-version=PROPERTIES_GI_VERSION
      --properties-hostname-prefix=PROPERTIES_HOSTNAME_PREFIX
      --properties-local-backup-enabled
      --properties-memory-size-gb=PROPERTIES_MEMORY_SIZE_GB
      --properties-node-count=PROPERTIES_NODE_COUNT
      --properties-ocpu-count=PROPERTIES_OCPU_COUNT
      --properties-sparse-diskgroup-enabled
      --properties-ssh-public-keys=[PROPERTIES_SSH_PUBLIC_KEYS,...]
      --properties-system-version=PROPERTIES_SYSTEM_VERSION
      --diagnostics-data-collection-options-events-enabled
      --diagnostics-data-collection-options-health-monitoring-enabled
      --diagnostics-data-collection-options-incident-logs-enabled
      --time-zone-id=TIME_ZONE_ID --time-zone-version=TIME_ZONE_VERSION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudVmCluster resource - Identifier. The name of the VM Cluster resource
with the format:
projects/{project}/locations/{region}/cloudVmClusters/{cloud_vm_cluster}
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument cloud_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument cloud_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  CLOUD_VM_CLUSTER
     ID of the cloudVmCluster or fully qualified identifier for the
     cloudVmCluster.

     To set the cloud_vm_cluster attribute:
     + provide the argument cloud_vm_cluster on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--exadata-infrastructure` | EXADATA_INFRASTRUCTURE |  | _[This must be specified.]_ ID of the cloudExadataInfrastructure or fully qualified identifier for the cloudExadataInfrastructure. To set the cloud-exadata-infrastructure attribute: + provide the argument --exadata-infrastructure on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-subnet-cidr` | BACKUP_SUBNET_CIDR |  | _[+ provide the argument --backup-odb-subnet on the command line.]_ CIDR range of the backup subnet. |
| `--cidr` | CIDR |  | _[+ provide the argument --backup-odb-subnet on the command line.]_ Network settings. CIDR to use for cluster IP allocation. |
| `--display-name` | DISPLAY_NAME |  | _[+ provide the argument --backup-odb-subnet on the command line.]_ User friendly name for this resource. |
| `--labels` | [LABELS,...] |  | _[+ provide the argument --backup-odb-subnet on the command line.]_ Labels or tags associated with the VM Cluster. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | _[+ provide the argument --backup-odb-subnet on the command line.]_ For resources [backup-odb-subnet, cloud_vm_cluster, exadata-infrastructure, odb-network, odb-subnet], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--odb-network` | ODB_NETWORK |  | _[+ provide the argument --network on the command line.]_ For resources [backup-odb-subnet, odb-network, odb-subnet], provides fallback value for resource odb-network attribute. When the resource's full URI path is not provided, odb-network will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | _[+ provide the argument --odb-subnet on the command line.]_ An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
Choose an available gi-versions in your location by running gcloud
oracle-database db-system-shapes list --location=us-east4. To create
CloudVmCluster instance with id my-instance in the location us-east4 with
display-name my instance, odb-network
projects/network-project/locations/us-east4/odbNetworks/my-odbnetwork,
odb-subnet
projects/network-project/locations/us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-odbsubnet,
backup-odb-subnet
projects/network-project/locations/us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-backup-odbsubnet,
cidr 10.1.0.0/24, network
projects/my-project/locations/global/networks/default, backup-subnet-cidr
10.2.0.0/24, license-type LICENSE_INCLUDED, ssh-public-keys
VtTxzlPJtIivthmLOmWdRDFy5l27pKUTwLp02, hostname-prefix hostname1,
cpu-core-count 4 and choosen gi-version xx.0.0.0, run:

To set the network configuration use one of the following options:

ODBNetwork based configuration(This is the recommended way):

    $ gcloud oracle-database cloud-vm-clusters create my-instance \
        --location=us-east4 --display-name="my instance" \
        --odb-network=projects/network-project/locations/us-east4/\
    odbNetworks/my-odbnetwork \
        --odb-subnet=projects/network-project/locations/us-east4/\
    odbNetworks/my-odbnetwork/odbSubnets/my-odbsubnet \
        --backup-odb-subnet=projects/network-project/locations/\
    us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-backup-odbsubnet \
        --properties-license-type=LICENSE_INCLUDED \
        --properties-ssh-public-keys="VtTxzlPJtIivthmLOmWdRDFy5l27pKUTwL\
    p02" --properties-gi-version=xx.0.0.0 \
        --properties-hostname-prefix=hostname1 \
        --properties-cpu-core-count=4

Network and CIDR based configuration:

    $ gcloud oracle-database cloud-vm-clusters create my-instance \
        --location=us-east4 --display-name="my instance" \
        --cidr=10.1.0.0/24 \
        --network=projects/my-project/locations/global/networks/\
    default --backup-subnet-cidr=10.2.0.0/24 \
        --properties-license-type=LICENSE_INCLUDED \
        --properties-ssh-public-keys="VtTxzlPJtIivthmLOmWdRDFy5l27pKUTwL\
    p02" --properties-gi-version=xx.0.0.0 \
        --properties-hostname-prefix=hostname1 \
        --properties-cpu-core-count=4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-vm-clusters/create)

---
### `gcloud oracle-database cloud-vm-clusters delete`

Delete a CloudVmCluster

Delete a CloudVmCluster.

**Synopsis:**
```
gcloud oracle-database cloud-vm-clusters delete
    (CLOUD_VM_CLUSTER : --location=LOCATION) [--async] [--force]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudVmCluster resource - The name of the Cloud VM Cluster in the
following format:
projects/{project}/locations/{location}/cloudVmClusters/{cloud_vm_cluster}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cloud_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLOUD_VM_CLUSTER
     ID of the cloudVmCluster or fully qualified identifier for the
     cloudVmCluster.

     To set the cloud_vm_cluster attribute:
     + provide the argument cloud_vm_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudVmCluster resource.

     To set the location attribute:
     + provide the argument cloud_vm_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, all child resources for the VM Cluster will be deleted. A VM Cluster can only be deleted once all its child resources have been deleted. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a CloudVmCluster with id my-instance in the location us-east4,
run:

    $ gcloud oracle-database cloud-vm-clusters delete my-instance \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-vm-clusters/delete)

---
### `gcloud oracle-database cloud-vm-clusters describe`

Describe cloudVmClusters

Describe a cloudVmCluster

**Synopsis:**
```
gcloud oracle-database cloud-vm-clusters describe
    (CLOUD_VM_CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudVmCluster resource - The name of the Cloud VM Cluster in the
following format:
projects/{project}/locations/{location}/cloudVmClusters/{cloud_vm_cluster}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument cloud_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLOUD_VM_CLUSTER
     ID of the cloudVmCluster or fully qualified identifier for the
     cloudVmCluster.

     To set the cloud_vm_cluster attribute:
     + provide the argument cloud_vm_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudVmCluster resource.

     To set the location attribute:
     + provide the argument cloud_vm_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the cloudVmCluster, run:

    $ gcloud oracle-database cloud-vm-clusters describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-vm-clusters/describe)

---
### `gcloud oracle-database cloud-vm-clusters list`

List all CloudVmClusters

List all CloudVmClusters.

**Synopsis:**
```
gcloud oracle-database cloud-vm-clusters list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all CloudVmClusters in the location us-east4, run:

    $ gcloud oracle-database cloud-vm-clusters list --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-vm-clusters/list)

---

## `gcloud oracle-database cloud-vm-clusters db-nodes` — manage Db Node resources
### `gcloud oracle-database cloud-vm-clusters db-nodes list`

List all DbNodes

List all DbNodes.

**Synopsis:**
```
gcloud oracle-database cloud-vm-clusters db-nodes list
    [--cloud-vm-cluster=CLOUD_VM_CLUSTER
      --exadb-vm-cluster=EXADB_VM_CLUSTER --location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-vm-cluster` | CLOUD_VM_CLUSTER |  | _[following types: [cloudVmCluster, exadbVmCluster].]_ ID of the cloudVmClusterOrExadbVmCluster or fully qualified identifier for the cloudVmClusterOrExadbVmCluster. To set the cloud_vm_cluster attribute: + provide the argument --cloud-vm-cluster on the command line. Must be specified for resource of type [cloudVmCluster]. |
| `--exadb-vm-cluster` | EXADB_VM_CLUSTER |  | _[following types: [cloudVmCluster, exadbVmCluster].]_ ID of the cloudVmClusterOrExadbVmCluster or fully qualified identifier for the cloudVmClusterOrExadbVmCluster. To set the exadb_vm_cluster attribute: + provide the argument --exadb-vm-cluster on the command line. Must be specified for resource of type [exadbVmCluster]. |
| `--location` | LOCATION |  | _[following types: [cloudVmCluster, exadbVmCluster].]_ The location id of the cloudVmClusterOrExadbVmCluster resource. To set the location attribute: + provide the argument --exadb-vm-cluster on the command line with a fully specified name; + provide the argument --cloud-vm-cluster on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DbNodes in the location us-east4, run:

    $ gcloud oracle-database cloud-vm-clusters db-nodes list \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/cloud-vm-clusters/db-nodes/list)

---
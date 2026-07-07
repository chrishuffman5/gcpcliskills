# gcloud oracle-database exadb-vm-clusters

manage Exadb Vm Cluster resources

### `gcloud oracle-database exadb-vm-clusters create`

Create exadbVmClusters

Create an exadbVmCluster

**Synopsis:**
```
gcloud oracle-database exadb-vm-clusters create EXADB_VM_CLUSTER
    --backup-odb-subnet=BACKUP_ODB_SUBNET --display-name=DISPLAY_NAME
    --odb-subnet=ODB_SUBNET
    (--properties-enabled-ecpu-count-per-node=PROPERTIES_ENABLED_ECPU_COUNT_PER_NODE --properties-exascale-db-storage-vault=PROPERTIES_EXASCALE_DB_STORAGE_VAULT --properties-grid-image-id=PROPERTIES_GRID_IMAGE_ID --properties-hostname-prefix=PROPERTIES_HOSTNAME_PREFIX --properties-node-count=PROPERTIES_NODE_COUNT --properties-shape-attribute=PROPERTIES_SHAPE_ATTRIBUTE --properties-ssh-public-keys=[PROPERTIES_SSH_PUBLIC_KEYS,
      ...]
      --vm-file-system-storage-size-in-gbs-per-node=VM_FILE_SYSTEM_STORAGE_SIZE_IN_GBS_PER_NODE : --properties-additional-ecpu-count-per-node=PROPERTIES_ADDITIONAL_ECPU_COUNT_PER_NODE --properties-cluster-name=PROPERTIES_CLUSTER_NAME --properties-license-model=PROPERTIES_LICENSE_MODEL --properties-scan-listener-port-tcp=PROPERTIES_SCAN_LISTENER_PORT_TCP --data-collection-options-is-diagnostics-events-enabled --data-collection-options-is-health-monitoring-enabled --data-collection-options-is-incident-logs-enabled --time-zone-id=TIME_ZONE_ID --time-zone-version=TIME_ZONE_VERSION)
    [--async] [--labels=[LABELS,...]] [--location=LOCATION]
    [--odb-network=ODB_NETWORK] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExadbVmCluster resource - Identifier. The name of the ExadbVmCluster
resource in the following format:
projects/{project}/locations/{region}/exadbVmClusters/{exadb_vm_cluster}
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument exadb_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument exadb_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  EXADB_VM_CLUSTER
     ID of the exadbVmCluster or fully qualified identifier for the
     exadbVmCluster.

     To set the exadb_vm_cluster attribute:
     + provide the argument exadb_vm_cluster on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-odb-subnet` | BACKUP_ODB_SUBNET |  | _[This must be specified.]_ ID of the odbSubnet or fully qualified identifier for the odbSubnet. To set the odb-subnet attribute: + provide the argument --backup-odb-subnet on the command line. |
| `--display-name` | DISPLAY_NAME |  | _[This must be specified.]_ The display name for the ExadbVmCluster. The name does not have to be unique within your project. The name must be 1-255 characters long and can only contain alphanumeric characters. |
| `--odb-subnet` | ODB_SUBNET |  | _[This must be specified.]_ ID of the odbSubnet or fully qualified identifier for the odbSubnet. To set the odb-subnet attribute: + provide the argument --odb-subnet on the command line. |
| `--properties-enabled-ecpu-count-per-node` | PROPERTIES_ENABLED_ECPU_COUNT_PER_NODE |  | _[This must be specified.]_ The number of ECPUs enabled per node for an exadata vm cluster on exascale infrastructure. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--properties-grid-image-id` | PROPERTIES_GRID_IMAGE_ID |  | _[the command line.]_ Grid Infrastructure Version. |
| `--properties-hostname-prefix` | PROPERTIES_HOSTNAME_PREFIX |  | _[the command line.]_ Prefix for VM cluster host names. |
| `--properties-node-count` | PROPERTIES_NODE_COUNT |  | _[the command line.]_ The number of nodes/VMs in the ExadbVmCluster. |
| `--properties-shape-attribute` | one of: block-storage Indicates that the resource is in block storage |  | _[the command line.]_ The shape attribute of the VM cluster. The type of Exascale storage used for Exadata VM cluster. The default is SMART_STORAGE which supports Oracle Database 23ai and later. PROPERTIES_SHAPE_ATTRIBUTE must be one of: block-storage Indicates that the resource is in block storage. smart-storage Indicates that the resource is in smart storage. |
| `--properties-ssh-public-keys` | [PROPERTIES_SSH_PUBLIC_KEYS,...] |  | _[the command line.]_ The SSH public keys for the ExadbVmCluster. |
| `--properties-additional-ecpu-count-per-node` | PROPERTIES_ADDITIONAL_ECPU_COUNT_PER_NODE |  | _[allocation for the exadbvmcluster.]_ The number of additional ECPUs per node for an Exadata VM cluster on exascale infrastructure. |
| `--properties-cluster-name` | PROPERTIES_CLUSTER_NAME |  | _[allocation for the exadbvmcluster.]_ The cluster name for Exascale vm cluster. The cluster name must begin with an alphabetic character and may contain hyphens(-) but can not contain underscores(). It should be not more than 11 characters and is not case sensitive. OCI Cluster name. |
| `--properties-license-model` | one of: bring-your-own-license Bring your own license |  | _[allocation for the exadbvmcluster.]_ The license type of the ExadbVmCluster. PROPERTIES_LICENSE_MODEL must be one of: bring-your-own-license Bring your own license. license-included Default is license included. |
| `--properties-scan-listener-port-tcp` | PROPERTIES_SCAN_LISTENER_PORT_TCP |  | _[allocation for the exadbvmcluster.]_ SCAN listener port - TCP |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [LABELS,...] |  | The labels or tags associated with the ExadbVmCluster. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | For resources [backup-odb-subnet, exadb_vm_cluster, odb-network, odb-subnet, properties-exascale-db-storage-vault], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--odb-network` | ODB_NETWORK |  | For resources [backup-odb-subnet, odb-network, odb-subnet], provides fallback value for resource odb-network attribute. When the resource's full URI path is not provided, odb-network will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create the exadbVmCluster, run:

    $ gcloud oracle-database exadb-vm-clusters create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exadb-vm-clusters/create)

---
### `gcloud oracle-database exadb-vm-clusters delete`

Delete exadbVmClusters

Delete an exadbVmCluster

**Synopsis:**
```
gcloud oracle-database exadb-vm-clusters delete
    (EXADB_VM_CLUSTER : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExadbVmCluster resource - The name of the ExadbVmCluster in the following
format:
projects/{project}/locations/{location}/exadbVmClusters/{exadb_vm_cluster}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exadb_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXADB_VM_CLUSTER
     ID of the exadbVmCluster or fully qualified identifier for the
     exadbVmCluster.

     To set the exadb_vm_cluster attribute:
     + provide the argument exadb_vm_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exadbVmCluster resource.

     To set the location attribute:
     + provide the argument exadb_vm_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete the exadbVmCluster, run:

    $ gcloud oracle-database exadb-vm-clusters delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exadb-vm-clusters/delete)

---
### `gcloud oracle-database exadb-vm-clusters describe`

Describe exadbVmClusters

Describe an exadbVmCluster

**Synopsis:**
```
gcloud oracle-database exadb-vm-clusters describe
    (EXADB_VM_CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExadbVmCluster resource - The name of the ExadbVmCluster in the following
format:
projects/{project}/locations/{location}/exadbVmClusters/{exadb_vm_cluster}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exadb_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXADB_VM_CLUSTER
     ID of the exadbVmCluster or fully qualified identifier for the
     exadbVmCluster.

     To set the exadb_vm_cluster attribute:
     + provide the argument exadb_vm_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exadbVmCluster resource.

     To set the location attribute:
     + provide the argument exadb_vm_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the exadbVmCluster, run:

    $ gcloud oracle-database exadb-vm-clusters describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exadb-vm-clusters/describe)

---
### `gcloud oracle-database exadb-vm-clusters list`

List exadbVmClusters

**Synopsis:**
```
gcloud oracle-database exadb-vm-clusters list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all exadbVmClusters, run:

    $ gcloud oracle-database exadb-vm-clusters list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exadb-vm-clusters/list)

---
### `gcloud oracle-database exadb-vm-clusters remove-virtual-machine`

Remove exadbVmClusters

**Synopsis:**
```
gcloud oracle-database exadb-vm-clusters remove-virtual-machine
    (EXADB_VM_CLUSTER : --location=LOCATION) --hostnames=[HOSTNAMES,...]
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExadbVmCluster resource - The name of the ExadbVmCluster in the following
format:
projects/{project}/locations/{location}/exadbVmClusters/{exadb_vm_cluster}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exadb_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXADB_VM_CLUSTER
     ID of the exadbVmCluster or fully qualified identifier for the
     exadbVmCluster.

     To set the exadb_vm_cluster attribute:
     + provide the argument exadb_vm_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exadbVmCluster resource.

     To set the location attribute:
     + provide the argument exadb_vm_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hostnames` | [HOSTNAMES,...] |  | The list of host names of db nodes to be removed from the ExadbVmCluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To remove all exadbVmClusters, run:

    $ gcloud oracle-database exadb-vm-clusters remove-virtual-machine
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exadb-vm-clusters/remove-virtual-machine)

---
### `gcloud oracle-database exadb-vm-clusters update`

Update exadbVmClusters

Update an exadbVmCluster

**Synopsis:**
```
gcloud oracle-database exadb-vm-clusters update
    (EXADB_VM_CLUSTER : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID]
    [--clear-properties --properties-node-count=PROPERTIES_NODE_COUNT]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ExadbVmCluster resource - Identifier. The name of the ExadbVmCluster
resource in the following format:
projects/{project}/locations/{region}/exadbVmClusters/{exadb_vm_cluster}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument exadb_vm_cluster on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXADB_VM_CLUSTER
     ID of the exadbVmCluster or fully qualified identifier for the
     exadbVmCluster.

     To set the exadb_vm_cluster attribute:
     + provide the argument exadb_vm_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the exadbVmCluster resource.

     To set the location attribute:
     + provide the argument exadb_vm_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the exadbVmCluster, run:

    $ gcloud oracle-database exadb-vm-clusters update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/exadb-vm-clusters/update)

---
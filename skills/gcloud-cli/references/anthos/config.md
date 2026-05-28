# gcloud anthos config

anthos configuration command group


## `gcloud anthos config controller` — manage Anthos Config Controller instances
### `gcloud anthos config controller create`

Create Anthos Config Controller instances

Create an Anthos Config Controller instance.

**Synopsis:**
```
gcloud anthos config controller create (NAME : --location=LOCATION)
    [--async] [--cluster-ipv4-cidr-block=CLUSTER_IPV4_CIDR_BLOCK]
    [--cluster-named-range=CLUSTER_NAMED_RANGE] [--full-management]
    [--man-block=MAN_BLOCK] [--man-blocks=[BLOCK,...]]
    [--master-ipv4-cidr-block=MASTER_IPV4_CIDR_BLOCK] [--network=NETWORK]
    [--services-ipv4-cidr-block=SERVICES_IPV4_CIDR_BLOCK]
    [--services-named-range=SERVICES_NAMED_RANGE] [--subnet=SUBNET]
    [--use-private-endpoint] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The identifier for a Config Controller instance. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the instance or fully qualified identifier for the instance.

     To set the name attribute:
     + provide the argument name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the Config Controller instance location. Currently, only
     us-central1, us-east1, us-east4, us-east5, us-west2,
     northamerica-northeast1, northamerica-northeast2, europe-north1,
     europe-west1, europe-west3, europe-west6, australia-southeast1,
     australia-southeast2, asia-northeast1, asia-northeast2 and
     asia-southeast1 are supported.

     To set the location attribute:
     + provide the argument name on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster-ipv4-cidr-block` | CLUSTER_IPV4_CIDR_BLOCK |  | The IP address range for the cluster pod IPs. Can be specified as a netmask size (e.g. '/14') or as in CIDR notation (e.g. '10.100.0.0/20'). Defaults to '/20' if flag is not provided. |
| `--cluster-named-range` | CLUSTER_NAMED_RANGE |  | The name of the existing secondary range in the clusters subnetwork to use for pod IP addresses. Alternatively, --cluster_cidr_block can be used to automatically create a GKE-managed one. |
| `--full-management` |  |  | Enable full cluster management type. |
| `--man-block` | MAN_BLOCK |  | (DEPRECATED) Master Authorized Network. Allows access to the Kubernetes control plane from this block. Defaults to 0.0.0.0/0 if flag is not provided. The --man-block option is deprecated; use --man-blocks instead. |
| `--man-blocks` | [BLOCK,...] |  | Master Authorized Network. Allows users to specify multiple blocks to access the Kubernetescontrol plane from this block. Defaults to 0.0.0.0/0 if flag is not provided. |
| `--master-ipv4-cidr-block` | MASTER_IPV4_CIDR_BLOCK |  | The /28 network that the control plane will use. Defaults to '172.16.0.128/28' if flag is not provided. |
| `--network` | NETWORK |  | Existing VPC Network to put the GKE cluster and nodes in. Defaults to 'default' if flag is not provided. If --subnet=SUBNET is also specified, subnet must be a subnetwork of the network specified by this --network=NETWORK flag. |
| `--services-ipv4-cidr-block` | SERVICES_IPV4_CIDR_BLOCK |  | The IP address range for the cluster service IPs. Can be specified as a netmask size (e.g. '/14') or as in CIDR notation (e.g. '10.100.0.0/20'). Defaults to '/24' if flag is not provided. |
| `--services-named-range` | SERVICES_NAMED_RANGE |  | The name of the existing secondary range in the clusters subnetwork to use for service ClusterIPs. Alternatively, --services_cidr_block can be used to automatically create a GKE-managed one. |
| `--subnet` | SUBNET |  | Specifies the subnet that the VM instances are a part of. --network=NETWORK must also be specified, subnet must be a subnetwork of the network specified by the --network=NETWORK flag. |
| `--use-private-endpoint` |  |  | Only allow access to the master's private endpoint IP. |


**Examples:**
```bash
To create an Anthos Config Controller instance with the name acc-default,
run:

    $ gcloud anthos config controller create acc-default \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/controller/create)

---
### `gcloud anthos config controller delete`

Delete Anthos Config Controller instances

Delete an Anthos Config Controller instance.

**Synopsis:**
```
gcloud anthos config controller delete (NAME : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The identifier for an Anthos Config Controller
instance. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the instance or fully qualified identifier for the instance.

     To set the name attribute:
     + provide the argument name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the Anthos Config Controller instance location.
     Currently, only us-central1, us-east1, us-east4, us-east5, us-west2,
     northamerica-northeast1, northamerica-northeast2, europe-north1,
     europe-west1, europe-west3, europe-west6, australia-southeast1,
     australia-southeast2, asia-northeast1, asia-northeast2 and
     asia-southeast1 are supported.

     To set the location attribute:
     + provide the argument name on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an Anthos Config Controller instance, run:

    $ gcloud anthos config controller delete NAME --location=LOCATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/controller/delete)

---
### `gcloud anthos config controller describe`

Describe Anthos Config Controller instances

Describe an Anthos Config Controller instance.

**Synopsis:**
```
gcloud anthos config controller describe (NAME : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The identifier for an Anthos Config Controller
instance. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the instance or fully qualified identifier for the instance.

     To set the name attribute:
     + provide the argument name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the Anthos Config Controller instance location.
     Currently, only us-central1, us-east1, us-east4, us-east5, us-west2,
     northamerica-northeast1, northamerica-northeast2, europe-north1,
     europe-west1, europe-west3, europe-west6, australia-southeast1,
     australia-southeast2, asia-northeast1, asia-northeast2 and
     asia-southeast1 are supported.

     To set the location attribute:
     + provide the argument name on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an Anthos Config Controller instance named default in the
location us-central1, run:

    $ gcloud anthos config controller describe default \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/controller/describe)

---
### `gcloud anthos config controller get-config-connector-identity`

Fetch default Config Connector identity

gcloud anthos config controller get-config-connector-identity prints the
default Config Connector Google Service Account in a specific Anthos Config
Controller.

**Synopsis:**
```
gcloud anthos config controller get-config-connector-identity NAME
    --location=LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Anthos Config Controller.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location (region) of the Anthos Config Controller. |


**Examples:**
```bash
To print the default Config Connector identity used by your Config
Controller 'main' in the location 'us-central1', run:

    $ gcloud anthos config controller get-config-connector-identity \
        main --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/controller/get-config-connector-identity)

---
### `gcloud anthos config controller get-credentials`

Fetch credentials for a running Anthos Config Controller

gcloud anthos config controller get-credentials updates a kubeconfig file
with appropriate credentials and endpoint information to point kubectl at a
specific Anthos Config Controller.

**Synopsis:**
```
gcloud anthos config controller get-credentials NAME --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Anthos Config Controller.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location (region) of the Anthos Config Controller. |


**Examples:**
```bash
To switch to working on your Config Controller 'main', run:

    $ gcloud anthos config controller get-credentials main \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/controller/get-credentials)

---
### `gcloud anthos config controller list`

List Anthos Config Controller instances

List Anthos Config Controller instances.

**Synopsis:**
```
gcloud anthos config controller list [--full-name] [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full-name` |  |  | Print the fully specified name of the instance. |


**Examples:**
```bash
To list all Anthos Config Controller instances in the region 'us-central1',
run:

    $ gcloud anthos config controller list --location=us-central1

To list all Anthos Config Controller instances in all regions with their
fully specified name, run:

    $ gcloud anthos config controller list --full-name

To list all Anthos Config Controller instances in all regions, run:

    $ gcloud anthos config controller list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/controller/list)

---

## `gcloud anthos config operations` — get and list operations for Anthos Config Controller instances
### `gcloud anthos config operations describe`

Describe Anthos Config Controller operations

Describe an Anthos Config Controller operation.

**Synopsis:**
```
gcloud anthos config operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The identifier for an Anthos Config Controller
operation. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the Anthos Config Controller instance location.
     Currently, only us-central1, us-east1, us-east4, us-east5, us-west2,
     northamerica-northeast1, northamerica-northeast2, europe-north1,
     europe-west1, europe-west3, europe-west6, australia-southeast1,
     australia-southeast2, asia-northeast1, asia-northeast2 and
     asia-southeast1 are supported.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an Anthos Config Controller operation named my-operation in the
location us-central1, run:

    $ gcloud anthos config operations describe my-operation \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/operations/describe)

---
### `gcloud anthos config operations list`

List Anthos Config Controller operations

List Anthos Config Controller operations.

**Synopsis:**
```
gcloud anthos config operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the operation-list or fully qualified identifier for the operation-list. To set the location attribute: + provide the argument --location on the command line; + use global location. |


**Examples:**
```bash
To list all Anthos Config Controller operations in the region
'us-central1', run:

    $ gcloud anthos config operations list --location=us-central1

To list all Anthos Config Controller operations in all regions, run:

    $ gcloud anthos config operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/config/operations/list)

---
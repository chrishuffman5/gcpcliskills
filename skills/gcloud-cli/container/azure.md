# gcloud container azure

deploy and manage clusters of machines on Azure for running containers

### `gcloud container azure get-server-config`

Get Anthos Multi-Cloud server configuration for Azure

(DEPRECATED) Get Anthos Multi-Cloud server configuration for Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure get-server-config [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_azure/location. |


**Examples:**
```bash
To return supported Azure regions and valid versions in location us-west1,
run:

    $ gcloud container azure get-server-config --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/get-server-config)

---

## `gcloud container azure clients` — create and manage Azure clients
### `gcloud container azure clients create`

Create an Azure client

(DEPRECATED) Create an Azure client.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clients create (CLIENT : --location=LOCATION)
    --application-id=APP_ID --tenant-id=TENANT_ID [--async]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client resource - Azure client to create. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT
     ID of the client or fully qualified identifier for the client.

     To set the client attribute:
     + provide the argument client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the client.

     To set the location attribute:
     + provide the argument client on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-id` | APP_ID |  | Azure Active Directory (AAD) Application/Client ID (GUID). |
| `--tenant-id` | TENANT_ID |  | Azure Active Directory (AAD) tenant ID (GUID) to associate with the client. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--validate-only` |  |  | Validate the creation of the client, but don't actually perform it. |


**Examples:**
```bash
To create an Azure client named my-client in location us-west1, run:

    $ gcloud container azure clients create my-client \
        --location=us-west1 --application-id=APP_ID \
        --tenant-id=TENANT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clients/create)

---
### `gcloud container azure clients delete`

Delete an Azure client

(DEPRECATED) Delete an Azure client.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clients delete (CLIENT : --location=LOCATION)
    [--allow-missing] [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client resource - Azure client to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT
     ID of the client or fully qualified identifier for the client.

     To set the client attribute:
     + provide the argument client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the client.

     To set the location attribute:
     + provide the argument client on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of client. The request will still succeed in case the client does not exist. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an Azure client named my-client in location us-west1, run:

    $ gcloud container azure clients delete my-client --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clients/delete)

---
### `gcloud container azure clients describe`

Describe an Azure client

(DEPRECATED) Describe an Azure client.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clients describe (CLIENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client resource - Azure client to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT
     ID of the client or fully qualified identifier for the client.

     To set the client attribute:
     + provide the argument client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the client.

     To set the location attribute:
     + provide the argument client on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Examples:**
```bash
To describe an Azure client named my-client in location us-west1, run:

    $ gcloud container azure clients describe my-client \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clients/describe)

---
### `gcloud container azure clients get-public-cert`

Get the public certificate of an Azure client

(DEPRECATED) Get the public certificate of an Azure client.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clients get-public-cert
    (CLIENT : --location=LOCATION) [--output-file=OUTPUT_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Client resource - Azure client to get the public certificate. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLIENT
     ID of the client or fully qualified identifier for the client.

     To set the client attribute:
     + provide the argument client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the client.

     To set the location attribute:
     + provide the argument client on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | Path to the output file to store PEM. |


**Examples:**
```bash
To get the public certificate of an Azure client named my-client in
location us-west1, run:

    $ gcloud container azure clients get-public-cert my-client \
        --location=us-west1

To store the certificate in a file named client.crt, run:

    $ gcloud container azure clients get-public-cert my-client \
        --location=us-west1 --output-file=client.crt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clients/get-public-cert)

---
### `gcloud container azure clients list`

List Azure clients

(DEPRECATED) List Azure clients.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clients list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_azure/location. |


**Examples:**
```bash
To lists all clients in location us-west1, run:

    $ gcloud container azure clients list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clients/list)

---

## `gcloud container azure clusters` — create and manage Anthos clusters on Azure
### `gcloud container azure clusters create`

Create an Anthos cluster on Azure

(DEPRECATED) Create an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clusters create (CLUSTER : --location=LOCATION)
    --azure-region=AZURE_REGION --cluster-version=CLUSTER_VERSION
    --fleet-project=FLEET_PROJECT
    --pod-address-cidr-blocks=POD_ADDRESS_CIDR_BLOCKS
    --resource-group-id=RESOURCE_GROUP_ID
    --service-address-cidr-blocks=SERVICE_ADDRESS_CIDR_BLOCKS
    --ssh-public-key=SSH_PUBLIC_KEY --vnet-id=VNET_ID
    (--client=CLIENT | --azure-application-id=AZURE_APPLICATION_ID
      --azure-tenant-id=AZURE_TENANT_ID) [--admin-groups=[GROUP,...]]
    [--admin-users=USER,[USER,...]]
    [--annotations=ANNOTATION,[ANNOTATION,...]] [--async]
    [--config-encryption-key-id=CONFIG_ENCRYPTION_KEY_ID]
    [--config-encryption-public-key=CONFIG_ENCRYPTION_PUBLIC_KEY]
    [--database-encryption-key-id=DATABASE_ENCRYPTION_KEY_ID]
    [--description=DESCRIPTION] [--enable-managed-prometheus]
    [--endpoint-subnet-id=ENDPOINT_SUBNET_ID]
    [--logging=COMPONENT,[COMPONENT,...]]
    [--main-volume-size=MAIN_VOLUME_SIZE]
    [--replica-placements=[REPLICA_PLACEMENT,...]]
    [--root-volume-size=ROOT_VOLUME_SIZE]
    [--service-load-balancer-subnet-id=SERVICE_LOAD_BALANCER_SUBNET_ID]
    [--subnet-id=SUBNET_ID] [--tags=TAG,[TAG,...]] [--validate-only]
    [--vm-size=VM_SIZE]
    [--proxy-resource-group-id=PROXY_RESOURCE_GROUP_ID
      --proxy-secret-id=PROXY_SECRET_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Azure cluster to create. The arguments in this group
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--azure-region` | AZURE_REGION |  | Azure location to deploy the cluster. Refer to your Azure subscription for available locations. |
| `--cluster-version` | CLUSTER_VERSION |  | Kubernetes version to use for the cluster. |
| `--fleet-project` | FLEET_PROJECT |  | ID or number of the Fleet host project where the cluster is registered. |
| `--pod-address-cidr-blocks` | POD_ADDRESS_CIDR_BLOCKS |  | IP address range for the pods in this cluster in CIDR notation (e.g. 10.0.0.0/8). |
| `--resource-group-id` | RESOURCE_GROUP_ID |  | ID of the Azure Resource Group to associate the cluster with. |
| `--service-address-cidr-blocks` | SERVICE_ADDRESS_CIDR_BLOCKS |  | IP address range for the services IPs in CIDR notation (e.g. 10.0.0.0/8). |
| `--ssh-public-key` | SSH_PUBLIC_KEY |  | SSH public key to use for authentication. |
| `--vnet-id` | VNET_ID |  | ID of the Azure Virtual Network to associate with the cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-groups` | [GROUP,...] |  | Groups of users that can perform operations as a cluster administrator. |
| `--admin-users` | USER,[USER,...] |  | Users that can perform operations as a cluster administrator. If not specified, the value of property core/account is used. |
| `--annotations` | ANNOTATION,[ANNOTATION,...] |  | Annotations for the cluster. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--config-encryption-key-id` | CONFIG_ENCRYPTION_KEY_ID |  | URL the of the Azure Key Vault key (with its version) to use to encrypt / decrypt config data. |
| `--config-encryption-public-key` | CONFIG_ENCRYPTION_PUBLIC_KEY |  | RSA key of the Azure Key Vault public key to use for encrypting config data. |
| `--database-encryption-key-id` | DATABASE_ENCRYPTION_KEY_ID |  | URL the of the Azure Key Vault key (with its version) to use to encrypt / decrypt cluster secrets. |
| `--description` | DESCRIPTION |  | Description for the cluster. |
| `--enable-managed-prometheus` |  |  | Enables managed collection for Managed Service for Prometheus in the cluster. See https://cloud.google.com/stackdriver/docs/managed-prometheus/setup-managed#enable-mgdcoll-gke for more info. Managed Prometheus is enabled by default for cluster versions 1.27 or greater, use --no-enable-managed-prometheus to disable. |
| `--endpoint-subnet-id` | ENDPOINT_SUBNET_ID |  | ARM ID of the subnet where the control plane load balancer is deployed. When unspecified, it defaults to the control plane subnet ID. |
| `--logging` | one of: SYSTEM, WORKLOAD |  | Set the components that have logging enabled. Examples: $ gcloud container azure clusters create --logging=SYSTEM $ gcloud container azure clusters create --logging=SYSTEM,WORKLOAD COMPONENT must be one of: SYSTEM, WORKLOAD. |
| `--main-volume-size` | MAIN_VOLUME_SIZE |  | Size of the main volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--replica-placements` | [REPLICA_PLACEMENT,...] |  | Placement info for the control plane replicas. Replica placement is of format subnetid:zone, for example subnetid12345:1 |
| `--root-volume-size` | ROOT_VOLUME_SIZE |  | Size of the root volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--service-load-balancer-subnet-id` | SERVICE_LOAD_BALANCER_SUBNET_ID |  | ARM ID of the subnet where Kubernetes private service type load balancers are deployed, when the Service lacks a subnet annotation. |
| `--subnet-id` | SUBNET_ID |  | Subnet ID of an existing VNET to use for the cluster control plane. |
| `--tags` | TAG,[TAG,...] |  | Applies the given tags (comma separated) on the cluster. Example: $ gcloud container azure clusters create EXAMPLE_CLUSTER \ --tags=tag1=one,tag2=two |
| `--validate-only` |  |  | Validate the creation of the cluster, but don't actually perform it. |
| `--vm-size` | VM_SIZE |  | Azure Virtual Machine Size (e.g. Standard_DS1_v). |


**Examples:**
```bash
To create a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container azure clusters create my-cluster \
        --location=us-west1 --azure-region=AZURE_REGION \
        --cluster-version=CLUSTER_VERSION --client=CLIENT \
        --pod-address-cidr-blocks=POD_ADDRESS_CIDR_BLOCKS \
        --resource-group-id=RESOURCE_GROUP_ID \
        --ssh-public-key=SSH_PUBLIC_KEY --subnet-id=SUBNET_ID \
        --vnet-id=VNET_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clusters/create)

---
### `gcloud container azure clusters delete`

Delete an Anthos cluster on Azure

(DEPRECATED) Delete an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clusters delete (CLUSTER : --location=LOCATION)
    [--allow-missing] [--async] [--ignore-errors] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to delete. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of cluster. The request will still succeed in case the cluster does not exist. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | Force delete an Azure cluster. Deletion of the Azure cluster will succeed even if errors occur during deleting in-cluster resources. Using this parameter may result in orphaned resources in the cluster. |


**Examples:**
```bash
To delete a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container azure clusters delete my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clusters/delete)

---
### `gcloud container azure clusters describe`

Describe an Anthos cluster on Azure

(DEPRECATED) Describe an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clusters describe (CLUSTER : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Examples:**
```bash
To describe a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container azure clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clusters/describe)

---
### `gcloud container azure clusters get-credentials`

Get credentials of an Anthos cluster on Azure

(DEPRECATED) This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

Fetch credentials for a running Anthos cluster on Azure.

This command updates a kubeconfig file with appropriate credentials and
endpoint information to point kubectl at a specific Anthos cluster on
Azure.

By default, credentials are written to HOME/.kube/config. You can provide
an alternate path by setting the KUBECONFIG environment variable. If
KUBECONFIG contains multiple paths, the first one is used.

This command enables switching to a specific cluster, when working with
multiple clusters. It can also be used to access a previously created
cluster from a new workstation.

By default, the command will configure kubectl to automatically refresh its
credentials using the same identity as the gcloud command-line tool. If you
are running kubectl as part of an application, it is recommended to use
application default credentials
(https://cloud.google.com/docs/authentication/production). To configure a
kubeconfig file to use application default credentials, set the
container/use_application_default_credentials Google Cloud CLI property
(https://cloud.google.com/sdk/docs/properties) to true before running the
command.

See https://cloud.google.com/kubernetes-engine/docs/kubectl for kubectl
documentation.

**Synopsis:**
```
gcloud container azure clusters get-credentials
    (CLUSTER : --location=LOCATION) [--private-endpoint]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to get credentials. The arguments in this group
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-endpoint` |  |  | If set, use private VPC for authentication. |


**Examples:**
```bash
To get credentials of a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container azure clusters get-credentials my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clusters/get-credentials)

---
### `gcloud container azure clusters list`

List Anthos clusters on Azure

(DEPRECATED) List Anthos clusters on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_azure/location. |


**Examples:**
```bash
To lists all clusters managed in location us-west1, run:

    $ gcloud container azure clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clusters/list)

---
### `gcloud container azure clusters update`

Update an Anthos cluster on Azure

(DEPRECATED) Update an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure clusters update (CLUSTER : --location=LOCATION)
    [--admin-groups=[GROUP,...]] [--admin-users=USER,[USER,...]] [--async]
    [--cluster-version=CLUSTER_VERSION]
    [--logging=COMPONENT,[COMPONENT,...]] [--ssh-public-key=SSH_PUBLIC_KEY]
    [--validate-only] [--vm-size=VM_SIZE]
    [--annotations=ANNOTATION,[ANNOTATION,...] | --clear-annotations]
    [--clear-description | --description=DESCRIPTION]
    [--client=CLIENT | --azure-application-id=AZURE_APPLICATION_ID
      --azure-tenant-id=AZURE_TENANT_ID --clear-client]
    [--disable-managed-prometheus | --enable-managed-prometheus]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Azure cluster to update. The arguments in this group
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-groups` | [GROUP,...] |  | Groups of users that can perform operations as a cluster administrator. |
| `--admin-users` | USER,[USER,...] |  | Users that can perform operations as a cluster administrator. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster-version` | CLUSTER_VERSION |  | Kubernetes version to use for the cluster. |
| `--logging` | one of: SYSTEM, WORKLOAD |  | Set the components that have logging enabled. Examples: $ gcloud container azure clusters update --logging=SYSTEM $ gcloud container azure clusters update --logging=SYSTEM,WORKLOAD COMPONENT must be one of: SYSTEM, WORKLOAD. |
| `--ssh-public-key` | SSH_PUBLIC_KEY |  | SSH public key to use for authentication. |
| `--validate-only` |  |  | Validate the update of the cluster, but don't actually perform it. |
| `--vm-size` | VM_SIZE |  | Azure Virtual Machine Size (e.g. Standard_DS1_v). |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container azure clusters update my-cluster \
        --location=us-west1 --cluster-version=CLUSTER_VERSION \
        --client=CLIENT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/clusters/update)

---

## `gcloud container azure node-pools` — create and manage node pools in an Anthos cluster on Azure
### `gcloud container azure node-pools create`

Create a node pool in an Anthos cluster on Azure

(DEPRECATED) Create a node pool in an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure node-pools create
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    --max-pods-per-node=MAX_PODS_PER_NODE --node-version=NODE_VERSION
    --ssh-public-key=SSH_PUBLIC_KEY --subnet-id=SUBNET_ID
    (--max-nodes=MAX_NODES --min-nodes=MIN_NODES)
    [--annotations=ANNOTATION,[ANNOTATION,...]] [--async]
    [--azure-availability-zone=AZURE_AVAILABILITY_ZONE]
    [--config-encryption-key-id=CONFIG_ENCRYPTION_KEY_ID]
    [--config-encryption-public-key=CONFIG_ENCRYPTION_PUBLIC_KEY]
    [--enable-autorepair] [--node-labels=NODE_LABEL,[NODE_LABEL,...]]
    [--node-taints=NODE_TAINT,[NODE_TAINT,...]]
    [--root-volume-size=ROOT_VOLUME_SIZE] [--tags=TAG,[TAG,...]]
    [--validate-only] [--vm-size=VM_SIZE]
    [--proxy-resource-group-id=PROXY_RESOURCE_GROUP_ID
      --proxy-secret-id=PROXY_SECRET_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nodepool resource - node pool to create. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the nodepool or fully qualified identifier for the nodepool.

     To set the nodepool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the nodepool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the nodepool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-pods-per-node` | MAX_PODS_PER_NODE |  | Maximum number of pods per node. |
| `--node-version` | NODE_VERSION |  | Kubernetes version to use for the node pool. |
| `--ssh-public-key` | SSH_PUBLIC_KEY |  | SSH public key to use for authentication. |
| `--subnet-id` | SUBNET_ID |  | Subnet ID of an existing VNET to use for the node pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | ANNOTATION,[ANNOTATION,...] |  | Annotations for the node pool. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--azure-availability-zone` | AZURE_AVAILABILITY_ZONE |  | Azure availability zone where the node pool will be created. |
| `--config-encryption-key-id` | CONFIG_ENCRYPTION_KEY_ID |  | URL the of the Azure Key Vault key (with its version) to use to encrypt / decrypt config data. |
| `--config-encryption-public-key` | CONFIG_ENCRYPTION_PUBLIC_KEY |  | RSA key of the Azure Key Vault public key to use for encrypting config data. |
| `--enable-autorepair` |  |  | Enable node autorepair feature for a node pool. Use --no-enable-autorepair to disable. $ gcloud container azure node-pools create --enable-autorepair Node autorepair is disabled by default. |
| `--node-labels` | NODE_LABEL,[NODE_LABEL,...] |  | Labels assigned to the node pool's nodes. |
| `--node-taints` | one of: NoExecute, NoSchedule, PreferNoSchedule |  | Taints assigned to nodes of the node pool. Node taint is of format key=value:effect. Effect must be one of: NoExecute, NoSchedule, PreferNoSchedule. |
| `--root-volume-size` | ROOT_VOLUME_SIZE |  | Size of the root volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--tags` | TAG,[TAG,...] |  | Applies the given tags (comma separated) on the node pool. Example: $ gcloud container azure node-pools create EXAMPLE_NODE_POOL \ --tags=tag1=one,tag2=two |
| `--validate-only` |  |  | Validate the creation of the node pool, but don't actually perform it. |
| `--vm-size` | VM_SIZE |  | Azure Virtual Machine Size (e.g. Standard_DS1_v). |


**Examples:**
```bash
To create a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container azure node-pools create my-node-pool \
        --cluster=my-cluster --location=us-west1 \
        --node-version=NODE_VERSION --ssh-public-key=SSH_PUBLIC_KEY \
        --subnet-id=SUBNET_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/node-pools/create)

---
### `gcloud container azure node-pools delete`

Delete a node pool in an Anthos cluster on Azure

(DEPRECATED) Delete a node pool in an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure node-pools delete
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--allow-missing]
    [--async] [--ignore-errors] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nodepool resource - node pool to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the nodepool or fully qualified identifier for the nodepool.

     To set the nodepool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the nodepool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the nodepool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of node pool. The request will still succeed in case the node pool does not exist. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | Force delete an Azure node pool. Deletion of the Azure node pool will succeed even if errors occur during deleting in-node pool resources. Using this parameter may result in orphaned resources in the node pool. |


**Examples:**
```bash
To delete a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container azure node-pools delete my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/node-pools/delete)

---
### `gcloud container azure node-pools describe`

Describe a node pool in an Anthos cluster on Azure

(DEPRECATED) Describe a node pool in an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure node-pools describe
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nodepool resource - node pool to describe. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the nodepool or fully qualified identifier for the nodepool.

     To set the nodepool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the nodepool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the nodepool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Examples:**
```bash
To describe a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container azure node-pools describe my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/node-pools/describe)

---
### `gcloud container azure node-pools list`

List node pools in an Anthos cluster on Azure

(DEPRECATED) List node pools in an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure node-pools list
    (--cluster=CLUSTER : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location for the cluster. To set the location attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --location on the command line; + set the property container_azure/location. |


**Examples:**
```bash
To list all node pools in a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container azure node-pools list --cluster=my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/node-pools/list)

---
### `gcloud container azure node-pools update`

Update a node pool in an Anthos cluster on Azure

(DEPRECATED) Update a node pool in an Anthos cluster on Azure.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure node-pools update
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [--enable-autorepair] [--node-version=NODE_VERSION]
    [--ssh-public-key=SSH_PUBLIC_KEY] [--validate-only]
    [--annotations=ANNOTATION,[ANNOTATION,...] | --clear-annotations]
    [--max-nodes=MAX_NODES --min-nodes=MIN_NODES] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Nodepool resource - node pool to update. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the nodepool or fully qualified identifier for the nodepool.

     To set the nodepool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the nodepool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the nodepool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-autorepair` |  |  | Enable node autorepair feature for a node pool. Use --no-enable-autorepair to disable. $ gcloud container azure node-pools update --enable-autorepair |
| `--node-version` | NODE_VERSION |  | Kubernetes version to use for the node pool. |
| `--ssh-public-key` | SSH_PUBLIC_KEY |  | SSH public key to use for authentication. |
| `--validate-only` |  |  | Validate the update of the node pool, but don't actually perform it. |


**Examples:**
```bash
To update a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container azure node-pools update my-node-pool \
        --cluster=my-cluster --location=us-west1 \
        --node-version=NODE_VERSION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/node-pools/update)

---

## `gcloud container azure operations` — manage Anthos Multi-Cloud long running operations for Azure
### `gcloud container azure operations cancel`

Cancel an operation

(DEPRECATED) Cancel an operation.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure operations cancel
    (OPERATION_ID : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to cancel. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION_ID
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation_id on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Examples:**
```bash
To cancel an operation in location us-west1, run:

    $ gcloud container azure operations cancel OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/operations/cancel)

---
### `gcloud container azure operations describe`

Describe an operation

(DEPRECATED) Describe an operation.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure operations describe
    (OPERATION_ID : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION_ID
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation_id on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Examples:**
```bash
To describe an operation in location us-west1, run:

    $ gcloud container azure operations describe OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/operations/describe)

---
### `gcloud container azure operations list`

List operations

(DEPRECATED) List operations.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_azure/location. |


**Examples:**
```bash
To list all operations in location us-west1, run:

    $ gcloud container azure operations list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/operations/list)

---
### `gcloud container azure operations wait`

Wait for an operation to complete

(DEPRECATED) Wait for an operation to complete.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/azure/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container azure operations wait (OPERATION_ID : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to wait for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION_ID
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation_id on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_azure/location.
```

**Examples:**
```bash
To wait for an operation in location us-west1 to complete, run:

    $ gcloud container azure operations wait OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/azure/operations/wait)

---
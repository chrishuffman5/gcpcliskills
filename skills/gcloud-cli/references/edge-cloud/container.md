# gcloud edge-cloud container

manage Edge Container resources

### `gcloud edge-cloud container get-server-config`

Get server config

gcloud edge-cloud container get-server-config gets the server configuration
for an Edge Container location. This configuration includes the default
cluster version, the supported cluster versions and version configuration
for each release channel.

**Synopsis:**
```
gcloud edge-cloud container get-server-config [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property edge_container/location. |


**Examples:**
```bash
To get server config in region us-central1, run:

    $ gcloud edge-cloud container get-server-config \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/get-server-config)

---

## `gcloud edge-cloud container clusters` — manage Kubernetes Edge clusters
### `gcloud edge-cloud container clusters create`

Create an Edge Container cluster

Create an Edge Container cluster.

**Synopsis:**
```
gcloud edge-cloud container clusters create (CLUSTER : --location=LOCATION)
    [--admin-users=ADMIN_USERS] [--async]
    [--cluster-ipv4-cidr=CLUSTER_IPV4_CIDR; default="10.0.0.0/17"]
    [--container-default-runtime-class=CONTAINER_DEFAULT_RUNTIME_CLASS]
    [--control-plane-kms-key=CONTROL_PLANE_KMS_KEY]
    [--control-plane-machine-filter=CONTROL_PLANE_MACHINE_FILTER]
    [--control-plane-node-count=CONTROL_PLANE_NODE_COUNT]
    [--control-plane-node-location=CONTROL_PLANE_NODE_LOCATION]
    [--control-plane-node-storage-schema=CONTROL_PLANE_NODE_STORAGE_SCHEMA]
    [--control-plane-shared-deployment-policy=CONTROL_PLANE_SHARED_DEPLOYMENT_POLICY]
    [--default-max-pods-per-node=DEFAULT_MAX_PODS_PER_NODE]
    [--enable-google-group-authentication]
    [--external-lb-ipv4-address-pools=[EXTERNAL_LB_IPV4_ADDRESS,...]]
    [--fleet-project=FLEET_PROJECT] [--labels=[KEY=VALUE,...]]
    [--lro-timeout=LRO_TIMEOUT]
    [--maintenance-window-end=MAINTENANCE_WINDOW_END]
    [--maintenance-window-recurrence=MAINTENANCE_WINDOW_RECURRENCE]
    [--maintenance-window-start=MAINTENANCE_WINDOW_START]
    [--offline-reboot-ttl=OFFLINE_REBOOT_TTL]
    [--release-channel=RELEASE_CHANNEL;
      default="RELEASE_CHANNEL_UNSPECIFIED"]
    [--services-ipv4-cidr=SERVICES_IPV4_CIDR; default="10.96.0.0/12"]
    [--system-addons-config=SYSTEM_ADDONS_CONFIG] [--version=VERSION]
    [--zone-storage-kms-key=ZONE_STORAGE_KMS_KEY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Edge Container cluster to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
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
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-users` | ADMIN_USERS |  | Username (Google email address) of the user who should be granted cluster-admin initially. This currently supports exactly one admin. If not set, the account issuing the creation request will be used by default. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster-ipv4-cidr` | CLUSTER_IPV4_CIDR | 10.0.0.0/17 | All pods in the cluster are assigned an RFC1918 IPv4 address from this block. This field cannot be changed after creation. |
| `--container-default-runtime-class` | CONTAINER_DEFAULT_RUNTIME_CLASS |  | Name of the default runtime class for containers. It supports two values RUNC and GVISOR. |
| `--control-plane-kms-key` | CONTROL_PLANE_KMS_KEY |  | Google Cloud KMS key that will be used to secure persistent disks of the control plane VMs of a remote control plane cluster. The Edge Container service account for this project must have roles/cloudkms.cryptoKeyEncrypterDecrypter on the key. If not provided, a Google-managed key will be used by default. |
| `--control-plane-machine-filter` | CONTROL_PLANE_MACHINE_FILTER |  | Only machines matching this filter will be allowed to host local control plane nodes. The filtering language accepts strings like "name=<name>", and is documented here: AIP-160 (https://google.aip.dev/160). |
| `--control-plane-node-count` | CONTROL_PLANE_NODE_COUNT |  | The number of local control plane nodes in a cluster. Use one to create a single-node control plane or use three to create a high availability control plane. Any other numbers of nodes will not be accepted. |
| `--control-plane-node-location` | CONTROL_PLANE_NODE_LOCATION |  | Google Edge Cloud zone where the local control plane nodes will be created. |
| `--control-plane-node-storage-schema` | CONTROL_PLANE_NODE_STORAGE_SCHEMA |  | Name for the storage schema of control plane nodes. |
| `--control-plane-shared-deployment-policy` | CONTROL_PLANE_SHARED_DEPLOYMENT_POLICY |  | Policy configuration about how user application is deployed for local control plane cluster. It supports two values, ALLOWED and DISALLOWED. ALLOWED means that user application can be deployed on control plane nodes. DISALLOWED means that user application can not be deployed on control plane nodes. Instead, it can only be deployed on worker nodes. By default, this value is DISALLOWED. The input is case insensitive. |
| `--default-max-pods-per-node` | DEFAULT_MAX_PODS_PER_NODE |  | The default maximum number of pods per node. |
| `--enable-google-group-authentication` |  |  | If set, the cluster will be configured to use Google Group authentication. |
| `--external-lb-ipv4-address-pools` | [EXTERNAL_LB_IPV4_ADDRESS,...] |  | IPv4 address pools that are used for data plane load balancing of local control plane clusters. Existing pools cannot be updated after cluster creation; only adding new pools is allowed. Each address pool must be specified as one of the following two types of values: 1. A IPv4 address range, for example, "10.0.0.1-10.0.0.10". A range that contains a single IP (e.g. "10.0.0.1-10.0.0.1") is allowed. 2. A IPv4 CIDR block, for example, "10.0.0.1/24" Use comma when specifying multiple address pools, for example: --external-lb-ipv4-address-pools 10.0.0.1-10.0.0.10,10.0.0.1/24 |
| `--fleet-project` | FLEET_PROJECT |  | Name of the Fleet host project where the cluster is registered. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--lro-timeout` | LRO_TIMEOUT |  | Overwrite the default LRO maximum timeout. |
| `--maintenance-window-end` | MAINTENANCE_WINDOW_END |  | End time of the recurring cluster maintenance window in the RFC 3339 (https://www.rfc-editor.org/rfc/rfc3339.txt) format. E.g. "2021-01-01T00:00:00Z" or "2021-01-01T00:00:00-05:00" |
| `--maintenance-window-recurrence` | MAINTENANCE_WINDOW_RECURRENCE |  | An RFC 5545 (https://tools.ietf.org/html/rfc5545#section-3.8.5.3) recurrence rule for how the cluster maintenance window recurs. They go on for the span of time between the start and the end time. E.g. FREQ=WEEKLY;BYDAY=SU. |
| `--maintenance-window-start` | MAINTENANCE_WINDOW_START |  | Start time of the recurring cluster maintenance window in the RFC 3339 (https://www.rfc-editor.org/rfc/rfc3339.txt) format. E.g. "2021-01-01T00:00:00Z" or "2021-01-01T00:00:00-05:00" |
| `--offline-reboot-ttl` | OFFLINE_REBOOT_TTL |  | Specifies the maximum duration a node can reboot offline (without connection to Google) and then rejoin its cluster to resume its designated workloads. This duration is relative to the machine's most recent connection to Google. The maximum allowed duration is 7 days. To disallow offline reboot, set the duration to "PT0S". The parameter should be an ISO 8601 duration string, for example, "P1DT1H2M3S". |
| `--release-channel` | RELEASE_CHANNEL | RELEASE_CHANNEL_UNSPECIFIED | Release channel a cluster is subscribed to. It supports two values, NONE and REGULAR. NONE is used to opt out of any release channel. Clusters subscribed to the REGULAR channel will be automatically upgraded to versions that are considered GA quality, and cannot be manually upgraded. Additionally, if the REGULAR channel is used, a specific target version cannot be set with the 'version' flag. If left unspecified, the release channel will default to REGULAR. |
| `--services-ipv4-cidr` | SERVICES_IPV4_CIDR | 10.96.0.0/12 | All services in the cluster are assigned an RFC1918 IPv4 address from this block. This field cannot be changed after creation. |
| `--system-addons-config` | SYSTEM_ADDONS_CONFIG |  | If specified as a YAML/JSON file, customized configuration in this file will be applied to the system add-ons. For example, { "systemAddonsConfig": { "ingress": { "disabled": true, "ipv4_vip": "10.0.0.1" } } } |
| `--version` | VERSION |  | Target cluster version. For example: "1.5.0". |
| `--zone-storage-kms-key` | ZONE_STORAGE_KMS_KEY |  | Google Cloud KMS key that will be used to encrypt and decrypt the root key for zone storage encryption. The zone storage KMS key is only applicable to the storage infra cluster. The Edge Container service account for this project must have roles/cloudkms.cryptoKeyEncrypterDecrypter on the key. If not provided, a Google-managed key will be used by default. |


**Examples:**
```bash
To create a cluster called my-cluster in region us-central1, run:

    $ gcloud edge-cloud container clusters create my-cluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/create)

---
### `gcloud edge-cloud container clusters delete`

Delete an Edge Container cluster

Delete an Edge Container cluster.

**Synopsis:**
```
gcloud edge-cloud container clusters delete (CLUSTER : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Edge Container cluster to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
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
     The global location name.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a cluster called 'my-cluster' in region us-central1, run:

    $ gcloud edge-cloud container clusters delete my-cluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/delete)

---
### `gcloud edge-cloud container clusters describe`

Show details about the cluster

Show details about the cluster.

**Synopsis:**
```
gcloud edge-cloud container clusters describe
    (CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The cluster you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
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
     The global location name.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To show details about a cluster called 'my-cluster' in region us-central1,
run:

    $ gcloud edge-cloud container clusters describe my-cluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/describe)

---
### `gcloud edge-cloud container clusters get-credentials`

Get credentials of an edge-container cluster

Fetch credentials for a running Edge Container cluster. This command
updates a kubeconfig file with appropriate credentials and endpoint
information to point kubectl at a specific Edge Container cluster. By
default, credentials are written to HOME/.kube/config. You can provide an
alternate path by setting the KUBECONFIG environment variable. If
KUBECONFIG contains multiple paths, the first one is used. This command
enables switching to a specific cluster, when working with multiple
clusters. It can also be used to access a previously created cluster from a
new workstation. The command will configure kubectl to automatically
refresh its credentials using the same identity as the gcloud command-line
tool. See https://cloud.google.com/kubernetes-engine/docs/kubectl for
kubectl documentation.

**Synopsis:**
```
gcloud edge-cloud container clusters get-credentials
    (CLUSTER : --location=LOCATION)
    [--auth-provider-cmd-path=AUTH_PROVIDER_CMD_PATH]
    [--offline-credential] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Edge Container cluster to get credentials. The
arguments in this group can be used to specify the attributes of this
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auth-provider-cmd-path` | AUTH_PROVIDER_CMD_PATH |  | Path to the gcloud executable for the auth provider field in kubeconfig. |
| `--offline-credential` |  |  | Once specified, an offline credential will be generated for the cluster. |


**Examples:**
```bash
To get credentials of a cluster named my-cluster managed in location
us-west1, run:        $ gcloud edge-cloud container clusters get-credentials my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/get-credentials)

---
### `gcloud edge-cloud container clusters list`

List Edge Container clusters

List Edge Container clusters.

**Synopsis:**
```
gcloud edge-cloud container clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property edge_container/location. |


**Examples:**
```bash
To list the clusters in region us-central1, run:

    $ gcloud edge-cloud container clusters list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/list)

---
### `gcloud edge-cloud container clusters update`

Update an Edge Container cluster

Update an Edge Container cluster.

**Synopsis:**
```
gcloud edge-cloud container clusters update (CLUSTER : --location=LOCATION)
    [--async]
    [--container-default-runtime-class=CONTAINER_DEFAULT_RUNTIME_CLASS]
    [--offline-reboot-ttl=OFFLINE_REBOOT_TTL]
    [--release-channel=RELEASE_CHANNEL]
    [--clear-maintenance-window
      | --remove-maintenance-exclusion-window=REMOVE_MAINTENANCE_EXCLUSION_WINDOW | --add-maintenance-exclusion-end=ADD_MAINTENANCE_EXCLUSION_END --add-maintenance-exclusion-name=ADD_MAINTENANCE_EXCLUSION_NAME --add-maintenance-exclusion-start=ADD_MAINTENANCE_EXCLUSION_START | --maintenance-window-end=MAINTENANCE_WINDOW_END --maintenance-window-recurrence=MAINTENANCE_WINDOW_RECURRENCE --maintenance-window-start=MAINTENANCE_WINDOW_START]
    [--control-plane-kms-key=CONTROL_PLANE_KMS_KEY
      | --use-google-managed-key]
    [--use-google-managed-zone-key
      | --zone-storage-kms-key=ZONE_STORAGE_KMS_KEY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Edge Container cluster to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
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
     The global location name.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--container-default-runtime-class` | CONTAINER_DEFAULT_RUNTIME_CLASS |  | If set, use the specified default container runtime class for the cluster. |
| `--offline-reboot-ttl` | OFFLINE_REBOOT_TTL |  | Specifies the maximum duration a node can reboot offline (without connection to Google) and then rejoin its cluster to resume its designated workloads. This duration is relative to the machine's most recent connection to Google. The maximum allowed duration is 7 days. If left unspecified, the default 0 means not allowed. The parameter should be an ISO 8601 duration string, for example, "P1DT1H2M3S". |
| `--release-channel` | one of: none, regular, release-channel-unspecified |  | Release channel a cluster is subscribed to. It supports two values, NONE and REGULAR. NONE is used to opt out of any release channel. Clusters subscribed to the REGULAR channel will be automatically upgraded to versions that are considered GA quality, and cannot be manually upgraded. RELEASE_CHANNEL must be one of: none, regular, release-channel-unspecified. |


**Examples:**
```bash
To update the maintenance window recurrence rule of a cluster called
'my-cluster' in region us-central1, run:

    $ gcloud edge-cloud container clusters update my-cluster \
        --location=us-central1 \
        --maintenance-window-recurrence="FREQ=WEEKLY"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/update)

---
### `gcloud edge-cloud container clusters upgrade`

Upgrade an Edge Container cluster

Upgrade an Edge Container cluster.

**Synopsis:**
```
gcloud edge-cloud container clusters upgrade
    (CLUSTER : --location=LOCATION) --schedule=SCHEDULE --version=VERSION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Edge Container cluster to upgrade. The arguments in
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

  --location=LOCATION
     Google Cloud location for the cluster.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--schedule` | SCHEDULE |  | Schedule to upgrade a cluster after the request is acknowledged by Google. Support values: IMMEDIATELY. |
| `--version` | VERSION |  | Target cluster version to upgrade to. For example: "1.5.1". |


**Examples:**
```bash
To upgrade an Edge Container cluster to 1.5.1 immediately, run:

    $ gcloud edge-cloud container clusters upgrade my-cluster \
        --version=1.5.1 --schedule=IMMEDIATELY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/upgrade)

---

## `gcloud edge-cloud container clusters node-pools` — manage Kubernetes Edge node pools
### `gcloud edge-cloud container clusters node-pools create`

Create an Edge Container node pool

Create an Edge Container node pool.

**Synopsis:**
```
gcloud edge-cloud container clusters node-pools create
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    --node-count=NODE_COUNT --node-location=NODE_LOCATION [--async]
    [--labels=[KEY=VALUE,...]] [--local-disk-kms-key=LOCAL_DISK_KMS_KEY]
    [--lro-timeout=LRO_TIMEOUT] [--machine-filter=MACHINE_FILTER]
    [--node-labels=[KEY=VALUE,...]]
    [--node-storage-schema=NODE_STORAGE_SCHEMA] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - Edge Container node pool to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node pool or fully qualified identifier for the node pool.

     To set the nodePool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     Cluster of the node pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-count` | NODE_COUNT |  | Default nodeCount used by this node pool. |
| `--node-location` | NODE_LOCATION |  | Google Edge Cloud zone where nodes in this node pool will be created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--local-disk-kms-key` | LOCAL_DISK_KMS_KEY |  | Google Cloud KMS key that will be used to secure local disks on nodes in this node pool. The Edge Container service account for this project must have roles/cloudkms.cryptoKeyEncrypterDecrypter on the key. If not provided, a Google-managed key will be used instead. |
| `--lro-timeout` | LRO_TIMEOUT |  | Overwrite the default LRO maximum timeout. |
| `--machine-filter` | MACHINE_FILTER |  | Only machines matching this filter will be allowed to join the node pool. The filtering language accepts strings like "name=<name>", and is documented in more detail at https://google.aip.dev/160. |
| `--node-labels` | [KEY=VALUE,...] |  | Comma-delimited list of key-value pairs that comprise labels for the individual nodes in the node pool. This flag sets the Kubernetes labels, unlike --labels which sets the cloud resource labels. |
| `--node-storage-schema` | NODE_STORAGE_SCHEMA |  | Name for the storage schema of worker nodes. |


**Examples:**
```bash
To create a node pool called my-nodePool, containing 3 nodes in region
us-central1, run:

    $ gcloud edge-cloud container clusters node-pools create \
        my-nodePool --cluster=<my-cluster> --location=us-central1 \
        --node-location=<my-node-location> --node-count=3

To create a node pool called my-nodePool, containing 3 nodes in region
us-central1, using only machine names matching a specific pattern, run:

    $ gcloud edge-cloud container clusters node-pools create \
        my-nodePool --cluster=<my-cluster> --location=us-central1 \
        --node-location=<my-node-location> --node-count=3 \
        --machine-filter="name:<name>"

To create a node pool called my-nodePool, containing 3 nodes in region
us-central1, using only machine names NOT matching a specific pattern, run:

    $ gcloud edge-cloud container clusters node-pools create \
        my-nodePool --cluster=<my-cluster> --location=us-central1 \
        --node-location=<my-node-location> --node-count=3 \
        --machine-filter="NOT name:<name>"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/node-pools/create)

---
### `gcloud edge-cloud container clusters node-pools delete`

Delete an Edge Container nodePool

Delete an Edge Container nodePool.

**Synopsis:**
```
gcloud edge-cloud container clusters node-pools delete
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - Edge Container nodePool to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node pool or fully qualified identifier for the node pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     Kubernetes cluster.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a nodePool called 'my-nodePool' in region us-central1, run:

    $ gcloud edge-cloud container clusters node-pools delete \
        my-nodePool --cluster=<my-cluster> --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/node-pools/delete)

---
### `gcloud edge-cloud container clusters node-pools describe`

Show details about the nodePool

Show details about the nodePool.

**Synopsis:**
```
gcloud edge-cloud container clusters node-pools describe
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - The nodePool you want to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node pool or fully qualified identifier for the node pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     Kubernetes cluster.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To show details about a node pool called 'my-nodePool' in region
us-central1, run:

    $ gcloud edge-cloud container clusters node-pools describe \
        my-nodePool --location=us-central1 --cluster=<my-cluster>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/node-pools/describe)

---
### `gcloud edge-cloud container clusters node-pools list`

List Edge Container nodePools

List Edge Container nodePools.

**Synopsis:**
```
gcloud edge-cloud container clusters node-pools list
    [--cluster=CLUSTER --location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[* set the property core/project.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line; + provide the argument --cluster on the command line. |
| `--location` | LOCATION |  | _[* set the property core/project.]_ The global location name. To set the location attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --cluster on the command line with a fully specified name; + provide the argument --location on the command line; + set the property edge_container/location. |


**Examples:**
```bash
To list the nodePools in region us-central1, run:

    $ gcloud edge-cloud container clusters node-pools list \
        --location=us-central1 --cluster=<my-cluster>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/node-pools/list)

---
### `gcloud edge-cloud container clusters node-pools update`

Updates an Edge Container node pool

Updates an Edge Container node pool.

**Synopsis:**
```
gcloud edge-cloud container clusters node-pools update
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [--local-disk-kms-key=LOCAL_DISK_KMS_KEY] [--lro-timeout=LRO_TIMEOUT]
    [--machine-filter=MACHINE_FILTER] [--node-count=NODE_COUNT]
    [--node-labels=[KEY=VALUE,...]] [--update-labels=[KEY=VALUE,...]]
    [--use-google-managed-key] [--clear-labels | --remove-labels=[KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - Edge Container node pool to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node pool or fully qualified identifier for the node pool.

     To set the nodePool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     Cluster of the node pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--local-disk-kms-key` | LOCAL_DISK_KMS_KEY |  | Google Cloud KMS key that will be used to secure local disks on nodes in this node pool. The Edge Container service account for this project must have roles/cloudkms.cryptoKeyEncrypterDecrypter on the key. If not provided, a Google-managed key will be used instead. |
| `--lro-timeout` | LRO_TIMEOUT |  | Overwrite the default LRO maximum timeout. |
| `--machine-filter` | MACHINE_FILTER |  | Only machines matching this filter will be allowed to join the node pool. The filtering language accepts strings like "name=<name>", and is documented in more detail at https://google.aip.dev/160. |
| `--node-count` | NODE_COUNT |  | Default nodeCount used by this node pool. |
| `--node-labels` | [KEY=VALUE,...] |  | Comma-delimited list of key-value pairs that comprise labels for the individual nodes in the node pool. This flag updates the Kubernetes labels, unlike --update-labels, --remove-labels, and --clear-labels which update the cloud resource labels. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--use-google-managed-key` |  |  | Once specified, a Google-managed key will be used for the control plane disk encryption. |


**Examples:**
```bash
To update the number of nodes in a node pool called my-node-pool in region
us-central1, run:

    $ gcloud edge-cloud container clusters node-pools update \
        my-node-pool --location=us-central1 --cluster=<my-cluster> \
        --node-count=<new-count>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/node-pools/update)

---

## `gcloud edge-cloud container machines` — manage Kubernetes Edge machines
### `gcloud edge-cloud container machines describe`

Show details about the machine

Show details about the machine.

**Synopsis:**
```
gcloud edge-cloud container machines describe
    (MACHINE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Machine resource - The machine you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument machine on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MACHINE
     ID of the machine or fully qualified identifier for the machine.

     To set the machine attribute:
     + provide the argument machine on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument machine on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To show details about a machine called 'my-machine' in region us-central1,
run:

    $ gcloud edge-cloud container machines describe my-machine \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/machines/describe)

---
### `gcloud edge-cloud container machines list`

List Edge Container machines

List Edge Container machines.

**Synopsis:**
```
gcloud edge-cloud container machines list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property edge_container/location. |


**Examples:**
```bash
To list the machines in region us-central1, run:

    $ gcloud edge-cloud container machines list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/machines/list)

---

## `gcloud edge-cloud container operations` — command group for working with Kubernetes Edge operations
### `gcloud edge-cloud container operations describe`

Get description of a long-running edge container operation

Get information about a long-running edge container operation.

**Synopsis:**
```
gcloud edge-cloud container operations describe
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
     The global location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To get information about a long-running operation with name
'projects/my-project/locations/us-east1/operations/123', run the following
command:

    $ gcloud edge-cloud container operations describe \
        projects/my-project/locations/us-east1/operations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/operations/describe)

---
### `gcloud edge-cloud container operations wait`

Poll long-running edge container operation until it completes

Poll a long-running edge container operation until it completes. When the
operation is complete, this command will display the results of the
analysis.

**Synopsis:**
```
gcloud edge-cloud container operations wait
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - ID for the operation to poll until complete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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
     The global location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To poll a long-running edge container operation named
'projects/my-project/locations/us-east1/operations/123' until it completes,
run the following:

    $ gcloud edge-cloud container operations wait \
        projects/my-project/locations/us-east1/operations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/operations/wait)

---

## `gcloud edge-cloud container regions` — manages Edge Container regions
### `gcloud edge-cloud container regions describe`

Describe an Edge Container region (location)

Describe an Edge Container region (location).

**Synopsis:**
```
gcloud edge-cloud container regions describe [LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The region to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument location on the command line with a fully
   specified name;
 * set the property edge_container/location with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [LOCATION]
     ID of the location or fully qualified identifier for the location.

     To set the location attribute:
     + provide the argument location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To display the metadata for the region us-central1, run:

    $ gcloud edge-cloud container regions describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/regions/describe)

---
### `gcloud edge-cloud container regions list`

List Edge Container regions

List all regions (locations) where Edge Container clusters can be created.

**Synopsis:**
```
gcloud edge-cloud container regions list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the regions (locations) where Edge Container clusters can be
created, run:

    $ gcloud edge-cloud container regions list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/regions/list)

---

## `gcloud edge-cloud container vpn-connections` — manage Edge VPN connections between an Edge Container cluster and a VPC network
### `gcloud edge-cloud container vpn-connections create`

Create a VPN connection between an Edge Container cluster and a VPC network

Creates a new VPN connection.

**Synopsis:**
```
gcloud edge-cloud container vpn-connections create VPN_CONNECTION
    --cluster=CLUSTER --vpc-network=VPC_NETWORK [--async]
    [--high-availability] [--labels=[KEY=VALUE,...]] [--location=LOCATION]
    [--nat-gateway-ip=NAT_GATEWAY_IP] [--router=ROUTER]
    [--vpc-project=VPC_PROJECT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Vpn connection resource - VPN connection to create. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument vpn_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument vpn_connection on the command line with a fully
   specified name;
 * provide the argument --location on the command line;
 * set the property edge_container/location.

This must be specified.

  VPN_CONNECTION
     ID of the vpn connection or fully qualified identifier for the vpn
     connection.

     To set the vpn_connection attribute:
     + provide the argument vpn_connection on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. |
| `--vpc-network` | VPC_NETWORK |  | _[This must be specified.]_ The name of the VPC network to be connected. By default it is assumed to be under the same project as cluster. If this VPC network is under a different project, vpc-project is required. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--high-availability` |  |  | Enables high availability on cluster side. This creates an additional VPN endpoint in cluster. Multiple Nodes/NodePools are required to enable this feature. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--location` | LOCATION |  | For resources [cluster, vpn_connection], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--nat-gateway-ip` | NAT_GATEWAY_IP |  | The NAT gateway IP for the gateway floating IPs. Required if cluster sits behind NAT. |
| `--router` | ROUTER |  | Name of the Cloud Router to use when creating the VPN connection. This Cloud Router must be in the same region as the cluster and connected to the provided VPC network. If not provided, a service-managed Cloud Router will either be created or reused to create the VPN connection. |
| `--vpc-project` | VPC_PROJECT |  | The project of the VPC network. Required if the project of VPC network differs from the project of the cluster. |


**Examples:**
```bash
To create a connection called 'my-vpn-connection' between the VPC network
'my-vpc' and the Edge Container cluster 'my-cluster' which is at region
us-central1, run:

    $ gcloud edge-cloud container vpn-connections create \
        my-vpn-connection --location=us-central1 \
        --vpc-network='my-vpc' --cluster='my-cluster'

Here VPC network and cluster should be under the same project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/vpn-connections/create)

---
### `gcloud edge-cloud container vpn-connections delete`

Delete a VPN connection between an Edge Container cluster and a VPC network

Delete a VPN connection.

**Synopsis:**
```
gcloud edge-cloud container vpn-connections delete
    (VPN_CONNECTION : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Vpn connection resource - VPN connection to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument vpn_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VPN_CONNECTION
     ID of the vpn connection or fully qualified identifier for the vpn
     connection.

     To set the vpn_connection attribute:
     + provide the argument vpn_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument vpn_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a VPN connection called 'test-vpn-connection' at region
'us-central1', run:

    $ gcloud edge-cloud container vpn-connections delete \
        test-vpn-connection --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/vpn-connections/delete)

---
### `gcloud edge-cloud container vpn-connections describe`

Show details about a VPN connection

Show details about a VPN connection.

**Synopsis:**
```
gcloud edge-cloud container vpn-connections describe
    (VPN_CONNECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Vpn connection resource - VPN connection you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument vpn_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VPN_CONNECTION
     ID of the vpn connection or fully qualified identifier for the vpn
     connection.

     To set the vpn_connection attribute:
     + provide the argument vpn_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument vpn_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property edge_container/location.
```

**Examples:**
```bash
To show details about the VPN connection 'test-vpn-connection' at region
us-central1, run:

    $ gcloud edge-cloud container vpn-connections describe \
        test-vpn-connection --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/vpn-connections/describe)

---
### `gcloud edge-cloud container vpn-connections list`

List VPN connections

List VPN connections.

**Synopsis:**
```
gcloud edge-cloud container vpn-connections list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property edge_container/location. |


**Examples:**
```bash
To list the VPN connections at region us-central1, run:

    $ gcloud edge-cloud container vpn-connections list \
        --location=us-central
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/vpn-connections/list)

---

## `gcloud edge-cloud container zones` — inspect Edge Container zones
### `gcloud edge-cloud container zones describe`

Describe an Edge Container zone

Describe an Edge Container zone.

**Synopsis:**
```
gcloud edge-cloud container zones describe ZONE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The zone name. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.
```

**Examples:**
```bash
To display the metadata for the zone us-central1-edge-operator-a, run:

    $ gcloud edge-cloud container zones describe \
        us-central1-edge-operator-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/zones/describe)

---
### `gcloud edge-cloud container zones list`

List Edge Container zones

List all zones where Edge Container node pools can be created.

**Synopsis:**
```
gcloud edge-cloud container zones list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the zones where Edge Container node pools can be created, run:

    $ gcloud edge-cloud container zones list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/zones/list)

---
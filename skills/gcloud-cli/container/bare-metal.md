# gcloud container bare-metal

deploy and manage Anthos clusters on bare metal for running containers


## `gcloud container bare-metal admin-clusters` — create and manage admin clusters in Anthos on bare metal
### `gcloud container bare-metal admin-clusters create`

Create an Anthos on bare metal admin cluster

Create an Anthos on bare metal admin cluster.

**Synopsis:**
```
gcloud container bare-metal admin-clusters create
    (ADMIN_CLUSTER : --location=LOCATION) --version=VERSION
    (--control-plane-load-balancer-port=CONTROL_PLANE_LOAD_BALANCER_PORT
      --control-plane-vip=CONTROL_PLANE_VIP : --enable-manual-lb)
    ((((--control-plane-node-configs=[labels=LABELS],[node-ip=NODE-IP]
      : --control-plane-node-labels=[KEY=VALUE,...]
      --control-plane-node-taints=[KEY=VALUE:EFFECT,...])))
      : --api-server-args=[KEY=VALUE,...])
    (--island-mode-pod-address-cidr-blocks=POD_ADDRESS,[POD_ADDRESS,...]
      --island-mode-service-address-cidr-blocks=SERVICE_ADDRESS,[...])
    ((--lvp-node-mounts-config-path=LVP_NODE_MOUNTS_CONFIG_PATH
      --lvp-node-mounts-config-storage-class=LVP_NODE_MOUNTS_CONFIG_STORAGE_CLASS) ((--lvp-share-path=LVP_SHARE_PATH --lvp-share-storage-class=LVP_SHARE_STORAGE_CLASS) : --shared-path-pv-count=SHARED_PATH_PV_COUNT))
    [--admin-users=ADMIN_USERS] [--annotations=[KEY=VALUE,...]] [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--description=DESCRIPTION] [--enable-application-logs]
    [--login-user=LOGIN_USER]
    [--maintenance-address-cidr-blocks=[MAINTENANCE_ADDRESS_CIDR_BLOCKS,
      ...]] [--max-pods-per-node=MAX_PODS_PER_NODE] [--validate-only]
    [--uri=URI : --no-proxy=[NO_PROXY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Admin cluster resource - admin cluster to create The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument admin_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADMIN_CLUSTER
     ID of the admin_cluster or fully qualified identifier for the
     admin_cluster.

     To set the admin_cluster attribute:
     + provide the argument admin_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the admin_cluster.

     To set the location attribute:
     + provide the argument admin_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Anthos cluster on bare metal version for the admin cluster resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-users` | ADMIN_USERS |  | _[Admin cluster authorization configurations]_ Users that will be granted the view role on the admin cluster, providing view only access to the cluster. |
| `--annotations` | [KEY=VALUE,...] |  | _[Admin cluster authorization configurations]_ |
| `--async` |  |  | _[Annotations on the Anthos on bare metal resource.]_ |
| `--binauthz-evaluation-mode` | BINAUTHZ_EVALUATION_MODE |  | _[complete.]_ |
| `--description` | DESCRIPTION |  | _[PROJECT_SINGLETON_POLICY_ENFORCE.]_ |
| `--enable-application-logs` |  |  | _[Anthos on bare metal cluster operations configuration.]_ Whether collection of application logs/metrics should be enabled (in addition to system logs/metrics). |
| `--login-user` | LOGIN_USER |  | _[Anthos on bare metal node access related settings for the admin cluster.]_ User name used to access node machines. |
| `--maintenance-address-cidr-blocks` | [MAINTENANCE_ADDRESS_CIDR_BLOCKS,...] |  | _[Anthos on bare metal cluster maintenance configuration.]_ IPv4 addresses to be placed into maintenance mode. |
| `--max-pods-per-node` | MAX_PODS_PER_NODE |  | _[Anthos on bare metal admin cluster workload node configuration.]_ Maximum number of pods a node can run. |
| `--validate-only` |  |  | _[Anthos on bare metal admin cluster workload node configuration.]_ |
| `--uri` | URI |  | _[Anthos on bare metal cluster proxy configuration.]_ Address of the proxy server. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--no-proxy` | [NO_PROXY,...] |  | _[Anthos on bare metal cluster proxy configuration.]_ List of IPs, hostnames, and domains that should skip the proxy. |


**Examples:**
```bash
To create a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container bare-metal admin-clusters create my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/create)

---
### `gcloud container bare-metal admin-clusters describe`

Describe an Anthos on bare metal admin cluster

Describe an Anthos on bare metal admin cluster.

**Synopsis:**
```
gcloud container bare-metal admin-clusters describe
    (ADMIN_CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Admin cluster resource - admin cluster to describe The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument admin_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADMIN_CLUSTER
     ID of the admin_cluster or fully qualified identifier for the
     admin_cluster.

     To set the admin_cluster attribute:
     + provide the argument admin_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the admin_cluster.

     To set the location attribute:
     + provide the argument admin_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Examples:**
```bash
To describe an admin cluster named my-cluster managed in location us-west1,
run:

    $ gcloud container bare-metal admin-clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/describe)

---
### `gcloud container bare-metal admin-clusters enroll`

Enroll an Anthos on bare metal admin cluster

Enroll an Anthos on bare metal admin cluster.

**Synopsis:**
```
gcloud container bare-metal admin-clusters enroll
    (ADMIN_CLUSTER : --location=LOCATION)
    (--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION; default="global")
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Admin cluster resource - admin cluster to enroll The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument admin_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADMIN_CLUSTER
     ID of the admin_cluster or fully qualified identifier for the
     admin_cluster.

     To set the admin_cluster attribute:
     + provide the argument admin_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the admin_cluster.

     To set the location attribute:
     + provide the argument admin_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-cluster-membership` | ADMIN_CLUSTER_MEMBERSHIP |  | _[This must be specified.]_ ID of the admin_cluster_membership or fully qualified identifier for the admin_cluster_membership. To set the admin_cluster_membership attribute: + provide the argument --admin-cluster-membership on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--admin-cluster-membership-location` | ADMIN_CLUSTER_MEMBERSHIP_LOCATION | global | _[This must be specified.]_ Google Cloud location for the admin_cluster_membership. To set the location attribute: + provide the argument --admin-cluster-membership on the command line with a fully specified name; + provide the argument --admin-cluster-membership-location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enroll a cluster named my-cluster managed in location us-west1 with
admin cluster membership of
projects/my-project/locations/us-west1/memberships/my-admin-cluster-membership,
run:

    $ gcloud container bare-metal admin-clusters enroll my-cluster \
        --location=us-west1 \
        --admin-cluster-membership=projects/my-project/locations/\
    us-west1/memberships/my-admin-cluster-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/enroll)

---
### `gcloud container bare-metal admin-clusters list`

List Anthos on bare metal admin clusters

List Anthos on bare metal admin clusters.

**Synopsis:**
```
gcloud container bare-metal admin-clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_bare_metal/location. |


**Examples:**
```bash
To list all admin clusters managed in location us-west1, run:

    $ gcloud container bare-metal admin-clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/list)

---
### `gcloud container bare-metal admin-clusters query-version-config`

Query versions for creating or upgrading an Anthos on bare metal admin cluster

Query versions for creating or upgrading an Anthos on bare metal admin
cluster.

**Synopsis:**
```
gcloud container bare-metal admin-clusters query-version-config
    [--admin-cluster=ADMIN_CLUSTER] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-cluster` | ADMIN_CLUSTER |  | _[- set the property container_bare_metal/location.]_ ID of the admin_cluster or fully qualified identifier for the admin_cluster. To set the admin_cluster attribute: o provide the argument --admin-cluster on the command line. |
| `--location` | LOCATION |  | _[* set the property core/project.]_ |


**Examples:**
```bash
To query versions for creating an admin cluster in location us-west1, run:

    $ gcloud container bare-metal admin-clusters query-version-config \
        --location=us-west1

To query versions for upgrading an admin cluster named my-admin-cluster in
location us-west1, run:

    $ gcloud container bare-metal admin-clusters query-version-config \
        --location=us-west1 --admin-cluster=my-admin-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/query-version-config)

---
### `gcloud container bare-metal admin-clusters unenroll`

Unenroll an Anthos on bare metal admin cluster so that it is no longer managed by the Anthos On-Prem API

Unenroll an Anthos on bare metal admin cluster so that it is no longer
managed by the Anthos On-Prem API.

**Synopsis:**
```
gcloud container bare-metal admin-clusters unenroll
    (ADMIN_CLUSTER : --location=LOCATION) [--allow-missing] [--async]
    [--ignore-errors] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Admin cluster resource - admin cluster to unenroll The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument admin_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADMIN_CLUSTER
     ID of the admin_cluster or fully qualified identifier for the
     admin_cluster.

     To set the admin_cluster attribute:
     + provide the argument admin_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the admin_cluster.

     To set the location attribute:
     + provide the argument admin_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the Bare Metal cluster is not found, the request will succeed but no action will be taken. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | If set, the unenrollment of a bare metal admin cluster resource will succeed even if errors occur during unenrollment. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To unenroll an admin cluster named my-cluster managed in location us-west1,
run:

    $ gcloud container bare-metal admin-clusters unenroll my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/unenroll)

---
### `gcloud container bare-metal admin-clusters update`

Update an Anthos on bare metal admin cluster

Update an Anthos on bare metal admin cluster.

**Synopsis:**
```
gcloud container bare-metal admin-clusters update
    (ADMIN_CLUSTER : --location=LOCATION) [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--description=DESCRIPTION] [--enable-application-logs]
    [--island-mode-service-address-cidr-blocks=SERVICE_ADDRESS,[...]]
    [--login-user=LOGIN_USER]
    [--maintenance-address-cidr-blocks=[MAINTENANCE_ADDRESS_CIDR_BLOCKS,
      ...]] [--max-pods-per-node=MAX_PODS_PER_NODE] [--validate-only]
    [--version=VERSION]
    [--api-server-args=[KEY=VALUE,...]
      --control-plane-node-configs=[labels=LABELS],[node-ip=NODE-IP]
      --control-plane-node-labels=[KEY=VALUE,...]
      --control-plane-node-taints=[KEY=VALUE:EFFECT,...]]
    [--no-proxy=[NO_PROXY,...] --uri=URI] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Admin cluster resource - admin cluster to update The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument admin_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADMIN_CLUSTER
     ID of the admin_cluster or fully qualified identifier for the
     admin_cluster.

     To set the admin_cluster attribute:
     + provide the argument admin_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the admin_cluster.

     To set the location attribute:
     + provide the argument admin_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--binauthz-evaluation-mode` | one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE |  | Set Binary Authorization evaluation mode for this cluster. BINAUTHZ_EVALUATION_MODE must be one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE. |
| `--description` | DESCRIPTION |  | Description for the resource. |
| `--validate-only` |  |  | _[Maximum number of pods a node can run.]_ If set, only validate the request, but do not actually perform the operation. |
| `--version` | VERSION |  | _[Maximum number of pods a node can run.]_ Anthos cluster on bare metal version for the admin cluster resource. |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container bare-metal admin-clusters update my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/admin-clusters/update)

---

## `gcloud container bare-metal clusters` — create and manage Anthos clusters on bare metal
### `gcloud container bare-metal clusters create`

Create an Anthos cluster on bare metal

Create an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal clusters create (CLUSTER : --location=LOCATION)
    --version=VERSION
    (--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION --admin-cluster-membership-project=ADMIN_CLUSTER_MEMBERSHIP_PROJECT)
    (--control-plane-load-balancer-port=CONTROL_PLANE_LOAD_BALANCER_PORT
      (--control-plane-vip=CONTROL_PLANE_VIP
      --ingress-vip=INGRESS_VIP) (--enable-manual-lb
      | [--bgp-address-pools=[addresses=ADDRESSES],
      [avoid-buggy-ips=AVOID-BUGGY-IPS],
      [manual-assign=MANUAL-ASSIGN],[pool=POOL] --bgp-asn=BGP_ASN
      --bgp-peer-configs=[asn=ASN,
      ip=IP,control-plane-nodes=NODE_IP_1;NODE_IP_2,...]
      : [--bgp-load-balancer-node-configs=[node-ip=IP,
      labels=KEY1=VALUE1;KEY2=VALUE2,...]
      : --bgp-load-balancer-node-labels=[KEY=VALUE,...]
      --bgp-load-balancer-node-taints=[KEY=VALUE:EFFECT,...]
      --bgp-load-balancer-registry-burst=BGP_LOAD_BALANCER_REGISTRY_BURST
      --bgp-load-balancer-registry-pull-qps=BGP_LOAD_BALANCER_REGISTRY_PULL_QPS --disable-bgp-load-balancer-serialize-image-pulls]] | [--metal-lb-address-pools=[addresses=ADDRESSES],
      [avoid-buggy-ips=AVOID-BUGGY-IPS],
      [manual-assign=MANUAL-ASSIGN],[pool=POOL]
      : --metal-lb-load-balancer-node-configs=[labels=LABELS],
      [node-ip=NODE-IP]
      --metal-lb-load-balancer-node-labels=[KEY=VALUE,...]
      --metal-lb-load-balancer-node-taints=[KEY=VALUE:EFFECT,...]
      --disable-metal-lb-load-balancer-serialize-image-pulls
      --metal-lb-load-balancer-registry-burst=METAL_LB_LOAD_BALANCER_REGISTRY_BURST --metal-lb-load-balancer-registry-pull-qps=METAL_LB_LOAD_BALANCER_REGISTRY_PULL_QPS]))
    ((((--control-plane-node-configs=[labels=LABELS],[node-ip=NODE-IP]
      : --control-plane-node-labels=[KEY=VALUE,...]
      --control-plane-node-taints=[KEY=VALUE:EFFECT,...]
      --control-plane-registry-burst=CONTROL_PLANE_REGISTRY_BURST
      --control-plane-registry-pull-qps=CONTROL_PLANE_REGISTRY_PULL_QPS
      --disable-control-plane-serialize-image-pulls)))
      : --api-server-args=[KEY=VALUE,...])
    ((--lvp-node-mounts-config-path=LVP_NODE_MOUNTS_CONFIG_PATH
      --lvp-node-mounts-config-storage-class=LVP_NODE_MOUNTS_CONFIG_STORAGE_CLASS) ((--lvp-share-path=LVP_SHARE_PATH --lvp-share-storage-class=LVP_SHARE_STORAGE_CLASS) : --shared-path-pv-count=SHARED_PATH_PV_COUNT))
    [--admin-users=ADMIN_USERS] [--annotations=[KEY=VALUE,...]] [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--description=DESCRIPTION] [--enable-application-logs]
    [--login-user=LOGIN_USER]
    [--maintenance-address-cidr-blocks=[MAINTENANCE_ADDRESS_CIDR_BLOCKS,
      ...]] [--validate-only]
    [--container-runtime=CONTAINER_RUNTIME
      --max-pods-per-node=MAX_PODS_PER_NODE]
    [[(--island-mode-pod-address-cidr-blocks=POD_ADDRESS,[POD_ADDRESS,...]
      --island-mode-service-address-cidr-blocks=SERVICE_ADDRESS,[...])
      : --enable-advanced-networking
      --enable-multi-nic-config --enable-sr-iov-config]]
    [--uri=URI : --no-proxy=[NO_PROXY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to create The arguments in this group can be
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
     + set the property container_bare_metal/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Anthos cluster on bare metal version for the user cluster resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-users` | ADMIN_USERS |  | _[cluster]_ Users that will be granted the cluster-admin role on the cluster, providing full access to the cluster. |
| `--annotations` | [KEY=VALUE,...] |  | _[cluster]_ |
| `--async` |  |  | _[Annotations on the Anthos on bare metal resource.]_ |
| `--binauthz-evaluation-mode` | BINAUTHZ_EVALUATION_MODE |  | _[complete.]_ |
| `--description` | DESCRIPTION |  | _[PROJECT_SINGLETON_POLICY_ENFORCE.]_ |
| `--enable-application-logs` |  |  | _[Anthos on bare metal cluster operations configuration.]_ Whether collection of application logs/metrics should be enabled (in addition to system logs/metrics). |
| `--login-user` | LOGIN_USER |  | _[Anthos on bare metal node access related settings for the user cluster.]_ User name used to access node machines. |
| `--maintenance-address-cidr-blocks` | [MAINTENANCE_ADDRESS_CIDR_BLOCKS,...] |  | _[Anthos on bare metal cluster maintenance configuration.]_ IPv4 addresses to be placed into maintenance mode. |
| `--validate-only` |  |  | _[Anthos on bare metal cluster maintenance configuration.]_ |
| `--container-runtime` | CONTAINER_RUNTIME |  | _[Anthos on bare metal cluster workload node configuration.]_ Container runtime which will be used in the bare metal user cluster. |
| `--max-pods-per-node` | MAX_PODS_PER_NODE |  | _[Anthos on bare metal cluster workload node configuration.]_ Maximum number of pods a node can run. |
| `--enable-advanced-networking` |  |  | _[Anthos on bare metal cluster network configurations.]_ Enables the use of advanced Anthos networking features, such as Bundled Load Balancing with BGP or the egress NAT gateway. |
| `--enable-multi-nic-config` |  |  | _[Multiple networking interfaces cluster configurations.]_ If set, enable multiple network interfaces for your pods. |
| `--enable-sr-iov-config` |  |  | _[SR-IOV networking operator configurations.]_ If set, install the SR-IOV operator. |
| `--uri` | URI |  | _[Anthos on bare metal cluster proxy configuration.]_ Address of the proxy server. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--no-proxy` | [NO_PROXY,...] |  | _[Anthos on bare metal cluster proxy configuration.]_ List of IPs, hostnames, and domains that should skip the proxy. |


**Examples:**
```bash
To create a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container bare-metal clusters create my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/create)

---
### `gcloud container bare-metal clusters delete`

Delete an Anthos cluster on bare metal

Delete an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal clusters delete (CLUSTER : --location=LOCATION)
    [--allow-missing] [--async] [--force] [--ignore-errors]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to delete The arguments in this group can be
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
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the Bare Metal cluster is not found, the request will succeed but no action will be taken. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set, the operation will also apply to the child node pools. This flag is required if the cluster has any associated node pools. |
| `--ignore-errors` |  |  | If set, the deletion of a bare metal user cluster resource will succeed even if errors occur during deletion. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To delete a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container bare-metal clusters delete my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/delete)

---
### `gcloud container bare-metal clusters describe`

Describe an Anthos cluster on bare metal

Describe an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal clusters describe
    (CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to describe The arguments in this group can be
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
     + set the property container_bare_metal/location.
```

**Examples:**
```bash
To describe a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container bare-metal clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/describe)

---
### `gcloud container bare-metal clusters enroll`

Enroll an Anthos cluster on bare metal

Enroll an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal clusters enroll (CLUSTER : --location=LOCATION)
    (--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION --admin-cluster-membership-project=ADMIN_CLUSTER_MEMBERSHIP_PROJECT)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to enroll The arguments in this group can be
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
     + set the property container_bare_metal/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-cluster-membership` | projects/example-project-12345/locations/us-west1/memberships/example-admin-cluster-name |  | _[$ gcloud container bare-metal clusters enroll]_ |
| `--admin-cluster-membership-project` | example-project-12345 |  | _[$ gcloud container bare-metal clusters enroll]_ |
| `--admin-cluster-membership-location` | us-west1 |  | _[$ gcloud container bare-metal clusters enroll]_ |
| `--admin-cluster-membership` | example-admin-cluster-name |  | _[$ gcloud container bare-metal clusters enroll]_ |
| `--admin-cluster-membership` | ADMIN_CLUSTER_MEMBERSHIP |  | _[This must be specified.]_ |
| `--admin-cluster-membership-location` | ADMIN_CLUSTER_MEMBERSHIP_LOCATION |  | _[this group are specified.]_ |
| `--admin-cluster-membership-project` | ADMIN_CLUSTER_MEMBERSHIP_PROJECT |  | _[command line.]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enroll a cluster named my-cluster managed in location us-west1 with
admin cluster membership of
projects/my-project/locations/us-west1/memberships/my-admin-cluster-membership,
run:

    $ gcloud container bare-metal clusters enroll my-cluster \
        --location=us-west1 \
        --admin-cluster-membership=projects/my-project/locations/\
    us-west1/memberships/my-admin-cluster-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/enroll)

---
### `gcloud container bare-metal clusters list`

List Anthos clusters on bare metal

List Anthos clusters on bare metal.

**Synopsis:**
```
gcloud container bare-metal clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_bare_metal/location. |


**Examples:**
```bash
To lists all clusters managed in location us-west1, run:

    $ gcloud container bare-metal clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/list)

---
### `gcloud container bare-metal clusters query-version-config`

Query versions for creating or upgrading an Anthos on bare metal user cluster

Query versions for creating or upgrading an Anthos on bare metal user
cluster.

**Synopsis:**
```
gcloud container bare-metal clusters query-version-config
    [--location=LOCATION]
    [--cluster=CLUSTER
      | [--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION; default="global" --admin-cluster-membership-project=ADMIN_CLUSTER_MEMBERSHIP_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_bare_metal/location. |


**Examples:**
```bash
To query all available versions in location us-west1, run:

    $ gcloud container bare-metal clusters query-version-config \
        --location=us-west1

To query versions for creating a cluster with an admin cluster membership
named my-admin-cluster-membership managed in project
my-admin-cluster-project and location us-west, run:

    $ gcloud container bare-metal clusters query-version-config \
        --location=us-west1 \
        --admin-cluster-membership=my-admin-cluster-membership \
        --admin-cluster-membership-project=my-admin-cluster-project

To query versions for upgrading a user cluster named my-user-cluster in
location us-west1, run:

    $ gcloud container bare-metal clusters query-version-config \
        --location=us-west1 --cluster=my-user-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/query-version-config)

---
### `gcloud container bare-metal clusters update`

Update an Anthos cluster on bare metal

Update an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal clusters update (CLUSTER : --location=LOCATION)
    [--admin-users=ADMIN_USERS] [--allow-missing] [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--description=DESCRIPTION] [--enable-application-logs]
    [--login-user=LOGIN_USER]
    [--maintenance-address-cidr-blocks=[MAINTENANCE_ADDRESS_CIDR_BLOCKS,
      ...]] [--validate-only] [--version=VERSION]
    [--add-annotations=[KEY1=VALUE1,KEY2=VALUE2,...]
      | --remove-annotations=[KEY1,KEY2,...]]
    [--api-server-args=[KEY=VALUE,...]
      --control-plane-node-configs=[labels=LABELS],[node-ip=NODE-IP]
      --control-plane-node-labels=[KEY=VALUE,...]
      --control-plane-node-taints=[KEY=VALUE:EFFECT,...]
      --control-plane-registry-burst=CONTROL_PLANE_REGISTRY_BURST
      --control-plane-registry-pull-qps=CONTROL_PLANE_REGISTRY_PULL_QPS
      --disable-control-plane-serialize-image-pulls
      | --enable-control-plane-serialize-image-pulls]
    [--bgp-address-pools=[addresses=ADDRESSES],
      [avoid-buggy-ips=AVOID-BUGGY-IPS],
      [manual-assign=MANUAL-ASSIGN],[pool=POOL] --bgp-asn=BGP_ASN
      --bgp-peer-configs=[asn=ASN,
      ip=IP,control-plane-nodes=NODE_IP_1;NODE_IP_2,...]
      --bgp-load-balancer-node-configs=[node-ip=IP,
      labels=KEY1=VALUE1;KEY2=VALUE2,...]
      --bgp-load-balancer-node-labels=[KEY=VALUE,...]
      --bgp-load-balancer-node-taints=[KEY=VALUE:EFFECT,...]
      --bgp-load-balancer-registry-burst=BGP_LOAD_BALANCER_REGISTRY_BURST
      --bgp-load-balancer-registry-pull-qps=BGP_LOAD_BALANCER_REGISTRY_PULL_QPS --disable-bgp-load-balancer-serialize-image-pulls | --enable-bgp-load-balancer-serialize-image-pulls | --metal-lb-address-pools=[addresses=ADDRESSES],
      [avoid-buggy-ips=AVOID-BUGGY-IPS],
      [manual-assign=MANUAL-ASSIGN],[pool=POOL]
      --metal-lb-load-balancer-node-configs=[labels=LABELS],
      [node-ip=NODE-IP]
      --metal-lb-load-balancer-node-labels=[KEY=VALUE,...]
      --metal-lb-load-balancer-node-taints=[KEY=VALUE:EFFECT,...]
      --metal-lb-load-balancer-registry-burst=METAL_LB_LOAD_BALANCER_REGISTRY_BURST --metal-lb-load-balancer-registry-pull-qps=METAL_LB_LOAD_BALANCER_REGISTRY_PULL_QPS --disable-metal-lb-load-balancer-serialize-image-pulls | --enable-metal-lb-load-balancer-serialize-image-pulls]
    [--island-mode-service-address-cidr-blocks=SERVICE_ADDRESS,[...]
      --disable-sr-iov-config | --enable-sr-iov-config]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to update The arguments in this group can be
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
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-users` | ADMIN_USERS |  | _[cluster]_ Users that will be granted the cluster-admin role on the cluster, providing full access to the cluster. |
| `--allow-missing` |  |  | _[cluster]_ |
| `--async` |  |  | _[configuration.]_ |
| `--binauthz-evaluation-mode` | BINAUTHZ_EVALUATION_MODE |  | _[complete.]_ |
| `--description` | DESCRIPTION |  | _[PROJECT_SINGLETON_POLICY_ENFORCE.]_ |
| `--enable-application-logs` |  |  | _[Anthos on bare metal cluster operations configuration.]_ Whether collection of application logs/metrics should be enabled (in addition to system logs/metrics). |
| `--login-user` | LOGIN_USER |  | _[Anthos on bare metal node access related settings for the user cluster.]_ User name used to access node machines. |
| `--maintenance-address-cidr-blocks` | [MAINTENANCE_ADDRESS_CIDR_BLOCKS,...] |  | _[Anthos on bare metal cluster maintenance configuration.]_ IPv4 addresses to be placed into maintenance mode. |
| `--validate-only` |  |  | _[Anthos on bare metal cluster maintenance configuration.]_ |
| `--version` | VERSION |  | _[operation.]_ |
| `--add-annotations` | [KEY1=VALUE1,KEY2=VALUE2,...] |  | _[At most one of these can be specified:]_ Add the given key-value pairs to the current annotations, or update its value if the key already exists. |
| `--remove-annotations` | [KEY1,KEY2,...] |  | _[At most one of these can be specified:]_ Remove annotations of the given keys. |
| `--api-server-args` | [KEY=VALUE,...] |  | _[Anthos on bare metal cluster control plane configuration.]_ API Server argument configuration. |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container bare-metal clusters update my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/clusters/update)

---

## `gcloud container bare-metal node-pools` — create and manage node pools in an Anthos cluster on bare metal
### `gcloud container bare-metal node-pools create`

Create a node pool in an Anthos cluster on bare metal

Create a node pool in an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal node-pools create
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    (--node-configs=[labels=LABELS],[node-ip=NODE-IP]
      : --node-labels=[KEY=VALUE,...] --node-taints=[KEY=VALUE:EFFECT,...]
      --disable-serialize-image-pulls --registry-burst=REGISTRY_BURST
      --registry-pull-qps=REGISTRY_PULL_QPS)
    [--annotations=[KEY=VALUE,...]] [--async] [--display-name=DISPLAY_NAME]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to create The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node_pool or fully qualified identifier for the node_pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the node_pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node_pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--node-configs` | [labels=LABELS],[node-ip=NODE-IP] |  | _[Exactly one of these must be specified:]_ Bare Metal Node Pool node configuration. |
| `--node-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ Labels assigned to nodes of a node pool. |
| `--node-taints` | [KEY=VALUE:EFFECT,...] |  | _[Exactly one of these must be specified:]_ Node taint applied to every Kubernetes node in a node pool. |
| `--disable-serialize-image-pulls` |  |  | _[Modifiable kubelet configurations for bare metal machines.]_ If set, prevent the Kubelet from pulling multiple images at a time. |
| `--registry-burst` | REGISTRY_BURST |  | _[Modifiable kubelet configurations for bare metal machines.]_ Maximum size of bursty pulls, temporarily allow pulls to burst to this number, while still not exceeding registry_pull_qps. |
| `--registry-pull-qps` | REGISTRY_PULL_QPS |  | _[Modifiable kubelet configurations for bare metal machines.]_ Limit of registry pulls per second. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations on the node pool. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name for the resource. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To create a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container bare-metal node-pools create my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/node-pools/create)

---
### `gcloud container bare-metal node-pools delete`

Delete a node pool in an Anthos cluster on bare metal

Delete a node pool in an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal node-pools delete
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--allow-missing]
    [--async] [--ignore-errors] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to delete The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node_pool or fully qualified identifier for the node_pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the node_pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node_pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the Bare Metal Node Pool is not found, the request will succeed but no action will be taken. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | If set, the deletion of a Bare Metal Node Pool resource will succeed even if errors occur during deletion. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To delete a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container bare-metal node-pools delete my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/node-pools/delete)

---
### `gcloud container bare-metal node-pools describe`

Describe a node pool in an Anthos cluster on bare metal

Describe a node pool in an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal node-pools describe
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to describe The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node_pool or fully qualified identifier for the node_pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the node_pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node_pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Examples:**
```bash
To describe a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container bare-metal node-pools describe my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/node-pools/describe)

---
### `gcloud container bare-metal node-pools enroll`

Enroll a node pool of a user cluster in Anthos on bare metal

Enroll a node pool of a user cluster in Anthos on bare metal.

**Synopsis:**
```
gcloud container bare-metal node-pools enroll
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to enroll The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node_pool or fully qualified identifier for the node_pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the node_pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node_pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To enroll a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container bare-metal node-pools enroll my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/node-pools/enroll)

---
### `gcloud container bare-metal node-pools list`

List node pools in an Anthos cluster on bare metal

List node pools in an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal node-pools list
    (--cluster=CLUSTER : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location for the cluster. To set the location attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --location on the command line; + set the property container_bare_metal/location. |


**Examples:**
```bash
To list all node pools in a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container bare-metal node-pools list --cluster=my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/node-pools/list)

---
### `gcloud container bare-metal node-pools update`

Update a node pool in an Anthos cluster on bare metal

Update a node pool in an Anthos cluster on bare metal.

**Synopsis:**
```
gcloud container bare-metal node-pools update
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--allow-missing]
    [--async] [--display-name=DISPLAY_NAME] [--validate-only]
    [--node-configs=[labels=LABELS],[node-ip=NODE-IP]
      --node-labels=[KEY=VALUE,...] --node-taints=[KEY=VALUE:EFFECT,...]
      --registry-burst=REGISTRY_BURST
      --registry-pull-qps=REGISTRY_PULL_QPS --disable-serialize-image-pulls
      | --enable-serialize-image-pulls] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to update The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument node_pool on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NODE_POOL
     ID of the node_pool or fully qualified identifier for the node_pool.

     To set the node_pool attribute:
     + provide the argument node_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     cluster of the node_pool.

     To set the cluster attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     Google Cloud location for the node_pool.

     To set the location attribute:
     + provide the argument node_pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the Anthos cluster on bare metal is not found, the update request will try to create a new cluster with the provided configuration. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name for the resource. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To update a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container bare-metal node-pools update my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/node-pools/update)

---

## `gcloud container bare-metal operations` — manage Anthos on bare metal long running operations
### `gcloud container bare-metal operations describe`

Describe an operation

Describe an operation.

**Synopsis:**
```
gcloud container bare-metal operations describe
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

     To set the name attribute:
     + provide the argument operation_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation_id on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Examples:**
```bash
To describe an operation in location us-west1, run:

    $ gcloud container bare-metal operations describe OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/operations/describe)

---
### `gcloud container bare-metal operations list`

List operations

List operations.

**Synopsis:**
```
gcloud container bare-metal operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_bare_metal/location. |


**Examples:**
```bash
To list all operations in location us-west1, run:

    $ gcloud container bare-metal operations list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/operations/list)

---
### `gcloud container bare-metal operations wait`

Poll an operation for completion

Poll an operation for completion.

**Synopsis:**
```
gcloud container bare-metal operations wait
    (OPERATION_ID : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to wait for completion. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation_id on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION_ID
     ID of the operation or fully qualified identifier for the operation.

     To set the name attribute:
     + provide the argument operation_id on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation_id on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property container_bare_metal/location.
```

**Examples:**
```bash
To wait for an operation in location us-west1 to complete, run:

    $ gcloud container bare-metal operations wait OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/bare-metal/operations/wait)

---
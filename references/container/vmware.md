# gcloud container vmware

deploy and manage Anthos clusters on VMware for running containers


## `gcloud container vmware admin-clusters` — create and manage admin clusters in Anthos on VMware
### `gcloud container vmware admin-clusters describe`

Describe an Anthos on VMware admin cluster

Describe an Anthos on VMware admin cluster.

**Synopsis:**
```
gcloud container vmware admin-clusters describe
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
     + set the property container_vmware/location.
```

**Examples:**
```bash
To describe an admin cluster named my-cluster managed in location us-west1,
run:

    $ gcloud container vmware admin-clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/admin-clusters/describe)

---
### `gcloud container vmware admin-clusters enroll`

Enroll an Anthos on VMware admin cluster

Enroll an Anthos on VMware admin cluster.

**Synopsis:**
```
gcloud container vmware admin-clusters enroll
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
     + set the property container_vmware/location.
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

    $ gcloud container vmware admin-clusters enroll my-cluster \
        --location=us-west1 \
        --admin-cluster-membership=projects/my-project/locations/\
    us-west1/memberships/my-admin-cluster-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/admin-clusters/enroll)

---
### `gcloud container vmware admin-clusters list`

List Anthos on VMware admin clusters

List Anthos on VMware admin clusters.

**Synopsis:**
```
gcloud container vmware admin-clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_vmware/location. |


**Examples:**
```bash
To list all admin clusters managed in location us-west1, run:

    $ gcloud container vmware admin-clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/admin-clusters/list)

---
### `gcloud container vmware admin-clusters unenroll`

Unenroll an Anthos on VMware admin cluster

Unenroll an Anthos on VMware admin cluster.

**Synopsis:**
```
gcloud container vmware admin-clusters unenroll
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the VMware Cluster is not found, the request will succeed but no action will be taken on the server and return a completed LRO. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | If set, the unenrollment of a VMware admin cluster resource will succeed even if errors occur during deletion. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To unenroll an admin cluster named my-cluster managed in location us-west1,
run:

    $ gcloud container vmware admin-clusters unenroll my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/admin-clusters/unenroll)

---
### `gcloud container vmware admin-clusters update`

Update an Anthos on VMware admin cluster

Update an Anthos on VMware admin cluster.

**Synopsis:**
```
gcloud container vmware admin-clusters update
    (ADMIN_CLUSTER : --location=LOCATION) [--async]
    [--required-platform-version=REQUIRED_PLATFORM_VERSION]
    [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--required-platform-version` | REQUIRED_PLATFORM_VERSION |  | Platform version required for upgrading an admin cluster or a user cluster. If the current platform version is lower than the required version, the platform version will be updated to the required version. If it is not installed in the platform, download the required version bundle. |
| `--version` | VERSION |  | Anthos Cluster on VMware version for the cluster resource |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container vmware admin-clusters update my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/admin-clusters/update)

---

## `gcloud container vmware clusters` — create and manage Anthos clusters on VMware
### `gcloud container vmware clusters create`

Create an Anthos cluster on VMware

Create an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware clusters create (CLUSTER : --location=LOCATION)
    --version=VERSION
    (--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION --admin-cluster-membership-project=ADMIN_CLUSTER_MEMBERSHIP_PROJECT)
    ((--control-plane-vip=CONTROL_PLANE_VIP --ingress-vip=INGRESS_VIP)
      (--metal-lb-config-address-pools=[addresses=ADDRESSES],
      [avoid-buggy-ips=AVOID-BUGGY-IPS],
      [manual-assign=MANUAL-ASSIGN],[pool=POOL]
      | --control-plane-node-port=CONTROL_PLANE_NODE_PORT
      --ingress-http-node-port=INGRESS_HTTP_NODE_PORT
      --ingress-https-node-port=INGRESS_HTTPS_NODE_PORT
      --konnectivity-server-node-port=KONNECTIVITY_SERVER_NODE_PORT
      | [--f5-config-address=F5_CONFIG_ADDRESS
      --f5-config-partition=F5_CONFIG_PARTITION
      : --f5-config-snat-pool=F5_CONFIG_SNAT_POOL]))
    (--pod-address-cidr-blocks=POD_ADDRESS
      --service-address-cidr-blocks=SERVICE_ADDRESS
      : --control-plane-ip-block=[gateway=GATEWAY],
      [ips=IPS],[netmask=NETMASK]
      --dns-search-domains=[DNS_SEARCH_DOMAINS,...]
      --dns-servers=[DNS_SERVERS,...]
      --ntp-servers=[NTP_SERVERS,...] --enable-dhcp
      | --static-ip-config-ip-blocks=[gateway=GATEWAY],
      [ips=IPS],[netmask=NETMASK]) [--admin-users=ADMIN_USERS]
    [--annotations=[KEY=VALUE,...]] [--async] [--description=DESCRIPTION]
    [--disable-aag-config] [--disable-vsphere-csi] [--enable-auto-repair]
    [--enable-vm-tracking]
    [--upgrade-policy=[control-plane-only=CONTROL-PLANE-ONLY]]
    [--validate-only]
    [--cpus=CPUS --enable-auto-resize --memory=MEMORY --replicas=REPLICAS]
    [--disable-control-plane-v2 | --enable-control-plane-v2]
    [--enable-advanced-networking --enable-dataplane-v2]
    [--vcenter-ca-cert-data=VCENTER_CA_CERT_DATA
      --vcenter-cluster=VCENTER_CLUSTER
      --vcenter-datacenter=VCENTER_DATACENTER
      --vcenter-datastore=VCENTER_DATASTORE --vcenter-folder=VCENTER_FOLDER
      --vcenter-resource-pool=VCENTER_RESOURCE_POOL
      --vcenter-storage-policy-name=VCENTER_STORAGE_POLICY_NAME]
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Anthos Cluster on VMware version for the cluster resource |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-users` | ADMIN_USERS |  | _[cluster]_ Users that will be granted the cluster-admin role on the cluster, providing full access to the cluster. To add multiple users, specify one in each flag. When updating, the update command overwrites the whole grant list. Specify all existing and new users that you want to be cluster administrators. Examples: $ gcloud container vmware clusters create --admin-users alice@example.com --admin-users bob@example.com |
| `--annotations` | [KEY=VALUE,...] |  | _[cluster]_ Annotations on the VMware user cluster. |
| `--async` |  |  | _[cluster]_ Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | _[cluster]_ Description for the resource. |
| `--disable-aag-config` |  |  | _[Anti-affinity group configurations]_ If set, spread nodes across at least three physical hosts (requires at least three hosts). Enabled by default. |
| `--disable-vsphere-csi` |  |  | _[Storage configurations]_ If set, vSphere CSI components are not deployed in the VMware User Cluster. Enabled by default. |
| `--enable-auto-repair` |  |  | _[Auto-repair configurations]_ If set, deploy the cluster-health-controller. |
| `--enable-vm-tracking` |  |  | _[Auto-repair configurations]_ If set, enable VM tracking. |
| `--upgrade-policy` | [control-plane-only=CONTROL-PLANE-ONLY] |  | _[Upgrade policy for the cluster.]_ If not specified, control-plane-only is set to False. In the next upgrade operation, all worker node pools will be upgraded together with the control plane. Example: To upgrade the control plane only and keep worker node pools version unchanged, first specify the policy: $ gcloud container vmware clusters create CLUSTER \ --upgrade-policy control-plane-only=True Then to start the upgrade operation using the specified policy, run: $ gcloud container vmware clusters upgrade CLUSTER --version=VERSION After upgrading only the cluster control plane, to upgrade an individual node pool, run: $ gcloud container vmware node-pools update NODE_POOL \ --version=VERSION Example: Alternatively, to upgrade both the control plane and all worker node pools, first specify the policy: $ gcloud container vmware clusters create CLUSTER \ --upgrade-policy control-plane-only=False Then to start the upgrade operation using the specified policy, run: $ gcloud container vmware clusters upgrade CLUSTER --version=VERSION |
| `--validate-only` |  |  | _[Upgrade policy for the cluster.]_ If set, only validate the request, but do not actually perform the operation. |
| `--cpus` | CPUS |  | _[Control plane node configurations]_ Number of CPUs for each admin cluster node that serve as control planes for this VMware user cluster. (default: 4 CPUs) |
| `--memory` | MEMORY |  | _[Enable controle plane node auto resize.]_ Megabytes of memory for each admin cluster node that serves as a control plane for this VMware User Cluster (default: 8192 MB memory). |
| `--replicas` | REPLICAS |  | _[Enable controle plane node auto resize.]_ Number of control plane nodes for this VMware user cluster. (default: 1 replica). |
| `--disable-control-plane-v2` |  |  | _[At most one of these can be specified:]_ If set, disable control plane v2. |
| `--enable-control-plane-v2` |  |  | _[At most one of these can be specified:]_ If set, enable control plane v2. |
| `--enable-advanced-networking` |  |  | _[Dataplane V2 configurations]_ If set, enable advanced networking. Requires dataplane_v2_enabled to be set true. |
| `--enable-dataplane-v2` |  |  | _[Dataplane V2 configurations]_ If set, enables Dataplane V2. |
| `--vcenter-ca-cert-data` | VCENTER_CA_CERT_DATA |  | _[from the admin cluster.]_ Name of the vCenter CA certificate public key for SSL verification. |
| `--vcenter-cluster` | VCENTER_CLUSTER |  | _[from the admin cluster.]_ Name of the vCenter cluster for the user cluster. |
| `--vcenter-datacenter` | VCENTER_DATACENTER |  | _[from the admin cluster.]_ Name of the vCenter datacenter for the user cluster. |
| `--vcenter-datastore` | VCENTER_DATASTORE |  | _[from the admin cluster.]_ Name of the vCenter datastore for the user cluster. |
| `--vcenter-folder` | VCENTER_FOLDER |  | _[from the admin cluster.]_ Name of the vCenter folder for the user cluster. |
| `--vcenter-resource-pool` | VCENTER_RESOURCE_POOL |  | _[from the admin cluster.]_ Name of the vCenter resource pool for the user cluster. |
| `--vcenter-storage-policy-name` | VCENTER_STORAGE_POLICY_NAME |  | _[from the admin cluster.]_ Name of the vCenter storage policy for the user cluster. |


**Examples:**
```bash
To create a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container vmware clusters create my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/create)

---
### `gcloud container vmware clusters delete`

Delete an Anthos cluster on VMware

Delete an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware clusters delete (CLUSTER : --location=LOCATION)
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the Anthos cluster on VMware is not found, the request will succeed but no action will be taken. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set, any node pools from the cluster will also be deleted. This flag is required if the cluster has any associated node pools. |
| `--ignore-errors` |  |  | If set, the deletion of a VMware user cluster resource will succeed even if errors occur during deletion. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To delete a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container vmware clusters delete my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/delete)

---
### `gcloud container vmware clusters describe`

Describe an Anthos cluster on VMware

Describe an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware clusters describe (CLUSTER : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Examples:**
```bash
To describe a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container vmware clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/describe)

---
### `gcloud container vmware clusters enroll`

Enroll an Anthos cluster on VMware

Enroll an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware clusters enroll (CLUSTER : --location=LOCATION)
    (--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION --admin-cluster-membership-project=ADMIN_CLUSTER_MEMBERSHIP_PROJECT)
    [--async] [--local-name=LOCAL_NAME] [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-cluster-membership` | projects/example-project-12345/locations/us-west1/memberships/example-admin-cluster-name |  | _[$ gcloud container vmware clusters enroll]_ |
| `--admin-cluster-membership-project` | example-project-12345 |  | _[$ gcloud container vmware clusters enroll]_ |
| `--admin-cluster-membership-location` | us-west1 |  | _[$ gcloud container vmware clusters enroll]_ |
| `--admin-cluster-membership` | example-admin-cluster-name |  | _[$ gcloud container vmware clusters enroll]_ |
| `--admin-cluster-membership` | ADMIN_CLUSTER_MEMBERSHIP |  | _[This must be specified.]_ |
| `--admin-cluster-membership-location` | ADMIN_CLUSTER_MEMBERSHIP_LOCATION |  | _[this group are specified.]_ |
| `--admin-cluster-membership-project` | ADMIN_CLUSTER_MEMBERSHIP_PROJECT |  | _[command line.]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--local-name` | LOCAL_NAME |  | The object name of the VMware OnPremUserCluster custom resource on the associated admin cluster. This field is used to support conflicting resource names when enrolling existing clusters to the API. When not provided, this field will resolve to the vmware_cluster_id. Otherwise, it must match the object name of the VMware OnPremUserCluster custom resource. It is not modifiable outside / beyond the enrollment operation. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To enroll a cluster named my-cluster managed in location us-west1 with
admin cluster membership of
projects/my-project/locations/us-west1/memberships/my-admin-cluster-membership,
run:

    $ gcloud container vmware clusters enroll my-cluster \
        --location=us-west1 \
        --admin-cluster-membership=projects/my-project/locations/\
    us-west1/memberships/my-admin-cluster-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/enroll)

---
### `gcloud container vmware clusters list`

List Anthos clusters on VMware

List Anthos clusters on VMware.

**Synopsis:**
```
gcloud container vmware clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_vmware/location. |


**Examples:**
```bash
To lists all clusters managed in location us-west1, run:

    $ gcloud container vmware clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/list)

---
### `gcloud container vmware clusters query-version-config`

Query versions for creating or upgrading an Anthos on VMware user cluster

Query versions for creating or upgrading an Anthos on VMware user cluster.

**Synopsis:**
```
gcloud container vmware clusters query-version-config [--location=LOCATION]
    [--cluster=CLUSTER
      | [--admin-cluster-membership=ADMIN_CLUSTER_MEMBERSHIP
      : --admin-cluster-membership-location=ADMIN_CLUSTER_MEMBERSHIP_LOCATION; default="global" --admin-cluster-membership-project=ADMIN_CLUSTER_MEMBERSHIP_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_vmware/location. |


**Examples:**
```bash
To query all available versions in location us-west1, run:

    $ gcloud container vmware clusters query-version-config \
        --location=us-west1

To query versions for creating a cluster with an admin cluster membership
named my-admin-cluster-membership managed in project
my-admin-cluster-project and location us-west, run:

    $ gcloud container vmware clusters query-version-config \
        --location=us-west1 \
        --admin-cluster-membership=my-admin-cluster-membership \
        --admin-cluster-membership-project=my-admin-cluster-project

To query versions for upgrading a user cluster named my-user-cluster in
location us-west1, run:

    $ gcloud container vmware clusters query-version-config \
        --location=us-west1 --cluster=my-user-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/query-version-config)

---
### `gcloud container vmware clusters update`

Update an Anthos cluster on VMware

Update an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware clusters update (CLUSTER : --location=LOCATION)
    [--admin-users=ADMIN_USERS] [--async] [--description=DESCRIPTION]
    [--metal-lb-config-address-pools=[addresses=ADDRESSES],
      [avoid-buggy-ips=AVOID-BUGGY-IPS],
      [manual-assign=MANUAL-ASSIGN],[pool=POOL]]
    [--static-ip-config-ip-blocks=[gateway=GATEWAY],
      [ips=IPS],[netmask=NETMASK]]
    [--upgrade-policy=[control-plane-only=CONTROL-PLANE-ONLY]]
    [--validate-only] [--version=VERSION]
    [--add-annotations=[KEY1=VALUE1,KEY2=VALUE2,...]
      | --remove-annotations=[KEY1,KEY2,...]]
    [--cpus=CPUS --memory=MEMORY --disable-auto-resize
      | --enable-auto-resize] [--disable-aag-config | --enable-aag-config]
    [--disable-auto-repair | --enable-auto-repair]
    [--disable-vsphere-csi | --enable-vsphere-csi] [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-users` | ADMIN_USERS |  | _[cluster]_ Users that will be granted the cluster-admin role on the cluster, providing full access to the cluster. To add multiple users, specify one in each flag. When updating, the update command overwrites the whole grant list. Specify all existing and new users that you want to be cluster administrators. Examples: $ gcloud container vmware clusters update --admin-users alice@example.com --admin-users bob@example.com |
| `--async` |  |  | _[cluster]_ Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | _[cluster]_ Description for the resource. |
| `--upgrade-policy` | [control-plane-only=CONTROL-PLANE-ONLY] |  | _[Upgrade policy for the cluster.]_ If not specified, control-plane-only is set to False. In the next upgrade operation, all worker node pools will be upgraded together with the control plane. Example: To upgrade the control plane only and keep worker node pools version unchanged, first specify the policy: $ gcloud container vmware clusters update CLUSTER \ --upgrade-policy control-plane-only=True Then to start the upgrade operation using the specified policy, run: $ gcloud container vmware clusters upgrade CLUSTER --version=VERSION After upgrading only the cluster control plane, to upgrade an individual node pool, run: $ gcloud container vmware node-pools update NODE_POOL \ --version=VERSION Example: Alternatively, to upgrade both the control plane and all worker node pools, first specify the policy: $ gcloud container vmware clusters update CLUSTER \ --upgrade-policy control-plane-only=False Then to start the upgrade operation using the specified policy, run: $ gcloud container vmware clusters upgrade CLUSTER --version=VERSION |
| `--validate-only` |  |  | _[Upgrade policy for the cluster.]_ If set, only validate the request, but do not actually perform the operation. |
| `--version` | VERSION |  | _[Upgrade policy for the cluster.]_ Anthos Cluster on VMware version for the cluster resource |
| `--add-annotations` | [KEY1=VALUE1,KEY2=VALUE2,...] |  | _[At most one of these can be specified:]_ Add the given key-value pairs to the current annotations, or update its value if the key already exists. |
| `--remove-annotations` | [KEY1,KEY2,...] |  | _[At most one of these can be specified:]_ Remove annotations of the given keys. |
| `--cpus` | CPUS |  | _[Control plane node configurations]_ Number of CPUs for each admin cluster node that serve as control planes for this VMware user cluster. (default: 4 CPUs) |
| `--memory` | MEMORY |  | _[Control plane node configurations]_ Megabytes of memory for each admin cluster node that serves as a control plane for this VMware User Cluster (default: 8192 MB memory). |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container vmware clusters update my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/update)

---
### `gcloud container vmware clusters upgrade`

Centrally upgrade an Anthos cluster on VMware

Centrally upgrade an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware clusters upgrade (CLUSTER : --location=LOCATION)
    --version=VERSION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to upgrade The arguments in this group can be
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
     + set the property container_vmware/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Anthos Cluster on VMware version for the cluster resource |


**Examples:**
```bash
To upgrade a cluster named my-cluster managed in location us-west1 to
version 1.13.0-gke.1000, run:

    $ gcloud container vmware clusters upgrade my-cluster \
        --location=us-west1 --version=1.13.0-gke.1000
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/clusters/upgrade)

---

## `gcloud container vmware node-pools` — create and manage node pools in an Anthos cluster on VMware
### `gcloud container vmware node-pools create`

Create a node pool in an Anthos cluster on VMware

Create a node pool in an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware node-pools create
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    (--image-type=IMAGE_TYPE : --boot-disk-size=BOOT_DISK_SIZE --cpus=CPUS
      --enable-load-balancer --image=IMAGE --memory=MEMORY
      --node-labels=[KEY=VALUE,...]
      --node-taints=[KEY=VALUE:EFFECT,...] --replicas=REPLICAS)
    [--annotations=[KEY=VALUE,...]] [--async] [--display-name=DISPLAY_NAME]
    [--validate-only]
    [--max-replicas=MAX_REPLICAS --min-replicas=MIN_REPLICAS]
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--image-type` | IMAGE_TYPE |  | _[This must be specified.]_ OS image type to use on node pool instances. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--boot-disk-size` | BOOT_DISK_SIZE |  | _[This must be specified.]_ Size of VMware disk to be used during creation in GB. |
| `--cpus` | CPUS |  | _[This must be specified.]_ Number of CPUs for each node in the node pool. |
| `--enable-load-balancer` |  |  | _[This must be specified.]_ If set, enable the use of load balancer on the node pool instances. |
| `--image` | IMAGE |  | _[This must be specified.]_ OS image name in vCenter. |
| `--memory` | MEMORY |  | _[This must be specified.]_ Size of memory for each node in the node pool in MB. |
| `--node-labels` | [KEY=VALUE,...] |  | _[This must be specified.]_ Kubernetes labels (key/value pairs) to be applied to each node. |
| `--node-taints` | [KEY=VALUE:EFFECT,...] |  | _[This must be specified.]_ Applies the given kubernetes taints on all nodes in the new node pool, which can be used with tolerations for pod scheduling. Taint effect must be one of the following: NoSchedule, PreferNoSchedule, or NoExecute. Examples: $ gcloud container vmware node-pools create node-pool-1 \ --cluster=example-cluster \ --node-taints=key1=val1:NoSchedule,key2=val2:PreferNoSchedule |
| `--replicas` | REPLICAS |  | _[This must be specified.]_ Number of replicas to use on node pool instances. |


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

    $ gcloud container vmware node-pools create my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/node-pools/create)

---
### `gcloud container vmware node-pools delete`

Delete a node pool in an Anthos cluster on VMware

Delete a node pool in an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware node-pools delete
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set, and the Vmware Node Pool is not found, the request will succeed but no action will be taken. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | If set, the deletion of a VMware node pool resource will succeed even if errors occur during deletion. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To delete a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container vmware node-pools delete my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/node-pools/delete)

---
### `gcloud container vmware node-pools describe`

Describe a node pool in an Anthos cluster on VMware

Describe a node pool in an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware node-pools describe
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
     + set the property container_vmware/location.
```

**Examples:**
```bash
To describe a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container vmware node-pools describe my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/node-pools/describe)

---
### `gcloud container vmware node-pools enroll`

Enroll a node pool in an Anthos cluster on VMware

Enroll a node pool in an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware node-pools enroll
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enroll a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container vmware node-pools enroll my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/node-pools/enroll)

---
### `gcloud container vmware node-pools list`

List node pools in an Anthos cluster on VMware

List node pools in an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware node-pools list
    (--cluster=CLUSTER : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location for the cluster. To set the location attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --location on the command line; + set the property container_vmware/location. |


**Examples:**
```bash
To list all node pools in a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container vmware node-pools list --cluster=my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/node-pools/list)

---
### `gcloud container vmware node-pools update`

Update a node pool in an Anthos cluster on VMware

Update a node pool in an Anthos cluster on VMware.

**Synopsis:**
```
gcloud container vmware node-pools update
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [--display-name=DISPLAY_NAME] [--validate-only]
    [--boot-disk-size=BOOT_DISK_SIZE --cpus=CPUS --image=IMAGE
      --image-type=IMAGE_TYPE --memory=MEMORY --node-labels=[KEY=VALUE,...]
      --node-taints=[KEY=VALUE:EFFECT,...]
      --replicas=REPLICAS --disable-load-balancer | --enable-load-balancer]
    [--max-replicas=MAX_REPLICAS --min-replicas=MIN_REPLICAS]
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_vmware/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name for the resource. |
| `--validate-only` |  |  | If set, only validate the request, but do not actually perform the operation. |


**Examples:**
```bash
To update a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container vmware node-pools update my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/node-pools/update)

---

## `gcloud container vmware operations` — manage Anthos on VMware long running operations
### `gcloud container vmware operations describe`

Describe an operation

Describe an operation.

**Synopsis:**
```
gcloud container vmware operations describe
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
     + set the property container_vmware/location.
```

**Examples:**
```bash
To describe an operation in location us-west1, run:

    $ gcloud container vmware operations describe OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/operations/describe)

---
### `gcloud container vmware operations list`

List operations

List operations.

**Synopsis:**
```
gcloud container vmware operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_vmware/location. |


**Examples:**
```bash
To list all operations in location us-west1, run:

    $ gcloud container vmware operations list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/operations/list)

---
### `gcloud container vmware operations wait`

Poll an operation for completion

Poll an operation for completion.

**Synopsis:**
```
gcloud container vmware operations wait
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
     + set the property container_vmware/location.
```

**Examples:**
```bash
To wait for an operation in location us-west1 to complete, run:

    $ gcloud container vmware operations wait OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/vmware/operations/wait)

---
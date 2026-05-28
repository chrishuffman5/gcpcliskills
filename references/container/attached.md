# gcloud container attached

manage Attached clusters for running containers

### `gcloud container attached get-server-config`

Get Anthos Multi-Cloud server configuration for Attached clusters

Get Anthos Multi-Cloud server configuration for Attached clusters.

**Synopsis:**
```
gcloud container attached get-server-config [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_attached/location. |


**Examples:**
```bash
To return supported Attached cluster valid platform versions in location
us-west1, run:

    $ gcloud container attached get-server-config --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/get-server-config)

---

## `gcloud container attached clusters` — create and manage Attached clusters
### `gcloud container attached clusters delete`

Delete a registered AttachedCluster resource

Delete a registered AttachedCluster resource.

**Synopsis:**
```
gcloud container attached clusters delete (CLUSTER : --location=LOCATION)
    [--allow-missing] [--async] [--ignore-errors] [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_attached/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of cluster. The request will still succeed in case the cluster does not exist. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | Force delete an Attached cluster. Deletion of the Attached cluster will succeed even if errors occur during deleting in-cluster resources. Using this parameter may result in orphaned resources in the cluster. |
| `--validate-only` |  |  | Validate the cluster to delete, but don't actually perform it. |


**Examples:**
```bash
To delete an AttachedCluster resource named my-cluster managed in location
us-west1, run:

    $ gcloud container attached clusters delete my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/delete)

---
### `gcloud container attached clusters describe`

Describe an Attached cluster

Describe an Attached cluster.

**Synopsis:**
```
gcloud container attached clusters describe (CLUSTER : --location=LOCATION)
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
     + set the property container_attached/location.
```

**Examples:**
```bash
To describe a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container attached clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/describe)

---
### `gcloud container attached clusters generate-install-manifest`

Generate Install Manifest for an Attached cluster

Generate Install Manifest for an Attached cluster.

**Synopsis:**
```
gcloud container attached clusters generate-install-manifest
    (CLUSTER : --location=LOCATION) --platform-version=PLATFORM_VERSION
    [--output-file=OUTPUT_FILE]
    [--proxy-secret-name=PROXY_SECRET_NAME
      --proxy-secret-namespace=PROXY_SECRET_NAMESPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to generate install manifest. The arguments in
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
     + provide the argument --location on the command line;
     + set the property container_attached/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--platform-version` | PLATFORM_VERSION |  | Platform version to use for the cluster. To retrieve a list of valid versions, run: $ gcloud alpha container attached get-server-config \ --location=LOCATION Replace LOCATION with the target Google Cloud location for the cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | Path to the output file to store manifest. |


**Examples:**
```bash
To generate install manifest for cluster named my-cluster managed in
location us-west1, run:

    $ gcloud container attached clusters generate-install-manifest \
        my-cluster --location=us-west1 \
        --platform-version=PLATFORM_VERSION

To store the manifest in a file named manifest.yaml, run:

    $ gcloud container attached clusters generate-install-manifest \
        my-cluster --location=us-west1 \
        --platform-version=PLATFORM_VERSION --output-file=manifest.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/generate-install-manifest)

---
### `gcloud container attached clusters get-credentials`

Get credentials of an Attached cluster

Fetch credentials for a running Attached cluster.

This command updates a kubeconfig file with appropriate credentials and
endpoint information to point kubectl at a specific Attached cluster.

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
gcloud container attached clusters get-credentials
    (CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_attached/location.
```

**Examples:**
```bash
To get credentials of a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container attached clusters get-credentials my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/get-credentials)

---
### `gcloud container attached clusters import`

Import fleet membership for an Attached cluster

Import fleet membership for an Attached cluster.

**Synopsis:**
```
gcloud container attached clusters import --distribution=DISTRIBUTION
    --platform-version=PLATFORM_VERSION
    (--context=CONTEXT : --kubeconfig=KUBECONFIG)
    (--fleet-membership=FLEET_MEMBERSHIP
      : --fleet-membership-location=FLEET_MEMBERSHIP_LOCATION;
      default="global") [--async] [--location=LOCATION] [--validate-only]
    [--proxy-secret-name=PROXY_SECRET_NAME
      --proxy-secret-namespace=PROXY_SECRET_NAMESPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--distribution` | DISTRIBUTION |  | Set the base platform type of the cluster to attach. Examples: $ gcloud container attached clusters import --distribution=aks $ gcloud container attached clusters import --distribution=eks $ gcloud container attached clusters import --distribution=generic |
| `--platform-version` | PLATFORM_VERSION |  | Platform version to use for the cluster. To retrieve a list of valid versions, run: $ gcloud alpha container attached get-server-config \ --location=LOCATION Replace LOCATION with the target Google Cloud location for the cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--validate-only` |  |  | _[+ set the property container_attached/location.]_ Validate the cluster to import, but don't actually perform it. |


**Examples:**
```bash
To import the fleet membership of an attached cluster in fleet
FLEET_MEMBERSHIP managed in location us-west1, run:

    $ gcloud container attached clusters import --location=us-west1 \
        --platform-version=PLATFORM_VERSION \
        --fleet-membership=FLEET_MEMBERSHIP \
        --distribution=DISTRIBUTION --context=CLUSTER_CONTEXT \
        --kubeconfig=KUBECONFIG_PATH
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/import)

---
### `gcloud container attached clusters list`

List Attached clusters

List Attached clusters.

**Synopsis:**
```
gcloud container attached clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_attached/location. |


**Examples:**
```bash
To lists all clusters managed in location us-west1, run:

    $ gcloud container attached clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/list)

---
### `gcloud container attached clusters register`

Register an Attached cluster

Register an Attached cluster.

**Synopsis:**
```
gcloud container attached clusters register (CLUSTER : --location=LOCATION)
    --distribution=DISTRIBUTION --fleet-project=FLEET_PROJECT
    --platform-version=PLATFORM_VERSION
    (--context=CONTEXT : --kubeconfig=KUBECONFIG)
    (--has-private-issuer | --issuer-url=ISSUER_URL)
    [--admin-groups=[GROUP,...]] [--admin-users=[USER,...]]
    [--annotations=ANNOTATION,[ANNOTATION,...]]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--description=DESCRIPTION] [--enable-managed-prometheus]
    [--logging=COMPONENT,[COMPONENT,...]]
    [--system-component-labels=[LABEL,...]]
    [--system-component-tolerations=[TOLERATION,...]]
    [--tags=TAG,[TAG,...]] [--validate-only]
    [--disable-cloud-monitoring | --enable-cloud-monitoring]
    [--proxy-secret-name=PROXY_SECRET_NAME
      --proxy-secret-namespace=PROXY_SECRET_NAMESPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to register. The arguments in this group can be
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
     + set the property container_attached/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--distribution` | DISTRIBUTION |  | Set the base platform type of the cluster to attach. Examples: $ gcloud container attached clusters register --distribution=aks $ gcloud container attached clusters register --distribution=eks $ gcloud container attached clusters register --distribution=generic |
| `--fleet-project` | FLEET_PROJECT |  | ID or number of the Fleet host project where the cluster is registered. |
| `--platform-version` | PLATFORM_VERSION |  | Platform version to use for the cluster. To retrieve a list of valid versions, run: $ gcloud alpha container attached get-server-config \ --location=LOCATION Replace LOCATION with the target Google Cloud location for the cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-groups` | [GROUP,...] |  | Groups of users that can perform operations as a cluster administrator. |
| `--admin-users` | [USER,...] |  | Users that can perform operations as a cluster administrator. |
| `--annotations` | ANNOTATION,[ANNOTATION,...] |  | Annotations for the cluster. |
| `--binauthz-evaluation-mode` | one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE |  | Set Binary Authorization evaluation mode for this cluster. BINAUTHZ_EVALUATION_MODE must be one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE. |
| `--description` | DESCRIPTION |  | Description for the cluster. |
| `--enable-managed-prometheus` |  |  | Enables managed collection for Managed Service for Prometheus in the cluster. See https://cloud.google.com/stackdriver/docs/managed-prometheus/setup-managed#enable-mgdcoll-gke for more info. Managed Prometheus is enabled by default for cluster versions 1.27 or greater, use --no-enable-managed-prometheus to disable. |
| `--logging` | one of: NONE, SYSTEM, WORKLOAD |  | Set the components that have logging enabled. Examples: $ gcloud container attached clusters register --logging=SYSTEM $ gcloud container attached clusters register \ --logging=SYSTEM,WORKLOAD $ gcloud container attached clusters register --logging=NONE COMPONENT must be one of: NONE, SYSTEM, WORKLOAD. |
| `--system-component-labels` | [LABEL,...] |  | Kubernetes labels to be applied to system component pods. |
| `--system-component-tolerations` | [TOLERATION,...] |  | Kubernetes tolerations to be applied to system component pods. |
| `--tags` | TAG,[TAG,...] |  | Tag keys/values directly bound to this resource. The short name of a tag key or value can have a maximum length of 256 characters. The permitted character set for the short name includes UTF-8 encoded Unicode characters except single quotes, double quotes, backslashes, and forward slashes. |
| `--validate-only` |  |  | Validate the cluster to create, but don't actually perform it. |


**Examples:**
```bash
Register a cluster to a fleet.

To register a cluster with a private OIDC issuer, run:

    $ gcloud container attached clusters register my-cluster \
        --location=us-west1 --platform-version=PLATFORM_VERSION \
        --fleet-project=FLEET_PROJECT_NUM --distribution=DISTRIBUTION \
        --context=CLUSTER_CONTEXT --has-private-issuer

To register a cluster with a public OIDC issuer, run:

    $ gcloud container attached clusters register my-cluster \
        --location=us-west1 --platform-version=PLATFORM_VERSION \
        --fleet-project=FLEET_PROJECT_NUM --distribution=DISTRIBUTION \
        --context=CLUSTER_CONTEXT --issuer-url=https://ISSUER_URL

To specify a kubeconfig file, run:

    $ gcloud container attached clusters register my-cluster \
        --location=us-west1 --platform-version=PLATFORM_VERSION \
        --fleet-project=FLEET_PROJECT_NUM --distribution=DISTRIBUTION \
        --context=CLUSTER_CONTEXT --has-private-issuer \
        --kubeconfig=KUBECONFIG_PATH

To register and set cluster admin users, run:

    $ gcloud container attached clusters register my-cluster \
        --location=us-west1 --platform-version=PLATFORM_VERSION \
        --fleet-project=FLEET_PROJECT_NUM --distribution=DISTRIBUTION \
        --context=CLUSTER_CONTEXT --issuer-url=https://ISSUER_URL \
        --admin-users=USER1,USER2

To specify custom tolerations and labels for system component pods, run:

    $ gcloud container attached clusters register my-cluster \
        --location=us-west1 --platform-version=PLATFORM_VERSION \
        --fleet-project=FLEET_PROJECT_NUM --distribution=DISTRIBUTION \
        --context=CLUSTER_CONTEXT \
        --system-component-tolerations=TOLERATIONS \
        --system-component-labels=LABELS

where TOLERATIONS have the format:        key=value:Effect:NoSchedule (examples: key1=value1:Equal:NoSchedule,key2:Exists:PreferNoSchedule, :Exists:NoExecute)
and LABELS have the format:        key=value (examples: key1=value1,key2="")
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/register)

---
### `gcloud container attached clusters update`

Update an Attached cluster

Update an Attached cluster.

**Synopsis:**
```
gcloud container attached clusters update (CLUSTER : --location=LOCATION)
    [--annotations=ANNOTATION,[ANNOTATION,...]] [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--clear-description] [--description=DESCRIPTION]
    [--logging=COMPONENT,[COMPONENT,...]]
    [--platform-version=PLATFORM_VERSION] [--validate-only]
    [--admin-groups=[GROUP,...] | --clear-admin-groups]
    [--admin-users=[USER,...] | --clear-admin-users]
    [--disable-cloud-monitoring | --enable-cloud-monitoring]
    [--disable-managed-prometheus | --enable-managed-prometheus]
    [--proxy-secret-name=PROXY_SECRET_NAME
      --proxy-secret-namespace=PROXY_SECRET_NAMESPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to update. The arguments in this group can be
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
     + set the property container_attached/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | ANNOTATION,[ANNOTATION,...] |  | Annotations for the cluster. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--binauthz-evaluation-mode` | one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE |  | Set Binary Authorization evaluation mode for this cluster. BINAUTHZ_EVALUATION_MODE must be one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE. |
| `--clear-description` |  |  | Clear the description for the cluster. |
| `--description` | DESCRIPTION |  | Description for the cluster. |
| `--logging` | one of: NONE, SYSTEM, WORKLOAD |  | Set the components that have logging enabled. Examples: $ gcloud container attached clusters update --logging=SYSTEM $ gcloud container attached clusters update --logging=SYSTEM,WORKLOAD $ gcloud container attached clusters update --logging=NONE COMPONENT must be one of: NONE, SYSTEM, WORKLOAD. |
| `--platform-version` | PLATFORM_VERSION |  | Platform version to use for the cluster. To retrieve a list of valid versions, run: $ gcloud alpha container attached get-server-config \ --location=LOCATION Replace LOCATION with the target Google Cloud location for the cluster. |
| `--validate-only` |  |  | Validate the update of the cluster, but don't actually perform it. |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container attached clusters update my-cluster \
        --location=us-west1 --description=testcluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/clusters/update)

---

## `gcloud container attached operations` — manage Anthos Multi-Cloud long running operations for Attached clusters
### `gcloud container attached operations describe`

Describe an operation

Describe an operation.

**Synopsis:**
```
gcloud container attached operations describe
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
     + set the property container_attached/location.
```

**Examples:**
```bash
To describe an operation in location us-west1, run:

    $ gcloud container attached operations describe OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/operations/describe)

---
### `gcloud container attached operations list`

List operations

List operations.

**Synopsis:**
```
gcloud container attached operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_attached/location. |


**Examples:**
```bash
To list all operations in location us-west1, run:

    $ gcloud container attached operations list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/operations/list)

---
### `gcloud container attached operations wait`

Wait for an operation to complete

Wait for an operation to complete.

**Synopsis:**
```
gcloud container attached operations wait
    (OPERATION_ID : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_attached/location.
```

**Examples:**
```bash
To wait for an operation in location us-west1 to complete, run:

    $ gcloud container attached operations wait OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/attached/operations/wait)

---
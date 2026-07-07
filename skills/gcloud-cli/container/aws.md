# gcloud container aws

deploy and manage clusters of machines on AWS for running containers

### `gcloud container aws get-server-config`

Get Anthos Multi-Cloud server configuration for AWS

(DEPRECATED) Get Anthos Multi-Cloud server configuration for AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws get-server-config [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_aws/location. |


**Examples:**
```bash
To return supported AWS regions and valid versions in location us-west1,
run:

    $ gcloud container aws get-server-config --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/get-server-config)

---

## `gcloud container aws clusters` — create and manage Anthos clusters on AWS
### `gcloud container aws clusters create`

Create an Anthos cluster on AWS

(DEPRECATED) Create an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws clusters create (CLUSTER : --location=LOCATION)
    --aws-region=AWS_REGION --cluster-version=CLUSTER_VERSION
    --config-encryption-kms-key-arn=CONFIG_ENCRYPTION_KMS_KEY_ARN
    --database-encryption-kms-key-arn=DATABASE_ENCRYPTION_KMS_KEY_ARN
    --fleet-project=FLEET_PROJECT
    --iam-instance-profile=IAM_INSTANCE_PROFILE
    --pod-address-cidr-blocks=POD_ADDRESS_CIDR_BLOCKS --role-arn=ROLE_ARN
    --service-address-cidr-blocks=SERVICE_ADDRESS_CIDR_BLOCKS
    --subnet-ids=[SUBNET_ID,...] --vpc-id=VPC_ID
    [--admin-groups=[GROUP,...]] [--admin-users=USER,[USER,...]]
    [--annotations=ANNOTATION,[ANNOTATION,...]] [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--description=DESCRIPTION] [--disable-per-node-pool-sg-rules]
    [--enable-managed-prometheus] [--instance-type=INSTANCE_TYPE]
    [--logging=COMPONENT,[COMPONENT,...]]
    [--main-volume-iops=MAIN_VOLUME_IOPS]
    [--main-volume-kms-key-arn=MAIN_VOLUME_KMS_KEY_ARN]
    [--main-volume-size=MAIN_VOLUME_SIZE]
    [--main-volume-throughput=MAIN_VOLUME_THROUGHPUT]
    [--main-volume-type=MAIN_VOLUME_TYPE]
    [--role-session-name=ROLE_SESSION_NAME]
    [--root-volume-iops=ROOT_VOLUME_IOPS]
    [--root-volume-kms-key-arn=ROOT_VOLUME_KMS_KEY_ARN]
    [--root-volume-size=ROOT_VOLUME_SIZE]
    [--root-volume-throughput=ROOT_VOLUME_THROUGHPUT]
    [--root-volume-type=ROOT_VOLUME_TYPE]
    [--security-group-ids=[SECURITY_GROUP_ID,...]]
    [--ssh-ec2-key-pair=SSH_EC2_KEY_PAIR] [--tags=TAG,[TAG,...]]
    [--validate-only]
    [--proxy-secret-arn=PROXY_SECRET_ARN
      --proxy-secret-version-id=PROXY_SECRET_VERSION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - cluster to create. The arguments in this group can be
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
     + set the property container_aws/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aws-region` | AWS_REGION |  | AWS region to deploy the cluster. |
| `--cluster-version` | CLUSTER_VERSION |  | Kubernetes version to use for the cluster. |
| `--config-encryption-kms-key-arn` | CONFIG_ENCRYPTION_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the user data. |
| `--database-encryption-kms-key-arn` | DATABASE_ENCRYPTION_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the cluster secrets. |
| `--fleet-project` | FLEET_PROJECT |  | ID or number of the Fleet host project where the cluster is registered. |
| `--iam-instance-profile` | IAM_INSTANCE_PROFILE |  | Name or ARN of the IAM instance profile associated with the cluster. |
| `--pod-address-cidr-blocks` | POD_ADDRESS_CIDR_BLOCKS |  | IP address range for the pods in this cluster in CIDR notation (e.g. 10.0.0.0/8). |
| `--role-arn` | ROLE_ARN |  | Amazon Resource Name (ARN) of the IAM role to assume when managing AWS resources. |
| `--service-address-cidr-blocks` | SERVICE_ADDRESS_CIDR_BLOCKS |  | IP address range for the services IPs in CIDR notation (e.g. 10.0.0.0/8). |
| `--subnet-ids` | [SUBNET_ID,...] |  | Subnet ID of an existing VNET to use for the cluster control plane. |
| `--vpc-id` | VPC_ID |  | VPC associated with the cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-groups` | [GROUP,...] |  | Groups of users that can perform operations as a cluster administrator. |
| `--admin-users` | USER,[USER,...] |  | Users that can perform operations as a cluster administrator. If not specified, the value of property core/account is used. |
| `--annotations` | ANNOTATION,[ANNOTATION,...] |  | Annotations for the cluster. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--binauthz-evaluation-mode` | one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE |  | Set Binary Authorization evaluation mode for this cluster. BINAUTHZ_EVALUATION_MODE must be one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE. |
| `--description` | DESCRIPTION |  | Description for the cluster. |
| `--disable-per-node-pool-sg-rules` |  |  | Disable the default per node pool subnet security group rules on the control plane security group. When disabled, at least one security group that allows node pools to send traffic to the control plane on ports TCP/443 and TCP/8132 must be provided. |
| `--enable-managed-prometheus` |  |  | Enables managed collection for Managed Service for Prometheus in the cluster. See https://cloud.google.com/stackdriver/docs/managed-prometheus/setup-managed#enable-mgdcoll-gke for more info. Managed Prometheus is enabled by default for cluster versions 1.27 or greater, use --no-enable-managed-prometheus to disable. |
| `--instance-type` | INSTANCE_TYPE |  | AWS EC2 instance type for the control plane's nodes. |
| `--logging` | one of: SYSTEM, WORKLOAD |  | Set the components that have logging enabled. Examples: $ gcloud container aws clusters create --logging=SYSTEM $ gcloud container aws clusters create --logging=SYSTEM,WORKLOAD COMPONENT must be one of: SYSTEM, WORKLOAD. |
| `--main-volume-iops` | MAIN_VOLUME_IOPS |  | Number of I/O operations per second (IOPS) to provision for the main volume. |
| `--main-volume-kms-key-arn` | MAIN_VOLUME_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the main volume. |
| `--main-volume-size` | MAIN_VOLUME_SIZE |  | Size of the main volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--main-volume-throughput` | MAIN_VOLUME_THROUGHPUT |  | Throughput to provision for the main volume, in MiB/s. Only valid if the volume type is GP3. If volume type is GP3 and throughput is not provided, it defaults to 125. |
| `--main-volume-type` | one of: gp2, gp3 |  | Type of the main volume. MAIN_VOLUME_TYPE must be one of: gp2, gp3. |
| `--role-session-name` | ROLE_SESSION_NAME |  | Identifier for the assumed role session. |
| `--root-volume-iops` | ROOT_VOLUME_IOPS |  | Number of I/O operations per second (IOPS) to provision for the root volume. |
| `--root-volume-kms-key-arn` | ROOT_VOLUME_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the root volume. |
| `--root-volume-size` | ROOT_VOLUME_SIZE |  | Size of the root volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--root-volume-throughput` | ROOT_VOLUME_THROUGHPUT |  | Throughput to provision for the root volume, in MiB/s. Only valid if the volume type is GP3. If volume type is GP3 and throughput is not provided, it defaults to 125. |
| `--root-volume-type` | one of: gp2, gp3 |  | Type of the root volume. ROOT_VOLUME_TYPE must be one of: gp2, gp3. |
| `--security-group-ids` | [SECURITY_GROUP_ID,...] |  | IDs of additional security groups to add to the control plane's nodes. |
| `--ssh-ec2-key-pair` | SSH_EC2_KEY_PAIR |  | Name of the EC2 key pair authorized to login to the control plane's nodes. |
| `--tags` | TAG,[TAG,...] |  | Applies the given tags (comma separated) on the cluster. Example: $ gcloud container aws clusters create EXAMPLE_CLUSTER \ --tags=tag1=one,tag2=two |
| `--validate-only` |  |  | Validate the cluster to create, but don't actually perform it. |


**Examples:**
```bash
To create a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container aws clusters create my-cluster \
        --location=us-west1 --aws-region=AWS_REGION \
        --cluster-version=CLUSTER_VERSION \
        --database-encryption-kms-key-arn=KMS_KEY_ARN \
        --iam-instance-profile=IAM_INSTANCE_PROFILE \
        --pod-address-cidr-blocks=POD_ADDRESS_CIDR_BLOCKS \
        --role-arn=ROLE_ARN \
        --service-address-cidr-blocks=SERVICE_ADDRESS_CIDR_BLOCKS \
        --subnet-ids=SUBNET_ID --vpc-id=VPC_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/clusters/create)

---
### `gcloud container aws clusters delete`

Delete an Anthos cluster on AWS

(DEPRECATED) Delete an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws clusters delete (CLUSTER : --location=LOCATION)
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
     + set the property container_aws/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of cluster. The request will still succeed in case the cluster does not exist. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | Force delete an AWS cluster. Deletion of the AWS cluster will succeed even if errors occur during deleting in-cluster resources. Using this parameter may result in orphaned resources in the cluster. |
| `--validate-only` |  |  | Validate the cluster to delete, but don't actually perform it. |


**Examples:**
```bash
To delete a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container aws clusters delete my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/clusters/delete)

---
### `gcloud container aws clusters describe`

Describe an Anthos cluster on AWS

(DEPRECATED) Describe an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws clusters describe (CLUSTER : --location=LOCATION)
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
     + set the property container_aws/location.
```

**Examples:**
```bash
To describe a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container aws clusters describe my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/clusters/describe)

---
### `gcloud container aws clusters get-credentials`

Get credentials of an Anthos cluster on AWS

(DEPRECATED) This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

Fetch credentials for a running Anthos cluster on AWS.

This command updates a kubeconfig file with appropriate credentials and
endpoint information to point kubectl at a specific Anthos cluster on AWS.

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
gcloud container aws clusters get-credentials
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
     + set the property container_aws/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-endpoint` |  |  | If set, use private VPC for authentication. |


**Examples:**
```bash
To get credentials of a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container aws clusters get-credentials my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/clusters/get-credentials)

---
### `gcloud container aws clusters list`

List Anthos clusters on AWS

(DEPRECATED) List Anthos clusters on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws clusters list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_aws/location. |


**Examples:**
```bash
To lists all clusters managed in location us-west1, run:

    $ gcloud container aws clusters list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/clusters/list)

---
### `gcloud container aws clusters update`

Update an Anthos cluster on AWS

(DEPRECATED) Update an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws clusters update (CLUSTER : --location=LOCATION)
    [--admin-groups=[GROUP,...]] [--admin-users=USER,[USER,...]] [--async]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE]
    [--cluster-version=CLUSTER_VERSION]
    [--config-encryption-kms-key-arn=CONFIG_ENCRYPTION_KMS_KEY_ARN]
    [--iam-instance-profile=IAM_INSTANCE_PROFILE]
    [--instance-type=INSTANCE_TYPE] [--logging=COMPONENT,[COMPONENT,...]]
    [--role-arn=ROLE_ARN] [--role-session-name=ROLE_SESSION_NAME]
    [--root-volume-iops=ROOT_VOLUME_IOPS]
    [--root-volume-kms-key-arn=ROOT_VOLUME_KMS_KEY_ARN]
    [--root-volume-size=ROOT_VOLUME_SIZE]
    [--root-volume-throughput=ROOT_VOLUME_THROUGHPUT]
    [--root-volume-type=ROOT_VOLUME_TYPE] [--validate-only]
    [--annotations=ANNOTATION,[ANNOTATION,...] | --clear-annotations]
    [--clear-description | --description=DESCRIPTION]
    [--clear-proxy-config | --proxy-secret-arn=PROXY_SECRET_ARN
      --proxy-secret-version-id=PROXY_SECRET_VERSION_ID]
    [--clear-security-group-ids
      | --security-group-ids=[SECURITY_GROUP_ID,...]]
    [--clear-ssh-ec2-key-pair | --ssh-ec2-key-pair=SSH_EC2_KEY_PAIR]
    [--clear-tags | --tags=TAG,[TAG,...]]
    [--disable-managed-prometheus | --enable-managed-prometheus]
    [--disable-per-node-pool-sg-rules | --enable-per-node-pool-sg-rules]
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
     + set the property container_aws/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-groups` | [GROUP,...] |  | Groups of users that can perform operations as a cluster administrator. |
| `--admin-users` | USER,[USER,...] |  | Users that can perform operations as a cluster administrator. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--binauthz-evaluation-mode` | one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE |  | Set Binary Authorization evaluation mode for this cluster. BINAUTHZ_EVALUATION_MODE must be one of: DISABLED, PROJECT_SINGLETON_POLICY_ENFORCE. |
| `--cluster-version` | CLUSTER_VERSION |  | Kubernetes version to use for the cluster. |
| `--config-encryption-kms-key-arn` | CONFIG_ENCRYPTION_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the user data. |
| `--iam-instance-profile` | IAM_INSTANCE_PROFILE |  | Name or ARN of the IAM instance profile associated with the cluster. |
| `--instance-type` | INSTANCE_TYPE |  | AWS EC2 instance type for the control plane's nodes. |
| `--logging` | one of: SYSTEM, WORKLOAD |  | Set the components that have logging enabled. Examples: $ gcloud container aws clusters update --logging=SYSTEM $ gcloud container aws clusters update --logging=SYSTEM,WORKLOAD COMPONENT must be one of: SYSTEM, WORKLOAD. |
| `--role-arn` | ROLE_ARN |  | Amazon Resource Name (ARN) of the IAM role to assume when managing AWS resources. |
| `--role-session-name` | ROLE_SESSION_NAME |  | Identifier for the assumed role session. |
| `--root-volume-iops` | ROOT_VOLUME_IOPS |  | Number of I/O operations per second (IOPS) to provision for the root volume. |
| `--root-volume-kms-key-arn` | ROOT_VOLUME_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the root volume. |
| `--root-volume-size` | ROOT_VOLUME_SIZE |  | Size of the root volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--root-volume-throughput` | ROOT_VOLUME_THROUGHPUT |  | Throughput to provision for the root volume, in MiB/s. Only valid if the volume type is GP3. If volume type is GP3 and throughput is not provided, it defaults to 125. |
| `--root-volume-type` | one of: gp2, gp3 |  | Type of the root volume. ROOT_VOLUME_TYPE must be one of: gp2, gp3. |
| `--validate-only` |  |  | Validate the update of the cluster, but don't actually perform it. |


**Examples:**
```bash
To update a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container aws clusters update my-cluster \
        --location=us-west1 --cluster-version=CLUSTER_VERSION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/clusters/update)

---

## `gcloud container aws node-pools` — create and manage node pools in an Anthos cluster on AWS
### `gcloud container aws node-pools create`

Create a node pool in an Anthos cluster on AWS

(DEPRECATED) Create a node pool in an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws node-pools create
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    --config-encryption-kms-key-arn=CONFIG_ENCRYPTION_KMS_KEY_ARN
    --iam-instance-profile=IAM_INSTANCE_PROFILE
    --max-pods-per-node=MAX_PODS_PER_NODE --node-version=NODE_VERSION
    --subnet-id=SUBNET_ID (--max-nodes=MAX_NODES --min-nodes=MIN_NODES)
    [--annotations=ANNOTATION,[ANNOTATION,...]] [--async]
    [--enable-autorepair]
    [--kubelet-config-cpu-cfs-quota=KUBELET_CONFIG_CPU_CFS_QUOTA]
    [--kubelet-config-cpu-cfs-quota-period=KUBELET_CONFIG_CPU_CFS_QUOTA_PERIOD]
    [--kubelet-config-cpu-manager-policy=KUBELET_CONFIG_CPU_MANAGER_POLICY]
    [--kubelet-config-pod-pids-limit=KUBELET_CONFIG_POD_PIDS_LIMIT]
    [--max-surge-update=MAX_SURGE_UPDATE]
    [--max-unavailable-update=MAX_UNAVAILABLE_UPDATE]
    [--node-labels=NODE_LABEL,[NODE_LABEL,...]]
    [--node-taints=NODE_TAINT,[NODE_TAINT,...]]
    [--root-volume-iops=ROOT_VOLUME_IOPS]
    [--root-volume-kms-key-arn=ROOT_VOLUME_KMS_KEY_ARN]
    [--root-volume-size=ROOT_VOLUME_SIZE]
    [--root-volume-throughput=ROOT_VOLUME_THROUGHPUT]
    [--root-volume-type=ROOT_VOLUME_TYPE]
    [--security-group-ids=[SECURITY_GROUP_ID,...]]
    [--ssh-ec2-key-pair=SSH_EC2_KEY_PAIR] [--tags=TAG,[TAG,...]]
    [--validate-only]
    [--autoscaling-metrics-granularity=AUTOSCALING_METRICS_GRANULARITY
      : --autoscaling-metrics=[AUTOSCALING_METRIC,...]]
    [--instance-type=INSTANCE_TYPE
      | --spot-instance-types=[INSTANCE_TYPE,...]]
    [--proxy-secret-arn=PROXY_SECRET_ARN
      --proxy-secret-version-id=PROXY_SECRET_VERSION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to create. The arguments in this group can
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
     + set the property container_aws/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-encryption-kms-key-arn` | CONFIG_ENCRYPTION_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the user data. |
| `--iam-instance-profile` | IAM_INSTANCE_PROFILE |  | Name or ARN of the IAM instance profile associated with the node pool. |
| `--max-pods-per-node` | MAX_PODS_PER_NODE |  | Maximum number of pods per node. |
| `--node-version` | NODE_VERSION |  | Kubernetes version to use for the node pool. |
| `--subnet-id` | SUBNET_ID |  | Subnet ID of an existing VNET to use for the node pool. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | ANNOTATION,[ANNOTATION,...] |  | Annotations for the node pool. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-autorepair` |  |  | Enable node autorepair feature for a node pool. Use --no-enable-autorepair to disable. $ gcloud container aws node-pools create --enable-autorepair Node autorepair is disabled by default. |
| `--kubelet-config-cpu-cfs-quota` | KUBELET_CONFIG_CPU_CFS_QUOTA |  | Enforce a Kubelet CPU CFS quota. |
| `--kubelet-config-cpu-cfs-quota-period` | KUBELET_CONFIG_CPU_CFS_QUOTA_PERIOD |  | Kubelet CPU CFS quota period, within the range "1ms" to "1s". |
| `--kubelet-config-cpu-manager-policy` | one of: none, static |  | Kubelet CPU manager policy. KUBELET_CONFIG_CPU_MANAGER_POLICY must be one of: none, static. |
| `--kubelet-config-pod-pids-limit` | KUBELET_CONFIG_POD_PIDS_LIMIT |  | Kubelet maximum number of PIDS in any pod, within the range 1024 to 4194304. |
| `--max-surge-update` | MAX_SURGE_UPDATE |  | Maximum number of extra (surge) nodes to be created beyond the current size of the node pool during its update process. Use --max-unavailable-update as well, if needed, to control the overall surge settings. To create an extra node each time the node pool is rolling updated, run: $ gcloud container aws node-pools create --max-surge-update=1 \ --max-unavailable-update=0 |
| `--max-unavailable-update` | MAX_UNAVAILABLE_UPDATE |  | Maximum number of nodes that can be simultaneously unavailable during this node pool's update process. Use --max-surge-update as well, if needed, to control the overall surge settings. To update 3 nodes in parallel (1 + 2), but keep at least 4 nodes (6 - 2) available each time the node pool is rolling updated, run: $ gcloud container aws node-pools create --min-nodes=6 \ --max-surge-update=1 --max-unavailable-update=2 |
| `--node-labels` | NODE_LABEL,[NODE_LABEL,...] |  | Labels assigned to the node pool's nodes. |
| `--node-taints` | one of: NoExecute, NoSchedule, PreferNoSchedule |  | Taints assigned to nodes of the node pool. Node taint is of format key=value:effect. Effect must be one of: NoExecute, NoSchedule, PreferNoSchedule. |
| `--root-volume-iops` | ROOT_VOLUME_IOPS |  | Number of I/O operations per second (IOPS) to provision for the root volume. |
| `--root-volume-kms-key-arn` | ROOT_VOLUME_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the root volume. |
| `--root-volume-size` | ROOT_VOLUME_SIZE |  | Size of the root volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--root-volume-throughput` | ROOT_VOLUME_THROUGHPUT |  | Throughput to provision for the root volume, in MiB/s. Only valid if the volume type is GP3. If volume type is GP3 and throughput is not provided, it defaults to 125. |
| `--root-volume-type` | one of: gp2, gp3 |  | Type of the root volume. ROOT_VOLUME_TYPE must be one of: gp2, gp3. |
| `--security-group-ids` | [SECURITY_GROUP_ID,...] |  | IDs of additional security groups to add to the node pool's nodes. |
| `--ssh-ec2-key-pair` | SSH_EC2_KEY_PAIR |  | Name of the EC2 key pair authorized to login to the node pool's nodes. |
| `--tags` | TAG,[TAG,...] |  | Applies the given tags (comma separated) on the node pool. Example: $ gcloud container aws node-pools create EXAMPLE_NODE_POOL \ --tags=tag1=one,tag2=two |
| `--validate-only` |  |  | Validate the node pool to create, but don't actually perform it. |


**Examples:**
```bash
To create a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container aws node-pools create my-node-pool \
        --cluster=my-cluster --location=us-west1 \
        --iam-instance-profile=IAM_INSTANCE_PROFILE \
        --node-version=NODE_VERSION --subnet-id=SUBNET_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/node-pools/create)

---
### `gcloud container aws node-pools delete`

Delete a node pool in an Anthos cluster on AWS

(DEPRECATED) Delete a node pool in an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws node-pools delete
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--allow-missing]
    [--async] [--ignore-errors] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to delete. The arguments in this group can
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
     + set the property container_aws/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of node pool. The request will still succeed in case the node pool does not exist. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-errors` |  |  | Force delete an AWS node pool. Deletion of the AWS node pool will succeed even if errors occur during deleting in-node pool resources. Using this parameter may result in orphaned resources in the node pool. |
| `--validate-only` |  |  | Validate the node pool to delete, but don't actually perform it. |


**Examples:**
```bash
To delete a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container aws node-pools delete my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/node-pools/delete)

---
### `gcloud container aws node-pools describe`

Describe a node pool in an Anthos cluster on AWS

(DEPRECATED) Describe a node pool in an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws node-pools describe
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     + set the property container_aws/location.
```

**Examples:**
```bash
To describe a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container aws node-pools describe my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/node-pools/describe)

---
### `gcloud container aws node-pools list`

List node pools in an Anthos cluster on AWS

(DEPRECATED) List node pools in an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws node-pools list
    (--cluster=CLUSTER : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[This must be specified.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location for the cluster. To set the location attribute: + provide the argument --cluster on the command line with a fully specified name; + provide the argument --location on the command line; + set the property container_aws/location. |


**Examples:**
```bash
To list all node pools in a cluster named my-cluster managed in location
us-west1, run:

    $ gcloud container aws node-pools list --cluster=my-cluster \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/node-pools/list)

---
### `gcloud container aws node-pools rollback`

Rollback a node pool in an Anthos cluster on AWS

(DEPRECATED) Rollback a node pool in an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws node-pools rollback
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [--respect-pdb] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to rollback. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     + set the property container_aws/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--respect-pdb` |  |  | Indicates whether the node pool rollback should respect pod disruption budget. |


**Examples:**
```bash
To roll back a canceled or failed update in node pool named my-node-pool in
a cluster named my-cluster managed in location us-west1, run:

    $ gcloud container aws node-pools rollback my-node-pool \
        --cluster=my-cluster --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/node-pools/rollback)

---
### `gcloud container aws node-pools update`

Update a node pool in an Anthos cluster on AWS

(DEPRECATED) Update a node pool in an Anthos cluster on AWS.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws node-pools update
    (NODE_POOL : --cluster=CLUSTER --location=LOCATION) [--async]
    [--config-encryption-kms-key-arn=CONFIG_ENCRYPTION_KMS_KEY_ARN]
    [--enable-autorepair] [--iam-instance-profile=IAM_INSTANCE_PROFILE]
    [--instance-type=INSTANCE_TYPE] [--max-surge-update=MAX_SURGE_UPDATE]
    [--max-unavailable-update=MAX_UNAVAILABLE_UPDATE]
    [--node-version=NODE_VERSION] [--root-volume-iops=ROOT_VOLUME_IOPS]
    [--root-volume-kms-key-arn=ROOT_VOLUME_KMS_KEY_ARN]
    [--root-volume-size=ROOT_VOLUME_SIZE]
    [--root-volume-throughput=ROOT_VOLUME_THROUGHPUT]
    [--root-volume-type=ROOT_VOLUME_TYPE] [--validate-only]
    [--annotations=ANNOTATION,[ANNOTATION,...] | --clear-annotations]
    [--clear-autoscaling-metrics
      | --autoscaling-metrics=[AUTOSCALING_METRIC,...]
      --autoscaling-metrics-granularity=AUTOSCALING_METRICS_GRANULARITY]
    [--clear-node-labels | --node-labels=NODE_LABEL,[NODE_LABEL,...]]
    [--clear-proxy-config | --proxy-secret-arn=PROXY_SECRET_ARN
      --proxy-secret-version-id=PROXY_SECRET_VERSION_ID]
    [--clear-security-group-ids
      | --security-group-ids=[SECURITY_GROUP_ID,...]]
    [--clear-ssh-ec2-key-pair | --ssh-ec2-key-pair=SSH_EC2_KEY_PAIR]
    [--clear-tags | --tags=TAG,[TAG,...]]
    [--max-nodes=MAX_NODES --min-nodes=MIN_NODES] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Node pool resource - node pool to update. The arguments in this group can
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
     + set the property container_aws/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--config-encryption-kms-key-arn` | CONFIG_ENCRYPTION_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the user data. |
| `--enable-autorepair` |  |  | Enable node autorepair feature for a node pool. Use --no-enable-autorepair to disable. $ gcloud container aws node-pools update --enable-autorepair |
| `--iam-instance-profile` | IAM_INSTANCE_PROFILE |  | Name or ARN of the IAM instance profile associated with the node pool. |
| `--instance-type` | INSTANCE_TYPE |  | AWS EC2 instance type for the node pool's nodes. |
| `--max-surge-update` | MAX_SURGE_UPDATE |  | Maximum number of extra (surge) nodes to be created beyond the current size of the node pool during its update process. Use --max-unavailable-update as well, if needed, to control the overall surge settings. To create an extra node each time the node pool is rolling updated, run: $ gcloud container aws node-pools update --max-surge-update=1 \ --max-unavailable-update=0 |
| `--max-unavailable-update` | MAX_UNAVAILABLE_UPDATE |  | Maximum number of nodes that can be simultaneously unavailable during this node pool's update process. Use --max-surge-update as well, if needed, to control the overall surge settings. To modify a node pool with 6 nodes such that, 3 nodes are updated in parallel (1 + 2), but keep at least 4 nodes (6 - 2) available each time this node pool is rolling updated, run: $ gcloud container aws node-pools update --max-surge-update=1 \ --max-unavailable-update=2 |
| `--node-version` | NODE_VERSION |  | Kubernetes version to use for the node pool. |
| `--root-volume-iops` | ROOT_VOLUME_IOPS |  | Number of I/O operations per second (IOPS) to provision for the root volume. |
| `--root-volume-kms-key-arn` | ROOT_VOLUME_KMS_KEY_ARN |  | Amazon Resource Name (ARN) of the AWS KMS key to encrypt the root volume. |
| `--root-volume-size` | ROOT_VOLUME_SIZE |  | Size of the root volume. The value must be a whole number followed by a size unit of GB for gigabyte, or TB for terabyte. If no size unit is specified, GB is assumed. |
| `--root-volume-throughput` | ROOT_VOLUME_THROUGHPUT |  | Throughput to provision for the root volume, in MiB/s. Only valid if the volume type is GP3. If volume type is GP3 and throughput is not provided, it defaults to 125. |
| `--root-volume-type` | one of: gp2, gp3 |  | Type of the root volume. ROOT_VOLUME_TYPE must be one of: gp2, gp3. |
| `--validate-only` |  |  | Validate the node pool to update, but don't actually perform it. |


**Examples:**
```bash
To update a node pool named my-node-pool in a cluster named my-cluster
managed in location us-west1, run:

    $ gcloud container aws node-pools update my-node-pool \
        --cluster=my-cluster --location=us-west1 \
        --node-version=NODE_VERSION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/node-pools/update)

---

## `gcloud container aws operations` — manage Anthos Multi-Cloud long running operations for AWS
### `gcloud container aws operations cancel`

Cancel an operation

(DEPRECATED) Cancel an operation.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws operations cancel (OPERATION_ID : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
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
     + set the property container_aws/location.
```

**Examples:**
```bash
To cancel an operation in location us-west1, run:

    $ gcloud container aws operations cancel OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/operations/cancel)

---
### `gcloud container aws operations describe`

Describe an operation

(DEPRECATED) Describe an operation.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws operations describe
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
     + set the property container_aws/location.
```

**Examples:**
```bash
To describe an operation in location us-west1, run:

    $ gcloud container aws operations describe OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/operations/describe)

---
### `gcloud container aws operations list`

List operations

(DEPRECATED) List operations.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property container_aws/location. |


**Examples:**
```bash
To list all operations in location us-west1, run:

    $ gcloud container aws operations list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/operations/list)

---
### `gcloud container aws operations wait`

Wait for an operation to complete

(DEPRECATED) Wait for an operation to complete.

This command is deprecated. See
https://cloud.google.com/kubernetes-engine/multi-cloud/docs/aws/deprecations/deprecation-announcement
for more details.

**Synopsis:**
```
gcloud container aws operations wait (OPERATION_ID : --location=LOCATION)
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
     + set the property container_aws/location.
```

**Examples:**
```bash
To wait for an operation in location us-west1 to complete, run:

    $ gcloud container aws operations wait OPERATION_ID \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/aws/operations/wait)

---
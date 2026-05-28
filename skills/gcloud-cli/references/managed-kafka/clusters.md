# gcloud managed-kafka clusters

administer Managed Service for Apache Kafka clusters

### `gcloud managed-kafka clusters create`

Create a Managed Service for Apache Kafka cluster

Create a Managed Service for Apache Kafka cluster.

**Synopsis:**
```
gcloud managed-kafka clusters create (CLUSTER : --location=LOCATION)
    --cpu=CPU --memory=MEMORY --subnets=[SUBNETS,...] [--async]
    [--no-auto-rebalance] [--encryption-key=ENCRYPTION_KEY]
    [--labels=[KEY=VALUE,...]] [--mtls-ca-pools=[MTLS_CA_POOLS,...]]
    [--ssl-principal-mapping-rules=SSL_PRINCIPAL_MAPPING_RULES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster for which the command runs. The
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
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cpu` | CPU |  | The number of vCPUs to provision for the cluster. The minimum is 3. |
| `--memory` | MEMORY |  | The memory to provision for the cluster in bytes. The value must be between 1 GiB and 8 GiB per vCPU. Ex. 1024Mi, 4Gi. |
| `--subnets` | [SUBNETS,...] |  | A comma-separated list of VPC subnets from which the cluster is accessible. Both broker and bootstrap server IP addresses and DNS entries are automatically created in each subnet. Only one subnet per network is allowed, and the subnet must be located in the same region as the cluster. The project may differ. A minimum of 1 subnet is required. A maximum of 10 subnets can be specified. Use commas to separate multiple subnets. The name of the subnet must be in the format projects/PROJECT_ID/regions/REGION/subnetworks/SUBNET. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-rebalance` |  |  | Whether the automatic rebalancing is enabled. If automatic rebalancing is enabled, topic partitions are rebalanced among brokers when the number of CPUs in the cluster changes. Automatic rebalancing is enabled by default. Use --no-auto-rebalance to disable this flag. Enabled by default, use --no-auto-rebalance to disable. |
| `--encryption-key` | ENCRYPTION_KEY |  | The relative resource path of the Cloud KMS key to use for encryption in the form: projects/PROJECT_ID/locations/LOCATION/keyRings/KEY_RING/cryptoKeys/KEY. The key must be located in the same region as the cluster. The key cannot be changed once set. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--mtls-ca-pools` | [MTLS_CA_POOLS,...] |  | A comma-separated list of CA pools from the Google Cloud Certificate Authority Service. The root certificates of these CA pools will be installed in the truststore of each broker in the cluster for use with mTLS. A maximum of 10 CA pools can be specified. CA pools can be in a different project and region than the cluster. This command overwrites the entire set of pools currently configured on the cluster. If you want to add a new pool to an existing configuration, you must provide the full list of both the old and new CA pools in the command. Each CA pool must be in the format projects/PROJECT_ID/locations/LOCATION/caPools/CA_POOL. Clear the CA pools using the --clear-mtls-ca-pools flag. |
| `--ssl-principal-mapping-rules` | SSL_PRINCIPAL_MAPPING_RULES |  | The rules for mapping mTLS certificate Distinguished Names (DNs) to shortened principal names for Kafka ACLs. This flag corresponds exactly to the ssl.principal.mapping.rules broker config and matches the format and syntax defined in the Apache Kafka documentation. Setting or modifying this field will trigger a rolling restart of the Kafka brokers to apply the change. An empty string means that the default Kafka behavior is used. Example: "RULE:^CN=(.?),OU=ServiceUsers.$/$1@example.com/,DEFAULT" |


**Examples:**
```bash
To create a cluster, run the following:

    $ gcloud managed-kafka clusters create mycluster \
        --location=us-central1 --cpu=3 --memory=3GiB \
        --subnets=projects/PROJECT_ID/regions/us-central1/subnetworks/\
    default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/clusters/create)

---
### `gcloud managed-kafka clusters delete`

Delete a Managed Service for Apache Kafka cluster

Delete a Managed Service for Apache Kafka cluster.

**Synopsis:**
```
gcloud managed-kafka clusters delete (CLUSTER : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster for deletion. The arguments in
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
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a cluster named mycluster located in us-central1, run the
following:

    $ gcloud managed-kafka clusters delete mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/clusters/delete)

---
### `gcloud managed-kafka clusters describe`

Describe a Managed Service for Apache Kafka cluster

Describe a Managed Service for Apache Kafka cluster.

**Synopsis:**
```
gcloud managed-kafka clusters describe (CLUSTER : --location=LOCATION)
    [--full] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster for details to be displayed. The
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
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full` |  |  | Show detailed information about individual brokers, such as broker id and zone, as well as the Kafka version running on the cluster. |


**Examples:**
```bash
To describe a cluster named mycluster located in us-central1, run the
following:

    $ gcloud managed-kafka clusters describe mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/clusters/describe)

---
### `gcloud managed-kafka clusters list`

List all Managed Service for Apache Kafka clusters in a given location

List all Apache Kafka for BigQuery clusters in a given location. To specify
the maximum number of clusters to list, use the --limit flag.

**Synopsis:**
```
gcloud managed-kafka clusters list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all clusters in a given location, such as us-central1, run the
following:

    $ gcloud managed-kafka clusters list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/clusters/list)

---
### `gcloud managed-kafka clusters update`

Update a Managed Service for Apache Kafka cluster

Update a Managed Service for Apache Kafka cluster.

**Synopsis:**
```
gcloud managed-kafka clusters update (CLUSTER : --location=LOCATION)
    (--auto-rebalance --cpu=CPU --labels=[KEY=VALUE,...] --memory=MEMORY
      --ssl-principal-mapping-rules=SSL_PRINCIPAL_MAPPING_RULES
      --subnets=[SUBNETS,...] --clear-mtls-ca-pools
      | --mtls-ca-pools=[MTLS_CA_POOLS,...])
    [--allow-broker-downscale-on-cluster-upscale] [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster to be updated. The arguments in
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
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-rebalance` |  |  | _[At least one of these must be specified:]_ Whether the automatic rebalancing is enabled. If automatic rebalancing is enabled, topic partitions are rebalanced among brokers when the number of CPUs in the cluster changes. Automatic rebalancing is enabled by default. Use --no-auto-rebalance to disable this flag. |
| `--cpu` | CPU |  | _[At least one of these must be specified:]_ The number of vCPUs to provision for the cluster. The minimum is 3. |
| `--labels` | [KEY=VALUE,...] |  | _[At least one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--memory` | MEMORY |  | _[At least one of these must be specified:]_ The memory to provision for the cluster in bytes. The value must be between 1 GiB and 8 GiB per vCPU. Ex. 1024Mi, 4Gi. |
| `--ssl-principal-mapping-rules` | SSL_PRINCIPAL_MAPPING_RULES |  | _[At least one of these must be specified:]_ The rules for mapping mTLS certificate Distinguished Names (DNs) to shortened principal names for Kafka ACLs. This flag corresponds exactly to the ssl.principal.mapping.rules broker config and matches the format and syntax defined in the Apache Kafka documentation. Setting or modifying this field will trigger a rolling restart of the Kafka brokers to apply the change. An empty string means that the default Kafka behavior is used. Example: "RULE:^CN=(.?),OU=ServiceUsers.$/$1@example.com/,DEFAULT" |
| `--subnets` | [SUBNETS,...] |  | _[At least one of these must be specified:]_ A comma-separated list of VPC subnets from which the cluster is accessible. Both broker and bootstrap server IP addresses and DNS entries are automatically created in each subnet. Only one subnet per network is allowed, and the subnet must be located in the same region as the cluster. The project may differ. A minimum of 1 subnet is required. A maximum of 10 subnets can be specified. Use commas to separate multiple subnets. The name of the subnet must be in the format projects/PROJECT_ID/regions/REGION/subnetworks/SUBNET. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-broker-downscale-on-cluster-upscale` |  |  | If enabled, this setting allows an update operation that could significantly decrease the per-broker vCPU and/or memory allocation, which can lead to reduced performance and availability. By default, an update operation will fail if it results in a reduction of 10% or more to the brokers' vCPU or memory allocation. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update an attribute in a cluster named mycluster located in us-central1,
such as the CPU, run the following:

    $ gcloud managed-kafka clusters update mycluster \
        --location=us-central1 --cpu=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/clusters/update)

---
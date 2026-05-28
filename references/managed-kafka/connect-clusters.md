# gcloud managed-kafka connect-clusters

administer Managed Service for Apache Kafka connect-clusters

### `gcloud managed-kafka connect-clusters create`

Create a Managed Service for Apache Kafka connect cluster

Create a Managed Service for Apache Kafka connect cluster.

**Synopsis:**
```
gcloud managed-kafka connect-clusters create
    (CONNECT_CLUSTER : --location=LOCATION) --cpu=CPU
    --kafka-cluster=KAFKA_CLUSTER --memory=MEMORY
    --primary-subnet=PRIMARY_SUBNET [--additional-subnet=ADDITIONAL_SUBNET]
    [--async] [--dns-name=DNS_NAME] [--labels=[KEY=VALUE,...]]
    [--secret=SECRET]
    [--config-file=JSON|YAML|FILE | --configs=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connect cluster resource - Identifies the connect cluster that is created.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connect_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECT_CLUSTER
     ID of the connect_cluster or fully qualified identifier for the
     connect_cluster.

     To set the connect_cluster attribute:
     + provide the argument connect_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connect_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cpu` | CPU |  | The number of vCPUs to provision for the cluster. The minimum is 3. |
| `--kafka-cluster` | KAFKA_CLUSTER |  | The resource path of the Kafka cluster to connect to, or the name of the Kafka cluster to connect to if the cluster is in the same project as the Connect cluster. |
| `--memory` | MEMORY |  | The memory to provision for the cluster in bytes. The value must be between 1 GiB and 8 GiB per vCPU. Ex. 1024Mi, 4Gi. |
| `--primary-subnet` | PRIMARY_SUBNET |  | VPC subnet to make available to the Kafka Connect cluster. Structured like: projects/{project}/regions/{region}/subnetworks/{subnet_id}. The primary subnet is used to create a Private Service Connect (PSC) interface for the Kafka Connect workers. It must be located in the same region as the Connect cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-subnet` | ADDITIONAL_SUBNET |  | (DEPRECATED) Additional subnet to make available to the Kafka Connect cluster. Structured like: projects/{project}/regions/{region}/subnetworks/{subnet_id}. The --additional-subnet flag is deprecated and will be removed in a future version. Managed Kafka Connect clusters can now reach any endpoint accessible from the primary subnet without the need to define additional subnets. Please see https://cloud.google.com/managed-service-for-apache-kafka/docs/connect-cluster/create-connect-cluster#worker-subnet for more information. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--dns-name` | DNS_NAME |  | DNS domain name from the subnet's network to be made visible to the Connect Cluster. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--secret` | SECRET |  | Secrets to load into workers. Exact SecretVersions from Secret Manager must be provided -- aliases are not supported. Up to 32 secrets may be loaded into one cluster. Format: projects/<project-id>/secrets/<secret-name>/versions/<version-id> |


**Examples:**
```bash
To create a connector cluster, run the following:

    $ gcloud managed-kafka connect-clusters create myconnectorCluster \
        --location=us-central1 --cpu=3 --memory=3GiB \
        --primary-subnet=projects/PROJECT_ID/regions/us-central1/\
    subnetworks/default --kafka-cluster=my-kafka-cluster OR \
        --kafka-cluster=projects/PROJECT_ID/locations/us-central1/\
    clusters/my-kafka-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connect-clusters/create)

---
### `gcloud managed-kafka connect-clusters delete`

Delete a Managed Service for Apache Kafka connect cluster

Delete a Managed Service for Apache Kafka connect cluster.

**Synopsis:**
```
gcloud managed-kafka connect-clusters delete
    (CONNECT_CLUSTER : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connect cluster resource - Identifies the connect cluster for deletion.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connect_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECT_CLUSTER
     ID of the connect_cluster or fully qualified identifier for the
     connect_cluster.

     To set the connect_cluster attribute:
     + provide the argument connect_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connect_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a connect cluster named myconnectcluster located in us-central1,
run the following:

    $ gcloud managed-kafka connect-clusters delete myconnectcluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connect-clusters/delete)

---
### `gcloud managed-kafka connect-clusters describe`

Describe a Managed Service for Apache Kafka connect cluster

Describe a Managed Service for Apache Kafka for BigQuery connect cluster.

**Synopsis:**
```
gcloud managed-kafka connect-clusters describe
    (CONNECT_CLUSTER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connect cluster resource - Identifies the connect cluster. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument connect_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECT_CLUSTER
     ID of the connect_cluster or fully qualified identifier for the
     connect_cluster.

     To set the connect_cluster attribute:
     + provide the argument connect_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connect_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a connect cluster named myconnectcluster located in
us-central1, run the following:

    $ gcloud managed-kafka connect-clusters describe myconnectcluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connect-clusters/describe)

---
### `gcloud managed-kafka connect-clusters list`

List all Managed Service for Apache Kafka connect clusters in a given location

List all Managed Service for Apache Kafka connect clusters in a given
location. To specify the maximum number of clusters to list, use the
--limit flag.

**Synopsis:**
```
gcloud managed-kafka connect-clusters list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all connect clusters in a given location, such as us-central1, run
the following:

    $ gcloud managed-kafka connect-clusters list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connect-clusters/list)

---
### `gcloud managed-kafka connect-clusters update`

Update a Managed Service for Apache Kafka for BigQuery connect cluster

Update an Managed Service for Apache Kafka for BigQuery connect cluster.

**Synopsis:**
```
gcloud managed-kafka connect-clusters update
    (CONNECT_CLUSTER : --location=LOCATION)
    (--cpu=CPU --memory=MEMORY --clear-configs
      | --config-file=JSON|YAML|FILE
      | --configs=[KEY=VALUE,...] --clear-dns-names
      | --dns-name=DNS_NAME --clear-labels
      | --labels=[KEY=VALUE,...] --clear-secrets
      | --secret=SECRET [--primary-subnet=PRIMARY_SUBNET
      : --additional-subnet=ADDITIONAL_SUBNET]) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connect cluster resource - Identifies the connect cluster for which the
command runs. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connect_cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECT_CLUSTER
     ID of the connect_cluster or fully qualified identifier for the
     connect_cluster.

     To set the connect_cluster attribute:
     + provide the argument connect_cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument connect_cluster on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cpu` | CPU |  | _[At least one of these must be specified:]_ The number of vCPUs to provision for the cluster. The minimum is 3. |
| `--memory` | MEMORY |  | _[At least one of these must be specified:]_ The memory to provision for the cluster in bytes. The value must be between 1 GiB and 8 GiB per vCPU. Ex. 1024Mi, 4Gi. |
| `--primary-subnet` | PRIMARY_SUBNET |  | _[projects/<project-id>/secrets/<secret-name>/versions/<version-id>]_ VPC subnet to make available to the Kafka Connect cluster. Structured like: projects/{project}/regions/{region}/subnetworks/{subnet_id}. The primary subnet is used to create a Private Service Connect (PSC) interface for the Kafka Connect workers. It must be located in the same region as the Connect cluster. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--additional-subnet` | ADDITIONAL_SUBNET |  | _[projects/<project-id>/secrets/<secret-name>/versions/<version-id>]_ (DEPRECATED) Additional subnet to make available to the Kafka Connect cluster. Structured like: projects/{project}/regions/{region}/subnetworks/{subnet_id}. The --additional-subnet flag is deprecated and will be removed in a future version. Managed Kafka Connect clusters can now reach any endpoint accessible from the primary subnet without the need to define additional subnets. Please see https://cloud.google.com/managed-service-for-apache-kafka/docs/connect-cluster/create-connect-cluster#worker-subnet for more information. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update a connect cluster, run the following:

    $ gcloud managed-kafka connect-clusters update myconnectorCluster \
        --location=us-central1 --configs=KEY1=VALUE1,KEY2=VALUE2... OR \
        --config-file=my-config-file.yaml --cpu=3 --memory=3GiB \
        --primary-subnet=projects/my-project/regions/us-central1/\
    subnetworks/default/1 \
        --dns-name=bootstrap.myconnectorCluster.us-central1.managedkafka\
    .my-project.cloud.goog:9092 \
        --secret=projects/my-project/secrets/my-secret/versions/1 \
        --labels=KEY1=VALUE1,KEY2=VALUE2...
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/connect-clusters/update)

---
# gcloud managed-kafka topics

administer Managed Service for Apache Kafka topics

### `gcloud managed-kafka topics create`

Create a Managed Service for Apache Kafka topic

Create a Managed Service for Apache Kafka topic.

**Synopsis:**
```
gcloud managed-kafka topics create
    (TOPIC : --cluster=CLUSTER --location=LOCATION) --partitions=PARTITIONS
    --replication-factor=REPLICATION_FACTOR [--configs=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Identifies the name of the topic that this command
creates. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--partitions` | PARTITIONS |  | The number of partitions in a topic. You can increase the partition count for a topic, but you cannot decrease it. Increasing partitions for a topic that uses a key might change how messages are distributed. |
| `--replication-factor` | REPLICATION_FACTOR |  | The number of replicas of each partition. A replication factor of 3 is recommended for high availability. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--configs` | [KEY=VALUE,...] |  | Configuration for the topic that are overridden from the cluster defaults. The key of the map is a Kafka topic property name, for example: cleanup.policy=compact,compression.type=producer. If you provide a map with a key that already exists, only that configuration is updated. If the map contains a key that does not exist, the entry is appended to the topic configuration. |


**Examples:**
```bash
To create a topic in a cluster named mycluster located in us-central1, run
the following:

    $ gcloud managed-kafka topics create mytopic --cluster=mycluster \
        --location=us-central1 --partitions=1 --replication-factor=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/topics/create)

---
### `gcloud managed-kafka topics delete`

Delete a Managed Service for Apache Kafka topic

Delete a Managed Service for Apache Kafka topic.

**Synopsis:**
```
gcloud managed-kafka topics delete
    (TOPIC : --cluster=CLUSTER --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Identifies the topic for deletion. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a topic in a cluster named mycluster located in us-central1, run
the following:

    $ gcloud managed-kafka topics delete mytopic --cluster=mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/topics/delete)

---
### `gcloud managed-kafka topics describe`

Describe a Managed Service for Apache Kafka topic

Describe a Managed Service for Apache Kafka topic.

**Synopsis:**
```
gcloud managed-kafka topics describe
    (TOPIC : --cluster=CLUSTER --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - The describe command displays properties of the topic
specified by this parameter. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a topic in a cluster named mycluster located in us-central1,
run the following:

    $ gcloud managed-kafka topics describe mytopic --cluster=mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/topics/describe)

---
### `gcloud managed-kafka topics list`

List all Managed Service for Apache Kafka topics in a given cluster

List all Managed Service for Apache Kafka topics in a given cluster. To
specify the maximum number of topics to list, use the --limit flag.

**Synopsis:**
```
gcloud managed-kafka topics list (CLUSTER : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster which contains all the topics to
be listed. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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

**Examples:**
```bash
To list all topics in a cluster named mycluster located in us-central1, run
the following:

    $ gcloud managed-kafka topics list mycluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/topics/list)

---
### `gcloud managed-kafka topics update`

Update a Managed Service for Apache Kafka topic

Update a Managed Service for Apache Kafka topic.

**Synopsis:**
```
gcloud managed-kafka topics update
    (TOPIC : --cluster=CLUSTER --location=LOCATION)
    (--partitions=PARTITIONS --clear-configs | --configs=[KEY=VALUE,...])
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Identifies the topic to be updated. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--partitions` | PARTITIONS |  | _[At least one of these must be specified:]_ The number of partitions in a topic. You can increase the partition count for a topic, but you cannot decrease it. Increasing partitions for a topic that uses a key might change how messages are distributed. |


**Examples:**
```bash
To update an attribute in a topic, such as the partitions, for a cluster
named mycluster located in us-central1, run the following:

    $ gcloud managed-kafka topics update mytopic --cluster=mycluster \
        --location=us-central1 --partitions=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/topics/update)

---
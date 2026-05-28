# gcloud managed-kafka consumer-groups

administer Managed Service for Apache Kafka consumer groups

### `gcloud managed-kafka consumer-groups delete`

Delete a Managed Service for Apache Kafka consumer group

Delete a Managed Service for Apache Kafka consumer group.

**Synopsis:**
```
gcloud managed-kafka consumer-groups delete
    (CONSUMER_GROUP : --cluster=CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Consumer group resource - Identifies the consumer group for deletion. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument consumer_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSUMER_GROUP
     ID of the consumer_group or fully qualified identifier for the
     consumer_group.

     To set the consumer_group attribute:
     + provide the argument consumer_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument consumer_group on the command line with a
       fully specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument consumer_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a consumer group in a cluster named mycluster located in
us-central1, run the following:

    $ gcloud managed-kafka consumer-groups delete myconsumergroup \
        --cluster=mycluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/consumer-groups/delete)

---
### `gcloud managed-kafka consumer-groups describe`

Describe a Managed Service for Apache Kafka consumer group

Describe a Managed Service for Apache Kafka consumer group.

**Synopsis:**
```
gcloud managed-kafka consumer-groups describe
    (CONSUMER_GROUP : --cluster=CLUSTER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Consumer group resource - Identifies the consumer group for details to be
displayed. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument consumer_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSUMER_GROUP
     ID of the consumer_group or fully qualified identifier for the
     consumer_group.

     To set the consumer_group attribute:
     + provide the argument consumer_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument consumer_group on the command line with a
       fully specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument consumer_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a consumer group in a cluster named mycluster located in
us-central1, run the following:

    $ gcloud managed-kafka consumer-groups describe myconsumergroup \
        --cluster=mycluster --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/consumer-groups/describe)

---
### `gcloud managed-kafka consumer-groups list`

List all Managed Service for Apache Kafka consumer groups in a given cluster and location

List all Managed Service for Apache Kafka consumer groups in a given
cluster and location. To specify the maximum number of consumer groups to
list, use the --limit flag.

**Synopsis:**
```
gcloud managed-kafka consumer-groups list (CLUSTER : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - Identifies the cluster which contains all the consumer
groups to be listed. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
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
To list all consumer groups in a cluster named mycluster located in
us-central1, run the following:

    $ gcloud managed-kafka consumer-groups list mycluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/consumer-groups/list)

---
### `gcloud managed-kafka consumer-groups update`

Update a Managed Service for Apache Kafka consumer group

Update a Managed Service for Apache Kafka consumer group.

**Synopsis:**
```
gcloud managed-kafka consumer-groups update
    (CONSUMER_GROUP : --cluster=CLUSTER --location=LOCATION)
    --topics-file=JSON|YAML|FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Consumer group resource - Identifies the consumer group to be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument consumer_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONSUMER_GROUP
     ID of the consumer_group or fully qualified identifier for the
     consumer_group.

     To set the consumer_group attribute:
     + provide the argument consumer_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --cluster=CLUSTER
     The cluster name.

     To set the cluster attribute:
     + provide the argument consumer_group on the command line with a
       fully specified name;
     + provide the argument --cluster on the command line.

  --location=LOCATION
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument consumer_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--topics-file` | JSON\|YAML\|FILE |  | The path to the JSON or YAML file containing the configuration of the topics to be updated for the consumer group. This also supports inline JSON or YAML. Required, sets topics_file value. Input Example: --topics-file=string File Example: --topics-file=path_to_file.(yaml\|json) |


**Examples:**
```bash
To specify a file for updating the topics of a consumer group, run the
following:

    $gcloud managed-kafka consumer-groups update myconsumergroup |
        --cluster=mycluster \
        --location=us-central1 \
        --topics-file=topics.json

To update the topics of a consumer group with inline JSON, run the
following:

    $gcloud managed-kafka consumer-groups update myconsumergroup |
        --cluster=mycluster \
        --location=us-central1 \
        --topics-file='{"topic":{"partitions":{"0":{"offset":1,"metadata":"metadata"}}}}'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/consumer-groups/update)

---
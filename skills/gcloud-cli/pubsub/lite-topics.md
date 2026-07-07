# gcloud pubsub lite-topics

manage Pub/Sub Lite topics

### `gcloud pubsub lite-topics create`

Create a Pub/Sub Lite topic

Create a Pub/Sub Lite topic.

**Synopsis:**
```
gcloud pubsub lite-topics create TOPIC --partitions=PARTITIONS
    --per-partition-bytes=PER_PARTITION_BYTES [--location=LOCATION]
    [--message-retention-period=MESSAGE_RETENTION_PERIOD]
    [--per-partition-publish-mib=PER_PARTITION_PUBLISH_MIB]
    [--per-partition-subscribe-mib=PER_PARTITION_SUBSCRIBE_MIB]
    [--throughput-reservation=THROUGHPUT_RESERVATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TOPIC
   Topic ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--partitions` | PARTITIONS |  | Number of partitions in the topic. |
| `--per-partition-bytes` | PER_PARTITION_BYTES |  | Provisioned storage, in bytes, per partition. If the number of bytes stored in any of the topic's partitions exceeds this value, older messages will be dropped to make room for newer ones, regardless of the value of message-retention-period. A valid example value of this flag would be per-partition-bytes=30GiB. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + provide the argument --zone on the command line. |
| `--message-retention-period` | MESSAGE_RETENTION_PERIOD |  | _[* set the property core/project.]_ How long a published message is retained. If unset, messages will only be dropped to make space for new ones once the per-partition-bytes limit is reached. A valid example value of this flag would be message-retention-period="2w". |
| `--per-partition-publish-mib` | PER_PARTITION_PUBLISH_MIB |  | _[* set the property core/project.]_ Topic partition publish throughput capacity in MiB/s. Must be between 4 and 16. |
| `--per-partition-subscribe-mib` | PER_PARTITION_SUBSCRIBE_MIB |  | _[* set the property core/project.]_ Topic partition subscribe throughput capacity in MiB/s. Must be between 4 and 32. |
| `--throughput-reservation` | THROUGHPUT_RESERVATION |  | _[* set the property core/project.]_ Reservation ID to use for topic throughput. |


**Examples:**
```bash
To create a Pub/Sub lite-topic, run:

    $ gcloud pubsub lite-topics create mytopic \
      --location=us-central1-a --partitions=1 \
      --per-partition-bytes=30GiB --message-retention-period=2w
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/create)

---
### `gcloud pubsub lite-topics delete`

Delete a Pub/Sub Lite topic

Delete a Pub/Sub Lite topic.

**Synopsis:**
```
gcloud pubsub lite-topics delete (TOPIC : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Topic to delete. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
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

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To delete a Pub/Sub Lite topic, run:

    $ gcloud pubsub lite-topics delete mytopic --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/delete)

---
### `gcloud pubsub lite-topics describe`

Describe a Pub/Sub Lite topic

Describe a Pub/Sub Lite topic.

**Synopsis:**
```
gcloud pubsub lite-topics describe (TOPIC : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Topic to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To describe a Pub/Sub Lite topic, run:

    $ gcloud pubsub lite-topics describe mytopic --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/describe)

---
### `gcloud pubsub lite-topics list`

List Pub/Sub Lite topics

List Pub/Sub Lite topics.

**Synopsis:**
```
gcloud pubsub lite-topics list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + provide the argument --zone on the command line. |


**Examples:**
```bash
To list Pub/Sub Lite topics, run:

    $ gcloud pubsub lite-topics list --location=us-central1-a --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/list)

---
### `gcloud pubsub lite-topics list-subscriptions`

List Pub/Sub Lite subscriptions for a given Lite topic

List Pub/Sub Lite subscriptions for a given Lite topic.

**Synopsis:**
```
gcloud pubsub lite-topics list-subscriptions (TOPIC : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Topic to list subscriptions for. The arguments in this
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

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To list Pub/Sub Lite subscriptions for a given Lite topic, run:

    $ gcloud pubsub lite-topics list-subscriptions mytopic \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/list-subscriptions)

---
### `gcloud pubsub lite-topics publish`

Publish Pub/Sub Lite messages

Publishes a message to the specified Pub/Sub Lite topic. This command
requires Python 3.6 or greater, and requires the grpcio Python package to
be installed.

For MacOS, Linux, and Cloud Shell users, to install the gRPC client
libraries, run:

    $ sudo pip3 install grpcio
    $ export CLOUDSDK_PYTHON_SITEPACKAGES=1

**Synopsis:**
```
gcloud pubsub lite-topics publish (TOPIC : --location=LOCATION)
    [--attributes=[KEY=VALUE,...]] [--event-time=DATETIME]
    [--message=MESSAGE] [--ordering-key=ORDERING_KEY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - The pubsub lite topic to publish to. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [KEY=VALUE,...] |  | Comma-separated list of attributes. Each ATTRIBUTE has the form name="value". You can specify up to 100 attributes. |
| `--event-time` | DATETIME |  | A user-specified event time. Run gcloud topic datetimes for information on time formats. |
| `--message` | MESSAGE |  | The body of the message to publish to the given topic name. |
| `--ordering-key` | ORDERING_KEY |  | A string key, used for ordering delivery to subscribers. All messages with the same ordering key will be assigned to the same partition for ordered delivery. |


**Examples:**
```bash
To publish a message to a Pub/Sub Lite topic, run:

    $ gcloud pubsub lite-topics publish mytopic \
        --location=us-central1-a --message="Hello World!"

To publish a message to a Pub/Sub Lite topic with an ordering key and
attributes, run:

    $ gcloud pubsub lite-topics publish mytopic \
        --location=us-central1-a --message="Hello World!" \
        --ordering-key="key" --attributes=KEY1=VAL1,KEY2=VAL2

To publish a message to a Pub/Sub Lite topic with an event time, run:

    $ gcloud pubsub lite-topics publish mytopic \
        --location=us-central1-a --message="Hello World!" \
        --event-time="2021-01-01T12:00:00Z"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/publish)

---
### `gcloud pubsub lite-topics update`

Update a Pub/Sub Lite topic

Update a Pub/Sub Lite topic.

**Synopsis:**
```
gcloud pubsub lite-topics update (TOPIC : --location=LOCATION)
    (--message-retention-period=MESSAGE_RETENTION_PERIOD
      --partitions=PARTITIONS --per-partition-bytes=PER_PARTITION_BYTES
      --per-partition-publish-mib=PER_PARTITION_PUBLISH_MIB
      --per-partition-subscribe-mib=PER_PARTITION_SUBSCRIBE_MIB
      --throughput-reservation=THROUGHPUT_RESERVATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Topic to update. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
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

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument topic on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--message-retention-period` | MESSAGE_RETENTION_PERIOD |  | _[At least one of these must be specified:]_ How long a published message is retained. If unset, messages will only be dropped to make space for new ones once the per-partition-bytes limit is reached. A valid example value of this flag would be message-retention-period="2w". |
| `--partitions` | PARTITIONS |  | _[At least one of these must be specified:]_ Number of partitions in the topic. |
| `--per-partition-bytes` | PER_PARTITION_BYTES |  | _[At least one of these must be specified:]_ Provisioned storage, in bytes, per partition. If the number of bytes stored in any of the topic's partitions exceeds this value, older messages will be dropped to make room for newer ones, regardless of the value of message-retention-period. A valid example value of this flag would be per-partition-bytes=30GiB. |
| `--per-partition-publish-mib` | PER_PARTITION_PUBLISH_MIB |  | _[At least one of these must be specified:]_ Topic partition publish throughput capacity in MiB/s. Must be between 4 and 16. |
| `--per-partition-subscribe-mib` | PER_PARTITION_SUBSCRIBE_MIB |  | _[At least one of these must be specified:]_ Topic partition subscribe throughput capacity in MiB/s. Must be between 4 and 32. |
| `--throughput-reservation` | THROUGHPUT_RESERVATION |  | _[At least one of these must be specified:]_ Reservation ID to use for topic throughput. |


**Examples:**
```bash
To update a Pub/Sub Lite topic, run:

    $ gcloud pubsub lite-topics update mytopic \
      --location=us-central1-a --per-partition-publish-mib=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-topics/update)

---
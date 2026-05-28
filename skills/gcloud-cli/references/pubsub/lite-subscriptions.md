# gcloud pubsub lite-subscriptions

manage Pub/Sub Lite subscriptions

### `gcloud pubsub lite-subscriptions ack-up-to`

Acknowledge messages on a Pub/Sub Lite subscription

Acknowledge all messages on a Pub/Sub Lite subscription up to the provided
offset. The message corresponding to the provided offset will be included
in the list of messages that are acknowledged.

**Synopsis:**
```
gcloud pubsub lite-subscriptions ack-up-to
    (SUBSCRIPTION : --location=LOCATION) --offset=OFFSET
    --partition=PARTITION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Subscription on which to acknowledge messages. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument subscription on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--offset` | OFFSET |  | The offset of a message within a topic partition. Must be greater than or equal to 0. |
| `--partition` | PARTITION |  | The topic partition. Partitions are zero indexed, so the partition must be in the range [0, topic.num_partitions). If you do not know your topic.num_partitions, run gcloud pubsub lite-topic describe TOPIC --location=ZONE. |


**Examples:**
```bash
To acknowledge messages on a Pub/Sub Lite subscription, run:

    $ gcloud pubsub lite-subscriptions ack-up-to mysubscription \
      --location=us-central1-a --partition=0 --offset=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/ack-up-to)

---
### `gcloud pubsub lite-subscriptions create`

Create a Pub/Sub Lite subscription

Create a Pub/Sub Lite subscription.

**Synopsis:**
```
gcloud pubsub lite-subscriptions create SUBSCRIPTION --topic=TOPIC
    [--delivery-requirement=DELIVERY_REQUIREMENT;
      default="deliver-immediately"] [--location=LOCATION]
    [--event-time=EVENT_TIME | --publish-time=PUBLISH_TIME
      | --starting-offset=STARTING_OFFSET; default="end"]
    [--export-pubsub-topic=EXPORT_PUBSUB_TOPIC
      : --export-dead-letter-topic=EXPORT_DEAD_LETTER_TOPIC
      --export-desired-state=EXPORT_DESIRED_STATE; default="active"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SUBSCRIPTION
   Subscription ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--topic` | TOPIC |  | Topic ID associated with the subscription. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delivery-requirement` | one of: deliver-after-stored, deliver-immediately | deliver-immediately | When this subscription should send messages to subscribers relative to messages persistence in storage. See https://cloud.google.com/pubsub/lite/docs/subscriptions#creating_lite_subscriptions for more info. DELIVERY_REQUIREMENT must be one of: deliver-after-stored, deliver-immediately. |
| `--export-pubsub-topic` | EXPORT_PUBSUB_TOPIC |  | _[offset (end). STARTING_OFFSET must be one of: beginning, end.]_ The name of the destination Pub/Sub topic to which messages are exported. Must be the topic's fully specified path if it is not in the same project as the subscription to be created. |
| `--export-dead-letter-topic` | EXPORT_DEAD_LETTER_TOPIC |  | _[offset (end). STARTING_OFFSET must be one of: beginning, end.]_ The name of the Pub/Sub Lite topic to write messages that cannot be exported. Must be in the same project and location as the subscription to be created. Note that this is a Lite topic. |
| `--export-desired-state` | one of: active, paused | active | _[offset (end). STARTING_OFFSET must be one of: beginning, end.]_ The desired state of the export. Process messages by setting the value to ACTIVE or pause message processing by setting the value to PAUSED. EXPORT_DESIRED_STATE must be one of: active, paused. |


**Examples:**
```bash
To create a Pub/Sub Lite subscription, run:

    $ gcloud pubsub lite-subscriptions create mysubscription \
      --location=us-central1-a --topic=mytopic

To create a Pub/Sub Lite subscription at the offset of the oldest retained
message, run:

    $ gcloud pubsub lite-subscriptions create mysubscription \
      --location=us-central1-a --topic=mytopic \
      --starting-offset=beginning

To create a Pub/Sub Lite subscription that exports messages from a Pub/Sub
Lite topic to a Pub/Sub topic, run:

    $ gcloud pubsub lite-subscriptions create mysubscription \
      --location=us-central1-a --topic=mytopic \
      --export-pubsub-topic=pubsubtopic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/create)

---
### `gcloud pubsub lite-subscriptions delete`

Delete a Pub/Sub Lite subscription

Delete a Pub/Sub Lite subscription.

**Synopsis:**
```
gcloud pubsub lite-subscriptions delete
    (SUBSCRIPTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Subscription to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument subscription on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To delete a Pub/Sub Lite subscription, run:

    $ gcloud pubsub lite-subscriptions delete mysubscription \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/delete)

---
### `gcloud pubsub lite-subscriptions describe`

Describe a Pub/Sub Lite subscription

Describe a Pub/Sub Lite subscription.

**Synopsis:**
```
gcloud pubsub lite-subscriptions describe
    (SUBSCRIPTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Subscription to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument subscription on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To describe a Pub/Sub Lite subscription, run:

    $ gcloud pubsub lite-subscriptions describe mysubscription \
      --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/describe)

---
### `gcloud pubsub lite-subscriptions list`

List Pub/Sub Lite subscriptions

List Pub/Sub Lite subscriptions.

**Synopsis:**
```
gcloud pubsub lite-subscriptions list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + provide the argument --zone on the command line. |


**Examples:**
```bash
To list Pub/Sub Lite subscriptions, run:

    $ gcloud pubsub lite-subscriptions list --location=us-central1-a \
      --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/list)

---
### `gcloud pubsub lite-subscriptions seek`

Seek a Pub/Sub Lite subscription

Initiate an out-of-band seek operation for a Pub/Sub Lite subscription to a
specified target, which may be timestamps or named locations within the
message backlog.

The seek operation will complete once subscriber clients react to the seek
for all partitions of the topic. Note that the seek operation will not
complete until subscribers are online. It may take some time (usually
within 30 seconds) for the seek to propagate if subscribers are online. Use
the --async flag if it's not necessary to wait for completion.

**Synopsis:**
```
gcloud pubsub lite-subscriptions seek (SUBSCRIPTION : --location=LOCATION)
    (--event-time=EVENT_TIME | --publish-time=PUBLISH_TIME
      | --starting-offset=STARTING_OFFSET) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Subscription to seek. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument subscription on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--event-time` | EVENT_TIME |  | _[Exactly one of these must be specified:]_ The event time to which you seek a subscription. The subscription seeks to the first message with event time greater than or equal to the specified event time. Messages missing an event time use publish time as a fallback. As event times are user supplied, subsequent messages may have event times less than the specified event time and must be filtered by the client, if necessary. Run $ gcloud topic datetimes for information on time formats. |
| `--publish-time` | PUBLISH_TIME |  | _[Exactly one of these must be specified:]_ The publish time to which you seek a subscription. Messages with publish time greater than or equal to the specified time are delivered after the seek operation. Run $ gcloud topic datetimes for information on time formats. |
| `--starting-offset` | one of: beginning, end |  | _[Exactly one of these must be specified:]_ The offset at which a newly created or seeked subscription starts receiving messages. A subscription can be initialized at the offset of the oldest retained message (beginning), or at the current HEAD offset (end). STARTING_OFFSET must be one of: beginning, end. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To seek a Pub/Sub Lite subscription to the beginning of the message
backlog, run:

    $ gcloud pubsub lite-subscriptions seek mysubscription \
      --location=us-central1-a --starting-offset=beginning

To seek a Pub/Sub Lite subscription to a publish time without waiting for
the operation to complete, run:

    $ gcloud pubsub lite-subscriptions seek mysubscription \
      --location=us-central1-a --publish-time="2021-01-01T12:00:00Z" \
      --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/seek)

---
### `gcloud pubsub lite-subscriptions subscribe`

Stream messages from a Pub/Sub Lite subscription

Streams messages from a Pub/Sub Lite subscription. This command requires
Python 3.6 or greater, and requires the grpcio Python package to be
installed.

For MacOS, Linux, and Cloud Shell users, to install the gRPC client
libraries, run:

    $ sudo pip3 install grpcio
    $ export CLOUDSDK_PYTHON_SITEPACKAGES=1

**Synopsis:**
```
gcloud pubsub lite-subscriptions subscribe
    (SUBSCRIPTION : --location=LOCATION) [--auto-ack]
    [--num-messages=NUM_MESSAGES; default=1] [--partitions=[INT,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - The Pub/Sub Lite subscription to receive messages
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument subscription on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-ack` |  |  | Automatically ACK every message received on this subscription. |
| `--num-messages` | NUM_MESSAGES | 1 | The number of messages to stream before exiting. This value must be less than or equal to 1000. |
| `--partitions` | [INT,...] |  | The partitions this subscriber should connect to to receive messages. If empty, partitions will be automatically assigned. |


**Examples:**
```bash
To subscribe to a Pub/Sub Lite subscription and automatically acknowledge
messages, run:

    $ gcloud pubsub lite-subscriptions subscribe mysubscription \
        --location=us-central1-a --auto-ack

To subscribe to specific partitions in a subscription, run:

    $ gcloud pubsub lite-subscriptions subscribe mysubscription \
        --location=us-central1-a --partitions=0,1,2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/subscribe)

---
### `gcloud pubsub lite-subscriptions update`

Update a Pub/Sub Lite subscription

Update a Pub/Sub Lite subscription.

**Synopsis:**
```
gcloud pubsub lite-subscriptions update
    (SUBSCRIPTION : --location=LOCATION)
    (--delivery-requirement=DELIVERY_REQUIREMENT
      --export-dead-letter-topic=EXPORT_DEAD_LETTER_TOPIC
      --export-desired-state=EXPORT_DESIRED_STATE
      --export-pubsub-topic=EXPORT_PUBSUB_TOPIC) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Subscription to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument subscription on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delivery-requirement` | one of: deliver-after-stored, deliver-immediately |  | _[At least one of these must be specified:]_ When this subscription should send messages to subscribers relative to messages persistence in storage. See https://cloud.google.com/pubsub/lite/docs/subscriptions#creating_lite_subscriptions for more info. DELIVERY_REQUIREMENT must be one of: deliver-after-stored, deliver-immediately. |
| `--export-dead-letter-topic` | EXPORT_DEAD_LETTER_TOPIC |  | _[At least one of these must be specified:]_ The name of the Pub/Sub Lite topic to write messages that cannot be exported. Must be in the same project and location as the subscription to be created. Note that this is a Lite topic. |
| `--export-desired-state` | one of: active, paused |  | _[At least one of these must be specified:]_ The desired state of the export. Process messages by setting the value to ACTIVE or pause message processing by setting the value to PAUSED. EXPORT_DESIRED_STATE must be one of: active, paused. |
| `--export-pubsub-topic` | EXPORT_PUBSUB_TOPIC |  | _[At least one of these must be specified:]_ The name of the destination Pub/Sub topic to which messages are exported. Must be the topic's fully specified path if it is not in the same project as the subscription to be created. |


**Examples:**
```bash
To update a Pub/Sub Lite subscription, run:

    $ gcloud pubsub lite-subscriptions update mysubscription \
      --location=us-central1-a \
      --delivery-requirement=DELIVER_IMMEDIATELY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-subscriptions/update)

---
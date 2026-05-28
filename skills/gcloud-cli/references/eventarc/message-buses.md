# gcloud eventarc message-buses

manage Eventarc message buses

### `gcloud eventarc message-buses create`

Create an Eventarc message bus

Create an Eventarc message bus.

**Synopsis:**
```
gcloud eventarc message-buses create (MESSAGE_BUS : --location=LOCATION)
    [--async] [--crypto-key=CRYPTO_KEY] [--labels=[KEY=VALUE,...]]
    [--logging-config=LOGGING_CONFIG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Message bus resource - The message bus to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument message_bus on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESSAGE_BUS
     ID of the message bus or fully qualified identifier for the message
     bus.

     To set the message-bus attribute:
     + provide the argument message_bus on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc message bus, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument message_bus on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--crypto-key` | CRYPTO_KEY |  | Fully qualified name of the crypto key to use for customer-managed encryption. If this is unspecified, Google-managed keys will be used for encryption. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--logging-config` | one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY |  | The logging config of the message bus. LOGGING_CONFIG must be one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY. |


**Examples:**
```bash
To create a new message bus my-message-bus in location us-central1, run:

    $ gcloud eventarc message-buses create my-message-bus \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/create)

---
### `gcloud eventarc message-buses delete`

Delete an Eventarc message bus

Delete an Eventarc message bus.

**Synopsis:**
```
gcloud eventarc message-buses delete (MESSAGE_BUS : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Message bus resource - Message bus to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument message_bus on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESSAGE_BUS
     ID of the message bus or fully qualified identifier for the message
     bus.

     To set the message-bus attribute:
     + provide the argument message_bus on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc message bus, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument message_bus on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the message bus my-message-bus in location us-central1, run:

    $ gcloud eventarc message-buses delete my-message-bus \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/delete)

---
### `gcloud eventarc message-buses describe`

Describe an Eventarc message bus

Describe an Eventarc message bus.

**Synopsis:**
```
gcloud eventarc message-buses describe (MESSAGE_BUS : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Message bus resource - Message bus to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument message_bus on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESSAGE_BUS
     ID of the message bus or fully qualified identifier for the message
     bus.

     To set the message-bus attribute:
     + provide the argument message_bus on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc message bus, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument message_bus on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the message bus my-message-bus in location us-central1, run:

    $ gcloud eventarc message-buses describe my-message-bus \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/describe)

---
### `gcloud eventarc message-buses list`

List Eventarc message buses

List Eventarc message buses.

**Synopsis:**
```
gcloud eventarc message-buses list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |


**Examples:**
```bash
To list all message buses in location us-central1, run:

    $ gcloud eventarc message-buses list --location=us-central1

To list all message buses in all locations, run:

    $ gcloud eventarc message-buses list --location=-

or

    $ gcloud eventarc message-buses list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/list)

---
### `gcloud eventarc message-buses list-enrollments`

List Eventarc enrollments attached to an Eventarc message bus

List Eventarc enrollments attached to an Eventarc message bus.

**Synopsis:**
```
gcloud eventarc message-buses list-enrollments
    (MESSAGE_BUS : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Message bus resource - The message bus on which to list enrollments. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument message_bus on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESSAGE_BUS
     ID of the message bus or fully qualified identifier for the message
     bus.

     To set the message-bus attribute:
     + provide the argument message_bus on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc message bus, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument message_bus on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To list all enrollments in message-bus my-message-bus in us-central1, run:

    $ gcloud eventarc message-buses list-enrollments my-message-bus \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/list-enrollments)

---
### `gcloud eventarc message-buses publish`

Publish to an Eventarc message bus

Publish to an Eventarc message bus.

**Synopsis:**
```
gcloud eventarc message-buses publish (MESSAGE_BUS : --location=LOCATION)
    (--avro-message=AVRO_MESSAGE | --json-message=JSON_MESSAGE
      | [--event-data=EVENT_DATA --event-id=EVENT_ID
      --event-source=EVENT_SOURCE --event-type=EVENT_TYPE
      : --event-attributes=[ATTRIBUTE=VALUE,...]]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Message bus resource - Message bus to publish to. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument message_bus on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESSAGE_BUS
     ID of the message bus or fully qualified identifier for the message
     bus.

     To set the message-bus attribute:
     + provide the argument message_bus on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc message bus, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument message_bus on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--avro-message` | AVRO_MESSAGE |  | _[Exactly one of these must be specified:]_ An Avro message to publish to the message bus. |
| `--json-message` | JSON_MESSAGE |  | _[Exactly one of these must be specified:]_ A JSON message to publish to the message bus. |
| `--event-data` | EVENT_DATA |  | _[Exactly one of these must be specified:]_ An event data. The event data of a published event. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--event-id` | EVENT_ID |  | _[Exactly one of these must be specified:]_ An event id. The id of a published event. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--event-source` | EVENT_SOURCE |  | _[Exactly one of these must be specified:]_ An event source. The event source of a published event. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--event-type` | EVENT_TYPE |  | _[Exactly one of these must be specified:]_ An event type. The event type of a published event. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--event-attributes` | [ATTRIBUTE=VALUE,...] |  | _[Exactly one of these must be specified:]_ Event attributes. The event attributes of a published event.This flag can be repeated to add more attributes. |


**Examples:**
```bash
To publish an event to the message bus my-message-bus with event id 1234,
event type event-provider.event.v1.eventType, event source
//event-provider/event/source, event data { "key": "value" } and event
attributes of attribute1=value, run:

    $ gcloud eventarc message-buses publish my-message-bus \
        --location=us-central1 --event-id=1234 \
        --event-type=event-provider.event.v1.eventType \
        --event-source="//event-provider/event/source" \
        --event-data='{"key": "value"}' \
        --event-attributes=attribute1=value

To publish an event to the message bus my-message-bus with a json message,
run:

    $ gcloud eventarc message-buses publish my-message-bus \
        --location=us-central1 \
        --json-message='{"id": 1234, "type":
     "event-provider.event.v1.eventType", "source":
     "//event-provider/event/source", "specversion": "1.0", "data":
     {"key": "value"}}'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/publish)

---
### `gcloud eventarc message-buses update`

Update an Eventarc message bus

Update an Eventarc message bus.

**Synopsis:**
```
gcloud eventarc message-buses update (MESSAGE_BUS : --location=LOCATION)
    [--async] [--logging-config=LOGGING_CONFIG]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-crypto-key | --crypto-key=CRYPTO_KEY]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Message bus resource - Message bus to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument message_bus on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESSAGE_BUS
     ID of the message bus or fully qualified identifier for the message
     bus.

     To set the message-bus attribute:
     + provide the argument message_bus on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc message bus, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument message_bus on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--logging-config` | one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY |  | The logging config of the message bus. LOGGING_CONFIG must be one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the message bus my-message-bus in location us-central1, run:

    $ gcloud eventarc message-buses update my-message-bus \
        --location=us-central1

To configure the message bus my-message-bus in location us-central1 with a
Cloud KMS CryptoKey, run:

    $ gcloud eventarc message-buses update my-message-bus \
        --location=us-central1 \
        --crypto-key=projects/PROJECT_ID/locations/KMS_LOCATION/\
    keyRings/KEYRING/cryptoKeys/KEY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/message-buses/update)

---
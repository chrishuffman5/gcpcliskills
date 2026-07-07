# gcloud eventarc channel-connections

manage Eventarc channel connections

### `gcloud eventarc channel-connections create`

Create an Eventarc channel connection

Create an Eventarc channel connection.

**Synopsis:**
```
gcloud eventarc channel-connections create
    (CHANNEL_CONNECTION : --location=LOCATION)
    --activation-token=ACTIVATION_TOKEN --channel=CHANNEL [--async]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel connection resource - Channel connection to create. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument channel_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL_CONNECTION
     ID of the channel connection or fully qualified identifier for the
     channel connection.

     To set the channel-connection attribute:
     + provide the argument channel_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel connection, which should be
     either global or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activation-token` | ACTIVATION_TOKEN |  | Activation token for the specified channel. |
| `--channel` | CHANNEL |  | Subscriber channel for which to create the channel connection. This argument should be the full channel name, including project, location and the channel id. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the channel connection. |


**Examples:**
```bash
To create a new channel connection my-channel-connection for channel
my-channel with activation token channel-activation-token, run:

    $ gcloud eventarc channel-connections create my-channel-connection \
        --channel=my-channel --activation-token=channel-activation-token
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channel-connections/create)

---
### `gcloud eventarc channel-connections delete`

Delete an Eventarc channel connection

Delete an Eventarc channel connection.

**Synopsis:**
```
gcloud eventarc channel-connections delete
    (CHANNEL_CONNECTION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel connection resource - Channel connection to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument channel_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL_CONNECTION
     ID of the channel connection or fully qualified identifier for the
     channel connection.

     To set the channel-connection attribute:
     + provide the argument channel_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel connection, which should be
     either global or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the channel connection my-channel-connection in location
us-central1, run:

    $ gcloud eventarc channel-connections delete my-channel-connection \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channel-connections/delete)

---
### `gcloud eventarc channel-connections describe`

Describe an Eventarc channel connection

Describe an Eventarc channel connection.

**Synopsis:**
```
gcloud eventarc channel-connections describe
    (CHANNEL_CONNECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel connection resource - Channel connection to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument channel_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL_CONNECTION
     ID of the channel connection or fully qualified identifier for the
     channel connection.

     To set the channel-connection attribute:
     + provide the argument channel_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel connection, which should be
     either global or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the channel connection my-channel-connection in location
us-central1, run:

    $ gcloud eventarc channel-connections describe \
        my-channel-connection --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channel-connections/describe)

---
### `gcloud eventarc channel-connections list`

List Eventarc channel connections

List Eventarc channel connections.

**Synopsis:**
```
gcloud eventarc channel-connections list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |


**Examples:**
```bash
To list all channel connections in location us-central1, run:

    $ gcloud eventarc channel-connections list --location=us-central1

To list all channel connections in all locations, run:

    $ gcloud eventarc channel-connections list --location=-

or

    $ gcloud eventarc channel-connections list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channel-connections/list)

---
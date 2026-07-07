# gcloud eventarc channels

manage Eventarc channels

### `gcloud eventarc channels create`

Create an Eventarc channel

Create an Eventarc channel.

**Synopsis:**
```
gcloud eventarc channels create (CHANNEL : --location=LOCATION) [--async]
    [--crypto-key=CRYPTO_KEY] [--labels=[KEY=VALUE,...]]
    [--provider=PROVIDER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel resource - Channel to create. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument channel on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL
     ID of the channel or fully qualified identifier for the channel.

     To set the channel attribute:
     + provide the argument channel on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel on the command line with a fully
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


**Examples:**
```bash
To create a new channel my-channel in location us-central1, run:

    $ gcloud eventarc channels create my-channel --location=us-central1

To create a new channel my-channel in location us-central1 with a Cloud KMS
CryptoKey, run:

    $ gcloud eventarc channels create my-channel \
        --location=us-central1 \
        --crypto-key=projects/PROJECT_ID/locations/KMS_LOCATION/\
    keyRings/KEYRING/cryptoKeys/KEY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channels/create)

---
### `gcloud eventarc channels delete`

Delete an Eventarc channel

Delete an Eventarc channel.

**Synopsis:**
```
gcloud eventarc channels delete (CHANNEL : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel resource - Channel to delete. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument channel on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL
     ID of the channel or fully qualified identifier for the channel.

     To set the channel attribute:
     + provide the argument channel on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel on the command line with a fully
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
To delete the channel my-channel in location us-central1, run:

    $ gcloud eventarc channels delete my-channel --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channels/delete)

---
### `gcloud eventarc channels describe`

Describe an Eventarc channel

Describe an Eventarc channel.

**Synopsis:**
```
gcloud eventarc channels describe (CHANNEL : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel resource - Channel to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument channel on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL
     ID of the channel or fully qualified identifier for the channel.

     To set the channel attribute:
     + provide the argument channel on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the channel my-channel in location us-central1, run:

    $ gcloud eventarc channels describe my-channel --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channels/describe)

---
### `gcloud eventarc channels list`

List Eventarc channels

List Eventarc channels.

**Synopsis:**
```
gcloud eventarc channels list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |


**Examples:**
```bash
To list all channels in location us-central1, run:

    $ gcloud eventarc channels list --location=us-central1

To list all channels in all locations, run:

    $ gcloud eventarc channels list --location=-

or

    $ gcloud eventarc channels list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channels/list)

---
### `gcloud eventarc channels update`

Update an Eventarc channel

Update an Eventarc channel.

**Synopsis:**
```
gcloud eventarc channels update (CHANNEL : --location=LOCATION) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-crypto-key | --crypto-key=CRYPTO_KEY]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Channel resource - Channel to update. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument channel on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CHANNEL
     ID of the channel or fully qualified identifier for the channel.

     To set the channel attribute:
     + provide the argument channel on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc channel, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument channel on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the channel my-channel in location us-central1, run:

    $ gcloud eventarc channels update my-channel --location=us-central1

To configure the channel my-channel in location us-central1 with a Cloud
KMS CryptoKey, run:

    $ gcloud eventarc channels update my-channel \
        --location=us-central1 \
        --crypto-key=projects/PROJECT_ID/locations/KMS_LOCATION/\
    keyRings/KEYRING/cryptoKeys/KEY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/channels/update)

---
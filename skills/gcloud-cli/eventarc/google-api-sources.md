# gcloud eventarc google-api-sources

manage Eventarc Google API sources

### `gcloud eventarc google-api-sources create`

Create an Eventarc Google API source

Create an Eventarc Google API source.

**Synopsis:**
```
gcloud eventarc google-api-sources create
    (GOOGLE_API_SOURCE : --location=LOCATION)
    (--destination-message-bus=DESTINATION_MESSAGE_BUS
      : --destination-message-bus-project=DESTINATION_MESSAGE_BUS_PROJECT)
    [--async] [--crypto-key=CRYPTO_KEY] [--labels=[KEY=VALUE,...]]
    [--logging-config=LOGGING_CONFIG]
    [--[no-]organization-subscription
      | --project-subscriptions=GAS_PROJECT_SUBSCRIPTION,[...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Google API source resource - The Google API source to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument google_api_source on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GOOGLE_API_SOURCE
     ID of the Google API source or fully qualified identifier for the
     Google API source.

     To set the google-api-source attribute:
     + provide the argument google_api_source on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc Google API source, which should be one
     of the supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument google_api_source on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-message-bus` | DESTINATION_MESSAGE_BUS |  | _[This must be specified.]_ ID of the message bus or fully qualified identifier for the message bus. To set the message-bus attribute: + provide the argument --destination-message-bus on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--destination-message-bus-project` | DESTINATION_MESSAGE_BUS_PROJECT |  | _[This must be specified.]_ Project ID of the Google Cloud project for the message bus. To set the project attribute: + provide the argument --destination-message-bus on the command line with a fully specified name; + provide the argument --destination-message-bus-project on the command line; + provide the argument --project on the command line; + set the property core/project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--crypto-key` | CRYPTO_KEY |  | Fully qualified name of the crypto key to use for customer-managed encryption. If this is unspecified, Google-managed keys will be used for encryption. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--logging-config` | one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY |  | The logging config for the Google API source. LOGGING_CONFIG must be one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY. |


**Examples:**
```bash
To create a new Google API source my-google-api-source in location
us-central1 with a destination message bus my-message-bus, run:

    $ gcloud eventarc google-api-sources create my-google-api-source \
         --location=us-central1 --destination-message-bus=my-message-bus
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-api-sources/create)

---
### `gcloud eventarc google-api-sources delete`

Delete an Eventarc Google API source

Delete an Eventarc Google API source.

**Synopsis:**
```
gcloud eventarc google-api-sources delete
    (GOOGLE_API_SOURCE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Google API source resource - Google API source to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument google_api_source on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GOOGLE_API_SOURCE
     ID of the Google API source or fully qualified identifier for the
     Google API source.

     To set the google-api-source attribute:
     + provide the argument google_api_source on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc Google API source, which should be one
     of the supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument google_api_source on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the Google API source my-google-api-source in location
us-central1, run:

    $ gcloud eventarc google-api-sources delete my-google-api-source \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-api-sources/delete)

---
### `gcloud eventarc google-api-sources describe`

Describe an Eventarc Google API source

Describe an Eventarc Google API source.

**Synopsis:**
```
gcloud eventarc google-api-sources describe
    (GOOGLE_API_SOURCE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Google API source resource - Google API source to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument google_api_source on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GOOGLE_API_SOURCE
     ID of the Google API source or fully qualified identifier for the
     Google API source.

     To set the google-api-source attribute:
     + provide the argument google_api_source on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc Google API source, which should be one
     of the supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument google_api_source on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the google API source my-google-api-source in location
us-central1, run:

    $ gcloud eventarc google-api-sources describe my-google-api-source \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-api-sources/describe)

---
### `gcloud eventarc google-api-sources list`

List Eventarc Google API sources

List Eventarc Google API sources.

**Synopsis:**
```
gcloud eventarc google-api-sources list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |


**Examples:**
```bash
To list all Google API sources in location us-central1, run:

    $ gcloud eventarc google-api-sources list --location=us-central1

To list all Google API sources in all locations, run:

    $ gcloud eventarc google-api-sources list --location=-

or

    $ gcloud eventarc google-api-sources list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-api-sources/list)

---
### `gcloud eventarc google-api-sources update`

Update an Eventarc Google API source

Update an Eventarc Google API source.

**Synopsis:**
```
gcloud eventarc google-api-sources update
    (GOOGLE_API_SOURCE : --location=LOCATION) [--async]
    [--logging-config=LOGGING_CONFIG] [--update-labels=[KEY=VALUE,...]]
    [--clear-crypto-key | --crypto-key=CRYPTO_KEY]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-project-subscriptions | --[no-]organization-subscription
      | --project-subscriptions=GAS_PROJECT_SUBSCRIPTION,[...]]
    [--destination-message-bus=DESTINATION_MESSAGE_BUS
      : --destination-message-bus-project=DESTINATION_MESSAGE_BUS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Google API source resource - The Google API source to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument google_api_source on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GOOGLE_API_SOURCE
     ID of the Google API source or fully qualified identifier for the
     Google API source.

     To set the google-api-source attribute:
     + provide the argument google_api_source on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc Google API source, which should be one
     of the supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument google_api_source on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--logging-config` | one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY |  | The logging config of the Google API source. LOGGING_CONFIG must be one of: NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the Google API source my-google-api-source in location
us-central1 with destination message bus my-message-bus, run:

    $ gcloud eventarc google-api-sources update my-google-api-source \
        --location=us-central1 --destination-message-bus=my-message-bus

To update the Google API source my-google-api-source in location
us-central1 with INFO level logging, run:

    $ gcloud eventarc google-api-sources update my-google-api-source \
        --location=us-central1 --logging-config=INFO

To update the Google API source my-google-api-source in location
us-central1 with a Cloud KMS CryptoKey, run:

    $ gcloud eventarc google-api-sources update my-google-api-source \
        --location=us-central1 \
        --crypto-key=projects/PROJECT_ID/locations/KMS_LOCATION/\
    keyRings/KEYRING/cryptoKeys/KEY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-api-sources/update)

---
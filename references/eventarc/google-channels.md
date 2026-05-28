# gcloud eventarc google-channels

manage Eventarc Google channels

### `gcloud eventarc google-channels describe`

Describe an Eventarc Google channel

Describe an Eventarc Google channel.

**Synopsis:**
```
gcloud eventarc google-channels describe [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location. |


**Examples:**
```bash
To describe the Google channel in location us-central1, run:

    $ gcloud eventarc google-channels describe --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-channels/describe)

---
### `gcloud eventarc google-channels update`

Update an Eventarc Google channel

Update an Eventarc Google channel.

**Synopsis:**
```
gcloud eventarc google-channels update [--location=LOCATION]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-crypto-key | --crypto-key=CRYPTO_KEY]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location. |
| `--update-labels` | [KEY=VALUE,...] |  | _[* set the property core/project.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--clear-crypto-key` |  |  | _[At most one of these can be specified:]_ Remove the previously configured crypto key. The channel will continue to be encrypted using Google-managed keys. |
| `--crypto-key` | CRYPTO_KEY |  | _[At most one of these can be specified:]_ Fully qualified name of the crypto key to use for customer-managed encryption. If this is unspecified, Google-managed keys will be used for encryption. |
| `--clear-labels` |  |  | _[At most one of these can be specified:]_ Remove all labels. If --update-labels is also specified then --clear-labels is applied first. For example, to remove all labels: $ gcloud eventarc google-channels update --clear-labels To remove all existing labels and create two new labels, foo and baz: $ gcloud eventarc google-channels update --clear-labels \ --update-labels foo=bar,baz=qux |
| `--remove-labels` | [KEY,...] |  | _[At most one of these can be specified:]_ List of label keys to remove. If a label does not exist it is silently ignored. If --update-labels is also specified then --update-labels is applied first. |


**Examples:**
```bash
To update the Google channel in location us-central1, run:

    $ gcloud eventarc google-channels update --location=us-central1

To configure the Google channel in location us-central1 with a Cloud KMS
CryptoKey, run:

    $ gcloud eventarc google-channels update --location=us-central1 \
        --crypto-key=projects/PROJECT_ID/locations/KMS_LOCATION/\
    keyRings/KEYRING/cryptoKeys/KEY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/google-channels/update)

---
# gcloud tasks cmek-config

get or change CMEK configuration for Cloud Tasks

### `gcloud tasks cmek-config describe`

Get CMEK configuration for Cloud Tasks in the specified location

Get CMEK configuration for Cloud Tasks in the specified location.

**Synopsis:**
```
gcloud tasks cmek-config describe --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud location for the KMS key. |


**Examples:**
```bash
To get a CMEK config:

    $ gcloud tasks cmek-config describe --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/cmek-config/describe)

---
### `gcloud tasks cmek-config update`

Enable, disable, or edit CMEK configuration for Cloud Tasks in the specified location

Enable, disable, or edit CMEK configuration for Cloud Tasks in the
specified location.

**Synopsis:**
```
gcloud tasks cmek-config update [--location=LOCATION]
    [--clear-kms-key | [--kms-key-name=KMS_KEY_NAME
      : --kms-keyring=KMS_KEYRING --kms-project=KMS_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud location for the KMS key. |


**Examples:**
```bash
To update a CMEK config:

    $ gcloud tasks cmek-config update \
      --kms-key-name=projects/my-project/locations/my-location/\
    keyRings/my-keyring/cryptoKeys/key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/cmek-config/update)

---
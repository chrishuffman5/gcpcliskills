# gcloud scheduler cmek-config

manage CMEK configuration for Cloud Scheduler

### `gcloud scheduler cmek-config describe`

Get CMEK configuration for Cloud Scheduler in the specified location

Get CMEK configuration for Cloud Scheduler in the specified location.

**Synopsis:**
```
gcloud scheduler cmek-config describe --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud location for the KMS key. |


**Examples:**
```bash
To get a CMEK config:

    $ gcloud scheduler cmek-config describe --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/cmek-config/describe)

---
### `gcloud scheduler cmek-config update`

Update CMEK configuration for Cloud Scheduler in the specified location

Update CMEK configuration for Cloud Scheduler in the specified location.

**Synopsis:**
```
gcloud scheduler cmek-config update [--location=LOCATION]
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
To update a CMEK config:        $ gcloud scheduler cmek-config update --location=my-location \
      --kms-project=new-kms-project --kms-keyring=kms-keyring2 \
      --kms-key-name=crypto-key2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/cmek-config/update)

---
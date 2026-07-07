# gcloud dataplex encryption-config

manage Dataplex encryption configs

### `gcloud dataplex encryption-config create`

Create a Dataplex encryption config resource

An EncryptionConfig is created only for CMEK opted in organizations.

**Synopsis:**
```
gcloud dataplex encryption-config create
    (ENCRYPTION_CONFIG : --location=LOCATION --organization=ORGANIZATION)
    [--key=KEY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Encryption config resource - Arguments and flags that define the Dataplex
EncryptionConfig you want to create. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  ENCRYPTION_CONFIG
     ID of the encryption config or fully qualified identifier for the
     encryption config.

     To set the encryption_config attribute:
     + provide the argument encryption_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument encryption_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --organization=ORGANIZATION
     The name of encryption config to use.

     To set the organization attribute:
     + provide the argument encryption_config on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The KMS key to use for encryption. |


**Examples:**
```bash
To create an EncryptionConfig default in organization test-org-id at
location us-central1 with key test-key, run:        $ gcloud dataplex encryption-config create default \
        --location=us-central1 --organization=test-org-id \
        --key='test-key'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/encryption-config/create)

---
### `gcloud dataplex encryption-config describe`

Describe an EncryptionConfig

Describe an EncryptionConfig. Displays all the details of an
EncryptionConfig used for CMEK with valid organization and location.

**Synopsis:**
```
gcloud dataplex encryption-config describe
    (ENCRYPTION_CONFIG : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Encryption config resource - encryption_config you want to Describe The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  ENCRYPTION_CONFIG
     ID of the encryption config or fully qualified identifier for the
     encryption config.

     To set the encryption_config attribute:
     + provide the argument encryption_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument encryption_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --organization=ORGANIZATION
     Name of the Cloud organization to use.

     To set the organization attribute:
     + provide the argument encryption_config on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To describe an EncryptionConfig:        $ gcloud dataplex encryption-config describe default \
        --location=us-central1 --organization=test-org
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/encryption-config/describe)

---
### `gcloud dataplex encryption-config update`

Update an Encryption Config

Update an Encryption Config.

**Synopsis:**
```
gcloud dataplex encryption-config update
    (ENCRYPTION_CONFIG : --location=LOCATION --organization=ORGANIZATION)
    [--enable-metastore-encryption] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Encryption config resource - Arguments and flags that define the Dataplex
EncryptionConfig you want to update. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  ENCRYPTION_CONFIG
     ID of the encryption config or fully qualified identifier for the
     encryption config.

     To set the encryption_config attribute:
     + provide the argument encryption_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument encryption_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --organization=ORGANIZATION
     The name of encryption config to use.

     To set the organization attribute:
     + provide the argument encryption_config on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-metastore-encryption` |  |  | Helps user to explicitly enable cmek encryption for dataplex metadata storage. |


**Examples:**
```bash
To update EncryptionConfig in organization 123 and location us-central1,
run:

    $ gcloud dataplex encryption-config update \
        organizations/123/locations/us-central1/encryptionConfigs/\
    default --enable-metastore-encryption
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/encryption-config/update)

---
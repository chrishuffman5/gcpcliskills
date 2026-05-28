# gcloud netapp kms-configs

create and manage Cloud NetApp Volumes KMS Configs

### `gcloud netapp kms-configs create`

Create a Cloud NetApp Volumes KMS Config

Creates a KMS (Key Management System) Config to encrypt Cloud NetApp
Volumes, Storage Pools etc. using Customer Managed Encryption Keys (CMEK)

**Synopsis:**
```
gcloud netapp kms-configs create (KMS_CONFIG : --location=LOCATION)
    (--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Kms config resource - The KMS Config to create The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument kms_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KMS_CONFIG
     ID of the kms_config or fully qualified identifier for the
     kms_config.

     To set the kms_config attribute:
     + provide the argument kms_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the kms_config.

     To set the location attribute:
     + provide the argument kms_config on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--kms-key` | KMS_KEY |  | _[This must be specified.]_ ID of the kms_key or fully qualified identifier for the kms_key. To set the kms-key attribute: + provide the argument --kms-key on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--kms-keyring` | KMS_KEYRING |  | _[This must be specified.]_ The KMS keyring of the kms_key To set the kms-keyring attribute: + provide the argument --kms-key on the command line with a fully specified name; + provide the argument --kms-keyring on the command line. |
| `--kms-location` | KMS_LOCATION |  | _[This must be specified.]_ The Cloud location for the kms_key. To set the kms-location attribute: + provide the argument --kms-key on the command line with a fully specified name; + provide the argument --kms-location on the command line; + provide the argument --location on the command line; + set the property netapp/location. |
| `--kms-project` | KMS_PROJECT |  | _[This must be specified.]_ The Cloud project for the kms_key. To set the kms-project attribute: + provide the argument --kms-key on the command line with a fully specified name; + provide the argument --kms-project on the command line; + set the property core/project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp KMS Config |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a KMS Config instance named KMS_CONFIG using
specified project, location, Key Ring and Crypto Key

    $ gcloud netapp kms-configs create KMS_CONFIG \
      --location=us-central1 --kms-location=northamerica-northeast1 \
      --kms-project=kms-project1 --kms-keyring=kms-keyring21 \
      --kms-key=crypto-key1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/create)

---
### `gcloud netapp kms-configs delete`

Delete a Cloud NetApp Volumes KMS Config

Delete a KMS (Key Management System) Config

**Synopsis:**
```
gcloud netapp kms-configs delete (KMS_CONFIG : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Kms config resource - The KMS Config to delete The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument kms_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KMS_CONFIG
     ID of the kms_config or fully qualified identifier for the
     kms_config.

     To set the kms_config attribute:
     + provide the argument kms_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the kms_config.

     To set the location attribute:
     + provide the argument kms_config on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a KMS Config instance named KMS_CONFIG in the
default netapp/location.

    $ gcloud netapp kms-configs delete KMS_CONFIG

To delete a KMS Config named KMS_CONFIG asynchronously, run the following
command:

    $ gcloud netapp kms-configs delete KMS_CONFIG --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/delete)

---
### `gcloud netapp kms-configs describe`

Show metadata for a Cloud NetApp Volumes KMS Config

Describe a KMS (Key Management System) Config.

**Synopsis:**
```
gcloud netapp kms-configs describe (KMS_CONFIG : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Kms config resource - The KMS Config to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument kms_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KMS_CONFIG
     ID of the kms_config or fully qualified identifier for the
     kms_config.

     To set the kms_config attribute:
     + provide the argument kms_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the kms_config.

     To set the location attribute:
     + provide the argument kms_config on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command gets metadata using describe for a KMS Config
instance named KMS_CONFIG in the default netapp/location.

    $ gcloud netapp kms-configs describe KMS_CONFIG

To get metadata on a KMS Config named KMS_CONFIG in a specified location,
run:

    $ gcloud netapp kms-configs describe KMS_CONFIG \
      --location=us-central1s
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/describe)

---
### `gcloud netapp kms-configs encrypt`

Encrypt all existing volumes and storage pools in the same region with the desired Cloud NetApp Volumes KMS Config

Encrypt the existing volumes with the desired KMS (Key Management System)
Config using Customer Managed Encryption Keys (CMEK).

**Synopsis:**
```
gcloud netapp kms-configs encrypt (KMS_CONFIG : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Kms config resource - The KMS Config used to encrypt The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument kms_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KMS_CONFIG
     ID of the kms_config or fully qualified identifier for the
     kms_config.

     To set the kms_config attribute:
     + provide the argument kms_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the kms_config.

     To set the location attribute:
     + provide the argument kms_config on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command encrypts the existing volumes with the desired KMS
Config instance named KMS_CONFIG using specified project and location.

    $ gcloud netapp kms-configs encrypt KMS_CONFIG --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/encrypt)

---
### `gcloud netapp kms-configs list`

List Cloud NetApp Volumes KMS Configs

Lists KMS (Key Management System) Configs to encrypt Cloud NetApp Volumes,
Storage Pools etc. using Customer Managed Encryption Keys (CMEK).

**Synopsis:**
```
gcloud netapp kms-configs list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists all KMS Config instance in the default
netapp/location

    $ gcloud netapp kms-configs list

To list all KMS Configs in a specified location, run:

    $ gcloud netapp kms-configs list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/list)

---
### `gcloud netapp kms-configs update`

Update a Cloud NetApp Volumes KMS Config

Updates a KMS (Key Management System) Config.

**Synopsis:**
```
gcloud netapp kms-configs update (KMS_CONFIG : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Kms config resource - The KMS Config to update The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument kms_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KMS_CONFIG
     ID of the kms_config or fully qualified identifier for the
     kms_config.

     To set the kms_config attribute:
     + provide the argument kms_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the kms_config.

     To set the location attribute:
     + provide the argument kms_config on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp KMS Config |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a KMS Config instance named KMS_CONFIG with
all possible arguments:

    $ gcloud netapp kms-configs update KMS_CONFIG \
      --location=us-central1 --kms-location=europe-southwest1 \
      --kms-project=new-kms-project --kms-keyring=kms-keyring2 \
      --kms-key=crypto-key2

To update a KMS Config named KMS_CONFIG asynchronously, run the following
command:

    $ gcloud netapp kms-configs update KMS_CONFIG --async \
      --location=us-central1 --kms-location=europe-southwest1 \
      --kms-project=new-kms-project --kms-keyring=kms-keyring2 \
      --kms-key=crypto-key2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/update)

---
### `gcloud netapp kms-configs verify`

Verify that the Cloud NetApp Volumes KMS Config is reachable

Verifies that the Cloud NetApp Volumes KMS (Key Management System) Config
is reachable.

**Synopsis:**
```
gcloud netapp kms-configs verify (KMS_CONFIG : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Kms config resource - The KMS Config used to verify The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument kms_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KMS_CONFIG
     ID of the kms_config or fully qualified identifier for the
     kms_config.

     To set the kms_config attribute:
     + provide the argument kms_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the kms_config.

     To set the location attribute:
     + provide the argument kms_config on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command verifies that the KMS Config instance named
KMS_CONFIG is reachable using specified location.

    $ gcloud netapp kms-configs verify KMS_CONFIG --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/kms-configs/verify)

---
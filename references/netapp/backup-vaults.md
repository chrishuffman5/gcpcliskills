# gcloud netapp backup-vaults

create and manage Cloud NetApp Backup Vaults

### `gcloud netapp backup-vaults create`

Create a Cloud NetApp Backup Vault

Create a Cloud NetApp Backup Vault.

**Synopsis:**
```
gcloud netapp backup-vaults create (BACKUP_VAULT : --location=LOCATION)
    [--async]
    [--backup-retention-policy=[backup-minimum-enforced-retention-days=BACKUP-MINIMUM-ENFORCED-RETENTION-DAYS],
      [daily-backup-immutable=DAILY-BACKUP-IMMUTABLE],
      [manual-backup-immutable=MANUAL-BACKUP-IMMUTABLE],
      [monthly-backup-immutable=MONTHLY-BACKUP-IMMUTABLE],
      [weekly-backup-immutable=WEEKLY-BACKUP-IMMUTABLE]]
    [--description=DESCRIPTION] [--kms-config=KMS_CONFIG]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup vault resource - The Backup Vault to create The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the backup_vault or fully qualified identifier for the
     backup_vault.

     To set the backup_vault attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-retention-policy` | [backup-minimum-enforced-retention-days=BACKUP-MINIMUM-ENFORCED-RETENTION-DAYS],[daily-backup-immutable=DAILY-BACKUP-IMMUTABLE],[manual-backup-immutable=MANUAL-BACKUP-IMMUTABLE],[monthly-backup-immutable=MONTHLY-BACKUP-IMMUTABLE],[weekly-backup-immutable=WEEKLY-BACKUP-IMMUTABLE] |  | Backup Retention Policy of the Backup Vault. Backup Retention Policy allows you to configure the retention policy for backups created within this vault. It consists of several fields that govern how long backups are kept and what type of backups are immutable. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Backup Vault |
| `--labels` | [KEY=VALUE,...] |  | _[+ provide the argument --kms-config on the command line.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a Backup Vault named BACKUP_VAULT
asynchronously using the specified arguments:

    $ gcloud netapp backup-vaults create BACKUP_VAULT \
      --location=LOCATION --async --description="test" The following \
      command creates a Backup Vault named CMEK_BACKUP_VAULT with a \
      KMS config:

    $ gcloud netapp backup-vaults create CMEK_BACKUP_VAULT \
      --location=LOCATION \
      --kms-config=projects/PROJECT/locations/LOCATION/kmsConfigs/\
    KMS_CONFIG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/create)

---
### `gcloud netapp backup-vaults delete`

Delete a Cloud NetApp Volumes Backup Vault

Delete a Backup Vault.

**Synopsis:**
```
gcloud netapp backup-vaults delete (BACKUP_VAULT : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup vault resource - The Backup Vault to delete The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the backup_vault or fully qualified identifier for the
     backup_vault.

     To set the backup_vault attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a Backup Vault instance named BACKUP_VAULT in
the default netapp/location:

    $ gcloud netapp backup-vaults delete BACKUP_VAULT

To delete a Backup Vault named BACKUP_VAULT asynchronously, run the
following command:

    $ gcloud netapp backup-vaults delete BACKUP_VAULT --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/delete)

---
### `gcloud netapp backup-vaults describe`

Show metadata for a Cloud NetApp Volumes Backup Vault

Describe a Backup Vault.

**Synopsis:**
```
gcloud netapp backup-vaults describe (BACKUP_VAULT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup vault resource - The Backup Vault to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the backup_vault or fully qualified identifier for the
     backup_vault.

     To set the backup_vault attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command gets metadata using describe for a Backup Vault
instance named BACKUP_VAULT in the default netapp/location:

    $ gcloud netapp backup-vaults describe BACKUP_VAULT

To get metadata on a Backup Vault named BACKUP_VAULT in a specified
location, run:

    $ gcloud netapp backup-vaults describe BACKUP_VAULT \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/describe)

---
### `gcloud netapp backup-vaults list`

List Cloud NetApp Volumes Backup Vaults

Lists Cloud NetApp Backup Vaults to store Cloud NetApp Volumes Backups.

**Synopsis:**
```
gcloud netapp backup-vaults list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists all Backup Vaults in the default
netapp/location

    $ gcloud netapp backup-vaults list

To list all Backup Vaults in a specified location, run:

    $ gcloud netapp backup-vaults list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/list)

---
### `gcloud netapp backup-vaults update`

Update a Cloud NetApp Volumes Backup Vault

Updates a Backup Vault

**Synopsis:**
```
gcloud netapp backup-vaults update (BACKUP_VAULT : --location=LOCATION)
    [--async]
    [--backup-retention-policy=[backup-minimum-enforced-retention-days=BACKUP-MINIMUM-ENFORCED-RETENTION-DAYS],
      [daily-backup-immutable=DAILY-BACKUP-IMMUTABLE],
      [manual-backup-immutable=MANUAL-BACKUP-IMMUTABLE],
      [monthly-backup-immutable=MONTHLY-BACKUP-IMMUTABLE],
      [weekly-backup-immutable=WEEKLY-BACKUP-IMMUTABLE]]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup vault resource - The Backup Vault to update The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the backup_vault or fully qualified identifier for the
     backup_vault.

     To set the backup_vault attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-retention-policy` | [backup-minimum-enforced-retention-days=BACKUP-MINIMUM-ENFORCED-RETENTION-DAYS],[daily-backup-immutable=DAILY-BACKUP-IMMUTABLE],[manual-backup-immutable=MANUAL-BACKUP-IMMUTABLE],[monthly-backup-immutable=MONTHLY-BACKUP-IMMUTABLE],[weekly-backup-immutable=WEEKLY-BACKUP-IMMUTABLE] |  | Backup Retention Policy of the Backup Vault. Backup Retention Policy allows you to configure the retention policy for backups created within this vault. It consists of several fields that govern how long backups are kept and what type of backups are immutable. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Backup Vault |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Backup Vault instance named BACKUP_VAULT

    $ gcloud netapp backup-vaults update BACKUP_VAULT \
      --location=us-central1 --description="new description" \
      --update-labels=newkey=newval

To update a Backup Vault named BACKUP_VAULT asynchronously, run the
following command:

    $ gcloud netapp backup-vaults update BACKUP_VAULT --async \
      --location=us-central1 --description="new description" \
      --update-labels=newkey=newval
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/update)

---

## `gcloud netapp backup-vaults backups` — create and manage Cloud NetApp Backups
### `gcloud netapp backup-vaults backups create`

Create a Cloud NetApp Backup

Create a Cloud NetApp Backup.

**Synopsis:**
```
gcloud netapp backup-vaults backups create (BACKUP : --location=LOCATION)
    [--async] [--backup-vault=BACKUP_VAULT] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [--source-snapshot=SOURCE_SNAPSHOT]
    [--source-volume=SOURCE_VOLUME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Backup to create The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the backup_vault attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --backup-vault on the command line.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | _[+ provide the argument --backup-vault on the command line.]_ A description of the Cloud NetApp Backup Vault |
| `--labels` | [KEY=VALUE,...] |  | _[+ provide the argument --backup-vault on the command line.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a Backup named BACKUP attached to a Backup
Vault named BACKUP_VAULT, and a source volume named SOURCE_VOL
asynchronously using the specified arguments:

    $ gcloud netapp backup-vaults backups create BACKUP \
      --location=LOCATION --async --backup-vault=BACKUP_VAULT \
      --source-volume=SOURCE_VOL
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/backups/create)

---
### `gcloud netapp backup-vaults backups delete`

Delete a Cloud NetApp Backup

Delete a Cloud NetApp Backup.

**Synopsis:**
```
gcloud netapp backup-vaults backups delete (BACKUP : --location=LOCATION)
    [--async] [--backup-vault=BACKUP_VAULT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Backup to delete. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the backup_vault attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --backup-vault on the command line.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
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
The following command deletes a Backup named BACKUP inside a backup vault
named BACKUP_VAULT using the required arguments:

    $ gcloud netapp backup-vaults backups delete BACKUP \
      --location=us-central1 --backup-vault=BACKUP_VAULT

To delete a Backup named BACKUP asynchronously, run the following command:

    $ gcloud netapp backup-vaults backups delete BACKUP \
      --location=us-central1 --backup-vault=BACKUP_VAULT --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/backups/delete)

---
### `gcloud netapp backup-vaults backups describe`

Describe a Cloud NetApp Backup

Describe a Cloud NetApp Backup.

**Synopsis:**
```
gcloud netapp backup-vaults backups describe (BACKUP : --location=LOCATION)
    [--backup-vault=BACKUP_VAULT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Backup to describe. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the backup_vault attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --backup-vault on the command line.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-vault` | BACKUP_VAULT |  | _[* set the property netapp/location.]_ ID of the backup_vault or fully qualified identifier for the backup_vault. To set the backup_vault attribute: + provide the argument --backup-vault on the command line. |


**Examples:**
```bash
The following command describes a Backup named BACKUP in the given location
and backup vault:

    $ gcloud netapp backup-vaults backups describe NAME \
      --location=us-central1 --backup-vault=BACKUP_VAULT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/backups/describe)

---
### `gcloud netapp backup-vaults backups list`

List Cloud NetApp Backups

Lists Cloud NetApp Backups.

**Synopsis:**
```
gcloud netapp backup-vaults backups list [--backup-vault=BACKUP_VAULT]
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-vault` | BACKUP_VAULT |  | _[* set the property netapp/location.]_ ID of the backup_vault or fully qualified identifier for the backup_vault. To set the backup_vault attribute: + provide the argument --backup-vault on the command line. |
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists all Backups in the given location and Backup
Vault named BACKUP_VAULT:

    $ gcloud netapp backup-vaults backups list --location=us-central1 \
      --backup-vault=BACKUP_VAULT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/backups/list)

---
### `gcloud netapp backup-vaults backups update`

Update a Cloud NetApp Backup

Update a Cloud NetApp Backup and its specified parameters.

**Synopsis:**
```
gcloud netapp backup-vaults backups update (BACKUP : --location=LOCATION)
    [--async] [--backup-vault=BACKUP_VAULT] [--description=DESCRIPTION]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Backup to update The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the backup_vault attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --backup-vault on the command line.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | _[+ provide the argument --backup-vault on the command line.]_ A description of the Cloud NetApp Backup |
| `--update-labels` | [KEY=VALUE,...] |  | _[+ provide the argument --backup-vault on the command line.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Backup named BACKUP and its specified
parameters:

    $ gcloud netapp backup-vaults backups update NAME \
      --location=us-central1 --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-vaults/backups/update)

---
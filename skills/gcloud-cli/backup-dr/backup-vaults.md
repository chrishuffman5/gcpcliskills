# gcloud backup-dr backup-vaults

manage Backup and DR backup vaults

### `gcloud backup-dr backup-vaults create`

Create a Backup and DR backup vault

Create a Backup and DR backup vault.

**Synopsis:**
```
gcloud backup-dr backup-vaults create (BACKUP_VAULT : --location=LOCATION)
    --backup-min-enforced-retention=BACKUP_MIN_ENFORCED_RETENTION
    [--access-restriction=ACCESS_RESTRICTION; default="within-org"]
    [--no-async]
    [--backup-retention-inheritance=BACKUP_RETENTION_INHERITANCE]
    [--description=DESCRIPTION] [--effective-time=EFFECTIVE_TIME]
    [--kms-key=KMS_KEY] [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Vault resource - Name of the backup vault to create. A vault name
cannot be changed after creation. It must be between 3-63 characters long
and must be unique within the project and location. The arguments in this
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
     ID of the Backup Vault or fully qualified identifier for the Backup
     Vault.

     To set the name attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-min-enforced-retention` | BACKUP_MIN_ENFORCED_RETENTION |  | Backups will be kept for this minimum period before they can be deleted. Once the effective time is reached, the enforced retention period cannot be decreased or removed. The value must be specified in relative time format (e.g. p1d, p1m, p1m1d). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-restriction` | one of: within-project, within-org, unrestricted, within-org-but-unrestricted-for-ba | within-org | Authorize certain sources and destinations for data being sent into, or restored from, the backup vault being created. This choice determines the type of resources that can be stored. Restricting access to within your project or organization limits the resources to those managed through the Google Cloud console (e.g., Compute Engine VMs). Unrestricted access is required for resources managed through the management console (e.g., VMware Engine VMs, databases, and file systems). ACCESS_RESTRICTION must be one of: within-project, within-org, unrestricted, within-org-but-unrestricted-for-ba. |
| `--no-async` |  |  | Wait for the operation in progress to complete. |
| `--backup-retention-inheritance` | one of: inherit-vault-retention, match-backup-expire-time |  | The inheritance mode for enforced retention end time of the backup within this backup vault. Once set, the inheritance mode cannot be changed. Default is inherit-vault-retention. If set to inherit-vault-retention, the backup retention period will be inherited from the backup vault. If set to match-backup-expire-time, the backup retention period will be the same as the backup expiration time. BACKUP_RETENTION_INHERITANCE must be one of: inherit-vault-retention, match-backup-expire-time. |
| `--description` | DESCRIPTION |  | Optional description for the backup vault (2048 characters or less). |
| `--effective-time` | EFFECTIVE_TIME |  | The time at which the enforced retention period becomes locked. This flag is mutually exclusive with --unlock-backup-min-enforced-retention. |
| `--kms-key` | KMS_KEY |  | The Cloud KMS key resource name to be used for encryption. Format: projects/{project}/locations/{location}/keyRings/{ring}/cryptoKeys/{key} |
| `--labels` | [KEY=VALUE,...] |  | Optional resource labels to represent metadata provided by the user. |


**Examples:**
```bash
To create a new backup vault BACKUP_VAULT in location MY_LOCATION with
minimum enforced-retention for backups of 1 month and 1 day, run:

    $ gcloud backup-dr backup-vaults create BACKUP_VAULT \
        --location=MY_LOCATION --backup-min-enforced-retention="p1m1d"

To create a new backup vault BACKUP_VAULT in location MY_LOCATION with
minimum enforced-retention for backups of 1 day and description
DESCRIPTION, run:

    $ gcloud backup-dr backup-vaults create BACKUP_VAULT \
        --location=MY_LOCATION --backup-min-enforced-retention="1d" \
        --description=DESCRIPTION

To create a new backup vault BACKUP_VAULT in location MY_LOCATION with
minimum enforced-retention for backups of 1 day and label key1 with value
value1, run:

    $ gcloud backup-dr backup-vaults create BACKUP_VAULT \
        --location=MY_LOCATION --backup-min-enforced-retention="1d" \
        --labels=key1=value1

To create a new backup vault BACKUP_VAULT in location MY_LOCATION with
minimum enforced-retention for backups of 1 day and effective-time
"2024-03-22", run:

    $ gcloud backup-dr backup-vaults create BACKUP_VAULT \
        --location=MY_LOCATION --backup-min-enforced-retention="1d" \
        --effective-time="2024-03-22"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-vaults/create)

---
### `gcloud backup-dr backup-vaults delete`

Delete the specified Backup Vault

Delete the specified Backup Vault.

**Synopsis:**
```
gcloud backup-dr backup-vaults delete (BACKUP_VAULT : --location=LOCATION)
    [--allow-missing] [--no-async] [--ignore-backup-plan-references]
    [--ignore-inactive-datasources] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Vault resource - Name of the backup vault to delete. Before you
delete, take a look at the prerequisites here
(https://cloud.google.com/backup-disaster-recovery/docs/configuration/decommission).
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the Backup Vault or fully qualified identifier for the Backup
     Vault.

     To set the name attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | Allow idempotent deletion of backup vault. The request will still succeed in case the backup vault does not exist. |
| `--no-async` |  |  | Wait for the operation in progress to complete. |
| `--ignore-backup-plan-references` |  |  | If set, the following restrictions against deletion of the backup vault instance can be overridden: * deletion of a backup vault instance being actively referenced by a backup plan. |
| `--ignore-inactive-datasources` |  |  | If set, the following restrictions against deletion of the backup vault instance can be overridden: * deletion of a backup vault instance containing no backups,but still contains empty datasources. |


**Examples:**
```bash
To delete a backup vault BACKUP_VAULT in location MY_LOCATION, run:

    $ gcloud backup-dr backup-vaults delete BACKUP_VAULT \
        --location=MY_LOCATION

To override restrictions against the deletion of a backup vault
BACKUP_VAULT containing inactive datasources in location MY_LOCATION, run:

    $ gcloud backup-dr backup-vaults delete BACKUP_VAULT \
        --location=MY_LOCATION --ignore-inactive-datasources

To override restrictions against the deletion of a backup vault
BACKUP_VAULT containing backup plan references in location MY_LOCATION,
run:

    $ gcloud backup-dr backup-vaults delete BACKUP_VAULT \
        --location=MY_LOCATION --ignore-backup-plan-references
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-vaults/delete)

---
### `gcloud backup-dr backup-vaults describe`

Show the metadata for a Backup and DR backup vault

Show the metadata for a Backup and DR backup vault.

**Synopsis:**
```
gcloud backup-dr backup-vaults describe
    (BACKUP_VAULT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Vault resource - Name of the backup vault to retreive metadata of.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the Backup Vault or fully qualified identifier for the Backup
     Vault.

     To set the name attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details associated with backup vault 'BACKUP_VAULT', run:

    $ gcloud backup-dr backup-vaults describe BACKUP_VAULT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-vaults/describe)

---
### `gcloud backup-dr backup-vaults list`

List Backup and DR backup vaults

List Backup and DR backup vaults.

**Synopsis:**
```
gcloud backup-dr backup-vaults list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Defaults to all locations. |


**Examples:**
```bash
To list backup vaults in all location, run:

    $ gcloud backup-dr backup-vaults list

To list backup vaults in a location ''my-location'', run:

    $ gcloud backup-dr backup-vaults list --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-vaults/list)

---
### `gcloud backup-dr backup-vaults update`

Update a Backup and DR backup vault

Update a Backup and DR backup vault.

**Synopsis:**
```
gcloud backup-dr backup-vaults update (BACKUP_VAULT : --location=LOCATION)
    [--access-restriction=ACCESS_RESTRICTION] [--no-async]
    [--backup-min-enforced-retention=BACKUP_MIN_ENFORCED_RETENTION]
    [--description=DESCRIPTION] [--effective-time=EFFECTIVE_TIME]
    [--force-update] [--force-update-access-restriction]
    [--unlock-backup-min-enforced-retention] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup Vault resource - Name of the existing backup vault to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup_vault on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_VAULT
     ID of the Backup Vault or fully qualified identifier for the Backup
     Vault.

     To set the name attribute:
     + provide the argument backup_vault on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Backup Vault.

     To set the location attribute:
     + provide the argument backup_vault on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-restriction` | one of: within-project, within-org, unrestricted, within-org-but-unrestricted-for-ba |  | Authorize certain sources and destinations for data being sent into, or restored from the current backup vault. Access restrictions can be modified to be more or less restrictive. ::: More restrictive access restriction update will fail by default if there will be non compliant Data Sources. To allow such updates, use the --force-update-access-restriction flag. ::: For Google Cloud Console resources, the following changes are allowed to make access restrictions more restrictive: * `UNRESTRICTED` to `WITHIN_PROJECT` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` / `WITHIN_ORGANIZATION` * `WITHIN_PROJECT` to `WITHIN_ORGANIZATION` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` ::: For Management Server resources, the following changes are allowed to make access restrictions more restrictive: * `UNRESTRICTED` to `WITHIN_PROJECT` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` / `WITHIN_ORGANIZATION` * `WITHIN_PROJECT` to `WITHIN_ORGANIZATION` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` ::: For both Google Cloud Console and Management Server resources, the following changes are allowed to make access restrictions more restrictive: * `UNRESTRICTED` to `WITHIN_PROJECT` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` / `WITHIN_ORGANIZATION` * `WITHIN_PROJECT` to `WITHIN_ORGANIZATION` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` ::: For Google Cloud Console resources, the following changes are allowed to make access restrictions less restrictive: * `WITHIN_ORGANIZATION` to `UNRESTRICTED` / `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` * `WITHIN_PROJECT` to `UNRESTRICTED` * `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` to `UNRESTRICTED` ::: For Management Server resources, the following changes are allowed to make access restrictions less restrictive: * `WITHIN_ORG_BUT_UNRESTRICTED_FOR_BA` to `UNRESTRICTED` ACCESS_RESTRICTION must be one of: within-project, within-org, unrestricted, within-org-but-unrestricted-for-ba. |
| `--no-async` |  |  | Wait for the operation in progress to complete. |
| `--backup-min-enforced-retention` | BACKUP_MIN_ENFORCED_RETENTION |  | Backups will be kept for this minimum period before they can be deleted. Once the effective time is reached, the enforced retention period cannot be decreased or removed. The value must be specified in relative time format (e.g. p1d, p1m, p1m1d). |
| `--description` | DESCRIPTION |  | Optional description for the backup vault (2048 characters or less). |
| `--effective-time` | EFFECTIVE_TIME |  | The time at which the enforced retention period becomes locked. This flag is mutually exclusive with --unlock-backup-min-enforced-retention. |
| `--force-update` |  |  | If set, allow update to extend the minimum enforced retention for backup vault. This overrides the restriction against conflicting retention periods. This conflict may occur when the expiration schedule defined by the associated backup plan is shorter than the minimum retention set by the backup vault. |
| `--force-update-access-restriction` |  |  | If set, the access restriction can be updated even if there are non-compliant data sources. Backups for those data sources will fail afterward. |
| `--unlock-backup-min-enforced-retention` |  |  | Removes the lock on the backup minimum enforced retention period, and resets the effective time. When unlocked, the enforced retention period can be changed at any time. This flag is mutually exclusive with --effective-time. |


**Examples:**
```bash
To update a backup vault BACKUP_VAULT in location MY_LOCATION with one
update field, run:

    $ gcloud backup-dr backup-vaults update BACKUP_VAULT \
        --location=MY_LOCATION --effective-time="2024-03-22"

To update a backup vault BACKUP_VAULT in location MY_LOCATION with multiple
update fields, run:

    $ gcloud backup-dr backup-vaults update BACKUP_VAULT \
        --location=MY_LOCATION \
        --backup-min-enforced-retention="400000s" \
        --description="Updated backup vault"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-vaults/update)

---
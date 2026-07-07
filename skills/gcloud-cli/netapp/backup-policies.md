# gcloud netapp backup-policies

create and manage Cloud NetApp Backup Policies

### `gcloud netapp backup-policies create`

Create a Cloud NetApp Backup Policy

Creates a Backup Policy for Cloud NetApp Volumes.

**Synopsis:**
```
gcloud netapp backup-policies create (BACKUP_POLICY : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--enabled=ENABLED]
    [--labels=[KEY=VALUE,...]]
    [--daily-backup-limit=DAILY_BACKUP_LIMIT
      --monthly-backup-limit=MONTHLY_BACKUP_LIMIT
      --weekly-backup-limit=WEEKLY_BACKUP_LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup policy resource - The Backup Policy to create The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_POLICY
     ID of the backup_policy or fully qualified identifier for the
     backup_policy.

     To set the backup_policy attribute:
     + provide the argument backup_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_policy.

     To set the location attribute:
     + provide the argument backup_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Backup Policy |
| `--enabled` | ENABLED |  | The Boolean value indiciating whether backups are made automatically according to the schedules. If enabled, this will be applied to all volumes that have this backup policy attached and enforced on the volume level. If not specified, the default is true. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command creates a Backup Policy named BACKUP_POLICY with all
possible arguments:

    $ gcloud netapp backup-policies create BACKUP_POLICY \
      --location=us-central1 --enabled=true --daily-backup-limit=3 \
      --weekly-backup-limit=5 --monthly-backup-limit=2 \
      --description="first backup policy" --labels=key1=val1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-policies/create)

---
### `gcloud netapp backup-policies delete`

Delete a Cloud NetApp Volumes Backup Policy

Delete a Backup Policy

**Synopsis:**
```
gcloud netapp backup-policies delete (BACKUP_POLICY : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup policy resource - The Backup Policy to delete The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_POLICY
     ID of the backup_policy or fully qualified identifier for the
     backup_policy.

     To set the backup_policy attribute:
     + provide the argument backup_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_policy.

     To set the location attribute:
     + provide the argument backup_policy on the command line with a
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
The following command deletes a Backup Policy instance named BACKUP_POLICY
in the default netapp/location

    $ gcloud netapp backup-policies delete BACKUP_POLICY

To delete a Backup Policy named BACKUP_POLICY asynchronously, run the
following command:

    $ gcloud netapp backup-policies delete BACKUP_POLICY --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-policies/delete)

---
### `gcloud netapp backup-policies describe`

Show metadata for a Cloud NetApp Volumes Backup Policy

Describe a Backup Policy

**Synopsis:**
```
gcloud netapp backup-policies describe
    (BACKUP_POLICY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup policy resource - The Backup Policy to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_POLICY
     ID of the backup_policy or fully qualified identifier for the
     backup_policy.

     To set the backup_policy attribute:
     + provide the argument backup_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_policy.

     To set the location attribute:
     + provide the argument backup_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command gets metadata using describe for a Backup Policy
named BACKUP_POLICY in the default netapp/location:

    $ gcloud netapp backup-policies describe BACKUP_POLICY

To get metadata on a Backup Policy named BACKUP_POLICY in a specified
location, run:

    $ gcloud netapp backup-policies describe BACKUP_POLICY \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-policies/describe)

---
### `gcloud netapp backup-policies list`

List Cloud NetApp Volumes Backup Policies

Lists Backup Policies for Cloud NetApp Volumes

**Synopsis:**
```
gcloud netapp backup-policies list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists all Backup Policies in the default
netapp/location

    $ gcloud netapp backup-policies list

To list all Backup Policies in a specified location, run:

    $ gcloud netapp backup-policies list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-policies/list)

---
### `gcloud netapp backup-policies update`

Update a Cloud NetApp Volumes Backup Policies

Updates a Backup Policy

**Synopsis:**
```
gcloud netapp backup-policies update (BACKUP_POLICY : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--enabled=ENABLED]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--daily-backup-limit=DAILY_BACKUP_LIMIT
      --monthly-backup-limit=MONTHLY_BACKUP_LIMIT
      --weekly-backup-limit=WEEKLY_BACKUP_LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup policy resource - The Backup Policy to update The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_POLICY
     ID of the backup_policy or fully qualified identifier for the
     backup_policy.

     To set the backup_policy attribute:
     + provide the argument backup_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the backup_policy.

     To set the location attribute:
     + provide the argument backup_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the Cloud NetApp Backup Policy |
| `--enabled` | ENABLED |  | The Boolean value indiciating whether backups are made automatically according to the schedules. If enabled, this will be applied to all volumes that have this backup policy attached and enforced on the volume level. If not specified, the default is true. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates a Backup Policy named BACKUP_POLICY with all
possible arguments

    $ gcloud netapp backup-policies update BACKUP_POLICY \
      --location=us-central1 --enabled=True --daily-backup-limit=5 \
      --weekly-backup-limit=3 --monthly-backup-limit=2

To update a Backup Policy named BACKUP_POLICY asynchronously, run the
following command:

    $ gcloud netapp backup-policies update BACKUP_POLICY --async \
      --location=us-central1 --enabled=True --daily-backup-limit=5 \
      --weekly-backup-limit=3 --monthly-backup-limit=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/backup-policies/update)

---
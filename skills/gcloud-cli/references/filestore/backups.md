# gcloud filestore backups

create and manage Filestore backups

### `gcloud filestore backups create`

Create a Filestore backup

Create a Filestore backup of an instance file share.

This command can fail for the following reasons:
  o A backup with the same name already exists.
  o The active account does not have permission to create backups.

**Synopsis:**
```
gcloud filestore backups create BACKUP --file-share=FILE_SHARE
    --instance=INSTANCE --region=REGION
    (--instance-location=INSTANCE_LOCATION | --instance-zone=INSTANCE_ZONE)
    [--async] [--description=DESCRIPTION] [--kms-key=KMS_KEY]
    [--labels=[KEY=VALUE,...]] [--tags=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   Arguments and flags that specify the Filestore backup you want to
   create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-share` | FILE_SHARE |  | File share name on the Filestore instance to backup. |
| `--instance` | INSTANCE |  | Share name of the Filestore instance you want to backup. |
| `--region` | REGION |  | Region (e.g. us-central1) for the backup. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description for the backup. Limit: 2048 characters. |
| `--kms-key` | KMS_KEY |  | CMEK for backup in the form of projects/{project}/locations/{location}/keyRings/{key-ring}/cryptoKeys/{crypto-key} |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--tags` | [KEY=VALUE,...] |  | List of tag KEY=VALUE pairs to add. |


**Examples:**
```bash
To create a backup with the name 'my-backup' and description 'My backup
description' in a particular region like 'us-central1' from an instance
called 'my-instance' in 'us-central1-c' and the source file share called
'my-fs', run:

    $ gcloud filestore backups create my-backup --instance=my-instance \
        --file-share=my-fs --instance-zone=us-central1-c \
        --region=us-central1 --description="My backup description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/backups/create)

---
### `gcloud filestore backups delete`

Delete a Filestore backup

Delete a Filestore backup.

This command can fail for the following reasons:
  o The backup specified does not exist.
  o The active account does not have permission to delete the given
    backup.

**Synopsis:**
```
gcloud filestore backups delete BACKUP --region=REGION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   Arguments and flags that specify the Filestore backup you want to
   delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Compute region (e.g. us-central1) for the backup. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a backup with the name 'my-backup' in the
region us-central1:

    $ gcloud filestore backups delete my-backup --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/backups/delete)

---
### `gcloud filestore backups describe`

Describe a Filestore backup

Displays all data associated with a Filestore backup given a valid backup
name.

This command can fail for the following reasons:
  o The backup specified does not exist.
  o The active account does not have permission to access the given
    backup.

**Synopsis:**
```
gcloud filestore backups describe BACKUP --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   Arguments and flags that specify the Filestore backup you want to
   create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region (e.g. us-central1) for the backup. |


**Examples:**
```bash
To display all data associated with a backup of the name 'my-backup' in the
region us-central1:

    $ gcloud filestore backups describe my-backup --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/backups/describe)

---
### `gcloud filestore backups list`

List Filestore backups

List all Filestore backups in a project for either a specified region or
for all region.

To specify the maximum number of backups to list, use the --limit flag.

**Synopsis:**
```
gcloud filestore backups list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The region of the Backups to display. If unspecified, all backups will be listed. |


**Examples:**
```bash
To list up to five backups, run:

    $ gcloud filestore backups list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/backups/list)

---
### `gcloud filestore backups update`

Update a Filestore backup

Update the metadata of a Filestore backup.

This command can fail for the following reasons:
  o The backup specified does not exist.
  o The active account does not have permission to update the given
    backup.

**Synopsis:**
```
gcloud filestore backups update BACKUP --region=REGION [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKUP
   Arguments and flags that specify the Filestore backup you want to
   update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Compute region (e.g. us-central1) for the backup. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the backup. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates the Filestore Backup named 'my-backup' in
region us-central1 to change the description to 'A new description.'

    $ gcloud filestore backups update my-backup --region=us-central1 \
        --description="A new description."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/backups/update)

---
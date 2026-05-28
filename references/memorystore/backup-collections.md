# gcloud memorystore backup-collections

manage Backup Collection resources

### `gcloud memorystore backup-collections describe`

Describe backupCollections

Describe a backupCollection

**Synopsis:**
```
gcloud memorystore backup-collections describe
    (BACKUP_COLLECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BackupCollection resource - Instance backupCollection resource name using
the form:
projects/{project_id}/locations/{location_id}/backupCollections/{backup_collection_id}
where location_id refers to a Google Cloud region. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup_collection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP_COLLECTION
     ID of the backupCollection or fully qualified identifier for the
     backupCollection.

     To set the backup_collection attribute:
     + provide the argument backup_collection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the backupCollection resource.

     To set the location attribute:
     + provide the argument backup_collection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the backupCollection, run:

    $ gcloud memorystore backup-collections describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/backup-collections/describe)

---
### `gcloud memorystore backup-collections list`

List backupCollections

**Synopsis:**
```
gcloud memorystore backup-collections list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all backupCollections, run:

    $ gcloud memorystore backup-collections list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/backup-collections/list)

---

## `gcloud memorystore backup-collections backups` — manage Backup resources
### `gcloud memorystore backup-collections backups delete`

Delete backups

Delete a backup

**Synopsis:**
```
gcloud memorystore backup-collections backups delete
    (BACKUP : --backup-collection=BACKUP_COLLECTION --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Instance backup resource name using the form:
projects/{project_id}/locations/{location_id}/backupCollections/{backup_collection_id}/backups/{backup_id}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-collection=BACKUP_COLLECTION
     The backupCollection id of the backup resource.

     To set the backup-collection attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-collection on the command line.

  --location=LOCATION
     The location id of the backup resource.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | Idempotent request UUID. |


**Examples:**
```bash
To delete the backup, run:

    $ gcloud memorystore backup-collections backups delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/backup-collections/backups/delete)

---
### `gcloud memorystore backup-collections backups describe`

Describe backups

Describe a backup

**Synopsis:**
```
gcloud memorystore backup-collections backups describe
    (BACKUP : --backup-collection=BACKUP_COLLECTION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Instance backup resource name using the form:
projects/{project_id}/locations/{location_id}/backupCollections/{backup_collection_id}/backups/{backup_id}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-collection=BACKUP_COLLECTION
     The backupCollection id of the backup resource.

     To set the backup-collection attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-collection on the command line.

  --location=LOCATION
     The location id of the backup resource.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the backup, run:

    $ gcloud memorystore backup-collections backups describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/backup-collections/backups/describe)

---
### `gcloud memorystore backup-collections backups export`

Export backups

**Synopsis:**
```
gcloud memorystore backup-collections backups export
    (BACKUP : --backup-collection=BACKUP_COLLECTION --location=LOCATION)
    [--async] [--gcs-bucket=GCS_BUCKET] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Instance backup resource name using the form:
projects/{project_id}/locations/{location_id}/backupCollections/{backup_collection_id}/backups/{backup_id}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --backup-collection=BACKUP_COLLECTION
     The backupCollection id of the backup resource.

     To set the backup-collection attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --backup-collection on the command line.

  --location=LOCATION
     The location id of the backup resource.

     To set the location attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--gcs-bucket` | GCS_BUCKET |  | Google Cloud Storage bucket, like "my-bucket". |


**Examples:**
```bash
To export all backups, run:

    $ gcloud memorystore backup-collections backups export
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/backup-collections/backups/export)

---
### `gcloud memorystore backup-collections backups list`

List backups

**Synopsis:**
```
gcloud memorystore backup-collections backups list
    (--backup-collection=BACKUP_COLLECTION : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup-collection` | BACKUP_COLLECTION |  | _[This must be specified.]_ ID of the backupCollection or fully qualified identifier for the backupCollection. To set the backup-collection attribute: + provide the argument --backup-collection on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the backupCollection resource. To set the location attribute: + provide the argument --backup-collection on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all backups, run:

    $ gcloud memorystore backup-collections backups list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/backup-collections/backups/list)

---
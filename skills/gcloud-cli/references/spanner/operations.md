# gcloud spanner operations

manage Cloud Spanner operations

### `gcloud spanner operations cancel`

Cancel a Cloud Spanner operation

Cancel a Cloud Spanner operation.

**Synopsis:**
```
gcloud spanner operations cancel OPERATION-ID
    (--instance=INSTANCE | --instance-config=INSTANCE_CONFIG)
    [--backup=BACKUP] [--database=DATABASE]
    [--instance-partition=INSTANCE_PARTITION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION-ID
   ID of the operation
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[Exactly one of these must be specified:]_ The ID of the instance the operation is executing on. |
| `--instance-config` | INSTANCE_CONFIG |  | _[Exactly one of these must be specified:]_ The ID of the instance configuration the operation is executing on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | For a backup operation, the name of the backup the operation is executing on. |
| `--database` | DATABASE |  | For a database operation, the name of the database the operation is executing on. |
| `--instance-partition` | INSTANCE_PARTITION |  | For an instance partition operation, the name of the instance partition the operation is executing on. |


**Examples:**
```bash
To cancel an instance operation with ID auto_12345, run:

    $ gcloud spanner operations cancel _auto_12345 \
        --instance=my-instance-id

To cancel a database operation with ID auto_12345, run:

    $ gcloud spanner operations cancel _auto_12345 \
        --instance=my-instance-id --database=my-database-id

To cancel a backup operation with ID auto_12345, run:

    $ gcloud spanner operations cancel _auto_12345 \
        --instance=my-instance-id --backup=my-backup-id

To cancel an instance partition operation with ID auto_12345, run:

    $ gcloud spanner operations cancel auto_12345 \
        --instance=my-instance-id --instance-partition=my-partition-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/operations/cancel)

---
### `gcloud spanner operations describe`

Describe a Cloud Spanner operation

Describe a Cloud Spanner operation.

**Synopsis:**
```
gcloud spanner operations describe OPERATION-ID
    (--instance=INSTANCE | --instance-config=INSTANCE_CONFIG)
    [--backup=BACKUP] [--database=DATABASE]
    [--instance-partition=INSTANCE_PARTITION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION-ID
   ID of the operation
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[Exactly one of these must be specified:]_ The ID of the instance the operation is executing on. |
| `--instance-config` | INSTANCE_CONFIG |  | _[Exactly one of these must be specified:]_ The ID of the instance configuration the operation is executing on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | For a backup operation, the name of the backup the operation is executing on. |
| `--database` | DATABASE |  | For a database operation, the name of the database the operation is executing on. |
| `--instance-partition` | INSTANCE_PARTITION |  | For an instance partition operation, the name of the instance partition the operation is executing on. |


**Examples:**
```bash
To describe a Cloud Spanner instance operation, run:

    $ gcloud spanner operations describe _auto_12345 \
        --instance=my-instance-id

To describe a Cloud Spanner database operation, run:

    $ gcloud spanner operations describe _auto_12345 \
        --instance=my-instance-id --database=my-database-id

To describe a Cloud Spanner backup operation, run:

    $ gcloud spanner operations describe _auto_12345 \
        --instance=my-instance-id --backup=my-backup-id

To describe an instance partition operation, run:

    $ gcloud spanner operations describe _auto_12345 \
        --instance=my-instance-id --instance-partition=my-partition-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/operations/describe)

---
### `gcloud spanner operations list`

List the Cloud Spanner operations

List the Cloud Spanner operations.

**Synopsis:**
```
gcloud spanner operations list
    (--instance=INSTANCE | --instance-config=INSTANCE_CONFIG)
    [--backup=BACKUP] [--database=DATABASE]
    [--instance-partition=INSTANCE_PARTITION] [--type=TYPE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[Exactly one of these must be specified:]_ The ID of the instance the operation is executing on. |
| `--instance-config` | INSTANCE_CONFIG |  | _[Exactly one of these must be specified:]_ The ID of the instance configuration the operation is executing on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backup` | BACKUP |  | For backup operations, the name of the backup the operations are executing on. |
| `--database` | DATABASE |  | For database operations, the name of the database the operations are executing on. |
| `--instance-partition` | INSTANCE_PARTITION |  | For instance partition operations, the name of the instance partition the operation is executing on. |
| `--type` | one of: BACKUP If only the instance is specified (--instance), returns all backup operations associated with backups in the instance |  | (optional) List only the operations of the given type. TYPE must be one of: BACKUP If only the instance is specified (--instance), returns all backup operations associated with backups in the instance. When a backup is specified (--backup), only the backup operations for the given backup are returned. DATABASE If only the instance is specified (--instance), returns all database operations associated with the databases in the instance. When a database is specified (--database), the command would return database operations for the given database. DATABASE_CHANGE_QUORUM Database change quorum operations are returned for all databases in the given instance (--instance only) or only those associated with the given database (--database). DATABASE_CREATE Database create operations are returned for all databases in the given instance (--instance only) or only those associated with the given database (--database) DATABASE_RESTORE Database restore operations are returned for all databases in the given instance (--instance only) or only those associated with the given database (--database) DATABASE_UPDATE_DDL Database update DDL operations are returned for all databases in the given instance (--instance only) or only those associated with the given database (--database) INSTANCE Returns instance operations for the given instance. Note, type=INSTANCE does not work with --database or --backup. INSTANCE_CONFIG_CREATE Instance configuration create operations are returned for the given instance configuration (--instance-config). INSTANCE_CONFIG_UPDATE Instance configuration update operations are returned for the given instance configuration (--instance-config). INSTANCE_PARTITION If only the instance is specified (--instance), returns all instance partition operations associated with instance partitions in the instance. When an instance partition is specified (--instance-partition), only the instance partition operations for the given instance partition are returned. |


**Examples:**
```bash
To list Cloud Spanner instance operations for an instance, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --type=INSTANCE

To list Cloud Spanner backup operations for an instance, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --type=BACKUP

To list Cloud Spanner database operations for an instance, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --type=DATABASE

To list Cloud Spanner database operations for a database, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --database=my-database-id --type=DATABASE

To list Cloud Spanner backup operations for a database, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --database=my-database-id --type=BACKUP

To list Cloud Spanner backup operations for a backup, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --backup=my-backup-id --type=BACKUP

To list instance partition operations for an instance partition, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --instance-partition=my-partition-id --type=INSTANCE_PARTITION

To list instance partition operations for all instance partitions belonging
to this instance, run:

    $ gcloud spanner operations list --instance=my-instance-id \
        --type=INSTANCE_PARTITION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/operations/list)

---
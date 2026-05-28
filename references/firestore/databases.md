# gcloud firestore databases

manage Creation of Cloud Firestore in Native mode Database

### `gcloud firestore databases clone`

Clone a Google Cloud Firestore database from another

**Synopsis:**
```
gcloud firestore databases clone
    --destination-database=DESTINATION_DATABASE
    --snapshot-time=SNAPSHOT_TIME --source-database=SOURCE_DATABASE
    [--tags=[KEY=VALUE,...]]
    [--encryption-type=ENCRYPTION_TYPE : --kms-key-name=KMS_KEY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-database` | DESTINATION_DATABASE |  | Destination database to clone to. Destination database will be created in the same location as the source database. This value should be 4-63 characters. Valid characters are /[a-z][0-9]-/ with first character a letter and the last a letter or a number. Must not be UUID-like /[0-9a-f]8(-[0-9a-f]4)3-[0-9a-f]12/. Using "(default)" database ID is also allowed. For example, to clone to database testdb: $ gcloud firestore databases clone --destination-database=testdb |
| `--snapshot-time` | SNAPSHOT_TIME |  | Snapshot time at which to clone. This must be a whole minute, in the past, and not earlier than the source database's earliest_version_time. Additionally, if older than one hour in the past, PITR must be enabled on the source database. For example, to restore from snapshot 2025-05-26T10:20:00.00Z of source database source-db: $ gcloud firestore databases clone \ --source-database=projects/PROJECT_ID/databases/source-db \ --snapshot-time=2025-05-26T10:20:00.00Z |
| `--source-database` | SOURCE_DATABASE |  | The source database to clone from. For example, to clone from database source-db: $ gcloud firestore databases clone \ --source-database=projects/PROJECT_ID/databases/source-db |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tags` | [KEY=VALUE,...] |  | Tags to attach to the destination database. Example: --tags=key1=value1,key2=value2 For example, to attach tags to a database: $ --tags=key1=value1,key2=value2 |


**Examples:**
```bash
To clone a database from another:

    $ gcloud firestore databases clone \
      --source-database=projects/PROJECT_ID/databases/\
    SOURCE_DATABASE --snapshot-time=2025-05-26T10:20:00.00Z \
        --destination-database=DATABASE_ID

To clone to a CMEK-enabled database:

    $ gcloud firestore databases clone \
      --source-database=projects/PROJECT_ID/databases/\
    SOURCE_DATABASE --snapshot-time=2025-05-26T10:20:00.00Z \
        --destination-database=DATABASE_ID \
        --encryption-type=customer-managed-encryption \
        --kms-key-name=projects/PROJECT_ID/locations/LOCATION_ID/\
    keyRings/KEY_RING_ID/cryptoKeys/CRYPTO_KEY_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/clone)

---
### `gcloud firestore databases connection-string`

Prints the mongo connection string for the given Firestore database

**Synopsis:**
```
gcloud firestore databases connection-string --database=DATABASE
    [--auth=AUTH; default="none" | --validate=VALIDATE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore databases connection-string --database='foo' |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auth` | one of: none, gce-vm, access-token, scram-sha-256 | none | _[At most one of these can be specified:]_ The auth configuration for the connection string. If connecting from a Google Compute Engine VM, use gce-vm. For short term access using the gcloud CLI's access token, use access-token. For password auth use scram-sha-256. Otherwise, use none and configure auth manually. AUTH must be one of: none, gce-vm, access-token, scram-sha-256. |
| `--validate` | VALIDATE |  | _[At most one of these can be specified:]_ Validate the specified connection string for the current database. This command checks that the connection string is well formed, contains the required parameters, and specifies correct configuration values for the current database. |


**Examples:**
```bash
To get the connection string for a Firestore database with a databaseId
testdb without auth configuration.

    $ gcloud firestore databases connection-string --database=testdb \
      --auth=none

To get the connection string for a Firestore database with a databaseId
testdb with Google Compute Engine VM auth.

    $ gcloud firestore databases connection-string --database=testdb \
      --auth=gce-vm
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/connection-string)

---
### `gcloud firestore databases create`

Create a Google Cloud Firestore database via Firestore API

**Synopsis:**
```
gcloud firestore databases create --location=LOCATION
    [--database=DATABASE; default="(default)"] [--delete-protection]
    [--edition=EDITION; default="standard"]
    [--enable-firestore-data-access]
    [--enable-mongodb-compatible-data-access] [--enable-pitr]
    [--enable-realtime-updates] [--kms-key-name=KMS_KEY_NAME]
    [--tags=[KEY=VALUE,...]] [--type=TYPE; default="firestore-native"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location to operate on. Available locations are listed at https://cloud.google.com/firestore/docs/locations. For example, to operate on location us-east1: $ gcloud firestore databases create --location='us-east1' |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE | (default) | The ID to use for the database, which will become the final component of the database's resource name. If database ID is not provided, (default) will be used as database ID. This value should be 4-63 characters. Valid characters are /[a-z][0-9]-/ with first character a letter and the last a letter or a number. Must not be UUID-like /[0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12}/. Using "(default)" database ID is also allowed. |
| `--delete-protection` |  |  | Whether to enable delete protection on the created database. If set to true, delete protection of the new database will be enabled and delete operations will fail unless delete protection is disabled. Default to false. |
| `--edition` | one of: standard, enterprise | standard | The edition of the database. EDITION must be one of: standard, enterprise. |
| `--enable-firestore-data-access` |  |  | Whether to enable Firestore API Data Access on the created database. If set to true, Firestore API Data Access on the new database will be enabled. By default, this feature is disabled for Enterprise edition databases. To explicitly disable, use --no-enable-firestore-data-access. |
| `--enable-mongodb-compatible-data-access` |  |  | Whether to enable MongoDB Compatible API Data Access on the created database. If set to true, MongoDB Compatible API Data Access on the new database will be enabled. By default, this feature is enabled for Enterprise edition databases. To disable, use --no-enable-mongodb-compatible-data-access. |
| `--enable-pitr` |  |  | Whether to enable Point In Time Recovery (PITR) on the created database. If set to true, PITR on the new database will be enabled. By default, this feature is not enabled. |
| `--enable-realtime-updates` |  |  | Whether to enable Realtime Updates feature on the created database. If set to true, Realtime Updates feature on the new database will be enabled. By default, this feature is disabled for Enterprise edition databases. To explicitly disable, use --no-enable-realtime-updates. |
| `--kms-key-name` | KMS_KEY_NAME |  | The resource ID of a Cloud KMS key. If set, the database created will be a Customer-Managed Encryption Key (CMEK) database encrypted with this key. This feature is allowlist only in initial launch. Only a key in the same location as this database is allowed to be used for encryption. For Firestore's nam5 multi-region, this corresponds to Cloud KMS location us. For Firestore's eur3 multi-region, this corresponds to Cloud KMS location europe. See https://cloud.google.com/kms/docs/locations. This value should be the KMS key resource ID in the format of projects/{project_id}/locations/{kms_location}/keyRings/{key_ring}/cryptoKeys/{crypto_key}. How to retrieve this resource ID is listed at https://cloud.google.com/kms/docs/getting-resource-ids#getting_the_id_for_a_key_and_version. |
| `--tags` | [KEY=VALUE,...] |  | Tags to attach to the destination database. Example: --tags=key1=value1,key2=value2 For example, to attach tags to a database: $ --tags=key1=value1,key2=value2 |
| `--type` | one of: firestore-native, datastore-mode | firestore-native | The type of the database. TYPE must be one of: firestore-native, datastore-mode. |


**Examples:**
```bash
To create a Firestore Enterprise database named foo in nam5 for use with
MongoDB Compatible API with Data Access Mode enabled.

    $ gcloud firestore databases create --database=foo \
      --edition=enterprise --location=nam5 \
      --enable-mongodb-compatible-data-access

To create a Firestore Enterprise database named foo in nam5 for use with
Firestore API Data Access Mode enabled and Realtime Updates disabled.

    $ gcloud firestore databases create --database=foo \
      --edition=enterprise --location=nam5 \
      --enable-firestore-data-access

To create a Firestore Enterprise database named foo in nam5 for use with
Firestore API Data Access Mode enabled and Realtime Updates enabled.

    $ gcloud firestore databases create --database=foo \
      --edition=enterprise --location=nam5 \
      --enable-firestore-data-access --enable-realtime-updates

To create a Firestore Native database in nam5.

    $ gcloud firestore databases create --location=nam5

To create a Firestore Native database in us-central1 with tags.

    $ gcloud firestore databases create --location=us-central1 \
      --tags=key1=value1,key2=value2

To create a Datastore Mode database in us-east1.

    $ gcloud firestore databases create --location=us-east1 \
      --type=datastore-mode

To create a Datastore Mode database in us-east1 with a databaseId foo.

    $ gcloud firestore databases create --database=foo \
      --location=us-east1 --type=datastore-mode

To create a Firestore Native database in nam5 with delete protection
enabled.

    $ gcloud firestore databases create --location=nam5 \
      --delete-protection

To create a Firestore Native database in nam5 with Point In Time Recovery
(PITR) enabled.

    $ gcloud firestore databases create --location=nam5 --enable-pitr

To create a Firestore Native database in nam5 encrypted by a
Customer-managed encryption key (CMEK).

    $ gcloud firestore databases create --location=nam5 \
      --kms-key-name=projects/PROJECT_ID/locations/us/keyRings/\
    KEY_RING_ID/cryptoKeys/CRYPTO_KEY_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/create)

---
### `gcloud firestore databases delete`

Delete a Google Cloud Firestore database

**Synopsis:**
```
gcloud firestore databases delete --database=DATABASE [--etag=ETAG]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | The current etag of the Database. If an etag is provided and does not match the current etag of the database, deletion will be blocked and a FAILED_PRECONDITION error will be returned. |


**Examples:**
```bash
To delete a Firestore database test.

    $ gcloud firestore databases delete --database=test

To delete the Firestore (default) database.

    $ gcloud firestore databases delete --database=(default)

To delete a Firestore database test providing etag.

    $ gcloud firestore databases delete --database=test --etag=etag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/delete)

---
### `gcloud firestore databases describe`

Describes information about a Cloud Firestore database

The following command describes a Google Cloud Firestore database.

**Synopsis:**
```
gcloud firestore databases describe
    [--database=DATABASE; default="(default)"] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore databases describe --database='foo' |


**Examples:**
```bash
To describe a Firestore database with a databaseId testdb.

    $ gcloud firestore databases describe --database=testdb

If databaseId is not specified, the command will describe information about
the (default) database.

    $ gcloud firestore databases describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/describe)

---
### `gcloud firestore databases list`

Lists all Firestore databases under the project

**Synopsis:**
```
gcloud firestore databases list [--show-deleted] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Show the deleted databases. |


**Examples:**
```bash
To list all active Firestore databases.

    $ gcloud firestore databases list

To list all Firestore databases including deleted databases.

    $ gcloud firestore databases list --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/list)

---
### `gcloud firestore databases ping`

Times the connection and ping time for a Firestore with MongoDB compatibility database

**Synopsis:**
```
gcloud firestore databases ping --database=DATABASE [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore databases ping --database='foo' |


**Examples:**
```bash
To time the connection and ping times for a Firestore with MongoDB
compatibility database testdb:

    $ gcloud firestore databases ping --database=testdb
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/ping)

---
### `gcloud firestore databases restore`

Restores a Cloud Firestore database from a backup

**Synopsis:**
```
gcloud firestore databases restore
    --destination-database=DESTINATION_DATABASE
    --source-backup=SOURCE_BACKUP [--tags=[KEY=VALUE,...]]
    [--encryption-type=ENCRYPTION_TYPE : --kms-key-name=KMS_KEY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-database` | DESTINATION_DATABASE |  | Destination database to restore to. Destination database will be created in the same location as the source backup. This value should be 4-63 characters. Valid characters are /[a-z][0-9]-/ with first character a letter and the last a letter or a number. Must not be UUID-like /[0-9a-f]8(-[0-9a-f]4)3-[0-9a-f]12/. Using "(default)" database ID is also allowed. For example, to restore to database testdb: $ gcloud firestore databases restore --destination-database=testdb |
| `--source-backup` | SOURCE_BACKUP |  | The source backup to restore from. For example, to restore from backup cf9f748a-7980-4703-b1a1-d1ffff591db0 in us-east1: $ gcloud firestore databases restore \ --source-backup=projects/PROJECT_ID/locations/us-east1/backups/\ cf9f748a-7980-4703-b1a1-d1ffff591db0 |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--tags` | [KEY=VALUE,...] |  | Tags to attach to the destination database. Example: --tags=key1=value1,key2=value2 For example, to attach tags to a database: $ --tags=key1=value1,key2=value2 |


**Examples:**
```bash
To restore a database from a backup.

    $ gcloud firestore databases restore \
      --source-backup=projects/PROJECT_ID/locations/LOCATION_ID/\
    backups/BACKUP_ID --destination-database=DATABASE_ID

To restore a database from a backup with tags.

    $ gcloud firestore databases restore \
      --source-backup=projects/PROJECT_ID/locations/LOCATION_ID/\
    backups/BACKUP_ID --destination-database=DATABASE_ID \
        --tags=key1=value1,key2=value2

To restore to a CMEK-enabled database.

    $ gcloud firestore databases restore \
      --source-backup=projects/PROJECT_ID/locations/LOCATION_ID/\
    backups/BACKUP_ID --destination-database=DATABASE_ID \
        --encryption-type=customer-managed-encryption \
        --kms-key-name=projects/PROJECT_ID/locations/LOCATION_ID/\
    keyRings/KEY_RING_ID/cryptoKeys/CRYPTO_KEY_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/restore)

---
### `gcloud firestore databases update`

Update the database configuration of a Cloud Firestore database

Update the database configuration of a Cloud Firestore database.

**Synopsis:**
```
gcloud firestore databases update [--async] [--database=DATABASE]
    [--delete-protection] [--enable-pitr] [--type=TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--delete-protection` |  |  | _[+ the default value of argument [--database] is (default).]_ If set to true, the Firestore database will be updated to have database delete protection enabled. A database with delete protection enabled cannot be deleted. You can disable the delete protection via --no-delete-protection. |
| `--enable-pitr` |  |  | _[+ the default value of argument [--database] is (default).]_ If set to true, the Firestore database will be updated to enable Point In Time Recovery. You can disable the this feature via --no-enable-pitr. |
| `--type` | one of: datastore-mode, firestore-native |  | _[+ the default value of argument [--database] is (default).]_ The database type. TYPE must be one of: datastore-mode, firestore-native. |


**Examples:**
```bash
The following command updates the database type of a Cloud Firestore
database.

    $ gcloud firestore databases update --type=firestore-native
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/databases/update)

---
# gcloud sql export

provide commands to export Cloud SQL instances

### `gcloud sql export bak`

Export data from a Cloud SQL instance to a BAK file

Export data from a Cloud SQL instance to a Google Cloud Storage bucket as a
BAK backup file. This is only supported for SQL Server.

**Synopsis:**
```
gcloud sql export bak INSTANCE URI --database=DATABASE,[DATABASE,...], -d
    DATABASE,[DATABASE,...] [--async] [--bak-type=BAK_TYPE; default="FULL"]
    [--differential-base] [--export-log-end-time=EXPORT_LOG_END_TIME]
    [--export-log-start-time=EXPORT_LOG_START_TIME]
    [--stripe_count=STRIPE_COUNT] [--[no-]striped] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.

URI
   The path to the file in Google Cloud Storage where the export will be
   stored. The URI is in the form gs://bucketName/fileName. If the file
   already exists, the operation fails.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...] |  | Database from which the export is made. Information on requirements can be found here: https://cloud.google.com/sql/docs/sqlserver/admin-api/v1beta4/instances/export#exportContext.databases |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bak-type` | one of: FULL, DIFF, TLOG | FULL | Type of bak file that will be exported, FULL or DIFF. SQL Server only. BAK_TYPE must be one of: FULL, DIFF, TLOG. |
| `--differential-base` |  |  | Whether the bak file export can be used as differential base for future differential backup. SQL Server only |
| `--export-log-end-time` | EXPORT_LOG_END_TIME |  | Optional flag. The end time of the transaction log files that are included in the export file. Use this flag to export transaction logs for Cloud SQL for SQL Server only. Format: YYYY-MM-DDTHH:MM:SSZ, UTC timezone only. |
| `--export-log-start-time` | EXPORT_LOG_START_TIME |  | Optional flag. The start time of the transaction log files that are included in the export file. Use this flag to export transaction logs for Cloud SQL for SQL Server only. Format: YYYY-MM-DDTHH:MM:SSZ, UTC timezone only. |
| `--stripe` | STRIPE_COUNT |  | Specifies the number of stripes to use for SQL Server exports. |
| `--[no-]striped` |  |  | Whether SQL Server export should be striped. Use --striped to enable and --no-striped to disable. |


**Examples:**
```bash
To export data from the database my-database in the Cloud SQL instance
my-instance to a BAK file my-bucket/my-export.bak, run:

    $ gcloud sql export bak my-instance gs://my-bucket/my-export.bak \
        --database=my-database
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/export/bak)

---
### `gcloud sql export csv`

Exports data from a Cloud SQL instance to a CSV file

Exports data from a Cloud SQL instance to a Google Cloud Storage bucket as
a plain text file with one line per row and comma-separated fields.

**Synopsis:**
```
gcloud sql export csv INSTANCE URI --query=QUERY [--async]
    [--database=DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...]]
    [--escape=ESCAPE] [--fields-terminated-by=FIELDS_TERMINATED_BY]
    [--lines-terminated-by=LINES_TERMINATED_BY] [--offload] [--quote=QUOTE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.

URI
   The path to the file in Google Cloud Storage where the export will be
   stored. The URI is in the form gs://bucketName/fileName. If the file
   already exists, the operation fails. If the filename ends with .gz, the
   contents are compressed.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--query` | QUERY |  | A SQL SELECT query (e.g., SELECT * FROM table) that specifies the data to export. WARNING: While in-transit, the query might be processed in intermediate locations other than the location of the target instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--database` | DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...] |  | Database(s) from which the export is made. Information on requirements can be found here: https://cloud.google.com/sql/docs/mysql/admin-api/v1beta4/instances/export#exportContext.databases |
| `--escape` | ESCAPE |  | Specifies the character that should appear before a data character that needs to be escaped. The value of this argument has to be a character in Hex ASCII Code. For example, "22" represents double quotes. This flag is only available for MySQL and Postgres. If this flag is not provided, double quotes character will be used as the default value. |
| `--fields-terminated-by` | FIELDS_TERMINATED_BY |  | Specifies the character that splits column values. The value of this argument has to be a character in Hex ASCII Code. For example, "2C" represents a comma. This flag is only available for MySQL and Postgres. If this flag is not provided, a comma character will be used as the default value. |
| `--lines-terminated-by` | LINES_TERMINATED_BY |  | Specifies the character that split line records. The value of this argument has to be a character in Hex ASCII Code. For example, "0A" represents a new line. This flag is only available for MySQL. If this flag is not provided, a new line character will be used as the default value. |
| `--offload` |  |  | Offload an export to a temporary instance. Doing so reduces strain on source instances and allows other operations to be performed while the export is in progress. |
| `--quote` | QUOTE |  | Specifies the character that encloses values from columns that have string data type. The value of this argument has to be a character in Hex ASCII Code. For example, "22" represents double quotes. This flag is only available for MySQL and Postgres. If this flag is not provided, double quotes character will be used as the default value. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/export/csv)

---
### `gcloud sql export sql`

Exports data from a Cloud SQL instance to a SQL file

Exports data from a Cloud SQL instance to a Google Cloud Storage bucket as
a SQL dump file.

NOTE: Certain roles and permissions are required to export data to Google
Cloud Storage. For more information on exporting data from Google Cloud SQL
see Export from Cloud SQL to a SQL dump file
(https://cloud.google.com/sql/docs/mysql/import-export/import-export-sql#gcloud).

**Synopsis:**
```
gcloud sql export sql INSTANCE URI [--async] [--clean]
    [--database=DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...]]
    [--if-exists] [--offload] [--parallel]
    [--table=TABLE,[TABLE,...], -t TABLE,[TABLE,...]] [--threads=THREADS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.

URI
   The path to the file in Google Cloud Storage where the export will be
   stored. The URI is in the form gs://bucketName/fileName. If the file
   already exists, the operation fails. If the filename ends with .gz, the
   contents are compressed.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--clean` |  |  | Include SQL statements (DROP <object>) required to drop database objects prior to import; corresponds to the clean flag for pg_dump. Only applies to PostgreSQL non-parallel exports. |
| `--database` | DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...] |  | Database(s) from which the export is made. Information on requirements can be found here: https://cloud.google.com/sql/docs/mysql/admin-api/v1beta4/instances/export#exportContext.databases |
| `--if-exists` |  |  | Include an SQL statement (IF EXISTS) with each drop statement produced by the clean flag; corresponds to the if-exists flag for pg_dump. Only applies to PostgreSQL non-parallel exports. |
| `--offload` |  |  | Offload an export to a temporary instance. Doing so reduces strain on source instances and allows other operations to be performed while the export is in progress. |
| `--parallel` |  |  | Perform a parallel export. This flag is only applicable to MySQL and Postgres. |
| `--table` | TABLE,[TABLE,...], -t TABLE,[TABLE,...] |  | Tables to export from the specified database. If you specify tables, specify one and only one database. For PostgreSQL instances, only one table can be exported at a time. |
| `--threads` | THREADS |  | Specifies the number of threads to use for the parallel export. If --parallel is specified and this flag is not provided, Cloud SQL uses a default thread count to optimize performance. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/export/sql)

---
### `gcloud sql export tde`

Export a TDE certificate from a Cloud SQL for SQL Server instance

Exports a TDE certificate from a Cloud SQL instance to a Google Cloud
Storage bucket. This is only supported for SQL Server.

**Synopsis:**
```
gcloud sql export tde INSTANCE
    (--cert-path=CERT_PATH --certificate=CERTIFICATE
      --pvk-path=PVK_PATH (--prompt-for-pvk-password
      | --pvk-password=PVK_PASSWORD)) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cert-path` | CERT_PATH |  | _[This must be specified.]_ Path to the encryption certificate file in Google Cloud Storage. The URI is in the form gs://bucketName/fileName. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--certificate` | CERTIFICATE |  | _[This must be specified.]_ Name of the encryption certificate. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--pvk-path` | PVK_PATH |  | _[This must be specified.]_ Path to the encryption private key file in Google Cloud Storage. The URI is in the form gs://bucketName/fileName. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To export a TDE certificate with the name foo and private key password
my-pvk-password in the Cloud SQL instance my-instance to certificate path
my-bucket/my-cert.cert and private key path my-bucket/my-key.pvk, run:

    $ gcloud sql export tde my-instance --certificate=foo \
        --cert-path=gs://my-bucket/my-cert.cert \
        --pvk-path=gs://my-bucket/my-key.pvk \
        --pvk-password=my-pvk-password

To export a TDE certificate with the name foo and private key password
my-pvk-password in the Cloud SQL instance my-instance and prompting for the
private key password, run:

    $ gcloud sql export tde my-instance --certificate=foo \
        --cert-path=gs://my-bucket/my-cert.cert \
        --pvk-path=gs://my-bucket/my-key.pvk --prompt-for-pvk-password
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/export/tde)

---
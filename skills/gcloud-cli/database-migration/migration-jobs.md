# gcloud database-migration migration-jobs

manage Database Migration Service migration jobs

### `gcloud database-migration migration-jobs create`

Create a Database Migration Service migration job

Create a Database Migration Service migration job. Recommended steps before
creating the migration job:
  o Create a source connection profile. See prerequisites here
    (https://cloud.google.com/database-migration/docs/mysql/configure-source-database).
  o Create a destination connection profile. For migrating to Cloud SQL
    for MySQL or Cloud SQL for PostgreSQL, use the cloudsql connection
    profile for DMS to create the CloudSQL replica for you.
  o Configure the connectivity method. See prerequisites here
    (https://cloud.google.com/database-migration/docs/mysql/configure-connectivity).
  o [Heterogeneous migrations only] Create a conversion workspace.

**Synopsis:**
```
gcloud database-migration migration-jobs create
    (MIGRATION_JOB : --region=REGION) --destination=DESTINATION
    --source=SOURCE --type=TYPE [--no-async] [--commit-id=COMMIT_ID]
    [--conversion-workspace=CONVERSION_WORKSPACE]
    [--display-name=DISPLAY_NAME]
    [--dump-parallel-level=DUMP_PARALLEL_LEVEL] [--dump-type=DUMP_TYPE]
    [--filter=FILTER] [--labels=[KEY=VALUE,...]]
    [--all-databases | --databases-filter=databaseName,[...]]
    [--cmek-key=CMEK_KEY
      : --cmek-keyring=CMEK_KEYRING --cmek-project=CMEK_PROJECT]
    [--dump-flags=[KEY=VALUE,...] | --dump-path=DUMP_PATH]
    [--max-concurrent-cdc-connections=MAX_CONCURRENT_CDC_CONNECTIONS
      --max-concurrent-full-dump-connections=MAX_CONCURRENT_FULL_DUMP_CONNECTIONS --skip-full-dump --oracle-cdc-start-position=ORACLE_CDC_START_POSITION | --sqlserver-cdc-start-position=SQLSERVER_CDC_START_POSITION --max-concurrent-destination-connections=MAX_CONCURRENT_DESTINATION_CONNECTIONS --transaction-timeout=TRANSACTION_TIMEOUT]
    [--peer-vpc=PEER_VPC | --static-ip
      | [--vm-ip=VM_IP --vm-port=VM_PORT --vpc=VPC : --vm=VM]]
    [--sqlserver-databases=databaseName,[...] : --sqlserver-diff-backup
      --sqlserver-encrypted-databases=SQLSERVER_ENCRYPTED_DATABASES
      --sqlserver-promote-when-ready] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the migration_job.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | _[This must be specified.]_ ID of the connection_profile or fully qualified identifier for the connection_profile. To set the connection_profile attribute: + provide the argument --destination on the command line. |
| `--source` | SOURCE |  | _[This must be specified.]_ ID of the connection_profile or fully qualified identifier for the connection_profile. To set the connection_profile attribute: + provide the argument --source on the command line. |
| `--type` | one of: ONE_TIME, CONTINUOUS |  | _[This must be specified.]_ Type of the migration job. TYPE must be one of: ONE_TIME, CONTINUOUS. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--commit-id` | COMMIT_ID |  | Commit id for the conversion workspace to use for creating the migration job. If not specified, the latest commit id will be used by default. |
| `--display-name` | DISPLAY_NAME |  | _[+ provide the argument --conversion-workspace on the command line.]_ A user-friendly name for the migration job. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--dump-parallel-level` | one of: MIN, OPTIMAL, MAX |  | _[+ provide the argument --conversion-workspace on the command line.]_ Parallelization level during initial dump of the migration job. If not specified, will be defaulted to OPTIMAL. DUMP_PARALLEL_LEVEL must be one of: MIN, OPTIMAL, MAX. |
| `--dump-type` | one of: LOGICAL, PHYSICAL |  | _[+ provide the argument --conversion-workspace on the command line.]_ The type of the data dump. Currently applicable for MySQL to MySQL migrations only. DUMP_TYPE must be one of: LOGICAL, PHYSICAL. |
| `--filter` | FILTER |  | _[+ provide the argument --conversion-workspace on the command line.]_ Filter the entities based on AIP-160 (https://google.aip.dev/160) standard. Example: to filter all tables whose name start with "Employee" and are present under schema "Company", use filter as "Company.Employee* AND type=TABLE" |
| `--labels` | [KEY=VALUE,...] |  | _[+ provide the argument --conversion-workspace on the command line.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a continuous migration job with IP allowlist connectivity:

    $ gcloud database-migration migration-jobs create my-migration-job \
      --region=us-central1 --type=CONTINUOUS --source=cp1 \
      --destination=cp2

To create a continuous migration job with VPC peering connectivity:

    $ gcloud database-migration migration-jobs create my-migration-job \
      --region=us-central1 --type=CONTINUOUS --source=cp1 \
      --destination=cp2 \
      --peer-vpc=projects/my-project/global/networks/my-network

To create a one-time migration job with reverse-SSH tunnel connectivity:

    $ gcloud database-migration migration-jobs create my-migration-job \
      --region=us-central1 --type=ONE_TIME --source=cp1 \
      --destination=cp2 --vm=vm1 --vm-ip=1.1.1.1 --vm-port=1111 \
      --vpc=projects/my-project/global/networks/my-network

To create a heterogeneous continuous migration job:

    $ gcloud database-migration migration-jobs create my-migration-job \
      --region=us-central1 --type=CONTINUOUS --source=cp1 \
      --destination=cp2 --conversion-workspace=cw

To create a continuous SQL Server to SQL Server homogeneous migration job
with differential backup enabled:        $ gcloud database-migration migration-jobs create my-migration-job \
      --region=us-central1 --type=CONTINUOUS --source=cp1 \
      --destination=cp2 --sqlserver-diff-backup \
      --sqlserver-databases=db1,db2,db3

To create a continuous SQL Server to SQL Server homogeneous migration job
with encrypted databases:        $ gcloud database-migration migration-jobs create my-migration-job \
      --region=us-central1 --type=CONTINUOUS --source=cp1 \
      --destination=cp2 --sqlserver-databases=db1,db2,db3 \
      --sqlserver-encrypted-databases=PATH/TO/ENCRYPTION/SETTINGS
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/create)

---
### `gcloud database-migration migration-jobs delete`

Delete a Database Migration Service migration job

Delete a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs delete
    (MIGRATION_JOB : --region=REGION) [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - Migration job resource - Database Migration
Service migration job to delete. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | The destination Cloud SQL connection profile is always deleted with the migration job. In case of force delete, the destination Cloud SQL replica database is also deleted. |


**Examples:**
```bash
To delete a migration job:

    $ gcloud database-migration migration-jobs delete MIGRATION_JOB \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/delete)

---
### `gcloud database-migration migration-jobs demote-destination`

Demote a destination of a Database Migration Service migration job

Demote a destination of a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs demote-destination
    (MIGRATION_JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - Migration job resource - Cloud Database Migration
Service migration job to demote its destination. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To Demote a migration job destination:

    $ gcloud database-migration migration-jobs demote-destination \
      MIGRATION_JOB --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/demote-destination)

---
### `gcloud database-migration migration-jobs describe`

Show details about a Database Migration Service migration job

Show details about a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs describe
    (MIGRATION_JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job you want to get the details of.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To show details about a migration job, run:

    $ gcloud database-migration migration-jobs describe \
        my-migration-job --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/describe)

---
### `gcloud database-migration migration-jobs fetch-source-objects`

Fetch objects for a Database Migration Service migration job by connection to the source

Fetch objects for a Database Migration Service migration job by connection
to the source.

**Synopsis:**
```
gcloud database-migration migration-jobs fetch-source-objects
    (MIGRATION_JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job to restart. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the migration_job.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/fetch-source-objects)

---
### `gcloud database-migration migration-jobs generate-ssh-script`

Generate a SSH script for a Database Migration Service migration job

Generate a script for a Database Migration Service migration job, to
configure Reverse SSH tunnel connectivity with a bastion host on a Compute
Engine VM instance. You can use an existing VM instance or create a new VM
for this purpose.

Copy the generated script and run it in bash from a machine that has:
  o The gcloud command-line tool installed.
  o Access to your source database.
  o Access to the existing bastion VM, or permissions and access to the
    Cloud Compute API if creating a new bastion VM. Make sure this machine
    is available during the entire migration.

Running the script will set up the SSH tunnel on the VM you selected and
will establish connectivity between the source database and the Cloud SQL
instance. Find additional information here
(https://cloud.google.com/database-migration/docs/mysql/configure-connectivity-reverse-ssh-tunnel).

**Synopsis:**
```
gcloud database-migration migration-jobs generate-ssh-script
    (MIGRATION_JOB : --region=REGION) --vm=VM
    (--vm-zone=VM_ZONE | [--subnet=SUBNET --vm-machine-type=VM_MACHINE_TYPE
      : --vm-zone-create=VM_ZONE_CREATE]) [--vm-port=VM_PORT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job to generate the SSH script for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vm` | VM |  | Bastion Compute Engine VM instance name to use or to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vm-port` | VM_PORT |  | Port that will be open on the bastion host. |


**Examples:**
```bash
To generate an SSH script with bastion VM instance creation:

    $ gcloud database-migration migration-jobs generate-ssh-script \
        my-migration-job --vm=vm1 --vm-port=1111 \
        --vm-machine-type=n1-standard-1 --vm-zone-create=us-central1-a \
        --subnet=sample-subnet --region=us-central1

To generate an SSH script with an existing bastion VM instance:

    $ gcloud database-migration migration-jobs generate-ssh-script \
        my-migration-job --vm=vm1 --vm-port=1111 \
        --vm-zone=us-central1-a --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/generate-ssh-script)

---
### `gcloud database-migration migration-jobs list`

List Database Migration Service migration jobs

List Database Migration Service migration jobs.

**Synopsis:**
```
gcloud database-migration migration-jobs list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all migration jobs in a project and region 'us-central1', run:

    $ gcloud database-migration migration-jobs list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/list)

---
### `gcloud database-migration migration-jobs promote`

Promote a Database Migration Service migration job

Promote a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs promote
    (MIGRATION_JOB : --region=REGION)
    [--databases-filter=databaseName,[...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job to promote. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the migration_job.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--databases-filter` | databaseName,[...] |  | _[The migration job objects config.]_ A list of databases to be migrated to the destination instance. Provide databases as a comma separated list. This flag is used only for SQL Server to Cloud SQL SQL Server migrations. |


**Examples:**
```bash
To promote a migration job:

    $ gcloud database-migration migration-jobs promote MIGRATION_JOB \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/promote)

---
### `gcloud database-migration migration-jobs restart`

Restart a Database Migration Service migration job

Restart a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs restart
    (MIGRATION_JOB : --region=REGION)
    [--databases-filter=databaseName,[...]] [--restart-failed-objects]
    [--skip-validation] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job to restart. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the migration_job.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--databases-filter` | databaseName,[...] |  | _[At most one of these can be specified:]_ A list of databases to be migrated to the destination instance. Provide databases as a comma separated list. This flag is used only for SQL Server to Cloud SQL SQL Server migrations. |
| `--restart-failed-objects` |  |  | _[At most one of these can be specified:]_ Restart the failed objects in the migration job. This flag is used only for Postgres to AlloyDB migrations and Postgres to Cloud SQL Postgres migrations. |
| `--skip-validation` |  |  | _[At most one of these can be specified:]_ Restart the migration job without running prior configuration verification. |


**Examples:**
```bash
To restart a migration job:

    $ gcloud database-migration migration-jobs restart MIGRATION_JOB \
        --region=us-central1

To restart a migration job without running prior configuration
verification:

    $ gcloud database-migration migration-jobs restart MIGRATION_JOB \
        --region=us-central1 --skip-validation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/restart)

---
### `gcloud database-migration migration-jobs resume`

Resume a Database Migration Service migration job

Resume a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs resume
    (MIGRATION_JOB : --region=REGION) [--skip-validation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - Migration job resource - Cloud Database Migration
Service migration job to resume. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--skip-validation` |  |  | Resume the migration job without running prior configuration verification. |


**Examples:**
```bash
To resume a migration job:

    $ gcloud database-migration migration-jobs resume MIGRATION_JOB \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/resume)

---
### `gcloud database-migration migration-jobs start`

Start a Database Migration Service migration job

Start a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs start
    (MIGRATION_JOB : --region=REGION) [--skip-validation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - Migration job resource - Cloud Database Migration
Service migration job to start. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--skip-validation` |  |  | Start the migration job without running prior configuration verification. |


**Examples:**
```bash
To start a migration job:

    $ gcloud database-migration migration-jobs start MIGRATION_JOB \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/start)

---
### `gcloud database-migration migration-jobs stop`

Stop a Database Migration Service migration job

Stop a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs stop
    (MIGRATION_JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - Migration job resource - Cloud Database Migration
Service migration job to stop. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To stop a migration job:

    $ gcloud database-migration migration-jobs stop MIGRATION_JOB \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/stop)

---
### `gcloud database-migration migration-jobs update`

Update a Database Migration Service migration job

Update a Database Migration Service migration job.
  o Draft migration job: user can update all available flags.
  o Any other state can only update flags: --display-name, --dump-path,
    and connectivity method flags.

**Synopsis:**
```
gcloud database-migration migration-jobs update
    (MIGRATION_JOB : --region=REGION) [--no-async] [--commit-id=COMMIT_ID]
    [--destination=DESTINATION] [--display-name=DISPLAY_NAME]
    [--dump-parallel-level=DUMP_PARALLEL_LEVEL] [--dump-type=DUMP_TYPE]
    [--filter=FILTER] [--source=SOURCE] [--type=TYPE]
    [--update-labels=[KEY=VALUE,...]]
    [--all-databases | --databases-filter=databaseName,[...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--dump-flags=[KEY=VALUE,...] | --dump-path=DUMP_PATH]
    [--max-concurrent-cdc-connections=MAX_CONCURRENT_CDC_CONNECTIONS
      --max-concurrent-full-dump-connections=MAX_CONCURRENT_FULL_DUMP_CONNECTIONS --max-concurrent-destination-connections=MAX_CONCURRENT_DESTINATION_CONNECTIONS --transaction-timeout=TRANSACTION_TIMEOUT]
    [--peer-vpc=PEER_VPC | --static-ip
      | --vm=VM --vm-ip=VM_IP --vm-port=VM_PORT --vpc=VPC]
    [--sqlserver-databases=databaseName,[...] --sqlserver-diff-backup
      --sqlserver-encrypted-databases=SQLSERVER_ENCRYPTED_DATABASES
      --sqlserver-promote-when-ready] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - The migration job to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the migration_job.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--commit-id` | COMMIT_ID |  | Commit id for the conversion workspace to use for creating the migration job. If not specified, the latest commit id will be used by default. |
| `--display-name` | DISPLAY_NAME |  | _[+ provide the argument --destination on the command line.]_ A user-friendly name for the migration job. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--dump-parallel-level` | one of: MIN, OPTIMAL, MAX |  | _[+ provide the argument --destination on the command line.]_ Parallelization level during initial dump of the migration job. If not specified, will be defaulted to OPTIMAL. DUMP_PARALLEL_LEVEL must be one of: MIN, OPTIMAL, MAX. |
| `--dump-type` | one of: LOGICAL, PHYSICAL |  | _[+ provide the argument --destination on the command line.]_ The type of the data dump. Currently applicable for MySQL to MySQL migrations only. DUMP_TYPE must be one of: LOGICAL, PHYSICAL. |
| `--filter` | FILTER |  | _[+ provide the argument --destination on the command line.]_ Filter the entities based on AIP-160 (https://google.aip.dev/160) standard. Example: to filter all tables whose name start with "Employee" and are present under schema "Company", use filter as "Company.Employee* AND type=TABLE" |
| `--type` | one of: ONE_TIME, CONTINUOUS |  | _[+ provide the argument --source on the command line.]_ Type of the migration job. TYPE must be one of: ONE_TIME, CONTINUOUS. |
| `--update-labels` | [KEY=VALUE,...] |  | _[+ provide the argument --source on the command line.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the source and destination connection profiles of a draft
migration job:

    $ gcloud database-migration migration-jobs update my-migration-job \
      --region=us-central1 --source=new-src --destination=new-dest

To update the display name of a running migration job:

    $ gcloud database-migration migration-jobs update my-migration-job \
      --region=us-central1 --display-name=new-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/update)

---
### `gcloud database-migration migration-jobs verify`

Verify a Database Migration Service migration job

Verify a Database Migration Service migration job.

**Synopsis:**
```
gcloud database-migration migration-jobs verify
    (MIGRATION_JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Migration job resource - Migration job resource - Cloud Database Migration
Service migration job to verify. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument migration_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MIGRATION_JOB
     ID of the migration_job or fully qualified identifier for the
     migration_job.

     To set the migration_job attribute:
     + provide the argument migration_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument migration_job on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To verify a migration job:

    $ gcloud database-migration migration-jobs verify MIGRATION_JOB \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/migration-jobs/verify)

---
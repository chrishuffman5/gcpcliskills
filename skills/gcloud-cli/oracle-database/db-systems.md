# gcloud oracle-database db-systems

manage Db System resources

### `gcloud oracle-database db-systems create`

Create a new DbSystem

Create a new DbSystem.

**Synopsis:**
```
gcloud oracle-database db-systems create DB_SYSTEM
    --display-name=DISPLAY_NAME --odb-subnet=ODB_SUBNET [--async]
    [--gcp-oracle-zone=GCP_ORACLE_ZONE] [--labels=[LABELS,...]]
    [--location=LOCATION] [--odb-network=ODB_NETWORK]
    [--request-id=REQUEST_ID]
    [[--properties-compute-count=PROPERTIES_COMPUTE_COUNT
      --properties-database-edition=PROPERTIES_DATABASE_EDITION
      --properties-initial-data-storage-size-gb=PROPERTIES_INITIAL_DATA_STORAGE_SIZE_GB --properties-license-model=PROPERTIES_LICENSE_MODEL --properties-shape=PROPERTIES_SHAPE --properties-ssh-public-keys=[PROPERTIES_SSH_PUBLIC_KEYS,
      ...]
      : --db-system-options-storage-management=DB_SYSTEM_OPTIONS_STORAGE_MANAGEMENT --properties-compute-model=PROPERTIES_COMPUTE_MODEL --properties-data-storage-size-gb=PROPERTIES_DATA_STORAGE_SIZE_GB --properties-domain=PROPERTIES_DOMAIN --properties-hostname-prefix=PROPERTIES_HOSTNAME_PREFIX --properties-memory-size-gb=PROPERTIES_MEMORY_SIZE_GB --properties-node-count=PROPERTIES_NODE_COUNT --properties-private-ip=PROPERTIES_PRIVATE_IP --properties-reco-storage-size-gb=PROPERTIES_RECO_STORAGE_SIZE_GB --data-collection-options-is-diagnostics-events-enabled --data-collection-options-is-incident-logs-enabled [--db-home-version=DB_HOME_VERSION (--database-admin-password=DATABASE_ADMIN_PASSWORD : --database-character-set=DATABASE_CHARACTER_SET --database-db-home-name=DATABASE_DB_HOME_NAME --database-db-name=DATABASE_DB_NAME --database-db-unique-name=DATABASE_DB_UNIQUE_NAME --database-id=DATABASE_ID --database-name=DATABASE_NAME --database-ncharacter-set=DATABASE_NCHARACTER_SET --database-tde-wallet-password=DATABASE_TDE_WALLET_PASSWORD [--properties-db-version=PROPERTIES_DB_VERSION : --db-backup-config-auto-enabled --db-backup-config-auto-full-day=DB_BACKUP_CONFIG_AUTO_FULL_DAY --db-backup-config-auto-full-window=DB_BACKUP_CONFIG_AUTO_FULL_WINDOW --db-backup-config-auto-incremental-window=DB_BACKUP_CONFIG_AUTO_INCREMENTAL_WINDOW --db-backup-config-deletion-policy=DB_BACKUP_CONFIG_DELETION_POLICY --db-backup-config-destination-details=[type=TYPE] --db-backup-config-retention-period-days=DB_BACKUP_CONFIG_RETENTION_PERIOD_DAYS]) : --db-home-display-name=DB_HOME_DISPLAY_NAME --db-home-is-unified-auditing-enabled] --time-zone-id=TIME_ZONE_ID --time-zone-version=TIME_ZONE_VERSION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DbSystem resource - Identifier. The name of the DbSystem resource in the
following format:
projects/{project}/locations/{region}/dbSystems/{db_system} This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument db_system on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument db_system on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  DB_SYSTEM
     ID of the dbSystem or fully qualified identifier for the dbSystem.

     To set the db_system attribute:
     + provide the argument db_system on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name for the System db. The name does not have to be unique within your project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--gcp-oracle-zone` | GCP_ORACLE_ZONE |  | The GCP Oracle zone where Oracle DbSystem is hosted. Example: us-east4-b-r2. If not specified, the system will pick a zone based on availability. |
| `--labels` | [LABELS,...] |  | The labels or tags associated with the DbSystem. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | For resources [db_system, odb-network, odb-subnet], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--odb-network` | ODB_NETWORK |  | For resources [odb-network, odb-subnet], provides fallback value for resource odb-network attribute. When the resource's full URI path is not provided, odb-network will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
Choose an available db-version in your location by running gcloud
oracle-database db-versions list --location=us-east4. Choose an available
db-system-initial-storage-size in your location by running gcloud
oracle-database db-system-initial-storage-sizes list --location=us-east4.
Choose an available shape in your location by running gcloud
oracle-database db-system-shapes list --location=us-east4. To create
DbSystem with id my-db-system in the location us-east4 with display-name my
db system, run:

    $ gcloud oracle-database db-systems create my-db-system \
        --location=us-east4 --display-name="my db system" \
        --properties-db-home-db-version=xx.0.0.0 \
        --properties-db-system-initial-storage-size=1000 \
        --properties-shape=VM.FOO
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/db-systems/create)

---
### `gcloud oracle-database db-systems delete`

Delete a DbSystem

Delete a DbSystem.

**Synopsis:**
```
gcloud oracle-database db-systems delete (DB_SYSTEM : --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DbSystem resource - The name of the DbSystem in the following format:
projects/{project}/locations/{location}/dbSystems/{db_system}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument db_system on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DB_SYSTEM
     ID of the dbSystem or fully qualified identifier for the dbSystem.

     To set the db_system attribute:
     + provide the argument db_system on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dbSystem resource.

     To set the location attribute:
     + provide the argument db_system on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete a DbSystem with id my-db-system in the location us-east4, run:

    $ gcloud oracle-database db-systems delete my-db-system \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/db-systems/delete)

---
### `gcloud oracle-database db-systems describe`

Get details of a DbSystem

Get details of a DbSystem.

**Synopsis:**
```
gcloud oracle-database db-systems describe
    (DB_SYSTEM : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DbSystem resource - The name of the DbSystem in the following format:
projects/{project}/locations/{location}/dbSystems/{db_system}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument db_system on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DB_SYSTEM
     ID of the dbSystem or fully qualified identifier for the dbSystem.

     To set the db_system attribute:
     + provide the argument db_system on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the dbSystem resource.

     To set the location attribute:
     + provide the argument db_system on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get a DbSystem with id my-db-system in the location us-east4, run:

    $ gcloud oracle-database db-systems describe my-db-system \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/db-systems/describe)

---
### `gcloud oracle-database db-systems list`

List all DbSystems

List all DbSystems.

**Synopsis:**
```
gcloud oracle-database db-systems list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DbSystems in the location us-east4 for a given DbSystem with id
my-db-system, run:

    $ gcloud oracle-database db-systems list --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/db-systems/list)

---
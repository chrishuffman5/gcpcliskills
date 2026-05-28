# gcloud oracle-database autonomous-databases

manage Autonomous Database resources

### `gcloud oracle-database autonomous-databases create`

Create a new AutonomousDatabase

Create a new AutonomousDatabase.

**Synopsis:**
```
gcloud oracle-database autonomous-databases create AUTONOMOUS_DATABASE
    [--admin-password=ADMIN_PASSWORD] [--async] [--cidr=CIDR]
    [--database=DATABASE] [--display-name=DISPLAY_NAME]
    [--labels=[LABELS,...]] [--location=LOCATION] [--network=NETWORK]
    [--odb-network=ODB_NETWORK] [--odb-subnet=ODB_SUBNET]
    [--request-id=REQUEST_ID]
    [[--properties-db-workload=PROPERTIES_DB_WORKLOAD
      --properties-license-type=PROPERTIES_LICENSE_TYPE
      : --properties-allowlisted-ips=[PROPERTIES_ALLOWLISTED_IPS,...]
      --properties-backup-retention-period-days=PROPERTIES_BACKUP_RETENTION_PERIOD_DAYS --properties-character-set=PROPERTIES_CHARACTER_SET --properties-compute-count=PROPERTIES_COMPUTE_COUNT --properties-cpu-core-count=PROPERTIES_CPU_CORE_COUNT --properties-customer-contacts=[email=EMAIL] --properties-data-storage-size-gb=PROPERTIES_DATA_STORAGE_SIZE_GB --properties-data-storage-size-tb=PROPERTIES_DATA_STORAGE_SIZE_TB --properties-db-edition=PROPERTIES_DB_EDITION --properties-db-version=PROPERTIES_DB_VERSION --properties-is-auto-scaling-enabled --properties-is-storage-auto-scaling-enabled --properties-maintenance-schedule-type=PROPERTIES_MAINTENANCE_SCHEDULE_TYPE --properties-mtls-connection-required --properties-n-character-set=PROPERTIES_N_CHARACTER_SET --properties-private-endpoint-ip=PROPERTIES_PRIVATE_ENDPOINT_IP --properties-private-endpoint-label=PROPERTIES_PRIVATE_ENDPOINT_LABEL --properties-secret-id=PROPERTIES_SECRET_ID --properties-vault-id=PROPERTIES_VAULT_ID --encryption-key-provider=ENCRYPTION_KEY_PROVIDER [--encryption-key-kms=ENCRYPTION_KEY_KMS : --key-ring=KEY_RING]]]
    [--source-config-automatic-backups-replication-enabled
      --source-config-autonomous-database=SOURCE_CONFIG_AUTONOMOUS_DATABASE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - Identifier. The name of the Autonomous
Database resource in the following format:
projects/{project}/locations/{region}/autonomousDatabases/{autonomous_database}
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-password` | ADMIN_PASSWORD |  | The password for the default ADMIN user. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cidr` | CIDR |  | The subnet CIDR range for the Autonomous Database. |
| `--database` | DATABASE |  | The name of the Autonomous Database. The database name must be unique in the project. The name must begin with a letter and can contain a maximum of 30 alphanumeric characters. |
| `--display-name` | DISPLAY_NAME |  | The display name for the Autonomous Database. The name does not have to be unique within your project. |
| `--labels` | [LABELS,...] |  | The labels or tags associated with the Autonomous Database. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | For resources [autonomous_database, encryption-key-kms, odb-network, odb-subnet, source-config-autonomous-database], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--odb-network` | ODB_NETWORK |  | _[+ provide the argument --network on the command line.]_ For resources [odb-network, odb-subnet], provides fallback value for resource odb-network attribute. When the resource's full URI path is not provided, odb-network will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | _[+ provide the argument --odb-subnet on the command line.]_ An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create AutonomousDatabase with id my-instance in the location us-east4
with display-name my instance, odb-network
projects/network-project/locations/us-east4/odbNetworks/my-odbnetwork,
odb-subnet
projects/network-project/locations/us-east4/odbNetworks/my-odbnetwork/odbSubnets/my-odbsubnet,
network projects/my-project/locations/global/networks/default, location
us-east4, database testadb, admin-password 123Abpassdord, cidr 12.2.0.0/24,
properties-compute-count 2, properties-db-version 19c,
properties-license-type LICENSE_INCLUDED, properties-db-workload DW. run:
To set the network configuration use one of the following options:

ODBNetwork based configuration(This is the recommended way):

    $ gcloud oracle-database autonomous-databases create my-instance \
        --location=us-east4 --display-name="my instance" \
        --location=us-east4 --database=testadb \
        --admin-password=123Abpassdord --properties-compute-count=2 \
        --properties-db-version=19c \
        --properties-license-type=LICENSE_INCLUDED \
        --properties-db-workload=DW \
        --odb-network=projects/network-project/locations/us-east4/\
    odbNetworks/my-odbnetwork \
        --odb-subnet=projects/network-project/locations/us-east4/\
    odbNetworks/my-odbnetwork/odbSubnets/my-odbsubnet

Network and CIDR based configuration:

    $ gcloud oracle-database autonomous-databases create my-instance \
        --location=us-east4 --display-name="my instance" \
        --network=projects/my-project/locations/global/networks/\
    default --cidr=12.2.0.0/24 --location=us-east4 --database=testadb \
        --admin-password=123Abpassdord --properties-compute-count=2 \
        --properties-db-version=19c \
        --properties-license-type=LICENSE_INCLUDED \
        --properties-db-workload=DW
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/create)

---
### `gcloud oracle-database autonomous-databases delete`

Delete an AutonomousDatabase

Delete an AutonomousDatabase.

**Synopsis:**
```
gcloud oracle-database autonomous-databases delete
    (AUTONOMOUS_DATABASE : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the resource in the following
format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete an AutonomousDatabase with id my-instance in the location
us-east4, run:

    $ gcloud oracle-database autonomous-databases delete my-instance \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/delete)

---
### `gcloud oracle-database autonomous-databases describe`

Get details of an AutonomousDatabase

Get details of an AutonomousDatabase.

**Synopsis:**
```
gcloud oracle-database autonomous-databases describe
    (AUTONOMOUS_DATABASE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get an AutonomousDatabase with id my-instance in the location us-east4,
run:

    $ gcloud oracle-database autonomous-databases describe my-instance \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/describe)

---
### `gcloud oracle-database autonomous-databases failover`

Failovers a standby AutonomousDatabase to a new primary

Failovers an AutonomousDatabase from a standby database to a new primary.

**Synopsis:**
```
gcloud oracle-database autonomous-databases failover AUTONOMOUS_DATABASE
    --peer-autonomous-database=PEER_AUTONOMOUS_DATABASE [--async]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-autonomous-database` | PEER_AUTONOMOUS_DATABASE |  | _[This must be specified.]_ ID of the autonomousDatabase or fully qualified identifier for the autonomousDatabase. To set the autonomous-database attribute: + provide the argument --peer-autonomous-database on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | For resources [autonomous_database, peer-autonomous-database], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |


**Examples:**
```bash
To failover an AutonomousDatabase with id my-instance in the location
us-east4 with primary database name as
'projects/project-id/locations/us-west3/autonomousDatabases/my-peer-instance'
run:

    $ gcloud oracle-database autonomous-databases failover my-instance \
        --location=us-east4 \
        --peer-autonomous-database=projects/project-id/locations/\
    us-west3/autonomousDatabases/my-peer-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/failover)

---
### `gcloud oracle-database autonomous-databases generate-wallet`

Generate wallet for an AutonomousDatabase

Generate wallet for an AutonomousDatabase, Content is base64 encoded zip
archive.

**Synopsis:**
```
gcloud oracle-database autonomous-databases generate-wallet
    (AUTONOMOUS_DATABASE : --location=LOCATION) --password=PASSWORD
    [--is-regional] [--type=TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--password` | PASSWORD |  | The password used to encrypt the keys inside the wallet. The password must be a minimum of 8 characters. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--is-regional` |  |  | True when requesting regional connection strings in PDB connect info, applicable to cross-region Data Guard only. |
| `--type` | one of: all Used to generate wallet for all databases in the region |  | The type of wallet generation for the Autonomous Database. The default value is SINGLE. TYPE must be one of: all Used to generate wallet for all databases in the region. single Used to generate wallet for a single database. |


**Examples:**
```bash
To generate wallet for an AutonomousDatabase with id my-instance with
password 123Abpassword, to encrypt the keys inside the wallet in the
location us-east4, run:

    $ gcloud oracle-database autonomous-databases generate-wallet \
        my-instance --location=us-east4 --password=123Abpassword
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/generate-wallet)

---
### `gcloud oracle-database autonomous-databases list`

List all AutonomousDatabases

List all AutonomousDatabases.

**Synopsis:**
```
gcloud oracle-database autonomous-databases list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all AutonomousDatabases in the location us-east4, run:

    $ gcloud oracle-database autonomous-databases list \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/list)

---
### `gcloud oracle-database autonomous-databases restart`

Restarts an AutonomousDatabase

Restarts an AutonomousDatabase which is in Running state.

**Synopsis:**
```
gcloud oracle-database autonomous-databases restart
    (AUTONOMOUS_DATABASE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restart an AutonomousDatabase with id my-instance in the location
us-east4, run:

    $ gcloud oracle-database autonomous-databases restart my-instance \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/restart)

---
### `gcloud oracle-database autonomous-databases restore`

Restore an AutonomousDatabase

Restore an AutonomousDatabase to the state at specified restore-time.

**Synopsis:**
```
gcloud oracle-database autonomous-databases restore
    (AUTONOMOUS_DATABASE : --location=LOCATION) --restore-time=RESTORE_TIME
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--restore-time` | RESTORE_TIME |  | The time and date to restore the database to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restore an AutonomousDatabase with id my-instance at restore-time
2024-05-01T00:00:00.000Z in the location us-east4 , The restore-time is the
'endTime' property of a backup. run:

    $ gcloud oracle-database autonomous-databases restore my-instance \
        --location=us-east4 --restore-time=2024-05-01T00:00:00.000Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/restore)

---
### `gcloud oracle-database autonomous-databases start`

Starts an AutonomousDatabase

Starts an AutonomousDatabase which is in Stopped state.

**Synopsis:**
```
gcloud oracle-database autonomous-databases start
    (AUTONOMOUS_DATABASE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To start an AutonomousDatabase with id my-instance in the location
us-east4, run:

    $ gcloud oracle-database autonomous-databases start my-instance \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/start)

---
### `gcloud oracle-database autonomous-databases stop`

Stops an AutonomousDatabase

Stops an AutonomousDatabase which is in Running state.

**Synopsis:**
```
gcloud oracle-database autonomous-databases stop
    (AUTONOMOUS_DATABASE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the autonomousDatabase resource.

     To set the location attribute:
     + provide the argument autonomous_database on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To stop an AutonomousDatabase with id my-instance in the location us-east4,
run:

    $ gcloud oracle-database autonomous-databases stop my-instance \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/stop)

---
### `gcloud oracle-database autonomous-databases switchover`

Switchovers an AutonomousDatabase to a new primary

Switchovers an AutonomousDatabase from a standby database to a new primary.

**Synopsis:**
```
gcloud oracle-database autonomous-databases switchover AUTONOMOUS_DATABASE
    --peer-autonomous-database=PEER_AUTONOMOUS_DATABASE [--async]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - The name of the Autonomous Database in the
following format:
projects/{project}/locations/{location}/autonomousDatabases/{autonomous_database}.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-autonomous-database` | PEER_AUTONOMOUS_DATABASE |  | _[This must be specified.]_ ID of the autonomousDatabase or fully qualified identifier for the autonomousDatabase. To set the autonomous-database attribute: + provide the argument --peer-autonomous-database on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | For resources [autonomous_database, peer-autonomous-database], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |


**Examples:**
```bash
To switchover an AutonomousDatabase with id my-instance in the location
us-east4 with primary database name as
'projects/project-id/locations/us-west3/autonomousDatabases/my-instance'
run:

    $ gcloud oracle-database autonomous-databases switchover \
        my-instance --location=us-east4 \
        --peer-autonomous-database=projects/project-id/locations/\
    us-west3/autonomousDatabases/my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/switchover)

---
### `gcloud oracle-database autonomous-databases update`

Update an AutonomousDatabase

Update an AutonomousDatabase.

**Synopsis:**
```
gcloud oracle-database autonomous-databases update AUTONOMOUS_DATABASE
    [--admin-password=ADMIN_PASSWORD] [--async] [--cidr=CIDR]
    [--clear-odb-network] [--database=DATABASE]
    [--display-name=DISPLAY_NAME] [--location=LOCATION]
    [--odb-network=ODB_NETWORK] [--request-id=REQUEST_ID]
    [--clear-network | --network=NETWORK]
    [--clear-odb-subnet | --odb-subnet=ODB_SUBNET]
    [--clear-properties
      --properties-backup-retention-period-days=PROPERTIES_BACKUP_RETENTION_PERIOD_DAYS --properties-character-set=PROPERTIES_CHARACTER_SET --properties-compute-count=PROPERTIES_COMPUTE_COUNT --properties-cpu-core-count=PROPERTIES_CPU_CORE_COUNT --properties-data-storage-size-gb=PROPERTIES_DATA_STORAGE_SIZE_GB --properties-data-storage-size-tb=PROPERTIES_DATA_STORAGE_SIZE_TB --properties-db-edition=PROPERTIES_DB_EDITION --properties-db-version=PROPERTIES_DB_VERSION --properties-db-workload=PROPERTIES_DB_WORKLOAD --[no-]properties-is-auto-scaling-enabled --[no-]properties-is-storage-auto-scaling-enabled --properties-license-type=PROPERTIES_LICENSE_TYPE --properties-maintenance-schedule-type=PROPERTIES_MAINTENANCE_SCHEDULE_TYPE --[no-]properties-mtls-connection-required --properties-n-character-set=PROPERTIES_N_CHARACTER_SET --properties-private-endpoint-ip=PROPERTIES_PRIVATE_ENDPOINT_IP --properties-private-endpoint-label=PROPERTIES_PRIVATE_ENDPOINT_LABEL --properties-secret-id=PROPERTIES_SECRET_ID --properties-vault-id=PROPERTIES_VAULT_ID --encryption-key-provider=ENCRYPTION_KEY_PROVIDER --key-ring=KEY_RING --clear-encryption-key-kms | --encryption-key-kms=ENCRYPTION_KEY_KMS --properties-allowlisted-ips=[PROPERTIES_ALLOWLISTED_IPS,
      ...]
      | --add-properties-allowlisted-ips=[ADD_PROPERTIES_ALLOWLISTED_IPS,
      ...] --clear-properties-allowlisted-ips
      | --remove-properties-allowlisted-ips=[REMOVE_PROPERTIES_ALLOWLISTED_IPS,
      ...] --properties-customer-contacts=[email=EMAIL]
      | --add-properties-customer-contacts=[email=EMAIL]
      --clear-properties-customer-contacts
      | --remove-properties-customer-contacts=[email=EMAIL]]
    [--clear-source-config
      --[no-]source-config-automatic-backups-replication-enabled
      --clear-source-config-autonomous-database
      | --source-config-autonomous-database=SOURCE_CONFIG_AUTONOMOUS_DATABASE]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AutonomousDatabase resource - Identifier. The name of the Autonomous
Database resource in the following format:
projects/{project}/locations/{region}/autonomousDatabases/{autonomous_database}
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument autonomous_database on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  AUTONOMOUS_DATABASE
     ID of the autonomousDatabase or fully qualified identifier for the
     autonomousDatabase.

     To set the autonomous_database attribute:
     + provide the argument autonomous_database on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-password` | ADMIN_PASSWORD |  | The password for the default ADMIN user. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cidr` | CIDR |  | The subnet CIDR range for the Autonomous Database. |
| `--database` | DATABASE |  | _[Clear odb_network value and set to null.]_ The name of the Autonomous Database. The database name must be unique in the project. The name must begin with a letter and can contain a maximum of 30 alphanumeric characters. |
| `--display-name` | DISPLAY_NAME |  | _[Clear odb_network value and set to null.]_ The display name for the Autonomous Database. The name does not have to be unique within your project. |
| `--location` | LOCATION |  | _[Clear odb_network value and set to null.]_ For resources [autonomous_database, encryption-key-kms, odb-network, odb-subnet, source-config-autonomous-database], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--odb-network` | ODB_NETWORK |  | _[Clear odb_network value and set to null.]_ For resources [odb-network, odb-subnet], provides fallback value for resource odb-network attribute. When the resource's full URI path is not provided, odb-network will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | _[Clear odb_network value and set to null.]_ An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To Update the encryption for a given AutonomousDatabase with id
my-autonomous-database with custom KMS encryption key
projects/project-id/locations/us-east4/keyRings/keyring/cryptoKeys/key,
run:

    $ gcloud oracle-database autonomous-databases update \
        my-autonomous-database --location=us-east4 \
        --properties-encryption-key-provider=GOOGLE_MANAGED \
        --properties-encryption-key-kms-key=projects/project-id/\
    locations/us-east4/keyRings/keyring/cryptoKeys/key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/autonomous-databases/update)

---
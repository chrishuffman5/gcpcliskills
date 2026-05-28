# gcloud database-migration connection-profiles

manage Database Migration Service connection profiles

### `gcloud database-migration connection-profiles delete`

Delete a Database Migration Service connection profile

Deletes a connection profile. A connection profile can only be deleted if
it is not in use by any active migration jobs.

**Synopsis:**
```
gcloud database-migration connection-profiles delete
    (CONNECTION_PROFILE : --region=REGION) [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - Connection profile resource - Connection
profile to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Cloud SQL replica database is also deleted (only for Cloud SQL connection profiles). |


**Examples:**
```bash
To delete a connection profile:

    $ gcloud database-migration connection-profiles delete \
      CONNECTION_PROFILE --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/delete)

---
### `gcloud database-migration connection-profiles describe`

Show details about a Database Migration Service connection profile

Show details about a connection profile.

**Synopsis:**
```
gcloud database-migration connection-profiles describe
    (CONNECTION_PROFILE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile you want to get the
details of. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To show details about a connection profile, run:

    $ gcloud database-migration connection-profiles describe \
        my-connection-profile --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/describe)

---
### `gcloud database-migration connection-profiles list`

List Database Migration Service connection profiles

List connection profiles.

**Synopsis:**
```
gcloud database-migration connection-profiles list [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all connection profiles in a project and region 'us-central1', run:

    $ gcloud database-migration connection-profiles list \
      --region=us-central1

To filter connection profiles with the given state:

    $ gcloud database-migration connection-profiles list \
      --filter="state=READY"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/list)

---
### `gcloud database-migration connection-profiles test`

Test a Database Migration Service connection profile

Validates a Database Migration Service connection profile.

**Synopsis:**
```
gcloud database-migration connection-profiles test
    (CONNECTION_PROFILE : --region=REGION) [--no-async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to test. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |


**Examples:**
```bash
To test a connection profile:

    $ gcloud database-migration connection-profiles test my-profile \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/test)

---
### `gcloud database-migration connection-profiles update`

Update a Database Migration Service connection profile

Update a Database Migration Service connection profile.
  o Draft connection profile: the user can update all flags available in
    connection-profiles create command.
  o Existing connection profile: the user can update a limited list of
    flags, see connection-profiles update Synopsis.
  o If a migration job is using the connection profile, then updates to
    fields host, port, username, and password will propagate to the
    destination instance.

**Synopsis:**
```
gcloud database-migration connection-profiles update
    (CONNECTION_PROFILE : --region=REGION)
    [--alloydb-cluster=ALLOYDB_CLUSTER] [--ca-certificate=CA_CERTIFICATE]
    [--client-certificate=CLIENT_CERTIFICATE]
    [--cloudsql-instance=CLOUDSQL_INSTANCE]
    [--cloudsql-project-id=CLOUDSQL_PROJECT_ID] [--database=DATABASE]
    [--database-service=DATABASE_SERVICE] [--display-name=DISPLAY_NAME]
    [--host=HOST] [--port=PORT] [--private-key=PRIVATE_KEY]
    [--ssl-type=SSL_TYPE] [--update-labels=[KEY=VALUE,...]]
    [--username=USERNAME] [--clear-labels | --remove-labels=[KEY,...]]
    [--gcs-bucket=GCS_BUCKET : --gcs-prefix=GCS_PREFIX]
    [--password=PASSWORD | --prompt-for-password] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--alloydb-cluster` | ALLOYDB_CLUSTER |  | If the destination is an AlloyDB cluster, use this field to provide the AlloyDB cluster ID. |
| `--ca-certificate` | CA_CERTIFICATE |  | x509 PEM-encoded certificate of the CA that signed the database server's certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service will use this certificate to verify it's connecting to the correct host. Database Migration Service encrypts the value when storing it. |
| `--client-certificate` | CLIENT_CERTIFICATE |  | x509 PEM-encoded certificate that will be used by the replica to authenticate against the database server. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service encrypts the value when storing it. |
| `--cloudsql-instance` | CLOUDSQL_INSTANCE |  | If the source or destination is a Cloud SQL database, then use this field to provide the respective Cloud SQL instance ID. |
| `--cloudsql-project-id` | CLOUDSQL_PROJECT_ID |  | The project id of the Cloud SQL instance. Only needed if the Cloud SQL instance is in a different project than the connection profile. This is only supported for source connection profiles for SQL Server. |
| `--database` | DATABASE |  | The name of the specific database within the host. |
| `--database-service` | DATABASE_SERVICE |  | database service for the oracle connection profile. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--host` | HOST |  | IP or hostname of the database. When --psc-service-attachment is also specified, this field value should be: 1. For Cloud SQL PSC enabled instance - the dns_name field (e.g <uid>.<region>.sql.goog.). 2. For Cloud SQL PSA instance (vpc peering) - the private ip of the instance. 3. For AlloyDB PSC enabled cluster - the dns_name field of the primary instance (e.g <uid>.<region>.alloydb-psc.goog.). 4. For AlloyDB PSA cluster - the private ip of the primary instance. |
| `--port` | PORT |  | Network port of the database. |
| `--private-key` | PRIVATE_KEY |  | Unencrypted PKCS#1 or PKCS#8 PEM-encoded private key associated with the Client Certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service encrypts the value when storing it. |
| `--ssl-type` | one of: SERVER_ONLY, SERVER_CLIENT, REQUIRED, NONE |  | The type of SSL configuration. SSL_TYPE must be one of: SERVER_ONLY, SERVER_CLIENT, REQUIRED, NONE. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--username` | USERNAME |  | Username that Database Migration Service uses to connect to the database. Database Migration Service encrypts the value when storing it. |
| `--gcs-bucket` | GCS_BUCKET |  | _[--update-labels is applied first.]_ Cloud Storage bucket for the source SQL Server connection profile where the backups are stored. This flag is used only for SQL Server to Cloud SQL migrations. |
| `--gcs-prefix` | GCS_PREFIX |  | _[--update-labels is applied first.]_ Cloud Storage prefix path within the bucket for the source SQL Server connection profile where the backups are stored. This flag is used only for SQL Server to Cloud SQL migrations. |


**Examples:**
```bash
To update the username of a connection profile:

    $ gcloud database-migration connection-profiles update my-profile \
      --region=us-central1 --username=new-user
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/update)

---

## `gcloud database-migration connection-profiles create` — create Database Migration Service connection profiles
### `gcloud database-migration connection-profiles create alloydb`

Create a Database Migration Service connection profile for AlloyDB

Create a Database Migration Service destination connection profile for
AlloyDB. This will create an AlloyDB cluster and primary instance.

**Synopsis:**
```
gcloud database-migration connection-profiles create alloydb
    (CONNECTION_PROFILE : --region=REGION) --cpu-count=CPU_COUNT
    --password=PASSWORD --primary-id=PRIMARY_ID [--no-async]
    [--authorized-network-cidr-ranges=[NETWORK,...]]
    [--cluster-labels=[KEY=VALUE,...]] [--database-flags=[FLAG=VALUE,...]]
    [--database-version=DATABASE_VERSION] [--display-name=DISPLAY_NAME]
    [--enable-outbound-public-ip] [--enable-public-ip]
    [--labels=[KEY=VALUE,...]] [--network=NETWORK]
    [--primary-labels=[KEY=VALUE,...]] [--role=ROLE]
    [--kms-key=KMS_KEY
      : --kms-keyring=KMS_KEYRING --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cpu-count` | one of: 2, 4, 8, 16, 32, 64 |  | Whole number value indicating how many vCPUs the machine should contain. Each vCPU count corresponds to a N2 high-mem machine: (https://cloud.google.com/compute/docs/general-purpose-machines#n2_machines). CPU_COUNT must be one of: 2, 4, 8, 16, 32, 64. |
| `--password` | PASSWORD |  | Initial password for the 'postgres' user. |
| `--primary-id` | PRIMARY_ID |  | The ID of the primary instance for this AlloyDB cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--authorized-network-cidr-ranges` | [NETWORK,...] |  | Comma-separated list of CIDR ranges that can connect to the AlloyDB instance. |
| `--cluster-labels` | [KEY=VALUE,...] |  | The resource labels for an AlloyDB cluster. An object containing a list of "key": "value" pairs. |
| `--database-flags` | [FLAG=VALUE,...] |  | Comma-separated list of database flags to set on the AlloyDB primary instance. Use an equals sign to separate the flag name and value. Flags without values, like skip_grant_tables, can be written out without a value, e.g., skip_grant_tables=. Use on/off values for booleans. View AlloyDB's documentation for allowed flags (e.g., --database-flags max_allowed_packet=55555,skip_grant_tables=,log_output=1). |
| `--database-version` | one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17 |  | Database engine major version. DATABASE_VERSION must be one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--enable-outbound-public-ip` |  |  | If true, Enables an outbound public IP address to support a database server sending requests out into the internet. |
| `--enable-public-ip` |  |  | If true, the AlloyDB instance will be accessible via public IP. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--network` | NETWORK |  | The VPC network from which the AlloyDB instance is accessible via private IP. For example, projects/myProject/global/networks/default. This setting cannot be updated after it is set. |
| `--primary-labels` | [KEY=VALUE,...] |  | The resource labels for an AlloyDB primary instance. An object containing a list of "key": "value" pairs. |
| `--role` | one of: SOURCE, DESTINATION |  | The role of the connection profile. ROLE must be one of: SOURCE, DESTINATION. |


**Examples:**
```bash
To create a connection profile for AlloyDB:

    $ gcloud database-migration connection-profiles create alloydb \
      my-profile --region=us-central1 --password=my_password \
      --primary-id=my-primary --cpu-count=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/create/alloydb)

---
### `gcloud database-migration connection-profiles create cloudsql`

Create a Database Migration Service connection profile for Cloud SQL

Create a Database Migration Service destination connection profile for
Cloud SQL. This will create a Cloud SQL replica. Used for PostgreSQL and
MySQL migrations.

**Synopsis:**
```
gcloud database-migration connection-profiles create cloudsql
    (CONNECTION_PROFILE : --region=REGION) --source-id=SOURCE_ID
    --tier=TIER
    (--database-version=DATABASE_VERSION
      | --database-version-name=DATABASE_VERSION_NAME)
    [--activation-policy=ACTIVATION_POLICY]
    [--allocated-ip-range=ALLOCATED_IP_RANGE] [--no-async]
    [--authorized-networks=NETWORK,[NETWORK,...]]
    [--no-auto-storage-increase] [--availability-type=AVAILABILITY_TYPE]
    [--data-disk-size=DATA_DISK_SIZE] [--data-disk-type=DATA_DISK_TYPE]
    [--database-flags=[FLAG=VALUE,...]] [--display-name=DISPLAY_NAME]
    [--edition=EDITION] [--no-enable-ip-v4] [--labels=[KEY=VALUE,...]]
    [--private-network=PRIVATE_NETWORK] [--provider=PROVIDER]
    [--require-ssl] [--role=ROLE] [--root-password=ROOT_PASSWORD]
    [--secondary-zone=SECONDARY_ZONE]
    [--storage-auto-resize-limit=STORAGE_AUTO_RESIZE_LIMIT]
    [--user-labels=[KEY=VALUE,...]] [--zone=ZONE]
    [--cmek-key=CMEK_KEY
      : --cmek-keyring=CMEK_KEYRING --cmek-project=CMEK_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-id` | SOURCE_ID |  | _[This must be specified.]_ ID of the connection_profile or fully qualified identifier for the connection_profile. To set the connection_profile attribute: + provide the argument --source-id on the command line. |
| `--tier` | TIER |  | _[This must be specified.]_ Tier (or machine type) for this instance, for example: db-n1-standard-1 (MySQL instances) or db-custom-1-3840 (PostgreSQL instances). For more information, see Cloud SQL Instance Settings (https://cloud.google.com/sql/docs/mysql/instance-settings). |
| `--database-version` | one of: MYSQL_5_7, MYSQL_5_6, MYSQL_8_0, MYSQL_8_0_18, MYSQL_8_0_26, MYSQL_8_0_27, MYSQL_8_0_28, MYSQL_8_0_30, MYSQL_8_0_31, MYSQL_8_0_32, MYSQL_8_0_33, MYSQL_8_0_34, MYSQL_8_0_35, MYSQL_8_0_36, MYSQL_8_0_37, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16 |  | _[Exactly one of these must be specified:]_ Database engine type and version. DATABASE_VERSION must be one of: MYSQL_5_7, MYSQL_5_6, MYSQL_8_0, MYSQL_8_0_18, MYSQL_8_0_26, MYSQL_8_0_27, MYSQL_8_0_28, MYSQL_8_0_30, MYSQL_8_0_31, MYSQL_8_0_32, MYSQL_8_0_33, MYSQL_8_0_34, MYSQL_8_0_35, MYSQL_8_0_36, MYSQL_8_0_37, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16. |
| `--database-version-name` | DATABASE_VERSION_NAME |  | _[Exactly one of these must be specified:]_ Database version name (e.g. POSTGRES_15) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activation-policy` | one of: ALWAYS, NEVER |  | Activation policy specifies when the instance is activated; it is applicable only when the instance state is 'RUNNABLE'. Valid values: ALWAYS: The instance is on, and remains so even in the absence of connection requests. NEVER: The instance is off; it is not activated, even if a connection request arrives. ACTIVATION_POLICY must be one of: ALWAYS, NEVER. |
| `--allocated-ip-range` | ALLOCATED_IP_RANGE |  | The name of the allocated IP range for the private IP Cloud SQL instance. This name refers to an already allocated IP range. If set, the instance IP will be created in the allocated range. |
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--authorized-networks` | NETWORK,[NETWORK,...] |  | List of external networks that are allowed to connect to the instance. Specify values in CIDR notation, also known as 'slash' notation (e.g.192.168.100.0/24). |
| `--auto-storage-increase` |  |  | If you enable this setting, Cloud SQL checks your available storage every 30 seconds. If the available storage falls below a threshold size, Cloud SQL automatically adds additional storage capacity. If the available storage repeatedly falls below the threshold size, Cloud SQL continues to add storage until it reaches the maximum of 64 TB. Default: ON. Enabled by default, use --no-auto-storage-increase to disable. |
| `--availability-type` | one of: REGIONAL, ZONAL |  | Cloud SQL availability type. AVAILABILITY_TYPE must be one of: REGIONAL, ZONAL. |
| `--data-disk-size` | DATA_DISK_SIZE |  | Storage capacity available to the database, in GB. The minimum (and default) size is 10GB. |
| `--data-disk-type` | one of: PD_SSD, PD_HDD |  | Type of storage. DATA_DISK_TYPE must be one of: PD_SSD, PD_HDD. |
| `--database-flags` | [FLAG=VALUE,...] |  | Comma-separated list of database flags to set on the instance. Use an equals sign to separate the flag name and value. Flags without values, like skip_grant_tables, can be written out without a value, e.g., skip_grant_tables=. Use on/off values for booleans. View the Instance Resource API for allowed flags. (e.g., --database-flags max_allowed_packet=55555 skip_grant_tables=,log_output=1). |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--edition` | one of: enterprise Enterprise is the standard option for smaller instances |  | Specifies edition. EDITION must be one of: enterprise Enterprise is the standard option for smaller instances. enterprise-plus Enterprise plus option recommended for cpu-intensive workloads. Offers access to premium features and capabilities. |
| `--enable-ip-v4` |  |  | Whether the instance should be assigned an IPv4 address or not. Enabled by default, use --no-enable-ip-v4 to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--private-network` | PRIVATE_NETWORK |  | Resource link for the VPC network from which the Cloud SQL instance is accessible for private IP. For example, /projects/myProject/global/networks/default. This setting can be updated, but it cannot be removed after it is set. |
| `--provider` | one of: RDS, CLOUDSQL |  | Database provider, for managed databases. PROVIDER must be one of: RDS, CLOUDSQL. |
| `--require-ssl` |  |  | Whether SSL connections over IP should be enforced or not. |
| `--role` | one of: SOURCE, DESTINATION |  | The role of the connection profile. ROLE must be one of: SOURCE, DESTINATION. |
| `--root-password` | ROOT_PASSWORD |  | Root Cloud SQL user's password. |
| `--secondary-zone` | SECONDARY_ZONE |  | Google Cloud Platform zone where the failover Cloud SQL database instance is located. Used when the Cloud SQL database availability type is REGIONAL (i.e. multiple zones / highly available). |
| `--storage-auto-resize-limit` | STORAGE_AUTO_RESIZE_LIMIT |  | Maximum size to which storage capacity can be automatically increased. The default value is 0, which specifies that there is no limit. |
| `--user-labels` | [KEY=VALUE,...] |  | The resource labels for a Cloud SQL instance to use to annotate any related underlying resources such as Compute Engine VMs. An object containing a list of "key": "value" pairs. |
| `--zone` | ZONE |  | Google Cloud Platform zone where your Cloud SQL database instance is located. |


**Examples:**
```bash
To create a connection profile for Cloud SQL with database version MySQL
5.6:

    $ gcloud database-migration connection-profiles create cloudsql \
      my-profile --region=us-central1 --database-version=MYSQL_5_6 \
      --source-id=cp1 --tier=db-n1-standard-1

To create a connection profile for Cloud SQL and a Cloud SQL replica with
database version PostgreSQL 10:

    $ gcloud database-migration connection-profiles create cloudsql \
      my-profile --region=us-central1 --database-version=POSTGRES_10 \
      --source-id=cp1 --tier=db-custom-1-3840 --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/create/cloudsql)

---
### `gcloud database-migration connection-profiles create mysql`

Create a Database Migration Service connection profile for MySQL

Create a Database Migration Service connection profile for MySQL.

**Synopsis:**
```
gcloud database-migration connection-profiles create mysql
    (CONNECTION_PROFILE : --region=REGION) [--no-async]
    [--cloudsql-instance=CLOUDSQL_INSTANCE] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--provider=PROVIDER] [--role=ROLE]
    [--ca-certificate=CA_CERTIFICATE : --ssl-type=SSL_TYPE
      --client-certificate=CLIENT_CERTIFICATE --private-key=PRIVATE_KEY]
    [--host=HOST --port=PORT --username=USERNAME : --password=PASSWORD
      | --prompt-for-password] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--cloudsql-instance` | CLOUDSQL_INSTANCE |  | If the source or destination is a Cloud SQL database, then use this field to provide the respective Cloud SQL instance ID. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--provider` | one of: RDS, CLOUDSQL |  | Database provider, for managed databases. PROVIDER must be one of: RDS, CLOUDSQL. |
| `--role` | one of: SOURCE, DESTINATION |  | The role of the connection profile. ROLE must be one of: SOURCE, DESTINATION. |
| `--ca-certificate` | CA_CERTIFICATE |  | x509 PEM-encoded certificate of the CA that signed the database server's certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service will use this certificate to verify it's connecting to the correct host. Database Migration Service encrypts the value when storing it. |
| `--ssl-type` | one of: SERVER_ONLY, SERVER_CLIENT, REQUIRED, NONE |  | The type of SSL configuration. SSL_TYPE must be one of: SERVER_ONLY, SERVER_CLIENT, REQUIRED, NONE. |
| `--client-certificate` | CLIENT_CERTIFICATE |  | x509 PEM-encoded certificate that will be used by the replica to authenticate against the database server. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service encrypts the value when storing it. |
| `--private-key` | PRIVATE_KEY |  | Unencrypted PKCS#1 or PKCS#8 PEM-encoded private key associated with the Client Certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service encrypts the value when storing it. |
| `--host` | HOST |  | IP or hostname of the database. When --psc-service-attachment is also specified, this field value should be: 1. For Cloud SQL PSC enabled instance - the dns_name field (e.g <uid>.<region>.sql.goog.). 2. For Cloud SQL PSA instance (vpc peering) - the private ip of the instance. 3. For AlloyDB PSC enabled cluster - the dns_name field of the primary instance (e.g <uid>.<region>.alloydb-psc.goog.). 4. For AlloyDB PSA cluster - the private ip of the primary instance. |
| `--port` | PORT |  | Network port of the database. |
| `--username` | USERNAME |  | Username that Database Migration Service uses to connect to the database. Database Migration Service encrypts the value when storing it. |


**Examples:**
```bash
To create a connection profile for MySQL:

    $ gcloud database-migration connection-profiles create mysql \
      my-profile --region=us-central1 --password=123456 \
      --username=my-user --host=1.2.3.4 --port=3306

If the source is a Cloud SQL database, run:

    $ gcloud database-migration connection-profiles create mysql \
      my-profile --region=us-central1 --password=123456 \
      --username=my-user --host=1.2.3.4 --port=3306 \
      --cloudsql-instance=my-instance --provider=CLOUDSQL
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/create/mysql)

---
### `gcloud database-migration connection-profiles create oracle`

Create a Database Migration Service connection profile for Oracle

Create a Database Migration Service connection profile for Oracle.

**Synopsis:**
```
gcloud database-migration connection-profiles create oracle
    (CONNECTION_PROFILE : --region=REGION)
    --database-service=DATABASE_SERVICE --host=HOST --port=PORT
    --username=USERNAME (--password=PASSWORD | --prompt-for-password)
    [--no-async] [--ca-certificate=CA_CERTIFICATE]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]] [--role=ROLE]
    [--private-connection=PRIVATE_CONNECTION | --static-ip-connectivity
      | [--forward-ssh-hostname=FORWARD_SSH_HOSTNAME
      --forward-ssh-username=FORWARD_SSH_USERNAME
      (--forward-ssh-password=FORWARD_SSH_PASSWORD
      | --forward-ssh-private-key=FORWARD_SSH_PRIVATE_KEY)
      : --forward-ssh-port=FORWARD_SSH_PORT; default=22]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-service` | DATABASE_SERVICE |  | database service for the oracle connection profile. |
| `--host` | HOST |  | IP or hostname of the database. When --psc-service-attachment is also specified, this field value should be: 1. For Cloud SQL PSC enabled instance - the dns_name field (e.g <uid>.<region>.sql.goog.). 2. For Cloud SQL PSA instance (vpc peering) - the private ip of the instance. 3. For AlloyDB PSC enabled cluster - the dns_name field of the primary instance (e.g <uid>.<region>.alloydb-psc.goog.). 4. For AlloyDB PSA cluster - the private ip of the primary instance. |
| `--port` | PORT |  | Network port of the database. |
| `--username` | USERNAME |  | Username that Database Migration Service uses to connect to the database. Database Migration Service encrypts the value when storing it. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--ca-certificate` | CA_CERTIFICATE |  | x509 PEM-encoded certificate of the CA that signed the database server's certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service will use this certificate to verify it's connecting to the correct host. Database Migration Service encrypts the value when storing it. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--role` | one of: SOURCE, DESTINATION |  | The role of the connection profile. ROLE must be one of: SOURCE, DESTINATION. |


**Examples:**
```bash
To create a connection profile my-profile for Oracle:

    $ gcloud database-migration connection-profiles create oracle \
      my-profile --region=us-central1 --password=123456 \
      --username=my-user --host=1.2.3.4 --port=5432
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/create/oracle)

---
### `gcloud database-migration connection-profiles create postgresql`

Create a Database Migration Service connection profile for PostgreSQL

Create a Database Migration Service connection profile for PostgreSQL.

**Synopsis:**
```
gcloud database-migration connection-profiles create postgresql
    (CONNECTION_PROFILE : --region=REGION)
    [--alloydb-cluster=ALLOYDB_CLUSTER] [--no-async]
    [--cloudsql-instance=CLOUDSQL_INSTANCE] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--role=ROLE]
    [--ca-certificate=CA_CERTIFICATE : --ssl-type=SSL_TYPE
      --client-certificate=CLIENT_CERTIFICATE --private-key=PRIVATE_KEY]
    [--host=HOST --port=PORT
      : --database=DATABASE --username=USERNAME (--password=PASSWORD
      | --prompt-for-password)]
    [--psc-service-attachment=PSC_SERVICE_ATTACHMENT
      | --static-ip-connectivity] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--alloydb-cluster` | ALLOYDB_CLUSTER |  | If the destination is an AlloyDB cluster, use this field to provide the AlloyDB cluster ID. |
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--cloudsql-instance` | CLOUDSQL_INSTANCE |  | If the source or destination is a Cloud SQL database, then use this field to provide the respective Cloud SQL instance ID. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--role` | one of: SOURCE, DESTINATION |  | The role of the connection profile. ROLE must be one of: SOURCE, DESTINATION. |
| `--ca-certificate` | CA_CERTIFICATE |  | x509 PEM-encoded certificate of the CA that signed the database server's certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service will use this certificate to verify it's connecting to the correct host. Database Migration Service encrypts the value when storing it. |
| `--ssl-type` | one of: SERVER_ONLY, SERVER_CLIENT, REQUIRED, NONE |  | The type of SSL configuration. SSL_TYPE must be one of: SERVER_ONLY, SERVER_CLIENT, REQUIRED, NONE. |
| `--client-certificate` | CLIENT_CERTIFICATE |  | x509 PEM-encoded certificate that will be used by the replica to authenticate against the database server. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service encrypts the value when storing it. |
| `--private-key` | PRIVATE_KEY |  | Unencrypted PKCS#1 or PKCS#8 PEM-encoded private key associated with the Client Certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service encrypts the value when storing it. |
| `--host` | HOST |  | IP or hostname of the database. When --psc-service-attachment is also specified, this field value should be: 1. For Cloud SQL PSC enabled instance - the dns_name field (e.g <uid>.<region>.sql.goog.). 2. For Cloud SQL PSA instance (vpc peering) - the private ip of the instance. 3. For AlloyDB PSC enabled cluster - the dns_name field of the primary instance (e.g <uid>.<region>.alloydb-psc.goog.). 4. For AlloyDB PSA cluster - the private ip of the primary instance. |
| `--port` | PORT |  | Network port of the database. |
| `--database` | DATABASE |  | The name of the specific database within the host. |


**Examples:**
```bash
To create a connection profile my-profile for PostgreSQL:

    $ gcloud database-migration connection-profiles create postgresql \
      my-profile --region=us-central1 --password=123456 \
      --username=my-user --host=1.2.3.4 --port=5432

If the source is a Cloud SQL database, run:

    $ gcloud database-migration connection-profiles create postgresql \
      my-profile --region=us-central1 --password=123456 \
      --username=my-user --host=1.2.3.4 --port=5432 \
      --cloudsql-instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/create/postgresql)

---
### `gcloud database-migration connection-profiles create sqlserver`

Create a Database Migration Service connection profile for SQL Server

Create a Database Migration Service connection profile for SQL Server.

**Synopsis:**
```
gcloud database-migration connection-profiles create sqlserver
    (CONNECTION_PROFILE : --region=REGION) [--no-async]
    [--database=DATABASE] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--role=ROLE] [--ssl-flags=[FLAG=VALUE,...]]
    [--ca-certificate=CA_CERTIFICATE --ssl-type=SSL_TYPE]
    [[--gcs-bucket=GCS_BUCKET
      : --gcs-prefix=GCS_PREFIX --provider=PROVIDER]
      | --host=HOST --port=PORT]
    [--private-connection=PRIVATE_CONNECTION | --static-ip-connectivity
      | [--forward-ssh-hostname=FORWARD_SSH_HOSTNAME
      --forward-ssh-username=FORWARD_SSH_USERNAME
      (--forward-ssh-password=FORWARD_SSH_PASSWORD
      | --forward-ssh-private-key=FORWARD_SSH_PRIVATE_KEY)
      : --forward-ssh-port=FORWARD_SSH_PORT; default=22]]
    [--username=USERNAME (--password=PASSWORD | --prompt-for-password)
      : --cloudsql-instance=CLOUDSQL_INSTANCE
      --cloudsql-project-id=CLOUDSQL_PROJECT_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection profile resource - The connection profile to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument connection_profile on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION_PROFILE
     ID of the connection_profile or fully qualified identifier for the
     connection_profile.

     To set the connection_profile attribute:
     + provide the argument connection_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the connection_profile.

     To set the region attribute:
     + provide the argument connection_profile on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--database` | DATABASE |  | The name of the specific database within the host. |
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the connection profile. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--role` | one of: SOURCE, DESTINATION |  | The role of the connection profile. ROLE must be one of: SOURCE, DESTINATION. |
| `--ssl-flags` | [FLAG=VALUE,...] |  | Comma-separated list of SSL flags used for establishing SSL connection to the database. Use an equals sign to separate the flag name and value. Example: --ssl-flags ssl_mode=enable,server_certificate_hostname=server.com. |
| `--ca-certificate` | CA_CERTIFICATE |  | x509 PEM-encoded certificate of the CA that signed the database server's certificate. The value for this flag needs to be the content of the certificate file, not the path to the file. For example, on a Linux machine you can use command substitution: <code>--ca-certificate=$(</path/to/certificate_file.pem)</code>. Database Migration Service will use this certificate to verify it's connecting to the correct host. Database Migration Service encrypts the value when storing it. |
| `--ssl-type` | one of: SERVER_ONLY, REQUIRED, NONE |  | The type of SSL configuration. SSL_TYPE must be one of: SERVER_ONLY, REQUIRED, NONE. |
| `--username` | USERNAME |  | _[SSH private key..]_ Username that Database Migration Service uses to connect to the database for metrics and observability. We highly recommend that you use the sqlserver user for this. Database Migration Service encrypts the value when storing it. |
| `--cloudsql-instance` | CLOUDSQL_INSTANCE |  | _[SSH private key..]_ If the source or destination is a Cloud SQL database, then use this field to provide the respective Cloud SQL instance ID. |
| `--cloudsql-project-id` | CLOUDSQL_PROJECT_ID |  | _[SSH private key..]_ The project id of the Cloud SQL instance. Only needed if the Cloud SQL instance is in a different project than the connection profile. This is only supported for source connection profiles for SQL Server. |


**Examples:**
```bash
To create a source connection profile my-source-profile for SQL Server:

    $ gcloud database-migration connection-profiles create sqlserver \
      my-source-profile --region=us-central1 \
      --gcs-bucket=bucket-name --gcs-prefix=prefix/path

To create a destination connection profile my-dest-profile for SQL Server:

    $ gcloud database-migration connection-profiles create sqlserver \
      my-dest-profile --region=us-central1 \
      --cloudsql-instance=cloudsql-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/connection-profiles/create/sqlserver)

---
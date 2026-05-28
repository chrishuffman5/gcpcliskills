# gcloud sql instances

provide commands for managing Cloud SQL instances

### `gcloud sql instances acquire-ssrs-lease`

Acquires a SQL Server Reporting Services lease on a Cloud SQL instance

Acquire a SQL Server Reporting Services lease on a Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances acquire-ssrs-lease INSTANCE
    --report-database=REPORT_DATABASE --service-login=SERVICE_LOGIN
    --setup-login=SETUP_LOGIN [--duration=DURATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--report-database` | REPORT_DATABASE |  | Existing or new report database name in the Cloud SQL for SQL Server instance that is used for SSRS setup. |
| `--service-login` | SERVICE_LOGIN |  | Existing login in the Cloud SQL for SQL Server instance that is used as the service login for SSRS setup. |
| `--setup-login` | SETUP_LOGIN |  | Existing login in the Cloud SQL for SQL Server instance that is used as the setup login for SSRS setup. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--duration` | DURATION |  | Time duration, in hours, that the lease will be active to allow SSRS setup. Default lease duration is 5 hours if this flag is not specified. |


**Examples:**
```bash
To acquire a SQL Server Reporting Services lease on an instance:

    $ gcloud sql instances acquire-ssrs-lease instance-foo \
        --setup-login=setuplogin --service-login=reportuser \
        --report-database=ReportServer --duration=4h
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/acquire-ssrs-lease)

---
### `gcloud sql instances clone`

Clones a Cloud SQL instance

gcloud sql instances clone creates a clone of a Cloud SQL instance. The
clone is an independent copy of the source instance with the same data and
settings. Source and destination instances must be in the same project. An
instance can be cloned from its current state, or from an earlier point in
time.

For MySQL: The binary log coordinates or timestamp (point in time), if
specified, act as the point in time the source instance is cloned from. If
not specified, the current state of the instance is cloned.

For PostgreSQL: The point in time, if specified, defines a past state of
the instance to clone. If not specified, the current state of the instance
is cloned.

For SQL Server: The point in time, if specified, defines a past state of
the instance to clone. If not specified, the current state of the instance
is cloned.

**Synopsis:**
```
gcloud sql instances clone SOURCE DESTINATION [--async]
    [--preferred-secondary-zone=PREFERRED_SECONDARY_ZONE]
    [--preferred-zone=PREFERRED_ZONE]
    [--source-instance-deletion-time=SOURCE_INSTANCE_DELETION_TIME]
    [--bin-log-file-name=BIN_LOG_FILE_NAME
      --bin-log-position=BIN_LOG_POSITION | [--point-in-time=POINT_IN_TIME
      : --restore-database-name=RESTORE_DATABASE_NAME]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SOURCE
   Cloud SQL instance ID of the source.

DESTINATION
   Cloud SQL instance ID of the clone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--preferred-secondary-zone` | PREFERRED_SECONDARY_ZONE |  | The preferred secondary zone for the cloned regional instance. If you specify a value for this flag, then the destination instance uses the value as the secondary zone. The secondary zone can't be the same as the primary zone. |
| `--preferred-zone` | PREFERRED_ZONE |  | The preferred zone for the cloned instance. If you specify a value for this flag, then the destination instance uses the value as the primary zone. |
| `--source-instance-deletion-time` | SOURCE_INSTANCE_DELETION_TIME |  | The time the source instance was deleted. This is required if cloning from a deleted instance. |


**Examples:**
```bash
To clone an instance from its current state (most recent binary log
coordinates):

    $ gcloud sql instances clone my-source-instance my-cloned-instance

To clone a MySQL instance from an earlier point in time (past binary log
coordinates):

    $ gcloud sql instances clone my-source-instance my-cloned-instance \
        --bin-log-file-name mysql-bin.000020 --bin-log-position 170

To clone a MySQL source instance at a specific point in time:

    $ gcloud sql instances clone my-source-instance my-cloned-instance \
        --point-in-time '2012-11-15T16:19:00.094Z'

To clone a PostgreSQL source instance at a specific point in time:

    $ gcloud sql instances clone my-source-instance my-cloned-instance \
        --point-in-time '2012-11-15T16:19:00.094Z'

To clone a SQL Server source instance at a specific point in time:

    $ gcloud sql instances clone my-source-instance my-cloned-instance \
        --point-in-time '2012-11-15T16:19:00.094Z'

To clone a deleted instance, include the name and deletion time of the
source instance:

    $ gcloud sql instances clone my-source-instance my-cloned-instance \
        --source-instance-deletion-time '2012-11-15T16:19:00.094Z'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/clone)

---
### `gcloud sql instances create`

Creates a new Cloud SQL instance

Creates a new Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances create INSTANCE
    [--activation-policy=ACTIVATION_POLICY]
    [--active-directory-dns-servers=[DNS_SERVER_IP_ADDRESS,...]]
    [--active-directory-domain=ACTIVE_DIRECTORY_DOMAIN]
    [--active-directory-mode=ACTIVE_DIRECTORY_MODE]
    [--active-directory-organizational-unit=ACTIVE_DIRECTORY_ORGANIZATIONAL_UNIT]
    [--active-directory-secret-manager-key=ACTIVE_DIRECTORY_SECRET_MANAGER_KEY]
    [--[no-]assign-ip] [--async] [--audit-bucket-path=AUDIT_BUCKET_PATH]
    [--audit-retention-interval=AUDIT_RETENTION_INTERVAL]
    [--audit-upload-interval=AUDIT_UPLOAD_INTERVAL]
    [--authorized-networks=NETWORK,[NETWORK,...]]
    [--availability-type=AVAILABILITY_TYPE] [--no-backup]
    [--backup-location=BACKUP_LOCATION]
    [--backup-start-time=BACKUP_START_TIME] [--cascadable-replica]
    [--clear-active-directory-dns-servers] [--collation=COLLATION]
    [--connection-pool-flags=FLAG=VALUE,[FLAG=VALUE,...]]
    [--connector-enforcement=CONNECTOR_ENFORCEMENT] [--cpu=CPU]
    [--custom-subject-alternative-names=DNS,[DNS,[DNS]]]
    [--database-flags=FLAG=VALUE,[FLAG=VALUE,...]]
    [--database-version=DATABASE_VERSION; default="MYSQL_8_0"]
    [--[no-]deletion-protection]
    [--deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE]
    [--deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE]
    [--deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME]
    [--edition=EDITION] [--enable-auto-upgrade-minor-version]
    [--enable-bin-log] [--[no-]enable-connection-pooling]
    [--[no-]enable-data-cache] [--[no-]enable-dataplex-integration]
    [--[no-]enable-google-ml-integration] [--enable-google-private-path]
    [--enable-password-policy] [--enable-point-in-time-recovery]
    [--enforce-new-sql-network-architecture]
    [--failover-replica-name=FAILOVER_REPLICA_NAME] [--[no-]final-backup]
    [--final-backup-retention-days=FINAL_BACKUP_RETENTION_DAYS]
    [--[no-]insights-config-query-insights-enabled]
    [--insights-config-query-plans-per-minute=INSIGHTS_CONFIG_QUERY_PLANS_PER_MINUTE]
    [--insights-config-query-string-length=INSIGHTS_CONFIG_QUERY_STRING_LENGTH]
    [--[no-]insights-config-record-application-tags]
    [--[no-]insights-config-record-client-address]
    [--instance-type=INSTANCE_TYPE]
    [--maintenance-release-channel=MAINTENANCE_RELEASE_CHANNEL]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY]
    [--maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [--master-instance-name=MASTER_INSTANCE_NAME] [--memory=MEMORY]
    [--network=NETWORK] [--node-count=NODE_COUNT]
    [--password-policy-complexity=PASSWORD_POLICY_COMPLEXITY]
    [--[no-]password-policy-disallow-username-substring]
    [--password-policy-min-length=PASSWORD_POLICY_MIN_LENGTH]
    [--password-policy-password-change-interval=PASSWORD_POLICY_PASSWORD_CHANGE_INTERVAL]
    [--password-policy-reuse-interval=PASSWORD_POLICY_REUSE_INTERVAL]
    [--psc-auto-connections=[network=NETWORK],[project=PROJECT]]
    [--[no-]recreate-replicas-on-primary-crash]
    [--replica-type=REPLICA_TYPE] [--replication=REPLICATION]
    [--require-ssl] [--[no-]retain-backups-on-delete]
    [--retained-backups-count=RETAINED_BACKUPS_COUNT]
    [--retained-transaction-log-days=RETAINED_TRANSACTION_LOG_DAYS]
    [--root-password=ROOT_PASSWORD] [--server-ca-mode=SERVER_CA_MODE]
    [--server-ca-pool=SERVER_CA_POOL] [--ssl-mode=SSL_MODE]
    [--[no-]storage-auto-increase]
    [--storage-provisioned-iops=STORAGE_PROVISIONED_IOPS]
    [--storage-provisioned-throughput=STORAGE_PROVISIONED_THROUGHPUT]
    [--storage-size=STORAGE_SIZE] [--storage-type=STORAGE_TYPE]
    [--tags=TAG=VALUE,[TAG=VALUE,...]]
    [--threads-per-core=THREADS_PER_CORE] [--tier=TIER, -t TIER]
    [--time-zone=TIME_ZONE] [--timeout=TIMEOUT; default=3600]
    [--allowed-psc-projects=PROJECT,[PROJECT,...]
      --enable-private-service-connect]
    [--disk-encryption-key=DISK_ENCRYPTION_KEY
      : --disk-encryption-key-keyring=DISK_ENCRYPTION_KEY_KEYRING
      --disk-encryption-key-location=DISK_ENCRYPTION_KEY_LOCATION
      --disk-encryption-key-project=DISK_ENCRYPTION_KEY_PROJECT]
    [--[no-]auto-scale-disable-scale-in --[no-]auto-scale-enabled
      --auto-scale-in-cooldown-seconds=AUTO_SCALE_IN_COOLDOWN_SECONDS
      --auto-scale-max-node-count=AUTO_SCALE_MAX_NODE_COUNT
      --auto-scale-min-node-count=AUTO_SCALE_MIN_NODE_COUNT
      --auto-scale-out-cooldown-seconds=AUTO_SCALE_OUT_COOLDOWN_SECONDS
      --auto-scale-target-metrics=[METRIC=VALUE,...]]
    [--region=REGION; default="us-central" | --gce-zone=GCE_ZONE
      | --secondary-zone=SECONDARY_ZONE --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activation-policy` | one of: always, never |  | Activation policy for this instance. This specifies when the instance should be activated and is applicable only when the instance state is RUNNABLE. The default is always. More information on activation policies can be found here: https://cloud.google.com/sql/docs/mysql/start-stop-restart-instance#activation_policy. ACTIVATION_POLICY must be one of: always, never. |
| `--active-directory-dns-servers` | [DNS_SERVER_IP_ADDRESS,...] |  | A comma-separated list of the DNS servers to be used for Active Directory. Only available for SQL Server instances. E.g: 10.0.0.1,10.0.0.2 |
| `--active-directory-domain` | ACTIVE_DIRECTORY_DOMAIN |  | Managed Service for Microsoft Active Directory domain this instance is joined to. Only available for SQL Server instances. |
| `--active-directory-mode` | one of: MANAGED_ACTIVE_DIRECTORY, CUSTOMER_MANAGED_ACTIVE_DIRECTORY |  | Defines the Active Directory mode. Only available for SQL Server instances. ACTIVE_DIRECTORY_MODE must be one of: MANAGED_ACTIVE_DIRECTORY, CUSTOMER_MANAGED_ACTIVE_DIRECTORY. |
| `--active-directory-organizational-unit` | ACTIVE_DIRECTORY_ORGANIZATIONAL_UNIT |  | Defines the organizational unit to be used for Active Directory. Only available for SQL Server instances. E.g: OU=Cloud,DC=ad,DC=example,DC=com |
| `--active-directory-secret-manager-key` | ACTIVE_DIRECTORY_SECRET_MANAGER_KEY |  | The secret manager key storing administrator credentials. Only available for SQL Server instances. |
| `--[no-]assign-ip` |  |  | Assign a public IP address to the instance. This is a public, externally available IPv4 address that you can use to connect to your instance when properly authorized. Use --assign-ip to enable and --no-assign-ip to disable. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--audit-bucket-path` | AUDIT_BUCKET_PATH |  | The location, as a Cloud Storage bucket, to which audit files are uploaded. The URI is in the form gs://bucketName/folderName. Only available for SQL Server instances. |
| `--audit-retention-interval` | AUDIT_RETENTION_INTERVAL |  | The number of days for audit log retention on disk, for example, 3dfor 3 days. Only available for SQL Server instances. |
| `--audit-upload-interval` | AUDIT_UPLOAD_INTERVAL |  | How often to upload audit logs (audit files), for example, 30mfor 30 minutes. Only available for SQL Server instances. |
| `--authorized-networks` | NETWORK,[NETWORK,...] |  | The list of external networks that are allowed to connect to the instance. Specified in CIDR notation, also known as 'slash' notation (e.g. 192.168.100.0/24). |
| `--availability-type` | one of: regional Provides high availability and is recommended for production instances; instance automatically fails over to another zone within your selected region |  | Specifies level of availability. AVAILABILITY_TYPE must be one of: regional Provides high availability and is recommended for production instances; instance automatically fails over to another zone within your selected region. zonal Provides no failover capability. This is the default. |
| `--backup` |  |  | Enables daily backup. Enabled by default, use --no-backup to disable. |
| `--backup-location` | BACKUP_LOCATION |  | Choose where to store your backups. Backups are stored in the closest multi-region location to you by default. Only customize if needed. |
| `--backup-start-time` | BACKUP_START_TIME |  | Start time of daily backups, specified in the HH:MM format, in the UTC timezone. |
| `--cascadable-replica` |  |  | Specifies whether a SQL Server replica is a cascadable replica. A cascadable replica is a SQL Server cross-region replica that supports replica(s) under it. This flag only takes effect when the --master-instance-name flag is set, and the replica under creation is in a different region than the primary instance. |
| `--clear-active-directory-dns-servers` |  |  | Removes the list of DNS Servers from the Active Directory Config. |
| `--collation` | COLLATION |  | Cloud SQL server-level collation setting, which specifies the set of rules for comparing characters in a character set. |
| `--connection-pool-flags` | FLAG=VALUE,[FLAG=VALUE,...] |  | Comma-separated list of connection pool flags to set on the instance connection pool. Use an equals sign to separate flag name and value. More information on available flags can be found here: https://cloud.google.com/sql/docs/mysql/managed-connection-pooling#configuration-options for MySQL and https://cloud.google.com/sql/docs/postgres/managed-connection-pooling#configuration-options for PostgreSQL. (e.g., --connection-pool-flags max_pool_size=1000,max_client_connections=20) |
| `--connector-enforcement` | one of: CONNECTOR_ENFORCEMENT_UNSPECIFIED The requirement for Cloud SQL connectors is unknown |  | Cloud SQL Connector enforcement mode. It determines how Cloud SQL Connectors are used in the connection. See the list of modes here (https://cloud.google.com/sql/docs/mysql/admin-api/rest/v1beta4/instances#connectorenforcement). CONNECTOR_ENFORCEMENT must be one of: CONNECTOR_ENFORCEMENT_UNSPECIFIED The requirement for Cloud SQL connectors is unknown. NOT_REQUIRED Does not require Cloud SQL connectors. REQUIRED Requires all connections to use Cloud SQL connectors, including the Cloud SQL Auth Proxy and Cloud SQL Java, Python, and Go connectors. Note: This disables all existing authorized networks. |
| `--cpu` | CPU |  | Whole number value indicating how many cores are desired in the machine. Both --cpu and --memory must be specified if a custom machine type is desired, and the --tier flag must be omitted.--cpu and --memory flags are not compatible with the Enterprise Plus edition. These flags should not be used when creating an Enterprise Plus edition, as the machine configuration is determined by the --tier flag instead. |
| `--custom-subject-alternative-names` | DNS,[DNS,[DNS]] |  | A comma-separated list of DNS names to add to the instance's SSL certificate. A custom SAN is a structured way to add additional DNS names (host names) that are not managed by Cloud SQL to an instance. It allows for hostname verification during establishment of a database connection using the DNS name over SSL/TLS. When you create and/or update an instance, you can add a comma-separated list of up to three DNS names to the server certificate of your instance. |
| `--database-flags` | FLAG=VALUE,[FLAG=VALUE,...] |  | Comma-separated list of database flags to set on the instance. Use an equals sign to separate flag name and value. Flags without values, like skip_grant_tables, can be written out without a value after, e.g., skip_grant_tables=. Use on/off for booleans. View the Instance Resource API for allowed flags. (e.g., --database-flags max_allowed_packet=55555,skip_grant_tables=,log_output=1) |
| `--database-version` | one of: MYSQL_5_6, MYSQL_5_7, MYSQL_8_0, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17, POSTGRES_18, SQLSERVER_2017_EXPRESS, SQLSERVER_2017_WEB, SQLSERVER_2017_STANDARD, SQLSERVER_2017_ENTERPRISE, SQLSERVER_2019_EXPRESS, SQLSERVER_2019_WEB, SQLSERVER_2019_STANDARD, SQLSERVER_2019_ENTERPRISE, SQLSERVER_2022_EXPRESS, SQLSERVER_2022_WEB, SQLSERVER_2022_STANDARD, SQLSERVER_2022_ENTERPRISE | MYSQL_8_0 | The database engine type and versions. If left unspecified, MYSQL_8_0 is used. See the list of database versions at https://cloud.google.com/sql/docs/mysql/admin-api/rest/v1beta4/SqlDatabaseVersion. Apart from listed major versions, DATABASE_VERSION also accepts supported minor versions. DATABASE_VERSION must be one of: MYSQL_5_6, MYSQL_5_7, MYSQL_8_0, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17, POSTGRES_18, SQLSERVER_2017_EXPRESS, SQLSERVER_2017_WEB, SQLSERVER_2017_STANDARD, SQLSERVER_2017_ENTERPRISE, SQLSERVER_2019_EXPRESS, SQLSERVER_2019_WEB, SQLSERVER_2019_STANDARD, SQLSERVER_2019_ENTERPRISE, SQLSERVER_2022_EXPRESS, SQLSERVER_2022_WEB, SQLSERVER_2022_STANDARD, SQLSERVER_2022_ENTERPRISE. |
| `--[no-]deletion-protection` |  |  | Enable deletion protection on a Cloud SQL instance. Use --deletion-protection to enable and --no-deletion-protection to disable. |
| `--deny-maintenance-period-end-date` | DENY_MAINTENANCE_PERIOD_END_DATE |  | Date when the deny maintenance period ends, that is 2021-01-10. |
| `--deny-maintenance-period-start-date` | DENY_MAINTENANCE_PERIOD_START_DATE |  | Date when the deny maintenance period begins, that is 2020-11-01. |
| `--deny-maintenance-period-time` | DENY_MAINTENANCE_PERIOD_TIME |  | Time when the deny maintenance period starts or ends, that is 05:00:00. |
| `--edition` | one of: enterprise, enterprise-plus |  | Specifies the edition of Cloud SQL instance. EDITION must be one of: enterprise, enterprise-plus. |
| `--enable-auto-upgrade-minor-version` |  |  | Enables auto-upgrade for MySQL 8.0 minor versions. The MySQL version must be 8.0.35 or higher. |
| `--enable-bin-log` |  |  | Allows for data recovery from a specific point in time, down to a fraction of a second. Must have automatic backups enabled to use. Make sure storage can support at least 7 days of logs. |
| `--[no-]enable-connection-pooling` |  |  | Enable connection pooling for the instance. Use --enable-connection-pooling to enable and --no-enable-connection-pooling to disable. |
| `--[no-]enable-data-cache` |  |  | Enable use of data cache for accelerated read performance. This flag is only available for Enterprise_Plus edition instances. Use --enable-data-cache to enable and --no-enable-data-cache to disable. |
| `--[no-]enable-dataplex-integration` |  |  | Enable Dataplex integration for Google Cloud SQL. Use --enable-dataplex-integration to enable and --no-enable-dataplex-integration to disable. |
| `--[no-]enable-google-ml-integration` |  |  | Enable Vertex AI integration for Google Cloud SQL. You can integrate Vertex AI with Cloud SQL for MySQL and Cloud SQL for PostgreSQL instances only. Use --enable-google-ml-integration to enable and --no-enable-google-ml-integration to disable. |
| `--enable-google-private-path` |  |  | Enable a private path for Google Cloud services. This flag specifies whether the instance is accessible to internal Google Cloud services such as BigQuery. This is only applicable to MySQL and PostgreSQL instances that don't use public IP. Currently, SQL Server isn't supported. |
| `--enable-password-policy` |  |  | Enable the password policy, which enforces user password management with the policies configured for the instance. This flag is only available for Postgres. |
| `--enable-point-in-time-recovery` |  |  | Allows for data recovery from a specific point in time, down to a fraction of a second, via write-ahead logs. Must have automatic backups enabled to use. Make sure storage can support at least 7 days of logs. |
| `--enforce-new-sql-network-architecture` |  |  | Force the instance to use the new network architecture. |
| `--failover-replica-name` | FAILOVER_REPLICA_NAME |  | Also create a failover replica with the specified name. |
| `--[no-]final-backup` |  |  | Enables the final backup to be taken at the time of instance deletion. Use --final-backup to enable and --no-final-backup to disable. |
| `--final-backup-retention-days` | FINAL_BACKUP_RETENTION_DAYS |  | Specifies number of days to retain final backup. The valid range is between 1 and 365. For instances managed by BackupDR, the valid range is between 1 day and 99 years. Default value is 30 days. |
| `--[no-]insights-config-query-insights-enabled` |  |  | Enable query insights feature to provide query and query plan analytics. Use --insights-config-query-insights-enabled to enable and --no-insights-config-query-insights-enabled to disable. |
| `--insights-config-query-plans-per-minute` | INSIGHTS_CONFIG_QUERY_PLANS_PER_MINUTE |  | Number of query plans to sample every minute. Default value is 5. Allowed range: 0 to 20. |
| `--insights-config-query-string-length` | INSIGHTS_CONFIG_QUERY_STRING_LENGTH |  | Sets the default query length limit. For Cloud SQL Enterprise edition, the range is from 256 to 4500 (in bytes) and the default query length is 1024 bytes. For Cloud SQL Enterprise Plus edition, the range is from 1024 to 100,000 (in bytes) and the default query length is 10,000 bytes. |
| `--[no-]insights-config-record-application-tags` |  |  | Allow application tags to be recorded by the query insights feature. Use --insights-config-record-application-tags to enable and --no-insights-config-record-application-tags to disable. |
| `--[no-]insights-config-record-client-address` |  |  | Allow the client address to be recorded by the query insights feature. Use --insights-config-record-client-address to enable and --no-insights-config-record-client-address to disable. |
| `--instance-type` | one of: CLOUD_SQL_INSTANCE A primary instance |  | The type of the instance. INSTANCE_TYPE must be one of: CLOUD_SQL_INSTANCE A primary instance. READ_POOL_INSTANCE A read pool instance. READ_REPLICA_INSTANCE A read replica instance. |
| `--maintenance-release-channel` | one of: preview Preview updates release prior to production updates |  | Which channel's updates to apply during the maintenance window. If not specified, Cloud SQL chooses the timing of updates to your instance. MAINTENANCE_RELEASE_CHANNEL must be one of: preview Preview updates release prior to production updates. You may wish to use the preview channel for dev/test applications so that you can preview their compatibility with your application prior to the production release. production Production updates are stable and recommended for applications in production. week5 week5 updates release after the production updates. Use the week5 channel to receive a 5 week advance notification about the upcoming maintenance, so you can prepare your application for the release. |
| `--maintenance-window-day` | one of: SUN, MON, TUE, WED, THU, FRI, SAT |  | Day of week for maintenance window, in UTC time zone. MAINTENANCE_WINDOW_DAY must be one of: SUN, MON, TUE, WED, THU, FRI, SAT. |
| `--maintenance-window-hour` | MAINTENANCE_WINDOW_HOUR |  | Hour of day for maintenance window, in UTC time zone. |
| `--master-instance-name` | MASTER_INSTANCE_NAME |  | Name of the instance which will act as master in the replication setup. The newly created instance will be a read replica of the specified master instance. |
| `--memory` | MEMORY |  | Whole number value indicating how much memory is desired in the machine. A size unit should be provided (eg. 3072MiB or 9GiB) - if no units are specified, GiB is assumed. Both --cpu and --memory must be specified if a custom machine type is desired, and the --tier flag must be omitted. --cpu and --memory flags are not compatible with the Enterprise Plus edition. These flags should not be used when creating an Enterprise Plus edition, as the machine configuration is determined by the --tier flag instead. |
| `--network` | NETWORK |  | Network in the current project that the instance will be part of. To specify using a network with a shared VPC, use the full URL of the network. For an example host project, 'testproject', and shared network, 'testsharednetwork', this would use the form: --network=projects/testproject/global/networks/testsharednetwork |
| `--node-count` | NODE_COUNT |  | The number of nodes in the pool. This option is only available for read pools. |
| `--password-policy-complexity` | one of: COMPLEXITY_DEFAULT A combination of lowercase, uppercase, numeric, and non-alphanumeric characters |  | The complexity of the password. This flag is available only for PostgreSQL. PASSWORD_POLICY_COMPLEXITY must be one of: COMPLEXITY_DEFAULT A combination of lowercase, uppercase, numeric, and non-alphanumeric characters. COMPLEXITY_UNSPECIFIED The default value if COMPLEXITY_DEFAULT is not specified. It implies that complexity check is not enabled. |
| `--[no-]password-policy-disallow-username-substring` |  |  | Disallow username as a part of the password. Use --password-policy-disallow-username-substring to enable and --no-password-policy-disallow-username-substring to disable. |
| `--password-policy-min-length` | PASSWORD_POLICY_MIN_LENGTH |  | Minimum number of characters allowed in the password. |
| `--password-policy-password-change-interval` | PASSWORD_POLICY_PASSWORD_CHANGE_INTERVAL |  | Minimum interval after which the password can be changed, for example, 2m for 2 minutes. See <a href="/sdk/gcloud/reference/topic/datetimes"> $ gcloud topic datetimes</a> for information on duration formats. This flag is available only for PostgreSQL. |
| `--password-policy-reuse-interval` | PASSWORD_POLICY_REUSE_INTERVAL |  | Number of previous passwords that cannot be reused. The valid range is 0 to 100. |
| `--psc-auto-connections` | [network=NETWORK],[project=PROJECT] |  | A comma-separated list of networks or network-project pairs. Each project is represented by a project number (numeric) or by a project ID (alphanumeric). This allows Private Service Connect connections to be created automatically for the specified networks. For example, this connection uses "the form psc-auto-connections=network=projects/testproject1/global/networks/testnetwork1" or "the form psc-auto-connections=project=testproject1,network=projects/testproject1/global/networks/testnetwork1". Sets psc_auto_connections value. network Required, sets network value. project Sets project value. Shorthand Example: --psc-auto-connections=network=string,project=string JSON Example: --psc-auto-connections='{"network": "string", "project": "string"}' File Example: --psc-auto-connections=path_to_file.(yaml\|json) |
| `--[no-]recreate-replicas-on-primary-crash` |  |  | Allow/Disallow replica recreation when a primary MySQL instance operating in reduced durability mode crashes. Not recreating the replicas might lead to data inconsistencies between the primary and its replicas. This setting is only applicable for MySQL instances and is enabled by default. Use --recreate-replicas-on-primary-crash to enable and --no-recreate-replicas-on-primary-crash to disable. |
| `--replica-type` | one of: READ, FAILOVER |  | The type of replica to create. REPLICA_TYPE must be one of: READ, FAILOVER. |
| `--replication` | one of: synchronous, asynchronous |  | Type of replication this instance uses. The default is synchronous. REPLICATION must be one of: synchronous, asynchronous. |
| `--require-ssl` |  |  | Specified if users connecting over IP must use SSL. |
| `--[no-]retain-backups-on-delete` |  |  | Retain automated/ondemand backups of the instance after the instance is deleted. Use --retain-backups-on-delete to enable and --no-retain-backups-on-delete to disable. |
| `--retained-backups-count` | RETAINED_BACKUPS_COUNT |  | How many backups to keep. The valid range is between 1 and 365. Default value is 7 for Enterprise edition instances. For Enterprise_Plus, default value is 15. Applicable only if --no-backups is not specified. |
| `--retained-transaction-log-days` | RETAINED_TRANSACTION_LOG_DAYS |  | How many days of transaction logs to keep. The valid range is between 1 and 35. Only use this option when point-in-time recovery is enabled. If logs are stored on disk, storage size for transaction logs could increase when the number of days for log retention increases. For Enterprise, default and max retention values are 7 and 7 respectively. For Enterprise_Plus, default and max retention values are 14 and 35. |
| `--root-password` | ROOT_PASSWORD |  | Root Cloud SQL user's password. |
| `--server-ca-mode` | one of: CUSTOMER_MANAGED_CAS_CA Customer-managed CA hosted on Google Cloud's Certificate Authority Service (CAS) |  | Set the server CA mode of the instance. SERVER_CA_MODE must be one of: CUSTOMER_MANAGED_CAS_CA Customer-managed CA hosted on Google Cloud's Certificate Authority Service (CAS). GOOGLE_MANAGED_CAS_CA Google-managed regional CA part of root CA hierarchy hosted on Google Cloud's Certificate Authority Service (CAS). GOOGLE_MANAGED_INTERNAL_CA Google-managed self-signed internal CA. |
| `--server-ca-pool` | SERVER_CA_POOL |  | Set the server CA pool of the instance. |
| `--ssl-mode` | one of: ALLOW_UNENCRYPTED_AND_ENCRYPTED Allow non-SSL and SSL connections |  | Set the SSL mode of the instance. SSL_MODE must be one of: ALLOW_UNENCRYPTED_AND_ENCRYPTED Allow non-SSL and SSL connections. For SSL connections, client certificate will not be verified. ENCRYPTED_ONLY Only allow connections encrypted with SSL/TLS. TRUSTED_CLIENT_CERTIFICATE_REQUIRED Only allow connections encrypted with SSL/TLS and with valid client certificates. |
| `--[no-]storage-auto-increase` |  |  | Storage size can be increased, but it cannot be decreased; storage increases are permanent for the life of the instance. With this setting enabled, a spike in storage requirements can result in permanently increased storage costs for your instance. However, if an instance runs out of available space, it can result in the instance going offline, dropping existing connections. This setting is enabled by default. Use --storage-auto-increase to enable and --no-storage-auto-increase to disable. |
| `--storage-provisioned-iops` | STORAGE_PROVISIONED_IOPS |  | Indicates how many IOPS to provision for the data disk. This sets the number of I/O operations per second that the disk can handle. |
| `--storage-provisioned-throughput` | STORAGE_PROVISIONED_THROUGHPUT |  | Indicates how much throughput to provision for the data disk. This sets the throughput in MB per second that the disk can handle. |
| `--storage-size` | STORAGE_SIZE |  | Amount of storage allocated to the instance. Must be an integer number of GB. The default is 10GB. Information on storage limits can be found here: https://cloud.google.com/sql/docs/quotas#storage_limits |
| `--storage-type` | one of: SSD, HDD, HYPERDISK_BALANCED |  | The storage type for the instance, determined by the selected machine type. STORAGE_TYPE must be one of: SSD, HDD, HYPERDISK_BALANCED. |
| `--tags` | TAG=VALUE,[TAG=VALUE,...] |  | Comma-separated list of tags to set on the instance. Use an equals signto separate tag name and value.(e.g., --tags tag1:value1,tag2=value2) |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of threads per core. The value of this flag can be 1 or 2. To disable SMT, set this flag to 1. Only available in Cloud SQL for SQL Server instances. |
| `--tier` | TIER, -t TIER |  | Machine type for a shared-core instance e.g. db-g1-small. For all other instances, instead of using tiers, customize your instance by specifying its CPU and memory. You can do so with the --cpu and --memory flags. Learn more about how CPU and memory affects pricing: https://cloud.google.com/sql/pricing. |
| `--time-zone` | TIME_ZONE |  | Set a non-default time zone. Only available for SQL Server instances. |
| `--timeout` | TIMEOUT | 3600 | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --async flag is specified. By default, set to 3600s. To wait indefinitely, set to unlimited. |
| `--allowed-psc-projects` | PROJECT,[PROJECT,...] |  | A comma-separated list of projects. Each project in this list might be represented by a project number (numeric) or by a project ID (alphanumeric). This allows Private Service Connect connections to be established from specified consumer projects. |
| `--enable-private-service-connect` |  |  | Enable connecting to the Cloud SQL instance with Private Service Connect. |


**Examples:**
```bash
To create a MySQL 8.0 instance with ID prod-instance that has 2 CPUs, 4 GB
of RAM, and is in the region us-central1 (a zone will be auto-assigned),
where the 'root' user has its password set to password123, run:

    $ gcloud sql instances create prod-instance \
        --database-version=MYSQL_8_0 --cpu=2 --memory=4GB \
        --region=us-central1 --root-password=password123

To create a Postgres 15 instance with ID prod-instance that has 2 CPUs, 8
GiB of RAM, and is in the zone us-central1-a, where the 'postgres' user has
its password set to password123, run:

    $ gcloud sql instances create prod-instance \
        --database-version=POSTGRES_15 --cpu=2 --memory=8GiB \
        --zone=us-central1-a --root-password=password123

To create a SQL Server 2022 Express instance with ID prod-instance that has
2 CPUs, 3840MiB of RAM, and is in the zone us-central1-a, where the
'sqlserver' user has its password set to password123, run:

    $ gcloud sql instances create prod-instance \
        --database-version=SQLSERVER_2022_EXPRESS --cpu=2 \
        --memory=3840MiB --zone=us-central1-a \
        --root-password=password123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create)

---
### `gcloud sql instances delete`

Deletes a Cloud SQL instance

Deletes a Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances delete INSTANCE [--async] [--enable-final-backup]
    [--final-backup-description=FINAL_BACKUP_DESCRIPTION]
    [--final-backup-expiry-time=FINAL_BACKUP_EXPIRY_TIME
      | --final-backup-retention-days=FINAL_BACKUP_RETENTION_DAYS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-final-backup` |  |  | Enables the final backup to be taken at the time of instance deletion. |
| `--final-backup-description` | FINAL_BACKUP_DESCRIPTION |  | Provides description for the final backup going to be taken. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/delete)

---
### `gcloud sql instances describe`

Displays configuration and metadata about a Cloud SQL instance

Displays configuration and metadata about a Cloud SQL instance.

Information such as instance name, IP address, region, the CA certificate
and configuration settings will be displayed.

**Synopsis:**
```
gcloud sql instances describe INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/describe)

---
### `gcloud sql instances export`

Exports data from a Cloud SQL instance

(DEPRECATED) Exports data from a Cloud SQL instance.

This command is deprecated and will be removed in version 205.0.0. Use
gcloud sql export sql instead.

Exports data from a Cloud SQL instance to a Google Cloud Storage bucket as
a MySQL dump file.

**Synopsis:**
```
gcloud sql instances export INSTANCE URI [--async]
    [--database=DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...]]
    [--table=TABLE,[TABLE,...], -t TABLE,[TABLE,...]]
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
| `--database` | DATABASE,[DATABASE,...], -d DATABASE,[DATABASE,...] |  | Database(s) from which the export is made. Information on requirements can be found here: https://cloud.google.com/sql/docs/mysql/admin-api/v1beta4/instances/export#exportContext.databases |
| `--table` | TABLE,[TABLE,...], -t TABLE,[TABLE,...] |  | Tables to export from the specified database. If you specify tables, specify one and only one database. For Postgres instances, only one table can be exported at a time. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/export)

---
### `gcloud sql instances failover`

Causes a high-availability Cloud SQL instance to failover

Causes a high-availability Cloud SQL instance to failover.

**Synopsis:**
```
gcloud sql instances failover INSTANCE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/failover)

---
### `gcloud sql instances get-latest-recovery-time`

Displays the latest recovery time to which a Cloud SQL instance can be restored to

gcloud sql instances get-latest-recovery-time retrieves the latest recovery
time for a Cloud SQL instance. This is the latest time that can be used to
perform point in time recovery for the Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances get-latest-recovery-time INSTANCE
    [--source-instance-deletion-time=SOURCE_INSTANCE_DELETION_TIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-instance-deletion-time` | SOURCE_INSTANCE_DELETION_TIME |  | The deletion time of the source instance. This is used to identify the instance if it has been deleted. |


**Examples:**
```bash
To retrieve the latest recovery time for an instance:

    $ gcloud sql instances get-latest-recovery-time instance-foo

To retrieve the latest recovery time for an instance that has been deleted:

    $ gcloud sql instances get-latest-recovery-time instance-foo \
        --source-instance-deletion-time '2012-11-15T16:19:00.094Z'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/get-latest-recovery-time)

---
### `gcloud sql instances import`

Imports data into a Cloud SQL instance from Google Cloud Storage

(DEPRECATED) Imports data into a Cloud SQL instance from Google Cloud
Storage.

This command is deprecated and will be removed in version 205.0.0. Use
gcloud sql import sql instead.

Note: authorization is required. For more information on importing data
into Google Cloud SQL see
https://cloud.google.com/sql/docs/import-export/importing.

Cloud SQL supports importing CSV files and SQL dump files from both MySQL
and PostgreSQL. For more information on how to create these export formats,
see
https://cloud.google.com/sql/docs/mysql/import-export/creating-sqldump-csv

**Synopsis:**
```
gcloud sql instances import INSTANCE URI [--async]
    [--database=DATABASE, -d DATABASE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.

URI
   Path to the MySQL dump file in Google Cloud Storage from which the
   import is made. The URI is in the form gs://bucketName/fileName.
   Compressed gzip files (.gz) are also supported.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--database` | DATABASE, -d DATABASE |  | Database to which the import is made. The database needs to be created before importing. If not set, it is assumed that the database is specified in the file to be imported. If your SQL dump file includes a database statement, it will override the database set in this flag. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/import)

---
### `gcloud sql instances list`

Lists Cloud SQL instances in a given project

Lists Cloud SQL instances in a given project in the alphabetical order of
the instance name.

**Synopsis:**
```
gcloud sql instances list [--show-edition]
    [--show-sql-network-architecture]
    [--show-transactional-log-storage-state] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-edition` |  |  | Show the edition field. |
| `--show-sql-network-architecture` |  |  | Show the instance's current SqlNetworkArchitecture backend in addition to the default output list. An instance could use either the old or new network architecture. The new network architecture offers better isolation, reliability, and faster new feature adoption. |
| `--show-transactional-log-storage-state` |  |  | Show the storage location of the transactional logs used for point-in-time recovery (PITR) by the instance. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/list)

---
### `gcloud sql instances patch`

Updates the settings of a Cloud SQL instance

Updates the settings of a Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances patch INSTANCE [--activation-policy=ACTIVATION_POLICY]
    [--active-directory-dns-servers=[DNS_SERVER_IP_ADDRESS,...]]
    [--active-directory-domain=ACTIVE_DIRECTORY_DOMAIN]
    [--active-directory-mode=ACTIVE_DIRECTORY_MODE]
    [--active-directory-organizational-unit=ACTIVE_DIRECTORY_ORGANIZATIONAL_UNIT]
    [--active-directory-secret-manager-key=ACTIVE_DIRECTORY_SECRET_MANAGER_KEY]
    [--[no-]assign-ip] [--async] [--audit-bucket-path=AUDIT_BUCKET_PATH]
    [--audit-retention-interval=AUDIT_RETENTION_INTERVAL]
    [--audit-upload-interval=AUDIT_UPLOAD_INTERVAL]
    [--availability-type=AVAILABILITY_TYPE] [--clear-active-directory]
    [--clear-active-directory-dns-servers]
    [--clear-failover-dr-replica-name] [--clear-password-policy]
    [--connector-enforcement=CONNECTOR_ENFORCEMENT] [--cpu=CPU]
    [--database-version=DATABASE_VERSION] [--[no-]deletion-protection]
    [--deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE]
    [--deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE]
    [--deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME] [--diff]
    [--edition=EDITION] [--enable-auto-upgrade-minor-version]
    [--[no-]enable-bin-log] [--[no-]enable-connection-pooling]
    [--[no-]enable-data-cache] [--[no-]enable-database-replication]
    [--[no-]enable-dataplex-integration]
    [--[no-]enable-google-ml-integration]
    [--[no-]enable-google-private-path] [--enable-password-policy]
    [--enable-point-in-time-recovery]
    [--[no-]enable-private-service-connect]
    [--enforce-new-sql-network-architecture]
    [--failover-dr-replica-name=FAILOVER_DR_REPLICA_NAME]
    [--[no-]final-backup]
    [--final-backup-retention-days=FINAL_BACKUP_RETENTION_DAYS]
    [--follow-gae-app=FOLLOW_GAE_APP]
    [--[no-]include-replicas-for-major-version-upgrade]
    [--[no-]insights-config-query-insights-enabled]
    [--insights-config-query-plans-per-minute=INSIGHTS_CONFIG_QUERY_PLANS_PER_MINUTE]
    [--insights-config-query-string-length=INSIGHTS_CONFIG_QUERY_STRING_LENGTH]
    [--[no-]insights-config-record-application-tags]
    [--[no-]insights-config-record-client-address]
    [--instance-type=INSTANCE_TYPE]
    [--maintenance-release-channel=MAINTENANCE_RELEASE_CHANNEL]
    [--maintenance-version=MAINTENANCE_VERSION] [--maintenance-window-any]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY]
    [--maintenance-window-hour=MAINTENANCE_WINDOW_HOUR] [--memory=MEMORY]
    [--network=NETWORK] [--node-count=NODE_COUNT]
    [--password-policy-complexity=PASSWORD_POLICY_COMPLEXITY]
    [--[no-]password-policy-disallow-username-substring]
    [--password-policy-min-length=PASSWORD_POLICY_MIN_LENGTH]
    [--password-policy-password-change-interval=PASSWORD_POLICY_PASSWORD_CHANGE_INTERVAL]
    [--password-policy-reuse-interval=PASSWORD_POLICY_REUSE_INTERVAL]
    [--pricing-plan=PRICING_PLAN, -p PRICING_PLAN]
    [--[no-]recreate-replicas-on-primary-crash]
    [--remove-deny-maintenance-period] [--replication=REPLICATION]
    [--[no-]require-ssl] [--[no-]retain-backups-on-delete]
    [--server-ca-mode=SERVER_CA_MODE] [--server-ca-pool=SERVER_CA_POOL]
    [--simulate-maintenance-event] [--ssl-mode=SSL_MODE]
    [--[no-]storage-auto-increase]
    [--storage-provisioned-iops=STORAGE_PROVISIONED_IOPS]
    [--storage-provisioned-throughput=STORAGE_PROVISIONED_THROUGHPUT]
    [--storage-size=STORAGE_SIZE] [--storage-type=STORAGE_TYPE]
    [--switch-transaction-logs-to-cloud-storage]
    [--threads-per-core=THREADS_PER_CORE] [--tier=TIER, -t TIER]
    [--time-zone=TIME_ZONE] [--upgrade-sql-network-architecture]
    [--allowed-psc-projects=PROJECT,[PROJECT,...]
      | --clear-allowed-psc-projects]
    [--authorized-gae-apps=APP,[APP,...] | --clear-gae-apps]
    [--authorized-networks=NETWORK,[NETWORK,...]
      | --clear-authorized-networks]
    [--clear-connection-pool-flags
      | --connection-pool-flags=FLAG=VALUE,[FLAG=VALUE,...]]
    [--clear-custom-subject-alternative-names
      | --custom-subject-alternative-names=DNS,[DNS,[DNS]]]
    [--clear-database-flags | --database-flags=FLAG=VALUE,[FLAG=VALUE,...]]
    [--clear-psc-auto-connections
      | --psc-auto-connections=[network=NETWORK],[project=PROJECT]]
    [--clear-psc-network-attachment-uri
      | --psc-network-attachment-uri=PSC_NETWORK_ATTACHMENT_URI]
    [--gce-zone=GCE_ZONE | --secondary-zone=SECONDARY_ZONE --zone=ZONE]
    [--[no-]auto-scale-disable-scale-in --[no-]auto-scale-enabled
      --auto-scale-in-cooldown-seconds=AUTO_SCALE_IN_COOLDOWN_SECONDS
      --auto-scale-max-node-count=AUTO_SCALE_MAX_NODE_COUNT
      --auto-scale-min-node-count=AUTO_SCALE_MIN_NODE_COUNT
      --auto-scale-out-cooldown-seconds=AUTO_SCALE_OUT_COOLDOWN_SECONDS
      --auto-scale-target-metrics=[METRIC=VALUE,...]]
    [--no-backup | --backup-location=BACKUP_LOCATION
      --backup-start-time=BACKUP_START_TIME
      --retained-backups-count=RETAINED_BACKUPS_COUNT
      --retained-transaction-log-days=RETAINED_TRANSACTION_LOG_DAYS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activation-policy` | one of: always, never |  | Activation policy for this instance. This specifies when the instance should be activated and is applicable only when the instance state is RUNNABLE. The default is always. More information on activation policies can be found here: https://cloud.google.com/sql/docs/mysql/start-stop-restart-instance#activation_policy. ACTIVATION_POLICY must be one of: always, never. |
| `--active-directory-dns-servers` | [DNS_SERVER_IP_ADDRESS,...] |  | A comma-separated list of the DNS servers to be used for Active Directory. Only available for SQL Server instances. E.g: 10.0.0.1,10.0.0.2 |
| `--active-directory-domain` | ACTIVE_DIRECTORY_DOMAIN |  | Managed Service for Microsoft Active Directory domain this instance is joined to. Only available for SQL Server instances. |
| `--active-directory-mode` | one of: MANAGED_ACTIVE_DIRECTORY, CUSTOMER_MANAGED_ACTIVE_DIRECTORY |  | Defines the Active Directory mode. Only available for SQL Server instances. ACTIVE_DIRECTORY_MODE must be one of: MANAGED_ACTIVE_DIRECTORY, CUSTOMER_MANAGED_ACTIVE_DIRECTORY. |
| `--active-directory-organizational-unit` | ACTIVE_DIRECTORY_ORGANIZATIONAL_UNIT |  | Defines the organizational unit to be used for Active Directory. Only available for SQL Server instances. E.g: OU=Cloud,DC=ad,DC=example,DC=com |
| `--active-directory-secret-manager-key` | ACTIVE_DIRECTORY_SECRET_MANAGER_KEY |  | The secret manager key storing administrator credentials. Only available for SQL Server instances. |
| `--[no-]assign-ip` |  |  | Assign a public IP address to the instance. This is a public, externally available IPv4 address that you can use to connect to your instance when properly authorized. Use --assign-ip to enable and --no-assign-ip to disable. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--audit-bucket-path` | AUDIT_BUCKET_PATH |  | The location, as a Cloud Storage bucket, to which audit files are uploaded. The URI is in the form gs://bucketName/folderName. Only available for SQL Server instances. |
| `--audit-retention-interval` | AUDIT_RETENTION_INTERVAL |  | The number of days for audit log retention on disk, for example, 3dfor 3 days. Only available for SQL Server instances. |
| `--audit-upload-interval` | AUDIT_UPLOAD_INTERVAL |  | How often to upload audit logs (audit files), for example, 30mfor 30 minutes. Only available for SQL Server instances. |
| `--availability-type` | one of: regional Provides high availability and is recommended for production instances; instance automatically fails over to another zone within your selected region |  | Specifies level of availability. AVAILABILITY_TYPE must be one of: regional Provides high availability and is recommended for production instances; instance automatically fails over to another zone within your selected region. zonal Provides no failover capability. This is the default. |
| `--clear-active-directory` |  |  | Clears the Active Directory configuration. |
| `--clear-active-directory-dns-servers` |  |  | Removes the list of DNS Servers from the Active Directory Config. |
| `--clear-failover-dr-replica-name` |  |  | Clear the DR replica setting for the primary instance. Flag is only available for MySQL and PostgreSQL database instances. |
| `--clear-password-policy` |  |  | Clear the existing password policy. This flag is only available for Postgres. |
| `--connector-enforcement` | one of: CONNECTOR_ENFORCEMENT_UNSPECIFIED The requirement for Cloud SQL connectors is unknown |  | Cloud SQL Connector enforcement mode. It determines how Cloud SQL Connectors are used in the connection. See the list of modes here (https://cloud.google.com/sql/docs/mysql/admin-api/rest/v1beta4/instances#connectorenforcement). CONNECTOR_ENFORCEMENT must be one of: CONNECTOR_ENFORCEMENT_UNSPECIFIED The requirement for Cloud SQL connectors is unknown. NOT_REQUIRED Does not require Cloud SQL connectors. REQUIRED Requires all connections to use Cloud SQL connectors, including the Cloud SQL Auth Proxy and Cloud SQL Java, Python, and Go connectors. Note: This disables all existing authorized networks. |
| `--cpu` | CPU |  | Whole number value indicating how many cores are desired in the machine. Both --cpu and --memory must be specified if a custom machine type is desired, and the --tier flag must be omitted.--cpu and --memory flags are not compatible with the Enterprise Plus edition. These flags should not be used when creating an Enterprise Plus edition, as the machine configuration is determined by the --tier flag instead. |
| `--database-version` | one of: MYSQL_5_6, MYSQL_5_7, MYSQL_8_0, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17, POSTGRES_18, SQLSERVER_2017_EXPRESS, SQLSERVER_2017_WEB, SQLSERVER_2017_STANDARD, SQLSERVER_2017_ENTERPRISE, SQLSERVER_2019_EXPRESS, SQLSERVER_2019_WEB, SQLSERVER_2019_STANDARD, SQLSERVER_2019_ENTERPRISE, SQLSERVER_2022_EXPRESS, SQLSERVER_2022_WEB, SQLSERVER_2022_STANDARD, SQLSERVER_2022_ENTERPRISE |  | The database engine type and versions. If left unspecified, no changes occur. See the list of database versions at https://cloud.google.com/sql/docs/mysql/admin-api/rest/v1beta4/SqlDatabaseVersion. Apart from listed major versions, DATABASE_VERSION also accepts supported minor versions. DATABASE_VERSION must be one of: MYSQL_5_6, MYSQL_5_7, MYSQL_8_0, MYSQL_8_4, POSTGRES_9_6, POSTGRES_10, POSTGRES_11, POSTGRES_12, POSTGRES_13, POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17, POSTGRES_18, SQLSERVER_2017_EXPRESS, SQLSERVER_2017_WEB, SQLSERVER_2017_STANDARD, SQLSERVER_2017_ENTERPRISE, SQLSERVER_2019_EXPRESS, SQLSERVER_2019_WEB, SQLSERVER_2019_STANDARD, SQLSERVER_2019_ENTERPRISE, SQLSERVER_2022_EXPRESS, SQLSERVER_2022_WEB, SQLSERVER_2022_STANDARD, SQLSERVER_2022_ENTERPRISE. |
| `--[no-]deletion-protection` |  |  | Enable deletion protection on a Cloud SQL instance. Use --deletion-protection to enable and --no-deletion-protection to disable. |
| `--deny-maintenance-period-end-date` | DENY_MAINTENANCE_PERIOD_END_DATE |  | Date when the deny maintenance period ends, that is 2021-01-10. |
| `--deny-maintenance-period-start-date` | DENY_MAINTENANCE_PERIOD_START_DATE |  | Date when the deny maintenance period begins, that is 2020-11-01. |
| `--deny-maintenance-period-time` | DENY_MAINTENANCE_PERIOD_TIME |  | Time when the deny maintenance period starts or ends, that is 05:00:00. |
| `--diff` |  |  | Show what changed as a result of the update. |
| `--edition` | one of: enterprise, enterprise-plus |  | Specifies the edition of Cloud SQL instance. EDITION must be one of: enterprise, enterprise-plus. |
| `--enable-auto-upgrade-minor-version` |  |  | Enables auto-upgrade for MySQL 8.0 minor versions. The MySQL version must be 8.0.35 or higher. |
| `--[no-]enable-bin-log` |  |  | Allows for data recovery from a specific point in time, down to a fraction of a second. Must have automatic backups enabled to use. Make sure storage can support at least 7 days of logs. Use --enable-bin-log to enable and --no-enable-bin-log to disable. |
| `--[no-]enable-connection-pooling` |  |  | Enable connection pooling for the instance. Use --enable-connection-pooling to enable and --no-enable-connection-pooling to disable. |
| `--[no-]enable-data-cache` |  |  | Enable use of data cache for accelerated read performance. This flag is only available for Enterprise_Plus edition instances. Use --enable-data-cache to enable and --no-enable-data-cache to disable. |
| `--[no-]enable-database-replication` |  |  | Enable database replication. Applicable only for read replica instance(s). WARNING: Instance will be restarted. Use --enable-database-replication to enable and --no-enable-database-replication to disable. |
| `--[no-]enable-dataplex-integration` |  |  | Enable Dataplex integration for Google Cloud SQL. Use --enable-dataplex-integration to enable and --no-enable-dataplex-integration to disable. |
| `--[no-]enable-google-ml-integration` |  |  | Enable Vertex AI integration for Google Cloud SQL. You can integrate Vertex AI with Cloud SQL for MySQL and Cloud SQL for PostgreSQL instances only. Use --enable-google-ml-integration to enable and --no-enable-google-ml-integration to disable. |
| `--[no-]enable-google-private-path` |  |  | Enable a private path for Google Cloud services. This flag specifies whether the instance is accessible to internal Google Cloud services such as BigQuery. This is only applicable to MySQL and PostgreSQL instances that don't use public IP. Currently, SQL Server isn't supported. Use --enable-google-private-path to enable and --no-enable-google-private-path to disable. |
| `--enable-password-policy` |  |  | Enable the password policy, which enforces user password management with the policies configured for the instance. This flag is only available for Postgres. |
| `--enable-point-in-time-recovery` |  |  | Allows for data recovery from a specific point in time, down to a fraction of a second, via write-ahead logs. Must have automatic backups enabled to use. Make sure storage can support at least 7 days of logs. |
| `--[no-]enable-private-service-connect` |  |  | Enable connecting to the Cloud SQL instance with Private Service Connect. Use --enable-private-service-connect to enable and --no-enable-private-service-connect to disable. |
| `--enforce-new-sql-network-architecture` |  |  | Force the instance to use the new network architecture. |
| `--failover-dr-replica-name` | FAILOVER_DR_REPLICA_NAME |  | Set a Disaster Recovery (DR) replica with the specified name for the primary instance. This must be one of the existing cross region replicas of the primary instance. Flag is only available for MySQL and PostgreSQL database instances. |
| `--[no-]final-backup` |  |  | Enables the final backup to be taken at the time of instance deletion. Use --final-backup to enable and --no-final-backup to disable. |
| `--final-backup-retention-days` | FINAL_BACKUP_RETENTION_DAYS |  | Specifies number of days to retain final backup. The valid range is between 1 and 365. For instances managed by BackupDR, the valid range is between 1 day and 99 years. Default value is 30 days. |
| `--follow-gae-app` | FOLLOW_GAE_APP |  | First Generation instances only. The App Engine app this instance should follow. It must be in the same region as the instance. WARNING: Instance may be restarted. |
| `--[no-]include-replicas-for-major-version-upgrade` |  |  | Enable the major version upgrade of replicas when the in-place major version upgrade of a primary instance is initated with --database-version. Use --include-replicas-for-major-version-upgrade to enable and --no-include-replicas-for-major--version-upgrade to disable. Use --include-replicas-for-major-version-upgrade to enable and --no-include-replicas-for-major-version-upgrade to disable. |
| `--[no-]insights-config-query-insights-enabled` |  |  | Enable query insights feature to provide query and query plan analytics. Use --insights-config-query-insights-enabled to enable and --no-insights-config-query-insights-enabled to disable. |
| `--insights-config-query-plans-per-minute` | INSIGHTS_CONFIG_QUERY_PLANS_PER_MINUTE |  | Number of query plans to sample every minute. Default value is 5. Allowed range: 0 to 20. |
| `--insights-config-query-string-length` | INSIGHTS_CONFIG_QUERY_STRING_LENGTH |  | Sets the default query length limit. For Cloud SQL Enterprise edition, the range is from 256 to 4500 (in bytes) and the default query length is 1024 bytes. For Cloud SQL Enterprise Plus edition, the range is from 1024 to 100,000 (in bytes) and the default query length is 10,000 bytes. |
| `--[no-]insights-config-record-application-tags` |  |  | Allow application tags to be recorded by the query insights feature. Use --insights-config-record-application-tags to enable and --no-insights-config-record-application-tags to disable. |
| `--[no-]insights-config-record-client-address` |  |  | Allow the client address to be recorded by the query insights feature. Use --insights-config-record-client-address to enable and --no-insights-config-record-client-address to disable. |
| `--instance-type` | one of: CLOUD_SQL_INSTANCE A primary instance |  | The type of the instance. INSTANCE_TYPE must be one of: CLOUD_SQL_INSTANCE A primary instance. READ_POOL_INSTANCE A read pool instance. READ_REPLICA_INSTANCE A read replica instance. |
| `--maintenance-release-channel` | one of: preview Preview updates release prior to production updates |  | Which channel's updates to apply during the maintenance window. If not specified, Cloud SQL chooses the timing of updates to your instance. MAINTENANCE_RELEASE_CHANNEL must be one of: preview Preview updates release prior to production updates. You may wish to use the preview channel for dev/test applications so that you can preview their compatibility with your application prior to the production release. production Production updates are stable and recommended for applications in production. week5 week5 updates release after the production updates. Use the week5 channel to receive a 5 week advance notification about the upcoming maintenance, so you can prepare your application for the release. |
| `--maintenance-version` | MAINTENANCE_VERSION |  | The desired maintenance version of the instance. |
| `--maintenance-window-any` |  |  | Removes the user-specified maintenance window. |
| `--maintenance-window-day` | one of: SUN, MON, TUE, WED, THU, FRI, SAT |  | Day of week for maintenance window, in UTC time zone. MAINTENANCE_WINDOW_DAY must be one of: SUN, MON, TUE, WED, THU, FRI, SAT. |
| `--maintenance-window-hour` | MAINTENANCE_WINDOW_HOUR |  | Hour of day for maintenance window, in UTC time zone. |
| `--memory` | MEMORY |  | Whole number value indicating how much memory is desired in the machine. A size unit should be provided (eg. 3072MiB or 9GiB) - if no units are specified, GiB is assumed. Both --cpu and --memory must be specified if a custom machine type is desired, and the --tier flag must be omitted. --cpu and --memory flags are not compatible with the Enterprise Plus edition. These flags should not be used when creating an Enterprise Plus edition, as the machine configuration is determined by the --tier flag instead. |
| `--network` | NETWORK |  | Network in the current project that the instance will be part of. To specify using a network with a shared VPC, use the full URL of the network. For an example host project, 'testproject', and shared network, 'testsharednetwork', this would use the form: --network=projects/testproject/global/networks/testsharednetwork |
| `--node-count` | NODE_COUNT |  | The number of nodes in the pool. This option is only available for read pools. |
| `--password-policy-complexity` | one of: COMPLEXITY_DEFAULT A combination of lowercase, uppercase, numeric, and non-alphanumeric characters |  | The complexity of the password. This flag is available only for PostgreSQL. PASSWORD_POLICY_COMPLEXITY must be one of: COMPLEXITY_DEFAULT A combination of lowercase, uppercase, numeric, and non-alphanumeric characters. COMPLEXITY_UNSPECIFIED The default value if COMPLEXITY_DEFAULT is not specified. It implies that complexity check is not enabled. |
| `--[no-]password-policy-disallow-username-substring` |  |  | Disallow username as a part of the password. Use --password-policy-disallow-username-substring to enable and --no-password-policy-disallow-username-substring to disable. |
| `--password-policy-min-length` | PASSWORD_POLICY_MIN_LENGTH |  | Minimum number of characters allowed in the password. |
| `--password-policy-password-change-interval` | PASSWORD_POLICY_PASSWORD_CHANGE_INTERVAL |  | Minimum interval after which the password can be changed, for example, 2m for 2 minutes. See <a href="/sdk/gcloud/reference/topic/datetimes"> $ gcloud topic datetimes</a> for information on duration formats. This flag is available only for PostgreSQL. |
| `--password-policy-reuse-interval` | PASSWORD_POLICY_REUSE_INTERVAL |  | Number of previous passwords that cannot be reused. The valid range is 0 to 100. |
| `--pricing-plan` | one of: PER_USE, PACKAGE |  | First Generation instances only. The pricing plan for this instance. PRICING_PLAN must be one of: PER_USE, PACKAGE. |
| `--[no-]recreate-replicas-on-primary-crash` |  |  | Allow/Disallow replica recreation when a primary MySQL instance operating in reduced durability mode crashes. Not recreating the replicas might lead to data inconsistencies between the primary and its replicas. This setting is only applicable for MySQL instances and is enabled by default. Use --recreate-replicas-on-primary-crash to enable and --no-recreate-replicas-on-primary-crash to disable. |
| `--remove-deny-maintenance-period` |  |  | Removes the user-specified deny maintenance period. |
| `--replication` | one of: synchronous, asynchronous |  | Type of replication this instance uses. The default is synchronous. REPLICATION must be one of: synchronous, asynchronous. |
| `--[no-]require-ssl` |  |  | mysqld should default to 'REQUIRE X509' for users connecting over IP. Use --require-ssl to enable and --no-require-ssl to disable. |
| `--[no-]retain-backups-on-delete` |  |  | Retain automated/ondemand backups of the instance after the instance is deleted. Use --retain-backups-on-delete to enable and --no-retain-backups-on-delete to disable. |
| `--server-ca-mode` | one of: CUSTOMER_MANAGED_CAS_CA Customer-managed CA hosted on Google Cloud's Certificate Authority Service (CAS) |  | Set the server CA mode of the instance. SERVER_CA_MODE must be one of: CUSTOMER_MANAGED_CAS_CA Customer-managed CA hosted on Google Cloud's Certificate Authority Service (CAS). GOOGLE_MANAGED_CAS_CA Google-managed regional CA part of root CA hierarchy hosted on Google Cloud's Certificate Authority Service (CAS). GOOGLE_MANAGED_INTERNAL_CA Google-managed self-signed internal CA. |
| `--server-ca-pool` | SERVER_CA_POOL |  | Set the server CA pool of the instance. |
| `--simulate-maintenance-event` |  |  | Simulate a maintenance event without changing the version. Only applicable to instances that support near-zero downtime planned maintenance. |
| `--ssl-mode` | one of: ALLOW_UNENCRYPTED_AND_ENCRYPTED Allow non-SSL and SSL connections |  | Set the SSL mode of the instance. SSL_MODE must be one of: ALLOW_UNENCRYPTED_AND_ENCRYPTED Allow non-SSL and SSL connections. For SSL connections, client certificate will not be verified. ENCRYPTED_ONLY Only allow connections encrypted with SSL/TLS. TRUSTED_CLIENT_CERTIFICATE_REQUIRED Only allow connections encrypted with SSL/TLS and with valid client certificates. |
| `--[no-]storage-auto-increase` |  |  | Storage size can be increased, but it cannot be decreased; storage increases are permanent for the life of the instance. With this setting enabled, a spike in storage requirements can result in permanently increased storage costs for your instance. However, if an instance runs out of available space, it can result in the instance going offline, dropping existing connections. This setting is enabled by default. Use --storage-auto-increase to enable and --no-storage-auto-increase to disable. |
| `--storage-provisioned-iops` | STORAGE_PROVISIONED_IOPS |  | Indicates how many IOPS to provision for the data disk. This sets the number of I/O operations per second that the disk can handle. |
| `--storage-provisioned-throughput` | STORAGE_PROVISIONED_THROUGHPUT |  | Indicates how much throughput to provision for the data disk. This sets the throughput in MB per second that the disk can handle. |
| `--storage-size` | STORAGE_SIZE |  | Amount of storage allocated to the instance. Must be an integer number of GB. The default is 10GB. Information on storage limits can be found here: https://cloud.google.com/sql/docs/quotas#storage_limits |
| `--storage-type` | one of: SSD, HDD, HYPERDISK_BALANCED |  | The storage type for the instance, determined by the selected machine type. STORAGE_TYPE must be one of: SSD, HDD, HYPERDISK_BALANCED. |
| `--switch-transaction-logs-to-cloud-storage` |  |  | Switches the location of the transaction logs used for PITR from disk to Cloud Storage. |
| `--threads-per-core` | THREADS_PER_CORE |  | The number of threads per core. The value of this flag can be 1 or 2. To disable SMT, set this flag to 1. Only available in Cloud SQL for SQL Server instances. |
| `--tier` | TIER, -t TIER |  | Machine type for a shared-core instance e.g. db-g1-small. For all other instances, instead of using tiers, customize your instance by specifying its CPU and memory. You can do so with the --cpu and --memory flags. Learn more about how CPU and memory affects pricing: https://cloud.google.com/sql/pricing. WARNING: Instance will be restarted. |
| `--time-zone` | TIME_ZONE |  | Set a non-default time zone. Only available for SQL Server instances. |
| `--upgrade-sql-network-architecture` |  |  | Upgrade from old network architecture to new network architecture. The new network architecture offers better isolation, reliability, and faster new feature adoption. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/patch)

---
### `gcloud sql instances point-in-time-restore`

Performs a point in time restore for a Cloud SQL instance managed by Google Cloud Backup and Disaster Recovery Service

gcloud sql instances point-in-time-restore performs a point in time restore
for a Cloud SQL instance managed by Google Cloud Backup and Disaster
Recovery (DR) Service.

**Synopsis:**
```
gcloud sql instances point-in-time-restore DATASOURCE TARGET POINT_IN_TIME
    [--allocated-ip-range-name=ALLOCATED_IP_RANGE_NAME] [--async]
    [--preferred-secondary-zone=PREFERRED_SECONDARY_ZONE]
    [--preferred-zone=PREFERRED_ZONE] [--private-network=PRIVATE_NETWORK]
    [--restore-database-names=RESTORE_DATABASE_NAMES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DATASOURCE
   The Google Cloud Backup and Disaster Recovery (DR) Service Datasource
   URI, of the form projects/{project}/locations/{region}/backupVaults/
   {backupvault}/dataSources/{datasource}.

TARGET
   Cloud SQL instance ID of the target instance.

POINT_IN_TIME
   The point in time in which to restore the instance to. Uses RFC 3339
   format in UTC timezone. For example, '2012-11-15T16:19:00.094Z'.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocated-ip-range-name` | ALLOCATED_IP_RANGE_NAME |  | The name of the IP range allocated for the target instance with private network connectivity. For example: 'google-managed-services-default'. If set, the target instance IP is created in the allocated range represented by this name. Reserved for future use. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--preferred-secondary-zone` | PREFERRED_SECONDARY_ZONE |  | The preferred secondary zone for the cloned regional instance. If you specify a value for this flag, then the target instance uses the value as the secondary zone. The secondary zone can't be the same as the primary zone. |
| `--preferred-zone` | PREFERRED_ZONE |  | The preferred zone for the target instance. If you specify a value for this flag, then the target instance uses the value as the primary zone. |
| `--private-network` | PRIVATE_NETWORK |  | The resource link for the VPC network from which the Cloud SQL instance is accessible for private IP. For example, '/projects/myProject/global/networks/default'. |
| `--restore-database-names` | RESTORE_DATABASE_NAMES |  | The name of the databases to be restored for a point-in-time restore. If set, the destination instance will only restore the specified databases. |


**Examples:**
```bash
To perform a point in time restore from an earlier point in time:

    $ gcloud sql instances point-in-time-restore datasource \
        target-instance '2012-11-15T16:19:00.094Z'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/point-in-time-restore)

---
### `gcloud sql instances pre-check-major-version-upgrade`

Performs pre-checks for a major version upgrade of a Cloud SQL instance

gcloud sql instances pre-check-major-version-upgrade performs pre-checks
for a major version upgrade of a Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances pre-check-major-version-upgrade INSTANCE
    --target-database-version=TARGET_DATABASE_VERSION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-database-version` | TARGET_DATABASE_VERSION |  | Target database version for the upgrade. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To perform pre-checks before upgrading to a target version:

    $ gcloud sql instances pre-check-major-version-upgrade \
        test-instance --target-database-version=POSTGRES_15
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/pre-check-major-version-upgrade)

---
### `gcloud sql instances promote-replica`

Promotes Cloud SQL read replica to a stand-alone instance

Promotes Cloud SQL read replica to a stand-alone instance.

**Synopsis:**
```
gcloud sql instances promote-replica REPLICA [--async] [--[no-]failover]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPLICA
   Cloud SQL read replica ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--[no-]failover` |  |  | Whether the promote operation is a failover. Use --failover to enable and --no-failover to disable. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/promote-replica)

---
### `gcloud sql instances reencrypt`

Reencrypts a Cloud SQL CMEK instance

Reencrypt a Cloud SQL CMEK instance with the primary key version.

**Synopsis:**
```
gcloud sql instances reencrypt INSTANCE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To reencrypt a Cloud SQL CMEK instance with the primary key version:

    $ gcloud sql instances reencrypt instance-foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/reencrypt)

---
### `gcloud sql instances release-ssrs-lease`

Releases a SQL Server Reporting Services lease on a Cloud SQL instance

Release a SQL Server Reporting Services lease on a Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances release-ssrs-lease INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Examples:**
```bash
To release a SQL Server Reporting Services lease on an instance:

    $ gcloud sql instances release-ssrs-lease instance-foo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/release-ssrs-lease)

---
### `gcloud sql instances reset-ssl-config`

Reset SSL materials according to the reset SSL mode

Reset SSL materials according to the reset SSL mode.

**Synopsis:**
```
gcloud sql instances reset-ssl-config INSTANCE [--async] [--mode=MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--mode` | one of: ALL Refresh all TLS configs |  | Selectively refresh the SSL materials. MODE must be one of: ALL Refresh all TLS configs. This is the default behaviour. SYNC_FROM_PRIMARY Refreshes the replication-related TLS configuration settings provided by the primary instance. Not applicable to on-premises replication instances. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/reset-ssl-config)

---
### `gcloud sql instances restart`

Restarts a Cloud SQL instance

Restarts a Cloud SQL instance.

**Synopsis:**
```
gcloud sql instances restart INSTANCE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/restart)

---
### `gcloud sql instances restore-backup`

Restores a backup of a Cloud SQL instance

DEPRECATED: This command is deprecated and will be removed. Use 'gcloud
beta sql backups restore' instead.

**Synopsis:**
```
gcloud sql instances restore-backup INSTANCE [--async]
    [--backup-id=BACKUP_ID] [--backup-instance=BACKUP_INSTANCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud SQL instance ID that will be restored.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-id` | BACKUP_ID |  | The ID of the backup run to restore from. |
| `--backup-instance` | BACKUP_INSTANCE |  | The ID of the instance that the backup was taken from. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/restore-backup)

---
### `gcloud sql instances switchover`

Switches over a Cloud SQL instance to one of its replicas

Switches over a Cloud SQL instance to one of its replicas.

**Synopsis:**
```
gcloud sql instances switchover REPLICA [--async] [--db-timeout=DB_TIMEOUT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REPLICA
   Cloud SQL replica ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--db-timeout` | DB_TIMEOUT |  | (MySQL and PostgreSQL only) Cloud SQL instance operations timeout, which is the sum of all database operations. Default value is 10 minutes and can be modified to a maximum value of 24h. |


**Examples:**
```bash
To switch over an instance to its replica called replica-instance:

    $ gcloud sql instances switchover replica-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/instances/switchover)

---
# gcloud alloydb clusters

provide commands for managing AlloyDB clusters

### `gcloud alloydb clusters create`

Create a new AlloyDB cluster within a given project

Create a new AlloyDB cluster within a given project.

**Synopsis:**
```
gcloud alloydb clusters create CLUSTER --password=PASSWORD --region=REGION
    [--allocated-ip-range-name=ALLOCATED_IP_RANGE_NAME] [--async]
    [--database-version=DATABASE_VERSION]
    [--enable-private-service-connect] [--network=NETWORK]
    [--subscription-type=SUBSCRIPTION_TYPE] [--tags=[KEY=VALUE,...]]
    [--continuous-backup-recovery-window-days=RECOVERY_PERIOD
      --enable-continuous-backup
      [--continuous-backup-encryption-key=CONTINUOUS_BACKUP_ENCRYPTION_KEY
      : --continuous-backup-encryption-key-keyring=CONTINUOUS_BACKUP_ENCRYPTION_KEY_KEYRING --continuous-backup-encryption-key-location=CONTINUOUS_BACKUP_ENCRYPTION_KEY_LOCATION --continuous-backup-encryption-key-project=CONTINUOUS_BACKUP_ENCRYPTION_KEY_PROJECT]]
    [--deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE
      --deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE --deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME]
    [--disable-automated-backup
      | [--automated-backup-days-of-week=[DAYS_OF_WEEK,...]
      --automated-backup-start-times=[START_TIMES,...]
      : --automated-backup-window=TIMEOUT_PERIOD
      [--automated-backup-encryption-key=AUTOMATED_BACKUP_ENCRYPTION_KEY
      : --automated-backup-encryption-key-keyring=AUTOMATED_BACKUP_ENCRYPTION_KEY_KEYRING --automated-backup-encryption-key-location=AUTOMATED_BACKUP_ENCRYPTION_KEY_LOCATION --automated-backup-encryption-key-project=AUTOMATED_BACKUP_ENCRYPTION_KEY_PROJECT] --automated-backup-retention-count=RETENTION_COUNT | --automated-backup-retention-period=RETENTION_PERIOD]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--password` | PASSWORD |  | Initial postgres user password to set up during cluster creation. |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocated-ip-range-name` | ALLOCATED_IP_RANGE_NAME |  | Name of the allocated IP range for the private IP AlloyDB cluster, for example: "google-managed-services-default". If set, the instance IPs for this cluster will be created in the allocated range. The range name must comply with RFC 1035. Specifically, the name must be 1-63 characters long and match the regular expression [a-z]([-a-z0-9]*[a-z0-9])?. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--database-version` | one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17 |  | Database version of the cluster. DATABASE_VERSION must be one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17. |
| `--enable-private-service-connect` |  |  | Enable Private Service Connect (PSC) connectivity for the cluster. |
| `--network` | NETWORK |  | Network in the current project that the instance will be part of. To specify using a network with a shared VPC, use the full URL of the network. For an example host project, testproject, and shared network, testsharednetwork, this would be of the form:--network=projects/testproject/global/networks/testsharednetwork |
| `--subscription-type` | one of: STANDARD, TRIAL |  | Subscription type of the cluster. SUBSCRIPTION_TYPE must be one of: STANDARD, TRIAL. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To create a new cluster, run:

    $ gcloud alloydb clusters create my-cluster --region=us-central1 \
        --password=postgres
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/create)

---
### `gcloud alloydb clusters create-secondary`

Create a new AlloyDB SECONDARY cluster within a given project

Create a new AlloyDB SECONDARY cluster within a given project.

**Synopsis:**
```
gcloud alloydb clusters create-secondary CLUSTER
    --primary-cluster=PRIMARY_CLUSTER --region=REGION
    [--allocated-ip-range-name=ALLOCATED_IP_RANGE_NAME] [--async]
    [--tags=[KEY=VALUE,...]]
    [--automated-backup-days-of-week=[DAYS_OF_WEEK,...]
      --automated-backup-start-times=[START_TIMES,...]
      --automated-backup-window=TIMEOUT_PERIOD --enable-automated-backup
      [--automated-backup-encryption-key=AUTOMATED_BACKUP_ENCRYPTION_KEY
      : --automated-backup-encryption-key-keyring=AUTOMATED_BACKUP_ENCRYPTION_KEY_KEYRING --automated-backup-encryption-key-location=AUTOMATED_BACKUP_ENCRYPTION_KEY_LOCATION --automated-backup-encryption-key-project=AUTOMATED_BACKUP_ENCRYPTION_KEY_PROJECT] --automated-backup-retention-count=RETENTION_COUNT | --automated-backup-retention-period=RETENTION_PERIOD]
    [--continuous-backup-recovery-window-days=RECOVERY_PERIOD
      --enable-continuous-backup
      [--continuous-backup-encryption-key=CONTINUOUS_BACKUP_ENCRYPTION_KEY
      : --continuous-backup-encryption-key-keyring=CONTINUOUS_BACKUP_ENCRYPTION_KEY_KEYRING --continuous-backup-encryption-key-location=CONTINUOUS_BACKUP_ENCRYPTION_KEY_LOCATION --continuous-backup-encryption-key-project=CONTINUOUS_BACKUP_ENCRYPTION_KEY_PROJECT]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--primary-cluster` | PRIMARY_CLUSTER |  | AlloyDB primary cluster ID |
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocated-ip-range-name` | ALLOCATED_IP_RANGE_NAME |  | Name of the allocated IP range for the private IP AlloyDB cluster, for example: "google-managed-services-default". If set, the instance IPs for this cluster will be created in the allocated range. The range name must comply with RFC 1035. Specifically, the name must be 1-63 characters long and match the regular expression [a-z]([-a-z0-9]*[a-z0-9])?. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To create a new cluster, run:

    $ gcloud alloydb clusters create-secondary my-cluster \
        --region=us-central1 \
        --primary-cluster=projects/12345/locations/us-central1/\
    clusters/cluster1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/create-secondary)

---
### `gcloud alloydb clusters delete`

Delete an AlloyDB cluster in a given region

Delete an AlloyDB cluster in a given region.

**Synopsis:**
```
gcloud alloydb clusters delete CLUSTER --region=REGION [--async] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | Default value is false. If flag is specified, deletes instances (if any) within this cluster, before deleting the cluster. If flag is not specified, cluster delete will fail if there are instances present in the cluster. |


**Examples:**
```bash
To delete a cluster, run:

    $ gcloud alloydb clusters delete my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/delete)

---
### `gcloud alloydb clusters describe`

Describe an AlloyDB cluster in a given project and region

Describe an AlloyDB cluster in a given project and region.

**Synopsis:**
```
gcloud alloydb clusters describe CLUSTER --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Examples:**
```bash
To describe a cluster, run:

    $ gcloud alloydb clusters describe my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/describe)

---
### `gcloud alloydb clusters export`

Export data from an AlloyDB cluster to Google Cloud Storage

Export data from an AlloyDB cluster to Google Cloud Storage.

**Synopsis:**
```
gcloud alloydb clusters export CLUSTER --database=DATABASE
    --gcs-uri=GCS_URI --region=REGION
    ([--csv --select-query=SELECT_QUERY
      : --escape-character=ESCAPE_CHARACTER
      --field-delimiter=FIELD_DELIMITER --quote-character=QUOTE_CHARACTER]
      | [--sql : --schema-only --tables=TABLES [--clean-target-objects
      : --if-exist-target-objects]]) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | Database name. |
| `--region` | REGION |  | _[Path to the Google Cloud Storage file to which export has to be done.]_ Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To export a cluster, run:

    $ gcloud alloydb clusters export my-cluster --region=us-central1 \
        --database=my-database \
        --gcs-uri=gs://my-bucket/my-export-file-path --csv \
        --select-query="SELECT * FROM my-table"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/export)

---
### `gcloud alloydb clusters import`

Import data into an AlloyDB cluster from Google Cloud Storage

Import data into an AlloyDB cluster from Google Cloud Storage.

**Synopsis:**
```
gcloud alloydb clusters import CLUSTER --gcs-uri=GCS_URI --region=REGION
    (--sql | [--csv --table=TABLE : --columns=COLUMNS
      --escape-character=ESCAPE_CHARACTER
      --field-delimiter=FIELD_DELIMITER --quote-character=QUOTE_CHARACTER])
    [--async] [--database=DATABASE] [--user=USER] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | _[This must be specified.]_ Path to the Google Cloud Storage file from which import has to be done. |
| `--region` | REGION |  | _[This must be specified.]_ Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--database` | DATABASE |  | Database name. |
| `--user` | USER |  | Database user for the import. |


**Examples:**
```bash
To import data into a cluster, run:

    $ gcloud alloydb clusters import my-cluster --region=us-central1 \
        --database=my-database \
        --gcs-uri=gs://my-bucket/source-file-path --sql --user=my-user"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/import)

---
### `gcloud alloydb clusters list`

List AlloyDB clusters in a given project and region

List AlloyDB clusters in a given project in alphabetical order based on the
cluster name.

**Synopsis:**
```
gcloud alloydb clusters list [--region=REGION; default="-"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION | - | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. Default: list clusters in all regions. |


**Examples:**
```bash
To list clusters, run:

    $ gcloud alloydb clusters list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/list)

---
### `gcloud alloydb clusters migrate-cloud-sql`

Migrate Cloud SQL instance to an AlloyDB cluster using an existing Cloud SQL backup

Migrate Cloud SQL instance to an AlloyDB cluster using an existing Cloud
SQL backup.

**Synopsis:**
```
gcloud alloydb clusters migrate-cloud-sql CLUSTER
    --cloud-sql-backup-id=CLOUD_SQL_BACKUP_ID
    --cloud-sql-instance-id=CLOUD_SQL_INSTANCE_ID
    --cloud-sql-project-id=CLOUD_SQL_PROJECT_ID --password=PASSWORD
    --region=REGION [--allocated-ip-range-name=ALLOCATED_IP_RANGE_NAME]
    [--async] [--database-version=DATABASE_VERSION]
    [--enable-private-service-connect] [--network=NETWORK]
    [--subscription-type=SUBSCRIPTION_TYPE] [--tags=[KEY=VALUE,...]]
    [--continuous-backup-recovery-window-days=RECOVERY_PERIOD
      --enable-continuous-backup
      [--continuous-backup-encryption-key=CONTINUOUS_BACKUP_ENCRYPTION_KEY
      : --continuous-backup-encryption-key-keyring=CONTINUOUS_BACKUP_ENCRYPTION_KEY_KEYRING --continuous-backup-encryption-key-location=CONTINUOUS_BACKUP_ENCRYPTION_KEY_LOCATION --continuous-backup-encryption-key-project=CONTINUOUS_BACKUP_ENCRYPTION_KEY_PROJECT]]
    [--deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE
      --deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE --deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME]
    [--disable-automated-backup
      | [--automated-backup-days-of-week=[DAYS_OF_WEEK,...]
      --automated-backup-start-times=[START_TIMES,...]
      : --automated-backup-window=TIMEOUT_PERIOD
      [--automated-backup-encryption-key=AUTOMATED_BACKUP_ENCRYPTION_KEY
      : --automated-backup-encryption-key-keyring=AUTOMATED_BACKUP_ENCRYPTION_KEY_KEYRING --automated-backup-encryption-key-location=AUTOMATED_BACKUP_ENCRYPTION_KEY_LOCATION --automated-backup-encryption-key-project=AUTOMATED_BACKUP_ENCRYPTION_KEY_PROJECT] --automated-backup-retention-count=RETENTION_COUNT | --automated-backup-retention-period=RETENTION_PERIOD]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-sql-backup-id` | CLOUD_SQL_BACKUP_ID |  | _[existing backup.]_ CloudSQL backup ID to migrate from. This must be the backup ID (myBackup). |
| `--cloud-sql-instance-id` | CLOUD_SQL_INSTANCE_ID |  | _[existing backup.]_ |
| `--cloud-sql-project-id` | CLOUD_SQL_PROJECT_ID |  | _[(myInstance).]_ |
| `--password` | PASSWORD |  | _[(myProject).]_ |
| `--region` | REGION |  | _[Initial postgres user password to set up during cluster creation.]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocated-ip-range-name` | ALLOCATED_IP_RANGE_NAME |  | Name of the allocated IP range for the private IP AlloyDB cluster, for example: "google-managed-services-default". If set, the instance IPs for this cluster will be created in the allocated range. The range name must comply with RFC 1035. Specifically, the name must be 1-63 characters long and match the regular expression [a-z]([-a-z0-9]*[a-z0-9])?. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--database-version` | one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17 |  | Database version of the cluster. DATABASE_VERSION must be one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17. |
| `--enable-private-service-connect` |  |  | Enable Private Service Connect (PSC) connectivity for the cluster. |
| `--network` | NETWORK |  | Network in the current project that the instance will be part of. To specify using a network with a shared VPC, use the full URL of the network. For an example host project, testproject, and shared network, testsharednetwork, this would be of the form:--network=projects/testproject/global/networks/testsharednetwork |
| `--subscription-type` | one of: STANDARD, TRIAL |  | Subscription type of the cluster. SUBSCRIPTION_TYPE must be one of: STANDARD, TRIAL. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To migrate a Cloud SQL instance to an AlloyDB cluster from a backup, run:

    $ gcloud alloydb clusters migrate-cloud-sql my-alloydb-cluster \
      --region=us-central1 \
      --cloud-sql-project-id=my-cloud-sql-project-id \
      --cloud-sql-instance-id=my-cloud-sql-cluster-id \
      --cloud-sql-backup-id=my-cloud-sql-backup-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/migrate-cloud-sql)

---
### `gcloud alloydb clusters promote`

Promote an AlloyDB SECONDARY cluster in a given project and region

Promote an AlloyDB SECONDARY cluster in a given project and region.

**Synopsis:**
```
gcloud alloydb clusters promote CLUSTER --region=REGION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To promote a cluster, run:

    $ gcloud alloydb clusters promote my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/promote)

---
### `gcloud alloydb clusters restore`

Restore an AlloyDB cluster from a given backup or a source cluster and a timestamp

Restore an AlloyDB cluster from a given backup or a source cluster and a
timestamp.

**Synopsis:**
```
gcloud alloydb clusters restore CLUSTER --region=REGION
    (--backup=BACKUP
      | --point-in-time=POINT_IN_TIME --source-cluster=SOURCE_CLUSTER)
    [--allocated-ip-range-name=ALLOCATED_IP_RANGE_NAME] [--async]
    [--enable-private-service-connect] [--network=NETWORK]
    [--tags=[KEY=VALUE,...]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allocated-ip-range-name` | ALLOCATED_IP_RANGE_NAME |  | Name of the allocated IP range for the private IP AlloyDB cluster, for example: "google-managed-services-default". If set, the instance IPs for this cluster will be created in the allocated range. The range name must comply with RFC 1035. Specifically, the name must be 1-63 characters long and match the regular expression [a-z]([-a-z0-9]*[a-z0-9])?. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-private-service-connect` |  |  | Enable Private Service Connect (PSC) connectivity for the cluster. |
| `--network` | NETWORK |  | Network in the current project that the instance will be part of. To specify using a network with a shared VPC, use the full URL of the network. For an example host project, testproject, and shared network, testsharednetwork, this would be of the form:--network=projects/testproject/global/networks/testsharednetwork |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To restore a cluster from a backup, run:

    $ gcloud alloydb clusters restore my-cluster --region=us-central1 \
      --backup=my-backup

To restore a cluster from a source cluster and a timestamp, run:

    $ gcloud alloydb clusters restore my-cluster --region=us-central1 \
      --source-cluster=old-cluster \
      --point-in-time=2012-11-15T16:19:00.094Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/restore)

---
### `gcloud alloydb clusters switchover`

Switchover an AlloyDB SECONDARY cluster in a given project and region

Switchover an AlloyDB SECONDARY cluster in a given project and region.

**Synopsis:**
```
gcloud alloydb clusters switchover CLUSTER --region=REGION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To switchover a cluster, run:

    $ gcloud alloydb clusters switchover my-cluster --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/switchover)

---
### `gcloud alloydb clusters update`

Update an AlloyDB cluster within a given project and region

Update an AlloyDB cluster within a given project and region.

**Synopsis:**
```
gcloud alloydb clusters update CLUSTER --region=REGION [--async]
    [--maintenance-version=MAINTENANCE_VERSION]
    [--subscription-type=SUBSCRIPTION_TYPE]
    [--clear-automated-backup | --disable-automated-backup
      | --automated-backup-days-of-week=[DAYS_OF_WEEK,...]
      --automated-backup-start-times=[START_TIMES,...]
      --automated-backup-window=TIMEOUT_PERIOD
      [--automated-backup-encryption-key=AUTOMATED_BACKUP_ENCRYPTION_KEY
      : --automated-backup-encryption-key-keyring=AUTOMATED_BACKUP_ENCRYPTION_KEY_KEYRING --automated-backup-encryption-key-location=AUTOMATED_BACKUP_ENCRYPTION_KEY_LOCATION --automated-backup-encryption-key-project=AUTOMATED_BACKUP_ENCRYPTION_KEY_PROJECT] --automated-backup-retention-count=RETENTION_COUNT | --automated-backup-retention-period=RETENTION_PERIOD]
    [--continuous-backup-recovery-window-days=RECOVERY_PERIOD
      --enable-continuous-backup --clear-continuous-backup-encryption-key
      | [--continuous-backup-encryption-key=CONTINUOUS_BACKUP_ENCRYPTION_KEY : --continuous-backup-encryption-key-keyring=CONTINUOUS_BACKUP_ENCRYPTION_KEY_KEYRING --continuous-backup-encryption-key-location=CONTINUOUS_BACKUP_ENCRYPTION_KEY_LOCATION --continuous-backup-encryption-key-project=CONTINUOUS_BACKUP_ENCRYPTION_KEY_PROJECT]]
    [--maintenance-window-any
      | --maintenance-window-day=MAINTENANCE_WINDOW_DAY
      --maintenance-window-hour=MAINTENANCE_WINDOW_HOUR]
    [--remove-deny-maintenance-period
      | --deny-maintenance-period-end-date=DENY_MAINTENANCE_PERIOD_END_DATE
      --deny-maintenance-period-start-date=DENY_MAINTENANCE_PERIOD_START_DATE --deny-maintenance-period-time=DENY_MAINTENANCE_PERIOD_TIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--maintenance-version` | MAINTENANCE_VERSION |  | Maintenance version to update the cluster to. Use latest to apply the latest available maintenance version. |
| `--subscription-type` | one of: STANDARD, TRIAL |  | Subscription type of the cluster. SUBSCRIPTION_TYPE must be one of: STANDARD, TRIAL. |


**Examples:**
```bash
To update a cluster, run:

    $ gcloud alloydb clusters update my-cluster --region=us-central1 \
        --automated-backup-start-times=12:00 \
        --automated-backup-days-of-week=MONDAY \
        --automated-backup-retention-count=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/update)

---
### `gcloud alloydb clusters upgrade`

Upgrade an AlloyDB cluster within a given project and region

Upgrade an AlloyDB cluster within a given project and region.

**Synopsis:**
```
gcloud alloydb clusters upgrade CLUSTER --region=REGION --version=VERSION
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CLUSTER
   AlloyDB cluster ID
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Regional location (e.g. asia-east1, us-east1). See the full list of regions at https://cloud.google.com/sql/docs/instance-locations. |
| `--version` | one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17 |  | Target database version for the upgrade. VERSION must be one of: POSTGRES_14, POSTGRES_15, POSTGRES_16, POSTGRES_17. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upgrade a cluster, run:

    $ gcloud alloydb clusters upgrade my-cluster --region=us-central1 \
        --version=POSTGRES_15
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/alloydb/clusters/upgrade)

---
# gcloud storage insights

manage Cloud Storage inventory reports


## `gcloud storage insights dataset-configs` — manage Cloud Storage Insights dataset configurations
### `gcloud storage insights dataset-configs create`

Create a new dataset config for Insights

Create a new dataset config for Insights.

**Synopsis:**
```
gcloud storage insights dataset-configs create DATASET_CONFIG_NAME
    --location=LOCATION --organization=SOURCE_ORG_NUMBER
    --retention-period-days=RETENTION_DAYS
    (--enable-organization-scope
      | --source-folders=[SOURCE_FOLDER_NUMBERS,...]
      | --source-folders-file=SOURCE_FOLDER_NUMBERS_IN_FILE
      | --source-projects=[SOURCE_PROJECT_NUMBERS,...]
      | --source-projects-file=SOURCE_PROJECT_NUMBERS_IN_FILE)
    [--activity-data-retention-period-days=ACTIVITY_DATA_RETENTION_DAYS]
    [--auto-add-new-buckets] [--description=DESCRIPTION]
    [--identity=IDENTITY_TYPE; default="IDENTITY_TYPE_PER_CONFIG"]
    [--exclude-bucket-names=[BUCKETS_NAMES,...]
      --exclude-bucket-prefix-regexes=[BUCKETS_REGEXES,...]
      | --include-bucket-names=[BUCKETS_NAMES,...]
      --include-bucket-prefix-regexes=[BUCKETS_REGEXES,...]]
    [--exclude-source-locations=[LIST_OF_SOURCE_LOCATIONS,...]
      | --include-source-locations=[LIST_OF_SOURCE_LOCATIONS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DATASET_CONFIG_NAME
   Provide human readable config name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Provide location of the dataset config. |
| `--organization` | SOURCE_ORG_NUMBER |  | Provide the source organization number. |
| `--retention-period-days` | RETENTION_DAYS |  | Provide retention period for the config. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activity-data-retention-period-days` | ACTIVITY_DATA_RETENTION_DAYS |  | Provide retention period for the activity data in the config. This overrides the retention period for activity data. Otherwise, the retention_period_days value is used for activity data as well. |
| `--auto-add-new-buckets` |  |  | Automatically include any new buckets created if they satisfy criteria defined in config settings. |
| `--description` | DESCRIPTION |  | Description for dataset config. |
| `--identity` | one of: IDENTITY_TYPE_PER_CONFIG, IDENTITY_TYPE_PER_PROJECT | IDENTITY_TYPE_PER_CONFIG | The type of service account used in the dataset config. IDENTITY_TYPE must be one of: IDENTITY_TYPE_PER_CONFIG, IDENTITY_TYPE_PER_PROJECT. |


**Examples:**
```bash
To create a dataset config with config name as "my_config" in location
"us-central1" and project numbers "123456" and "456789" belonging to
organization number "54321":

    $ gcloud storage insights dataset-configs create my_config \
       --location=us-central1 --source-projects=123456,456789 \
       --organization=54321 --retention-period-days=1

To create a dataset config that automatically adds new buckets into config:

    $ gcloud storage insights dataset-configs create my_config \
       --location=us-central1 --source-projects=123456,456789 \
       --organization=54321 --auto-add-new-buckets \
       --retention-period-days=1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/create)

---
### `gcloud storage insights dataset-configs create-link`

Create a link to a BigQuery instance

Create link to the customer BigQuery instance for Insights dataset config.

**Synopsis:**
```
gcloud storage insights dataset-configs create-link
    (DATASET_CONFIG : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset config resource - The Dataset config to create link. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument dataset_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET_CONFIG
     ID of the dataset-config or fully qualified identifier for the
     dataset-config.

     To set the dataset-config attribute:
     + provide the argument dataset_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Insights supported Google Cloud location for the dataset-config.

     To set the location attribute:
     + provide the argument dataset_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To create a link to the customer BigQuery instance for config name:
"my_config" in location "us-central1":

    $ gcloud storage insights dataset-configs create-link my_config \
      --location=us-central1

To create a link for the same dataset config with fully specified name:

    $ gcloud storage insights dataset-configs create-link \
      projects/foo/locations/us-central1/datasetConfigs/my_config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/create-link)

---
### `gcloud storage insights dataset-configs delete`

Delete dataset config for Insights

Delete an Insights dataset config.

**Synopsis:**
```
gcloud storage insights dataset-configs delete
    (DATASET_CONFIG : --location=LOCATION) [--auto-delete-link] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset config resource - The Dataset config to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument dataset_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET_CONFIG
     ID of the dataset-config or fully qualified identifier for the
     dataset-config.

     To set the dataset-config attribute:
     + provide the argument dataset_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Insights supported Google Cloud location for the dataset-config.

     To set the location attribute:
     + provide the argument dataset_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-delete-link` |  |  | Delete the BigQuery instance links before the config gets deleted explicitly. |
| `--force` |  |  | Force delete the config by skipping the consent. |


**Examples:**
```bash
To delete a dataset config with config name "my_config" in location
"us-central1":

    $ gcloud storage insights dataset-configs delete my_config \
      --location=us-central1

To delete the same dataset config with fully specified name:

    $gcloud storage insights dataset-configs delete projects/foo/locations/us-central1/datasetConfigs/my_config

To delete the same dataset config and unlink it from the BigQuery instance:

    $ gcloud storage insights dataset-configs delete my_config \
      --location=us-central1 --auto-delete-link

To delete the same dataset config without taking user consent:

    $ gcloud storage insights dataset-configs delete my_config \
      --location=us-central1 --auto-delete-link --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/delete)

---
### `gcloud storage insights dataset-configs delete-link`

Delete a link to a BigQuery instance

Delete a link to a BigQuery instance.

**Synopsis:**
```
gcloud storage insights dataset-configs delete-link
    (DATASET_CONFIG : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset config resource - The Dataset config to delete link. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument dataset_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET_CONFIG
     ID of the dataset-config or fully qualified identifier for the
     dataset-config.

     To set the dataset-config attribute:
     + provide the argument dataset_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Insights supported Google Cloud location for the dataset-config.

     To set the location attribute:
     + provide the argument dataset_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To unlink a dataset config with config name "my_config" in location
"us-central1":

    $ gcloud storage insights dataset-configs delete-link my_config \
      --location=us-central1

To delete a link for the same dataset config with fully specified name:

    $ gcloud storage insights dataset-configs delete-link \
      projects/foo/locations/us-central1/datasetConfigs/my_config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/delete-link)

---
### `gcloud storage insights dataset-configs describe`

Describe dataset config for Insights

Describe the Insights dataset config.

**Synopsis:**
```
gcloud storage insights dataset-configs describe
    (DATASET_CONFIG : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset config resource - The Dataset config to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument dataset_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET_CONFIG
     ID of the dataset-config or fully qualified identifier for the
     dataset-config.

     To set the dataset-config attribute:
     + provide the argument dataset_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Insights supported Google Cloud location for the dataset-config.

     To set the location attribute:
     + provide the argument dataset_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a dataset config with config name "my_config" in location
"us-central1":

    $ gcloud storage insights dataset-configs describe my_config \
      --location=us-central1

To describe the same dataset config with fully specified name:

    $ gcloud storage insights dataset-configs describe \
      projects/foo/locations/us-central1/datasetConfigs/my_config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/describe)

---
### `gcloud storage insights dataset-configs list`

List returns all the Insights dataset configs for given location

List Cloud storage Insights dataset configs.

**Synopsis:**
```
gcloud storage insights dataset-configs list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Provide location of the dataset config. |


**Examples:**
```bash
List all dataset configs in all locations:

    $ gcloud storage insights dataset-configs list

List all dataset configs for location "us-central1":

    $ gcloud storage insights dataset-configs list --location=us-central1

List all dataset configs with a page size of "20":

    $ gcloud storage insights dataset-configs list \
      --location=us-central1 --page-size=20

List all dataset configs with JSON formatting:

    $ gcloud storage insights dataset-configs list \
      --location=us-central1 --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/list)

---
### `gcloud storage insights dataset-configs update`

Updates a dataset config for Insights

Update a dataset config for Insights.

**Synopsis:**
```
gcloud storage insights dataset-configs update
    (DATASET_CONFIG : --location=LOCATION)
    [--activity-data-retention-period-days=ACTIVITY_DATA_RETENTION_DAYS]
    [--auto-add-new-buckets=AUTO_ADD_NEW_BUCKETS]
    [--description=DESCRIPTION] [--retention-period-days=RETENTION_DAYS]
    [--enable-organization-scope
      | --source-folders=[SOURCE_FOLDER_NUMBERS,...]
      | --source-folders-file=SOURCE_FOLDER_NUMBERS_IN_FILE
      | --source-projects=[SOURCE_PROJECT_NUMBERS,...]
      | --source-projects-file=SOURCE_PROJECT_NUMBERS_IN_FILE]
    [--exclude-bucket-names=[BUCKETS_NAMES,...]
      --exclude-bucket-prefix-regexes=[BUCKETS_REGEXES,...]
      | --include-bucket-names=[BUCKETS_NAMES,...]
      --include-bucket-prefix-regexes=[BUCKETS_REGEXES,...]]
    [--exclude-source-locations=[LIST_OF_SOURCE_LOCATIONS,...]
      | --include-source-locations=[LIST_OF_SOURCE_LOCATIONS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset config resource - The Dataset config to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument dataset_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET_CONFIG
     ID of the dataset-config or fully qualified identifier for the
     dataset-config.

     To set the dataset-config attribute:
     + provide the argument dataset_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Insights supported Google Cloud location for the dataset-config.

     To set the location attribute:
     + provide the argument dataset_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activity-data-retention-period-days` | ACTIVITY_DATA_RETENTION_DAYS |  | Provide retention period for the activity data in the config. This overrides the retention period for activity data. Otherwise, the retention_period_days value is used for activity data as well. |
| `--auto-add-new-buckets` | one of: true, false |  | Automatically include any new buckets created if they satisfy criteria defined in config settings. AUTO_ADD_NEW_BUCKETS must be one of: true, false. |
| `--description` | DESCRIPTION |  | Description for dataset config. |
| `--retention-period-days` | RETENTION_DAYS |  | Provide retention period for the config. |


**Examples:**
```bash
To update the description for a dataset config "my_config" in location
"us-central1":

    $ gcloud storage insights dataset-configs update my_config \
      --location=us-central1 \
      --description="a user provided description"

To update the same dataset config with fully specified name:

    $ gcloud storage insights dataset-configs update \
      projects/foo/locations/us-central1/datasetConfigs/my_config

To update the retention period days for the dataset config "my_config" in
location "us-central1":

    $ gcloud storage insights dataset-configs update my_config \
      --location=us-central1 --retention-period-days=20
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/dataset-configs/update)

---

## `gcloud storage insights inventory-reports` — manage Cloud Storage inventory report configurations
### `gcloud storage insights inventory-reports create`

Create a new inventory report config

Create an inventory report config that defines how often inventory reports
are generated, the metadata fields you want the reports to include, and a
bucket/prefix in which to store the reports, also known as the destination.

**Synopsis:**
```
gcloud storage insights inventory-reports create SOURCE_BUCKET_URL
    [--destination=DESTINATION_URL] [--display-name=DISPLAY_NAME]
    [--metadata-fields=[METADATA_FIELDS,...];
      default="project,bucket,name,location,size,timeCreated,timeDeleted,
      updated,storageClass,etag,retentionExpirationTime,crc32c,md5Hash,
      generation,
      metageneration,contentType,contentEncoding,timeStorageClassUpdated"]
    [--schedule-repeats=FREQUENCY; default="daily"]
    [--schedule-repeats-until=END_DATE] [--schedule-starts=START_DATE]
    [--parquet | --csv-delimiter=DELIMITER
      --[no-]csv-header --csv-separator=SEPARATOR] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SOURCE_BUCKET_URL
   URL of the source bucket that will contain the inventory report
   configuration.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION_URL |  | Sets the URL of the destination bucket and path where generated reports are stored. Defaults to <SOURCE_BUCKET_URL>/inventory_reports/. |
| `--display-name` | DISPLAY_NAME |  | Sets the editable name of the report configuration. |
| `--metadata-fields` | one of: project, bucket, name, location, size, timeCreated, timeDeleted, updated, storageClass, etag, retentionExpirationTime, crc32c, md5Hash, generation, metageneration, contentType, contentEncoding, timeStorageClassUpdated | project,bucket,name,location,size,timeCreated,timeDeleted,updated,storageClass,etag,retentionExpirationTime,crc32c,md5Hash,generation,metageneration,contentType,contentEncoding,timeStorageClassUpdated | The metadata fields to be included in the inventory report. The fields: "project, bucket, name" are REQUIRED. Defaults to all fields being included. METADATA_FIELDS must be one of: project, bucket, name, location, size, timeCreated, timeDeleted, updated, storageClass, etag, retentionExpirationTime, crc32c, md5Hash, generation, metageneration, contentType, contentEncoding, timeStorageClassUpdated. |
| `--schedule-repeats` | one of: daily, weekly | daily | Sets how often the inventory report configuration will run. Defaults to DAILY. FREQUENCY must be one of: daily, weekly. |
| `--schedule-repeats-until` | END_DATE |  | Sets date after which you want to stop generating inventory reports. For example, 2022-03-30. Defaults to one year from --schedule-starts value. |
| `--schedule-starts` | START_DATE |  | Sets the date you want to start generating inventory reports. For example, 2022-01-30. Should be tomorrow or later based on UTC timezone. Defaults to tomorrow. |


**Examples:**
```bash
To create an inventory report about "my-bucket" that will store report
details in "report-bucket" with the prefix "save-path/".

    $ gcloud storage insights inventory-reports create gs://my-bucket \
        --destination=gs://report-bucket/save-path/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/create)

---
### `gcloud storage insights inventory-reports delete`

Delete an inventory report config

Delete an inventory report config.

**Synopsis:**
```
gcloud storage insights inventory-reports delete
    (REPORT_CONFIG : --location=LOCATION) [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Report config resource - The Report config to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument report_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPORT_CONFIG
     ID of the report-config or fully qualified identifier for the
     report-config.

     To set the report-config attribute:
     + provide the argument report_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the report-config.

     To set the location attribute:
     + provide the argument report_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set, all report details for this report config will be deleted. |


**Examples:**
```bash
To delete an inventory report config with ID=1234, location=us-central1 and
project=foo:

    $ gcloud storage insights inventory-reports delete 1234 \
        --location=us-central1 --project=foo

To delete the same inventory report config with fully specified name:

    $ gcloud storage insights inventory-reports delete \
        /projects/foo/locations/us-central1/reportConfigs/1234

To delete the report config with all generated report details:

    $ gcloud storage insights inventory-reports delete \
        /projects/foo/locations/us-central1/reportConfigs/1234 --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/delete)

---
### `gcloud storage insights inventory-reports describe`

Describe an inventory report config

Describe an inventory report config.

**Synopsis:**
```
gcloud storage insights inventory-reports describe
    (REPORT_CONFIG : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Report config resource - The Report config to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument report_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPORT_CONFIG
     ID of the report-config or fully qualified identifier for the
     report-config.

     To set the report-config attribute:
     + provide the argument report_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the report-config.

     To set the location attribute:
     + provide the argument report_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an inventory report config with ID=1234, location=us-central1,
and project=foo:

    $ gcloud storage insights inventory-reports describe 1234 \
        --location=us-central1 --project=foo

To describe the same inventory report config with fully specified name:

    $ gcloud storage insights inventory-reports describe \
        /projects/foo/locations/us-central1/reportConfigs/1234

Describe the same inventory report config with JSON formatting, only
returning the "displayName" field:

    $ gcloud storage insights inventory-reports describe \
        /projects/foo/locations/us-central1/reportConfigs/1234 \
        --format="json(displayName)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/describe)

---
### `gcloud storage insights inventory-reports list`

Lists all inventory report configs

List Cloud Storage inventory report configs.

**Synopsis:**
```
gcloud storage insights inventory-reports list [--location=LOCATION]
    [--source=SOURCE_BUCKET_URL] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location of the report configs. |
| `--source` | SOURCE_BUCKET_URL |  | Specifies URL of the source bucket that contains the inventory report configuration. |


**Examples:**
```bash
List all inventory report configs in the source bucket "my-bucket":

    $ gcloud storage insights inventory-reports list \
        --source=gs://my-bucket

List buckets with JSON formatting, only returning the "displayName" field:

    $ gcloud storage insights inventory-reports list \
        --source=gs://my-bucket --format="json(displayName)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/list)

---
### `gcloud storage insights inventory-reports update`

Update an inventory report config

Update an inventory report config.

**Synopsis:**
```
gcloud storage insights inventory-reports update
    (REPORT_CONFIG : --location=LOCATION) [--destination=DESTINATION_URL]
    [--display-name=DISPLAY_NAME] [--schedule-repeats=FREQUENCY]
    [--schedule-repeats-until=END_DATE] [--schedule-starts=START_DATE]
    [--metadata-fields=[METADATA_FIELDS,...]
      | --add-metadata-fields=[METADATA_FIELDS,...]
      --remove-metadata-fields=[METADATA_FIELDS,...]]
    [--parquet | --csv-delimiter=DELIMITER
      --[no-]csv-header --csv-separator=SEPARATOR] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Report config resource - The Report config to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument report_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPORT_CONFIG
     ID of the report-config or fully qualified identifier for the
     report-config.

     To set the report-config attribute:
     + provide the argument report_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the report-config.

     To set the location attribute:
     + provide the argument report_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION_URL |  | Sets the URL of the destination bucket and path where generated reports are stored. |
| `--display-name` | DISPLAY_NAME |  | Sets the editable name of the report configuration. |
| `--schedule-repeats` | one of: daily, weekly |  | Sets how often the inventory report configuration will run. FREQUENCY must be one of: daily, weekly. |
| `--schedule-repeats-until` | END_DATE |  | Sets date after which you want to stop generating inventory reports. For example, 2022-03-30. |
| `--schedule-starts` | START_DATE |  | Sets the date you want to start generating inventory reports. For example, 2022-01-30. Should be tomorrow or later based on UTC timezone. |


**Examples:**
```bash
To update the display-name of an inventory report config with ID=1234,
location=us-central1, and project=foo:

    $ gcloud storage insights inventory-reports update 1234 \
        --location=us-central1 --project=foo --display-name=bar

To update the same inventory report config with fully specified name:

    $ gcloud storage insights inventory-reports update \
        /projects/foo/locations/us-central1/reportConfigs/1234 \
        --display-name=bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/update)

---

## `gcloud storage insights inventory-reports details` — retrieve details of inventory reports
### `gcloud storage insights inventory-reports details describe`

Describe inventory reports detail

Describe the inventory report detail.

**Synopsis:**
```
gcloud storage insights inventory-reports details describe
    (REPORT_DETAIL : --location=LOCATION --report-config=REPORT_CONFIG)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Report detail resource - The report detail to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument report_detail on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPORT_DETAIL
     ID of the report-detail or fully qualified identifier for the
     report-detail.

     To set the report-detail attribute:
     + provide the argument report_detail on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the report-detail.

     To set the location attribute:
     + provide the argument report_detail on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --report-config=REPORT_CONFIG
     Report Config ID for the report-detail.

     To set the report-config attribute:
     + provide the argument report_detail on the command line with a
       fully specified name;
     + provide the argument --report-config on the command line.
```

**Examples:**
```bash
To describe an inventory report detail with ID=4568, location=us-central1,
project=foo, and report config ID=1234:

    $ gcloud storage insights inventory-reports details describe 1234 \
        --location=us-central1 --project=foo --report-config=1234

To describe the same inventory report detail with fully specified name:

    $ gcloud storage insights inventory-reports details describe \
        /projects/foo/locations/us-central1/reportConfigs/1234/\
    reportDetails/5678

To describe the same inventory report detail with JSON formatting, only
returning the "status" field:

    $ gcloud storage insights inventory-reports details describe \
        /projects/foo/locations/us-central1/reportConfigs/1234/\
    reportDetails/5678 --format="json(status)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/details/describe)

---
### `gcloud storage insights inventory-reports details list`

List inventory report details

List all inventory report details generated by a given inventory report
config.

**Synopsis:**
```
gcloud storage insights inventory-reports details list
    (REPORT_CONFIG : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Report config resource - The Report config for which the report details
should be listed. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument report_config on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REPORT_CONFIG
     ID of the report-config or fully qualified identifier for the
     report-config.

     To set the report-config attribute:
     + provide the argument report_config on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the report-config.

     To set the location attribute:
     + provide the argument report_config on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To list all inventory report details for report config ID=1234,
location=us-central1, and project=foo:

    $ gcloud storage insights inventory-reports details list 1234 \
        --location=us-central1 --project=foo

To list all the same inventory report details with fully specified name of
the report config:

    $ gcloud storage insights inventory-reports details list \
        /projects/foo/locations/us-central1/reportConfigs/1234

To list all inventory reports, only returning the "status" key:

    $ gcloud storage insights inventory-reports details list \
        projects/a/locations/b/reportConfigs/some-id \
        --format="json(status)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/insights/inventory-reports/details/list)

---
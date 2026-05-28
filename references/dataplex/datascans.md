# gcloud dataplex datascans

manage Dataplex Datascan

### `gcloud dataplex datascans delete`

Delete a Dataplex Datascan resource

Delete a Dataplex Datascan resource.

**Synopsis:**
```
gcloud dataplex datascans delete (DATASCAN : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex Datascan
you want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the datascan attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Dataplex Datascan test-datascan in location us-central1, run:

    $ gcloud dataplex datascans delete test-datascan \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/delete)

---
### `gcloud dataplex datascans describe`

Describe a Dataplex datascan resource

Displays all details of a Dataplex Datascan resource given a valid Datascan
ID.

**Synopsis:**
```
gcloud dataplex datascans describe (DATASCAN : --location=LOCATION)
    [--view=VIEW] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex Datascan
you want to retrieve. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the datascan attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: basic Does not include spec data in response |  | Displays spec data based on the argument value. The default view is 'basic'. VIEW must be one of: basic Does not include spec data in response. full Includes spec data in response. |


**Examples:**
```bash
To describe a Dataplex Datascan test-datascan in project test-project
location us-central1 , run:

    $ gcloud dataplex datascans describe test-datascan \
      --project=test-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/describe)

---
### `gcloud dataplex datascans get-iam-policy`

Get the IAM policy for a Dataplex datascan resource

Displays the IAM policy associated with a Dataplex datascan resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex datascans get-iam-policy (DATASCAN : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
IAM policy you want to retrieve. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the datascan attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To print the IAM policy for Dataplex datascan test-datascan in location
us-central1, run:

    $ gcloud dataplex datascans get-iam-policy test-datascan \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/get-iam-policy)

---
### `gcloud dataplex datascans list`

List Dataplex Datascan resources under a project

List all Dataplex Datascan resource under a specific project and location.

**Synopsis:**
```
gcloud dataplex datascans list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all Dataplex Datascan resources in project=test-project in location
us-central, run:

    $ gcloud dataplex datascans list --project=test-project \
      --location=us-central1

To list all Dataplex Datascan in all locations, run:

    $ gcloud dataplex datascans list --project=test-project --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/list)

---
### `gcloud dataplex datascans run`

Run a Dataplex DataScan resource

Run a Dataplex Datascan resource given a valid Datascan ID.

**Synopsis:**
```
gcloud dataplex datascans run (DATASCAN : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex Datascan
you want to run. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the datascan attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To run a Dataplex Datascan test-datascan in location us-central1 , run:

    $ gcloud dataplex datascans run test-datascan --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/run)

---
### `gcloud dataplex datascans set-iam-policy`

Set the IAM policy to a Dataplex datascan as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex datascans set-iam-policy (DATASCAN : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to set IAM policy binding to. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
policy.son and set it for the Dataplex datascan test-datascan defined in
location us-central1:

    $ gcloud dataplex datascans set-iam-policy --location=us-central1 \
        test-datascan policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/set-iam-policy)

---

## `gcloud dataplex datascans create` — manage Dataplex Datascans creation
### `gcloud dataplex datascans create data-discovery`

Create a Dataplex data discovery scan job

Allows users to auto discover BigQuery External and BigLake tables from
underlying Cloud Storage buckets.

**Synopsis:**
```
gcloud dataplex datascans create data-discovery
    (DATASCAN : --location=LOCATION)
    --data-source-resource=DATA_SOURCE_RESOURCE [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--async | --validate-only]
    [--bigquery-publishing-connection=BIGQUERY_PUBLISHING_CONNECTION
      --bigquery-publishing-dataset-location=BIGQUERY_PUBLISHING_DATASET_LOCATION --bigquery-publishing-dataset-project=BIGQUERY_PUBLISHING_DATASET_PROJECT --bigquery-publishing-table-type=BIGQUERY_PUBLISHING_TABLE_TYPE --storage-exclude-patterns=[PATTERN,
      ...] --storage-include-patterns=[PATTERN,...]
      --csv-delimiter=CSV_DELIMITER
      --csv-disable-type-inference=CSV_DISABLE_TYPE_INFERENCE
      --csv-encoding=CSV_ENCODING
      --csv-header-row-count=CSV_HEADER_ROW_COUNT
      --csv-quote-character=CSV_QUOTE_CHARACTER
      --json-disable-type-inference=JSON_DISABLE_TYPE_INFERENCE
      --json-encoding=JSON_ENCODING]
    [--on-demand=ON_DEMAND | --schedule=SCHEDULE
      | --one-time --ttl-after-scan-completion=TTL_AFTER_SCAN_COMPLETION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to create a data discovery scan for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-source-resource` | DATA_SOURCE_RESOURCE |  | Fully-qualified service resource name of the cloud resource bucket that contains the data for the data discovery scan, of the form: //storage.googleapis.com/projects/{project_id_or_number}/buckets/{bucket_id}. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data discovery scan. |
| `--display-name` | DISPLAY_NAME |  | Display name of the data discovery scan. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a data discovery scan data-discovery-datascan in project
test-project located in us-central1 on Cloud Storage bucket test-bucket,
run:

    $ gcloud dataplex datascans create data-discovery \
        data-discovery-datascan --project=test-project \
        --location=us-central1 \
        --data-source-resource="//storage.googleapis.com/projects/test-p\
    roject/buckets/test-bucket"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/create/data-discovery)

---
### `gcloud dataplex datascans create data-documentation`

Create a Dataplex data documentation scan job

Allows users to generate documentation for Dataplex BigQuery tables.

**Synopsis:**
```
gcloud dataplex datascans create data-documentation
    (DATASCAN : --location=LOCATION)
    (--data-source-entity=DATA_SOURCE_ENTITY
      | --data-source-resource=DATA_SOURCE_RESOURCE)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [--on-demand=ON_DEMAND | --schedule=SCHEDULE
      | --one-time --ttl-after-scan-completion=TTL_AFTER_SCAN_COMPLETION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to create a data documentation scan for. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-source-entity` | DATA_SOURCE_ENTITY |  | _[Exactly one of these must be specified:]_ The Dataplex entity that contains the data for the data documentation scan, of the form: projects/{project_id_or_number}/locations/{location_id}/lakes/{lake_id}/zones/{zone_id}/entities/{entity_id}. Currently only BigQuery table is supported. |
| `--data-source-resource` | DATA_SOURCE_RESOURCE |  | _[Exactly one of these must be specified:]_ Fully-qualified service resource name of the cloud resource that contains the data for the data documentation scan, of the form: //bigquery.{universe_domain}/projects/{project_id_or_number}/datasets/{dataset_id}/tables/{table_id}. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data documentation scan. |
| `--display-name` | DISPLAY_NAME |  | Display name of the data documentation scan. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a data documentation scan data-documentation-datascan in project
test-project located in us-central1 on entity test-entity, run:

    $ gcloud dataplex datascans create data-documentation \
        data-documentation-datascan --project=test-project \
        --location=us-central1 \
        --data-source-resource="//bigquery.{universe_domain}/projects/te\
    st-project/datasets/test-dataset/tables/test-table"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/create/data-documentation)

---
### `gcloud dataplex datascans create data-profile`

Create a Dataplex data profile scan job

Represents a user-visible job which provides the insights for the related
data source about the structure, content and relationships (such as null
percent, cardinality, min/max/mean, etc).

**Synopsis:**
```
gcloud dataplex datascans create data-profile
    (DATASCAN : --location=LOCATION)
    (--data-source-entity=DATA_SOURCE_ENTITY
      | --data-source-resource=DATA_SOURCE_RESOURCE)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [--data-profile-spec-file=DATA_PROFILE_SPEC_FILE
      | --enable-catalog-publishing
      --exclude-field-names=EXCLUDE_FIELD_NAMES
      --export-results-table=EXPORT_RESULTS_TABLE
      --include-field-names=INCLUDE_FIELD_NAMES
      --row-filter=ROW_FILTER --sampling-percent=SAMPLING_PERCENT]
    [--incremental-field=INCREMENTAL_FIELD --on-demand=ON_DEMAND
      | --schedule=SCHEDULE
      | --one-time --ttl-after-scan-completion=TTL_AFTER_SCAN_COMPLETION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to create a data profile scan for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-source-entity` | DATA_SOURCE_ENTITY |  | _[Exactly one of these must be specified:]_ Dataplex entity that contains the data for the data profile scan, of the form: projects/{project_number}/locations/{location_id}/lakes/{lake_id}/zones/{zone_id}/entities/{entity_id}. |
| `--data-source-resource` | DATA_SOURCE_RESOURCE |  | _[Exactly one of these must be specified:]_ Fully-qualified service resource name of the cloud resource that contains the data for the data profile scan, of the form: //bigquery.googleapis.com/projects/{project_number}/datasets/{dataset_id}/tables/{table_id}. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data profile scan. |
| `--display-name` | DISPLAY_NAME |  | Display name of the data profile scan. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a data profile scan data-profile-datascan in project test-project
located in us-central1 on bigquery resource table test-table in dataset
test-dataset, run:

    $ gcloud dataplex datascans create data-profile \
        data-profile-datascan --project=test-project \
        --location=us-central1 \
        --data-source-resource="//bigquery.googleapis.com/projects/test-\
    project/datasets/test-dataset/tables/test-table"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/create/data-profile)

---
### `gcloud dataplex datascans create data-quality`

Create a Dataplex data quality scan job

Represents a user-visible job which provides the insights for the related
data source and generates queries based on the rules and runs against the
data to get data quality check results.

**Synopsis:**
```
gcloud dataplex datascans create data-quality
    (DATASCAN : --location=LOCATION)
    --data-quality-spec-file=DATA_QUALITY_SPEC_FILE
    (--data-source-entity=DATA_SOURCE_ENTITY
      | --data-source-resource=DATA_SOURCE_RESOURCE)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [--incremental-field=INCREMENTAL_FIELD --on-demand=ON_DEMAND
      | --schedule=SCHEDULE
      | --one-time --ttl-after-scan-completion=TTL_AFTER_SCAN_COMPLETION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to create a data quality scan for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-quality-spec-file` | DATA_QUALITY_SPEC_FILE |  | Path to the JSON/YAML file containing the spec for the data quality scan. The JSON representation reference: https://cloud.google.com/dataplex/docs/reference/rest/v1/DataQualitySpec The YAML representation reference: https://cloud.google.com/dataplex/docs/use-auto-data-quality#create-scan-using-gcloud |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data quality scan. |
| `--display-name` | DISPLAY_NAME |  | Display name of the data quality scan. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a data quality scan data-quality-datascan in project test-project
located in us-central1 on bigquery resource table test-table in dataset
test-dataset with data spec file data-quality-spec.json, run:

    $ gcloud dataplex datascans create data-quality \
        data-quality-datascan --project=test-project \
        --location=us-central1 \
        --data-source-resource="//bigquery.googleapis.com/projects/test-\
    project/datasets/test-dataset/tables/test-table" \
        --data-quality-spec-file="data-quality-spec.json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/create/data-quality)

---

## `gcloud dataplex datascans jobs` — manage Dataplex Datascan Jobs service
### `gcloud dataplex datascans jobs describe`

Describe a Dataplex datascan job

Describe a Dataplex datascan job.

Displays all details of a Dataplex job given a valid job ID.

**Synopsis:**
```
gcloud dataplex datascans jobs describe
    (JOB : --datascan=DATASCAN --location=LOCATION) [--view=VIEW]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Arguments and flags that define the Dataplex Job running a
particular Datascan you want to retrieve. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --datascan=DATASCAN
     Datascan ID of the Dataplex datascan resource.

     To set the datascan attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --datascan on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: basic Does not include spec and result data in response |  | Displays spec and result data based on the argument value. The default view is 'basic'. VIEW must be one of: basic Does not include spec and result data in response. full Includes spec and result data in response. |


**Examples:**
```bash
To describe a Dataplex job test-job running a datascan test-datascan in
location us-central1, run:

    $ gcloud dataplex datascans jobs describe test-job \
        --location=us-central1 --datascan=test-datascan

To describe the details of Dataplex job test-job running a datascan
test-datascan in location us-central1, run:

    $ gcloud dataplex datascans jobs describe test-job \
        --location=us-central1 --datascan=test-datascan --view=FULL
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/jobs/describe)

---
### `gcloud dataplex datascans jobs list`

List job runs of a Dataplex datascan resource

List Jobs runs of a Datascan under a specific project, location and task.

**Synopsis:**
```
gcloud dataplex datascans jobs list
    (--datascan=DATASCAN : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--datascan` | DATASCAN |  | _[This must be specified.]_ ID of the datascan or fully qualified identifier for the datascan. To set the datascan attribute: + provide the argument --datascan on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --datascan on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all the Dataplex job runs for a datascan test-datascan in location
us-central1, run:

    gcloud dataplex datascans jobs list --location=us-central1 --datascan=test-datascan
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/jobs/list)

---

## `gcloud dataplex datascans update` — manage Dataplex Datascans updation
### `gcloud dataplex datascans update data-discovery`

Update a Dataplex data discovery scan job

Allows users to auto discover BigQuery External and BigLake tables from
underlying Cloud Storage buckets.

**Synopsis:**
```
gcloud dataplex datascans update data-discovery
    (DATASCAN : --location=LOCATION) [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--async | --validate-only]
    [--bigquery-publishing-connection=BIGQUERY_PUBLISHING_CONNECTION
      --bigquery-publishing-dataset-location=BIGQUERY_PUBLISHING_DATASET_LOCATION --bigquery-publishing-dataset-project=BIGQUERY_PUBLISHING_DATASET_PROJECT --bigquery-publishing-table-type=BIGQUERY_PUBLISHING_TABLE_TYPE --storage-exclude-patterns=[PATTERN,
      ...] --storage-include-patterns=[PATTERN,...]
      --csv-delimiter=CSV_DELIMITER
      --csv-disable-type-inference=CSV_DISABLE_TYPE_INFERENCE
      --csv-encoding=CSV_ENCODING
      --csv-header-row-count=CSV_HEADER_ROW_COUNT
      --csv-quote-character=CSV_QUOTE_CHARACTER
      --json-disable-type-inference=JSON_DISABLE_TYPE_INFERENCE
      --json-encoding=JSON_ENCODING]
    [--on-demand=ON_DEMAND | --schedule=SCHEDULE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to update a data discovery scan for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data discovery scan |
| `--display-name` | DISPLAY_NAME |  | Display name of the data discovery scan |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update description of a data discovery scan data-discovery-datascan in
project test-project located in us-central1, run:

    $ gcloud dataplex datascans update data-discovery \
        data-discovery-datascan --project=test-project \
        --location=us-central1 --description="Description is updated."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/update/data-discovery)

---
### `gcloud dataplex datascans update data-documentation`

Update a Dataplex data documentation scan job

Update a Dataplex data documentation scan job.

**Synopsis:**
```
gcloud dataplex datascans update data-documentation
    (DATASCAN : --location=LOCATION) [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--async | --validate-only]
    [--on-demand=ON_DEMAND | --schedule=SCHEDULE
      | --one-time --ttl-after-scan-completion=TTL_AFTER_SCAN_COMPLETION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to update a data documentation scan for. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data documentation scan. |
| `--display-name` | DISPLAY_NAME |  | Display name of the data documentation scan. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a data documentation scan data-documentation-datascan in project
test-project located in us-central1 with a new description, run:

    $ gcloud dataplex datascans update data-documentation \
        data-documentation-datascan --project=test-project \
        --location=us-central1 --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/update/data-documentation)

---
### `gcloud dataplex datascans update data-profile`

Update a Dataplex data profile scan job

Represents a user-visible job which provides the insights for the related
data source about the structure, content and relationships (such as null
percent, cardinality, min/max/mean, etc).

**Synopsis:**
```
gcloud dataplex datascans update data-profile
    (DATASCAN : --location=LOCATION) [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--async | --validate-only]
    [--data-profile-spec-file=DATA_PROFILE_SPEC_FILE
      | --enable-catalog-publishing
      --exclude-field-names=EXCLUDE_FIELD_NAMES
      --include-field-names=INCLUDE_FIELD_NAMES
      --row-filter=ROW_FILTER --sampling-percent=SAMPLING_PERCENT]
    [--on-demand=ON_DEMAND | --schedule=SCHEDULE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to update a data profile scan for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the data profile scan |
| `--display-name` | DISPLAY_NAME |  | Display name of the data profile scan |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update description of a data profile scan data-profile-datascan in
project test-project located in us-central1, run:

    $ gcloud dataplex datascans update data-profile \
        data-profile-datascan --project=test-project \
        --location=us-central1 --description="Description is updated."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/update/data-profile)

---
### `gcloud dataplex datascans update data-quality`

Update a Dataplex data quality scan job

Represents a user-visible job which provides the insights for the related
data source and generates queries based on the rules and runs against the
data to get data quality check results.

**Synopsis:**
```
gcloud dataplex datascans update data-quality
    (DATASCAN : --location=LOCATION)
    [--data-quality-spec-file=DATA_QUALITY_SPEC_FILE]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [--on-demand=ON_DEMAND | --schedule=SCHEDULE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Datascan resource - Arguments and flags that define the Dataplex datascan
you want to update a data quality scan for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument datascan on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASCAN
     ID of the datascan or fully qualified identifier for the datascan.

     To set the dataScans attribute:
     + provide the argument datascan on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument datascan on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-quality-spec-file` | DATA_QUALITY_SPEC_FILE |  | Path to the JSON/YAML file containing the spec for the data quality scan. The JSON representation reference: https://cloud.google.com/dataplex/docs/reference/rest/v1/DataQualitySpec The YAML representation reference: https://cloud.google.com/dataplex/docs/use-auto-data-quality#create-scan-using-gcloud |
| `--description` | DESCRIPTION |  | Description of the data quality scan |
| `--display-name` | DISPLAY_NAME |  | Display name of the data quality scan |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update description of a data quality scan data-quality-datascan in
project test-project located in us-central1, run:

    $ gcloud dataplex datascans update data-quality \
        data-quality-datascan --project=test-project \
        --location=us-central1 --description="Description is updated."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/datascans/update/data-quality)

---
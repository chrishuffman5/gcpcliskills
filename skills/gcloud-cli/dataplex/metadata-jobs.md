# gcloud dataplex metadata-jobs

manage Dataplex metadata jobs

### `gcloud dataplex metadata-jobs cancel`

Cancel a Metadata Job run

Cancels an existing Metadata Job run.

**Synopsis:**
```
gcloud dataplex metadata-jobs cancel (METADATA_JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Metadata job resource - Arguments and flags that define the Dataplex
metadata job you want to cancel. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument metadata_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  METADATA_JOB
     ID of the metadata job or fully qualified identifier for the metadata
     job.

     To set the metadata_job attribute:
     + provide the argument metadata_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument metadata_job on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To cancel a Dataplex Metadata Job run test-metadata-job within location
us-central1 and in project test-project

    $ gcloud dataplex metadata-jobs cancel test-metadata-job \
       --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/metadata-jobs/cancel)

---
### `gcloud dataplex metadata-jobs create`

Create a Dataplex Metadata Job

A metadata job represents a long running job on Dataplex Catalog metadata
entries. Some operations include importing and exporting metadata into
entry groups through the usage of entry types and aspect types.

The Metadata Job ID will be used to identify each configuration run. The
Metadata Job id must follow these rules:
  o Must contain only lowercase letters, numbers, and hyphens.
  o Must start with a letter.
  o Must end with a number or a letter.
  o Must be between 1-63 characters.
  o Must be unique within the customer project / location.

**Synopsis:**
```
gcloud dataplex metadata-jobs create [[METADATA_JOB] --location=LOCATION]
    --type=TYPE
    (--export-output-path=EXPORT_OUTPUT_PATH
      ((--export-entry-groups=[EXPORT_ENTRY_GROUPS,...]
      | --export-organization-level=EXPORT_ORGANIZATION_LEVEL
      | --export-projects=[EXPORT_PROJECTS,...])
      : --export-aspect-types=[EXPORT_ASPECT_TYPES,...]
      --export-entry-types=[EXPORT_ENTRY_TYPES,...])
      | [--import-aspect-sync-mode=IMPORT_ASPECT_SYNC_MODE
      --import-entry-sync-mode=IMPORT_ENTRY_SYNC_MODE
      --import-source-storage-uri=IMPORT_SOURCE_STORAGE_URI
      (--import-aspect-types=[IMPORT_ASPECT_TYPES,...]
      --import-entry-groups=[IMPORT_ENTRY_GROUPS,...]
      --import-entry-link-types=[IMPORT_ENTRY_LINK_TYPES,...]
      --import-entry-types=[IMPORT_ENTRY_TYPES,...]
      --import-glossaries=[IMPORT_GLOSSARIES,...]
      --import-referenced-entry-scopes=[IMPORT_REFERENCED_ENTRY_SCOPES,
      ...]) : --import-log-level=IMPORT_LOG_LEVEL
      --import-source-create-time=IMPORT_SOURCE_CREATE_TIME]) [--async]
    [--labels=[KEY=VALUE,...]] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Metadata job resource - Arguments and flags that define the Dataplex
metdata job you want to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument metadata_job on the command line with a fully
   specified name;
 * job ID is optional and will be generated if not specified with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [METADATA_JOB]
     ID of the metadata job or fully qualified identifier for the metadata
     job.

     To set the metadata_job attribute:
     + provide the argument metadata_job on the command line;
     + job ID is optional and will be generated if not specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument metadata_job on the command line with a
       fully specified name;
     + job ID is optional and will be generated if not specified with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: EXPORT A Metadata Export Job will export entries and aspects from the declared Dataplex scope to the specified Cloud Storage location |  | Type. TYPE must be one of: EXPORT A Metadata Export Job will export entries and aspects from the declared Dataplex scope to the specified Cloud Storage location. IMPORT A Metadata Import Job will ingest, update, or delete entries and aspects into the declared Dataplex entry group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | Validate the create action, but don't actually perform it. |


**Examples:**
```bash
To create a Dataplex Metadata Job with type IMPORT and name my-metadata-job
in location us-central1 with additional parameters, run:

    $ gcloud dataplex metadata-jobs create my-metadata-job \
        --location=us-central --project=test-project --type=import \
        --import-source-storage-uri=gs://test-storage/ \
        --import-source-create-time="2019-01-23T12:34:56.123456789Z" \
        --import-entry-sync-mode=FULL \
        --import-aspect-sync-mode=INCREMENTAL \
        --import-log-level="debug" \
        --import-entry-groups=projects/test-project/locations/\
    us-central1/entryGroups/eg1 \
        --import-entry-types="projects/test-project/locations/us-central\
    1/entryTypes/et1", \
        "projects/test-project/locations/us-central1/entryTypes/et2" \
        --import-aspect-types="projects/test-project/locations/us-centra\
    l1/aspectTypes/at1", \
        "projects/test-project/locations/us-central1/aspectTypes/at2"

To create a Dataplex Metadata Job with type EXPORT and name my-metadata-job
in location us-central1 with additional parameters, run:

    $ gcloud dataplex metadata-jobs create my-metadata-job \
        --location=us-central --project=test-project --type=export \
        --export-output-path=gs://test-storage/ \
        --export-entry-groups=projects/test-project/locations/\
    us-central1/entryGroups/eg1 \
        --export-entry-types="projects/test-project/locations/us-central\
    1/entryTypes/et1", \
        "projects/test-project/locations/us-central1/entryTypes/et2" \
        --export-aspect-types="projects/test-project/locations/us-centra\
    l1/aspectTypes/at1", \
        "projects/test-project/locations/us-central1/aspectTypes/at2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/metadata-jobs/create)

---
### `gcloud dataplex metadata-jobs describe`

Describe a Metadata Job

Displays all details of a Dataplex Metadata Job given a valid Metadata Job
ID.

**Synopsis:**
```
gcloud dataplex metadata-jobs describe (METADATA_JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Metadata job resource - Arguments and flags that define the Dataplex
metadata job you want to retrieve. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument metadata_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  METADATA_JOB
     ID of the metadata job or fully qualified identifier for the metadata
     job.

     To set the metadata_job attribute:
     + provide the argument metadata_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument metadata_job on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex Metadata Job test-metadata-job within location
us-central1 and in project test-project

    $ gcloud dataplex metadata-jobs describe test-metadata-job \
       --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/metadata-jobs/describe)

---
### `gcloud dataplex metadata-jobs list`

List Metadata Job resources under a project

List all Metadata Job resource under a specific project and location.

**Synopsis:**
```
gcloud dataplex metadata-jobs list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To List Metadata Jobs in project test-dataplex at location us-central1

    $ gcloud dataplex metadata-jobs list --location=us-central1 \
      --project=test-dataplex
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/metadata-jobs/list)

---
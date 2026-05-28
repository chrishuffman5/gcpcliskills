# gcloud backup-dr data-source-references

command group for Backup and DR Data Source References

### `gcloud backup-dr data-source-references describe`

Show details of the data source reference

Show all configuration data source associated with the specified data
source reference.

**Synopsis:**
```
gcloud backup-dr data-source-references describe
    (DATA_SOURCE_REFERENCE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Data source reference resource - Name of the data source reference to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument data_source_reference on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATA_SOURCE_REFERENCE
     ID of the data_source_reference or fully qualified identifier for the
     data_source_reference.

     To set the data_source_reference attribute:
     + provide the argument data_source_reference on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument data_source_reference on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for data source 'DATA_SOURCE_REFERENCE', run:

    $ gcloud backup-dr data-source-references describe \
        DATA_SOURCE_REFERENCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/data-source-references/describe)

---
### `gcloud backup-dr data-source-references fetch-for-resource-type`

Fetch Data Source References for a given resource type and location

Fetch Data Source References for a given resource type and location. Show
all configuration data associated with the specified data source reference.

**Synopsis:**
```
gcloud backup-dr data-source-references fetch-for-resource-type
    RESOURCE_TYPE --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_TYPE
   Resource type for which data source references should be fetched.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location for which data source references should be fetched. |


**Examples:**
```bash
To list data source references for Cloud SQL with location us-central1 in
project test-project, run:

    $ gcloud backup-dr data-source-references fetch-for-resource-type \
        sqladmin.googleapis.com/Instance --location="us-central1" \
        --project="test-project"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/data-source-references/fetch-for-resource-type)

---
### `gcloud backup-dr data-source-references list`

List Backup and DR data source references

List Backup and DR data source references.

**Synopsis:**
```
gcloud backup-dr data-source-references list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list data source references in all locations, run:

    $ gcloud backup-dr data-source-references list

To list data source references in a location 'my-location', run:

    $ gcloud backup-dr data-source-references list --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/data-source-references/list)

---
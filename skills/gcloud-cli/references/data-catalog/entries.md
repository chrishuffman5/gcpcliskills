# gcloud data-catalog entries

manage entries in Data Catalog

### `gcloud data-catalog entries create`

Create a Data Catalog entry

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead.

Create a Data Catalog entry.

**Synopsis:**
```
gcloud data-catalog entries create
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    ([--type=TYPE : --gcs-file-patterns=[GCS_FILE_PATTERNS,...]]
      | --user-specified-system=USER_SPECIFIED_SYSTEM
      ([--user-specified-type=USER_SPECIFIED_TYPE
      : --linked-resource=LINKED_RESOURCE
      --source-system-create-time=SOURCE_SYSTEM_CREATE_TIME
      --source-system-update-time=SOURCE_SYSTEM_UPDATE_TIME]))
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--fully-qualified-name=FULLY_QUALIFIED_NAME]
    [--schema=[COLUMN_NAME=COLUMN_TYPE,...]
      | --schema-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to create. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group of the entry.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: cluster, dashboard, database, database-schema, data-source-connection, data-stream, entry-type-unspecified, explore, feature-group, feature-online-store, feature-view, fileset, graph, lake, look, model, routine, service, table, zone |  | _[pattern must be specified.]_ Type of the entry. TYPE must be one of: cluster, dashboard, database, database-schema, data-source-connection, data-stream, entry-type-unspecified, explore, feature-group, feature-online-store, feature-view, fileset, graph, lake, look, model, routine, service, table, zone. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--gcs-file-patterns` | [GCS_FILE_PATTERNS,...] |  | _[pattern must be specified.]_ Patterns to identify a set of files in Google Cloud Storage. A star (*) may be used at the end of a pattern to match arbitrary files beginning with that pattern. Examples of valid file patterns: - gs://bucket_name/* - Matches all files in 'bucket_name'. - gs://bucket_name/file* - Matches files prefixed by 'file' in 'bucket_name'. - gs://another_bucket/a.txt - Matches 'gs://another_bucket/a.txt'. |
| `--user-specified-system` | USER_SPECIFIED_SYSTEM |  | _[pattern must be specified.]_ External system from which the entry is fed. If --type is not used, then --user-specified-system must be provided. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--user-specified-system` |  |  | _[For externally ingested resources, --user-specified-type and]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Textual description of the entry. |
| `--display-name` | DISPLAY_NAME |  | Human-readable name for the entry. |
| `--fully-qualified-name` | FULLY_QUALIFIED_NAME |  | Fully qualified name of the resource. |


**Examples:**
```bash
To create an entry for a Google Cloud Storage fileset, run:

    $ gcloud data-catalog entries create entry1 --location=us-central1 \
        --entry-group=group1 \
        --gcs-file-patterns="gs://bucket1/abc/*,gs://bucket1/file1" \
        --display-name="analytics data" --type=FILESET

To create an entry for a Google Cloud Storage fileset with an inline
schema, run:

    $ gcloud data-catalog entries create entry1 --location=us-central1 \
        --entry-group=group1 --gcs-file-patterns="gs://bucket1/*" \
        --display-name="sales data" \
        --schema="qtr=STRING,sales=FLOAT,year=STRING"

To create an entry for a resource of a custom type, run:

    $ gcloud data-catalog entries create entry1 --location=us-central1 \
        --entry-group=group1 --display-name="sales data" \
        --linked-resource="www.resource.com" \
        --user-specified-type="type_name" \
        --user-specified-system="system_name"

To create an entry for a Google Cloud Storage fileset with a schema from a
file, run:

    $ gcloud data-catalog entries create entry1 --location=us-central1 \
        --entry-group=group1 --gcs-file-patterns="gs://bucket1/*" \
        --display-name="sales data" \
        --schema-from-file=/tmp/schema.json --type=FILESET
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/create)

---
### `gcloud data-catalog entries delete`

Delete a Data Catalog entry

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead.

Delete a Data Catalog entry.

**Synopsis:**
```
gcloud data-catalog entries delete
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to delete. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group of the entry.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete the entry 'entry1' in the group 'group1', run:

    $ gcloud data-catalog entries delete entry1 --entry-group=group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/delete)

---
### `gcloud data-catalog entries describe`

Describe a Data Catalog entry

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead.

Describe a Data Catalog entry.

**Synopsis:**
```
gcloud data-catalog entries describe
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group of the entry.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the entry 'entry1' in the group 'group1', run:

    $ gcloud data-catalog entries describe entry1 --entry-group=group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/describe)

---
### `gcloud data-catalog entries list`

List all entries in a Data Catalog entry group

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead.

List all entries in a Data Catalog entry group.

**Synopsis:**
```
gcloud data-catalog entries list
    (--entry-group=ENTRY_GROUP : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--entry-group` | ENTRY_GROUP |  | _[This must be specified.]_ ID of the entry group or fully qualified identifier for the entry group. To set the entry-group attribute: + provide the argument --entry-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the entry group. To set the location attribute: + provide the argument --entry-group on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all entry in the group 'group1', run:

    $ gcloud data-catalog entries list --entry-group=group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/list)

---
### `gcloud data-catalog entries lookup`

Lookup a Data Catalog entry by its target name

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead.

Lookup a Data Catalog entry by its target name.

**Synopsis:**
```
gcloud data-catalog entries lookup RESOURCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE
   The name of the target resource to lookup. This can be either the
   Google Cloud Platform resource name or the SQL name of a Google Cloud
   Platform resource. SQL names follow Standard SQL lexical structure:
   https://cloud.google.com/bigquery/docs/reference/standard-sql/lexical
```

**Examples:**
```bash
To lookup the entry for a Cloud Pub/Sub topic by its Google Cloud Platform
resource name, run:

    $ gcloud data-catalog entries lookup \
        //pubsub.googleapis.com/projects/project1/topics/topic1

To lookup the entry for a Cloud Pub/Sub topic by its SQL name, run:

    $ gcloud data-catalog entries lookup \
        'pubsub.topic.`my-project1`.topic1'

To lookup the entry for a BigQuery table by its SQL name, run:

    $ gcloud data-catalog entries lookup \
        'bigquery.table.`my-project1`.my_dataset.my_table'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/lookup)

---
### `gcloud data-catalog entries star`

Star a Data Catalog entry

(DEPRECATED) This command is deprecated.

Star a Data Catalog entry.

**Synopsis:**
```
gcloud data-catalog entries star
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to star. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group of the entry.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To star the entry 'entry1' in the group 'group1', run:

    $ gcloud data-catalog entries star entry1 --entry-group=group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/star)

---
### `gcloud data-catalog entries unstar`

Unstar a Data Catalog entry

(DEPRECATED) This command is deprecated.

Unstar a Data Catalog entry.

**Synopsis:**
```
gcloud data-catalog entries unstar
    (ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to unstar. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group of the entry.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To unstar the entry 'entry1' in the group 'group1', run:

    $ gcloud data-catalog entries unstar entry1 --entry-group=group1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/unstar)

---
### `gcloud data-catalog entries update`

Update a Data Catalog entry

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
instead.

Update a Data Catalog entry. The entry to update can either be specified
directly, or the --lookup-entry flag may be used to update the entry
corresponding to the lookup of the given resource.

**Synopsis:**
```
gcloud data-catalog entries update
    [ENTRY : --entry-group=ENTRY_GROUP --location=LOCATION]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--lookup-entry=RESOURCE]
    [--add-file-patterns=[PATTERN,...] --clear-file-patterns
      | --remove-file-patterns=[PATTERN,...]
      | --linked-resource=LINKED_RESOURCE
      --user-specified-system=USER_SPECIFIED_SYSTEM
      --user-specified-type=USER_SPECIFIED_TYPE]
    [--schema=[COLUMN_NAME=COLUMN_TYPE,...]
      | --schema-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Entry resource - Entry to update. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  ENTRY
     ID of the entry or fully qualified identifier for the entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --entry-group=ENTRY_GROUP
     Entry group of the entry.

     To set the entry-group attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --entry-group on the command line.

  --location=LOCATION
     Location of the entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Textual description of the entry. |
| `--display-name` | DISPLAY_NAME |  | Human-readable name for the entry. |
| `--lookup-entry` | RESOURCE |  | The name of the target resource whose entry to update. This can be either the Google Cloud Platform resource name or the SQL name of a Google Cloud Platform resource. This flag allows one to update the entry corresponding to the lookup of the given resource, without needing to specify the entry directly. |


**Examples:**
```bash
To update the schema of a Cloud Pub/Sub entry inline, run:

    $ gcloud data-catalog entries update entry1 --location=global \
        --entry-group=@pubsub --schema="column1=type1,column2=type2"

To update the schema of a Cloud Pub/Sub entry from a file, run:

    $ gcloud data-catalog entries update entry1 --location=global \
        --entry-group=@pubsub --schema-from-file="/tmp/schema.json"

To lookup the entry of a Cloud Pub/Sub topic by its SQL name and update its
schema in one command, run:

    $ gcloud data-catalog entries update \
        --lookup-entry='pubsub.topic.`my-project1`.topic1' \
        --schema="column1=type1,column2=type2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/entries/update)

---
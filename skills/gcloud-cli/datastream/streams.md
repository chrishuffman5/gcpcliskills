# gcloud datastream streams

manage Datastream stream resources

### `gcloud datastream streams create`

Create a Datastream stream

Create a Datastream stream. If successful, the response body contains a
newly created instance of Operation. To get the operation result, call:
describe OPERATION

**Synopsis:**
```
gcloud datastream streams create (STREAM : --location=LOCATION)
    --display-name=DISPLAY_NAME
    (--backfill-none
      | --backfill-all --mongodb-excluded-objects=MONGODB_EXCLUDED_OBJECTS
      | --mysql-excluded-objects=MYSQL_EXCLUDED_OBJECTS
      | --oracle-excluded-objects=ORACLE_EXCLUDED_OBJECTS
      | --postgresql-excluded-objects=POSTGRESQL_EXCLUDED_OBJECTS
      | --salesforce-excluded-objects=SALESFORCE_EXCLUDED_OBJECTS
      | --sqlserver-excluded-objects=SQLSERVER_EXCLUDED_OBJECTS)
    (--destination=DESTINATION
      (--bigquery-destination-config=BIGQUERY_DESTINATION_CONFIG
      | --gcs-destination-config=GCS_DESTINATION_CONFIG))
    (--source=SOURCE (--mongodb-source-config=MONGODB_SOURCE_CONFIG
      | --mysql-source-config=MYSQL_SOURCE_CONFIG
      | --oracle-source-config=ORACLE_SOURCE_CONFIG
      | --postgresql-source-config=POSTGRESQL_SOURCE_CONFIG
      | --salesforce-source-config=SALESFORCE_SOURCE_CONFIG
      | --sqlserver-source-config=SQLSERVER_SOURCE_CONFIG))
    [--labels=[KEY=VALUE,...]] [--rule-sets=RULE_SETS]
    [--force | --validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream resource - The stream to create. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument stream on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STREAM
     ID of the stream or fully qualified identifier for the stream.

     To set the stream attribute:
     + provide the argument stream on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the stream.

     To set the location attribute:
     + provide the argument stream on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name for the stream. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--rule-sets` | RULE_SETS |  | Path to a JSON file containing a list of rule sets to be applied to the stream. The JSON file is formatted as follows, with camelCase field naming: [ { "objectFilter": { "sourceObjectIdentifier": { "oracleIdentifier": { "schema": "schema1", "table": "table1" } } }, "customizationRules": [ { "bigqueryClustering": { "columns": ["COL_A"] } } ] }, { "objectFilter": { "sourceObjectIdentifier": { "oracleIdentifier": { "schema": "schema2", "table": "table2" } } }, "customizationRules": [ { "bigqueryPartitioning": { "timeUnitPartition": { "column": "TIME_COL", "partitioningTimeGranularity": "PARTITIONING_TIME_GRANULARITY_DAY" } } } ] } ] |


**Examples:**
```bash
To create a stream with an Oracle source and a Google Cloud Storage
destination:

    $ gcloud datastream streams create STREAM --location=us-central1 \
      --display-name=my-stream --source=source \
      --oracle-source-config=source_config.json \
      --destination=destination \
      --gcs-destination-config=destination_config.json --backfill-none

To create a stream with a MySQL source and a Cloud Storage destination and
that excludes some objects from being backfilled:

    $ gcloud datastream streams create STREAM --location=us-central1 \
      --display-name=my-stream --source=source \
      --mysql-source-config=source_config.json \
      --destination=destination \
      --gcs-destination-config=destination_config.json \
      --backfill-all --mysql-excluded-objects=excluded_objects.json

To create a stream with an Oracle source and a BigQuery destination:

    $ gcloud datastream streams create STREAM --location=us-central1 \
      --display-name=my-stream --source=source \
      --oracle-source-config=source_config.json \
      --destination=destination \
      --bigquery-destination-config=destination_config.json \
      --backfill-none

To create a stream with a PostgreSQL source and a BigQuery destination:

    $ gcloud datastream streams create STREAM --location=us-central1 \
      --display-name=my-stream --source=source \
      --postgresql-source-config=source_config.json \
      --destination=destination \
      --bigquery-destination-config=destination_config.json \
      --backfill-none

To create a stream with a MongoDB source and a Cloud Storage destination
and that excludes some objects from being backfilled:

    $ gcloud datastream streams create STREAM --location=us-central1 \
      --display-name=my-stream --source=source \
      --mongodb-source-config=source_config.json \
      --destination=destination \
      --gcs-destination-config=destination_config.json \
      --backfill-all --mongodb-excluded-objects=excluded_objects.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/streams/create)

---
### `gcloud datastream streams delete`

Delete a Datastream stream

Deletes a stream.

**Synopsis:**
```
gcloud datastream streams delete (STREAM : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream resource - Stream resource - Stream to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument stream on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STREAM
     ID of the stream or fully qualified identifier for the stream.

     To set the stream attribute:
     + provide the argument stream on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument stream on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a stream:

    $ gcloud datastream streams delete STREAM --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/streams/delete)

---
### `gcloud datastream streams describe`

Show details about a Datastream stream resource

Show details about a Datastream stream resource.

**Synopsis:**
```
gcloud datastream streams describe (STREAM : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream resource - The stream you want to get the details of. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument stream on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STREAM
     ID of the stream or fully qualified identifier for the stream.

     To set the stream attribute:
     + provide the argument stream on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument stream on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about a stream, run:

    $ gcloud datastream streams describe my-stream --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/streams/describe)

---
### `gcloud datastream streams list`

List Datastream stream resources

List Datastream stream resources.

**Synopsis:**
```
gcloud datastream streams list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all streams in a project and location 'us-central1', run:

    $ gcloud datastream streams list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/streams/list)

---
### `gcloud datastream streams update`

Updates a Datastream stream

Update a Datastream stream. If successful, the response body contains a
newly created instance of Operation. To get the operation result, call:
describe OPERATION

**Synopsis:**
```
gcloud datastream streams update (STREAM : --location=LOCATION)
    [--display-name=DISPLAY_NAME] [--rule-sets=RULE_SETS] [--state=STATE]
    [--update-labels=[KEY=VALUE,...]] [--update-mask=UPDATE_MASK]
    [--backfill-none
      | --backfill-all --mongodb-excluded-objects=MONGODB_EXCLUDED_OBJECTS
      | --mysql-excluded-objects=MYSQL_EXCLUDED_OBJECTS
      | --oracle-excluded-objects=ORACLE_EXCLUDED_OBJECTS
      | --postgresql-excluded-objects=POSTGRESQL_EXCLUDED_OBJECTS
      | --salesforce-excluded-objects=SALESFORCE_EXCLUDED_OBJECTS
      | --sqlserver-excluded-objects=SQLSERVER_EXCLUDED_OBJECTS]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--destination=DESTINATION
      --bigquery-destination-config=BIGQUERY_DESTINATION_CONFIG
      | --gcs-destination-config=GCS_DESTINATION_CONFIG]
    [--force | --validate-only]
    [--source=SOURCE --mongodb-source-config=MONGODB_SOURCE_CONFIG
      | --mysql-source-config=MYSQL_SOURCE_CONFIG
      | --oracle-source-config=ORACLE_SOURCE_CONFIG
      | --postgresql-source-config=POSTGRESQL_SOURCE_CONFIG
      | --salesforce-source-config=SALESFORCE_SOURCE_CONFIG
      | --sqlserver-source-config=SQLSERVER_SOURCE_CONFIG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Stream resource - The stream to update. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument stream on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STREAM
     ID of the stream or fully qualified identifier for the stream.

     To set the stream attribute:
     + provide the argument stream on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the stream.

     To set the location attribute:
     + provide the argument stream on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name for the stream. |
| `--rule-sets` | RULE_SETS |  | Path to a JSON file containing a list of rule sets to be applied to the stream. The JSON file is formatted as follows, with camelCase field naming: [ { "objectFilter": { "sourceObjectIdentifier": { "oracleIdentifier": { "schema": "schema1", "table": "table1" } } }, "customizationRules": [ { "bigqueryClustering": { "columns": ["COL_A"] } } ] }, { "objectFilter": { "sourceObjectIdentifier": { "oracleIdentifier": { "schema": "schema2", "table": "table2" } } }, "customizationRules": [ { "bigqueryPartitioning": { "timeUnitPartition": { "column": "TIME_COL", "partitioningTimeGranularity": "PARTITIONING_TIME_GRANULARITY_DAY" } } } ] } ] |
| `--state` | STATE |  | Stream state, can be set to: "RUNNING" or "PAUSED". |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--update-mask` | UPDATE_MASK |  | Used to specify the fields to be overwritten in the stream resource by the update. If the update mask is used, then a field will be overwritten only if it is in the mask. If the user does not provide a mask then all fields will be overwritten. This is a comma-separated list of fully qualified names of fields, written as snake_case or camelCase. Example: "display_name, source_config.oracle_source_config". |


**Examples:**
```bash
To update a stream with a new source and new display name:

    $ gcloud datastream streams update STREAM --location=us-central1 \
      --display-name=my-stream --source=source \
      --update-mask=display_name,source

To update a stream's state to RUNNING:

    $ gcloud datastream streams update STREAM --location=us-central1 \
      --state=RUNNING --update-mask=state

To update a stream's oracle source config:

    $ gcloud datastream streams update STREAM --location=us-central1 \
      --oracle-source-config=good_oracle_cp.json \
      --update-mask=oracle_source_config.include_objects
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/streams/update)

---
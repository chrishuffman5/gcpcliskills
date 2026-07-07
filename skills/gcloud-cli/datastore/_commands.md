# gcloud datastore (top-level commands)

### `gcloud datastore export`

Export Cloud Datastore entities to Google Cloud Storage

Export a copy of all or a subset of entities from Google Cloud Datastore to
another storage system, such as Google Cloud Storage. Recent updates to
entities may not be reflected in the export. The export occurs in the
background and its progress can be monitored and managed via the operation
commands. The output of an export may only be used once the operation has
completed. If an export operation is cancelled before completion then it
may leave partial data behind in Google Cloud Storage.

**Synopsis:**
```
gcloud datastore export OUTPUT_URL_PREFIX [--async] [--kinds=[KIND,...]]
    [--namespaces=[NAMESPACE,...]]
    [--operation-labels=[OPERATION_LABEL,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OUTPUT_URL_PREFIX
   Location for the export metadata and data files. Must be a valid Google
   Cloud Storage bucket with an optional path prefix. For example:

       $ gcloud datastore export gs://mybucket/my/path

   Will place the export in the mybucket bucket in objects prefixed with
   my/path.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--kinds` | [KIND,...] |  | A list specifying what kinds will be included in the operation. When omitted, all Kinds are included. For example, to operate on only the 'Customer' and 'Order' Kinds: $ gcloud datastore export --kinds='Customer','Order' |
| `--namespaces` | [NAMESPACE,...] |  | A list specifying what namespaces will be included in the operation. When omitted, all namespaces are included in the operation, including the default namespace. To specify that only the default namespace should be operated on, use the special symbol '(default)'. For example, to operate on entities from both the 'customers' and default namespaces: $ gcloud datastore export --namespaces='(default)','customers' |
| `--operation-labels` | [OPERATION_LABEL,...] |  | A string:string map of custom labels to associate with this operation. For example: $ gcloud datastore export \ --operation-labels=comment='customer orders','sales rep'=pending |


**Examples:**
```bash
To export all kinds in the exampleNs namespace in the exampleProject
project to the exampleBucket, run:

    $ gcloud datastore export gs://exampleBucket \
        --namespaces='exampleNs' --project='exampleProject'

To export the exampleKind and otherKind kinds in the exampleNs namespace in
the exampleProject project to the exampleBucket, run:

    $ gcloud datastore export gs://exampleBucket \
        --kinds='exampleKind','otherKind' --namespaces='exampleNs' \
        --project='exampleProject'

To export all namespaces and kinds in the currently set project to the
exampleBucket without waiting for the operation to complete, run:

    $ gcloud datastore export gs://exampleBucket --async

To export the exampleKind in all namespaces in the currently set project to
the exampleBucket, and output the result in JSON, run:

    $ gcloud datastore export gs://exampleBucket --kinds='exampleKind' \
        --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/export)

---
### `gcloud datastore import`

Import Cloud Datastore entities from Google Cloud Storage

Imports entities into Google Cloud Datastore. Existing entities with the
same key are overwritten. The import occurs in the background and its
progress can be monitored and managed via the Operation resource that is
created. If an Import operation is cancelled, it is possible that a subset
of the data has already been imported to Cloud Datastore. This data will
not be removed.

**Synopsis:**
```
gcloud datastore import INPUT_URL [--async] [--kinds=[KIND,...]]
    [--namespaces=[NAMESPACE,...]]
    [--operation-labels=[OPERATION_LABEL,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_URL
   Location of the import metadata. Must be a valid Google Cloud Storage
   object. The file extension is 'overall_export_metadata'.

   This location is the 'output_url' field of a previous export, and can
   be found via the 'operations describe' command.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--kinds` | [KIND,...] |  | A list specifying what kinds will be included in the operation. When omitted, all Kinds are included. For example, to operate on only the 'Customer' and 'Order' Kinds: $ gcloud datastore import --kinds='Customer','Order' |
| `--namespaces` | [NAMESPACE,...] |  | A list specifying what namespaces will be included in the operation. When omitted, all namespaces are included in the operation, including the default namespace. To specify that only the default namespace should be operated on, use the special symbol '(default)'. For example, to operate on entities from both the 'customers' and default namespaces: $ gcloud datastore import --namespaces='(default)','customers' |
| `--operation-labels` | [OPERATION_LABEL,...] |  | A string:string map of custom labels to associate with this operation. For example: $ gcloud datastore import \ --operation-labels=comment='customer orders','sales rep'=pending |


**Examples:**
```bash
To import all data exported to the output URL
gs://exampleBucket/exampleExport/exampleExport.overall_export_metadata,
run:

    $ gcloud datastore import \
        gs://exampleBucket/exampleExport/\
    exampleExport.overall_export_metadata

To import all data exported to the output URL
gs://exampleBucket/exampleExport/exampleExport.overall_export_metadata
without waiting for the operation to complete, run:

    $ gcloud datastore import \
        gs://exampleBucket/exampleExport/\
    exampleExport.overall_export_metadata --async

To import only the exampleKind from the data exported to the output URL
gs://exampleBucket/exampleExport/exampleExport.overall_export_metadata,
run:

    $ gcloud datastore import \
        gs://exampleBucket/exampleExport/\
    exampleExport.overall_export_metadata --kinds='exampleKind'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/import)

---
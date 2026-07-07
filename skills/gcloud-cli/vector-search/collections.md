# gcloud vector-search collections

manage Collection resources

### `gcloud vector-search collections create`

Create a collection

**Synopsis:**
```
gcloud vector-search collections create (COLLECTION : --location=LOCATION)
    [--async] [--data-schema=DATA_SCHEMA] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME]
    [--encryption-spec-crypto-key-name=ENCRYPTION_SPEC_CRYPTO_KEY_NAME]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [--vector-schema=[VECTOR_SCHEMA,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Collection resource - Identifier. Name of the resource. The arguments in
this group can be used to specify the attributes of this resource.

To set the project attribute:
 * provide the argument collection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  COLLECTION
     ID of the collection or fully qualified identifier for the
     collection.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the collection resource.

     To set the location attribute:
     + provide the argument collection on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--data-schema` | DATA_SCHEMA |  | JSON Schema of the data. Field names must contain only alphanumeric characters, underscores, and hyphens. Must comply with JSON Schema Draft 7. |
| `--description` | DESCRIPTION |  | User-specified description of the collection. |
| `--display-name` | DISPLAY_NAME |  | User-specified display name of the collection. |
| `--encryption-spec-crypto-key-name` | KEY_NAME |  | Resource name of the Cloud KMS key used to protect the resource. Format: `projects/{project}/locations/{location}/keyRings/{key_ring}/cryptoKeys/{crypto_key}`. |
| `--labels` | [LABELS,...] |  | Labels as key-value pairs. Keys must start with a lowercase character and contain only hyphens, underscores, lowercase characters, and numbers; values follow the same rules. |
| `--request-id` | REQUEST_ID |  | Optional request ID so the server can ignore duplicate requests for 60 minutes. Must be a valid UUID (zero UUID not supported). |
| `--vector-schema` | [VECTOR_SCHEMA,...] |  | Schema of vector fields available for search, keyed by field name (alphanumeric, underscores, hyphens). Each field is `denseVector` (`dimensions` integer, optional `vertexEmbeddingConfig` with required `modelId`, `taskType`, and `textTemplate` — a template referencing data fields like `"{fieldname}"`) or `sparseVector`. |

**Examples:**
```bash
To create a collection my-collection in project my-project and location
us-central1 with data schema and vector schema, run:

    $ gcloud vector-search collections create my-collection \
        --location=us-central1 --display-name='My Collection' \
        --data-schema='{"type":"object","properties":{"year":{"type":"number"},"genre":{"type":"string"},"director":{"type":"string"},"title":{"type":"string"}}}' \
        --vector-schema='{"plot_embedding":{"denseVector":{"dimensions":3}},"genre_embedding":{"denseVector":{"dimensions":4}},"sparse_embedding":{"sparseVector":{}}}' \
        --project=my-project

To create a collection storing dense embedding vectors with 100
dimensions, run:

    $ gcloud vector-search collections create my-collection \
        --location=us-central1 --display-name='My Collection' \
        --vector-schema='{"my-embedding-field":{"denseVector":{"dimensions":100}}}'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/create)

---
### `gcloud vector-search collections delete`

Delete a collection

**Synopsis:**
```
gcloud vector-search collections delete (COLLECTION : --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Collection resource - Name of the resource. This must be specified.

  COLLECTION
     ID of the collection or fully qualified identifier for the
     collection. This positional argument must be specified if any of the
     other arguments in this group are specified.

  --location=LOCATION
     The location id of the collection resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | Optional request ID so the server can ignore duplicate requests for 60 minutes. Must be a valid UUID (zero UUID not supported). |

**Examples:**
```bash
To delete a collection my-collection in project my-project and location
us-central1, run:

    $ gcloud vector-search collections delete my-collection \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/delete)

---
### `gcloud vector-search collections describe`

Describe a collection

Get details about a specific collection.

**Synopsis:**
```
gcloud vector-search collections describe (COLLECTION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Collection resource - Name of the resource. This must be specified.

  COLLECTION
     ID of the collection or fully qualified identifier for the
     collection. This positional argument must be specified if any of the
     other arguments in this group are specified.

  --location=LOCATION
     The location id of the collection resource.
```

**Examples:**
```bash
To describe a collection my-collection in project my-project and location
us-central1, run:

    $ gcloud vector-search collections describe my-collection \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/describe)

---
### `gcloud vector-search collections export-data-objects`

Export data objects from a collection

Exports data objects from a collection to Google Cloud Storage.

**Synopsis:**
```
gcloud vector-search collections export-data-objects
    (COLLECTION : --location=LOCATION)
    --gcs-destination-export-uri=GCS_DESTINATION_EXPORT_URI
    --gcs-destination-format=GCS_DESTINATION_FORMAT [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Collection resource - The resource name of the Collection to export Data
Objects from. Format:
projects/{project}/locations/{location}/collections/{collection}.
This must be specified.

  COLLECTION
     ID of the collection or fully qualified identifier for the
     collection.

  --location=LOCATION
     The location id of the collection resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-destination-export-uri` | URI |  | URI prefix of the Cloud Storage destination. The bucket must be in the same region as the collection. |
| `--gcs-destination-format` | FORMAT |  | Format of the exported Data Objects. Supported value: `jsonl` (export in JSONL format). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |

**Examples:**
```bash
To export data objects from collection my-collection to Cloud Storage,
run:

    $ gcloud vector-search collections export-data-objects my-collection \
        --location=us-central1 \
        --gcs-destination-export-uri=gs://my-bucket/export/ \
        --gcs-destination-format=jsonl \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/export-data-objects)

---
### `gcloud vector-search collections import-data-objects`

Import data objects into a collection

Import data objects into a collection from Google Cloud Storage.

**Synopsis:**
```
gcloud vector-search collections import-data-objects
    (COLLECTION : --location=LOCATION)
    --gcs-import-contents-uri=GCS_IMPORT_CONTENTS_URI
    --gcs-import-error-uri=GCS_IMPORT_ERROR_URI [--async]
    [--gcs-import-output-uri=GCS_IMPORT_OUTPUT_URI] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Collection resource - The resource name of the Collection to create the
DataObjects in. Format:
projects/{project}/locations/{location}/collections/{collection}.
This must be specified.

  COLLECTION
     ID of the collection or fully qualified identifier for the
     collection.

  --location=LOCATION
     The location id of the collection resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-import-contents-uri` | URI |  | URI prefix of the Cloud Storage DataObjects to import. |
| `--gcs-import-error-uri` | URI |  | URI prefix of the Cloud Storage location to write import errors to. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--gcs-import-output-uri` | URI |  | URI prefix of the Cloud Storage location to write IDs and etags of successfully imported DataObjects to. If empty, no output is written. |

**Examples:**
```bash
To import data objects into collection my-collection from Cloud Storage,
run:

    $ gcloud vector-search collections import-data-objects my-collection \
        --location=us-central1 \
        --gcs-import-contents-uri=gs://my-bucket/contents/ \
        --gcs-import-error-uri=gs://my-bucket/errors/ \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/import-data-objects)

---
### `gcloud vector-search collections list`

List collections

**Synopsis:**
```
gcloud vector-search collections list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. Applied after `--flatten`, before `--sort-by` and `--limit`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page for services that support paging. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list collections in project my-project and location us-central1, run:

    $ gcloud vector-search collections list \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/list)

---
### `gcloud vector-search collections update`

Update a collection

**Synopsis:**
```
gcloud vector-search collections update (COLLECTION : --location=LOCATION)
    [--async] [--data-schema=DATA_SCHEMA] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--request-id=REQUEST_ID]
    [--labels=[LABELS,...] | --update-labels=[UPDATE_LABELS,...]
      [--clear-labels | --remove-labels=REMOVE_LABELS]]
    [--vector-schema=[VECTOR_SCHEMA,...]
      | --update-vector-schema=[UPDATE_VECTOR_SCHEMA,...]
      [--clear-vector-schema | --remove-vector-schema=REMOVE_VECTOR_SCHEMA]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Collection resource - Identifier. Name of the resource. This must be
specified.

  COLLECTION
     ID of the collection or fully qualified identifier for the
     collection. This positional argument must be specified if any of the
     other arguments in this group are specified.

  --location=LOCATION
     The location id of the collection resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--data-schema` | DATA_SCHEMA |  | JSON Schema of the data. Field names: alphanumeric characters, underscores, and hyphens only. Must comply with JSON Schema Draft 7. |
| `--description` | DESCRIPTION |  | User-specified description of the collection. |
| `--display-name` | DISPLAY_NAME |  | User-specified display name of the collection. |
| `--request-id` | REQUEST_ID |  | Optional request ID for deduplication (60-minute window). Must be a valid UUID (zero UUID not supported). |
| `--labels` | [LABELS,...] |  | Set labels to a new value (replaces all existing labels). Mutually exclusive with `--update-labels`. |
| `--update-labels` | [UPDATE_LABELS,...] |  | Add or update specific label key-value pairs. |
| `--clear-labels` |  |  | Clear all labels. Mutually exclusive with `--remove-labels`. |
| `--remove-labels` | REMOVE_LABELS |  | Remove the listed label keys. |
| `--vector-schema` | [VECTOR_SCHEMA,...] |  | Set the complete vector schema (same format as on create: `denseVector` with `dimensions` and optional `vertexEmbeddingConfig` (`modelId`, `taskType`, `textTemplate`), or `sparseVector`). Mutually exclusive with `--update-vector-schema`. |
| `--update-vector-schema` | [UPDATE_VECTOR_SCHEMA,...] |  | Add or update vector schema fields. |
| `--clear-vector-schema` |  |  | Clear the vector schema. Mutually exclusive with `--remove-vector-schema`. |
| `--remove-vector-schema` | REMOVE_VECTOR_SCHEMA |  | Remove the listed vector schema fields. |

**Examples:**
```bash
To update a collection my-collection in project my-project and location
us-central1, run:

    $ gcloud vector-search collections update my-collection \
        --location=us-central1 \
        --display-name='My Updated Collection' \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/update)

---

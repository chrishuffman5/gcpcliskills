# gcloud vector-search collections data-objects

manage Vector Search data objects

### `gcloud vector-search collections data-objects aggregate`

Aggregate data objects

**Synopsis:**
```
gcloud vector-search collections data-objects aggregate
    --aggregation-method=AGGREGATION_METHOD --collection=COLLECTION
    --location=LOCATION [--json-filter=JSON_FILTER] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aggregation-method` | AGGREGATION_METHOD |  | The aggregation method to apply to the query. Choices: `count` (count the number of data objects matching the filter). |
| `--collection` | COLLECTION |  | The collection to aggregate data objects from. |
| `--location` | LOCATION |  | Location of the collection. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-filter` | JSON_FILTER |  | A filter expression in JSON format to apply to the aggregate, e.g. `'{"genre": {"$eq": "sci-fi"}}'`. |

**Examples:**
```bash
To aggregate data objects from collection my-collection in location
us-central1 with the COUNT method, run:

    $ gcloud vector-search collections data-objects aggregate \
        --collection=my-collection --location=us-central1 \
        --aggregation-method=count --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/aggregate)

---
### `gcloud vector-search collections data-objects batch-create`

Create a batch of data objects

**Synopsis:**
```
gcloud vector-search collections data-objects batch-create
    --requests=[dataObject=DATAOBJECT],[dataObjectId=DATAOBJECTID],[parent=PARENT]
    (--collection=COLLECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--requests` | [dataObject=...],[dataObjectId=...],[parent=...] |  | The request message specifying the DataObjects to create. Max 1000 DataObjects per batch. `dataObject`: the DataObject to create (`data`, `etag`, `name` in format `projects/{project}/locations/{location}/collections/{collection}/dataObjects/{data_object_id}`, `vectors` keyed dense/sparse vectors). `dataObjectId`: 1-63 characters, RFC1035-compliant, matching `[a-z](?:[-a-z0-9]{0,61}[a-z0-9])?`. `parent`: collection resource name `projects/{project}/locations/{location}/collections/{collection}`. Accepts shorthand, JSON, or a YAML/JSON file. |
| `--collection` | COLLECTION |  | ID of the collection or fully qualified identifier for the collection. |
| `--location` | LOCATION |  | The location id of the collection resource. |

**Examples:**
```bash
To create a batch of data objects in collection my-collection, project
my-project and location us-central1, run:

    $ gcloud vector-search collections data-objects batch-create \
        --collection=my-collection --location=us-central1 \
        --requests='[{"parent":"projects/my-project/locations/us-central1/collections/my-collection","dataObjectId":"my-do-b1","dataObject":{"data":{"title":"Batched Movie 1"}}},{"parent":"projects/my-project/locations/us-central1/collections/my-collection","dataObjectId":"my-do-b2","dataObject":{"data":{"title":"Batched Movie 2"}}}]' \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/batch-create)

---
### `gcloud vector-search collections data-objects batch-delete`

Delete a batch of data objects

**Synopsis:**
```
gcloud vector-search collections data-objects batch-delete
    --requests=[etag=ETAG],[name=NAME]
    (--collection=COLLECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--requests` | [etag=ETAG],[name=NAME] |  | The request message specifying the resources to delete. Max 1000 DataObjects per batch. `etag`: current DataObject etag; if provided and mismatched, deletion is blocked with an ABORTED error. `name`: DataObject resource name in format `projects/{project}/locations/{location}/collections/{collection}/dataObjects/{dataObject}`. Accepts shorthand, JSON array, or a YAML/JSON file. |
| `--collection` | COLLECTION |  | ID of the collection or fully qualified identifier for the collection. |
| `--location` | LOCATION |  | The location id of the collection resource. |

**Examples:**
```bash
To delete a batch of data objects, run:

    $ gcloud vector-search collections data-objects batch-delete \
        --collection=my-collection --location=us-central1 \
        --requests='[{"name":"projects/my-project/locations/us-central1/collections/my-collection/dataObjects/my-do-b1"},{"name":"projects/my-project/locations/us-central1/collections/my-collection/dataObjects/my-do-b2"}]' \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/batch-delete)

---
### `gcloud vector-search collections data-objects batch-search`

Batch search data objects from a Vector Search collection

Performs multiple search operations in one request; the search specifications are provided through a JSON file via `--searches-from-file`. Results can optionally be combined with Reciprocal Rank Fusion (RRF).

**Synopsis:**
```
gcloud vector-search collections data-objects batch-search
    --collection=COLLECTION --location=LOCATION
    --searches-from-file=SEARCHES_FROM_FILE
    [--rrf-weights=[WEIGHT,...]
      : --combine-output-data-fields=[DATA_OUTPUT_FIELD,...]
      --combine-output-metadata-fields=[METADATA_OUTPUT_FIELD,...]
      --combine-output-vector-fields=[VECTOR_OUTPUT_FIELD,...]
      --combine-top-k=COMBINE_TOP_K] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collection` | COLLECTION |  | The collection to batch search data objects from. |
| `--location` | LOCATION |  | Location of the collection. |
| `--searches-from-file` | PATH |  | Path to a JSON file containing the list of searches; each element is a Search message with camelCase keys matching the API definitions (semantic, vector, or text search with per-search top-K and output field settings). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--rrf-weights` | [WEIGHT,...] |  | RRF weights applied when combining search results (ranker; required to enable the combine options below). |
| `--combine-output-data-fields` | [DATA_OUTPUT_FIELD,...] |  | Data fields to include in the combined output. |
| `--combine-output-metadata-fields` | [METADATA_OUTPUT_FIELD,...] |  | Metadata fields to include in the combined output. |
| `--combine-output-vector-fields` | [VECTOR_OUTPUT_FIELD,...] |  | Vector fields to include in the combined output. |
| `--combine-top-k` | COMBINE_TOP_K |  | Number of top results to return when combining results. |

**Examples:**
```bash
To batch search data objects from collection my-collection using searches
defined in searches.json, run:

    $ gcloud vector-search collections data-objects batch-search \
        --collection=my-collection --location=us-central1 \
        --searches-from-file=searches.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/batch-search)

---
### `gcloud vector-search collections data-objects batch-update`

Update a batch of data objects

**Synopsis:**
```
gcloud vector-search collections data-objects batch-update
    --requests=[dataObject=DATAOBJECT],[updateMask=UPDATEMASK]
    (--collection=COLLECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--requests` | [dataObject=...],[updateMask=...] |  | The request message specifying the resources to update. Max 1000 DataObjects per batch. `dataObject`: replacement DataObject (`name` in format `projects/{project}/locations/{location}/collections/{collection}/dataObjects/{data_object_id}`, `data`, `etag`, `vectors` keyed dense/sparse vectors). `updateMask`: field mask per google.protobuf.FieldMask. Accepts shorthand, JSON, or a YAML/JSON file. |
| `--collection` | COLLECTION |  | ID of the collection or fully qualified identifier for the collection. |
| `--location` | LOCATION |  | The location id of the collection resource. |

**Examples:**
```bash
To update a batch of data objects, run:

    $ gcloud vector-search collections data-objects batch-update \
        --collection=my-collection --location=us-central1 \
        --requests='[{"dataObject":{"name":"projects/my-project/locations/us-central1/collections/my-collection/dataObjects/my-do-b1","data":{"genre":"Thriller"}},"updateMask":"data.genre"}]' \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/batch-update)

---
### `gcloud vector-search collections data-objects create`

Create a data object

**Synopsis:**
```
gcloud vector-search collections data-objects create
    (DATA_OBJECT : --collection=COLLECTION --location=LOCATION)
    [--data=DATA] [--etag=ETAG] [--vectors=[VECTORS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataObject resource - Identifier. Name of the DataObject, in the format
projects/{project}/locations/{location}/collections/{collection}/dataObjects/{data_object_id}.
The data_object_id must be 1-63 characters, compliant with RFC1035.
This must be specified.

  DATA_OBJECT
     ID of the dataObject or fully qualified identifier for the
     dataObject. This positional argument must be specified if any of the
     other arguments in this group are specified.

  --collection=COLLECTION
     The collection id of the dataObject resource.

  --location=LOCATION
     The location id of the dataObject resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data` | DATA |  | The data of the dataObject (JSON). |
| `--etag` | ETAG |  | The etag of the dataObject. |
| `--vectors` | [VECTORS,...] |  | Vectors keyed by field name. Two formats: `dense` (contains `values`, a float array) or `sparse` (contains `indices`, an int array, and `values`, a float array). Accepts shorthand, JSON, or a YAML/JSON file. |

**Examples:**
```bash
To create a data object my-do-1 in collection my-collection, project
my-project and location us-central1, run:

    $ gcloud vector-search collections data-objects create my-do-1 \
        --collection=my-collection --location=us-central1 \
        --data='{"director":"Frank Darabont","year":1994}' \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/create)

---
### `gcloud vector-search collections data-objects delete`

Delete a data object

**Synopsis:**
```
gcloud vector-search collections data-objects delete
    (DATA_OBJECT : --collection=COLLECTION --location=LOCATION)
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataObject resource - The name of the DataObject resource to be deleted,
in the format
projects/{project}/locations/{location}/collections/{collection}/dataObjects/{dataObject}.
This must be specified.

  DATA_OBJECT
     ID of the dataObject or fully qualified identifier for the
     dataObject. This positional argument must be specified if any of the
     other arguments in this group are specified.

  --collection=COLLECTION
     The collection id of the dataObject resource.

  --location=LOCATION
     The location id of the dataObject resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | The current etag of the DataObject. If an etag is provided and does not match the current etag of the DataObject, deletion will be blocked and an ABORTED error will be returned. |

**Examples:**
```bash
To delete data object my-do-1 from collection my-collection, project
my-project and location us-central1, run:

    $ gcloud vector-search collections data-objects delete my-do-1 \
        --collection=my-collection --location=us-central1 \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/delete)

---
### `gcloud vector-search collections data-objects describe`

Describe a data object

**Synopsis:**
```
gcloud vector-search collections data-objects describe
    (DATA_OBJECT : --collection=COLLECTION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataObject resource - The data object to describe, in the format
projects/{project}/locations/{location}/collections/{collection}/dataObjects/{dataObject}.
This must be specified.

  DATA_OBJECT
     ID of the dataObject or fully qualified identifier for the
     dataObject.

  --collection=COLLECTION
     The collection id of the dataObject resource.

  --location=LOCATION
     The location id of the dataObject resource.
```

**Examples:**
```bash
To describe data object my-do-1 in collection my-collection, project
my-project and location us-central1, run:

    $ gcloud vector-search collections data-objects describe my-do-1 \
        --collection=my-collection --location=us-central1 \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/describe)

---
### `gcloud vector-search collections data-objects query`

Query data objects from a Vector Search collection

**Synopsis:**
```
gcloud vector-search collections data-objects query --collection=COLLECTION
    --location=LOCATION [--json-filter=JSON_FILTER]
    [--output-data-fields=[DATA_OUTPUT_FIELD,...]
      --output-metadata-fields=[METADATA_OUTPUT_FIELD,...]
      --output-vector-fields=[VECTOR_OUTPUT_FIELD,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collection` | COLLECTION |  | The collection to query data objects from. |
| `--location` | LOCATION |  | Location of the collection. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-filter` | JSON_FILTER |  | A filter expression in JSON format to apply to the query, e.g. `'{"genre": {"$eq": "sci-fi"}}'`. |
| `--output-data-fields` | [DATA_OUTPUT_FIELD,...] |  | List of data fields to include in the output; use `*` for all data fields. |
| `--output-metadata-fields` | [METADATA_OUTPUT_FIELD,...] |  | List of metadata fields to include in the output; use `*` for all metadata fields. |
| `--output-vector-fields` | [VECTOR_OUTPUT_FIELD,...] |  | List of vector fields to include in the output; use `*` for all vector fields. |
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed (client-side gcloud filter). |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To query data objects from collection my-collection with a JSON filter,
run:

    $ gcloud vector-search collections data-objects query \
        --collection=my-collection --location=us-central1 \
        --limit=10 --json-filter='{"some_field": {"$eq": "some_value"}}'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/query)

---
### `gcloud vector-search collections data-objects search`

Search data objects from a Vector Search collection

Exactly one search mode must be specified: semantic search, text search, or vector search.

**Synopsis:**
```
gcloud vector-search collections data-objects search --collection=COLLECTION
    --location=LOCATION
    (--semantic-search-field=SEMANTIC_SEARCH_FIELD
       --semantic-search-text=SEMANTIC_SEARCH_TEXT
       --semantic-task-type=SEMANTIC_TASK_TYPE
     | --text-search-data-fields=[DATA_FIELD_NAME,...]
       --text-search-text=TEXT_SEARCH_TEXT
     | --vector-from-file=VECTOR_FROM_FILE
       --vector-search-field=VECTOR_SEARCH_FIELD
       : [--distance-metric=DISTANCE_METRIC])
    [--json-filter=JSON_FILTER] [--top-k=TOP_K]
    [--output-data-fields=[DATA_OUTPUT_FIELD,...]]
    [--output-metadata-fields=[METADATA_OUTPUT_FIELD,...]]
    [--output-vector-fields=[VECTOR_OUTPUT_FIELD,...]]
    [--use-index=INDEX | --use-knn] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collection` | COLLECTION |  | The collection to search data objects from. |
| `--location` | LOCATION |  | Location of the collection. |
| `--semantic-search-field` | FIELD |  | _[Semantic search]_ The vector field to search. |
| `--semantic-search-text` | TEXT |  | _[Semantic search]_ The query text for semantic search (embedded server-side). |
| `--semantic-task-type` | TASK_TYPE |  | _[Semantic search]_ Task type for the query embedding. Choices: `classification`, `clustering`, `code-retrieval-query`, `fact-verification`, `question-answering`, `retrieval-document`, `retrieval-query`, `semantic-similarity`. |
| `--text-search-data-fields` | [DATA_FIELD_NAME,...] |  | _[Text search]_ Data field names to search. |
| `--text-search-text` | TEXT |  | _[Text search]_ The query text for text search. |
| `--vector-from-file` | PATH |  | _[Vector search]_ Path to a JSON file containing a dense or sparse query vector. |
| `--vector-search-field` | FIELD |  | _[Vector search]_ The vector field to search. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--distance-metric` | DISTANCE_METRIC | `dot-product` | _[Vector search only]_ Distance metric. Choices: `cosine-distance`, `dot-product`. |
| `--json-filter` | JSON_FILTER |  | A filter expression in JSON format to apply to the search, e.g. `'{"genre": {"$eq": "sci-fi"}}'`. |
| `--top-k` | TOP_K | 10 | Number of nearest neighbors to return. |
| `--output-data-fields` | [DATA_OUTPUT_FIELD,...] |  | Data fields to include in the output; use `*` for all. |
| `--output-metadata-fields` | [METADATA_OUTPUT_FIELD,...] |  | Metadata fields to include in the output; use `*` for all. |
| `--output-vector-fields` | [VECTOR_OUTPUT_FIELD,...] |  | Vector fields to include in the output; use `*` for all. |
| `--use-index` | INDEX |  | Full resource name or ID of the index to use (semantic/vector search only). At most one of `--use-index` / `--use-knn`. |
| `--use-knn` |  |  | Use the default exact KNN index engine (semantic/vector search only). |

**Examples:**
```bash
# Text search
$ gcloud vector-search collections data-objects search \
    --collection=my-collection --location=us-central1 \
    --text-search-text="test" --text-search-data-fields="text_field" \
    --top-k=10

# Semantic search
$ gcloud vector-search collections data-objects search \
    --collection=my-collection --location=us-central1 \
    --semantic-search-text="sci-fi" --semantic-search-field="plot_embedding" \
    --semantic-task-type="retrieval-query" --top-k=5

# Vector search using an index
$ gcloud vector-search collections data-objects search \
    --collection=my-collection --location=us-central1 \
    --vector-search-field="genre_embedding" --vector-from-file="vector.json" \
    --use-index="my-index" --top-k=7

# Vector search using exact KNN
$ gcloud vector-search collections data-objects search \
    --collection=my-collection --location=us-central1 \
    --vector-search-field="genre_embedding" --vector-from-file="vector.json" \
    --use-knn --top-k=7
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/search)

---
### `gcloud vector-search collections data-objects update`

Update a data object

**Synopsis:**
```
gcloud vector-search collections data-objects update
    (DATA_OBJECT : --collection=COLLECTION --location=LOCATION)
    [--data=DATA] [--etag=ETAG]
    [--vectors=[VECTORS,...] | --update-vectors=[UPDATE_VECTORS,...]
      [--clear-vectors | --remove-vectors=REMOVE_VECTORS]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DataObject resource - Identifier. Name of the DataObject, in the format
projects/{project}/locations/{location}/collections/{collection}/dataObjects/{data_object_id}.
The data_object_id must be 1-63 characters, compliant with RFC1035.
This must be specified.

  DATA_OBJECT
     ID of the dataObject or fully qualified identifier for the
     dataObject.

  --collection=COLLECTION
     The collection id of the dataObject resource.

  --location=LOCATION
     The location id of the dataObject resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data` | DATA |  | The data of the dataObject (JSON). |
| `--etag` | ETAG |  | The etag of the dataObject (optimistic concurrency control). |
| `--vectors` | [VECTORS,...] |  | Replace all vectors with new values. Dense (`values` float array) or sparse (`indices` + `values`) per field. Accepts shorthand, JSON, or a YAML/JSON file. Mutually exclusive with `--update-vectors`. |
| `--update-vectors` | [UPDATE_VECTORS,...] |  | Add or update specific vector entries (same format as `--vectors`). |
| `--clear-vectors` |  |  | Empty the vectors map entirely. Mutually exclusive with `--remove-vectors`. |
| `--remove-vectors` | REMOVE_VECTORS |  | Delete the specified vector keys from the dataObject. Accepts comma-separated keys or a JSON array. |

**Examples:**
```bash
To update data for data object my-do-1 in collection my-collection,
project my-project and location us-central1, run:

    $ gcloud vector-search collections data-objects update my-do-1 \
        --collection=my-collection --location=us-central1 \
        --data='{"year":1995}' --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/data-objects/update)

---

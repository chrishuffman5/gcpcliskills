# gcloud vector-search collections indexes

manage Index resources

### `gcloud vector-search collections indexes create`

Create an index

**Synopsis:**
```
gcloud vector-search collections indexes create
    (INDEX : --collection=COLLECTION --location=LOCATION)
    --index-field=INDEX_FIELD [--async]
    [--dense-scann-feature-norm-type=DENSE_SCANN_FEATURE_NORM_TYPE]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--distance-metric=DISTANCE_METRIC] [--filter-fields=[FILTER_FIELDS,...]]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [--store-fields=[STORE_FIELDS,...]]
    [--dedicated-infrastructure-mode=DEDICATED_INFRASTRUCTURE_MODE]
    [--dedicated-infrastructure-autoscaling-spec-max-replica-count=MAX_COUNT]
    [--dedicated-infrastructure-autoscaling-spec-min-replica-count=MIN_COUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Identifier. Name of the resource. This must be
specified.

  INDEX
     ID of the index or fully qualified identifier for the index. This
     positional argument must be specified if any of the other arguments
     in this group are specified.

  --collection=COLLECTION
     The collection id of the index resource.

  --location=LOCATION
     The location id of the index resource.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--index-field` | INDEX_FIELD |  | The collection schema field to index. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--dense-scann-feature-norm-type` | NORM_TYPE |  | Feature norm type. Choices: `none` (no norm applied), `unit-l2-norm` (unit L2 norm). |
| `--description` | DESCRIPTION |  | User-specified description of the index. |
| `--display-name` | DISPLAY_NAME |  | User-specified display name of the index. |
| `--distance-metric` | DISTANCE_METRIC | `dot-product` | Distance metric. Choices: `cosine-distance`, `dot-product`. |
| `--filter-fields` | [FILTER_FIELDS,...] |  | Fields to push into the index for fast ANN inline filtering. |
| `--labels` | [LABELS,...] |  | Labels as key-value pairs (lowercase characters, hyphens, underscores, numbers). |
| `--request-id` | REQUEST_ID |  | Optional request UUID for retry idempotency (60-minute deduplication window). |
| `--store-fields` | [STORE_FIELDS,...] |  | Fields to push into the index for inline data retrieval. |
| `--dedicated-infrastructure-mode` | MODE |  | Dedicated infrastructure mode. Choices: `performance-optimized`, `storage-optimized`. |
| `--dedicated-infrastructure-autoscaling-spec-max-replica-count` | MAX_COUNT | max(min_count, 2-5) | Maximum number of replicas (1-1000). |
| `--dedicated-infrastructure-autoscaling-spec-min-replica-count` | MIN_COUNT | 2 | Minimum number of replicas (1-1000). |

**Examples:**
```bash
To create an index on an embedding field, run:

    $ gcloud vector-search collections indexes create my-index \
        --collection=my-collection --location=us-central1 \
        --index-field='my-embedding-field' --display-name='My Index' \
        --project=my-project

To create an index with filter and store fields, run:

    $ gcloud vector-search collections indexes create my-index-2 \
        --collection=my-collection --location=us-central1 \
        --index-field='my-embedding-field' --display-name='My Index 2' \
        --filter-fields=genre,year --store-fields=title \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/indexes/create)

---
### `gcloud vector-search collections indexes delete`

Delete an index

**Synopsis:**
```
gcloud vector-search collections indexes delete
    (INDEX : --collection=COLLECTION --location=LOCATION)
    [--async] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Name of the resource, in the format
projects/{project}/locations/{location}/collections/{collection}/indexes/{index}.
This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

  --collection=COLLECTION
     The collection id of the index resource.

  --location=LOCATION
     The location id of the index resource.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | Optional request UUID for retry idempotency (60-minute deduplication window; zero UUID not supported). |

**Examples:**
```bash
To delete index my-index in collection my-collection, run:

    $ gcloud vector-search collections indexes delete my-index \
        --collection=my-collection --location=us-central1 \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/indexes/delete)

---
### `gcloud vector-search collections indexes describe`

Describe an index

Get details about a specific index.

**Synopsis:**
```
gcloud vector-search collections indexes describe
    (INDEX : --collection=COLLECTION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Name of the resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index. This
     positional argument must be specified if any of the other arguments
     in this group are specified.

  --collection=COLLECTION
     The collection id of the index resource.

  --location=LOCATION
     The location id of the index resource.
```

**Examples:**
```bash
To describe index my-index in collection my-collection, run:

    $ gcloud vector-search collections indexes describe my-index \
        --collection=my-collection --location=us-central1 \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/indexes/describe)

---
### `gcloud vector-search collections indexes list`

List indexes

List indexes in a collection.

**Synopsis:**
```
gcloud vector-search collections indexes list
    (--collection=COLLECTION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collection` | COLLECTION |  | ID of the collection or fully qualified identifier for the collection. |
| `--location` | LOCATION |  | The location id of the collection resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list indexes in collection my-collection, run:

    $ gcloud vector-search collections indexes list \
        --collection=my-collection --location=us-central1 \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/collections/indexes/list)

---

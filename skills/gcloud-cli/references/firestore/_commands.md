# gcloud firestore (top-level commands)

### `gcloud firestore bulk-delete`

Bulk delete Cloud Firestore documents

bulk delete Cloud Firestore documents.

**Synopsis:**
```
gcloud firestore bulk-delete [--async]
    [--collection-ids=[COLLECTION_GROUP_IDS,...]]
    [--database=DATABASE; default="(default)"]
    [--namespace-ids=[NAMESPACE_IDS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--collection-ids` | [COLLECTION_GROUP_IDS,...] |  | List specifying which collection groups will be included in the operation. When omitted, all collection groups are included. For example, to operate on only the customers and orders collections groups: $ gcloud firestore bulk-delete --collection-ids='customers','orders' |
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore bulk-delete --database='foo' |
| `--namespace-ids` | [NAMESPACE_IDS,...] |  | List specifying which namespaces will be included in the operation. When omitted, all namespaces are included. This is only supported for Datastore Mode databases. For example, to operate on only the customers and orders namespaces: $ gcloud firestore bulk-delete --namespaces-ids='customers','orders' |


**Examples:**
```bash
To bulk delete a specific set of collections groups asynchronously, run:

    $ gcloud firestore bulk-delete \
        --collection-ids='specific collection group1','specific
     collection group2' --async

To bulk delete all collection groups from certain namespace, run:

    $ gcloud firestore bulk-delete \
        --namespace-ids='specific namespace id'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/bulk-delete)

---
### `gcloud firestore export`

Export Cloud Firestore documents to Google Cloud Storage

export Cloud Firestore documents to Google Cloud Storage.

**Synopsis:**
```
gcloud firestore export OUTPUT_URI_PREFIX [--async]
    [--collection-ids=[COLLECTION_GROUP_IDS,...]]
    [--database=DATABASE; default="(default)"]
    [--namespace-ids=[NAMESPACE_IDS,...]] [--snapshot-time=SNAPSHOT_TIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OUTPUT_URI_PREFIX
   Location where the export files will be stored. Must be a valid Google
   Cloud Storage bucket with an optional path prefix.

   For example:

       $ gcloud firestore export gs://mybucket/my/path

   Will place the export in the mybucket bucket in objects prefixed with
   my/path.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--collection-ids` | [COLLECTION_GROUP_IDS,...] |  | List specifying which collection groups will be included in the operation. When omitted, all collection groups are included. For example, to operate on only the customers and orders collections groups: $ gcloud firestore export --collection-ids='customers','orders' |
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore export --database='foo' |
| `--namespace-ids` | [NAMESPACE_IDS,...] |  | List specifying which namespaces will be included in the operation. When omitted, all namespaces are included. This is only supported for Datastore Mode databases. For example, to operate on only the customers and orders namespaces: $ gcloud firestore export --namespaces-ids='customers','orders' |
| `--snapshot-time` | SNAPSHOT_TIME |  | The version of the database to export. The timestamp must be in the past, rounded to the minute and not older than earliestVersionTime. If specified, then the exported documents will represent a consistent view of the database at the provided time. Otherwise, there are no guarantees about the consistency of the exported documents. For example, to operate on snapshot time 2023-05-26T10:20:00.00Z: $ gcloud firestore export --snapshot-time='2023-05-26T10:20:00.00Z' |


**Examples:**
```bash
To export all collection groups to mybucket in objects prefixed with
my/path, run:

    $ gcloud firestore export gs://mybucket/my/path

To export a specific set of collections groups asynchronously, run:

    $ gcloud firestore export gs://mybucket/my/path \
        --collection-ids='specific collection group1','specific
     collection group2' --async

To export all collection groups from certain namespace, run:

    $ gcloud firestore export gs://mybucket/my/path \
        --namespace-ids='specific namespace id'

To export from a snapshot at '2023-05-26T10:20:00.00Z', run:

    $ gcloud firestore export gs://mybucket/my/path \
        --snapshot-time='2023-05-26T10:20:00.00Z'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/export)

---
### `gcloud firestore import`

Import Cloud Firestore documents from Google Cloud Storage

import Cloud Firestore documents from Google Cloud Storage.

**Synopsis:**
```
gcloud firestore import INPUT_URI_PREFIX [--async]
    [--collection-ids=[COLLECTION_GROUP_IDS,...]]
    [--database=DATABASE; default="(default)"]
    [--namespace-ids=[NAMESPACE_IDS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_URI_PREFIX
   Location of the import files.

   This location is the 'output_uri_prefix' field of a previous export,
   and can be found via the 'gcloud firestore operations describe'
   command.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--collection-ids` | [COLLECTION_GROUP_IDS,...] |  | List specifying which collection groups will be included in the operation. When omitted, all collection groups are included. For example, to operate on only the customers and orders collections groups: $ gcloud firestore import --collection-ids='customers','orders' |
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore import --database='foo' |
| `--namespace-ids` | [NAMESPACE_IDS,...] |  | List specifying which namespaces will be included in the operation. When omitted, all namespaces are included. This is only supported for Datastore Mode databases. For example, to operate on only the customers and orders namespaces: $ gcloud firestore import --namespaces-ids='customers','orders' |


**Examples:**
```bash
To import all collection groups from mybucket/my/path, run:

    $ gcloud firestore import gs://mybucket/my/path

To import a specific set of collections groups asynchronously, run:

    $ gcloud firestore import gs://mybucket/my/path \
        --collection-ids='specific collection group1','specific
     collection group2' --async

To import all collection groups from certain namespace, run:

    $ gcloud firestore import gs://mybucket/my/path \
        --namespace-ids='specific namespace id'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/import)

---
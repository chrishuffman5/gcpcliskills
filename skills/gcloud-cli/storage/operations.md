# gcloud storage operations

manage storage operations

### `gcloud storage operations cancel`

Cancel a storage operation

Cancel a storage operation. Since operations are asynchronous, this request
is best effort and may fail in cases such as when the operation is already
complete.

**Synopsis:**
```
gcloud storage operations cancel OPERATION_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_NAME
   The operation name including the Cloud Storage bucket and operation ID.
```

**Examples:**
```bash
To cancel the operation "C894F35J" on bucket "my-bucket", run:

    $ gcloud storage operations cancel \
        projects/_/buckets/my-bucket/operations/C894F35J
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/operations/cancel)

---
### `gcloud storage operations describe`

Get configuration and latest storage operation details

Get details about a specific storage operation.

**Synopsis:**
```
gcloud storage operations describe OPERATION_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_NAME
   The operation name including the Cloud Storage bucket and operation ID.
```

**Examples:**
```bash
To describe an operation "C894F35J" on bucket "my-bucket", run:

    $ gcloud storage operations describe \
        projects/_/buckets/my-bucket/operations/C894F35J
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/operations/describe)

---
### `gcloud storage operations list`

List storage operations

List storage operations.

**Synopsis:**
```
gcloud storage operations list PARENT_RESOURCE_NAME
    [--server-filter=SERVER_FILTER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PARENT_RESOURCE_NAME
   The operation parent resource in the format
   "projects/_/buckets/BUCKET".
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--server-filter` | SERVER_FILTER |  | Server-side filter string used to determine what operations to return. Example: '(done = true AND complete_time >= "2023-01-01T00:00:00Z") OR requested_cancellation = true' Note that the entire filter string must be in quotes and date strings within the filter must be in embedded quotes. |


**Examples:**
```bash
To list all storage operations that belong to the bucket "my-bucket", run:

    $ gcloud storage operations list projects/_/buckets/my-bucket

To list operations in JSON format, run:

    $ gcloud storage operations list projects/_/buckets/my-bucket \
        --format=json

An alternative bucket format is available:

    $ gcloud storage operations list gs://my-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/operations/list)

---
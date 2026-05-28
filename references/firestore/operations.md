# gcloud firestore operations

manage Long Running Operations for Cloud Firestore

### `gcloud firestore operations cancel`

Cancel a currently-running Cloud Firestore admin operation

Cancel a currently-running Cloud Firestore admin operation.

**Synopsis:**
```
gcloud firestore operations cancel NAME
    [--database=DATABASE; default="(default)"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The unique name of the Operation to cancel, formatted as either the
   full or relative resource path:

       projects/my-app-id/databases/(default)/operations/foo

   or:

       foo
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore operations cancel --database='foo' |


**Examples:**
```bash
To cancel the currently-running exampleOperationId operation, run:

    $ gcloud firestore operations cancel exampleOperationId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/operations/cancel)

---
### `gcloud firestore operations delete`

Delete a completed Cloud Firestore admin operation

Delete a completed Cloud Firestore admin operation.

**Synopsis:**
```
gcloud firestore operations delete NAME
    [--database=DATABASE; default="(default)"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The unique name of the operation to delete, formatted as either the
   full or relative resource path:

       projects/my-app-id/databases/(default)/operations/foo

   or:

       foo
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore operations delete --database='foo' |


**Examples:**
```bash
To delete the completed exampleOperationId operation, run:

    $ gcloud firestore operations delete exampleOperationId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/operations/delete)

---
### `gcloud firestore operations describe`

Retrieves information about a Cloud Firestore admin operation

Retrieves information about a Cloud Firestore admin operation.

**Synopsis:**
```
gcloud firestore operations describe NAME
    [--database=DATABASE; default="(default)"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The unique name of the Operation to retrieve, formatted as either the
   full or relative resource path:

       projects/my-app-id/databases/(default)/operations/foo

   or:

       foo
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore operations describe --database='foo' |


**Examples:**
```bash
To retrieve information about the exampleOperationId operation, run:

    $ gcloud firestore operations describe exampleOperationId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/operations/describe)

---
### `gcloud firestore operations list`

List pending Cloud Firestore admin operations and their status

Filters are case-sensitive and have the following syntax:

    field = value [AND [field = value]] ...

Only the logical AND operator is supported; space-separated items are
treated as having an implicit AND operator.

**Synopsis:**
```
gcloud firestore operations list [--database=DATABASE; default="(default)"]
    [--filter=EXPRESSION] [--limit=LIMIT; default=100]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE | (default) | The database to operate on. The default value is (default). For example, to operate on database foo: $ gcloud firestore operations list --database='foo' |


**Examples:**
```bash
To retrieve information about recent operations, run:

    $ gcloud firestore operations list

To only list operations that are done, run:

    $ gcloud firestore operations list --filter="done:true"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/operations/list)

---
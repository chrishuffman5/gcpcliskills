# gcloud sql operations

provide commands for working with Cloud SQL instance operations

### `gcloud sql operations cancel`

Cancels a Cloud SQL instance operation

Cancels a Cloud SQL instance operation.

**Synopsis:**
```
gcloud sql operations cancel OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   Name that uniquely identifies the operation.
```

**Examples:**
```bash
To cancel an operation with the id "prod-operation-id", like
"acb40108-a483-4a8b-8a5c-e27100000032", run:

    $ gcloud sql operations cancel prod-operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/operations/cancel)

---
### `gcloud sql operations describe`

Retrieves information about a Cloud SQL instance operation

Retrieves information about a Cloud SQL instance operation.

**Synopsis:**
```
gcloud sql operations describe OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   Name that uniquely identifies the operation.
```

**Examples:**
```bash
To describe an operation with the name "prod-operation-id", run:

    $ gcloud sql operations describe prod-operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/operations/describe)

---
### `gcloud sql operations list`

Lists all instance operations for the given Cloud SQL instance

Lists all instance operations for the given Cloud SQL instance.

**Synopsis:**
```
gcloud sql operations list --instance=INSTANCE, -i INSTANCE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE, -i INSTANCE |  | Cloud SQL instance ID. |


**Examples:**
```bash
To list operations for instances with ID "prod-instance" , run:

    $ gcloud sql operations list --instance=prod-instance

To list operations for instances with ID "prod-instance" that have 10
results, run:

    $ gcloud sql operations list --instance=prod-instance --limit=10

To list operations for instances with ID "prod-instance" that have 10
results in a page, run:

    $ gcloud sql operations list --instance=prod-instance --page-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/operations/list)

---
### `gcloud sql operations wait`

Waits for one or more operations to complete

Waits for one or more operations to complete.

**Synopsis:**
```
gcloud sql operations wait OPERATION [OPERATION ...]
    [--timeout=TIMEOUT; default=300] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION [OPERATION ...]
   An identifier that uniquely identifies the operation.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--timeout` | TIMEOUT | 300 | Maximum number of seconds to wait for an operation to complete. By default, wait for 300s. Set to unlimited to wait indefinitely. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/sql/operations/wait)

---
# gcloud endpoints operations

manage Operation for various services

### `gcloud endpoints operations describe`

Describes an operation resource for a given operation name

This command will return information about an operation given the name of
that operation.

Note that the operations/ prefix of the operation name is optional and may
be omitted.

**Synopsis:**
```
gcloud endpoints operations describe OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   The name of the operation to describe.
```

**Examples:**
```bash
To describe an operation resource named
operations/serviceConfigs.my-service.1, run:

    $ gcloud endpoints operations describe serviceConfigs.my-service.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/operations/describe)

---
### `gcloud endpoints operations list`

List operations for a project

This command will list operations for a service, optionally matching a
particular filter.

**Synopsis:**
```
gcloud endpoints operations list [--filter=EXPRESSION] [--service=SERVICE]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates as True then that item is listed. The available filter fields are startTime and done. Unrecognized fields will cause an error. startTime is an ISO 8601 datetime and supports >=, >, <=, and < operators. The datetime value must be wrapped in quotation marks. For example: --filter='startTime < "2017-03-20T16:02:32"' done is a boolean value and supports = and != operators. |
| `--service` | SERVICE |  | The name of the service for which to list operations. |


**Examples:**
```bash
To list all operations for a service named api.endpoints.proj.cloud.goog,
run:

    $ gcloud endpoints operations list \
        --service=api.endpoints.proj.cloud.goog

To list only operations which are complete, add the --filter argument with
a status filter:

    $ gcloud endpoints operations list \
        --service=api.endpoints.proj.cloud.goog --filter='done = true'

To list only operations begun after a certain point in time, add the
--filter argument with an ISO 8601 datetime startTime filter:

    $ gcloud endpoints operations list \
        --service=api.endpoints.proj.cloud.goog \
        --filter='startTime >= "2017-02-01"'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/operations/list)

---
### `gcloud endpoints operations wait`

Waits for an operation to complete

This command will block until an operation has been marked as complete.

Note that the operations/ prefix of the operation name is optional and may
be omitted.

**Synopsis:**
```
gcloud endpoints operations wait OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   The name of the operation on which to wait.
```

**Examples:**
```bash
To wait on an operation named operations/serviceConfigs.my-service.1 to
complete, run:

    $ gcloud endpoints operations wait serviceConfigs.my-service.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/operations/wait)

---
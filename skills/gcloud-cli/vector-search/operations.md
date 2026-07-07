# gcloud vector-search operations

manage Operation resources

### `gcloud vector-search operations cancel`

Cancel an operation

**Synopsis:**
```
gcloud vector-search operations cancel (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation resource to cancel. This must be
specified.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.
     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To cancel an operation, run:

    $ gcloud vector-search operations cancel operation-1234567890 \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/operations/cancel)

---
### `gcloud vector-search operations delete`

Delete an operation

**Synopsis:**
```
gcloud vector-search operations delete (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation resource to delete. This must be
specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To delete an operation, run:

    $ gcloud vector-search operations delete operation-1234567890 \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/operations/delete)

---
### `gcloud vector-search operations describe`

Describe an operation

**Synopsis:**
```
gcloud vector-search operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.
     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To describe an operation, run:

    $ gcloud vector-search operations describe operation-1234567890 \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/operations/describe)

---
### `gcloud vector-search operations list`

List operations

**Synopsis:**
```
gcloud vector-search operations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | ID of the location or fully qualified identifier for the location. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. Applied after `--flatten` and `--sort-by`, before `--limit`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page for services that support paging. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list operations in project my-project and location us-central1, run:

    $ gcloud vector-search operations list \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/operations/list)

---
### `gcloud vector-search operations wait`

Wait for an operation to complete

Blocks until the specified operation finishes processing.

**Synopsis:**
```
gcloud vector-search operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation resource to wait on. This must be
specified.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.
     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To wait for an operation to complete, run:

    $ gcloud vector-search operations wait operation-1234567890 \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vector-search/operations/wait)

---

# gcloud bigtable operations

manage Cloud Bigtable operations

### `gcloud bigtable operations describe`

Describe a Cloud Bigtable operation

Describe a Cloud Bigtable operation.

**Synopsis:**
```
gcloud bigtable operations describe OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Cloud Bigtable operation to describe. This represents
a Cloud resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
To view details for operation OPERATION_ID, run:

    $ gcloud bigtable operations describe OPERATION_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/operations/describe)

---
### `gcloud bigtable operations list`

List Cloud Bigtable operations

List Cloud Bigtable operations.

**Synopsis:**
```
gcloud bigtable operations list [--instance=INSTANCE]
    [--return-partial-success=RETURN_PARTIAL_SUCCESS; default=True]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[* set the property core/project.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line. |
| `--return-partial-success` | RETURN_PARTIAL_SUCCESS | True | _[* set the property core/project.]_ If true, operations that are reachable are returned as normal, and those that are unreachable are returned in the unreachable field of the response. If false, the command will fail if any location is unreachable. Enabled by default, use --no-return-partial-success to disable. |


**Examples:**
```bash
To list all operations for the default project, run:

    $ gcloud bigtable operations list

To list all operations for instance INSTANCE_NAME, run:

    $ gcloud bigtable operations list --instance=INSTANCE_NAME

To fail the command if any location is unreachable, run:

    $ gcloud bigtable operations list --return-partial-success=false
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/operations/list)

---
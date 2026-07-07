# gcloud edge-cache operations

manage EdgeCache operations

### `gcloud edge-cache operations describe`

Describe a long-running operation

Describe a long-running operation. You can use this to inspect whether a
create or update operation was successful or the operation returned any
errors.

**Synopsis:**
```
gcloud edge-cache operations describe OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * use global location.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
To describe an operation with name simple-operation, run:

    $ gcloud edge-cache operations describe simple-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/operations/describe)

---
### `gcloud edge-cache operations list`

List long-running operations

List long-running operations.

**Synopsis:**
```
gcloud edge-cache operations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all operations, run:

    $ gcloud edge-cache operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/operations/list)

---
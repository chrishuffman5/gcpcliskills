# gcloud network-management operations

manage Network Management operations

### `gcloud network-management operations describe`

Describe a Network Management operation

Describe a Network Management operation given a valid operation name.

**Synopsis:**
```
gcloud network-management operations describe OPERATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the Network Management operation you want to
describe. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
The following command describes an operation called operation-12345:

    $ gcloud network-management operations describe operation-12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/operations/describe)

---
### `gcloud network-management operations list`

List Network Management operations

List all Network Management operations in the specified project.

You can specify the maximum number of operations to list using the --limit
flag.

**Synopsis:**
```
gcloud network-management operations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five operations:

    $ gcloud network-management operations list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-management/operations/list)

---
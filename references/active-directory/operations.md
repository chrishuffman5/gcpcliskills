# gcloud active-directory operations

manage Managed Microsoft AD operations

### `gcloud active-directory operations cancel`

Cancel a Managed Microsoft AD operation

Cancel a Managed Microsoft AD operation.

**Synopsis:**
```
gcloud active-directory operations cancel NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation name to cancel. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument NAME on the command line.
```

**Examples:**
```bash
The following command cancels an operation called
operation-1484002552235-425b144f8c3f8-81aa4b49-0830d1e9:

    $ gcloud active-directory operations cancel \
        operation-1484002552235-425b144f8c3f8-81aa4b49-0830d1e9
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/operations/cancel)

---
### `gcloud active-directory operations describe`

Describe a Managed Microsoft AD operation

Describe a Managed Microsoft AD operation given a valid operation name.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud active-directory operations describe OPERATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the Managed Microsoft AD operation you want
to describe. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

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
The following command describes an operation called
operation-1484002552235-425b144f8c3f8-81aa4b49-0830d1e9:

    $ gcloud active-directory operations describe \
        operation-1484002552235-425b144f8c3f8-81aa4b49-0830d1e9
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/operations/describe)

---
### `gcloud active-directory operations list`

List Managed Microsoft AD operations

List all Managed Microsoft AD operations in the specified project.

You can specify the maximum number of operations to list using the --limit
flag.

**Synopsis:**
```
gcloud active-directory operations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five operations:

    $ gcloud active-directory operations list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/operations/list)

---
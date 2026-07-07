# gcloud composer operations

manage Cloud Composer operations

### `gcloud composer operations delete`

Delete one or more completed Cloud Composer operations

Delete operations that are done. If more than one operation is specified,
all deletes will be attempted. If any of the deletes fail, those operations
and their failure messages will be listed on the standard error, and the
command will exit with a non-zero status.

**Synopsis:**
```
gcloud composer operations delete
    (OPERATIONS [OPERATIONS ...] : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operations to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operations on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATIONS [OPERATIONS ...]
     IDs of the operations or fully qualified identifiers for the
     operations.

     To set the operation attribute:
     + provide the argument operations on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Compute Engine region in which to create the operations.

     To set the location attribute:
     + provide the argument operations on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Examples:**
```bash
To delete the operation operation-1, run:

    $ gcloud composer operations delete operation-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/operations/delete)

---
### `gcloud composer operations describe`

Get details about an asynchronous operation

Get details about an asynchronous operation.

**Synopsis:**
```
gcloud composer operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Compute Engine region in which to create the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Examples:**
```bash
To get details for the operation operation-1, run:

    $ gcloud composer operations describe operation-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/operations/describe)

---
### `gcloud composer operations list`

Lists environment operations

Prints a table containing the following columns:
  o uuid
  o type
  o location
  o target environment
  o status
  o last updated timestamp

**Synopsis:**
```
gcloud composer operations list [--locations=[LOCATIONS,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--locations` | [LOCATIONS,...] |  | _[* set the property core/project.]_ IDs of the locations or fully qualified identifiers for the locations. To set the location attribute: + provide the argument --locations on the command line. |


**Examples:**
```bash
To list the environment operations in locations us-central1 and
europe-west3, run:

    $ gcloud composer operations list \
        --locations=us-central1,europe-west3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/operations/list)

---
### `gcloud composer operations wait`

Wait for asynchronous operation to complete

Wait for asynchronous operation to complete.

**Synopsis:**
```
gcloud composer operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to wait for. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Compute Engine region in which to create the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property composer/location.
```

**Examples:**
```bash
To wait for the asynchronous operation operation-1 in the location
us-central1 to complete, run:

    $ gcloud composer operations wait operation-1 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/composer/operations/wait)

---
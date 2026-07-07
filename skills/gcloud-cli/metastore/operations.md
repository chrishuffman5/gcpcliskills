# gcloud metastore operations

manage Dataproc Metastore operations

### `gcloud metastore operations cancel`

Cancel a Dataproc Metastore operation

Cancel a Dataproc Metastore operation.

**Synopsis:**
```
gcloud metastore operations cancel (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation cancel. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     Location to which the operation belongs.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To cancel an active Dataproc Metastore operation with the name operation-1
in location us-central1, run:

    $ gcloud metastore operations cancel operation-1 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/operations/cancel)

---
### `gcloud metastore operations delete`

Delete one or more completed Dataproc Metastore operations

Delete one or more completed Dataproc Metastore operations.

**Synopsis:**
```
gcloud metastore operations delete
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
     Location to which the operations belongs.

     To set the location attribute:
     + provide the argument operations on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To delete a Dataproc Metastore operation with the name operation-1 in
location us-central1, run:

    $ gcloud metastore operations delete operation-1 \
        --location=us-central1

To delete multiple Dataproc Metastore services with the name operation-1
and operation-2 in the same location us-central1, run:

    $ gcloud metastore operations delete operation-1 operation-2 \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/operations/delete)

---
### `gcloud metastore operations describe`

Show metadata for a Dataproc Metastore operation

Display all metadata associated with a Metastore operation given a valid
operation name.

**Synopsis:**
```
gcloud metastore operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Dataproc
Metastore operation you want to describe. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To display the metadata for an operation named my-operation in the default
region, run:

    $ gcloud metastore operations describe my-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/operations/describe)

---
### `gcloud metastore operations list`

List Dataproc Metastore operations

List all Metastore operations under the specified location.

To specify the maximum number of operations to list, use the --limit flag.

**Synopsis:**
```
gcloud metastore operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property metastore/location. |


**Examples:**
```bash
To list up to five operations in location us-central1, run:

    $ gcloud metastore operations list --location=us-central1 --limit=5

To list all operations in all locations, run:

    $ gcloud metastore operations list --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/operations/list)

---
### `gcloud metastore operations wait`

Poll a long-running Dataproc Metastore operation until it completes

Poll a long-running Dataproc Metastore operation until it completes. When
the operation is complete, this command will display the results of the
operation.

**Synopsis:**
```
gcloud metastore operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - ID for the operation to poll until complete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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
     The location of the Dataproc Metastore service.

     If not specified, will use default metastore/location.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To poll a long-running Dataproc Metastore operation named 'my-operation'
until it completes, run the following:

    $ gcloud metastore operations wait my-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/operations/wait)

---
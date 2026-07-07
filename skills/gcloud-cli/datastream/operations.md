# gcloud datastream operations

manage Datastream operations

### `gcloud datastream operations cancel`

Cancel a Datastream operation

Cancel a Datastream operation.

**Synopsis:**
```
gcloud datastream operations cancel (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Operation resource - Datastream operation to cancel.
The arguments in this group can be used to specify the attributes of this
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
     The location of the resources.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To cancel an operation, run:

    $ gcloud datastream operations cancel OPERATION \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/operations/cancel)

---
### `gcloud datastream operations delete`

Delete a Datastream operation

Delete a Datastream operation.

**Synopsis:**
```
gcloud datastream operations delete (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Operation resource - Datastream operation to delete.
The arguments in this group can be used to specify the attributes of this
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
     The location of the resources.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete an operation.

    $ gcloud datastream operations delete OPERATION \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/operations/delete)

---
### `gcloud datastream operations describe`

Show details about a operation

Show details about a operation.

**Synopsis:**
```
gcloud datastream operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation you want to get the details of. The
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
     The location of the resources.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about a operation, run:

    $ gcloud datastream operations describe my-operation \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/operations/describe)

---
### `gcloud datastream operations list`

List operations

List operations.

**Synopsis:**
```
gcloud datastream operations list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all operations in a project and region 'us-central1', run:

    $ gcloud datastream operations list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/operations/list)

---
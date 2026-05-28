# gcloud network-services operations

manage Network Services Operations

### `gcloud network-services operations cancel`

Cancel a Network Services long running operation

Cancel a Network Services long running operation.

**Synopsis:**
```
gcloud network-services operations cancel (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to cancel. The arguments in
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

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command cancels an operation with the full name
OPERATION_NAME:

    $ gcloud network-services operations cancel OPERATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/operations/cancel)

---
### `gcloud network-services operations describe`

Show details of a Network Services long running operation

Show details of a Network Services long running operation.

**Synopsis:**
```
gcloud network-services operations describe
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to describe. The arguments in
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

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command describes an operation with the full name
OPERATION_NAME:

    $ gcloud network-services operations describe OPERATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/operations/describe)

---
### `gcloud network-services operations list`

List all Network Services long running operations

List all Network Services long running operations.

**Synopsis:**
```
gcloud network-services operations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
The following command lists all operations in the current project and in
location global:

    $ gcloud network-services operations list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/operations/list)

---
### `gcloud network-services operations wait`

Poll a Network Services long running operation

Poll a Network Services long running operation.

**Synopsis:**
```
gcloud network-services operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to poll. The arguments in this
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
     The location Id.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command polls an operation with the full name OPERATION_NAME:

    $ gcloud network-services operations wait OPERATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/operations/wait)

---
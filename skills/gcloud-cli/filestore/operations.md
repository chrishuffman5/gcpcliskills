# gcloud filestore operations

read and manipulate Filestore operations

### `gcloud filestore operations cancel`

Cancel a Filestore operation

Cancels a Filestore operation. The server makes a best effort to cancel the
operation, but success is not guaranteed. Clients can use the filestore
operations describe command to check whether the cancellation succeeded or
not.

**Synopsis:**
```
gcloud filestore operations cancel (OPERATION : --zone=ZONE)
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to cancel. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
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

  --zone=ZONE
     The zone of the operation.

     To set the zone attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument region on the command line;
     + provide the argument location on the command line;
     + set the property filestore/zone;
     + set the property filestore/region;
     + set the property filestore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |


**Examples:**
```bash
To cancel a Filestore operation named ``NAME" in the ``us-central1-c" zone,
run:

    $ gcloud filestore operations cancel NAME --zone=us-central1-c

To cancel a Filestore operation named ``NAME" in the ``us-central1" region,
run:

    $ gcloud filestore operations cancel NAME --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/operations/cancel)

---
### `gcloud filestore operations describe`

Describe a Filestore operation

Describe a Filestore operation.

**Synopsis:**
```
gcloud filestore operations describe (OPERATION : --zone=ZONE)
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
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

  --zone=ZONE
     The zone of the operation.

     To set the zone attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + provide the argument region on the command line;
     + provide the argument location on the command line;
     + set the property filestore/zone;
     + set the property filestore/region;
     + set the property filestore/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |


**Examples:**
```bash
The following command shows the details for the Filestore operation named
NAME in us-central1-c.

    $ gcloud filestore operations describe NAME --location=us-central1-c
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/operations/describe)

---
### `gcloud filestore operations list`

List all Filestore operations

List all Filestore operations.

**Synopsis:**
```
gcloud filestore operations list [--location=LOCATION] [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Cloud Filestore instance/operation. |


**Examples:**
```bash
The following command lists a maximum of five Filestore operations sorted
alphabetically by name in descending order:

    $ gcloud filestore operations list --limit=5 --sort-by=~name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/operations/list)

---
# gcloud backup-dr operations

manage Backup and DR operations

### `gcloud backup-dr operations describe`

Describe an operation

Describe a Backup and DR operation.

**Synopsis:**
```
gcloud backup-dr operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Backup and DR operation to describe. The arguments in
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
     Location ID of the resource.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for operation 'OPERATION', run:

    $ gcloud backup-dr operations describe OPERATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/operations/describe)

---
### `gcloud backup-dr operations list`

List all operations

List all Backup and DR operations.

**Synopsis:**
```
gcloud backup-dr operations list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all operations in a location my-location, run:

    $ gcloud backup-dr operations list --location=my-location

To list all operations in all locations, run:

    $ gcloud backup-dr operations list --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/operations/list)

---
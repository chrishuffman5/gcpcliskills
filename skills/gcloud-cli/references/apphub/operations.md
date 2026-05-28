# gcloud apphub operations

manage App Hub Operations (long-running operations)

### `gcloud apphub operations describe`

Describe an Apphub operation (long-running operation)

Describe an Apphub operation (long-running operation).

**Synopsis:**
```
gcloud apphub operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The Operation ID. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
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
     The Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a specific apphub operation with the name my-operation, run:

    $ gcloud apphub operations describe my-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/operations/describe)

---
### `gcloud apphub operations list`

List Apphub operations (long-running operations)

List Apphub operations (long-running operations).

**Synopsis:**
```
gcloud apphub operations list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all operations, run:

    $ gcloud apphub operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/operations/list)

---
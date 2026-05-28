# gcloud certificate-manager operations

manage Certificate Manager operations

### `gcloud certificate-manager operations describe`

Describe a long-running operation

Describe a Certificate Manager long-running operation.

**Synopsis:**
```
gcloud certificate-manager operations describe
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Certificate Manager operation to describe. The
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
     Certificate Manager location.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To describe an operation with name simple-operation, run:

    $ gcloud certificate-manager operations describe simple-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/operations/describe)

---
### `gcloud certificate-manager operations list`

List long-running operations

List Certificate Manager long-running operations.

**Synopsis:**
```
gcloud certificate-manager operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + default value of location is [global]. |


**Examples:**
```bash
To list all operations, run:

    $ gcloud certificate-manager operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/operations/list)

---
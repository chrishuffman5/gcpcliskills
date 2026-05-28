# gcloud compliance-manager operations

manage Operation resources

### `gcloud compliance-manager operations cancel`

Cancel operations

Cancel an operation

**Synopsis:**
```
gcloud compliance-manager operations cancel
    (OPERATION : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource to be cancelled.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the operation resource.

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To cancel the operation, run:

    $ gcloud compliance-manager operations cancel
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/operations/cancel)

---
### `gcloud compliance-manager operations delete`

Delete operations

Delete an operation

**Synopsis:**
```
gcloud compliance-manager operations delete
    (OPERATION : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource to be deleted. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the operation resource.

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To delete the operation, run:

    $ gcloud compliance-manager operations delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/operations/delete)

---
### `gcloud compliance-manager operations describe`

Describe operations

Describe an operation

**Synopsis:**
```
gcloud compliance-manager operations describe
    (OPERATION : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the operation resource.

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To describe the operation, run:

    $ gcloud compliance-manager operations describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/operations/describe)

---
### `gcloud compliance-manager operations list`

List operations

**Synopsis:**
```
gcloud compliance-manager operations list
    (--location=LOCATION : --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The organization id of the location resource. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list all operations, run:

    $ gcloud compliance-manager operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/operations/list)

---
### `gcloud compliance-manager operations wait`

Wait operations

Wait an operation

**Synopsis:**
```
gcloud compliance-manager operations wait
    (OPERATION : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource to wait on. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The organization id of the operation resource.

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To wait the operation, run:

    $ gcloud compliance-manager operations wait
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compliance-manager/operations/wait)

---
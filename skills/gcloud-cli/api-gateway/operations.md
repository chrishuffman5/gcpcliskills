# gcloud api-gateway operations

manage operations for Cloud API Gateways

### `gcloud api-gateway operations cancel`

Cancel a Cloud API Gateway operation

Cancel a Cloud API Gateway operation.

**Synopsis:**
```
gcloud api-gateway operations cancel (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation to cancel. The arguments in
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
     Cloud location for operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To cancel a Cloud API Gateway operation named NAME in the us-central1
region, run:

    $ gcloud api-gateway operations cancel NAME --location=us-central1

To cancel a Cloud API Gateway operation with a resource name of RESOURCE,
run:

    $ gcloud api-gateway operations cancel RESOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/operations/cancel)

---
### `gcloud api-gateway operations describe`

Show details about the Cloud API Gateway operation

Show details about the Cloud API Gateway operation.

**Synopsis:**
```
gcloud api-gateway operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

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
     Cloud location for operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a Cloud API Gateway operation named NAME in the us-central1
region, run:

    $ gcloud api-gateway operations describe NAME --location=us-central1

To describe a Cloud API Gateway operation with a resource name of RESOURCE,
run:

    $ gcloud api-gateway operations describe RESOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/operations/describe)

---
### `gcloud api-gateway operations list`

List API Gateway operations

List API Gateway operations.

**Synopsis:**
```
gcloud api-gateway operations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + Location for API and API Configs. Defaults to a wildcard. |


**Examples:**
```bash
To list all Cloud API Gateway operations, run:

    $ gcloud api-gateway operations list

To list all Cloud API Gateway operations in the us-central1 region, run:

    $ gcloud api-gateway operations list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/operations/list)

---
### `gcloud api-gateway operations wait`

Wait for a Cloud API Gateway operation to complete

Wait for a Cloud API Gateway operation to complete.

**Synopsis:**
```
gcloud api-gateway operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation to poll. The arguments in
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
     Cloud location for operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To wait for a Cloud API Gateway operation named NAME in the us-central1
region, run:

    $ gcloud api-gateway operations wait NAME --location=us-central1

To wait for a Cloud API Gateway operation with a resource name of RESOURCE,
run:

    $ gcloud api-gateway operations wait RESOURCE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway/operations/wait)

---
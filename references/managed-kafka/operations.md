# gcloud managed-kafka operations

view Managed Service for Apache Kafka operations

### `gcloud managed-kafka operations describe`

Describe a Managed Service for Apache Kafka operation

Describe a Managed Service for Apache Kafka operation.

**Synopsis:**
```
gcloud managed-kafka operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Identifies the operation for details to be displayed.
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
     ID of the location of the Managed Service for Apache Kafka resource.
     See
     https://cloud.google.com/managed-service-for-apache-kafka/docs/locations
     for a list of supported locations.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an operation named myoperation located in us-central1, run the
following:

    $ gcloud managed-kafka operations describe myoperation \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/operations/describe)

---
### `gcloud managed-kafka operations list`

List all Managed Service for Apache Kafka operations in a given location

List all Managed Service for Apache Kafka operations in a given location.
To specify the maximum number of operations to list, use the --limit flag.

**Synopsis:**
```
gcloud managed-kafka operations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all clusters in a given location, such as us-central1, run the
following:

    $ gcloud managed-kafka operations list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/managed-kafka/operations/list)

---
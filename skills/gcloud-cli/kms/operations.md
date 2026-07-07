# gcloud kms operations

commands for managing operations

### `gcloud kms operations describe`

View the details of an operation

View the details of an operation.

**Synopsis:**
```
gcloud kms operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The KMS operation resource. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view the details of an operation, run:

    $ gcloud kms operations describe operation_id --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/operations/describe)

---
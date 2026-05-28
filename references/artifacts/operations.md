# gcloud artifacts operations

manage Artifact Registry long-running operations

### `gcloud artifacts operations describe`

Describe an Artifact Registry operation

Describe an Artifact Registry operation given the operation id.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud artifacts operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The Artifact Registry operation to describe. The
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
     Location of the operation. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.
```

**Examples:**
```bash
The following command describes an operation with id
06d2817d-6566-47c3-88a0-295ef51eb434:

    $ gcloud artifacts operations describe \
        06d2817d-6566-47c3-88a0-295ef51eb434
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/operations/describe)

---
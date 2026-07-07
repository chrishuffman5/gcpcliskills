# gcloud audit-manager operations

check audit operation status

### `gcloud audit-manager operations describe`

Describe Audit operation

Obtain details about an audit operation.

**Synopsis:**
```
gcloud audit-manager operations describe
    (OPERATION : --folder=FOLDER --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [auditmanager.folders.locations.operationDetails,
   auditmanager.projects.locations.operationDetails].

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     The folder for the operation.

     To set the folder attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type
       [auditmanager.folders.locations.operationDetails].

  --location=LOCATION
     The location for the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an Audit operation in the us-central1 region, belonging to a
project with ID 123, with operation ID operation-456, run:

    $ gcloud audit-manager operations describe operation-456 \
        --project=123 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/audit-manager/operations/describe)

---
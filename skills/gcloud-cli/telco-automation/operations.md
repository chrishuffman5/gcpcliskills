# gcloud telco-automation operations

command group for working with telco automation operations

### `gcloud telco-automation operations describe`

Get description of a long-running telco automation operation

Get information about a long-running telco automation operation.

**Synopsis:**
```
gcloud telco-automation operations describe
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. The arguments in
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
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get information about a long-running operation with name test-operation
in region us-central1, run the following command:

    $ gcloud telco-automation operations describe test-operation \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation/operations/describe)

---
### `gcloud telco-automation operations wait`

Poll long-running telco automation operation until it completes

Poll a long-running telco automation operation until it completes. When the
operation is complete, this command will display the results of the
analysis.

**Synopsis:**
```
gcloud telco-automation operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - ID for the operation to poll until complete. The
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
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To poll a long-running telco automation operation named test-operation in
region us-central1 until it completes, run the following:

    $ gcloud telco-automation operations wait test-operation \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation/operations/wait)

---
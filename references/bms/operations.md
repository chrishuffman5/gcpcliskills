# gcloud bms operations

manage operations in Bare Metal Solution

### `gcloud bms operations describe`

Show metadata for a Bare Metal Solution operation

Display all metadata associated with a Bare Metal Solution operation given
a valid operation name.

**Synopsis:**
```
gcloud bms operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Bare Metal
Solution operation you want to describe. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To display the metadata for an operation named my-operation, run:

    $ gcloud bms operations describe my-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/operations/describe)

---
### `gcloud bms operations wait`

Poll a long-running Bare Metal Solution operation until it completes

Poll a long-running Bare Metal Solution operation until it completes. When
the operation is complete, this command will display the results of the
operation.

**Synopsis:**
```
gcloud bms operations wait (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Bare Metal
Solution operation you want to wait for. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
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

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To poll a long-running Bare Metal Solution operation named 'my-operation'
until it completes, run the following:

    $ gcloud bms operations wait my-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/operations/wait)

---
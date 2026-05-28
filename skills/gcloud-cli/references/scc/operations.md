# gcloud scc operations

manage Cloud SCC (Security Command Center) operations

### `gcloud scc operations describe`

Describe a Cloud SCC's long running scan operation

Describe a Cloud SCC's long running scan operation.

**Synopsis:**
```
gcloud scc operations describe (OPERATION : --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Cloud SCC's API operation to describe. The arguments
in this group can be used to specify the attributes of this resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     (Optional) If the full resource name isn't provided e.g.
     organizations/123, then provide the organization id which is the
     suffix of the organization. Example: organizations/123, the id is
     123.

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + Set the organization property in configuration using gcloud
       config set scc/organization if it is not specified in command
       line..
```

**Examples:**
```bash
Return long running scan operation status for operation id
(9c5fa5e5-e368-439a-baa4-08c17b77ec23) and organization 123456. Operation
id is obtained using run-discovery command:

    $ gcloud scc operations describe \
        9c5fa5e5-e368-439a-baa4-08c17b77ec23 --organization=123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/operations/describe)

---
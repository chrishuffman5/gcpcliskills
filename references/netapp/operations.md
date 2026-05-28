# gcloud netapp operations

read and manage Cloud NetApp Files Operations

### `gcloud netapp operations describe`

Describe a Cloud NetApp Files operation

Describe a Cloud NetApp Files operation.

**Synopsis:**
```
gcloud netapp operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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
     The location of the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property netapp/location.
```

**Examples:**
```bash
The following command shows the details for the NetApp Files operation
named NAME.

    $ gcloud netapp operations describe NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/operations/describe)

---
### `gcloud netapp operations list`

List Cloud NetApp Files operations

Lists all Cloud NetApp Files operations.

**Synopsis:**
```
gcloud netapp operations list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + uses all locations by default.; + set the property netapp/location. |


**Examples:**
```bash
The following command lists NetApp Files operations under a given location

    $ gcloud netapp operations list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/operations/list)

---
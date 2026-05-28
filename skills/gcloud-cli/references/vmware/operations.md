# gcloud vmware operations

list and describe operations in Google Cloud VMware Engine

### `gcloud vmware operations describe`

Describe a Google Cloud VMware Engine operation

Describe a VMware Engine operation. An operation contains information about
the status of a previous request.

**Synopsis:**
```
gcloud vmware operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

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
     Location of the private cloud or cluster.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To get details about an operation on a private cloud with the operation ID
operation-111-222-333-444, run:

    $ gcloud vmware operations describe operation-111-222-333-444 \
        --location=us-central1 --project=my-project

Or:

    $ gcloud vmware operations describe operation-111-222-333-444 \
        --location=us-central1

In the second example, the location is taken from gcloud property
compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/operations/describe)

---
### `gcloud vmware operations list`

List Google Cloud VMware Engine operations

List VMware Engine operations in a location.

**Synopsis:**
```
gcloud vmware operations list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list VMware Engine operations in a location us-west2-a, run:

    $ gcloud vmware operations list --location=us-west2-a

Or:

    $ gcloud vmware operations list

In the second example, the location is taken from gcloud property
compute/zone.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/operations/list)

---
# gcloud network-connectivity operations

manage Network Connectivity Center operations

### `gcloud network-connectivity operations describe`

Describe a Network Connectivity Center operation

Retrieve details about an operation; this command is useful if you want to
check on a long-running operation.

**Synopsis:**
```
gcloud network-connectivity operations describe
    (OPERATION : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Name of the operation to describe. The arguments in
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

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To describe operation operation-12345 in us-central1, run:

    $ gcloud network-connectivity operations describe operation-12345 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/operations/describe)

---
### `gcloud network-connectivity operations list`

List Network Connectivity Center operations

Retrieve and display a list of operations in the specified region, sorted
by creation time.

To specify the maximum number of operations to return, use the --limit
flag.

**Synopsis:**
```
gcloud network-connectivity operations list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all operations in region us-central1, run:

    $ gcloud network-connectivity operations list --region=us-central1

To list a maximum of five operations in us-central1, run:

    $ gcloud network-connectivity operations list --region=us-central1 \
        --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/operations/list)

---
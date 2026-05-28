# gcloud source-manager operations

manage Secure Source Manager operations

### `gcloud source-manager operations describe`

Describe a Secure Source Manager operation

Get details of a Secure Source Manager operation.

**Synopsis:**
```
gcloud source-manager operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation you want to describe. The arguments in
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
     Secure Source Manager location.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To describe a Secure Source Manager operation named 'my-operation' in
location 'us-central1' under the current project, run:

    $ gcloud source-manager operations describe my-operation \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/operations/describe)

---
### `gcloud source-manager operations list`

List Secure Source Manager operations

List all Secure Source Manager operations.

**Synopsis:**
```
gcloud source-manager operations list --region=REGION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all Secure Source Manager operations in location 'us-central1'
under the current project, run:

    $ gcloud source-manager operations list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source-manager/operations/list)

---
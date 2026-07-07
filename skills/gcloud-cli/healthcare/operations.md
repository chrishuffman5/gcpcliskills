# gcloud healthcare operations

manage Cloud Healthcare API operations

### `gcloud healthcare operations describe`

Describe a Cloud Healthcare API operation

Describe a Cloud Healthcare API operation.

**Synopsis:**
```
gcloud healthcare operations describe
    (OPERATION : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Cloud Healthcare API operation to describe. The
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

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To describe the operation '1234567890' in the dataset 'test-dataset', run:

    $ gcloud healthcare operations describe 1234567890 \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/operations/describe)

---
### `gcloud healthcare operations list`

List Cloud Healthcare API operations

List Cloud Healthcare API operations.

**Synopsis:**
```
gcloud healthcare operations list (--dataset=DATASET : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dataset` | DATASET |  | _[This must be specified.]_ ID of the dataset or fully qualified identifier for the dataset. To set the dataset attribute: + provide the argument --dataset on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location. To set the location attribute: + provide the argument --dataset on the command line with a fully specified name; + provide the argument --location on the command line; + set the property healthcare/location. |


**Examples:**
```bash
To list the operations in the dataset 'test-dataset', run:

    $ gcloud healthcare operations list --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/operations/list)

---
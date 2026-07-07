# gcloud database-migration operations

manage Database Migration Service operations

### `gcloud database-migration operations delete`

Delete a Database Migration Service operation

Delete a Database Migration Service operation.

**Synopsis:**
```
gcloud database-migration operations delete (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Operation resource - Database Migration Service
operation to delete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
     The name of the region.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To delete an operation.

    $ gcloud database-migration operations delete OPERATION \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/operations/delete)

---
### `gcloud database-migration operations describe`

Show details about a operation

Show details about a operation.

**Synopsis:**
```
gcloud database-migration operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation you want to get the details of. The
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

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To show details about a operation, run:

    $ gcloud database-migration operations describe my-operation \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/operations/describe)

---
### `gcloud database-migration operations list`

List operations

List operations.

**Synopsis:**
```
gcloud database-migration operations list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all operations in a project and region 'us-central1', run:

    $ gcloud database-migration operations list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/operations/list)

---
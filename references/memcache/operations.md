# gcloud memcache operations

manage Cloud Memorystore Memcached operations

### `gcloud memcache operations delete`

Delete a Memorystore Memcached operation

Delete a Memorystore Memcached operation given a valid operation name.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud memcache operations delete (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Memorystore
Memcached operation to delete. The arguments in this group can be used to
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

  --region=REGION
     The name of the Memcached region of the operation. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Examples:**
```bash
To delete an operation named my-memcache-operation in region us-central1,
run:

    $ gcloud memcache operations delete my-memcache-operation \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/operations/delete)

---
### `gcloud memcache operations describe`

Display metadata for a Memorystore Memcached operation

Display all metadata associated with a Memorystore Memcached operation
given a valid operation name.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud memcache operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Memorystore
Memcached operation to describe. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
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

  --region=REGION
     The name of the Memcached region of the operation. Overrides the
     default memcache/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property memcache/region.
```

**Examples:**
```bash
To display the metadata for an operation named my-memcache-operation in
region us-central1, run:

    $ gcloud memcache operations describe my-memcache-operation \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/operations/describe)

---
### `gcloud memcache operations list`

List Memorystore Memcached operations

List all Memorystore Memcached operations under the specified project and
region.

Specify the maximum number of operations to list using the --limit flag.

**Synopsis:**
```
gcloud memcache operations list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property memcache/region. |


**Examples:**
```bash
To list all operations in region us-central1, run:

    $ gcloud memcache operations list --region=us-central1

To list up to five operations in region us-central1, run:

    $ gcloud memcache operations list --limit=5 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/operations/list)

---
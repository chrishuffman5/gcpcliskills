# gcloud redis operations

manage Cloud Memorystore Redis operations

### `gcloud redis operations cancel`

Cancel a Memorystore Redis import or export operation

Cancel a Memorystore Redis import or export operation.

An export operation can be canceled at any time. This does not impact the
data or availability of an instance.

An import operation can also be canceled. Note that the cancellation will
result in the instance recovering with a fully flushed cache.

**Synopsis:**
```
gcloud redis operations cancel (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Memorystore
Redis operation you want to cancel. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
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
     The name of the Redis region of the operation. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To cancel an operation named my-redis-operation in the default region, run:

    $ gcloud redis operations cancel my-redis-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/operations/cancel)

---
### `gcloud redis operations describe`

Show metadata for a Memorystore Redis operation

Display all metadata associated with a Redis operation given a valid
operation name.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud redis operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Memorystore
Redis operation you want to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
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
     The name of the Redis region of the operation. Overrides the default
     redis/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property redis/region.
```

**Examples:**
```bash
To display the metadata for an operation named my-redis-operation in the
default region, run:

    $ gcloud redis operations describe my-redis-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/operations/describe)

---
### `gcloud redis operations list`

List Memorystore Redis operations

List all Redis operations under the specified project and region.

To specify the maximum number of operations to list, use the --limit flag.

**Synopsis:**
```
gcloud redis operations list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property redis/region. |


**Examples:**
```bash
To list up to five operations, run:

    $ gcloud redis operations list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/operations/list)

---
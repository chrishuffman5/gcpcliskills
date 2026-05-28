# gcloud looker operations

manage Looker operations

### `gcloud looker operations cancel`

Cancel a Looker import or export operation

Cancel a Looker import or export operation.

**Synopsis:**
```
gcloud looker operations cancel (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Looker operation
you want to describe. The arguments in this group can be used to specify
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
     The name of the Looker region of the operation. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Examples:**
```bash
To cancel an operation named my-looker-operation in the default region,
run:

    $ gcloud looker operations cancel my-looker-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/operations/cancel)

---
### `gcloud looker operations describe`

Show metadata for a Looker operation

Display all metadata associated with a Looker operation given a valid
operation name.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud looker operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - Arguments and flags that specify the Looker operation
you want to describe. The arguments in this group can be used to specify
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
     The name of the Looker region of the operation. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Examples:**
```bash
To display the metadata for an operation named my-looker-operation in the
default region, run:

    $ gcloud looker operations describe my-looker-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/operations/describe)

---
### `gcloud looker operations list`

List Looker operations

List all Looker operations under the specified project and region.

To specify the maximum number of operations to list, use the --limit flag.

**Synopsis:**
```
gcloud looker operations list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property looker/region. |


**Examples:**
```bash
To list up to five operations, run:

    $ gcloud looker operations list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/operations/list)

---
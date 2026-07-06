# gcloud datalineage processes

manage Data Lineage processes

### `gcloud datalineage processes create`

Create a Data Lineage process

Create a new Data Lineage process.

**Synopsis:**
```
gcloud datalineage processes create (PROCESS : --location=LOCATION)
    [--attributes=[ATTRIBUTES,...]] [--display-name=DISPLAY_NAME]
    [--origin-name=ORIGIN_NAME]
    [--origin-source-type=ORIGIN_SOURCE_TYPE; default="custom"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Process resource - The process to create. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument PROCESS on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROCESS
     ID of the process or fully qualified identifier for the process.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the process.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | Additional attributes for the process. |
| `--display-name` | DISPLAY_NAME |  | A human-readable name for the process. |
| `--origin-name` | ORIGIN_NAME |  | The name of the origin (e.g. the application or pipeline name). |
| `--origin-source-type` | ORIGIN_SOURCE_TYPE | `custom` | Type of the source. Must be one of: `bigquery`, `composer`, `custom`, `data-fusion`, `dataflow`, `dataproc`, `looker-core`, `looker-studio`, `source-type-unspecified`, `vertex-ai`. |

**Examples:**
```bash
# To create a process with ID my-process in location us-central1 with
# display name "My Process" and origin custom, run:
gcloud datalineage processes create my-process --location=us-central1 \
    --display-name="My Process" --origin-source-type=custom \
    --origin-name="my-app"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/processes/create)

---
### `gcloud datalineage processes delete`

Delete a Data Lineage process

Delete a Data Lineage process. All associated runs and lineage events will also be deleted.

**Synopsis:**
```
gcloud datalineage processes delete (PROCESS : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Process resource - The process to delete.

To set the project attribute:
 * provide the argument PROCESS on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROCESS
     ID of the process or fully qualified identifier for the process.

  --location=LOCATION
     The location of the process.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |

**Examples:**
```bash
# To delete a process with ID my-process in location us-central1, run:
gcloud datalineage processes delete my-process --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/processes/delete)

---
### `gcloud datalineage processes describe`

Describe a Data Lineage process

Display all metadata associated with a Data Lineage process.

**Synopsis:**
```
gcloud datalineage processes describe (PROCESS : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Process resource - The process to describe.

To set the project attribute:
 * provide the argument PROCESS on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROCESS
     ID of the process or fully qualified identifier for the process.

  --location=LOCATION
     The location of the process.
```

**Examples:**
```bash
# To describe a process with ID my-process in location us-central1, run:
gcloud datalineage processes describe my-process --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/processes/describe)

---
### `gcloud datalineage processes list`

List Data Lineage processes

List all Data Lineage processes in the specified location.

**Synopsis:**
```
gcloud datalineage processes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | ID of the location or fully qualified identifier for the location. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. |

**Examples:**
```bash
# To list processes in location us, run:
gcloud datalineage processes list --location=us
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/processes/list)

---
### `gcloud datalineage processes update`

Update a data lineage process

Update a data lineage process with new attributes and/or display name.

**Synopsis:**
```
gcloud datalineage processes update (PROCESS : --location=LOCATION)
    [--attributes=[ATTRIBUTES,...]] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Process resource - The process to update.

To set the project attribute:
 * provide the argument PROCESS on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROCESS
     ID of the process or fully qualified identifier for the process.

  --location=LOCATION
     The location of the process.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [ATTRIBUTES,...] |  | The new attributes of the process. This will replace any existing attributes. |
| `--display-name` | DISPLAY_NAME |  | The new display name of the process. |

**Examples:**
```bash
# To update the display name of a process:
gcloud datalineage processes update my-process --location=us-central1 \
    --display-name="New Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/processes/update)

---

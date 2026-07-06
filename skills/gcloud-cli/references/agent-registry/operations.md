# gcloud agent-registry operations

manage Operation resources

Agent Registry mutations (services / bindings create, update, delete) run as long-running operations; use this group to inspect, wait on, cancel, or clean up those operations. Note: the official operations command pages cite the `agentregistry/v1alpha` API even on the GA track.

### `gcloud agent-registry operations cancel`

Cancel operations

Cancels an operation within the Agent Registry service.

**Synopsis:**
```
gcloud agent-registry operations cancel (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to cancel, specified by name.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To cancel the operation, run:

    $ gcloud agent-registry operations cancel
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/operations/cancel)

---
### `gcloud agent-registry operations delete`

Delete operations

Removes an operation from the Agent Registry service.

**Synopsis:**
```
gcloud agent-registry operations delete (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to delete, specified by name.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To delete the operation, run:

    $ gcloud agent-registry operations delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/operations/delete)

---
### `gcloud agent-registry operations describe`

Describe operations

Retrieves and displays details about a specific operation in the Agent Registry.

**Synopsis:**
```
gcloud agent-registry operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to describe, specified by name.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To describe the operation, run:

    $ gcloud agent-registry operations describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/operations/describe)

---
### `gcloud agent-registry operations list`

List operations

Retrieves a list of operations from the Agent Registry service.

**Synopsis:**
```
gcloud agent-registry operations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. The project attribute can be set via `--project` or the `core/project` property. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter expression to each resource item to be listed; the item is listed if the expression evaluates True. See `gcloud topic filters`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list (applied after sorting and filtering). |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list all operations, run:

    $ gcloud agent-registry operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/operations/list)

---
### `gcloud agent-registry operations wait`

Wait operations

Wait an operation.

**Synopsis:**
```
gcloud agent-registry operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The name of the operation resource to wait on.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the operation resource.
```

**Examples:**
```bash
To wait the operation, run:

    $ gcloud agent-registry operations wait
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/operations/wait)

---

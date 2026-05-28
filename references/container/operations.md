# gcloud container operations

get and list operations for Google Kubernetes Engine clusters

### `gcloud container operations cancel`

Cancel a running operation

Cancel a running operation.

Cancel is a best-effort method for aborting a running operation. Operations
that have already completed can not be cancelled. If the operation has
passed the "point of no-return", cancel will have no effect.

An example of "point of no-return" in the context of Upgrade operations
would be if all the nodes have been upgraded but the operation hasn't been
marked as complete.

Only node pool upgrade operations support cancellation.

**Synopsis:**
```
gcloud container operations cancel OPERATION_ID
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_ID
   The operation id to cancel.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To cancel an operation, run:

    $ gcloud container operations cancel sample-operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/operations/cancel)

---
### `gcloud container operations describe`

Describe an operation

Describe an operation.

**Synopsis:**
```
gcloud container operations describe OPERATION_ID
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_ID
   The operation id to look up.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To describe an operation, run:

    $ gcloud container operations describe sample-operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/operations/describe)

---
### `gcloud container operations list`

List operations for container clusters

List operations for container clusters.

**Synopsis:**
```
gcloud container operations list
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To list operations, run:

    $ gcloud container operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/operations/list)

---
### `gcloud container operations wait`

Poll an operation for completion

Poll an operation for completion.

**Synopsis:**
```
gcloud container operations wait OPERATION_ID
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_ID
   The operation id to poll.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To poll an operation for completion, run:

    $ gcloud container operations wait sample-operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/operations/wait)

---
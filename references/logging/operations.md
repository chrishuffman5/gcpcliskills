# gcloud logging operations

manage long running operations

### `gcloud logging operations cancel`

Cancel a long running operation

Cancel a long running operation with given OPERATION_ID in given LOCATION.
This operation can be a copy_log_entries operation which is scheduled
before.

**Synopsis:**
```
gcloud logging operations cancel OPERATION_ID --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_ID
   The Id of the operation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the operation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the operation to cancel. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the operation to cancel. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the operation to cancel. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the operation to cancel. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To cancel an operation, run:

    $ gcloud logging operations cancel OPERATION_ID --location=LOCATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/operations/cancel)

---
### `gcloud logging operations describe`

Display the information about a long running operation

Display the information about a long running operation which was scheduled
before. For example, a copy_log_entries operation scheduled by command:
"gcloud alpha logging copy BUCKET_ID DESTINATION --location=LOCATION"
OPERATION_ID and LOCATION are required to locate such operation.

**Synopsis:**
```
gcloud logging operations describe OPERATION_ID --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_ID
   The Id of the operation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the operation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the operation to describe. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the operation to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the operation to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the operation to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe an operation, run:

    $ gcloud logging operations describe OPERATION_ID --location=LOCATION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/operations/describe)

---
### `gcloud logging operations list`

List long running operations

Return a list of long running operations in the given LOCATION. The
operations were scheduled by other gcloud commands.

For example, a CopyLogEntries operation may be scheduled by the command:
gcloud logging copy BUCKET_ID DESTINATION --location=LOCATION.

The --operation-filter flag is required and must specify the request_type.
Supported request types include but are not limited to: CopyLogEntries,
CreateBucket and UpdateBucket.

Additional supported filter expressions include: operation_start_time,
operation_finish_time and operation_state. These can be combined with the
case-sensitive keyword AND between them.

For operation_start_time and operation_end_time, the operators >=, >, <=,
and < are supported.

Timestamps must be in either RFC3339 or ISO8601 formats. If the timestamp
contains a time value, then it must be quoted. For examples:
"YYYY-MM-DDTHH:MM:SSZ", "YYYY-MM-DDTHH:MM:SS.mmmZ", "YY-MM-DD",
"YYYY-MM-DDTHH:MM:SS-0000", "YYYY-MM-DDTHH:MM+0000", "YYYY-MM-DD",
YYYY-MM-DD, YY-MM-DD, etc.

The operation_state filter expression can be used to filter for operations
that are in a specific state. The value can be one of the following:
SCHEDULED, WAITING_FOR_PRECONDITIONS, RUNNING, SUCCESS, FAILURE, CANCELLED,
PENDING.

For operation_state, the operators = and != are supported.

Other filter options are not supported.

**Synopsis:**
```
gcloud logging operations list --location=LOCATION
    --operation-filter=OPERATION_FILTER [--page-token=PAGE_TOKEN]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the operations. |
| `--operation-filter` | OPERATION_FILTER |  | Filter expression that specifies the operations to return. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-token` | PAGE_TOKEN |  | The next_page_token value returned from a previous List request, if any. |


**Examples:**
```bash
To list CopyLogEntries operations, run:

    $ gcloud logging operations list --location=LOCATION \
      --operation-filter='request_type=CopyLogEntries'

To list CopyLogEntries operations that started after a specified time, run:

    $ gcloud logging operations list --location=LOCATION \
      --operation-filter='request_type=CopyLogEntries AND
    operation_start_time>="2023-11-20T00:00:00Z"'

To list CopyLogEntries operations that finished before a specified time,
run:

    $ gcloud logging operations list --location=LOCATION \
      --operation-filter='request_type=CopyLogEntries AND
    operation_finish_time<="2023-11-20T00:00:00Z"'

To list CopyLogEntries operations that completed successfully, run:

    $ gcloud logging operations list --location=LOCATION \
      --operation-filter='request_type=CopyLogEntries AND
    operation_state=SUCCESS'

To list CopyLogEntries operations that have not failed, run:

    $ gcloud logging operations list --location=LOCATION \
      --operation-filter='request_type=CopyLogEntries AND
    operation_state!=FAILURE'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/operations/list)

---
# gcloud transfer operations

manage transfer operations

### `gcloud transfer operations cancel`

Cancel a transfer operation

Cancel a transfer operation.

**Synopsis:**
```
gcloud transfer operations cancel NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the transfer operation you want to cancel.
```

**Examples:**
```bash
To cancel an operation, run:

    $ gcloud transfer operations cancel OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/operations/cancel)

---
### `gcloud transfer operations describe`

Get configuration and latest transfer operation details

Get details about a specific transfer operation.

**Synopsis:**
```
gcloud transfer operations describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the operation you want to describe.
```

**Examples:**
```bash
To describe an operation, run:

    $ gcloud transfer operations describe OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/operations/describe)

---
### `gcloud transfer operations list`

List Transfer Service transfer operations

List Transfer Service transfer operations to view their progress details at
a glance.

**Synopsis:**
```
gcloud transfer operations list [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=256] [--job-names=[JOB_NAMES,...]]
    [--operation-names=[OPERATION_NAMES,...]]
    [--operation-statuses=[OPERATION_STATUSES,...]] [--expand-table]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--limit` | LIMIT |  | Return the first items from the API up to this limit. |
| `--page-size` | PAGE_SIZE | 256 | Retrieve batches of this many items from the API. |
| `--job-names` | [JOB_NAMES,...] |  | The names of the jobs whose operations you want to list. Separate multiple job names with commas (e.g., --job-names=foo,bar). If not specified, operations for all jobs are listed. |
| `--operation-names` | [OPERATION_NAMES,...] |  | The names of operations you want to list. Separate multiple operation names with commas (e.g., --operation-names-name=foo,bar). If not specified, all operations are listed. |
| `--operation-statuses` | [OPERATION_STATUSES,...] |  | List only transfer operations with the statuses you specify. Options include 'in_progress', 'paused', 'success','failed', 'aborted'. Separate multiple statuses with commas (e.g., --operation-statuses=failed,aborted). |
| `--expand-table` |  |  | Include additional table columns (operation name, start time, status, data copied, status, has errors, job name) in command output. Tip: increase the size of your terminal before running the command. |


**Examples:**
```bash
To list all transfer operations in your current project, run:

    $ gcloud transfer operations list

To list all failed operations in your project, run:

    $ gcloud transfer operations list --operation-statuses=failed

To list operations 'foo' and 'bar', run:

    $ gcloud transfer operations list --operation-names=foo,bar

To list all operations in your current project as JSON, which provides all
fields and formatting available in the API, run:

    $ gcloud transfer operations list --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/operations/list)

---
### `gcloud transfer operations monitor`

Track progress in real time for a transfer operation

Track progress in real time for a transfer operation.

**Synopsis:**
```
gcloud transfer operations monitor NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the operation you want to monitor.
```

**Examples:**
```bash
To monitor an operation, run:

    $ gcloud transfer operations monitor OPERATION-NAME

If you're looking for specific error details, use the "operations describe"
command:

    $ gcloud transfer operations describe OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/operations/monitor)

---
### `gcloud transfer operations pause`

Pause a currently running transfer operation

Pause a currently running transfer operation.

**Synopsis:**
```
gcloud transfer operations pause NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the paused transfer operation you want to cancel.
```

**Examples:**
```bash
To pause an operation, run:

    $ gcloud transfer operations pause OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/operations/pause)

---
### `gcloud transfer operations resume`

Resume a currently paused transfer operation

Resume a currently paused transfer operation.

**Synopsis:**
```
gcloud transfer operations resume NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the paused transfer operation you want to resume.
```

**Examples:**
```bash
To resume an operation, run:

    $ gcloud transfer operations resume OPERATION-NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/operations/resume)

---
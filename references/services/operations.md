# gcloud services operations

manage Operation for various services

### `gcloud services operations describe`

Describes an operation resource for a given operation name

This command will return information about an operation given the name of
that operation.

**Synopsis:**
```
gcloud services operations describe OPERATION [--full=FULL]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   The name of the operation to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full` | FULL |  | (DEPRECATED) This flag is deprecated. This flag is deprecated. |


**Examples:**
```bash
To describe an operation resource named operations/abc, run:

    $ gcloud services operations describe operations/abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/operations/describe)

---
### `gcloud services operations wait`

Waits for an operation to complete for a given operation name

This command will block until an operation has been marked as complete.

**Synopsis:**
```
gcloud services operations wait OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   The name of the operation on which to wait.
```

**Examples:**
```bash
To wait on an operation named operations/abc to complete, run:

    $ gcloud services operations wait operations/abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/operations/wait)

---
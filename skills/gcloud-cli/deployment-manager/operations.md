# gcloud deployment-manager operations

commands for Deployment Manager operations

### `gcloud deployment-manager operations describe`

Provide information about an operation

This command prints out all available details about an operation.

**Synopsis:**
```
gcloud deployment-manager operations describe OPERATION_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_NAME
   Operation name.
```

**Examples:**
```bash
To display information about an operation, run:

    $ gcloud deployment-manager operations describe operation-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/operations/describe)

---
### `gcloud deployment-manager operations list`

List operations in a project

Prints a table with summary information on all operations in the project.

**Synopsis:**
```
gcloud deployment-manager operations list [--simple-list]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--simple-list` |  |  | Changes the --format flag to print the resource IDs. Otherwise either the --format value or the default format is used. |


**Examples:**
```bash
To print out a list of operations with some summary information about each,
run:

    $ gcloud deployment-manager operations list

To print only the name of each operation, run:

    $ gcloud deployment-manager operations list --simple-list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/operations/list)

---
### `gcloud deployment-manager operations wait`

Wait for all operations specified to complete before returning

Polls until all operations have finished, then prints the resulting
operations along with any operation errors.

**Synopsis:**
```
gcloud deployment-manager operations wait OPERATION_NAME
    [OPERATION_NAME ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_NAME [OPERATION_NAME ...]
   Operation name.
```

**Examples:**
```bash
To poll until an operation has completed, run:

    $ gcloud deployment-manager operations wait operation-name

To poll until several operations have all completed, run:

    $ gcloud deployment-manager operations wait operation-one \
        operation-two operation-three
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deployment-manager/operations/wait)

---
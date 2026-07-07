# gcloud app operations

view and manage your App Engine Operations

### `gcloud app operations describe`

Describes the operation

Describes the operation.

**Synopsis:**
```
gcloud app operations describe OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   ID of operation.
```

**Examples:**
```bash
To describe an App Engine operation called o1, run:

    $ gcloud app operations describe o1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/operations/describe)

---
### `gcloud app operations list`

List the operations

List the operations.

**Synopsis:**
```
gcloud app operations list [--pending] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pending` |  |  | Only display pending operations |


**Examples:**
```bash
To list all App Engine operations, run:

    $ gcloud app operations list

To list only 100 App Engine operations, run:

    $ gcloud app operations list --limit=100

To list only pending App Engine operations, run:

    $ gcloud app operations list --pending
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/operations/list)

---
### `gcloud app operations wait`

Polls an operation until completion

Polls an operation until completion.

**Synopsis:**
```
gcloud app operations wait OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION
   ID of operation.
```

**Examples:**
```bash
To wait for an App Engine operation called o1 to complete, run:

    $ gcloud app operations wait o1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/operations/wait)

---
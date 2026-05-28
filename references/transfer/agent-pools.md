# gcloud transfer agent-pools

manage on-premise transfer agent pools

### `gcloud transfer agent-pools create`

Create a Transfer Service agent pool

Create an agent pool -- a group of agents used to connect to a source or
destination filesystem.

**Synopsis:**
```
gcloud transfer agent-pools create NAME [--no-async]
    [--bandwidth-limit=BANDWIDTH_LIMIT] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   A unique, permanent identifier for this pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Block other tasks in your terminal until the pool has been created. If not included, pool creation will run asynchronously. |
| `--bandwidth-limit` | BANDWIDTH_LIMIT |  | Set how much of your bandwidth to make available to this pool's agents. A bandwidth limit applies to all agents in a pool and can help prevent the pool's transfer workload from disrupting other operations that share your bandwidth. For example, enter '50' to set a bandwidth limit of 50 MB/s. By leaving this flag unspecified, this flag unspecified, this pool's agents will use all bandwidth available to them. |
| `--display-name` | DISPLAY_NAME |  | A modifiable name to help you identify this pool. You can include details that might not fit in the pool's unique full resource name. |


**Examples:**
```bash
To create an agent pool with name 'my-pool', display name 'daily backups',
and no bandwidth limit, run:

    $ gcloud transfer agent-pools create my-pool \
      --display-name='daily backups'

To create an agent pool with name 'my-pool', display name 'daily backups',
and a bandwidth limit of 50 MB/s, run:

    $ gcloud transfer agent-pools create my-pool \
      --display-name="daily backups" --bandwidth-limit=50
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/agent-pools/create)

---
### `gcloud transfer agent-pools delete`

Delete a Transfer Service agent pool

Delete an agent pool. Note that before you can delete a pool, all the
pool's agents must be stopped, its associated jobs must be disabled, and
there must be no associated in-progress transfer operations.

**Synopsis:**
```
gcloud transfer agent-pools delete NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the job you want to delete.
```

**Examples:**
```bash
To delete agent pool 'foo', run:

    $ gcloud transfer agent-pools delete foo

To check if there are active operations associated with a pool before
deleting it, scroll through the results of:

    $ gcloud transfer operations list --format=yaml \
        --operation-statuses=in_progress
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/agent-pools/delete)

---
### `gcloud transfer agent-pools describe`

Get details about a specific agent pool

Get details about a specific agent pool.

**Synopsis:**
```
gcloud transfer agent-pools describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the agent pool you want to describe.
```

**Examples:**
```bash
To monitor an agent pool, run:

    $ gcloud transfer agent-pools describe NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/agent-pools/describe)

---
### `gcloud transfer agent-pools list`

List Transfer Service transfer agent pools

List Transfer Service transfer pools in a given project to show their
configurations.

**Synopsis:**
```
gcloud transfer agent-pools list [--limit=LIMIT] [--names=[NAMES,...]]
    [--page-size=PAGE_SIZE; default=256] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--limit` | LIMIT |  | Return the first items from the API up to this limit. |
| `--names` | [NAMES,...] |  | The names of the agent pools you want to list. Separate multiple names with commas (e.g., --name=foo,bar). If not specified, all agent pools in your current project will be listed. |
| `--page-size` | PAGE_SIZE | 256 | Retrieve batches of this many items from the API. |


**Examples:**
```bash
To list all agent pools in your current project, run:

    $ gcloud transfer agent-pools list

To list agent pools named "foo" and "bar" in your project, run:

    $ gcloud transfer agent-pools list --names=foo,bar

To list all information about jobs 'foo' and 'bar' formatted as JSON, run:

    $ gcloud transfer agent-pools list --names=foo,bar --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/agent-pools/list)

---
### `gcloud transfer agent-pools update`

Update a Transfer Service agent pool

Update an agent pool.

**Synopsis:**
```
gcloud transfer agent-pools update NAME [--bandwidth-limit=BANDWIDTH_LIMIT]
    [--clear-bandwidth-limit] [--clear-display-name]
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   A unique, permanent identifier for this pool.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth-limit` | BANDWIDTH_LIMIT |  | Set how much of your bandwidth to make available to this pool's agents. A bandwidth limit applies to all agents in a pool and can help prevent the pool's transfer workload from disrupting other operations that share your bandwidth. For example, enter '50' to set a bandwidth limit of 50 MB/s. By leaving this flag unspecified, this flag unspecified, this pool's agents will use all bandwidth available to them. |
| `--clear-bandwidth-limit` |  |  | Remove the agent pool's bandwidth limit, which enables the pool's agents to use all bandwidth available to them. |
| `--clear-display-name` |  |  | Remove the display name from the agent pool. |
| `--display-name` | DISPLAY_NAME |  | A modifiable name to help you identify this pool. You can include details that might not fit in the pool's unique full resource name. |


**Examples:**
```bash
To remove the bandwidth limit for agent pool 'foo', run:

    $ gcloud transfer agent-pools update foo --clear-bandwidth-limit

To remove the display name for agent pool 'foo', run:

    $ gcloud transfer agent-pools update foo --clear-display-name

To update the bandwidth limit for agent pool 'foo' to 100 MB/s, run:

    $ gcloud transfer agent-pools update foo --bandwidth-limit=100

To update the display name for agent pool 'foo' to 'example name', run:

    $ gcloud transfer agent-pools update foo \
      --display-name="example name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/agent-pools/update)

---
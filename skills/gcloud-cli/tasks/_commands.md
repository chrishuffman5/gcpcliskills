# gcloud tasks (top-level commands)

### `gcloud tasks buffer`

Buffers a task into a queue

Buffers a task into a queue.

**Synopsis:**
```
gcloud tasks buffer --location=LOCATION --queue=QUEUE [--task-id=TASK_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where the queue exists. |
| `--queue` | QUEUE |  | The queue the task belongs to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--task-id` | TASK_ID |  | The task ID for the task being created. |


**Examples:**
```bash
To buffer into a queue:

    $ gcloud tasks buffer --queue=my-queue --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/buffer)

---
### `gcloud tasks create-app-engine-task`

Create and add a task that targets App Engine

Create and add a task that targets App Engine.

**Synopsis:**
```
gcloud tasks create-app-engine-task [TASK_ID] --queue=QUEUE
    [--header=HEADER_FIELD: HEADER_VALUE] [--location=LOCATION]
    [--method=METHOD] [--relative-uri=RELATIVE_URI]
    [--routing=KEY:VALUE,[...]] [--schedule-time=SCHEDULE_TIME]
    [--body-content=BODY_CONTENT | --body-file=BODY_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[TASK_ID]
   The task to create.

   If not specified then the system will generate a random unique task ID.
   Explicitly specifying a task ID enables task de-duplication. If a
   task's ID is identical to that of an existing task or a task that was
   deleted or completed recently then the call will fail.

   Because there is an extra lookup cost to identify duplicate task names,
   tasks created with IDs have significantly increased latency. Using
   hashed strings for the task ID or for the prefix of the task ID is
   recommended.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--queue` | QUEUE |  | The queue the task belongs to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--header` | HEADER_FIELD: HEADER_VALUE |  | An HTTP request header. Header values can contain commas. This flag can be repeated. Repeated header fields will have their values overridden. |
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |
| `--method` | METHOD |  | The HTTP method to use for the request. If not specified, "POST" will be used. |
| `--relative-uri` | RELATIVE_URI |  | The relative URI of the request. Must begin with "/" and must be a valid HTTP relative URI. It can contain a path and query string arguments. If not specified, then the root path "/" will be used. |
| `--routing` | KEY:VALUE,[...] |  | The route to be used for this task. KEY must be at least one of: [service, version, instance]. Any missing keys will use the default. Routing can be overridden by the queue-level --routing-override flag. |
| `--schedule-time` | SCHEDULE_TIME |  | The time when the task is scheduled to be first attempted. Defaults to "now" if not specified. |


**Examples:**
```bash
To create a task:

    $ gcloud tasks create-app-engine-task --queue=my-queue \
      --relative-uri=/handler-path my-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/create-app-engine-task)

---
### `gcloud tasks create-http-task`

Create and add a task that targets a HTTP endpoint

Create and add a task that targets a HTTP endpoint.

**Synopsis:**
```
gcloud tasks create-http-task [TASK_ID] --queue=QUEUE --url=URL
    [--header=HEADER_FIELD: HEADER_VALUE] [--location=LOCATION]
    [--method=METHOD] [--schedule-time=SCHEDULE_TIME]
    [--body-content=BODY_CONTENT | --body-file=BODY_FILE]
    [[--oauth-service-account-email=OAUTH_SERVICE_ACCOUNT_EMAIL
      : --oauth-token-scope=OAUTH_TOKEN_SCOPE]
      | [--oidc-service-account-email=OIDC_SERVICE_ACCOUNT_EMAIL
      : --oidc-token-audience=OIDC_TOKEN_AUDIENCE]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[TASK_ID]
   The task to create.

   If not specified then the system will generate a random unique task ID.
   Explicitly specifying a task ID enables task de-duplication. If a
   task's ID is identical to that of an existing task or a task that was
   deleted or completed recently then the call will fail.

   Because there is an extra lookup cost to identify duplicate task names,
   tasks created with IDs have significantly increased latency. Using
   hashed strings for the task ID or for the prefix of the task ID is
   recommended.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--queue` | QUEUE |  | The queue the task belongs to. |
| `--url` | URL |  | The full URL path that the request will be sent to. This string must begin with either "http://" or "https://". |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--header` | HEADER_FIELD: HEADER_VALUE |  | An HTTP request header. Header values can contain commas. This flag can be repeated. Repeated header fields will have their values overridden. |
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |
| `--method` | METHOD |  | The HTTP method to use for the request. If not specified, "POST" will be used. |
| `--schedule-time` | SCHEDULE_TIME |  | The time when the task is scheduled to be first attempted. Defaults to "now" if not specified. |


**Examples:**
```bash
To create a task:

    $ gcloud tasks create-http-task --queue=my-queue \
      --url=http://example.com/handler-path my-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/create-http-task)

---
### `gcloud tasks delete`

Delete a task from a queue

Delete a task from a queue.

**Synopsis:**
```
gcloud tasks delete TASK [--location=LOCATION] [--queue=QUEUE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TASK
   The task to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |
| `--queue` | QUEUE |  | The queue the task belongs to. |


**Examples:**
```bash
To delete a task:

    $ gcloud tasks delete --queue=my-queue my-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/delete)

---
### `gcloud tasks describe`

Show details about a task

Show details about a task.

**Synopsis:**
```
gcloud tasks describe TASK [--location=LOCATION] [--queue=QUEUE]
    [--response-view=RESPONSE_VIEW; default="basic"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TASK
   The task to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |
| `--queue` | QUEUE |  | The queue the task belongs to. |
| `--response-view` | one of: basic, full, view-unspecified | basic | Task response view. RESPONSE_VIEW must be one of: basic, full, view-unspecified. |


**Examples:**
```bash
To describe a task:

    $ gcloud tasks describe --queue=my-queue my-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/describe)

---
### `gcloud tasks list`

List tasks

List tasks.

**Synopsis:**
```
gcloud tasks list --queue=QUEUE [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=25]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--queue` | QUEUE |  | The queue the tasks belong to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To list tasks in a queue:

    $ gcloud tasks list --queue=my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/list)

---
### `gcloud tasks run`

Force a task to run now

Force a task to run now.

**Synopsis:**
```
gcloud tasks run TASK [--location=LOCATION] [--queue=QUEUE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TASK
   The task to run.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |
| `--queue` | QUEUE |  | The queue the task belongs to. |


**Examples:**
```bash
To run a task:

    $ gcloud tasks run --queue=my-queue my-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/run)

---
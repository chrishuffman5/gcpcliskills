# gcloud tasks queues

manage Cloud Tasks queues

### `gcloud tasks queues add-iam-policy-binding`

Add IAM policy binding for a tasks queue

Add an IAM policy binding to a tasks queue's access policy.

**Synopsis:**
```
gcloud tasks queues add-iam-policy-binding (QUEUE : --location=LOCATION)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queue resource - The task queue for which to add IAM policy binding to.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument queue on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUE
     ID of the queue or fully qualified identifier for the queue.

     To set the queue attribute:
     + provide the argument queue on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument queue on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with queue 'my-queue' and location='my-location',
run:

    $ gcloud tasks queues add-iam-policy-binding my-queue \
        --location='my-location' --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/add-iam-policy-binding)

---
### `gcloud tasks queues create`

Create a Cloud Tasks queue

The flags available to this command represent the fields of a queue that
are mutable.

**Synopsis:**
```
gcloud tasks queues create QUEUE
    [--http-header-override=HEADER_FIELD: HEADER_VALUE]
    [--http-method-override=HTTP_METHOD_OVERRIDE]
    [--http-uri-override=KEY:VALUE,[KEY:VALUE,...]] [--location=LOCATION]
    [--log-sampling-ratio=LOG_SAMPLING_RATIO] [--max-attempts=MAX_ATTEMPTS]
    [--max-backoff=MAX_BACKOFF]
    [--max-concurrent-dispatches=MAX_CONCURRENT_DISPATCHES]
    [--max-dispatches-per-second=MAX_DISPATCHES_PER_SECOND]
    [--max-doublings=MAX_DOUBLINGS]
    [--max-retry-duration=MAX_RETRY_DURATION] [--min-backoff=MIN_BACKOFF]
    [--routing-override=KEY:VALUE,[...]]
    [[--http-oauth-service-account-email-override=HTTP_OAUTH_SERVICE_ACCOUNT_EMAIL_OVERRIDE : --http-oauth-token-scope-override=HTTP_OAUTH_TOKEN_SCOPE_OVERRIDE] | [--http-oidc-service-account-email-override=HTTP_OIDC_SERVICE_ACCOUNT_EMAIL_OVERRIDE : --http-oidc-token-audience-override=HTTP_OIDC_TOKEN_AUDIENCE_OVERRIDE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--http-header-override` | HEADER_FIELD: HEADER_VALUE |  | If provided, the specified HTTP headers override the existing headers for all tasks in the queue. If a task has a header with the same Key as a queue-level header override, then the value of the task header will be overriden with the value of the queue-level header. Otherwise, the queue-level header will be added to the task headers. Header values can contain commas. This flag can be repeated. Repeated header fields will have their values overridden. |
| `--http-method-override` | HTTP_METHOD_OVERRIDE |  | If provided, the specified HTTP method type override is used for all tasks in the queue, no matter what is set at the task-level. |
| `--http-uri-override` | KEY:VALUE,[KEY:VALUE,...] |  | If provided, the specified HTTP target URI override is used for all tasks in the queue depending on what is set as the mode. Allowed values for mode are: ALWAYS, IF_NOT_EXISTS. If not set, mode defaults to ALWAYS. KEY must be at least one of: [scheme, host, port, path, query, mode]. Any missing keys will use the default. |
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |
| `--log-sampling-ratio` | LOG_SAMPLING_RATIO |  | Specifies the fraction of operations to write to Cloud Logging. This field may contain any value between 0.0 and 1.0, inclusive. 0.0 is the default and means that no operations are logged. |
| `--max-attempts` | MAX_ATTEMPTS |  | The maximum number of attempts per task in the queue. |
| `--max-backoff` | MAX_BACKOFF |  | The maximum amount of time to wait before retrying a task after it fails. Must be a string that ends in 's', such as "5s". |
| `--max-concurrent-dispatches` | MAX_CONCURRENT_DISPATCHES |  | The maximum number of concurrent tasks that Cloud Tasks allows to be dispatched for this queue. After this threshold has been reached, Cloud Tasks stops dispatching tasks until the number of outstanding requests decreases. |
| `--max-dispatches-per-second` | MAX_DISPATCHES_PER_SECOND |  | The maximum rate at which tasks are dispatched from this queue. |
| `--max-doublings` | MAX_DOUBLINGS |  | The time between retries will double maxDoublings times. A tasks retry interval starts at minBackoff, then doubles maxDoublings times, then increases linearly, and finally retries retries at intervals of maxBackoff up to maxAttempts times. For example, if minBackoff is 10s, maxBackoff is 300s, and maxDoublings is 3, then the a task will first be retried in 10s. The retry interval will double three times, and then increase linearly by 2^3 * 10s. Finally, the task will retry at intervals of maxBackoff until the task has been attempted maxAttempts times. Thus, the requests will retry at 10s, 20s, 40s, 80s, 160s, 240s, 300s, 300s. |
| `--max-retry-duration` | MAX_RETRY_DURATION |  | The time limit for retrying a failed task, measured from when the task was first run. Once the --max-retry-duration time has passed and the task has been attempted --max-attempts times, no further attempts will be made and the task will be deleted. Must be a string that ends in 's', such as "5s". |
| `--min-backoff` | MIN_BACKOFF |  | The minimum amount of time to wait before retrying a task after it fails. Must be a string that ends in 's', such as "5s". |
| `--routing-override` | KEY:VALUE,[...] |  | If provided, the specified App Engine route is used for all tasks in the queue, no matter what is set is at the task-level. KEY must be at least one of: [service, version, instance]. Any missing keys will use the default. |


**Examples:**
```bash
To create a Cloud Tasks queue:

    $ gcloud tasks queues create my-queue --max-attempts=10 \
      --max-retry-duration=5s --max-doublings=4 --min-backoff=1s \
      --max-backoff=10s --max-dispatches-per-second=100 \
      --max-concurrent-dispatches=10 --routing-override=service:abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/create)

---
### `gcloud tasks queues delete`

Delete a queue

Delete a queue.

**Synopsis:**
```
gcloud tasks queues delete QUEUE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To delete a queue:

    $ gcloud tasks queues delete my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/delete)

---
### `gcloud tasks queues describe`

Show details about a queue

Show details about a queue.

**Synopsis:**
```
gcloud tasks queues describe QUEUE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To describe queue:

    $ gcloud tasks queues describe my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/describe)

---
### `gcloud tasks queues get-iam-policy`

Get the IAM policy for a queue

gcloud tasks queues get-iam-policy displays the IAM policy associated with
a queue. If formatted as JSON, the output can be edited and used as a
policy file for set-iam-policy. The output includes an "etag" field
identifying the version emitted and allowing detection of concurrent policy
updates; see $ gcloud tasks queues set-iam-policy for additional details.

**Synopsis:**
```
gcloud tasks queues get-iam-policy (QUEUE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queue resource - The Cloud Tasks queue for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument queue on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUE
     ID of the queue or fully qualified identifier for the queue.

     To set the queue attribute:
     + provide the argument queue on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument queue on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given queue, run:

    $ gcloud tasks queues get-iam-policy my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/get-iam-policy)

---
### `gcloud tasks queues list`

List all queues

List all queues.

**Synopsis:**
```
gcloud tasks queues list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To list all queues:

    $ gcloud tasks queues list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/list)

---
### `gcloud tasks queues pause`

Pause a queue

If a queue is paused then the system will stop executing the tasks in the
queue until it is resumed. Tasks can still be added when the queue is
paused.

**Synopsis:**
```
gcloud tasks queues pause QUEUE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to pause.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To pause a queue:

    $ gcloud tasks queues pause my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/pause)

---
### `gcloud tasks queues purge`

Purge a queue by deleting all of its tasks

This command purges a queue by deleting all of its tasks. Purge operations
can take up to one minute to take effect. Tasks might be dispatched before
the purge takes effect. A purge is irreversible. All tasks created before
this command is run are permanently deleted.

**Synopsis:**
```
gcloud tasks queues purge QUEUE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to purge.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To purge a queue:

    $ gcloud tasks queues purge my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/purge)

---
### `gcloud tasks queues remove-iam-policy-binding`

Remove IAM policy binding of tasks queue

Remove an IAM policy binding of a tasks queue's access policy.

**Synopsis:**
```
gcloud tasks queues remove-iam-policy-binding (QUEUE : --location=LOCATION)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queue resource - The task queue for which to remove IAM policy binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument queue on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUE
     ID of the queue or fully qualified identifier for the queue.

     To set the queue attribute:
     + provide the argument queue on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument queue on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with queue 'my-queue' and location='my-location',
run:

    $ gcloud tasks queues remove-iam-policy-binding my-queue \
        --location='my-location' --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/remove-iam-policy-binding)

---
### `gcloud tasks queues resume`

Request to resume a paused or disabled queue

Request to resume a paused or disabled queue.

**Synopsis:**
```
gcloud tasks queues resume QUEUE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to resume.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To resume a queue:

    $ gcloud tasks queues resume my-queue
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/resume)

---
### `gcloud tasks queues set-iam-policy`

Set the IAM policy for a queue

This command replaces the existing IAM policy for a queue, given a queue
and a file encoded in JSON or YAML that contains the IAM policy. If the
given policy file specifies an "etag" value, then the replacement will
succeed only if the policy already in place matches that etag. (An etag
obtained via get-iam-policy will prevent the replacement if the policy for
the queue has been subsequently updated.) A policy file that does not
contain an etag value will replace any existing policy for the queue.

**Synopsis:**
```
gcloud tasks queues set-iam-policy (QUEUE : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Queue resource - The queue for which to set the IAM policy. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument queue on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  QUEUE
     ID of the queue or fully qualified identifier for the queue.

     To set the queue attribute:
     + provide the argument queue on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument queue on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for a queue:

    $ gcloud tasks queues set-iam-policy my-queue policy-file.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/set-iam-policy)

---
### `gcloud tasks queues update`

Update a Cloud Tasks queue

The flags available to this command represent the fields of a queue that
are mutable.

**Synopsis:**
```
gcloud tasks queues update QUEUE [--location=LOCATION]
    [--clear-http-header-override
      | --http-header-override=HEADER_FIELD: HEADER_VALUE]
    [--clear-http-method-override
      | --http-method-override=HTTP_METHOD_OVERRIDE]
    [--clear-http-oauth-service-account-email-override
      | --http-oauth-service-account-email-override=HTTP_OAUTH_SERVICE_ACCOUNT_EMAIL_OVERRIDE]
    [--clear-http-oauth-token-scope-override
      | --http-oauth-token-scope-override=HTTP_OAUTH_TOKEN_SCOPE_OVERRIDE]
    [--clear-http-oidc-service-account-email-override
      | --http-oidc-service-account-email-override=HTTP_OIDC_SERVICE_ACCOUNT_EMAIL_OVERRIDE]
    [--clear-http-oidc-token-audience-override
      | --http-oidc-token-audience-override=HTTP_OIDC_TOKEN_AUDIENCE_OVERRIDE]
    [--clear-http-uri-override
      | --http-uri-override=KEY:VALUE,[KEY:VALUE,...]]
    [--clear-log-sampling-ratio | --log-sampling-ratio=LOG_SAMPLING_RATIO]
    [--clear-max-attempts | --max-attempts=MAX_ATTEMPTS]
    [--clear-max-backoff | --max-backoff=MAX_BACKOFF]
    [--clear-max-concurrent-dispatches
      | --max-concurrent-dispatches=MAX_CONCURRENT_DISPATCHES]
    [--clear-max-dispatches-per-second
      | --max-dispatches-per-second=MAX_DISPATCHES_PER_SECOND]
    [--clear-max-doublings | --max-doublings=MAX_DOUBLINGS]
    [--clear-max-retry-duration | --max-retry-duration=MAX_RETRY_DURATION]
    [--clear-min-backoff | --min-backoff=MIN_BACKOFF]
    [--clear-routing-override | --routing-override=KEY:VALUE,[...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUEUE
   The queue to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location where we want to manage the queue or task. If not specified, uses the location of the current project's App Engine app if there is an associated app. |


**Examples:**
```bash
To update a Cloud Tasks queue:

    $ gcloud tasks queues update my-queue --clear-max-attempts \
      --clear-max-retry-duration --clear-max-doublings \
      --clear-min-backoff --clear-max-backoff \
      --clear-max-dispatches-per-second \
      --clear-max-concurrent-dispatches --clear-routing-override
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/queues/update)

---
# gcloud scheduler jobs

manage Cloud Scheduler jobs

### `gcloud scheduler jobs delete`

Delete a job

Delete a job.

**Synopsis:**
```
gcloud scheduler jobs delete (JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job you want to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Examples:**
```bash
The following command deletes a job:

    $ gcloud scheduler jobs delete my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/delete)

---
### `gcloud scheduler jobs describe`

Show details about a job

Show details about a job.

**Synopsis:**
```
gcloud scheduler jobs describe (JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job you want to show details for. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Examples:**
```bash
The following command shows details about a job:

    $ gcloud scheduler jobs describe my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/describe)

---
### `gcloud scheduler jobs list`

List jobs

List jobs.

**Synopsis:**
```
gcloud scheduler jobs list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + defaults to App Engine's app location if not provided & an app exists. |


**Examples:**
```bash
The following command lists all jobs in a project:

    $ gcloud scheduler jobs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/list)

---
### `gcloud scheduler jobs pause`

Pause the execution of a job

Pause the execution of a job.

**Synopsis:**
```
gcloud scheduler jobs pause (JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job to pause. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Examples:**
```bash
The following command pauses the execution of a job:

    $ gcloud scheduler jobs pause my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/pause)

---
### `gcloud scheduler jobs resume`

Resume execution of a paused job

Resume execution of a paused job.

**Synopsis:**
```
gcloud scheduler jobs resume (JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job to resume. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Examples:**
```bash
The following command resumes execution of a paused job:

    $ gcloud scheduler jobs resume my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/resume)

---
### `gcloud scheduler jobs run`

Trigger an on-demand execution of a job

Trigger an on-demand execution of a job.

**Synopsis:**
```
gcloud scheduler jobs run (JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job you want to run. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Examples:**
```bash
The following command runs a jobs:

    $ gcloud scheduler jobs run my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/run)

---

## `gcloud scheduler jobs create` — create Cloud Scheduler jobs for various types of targets
### `gcloud scheduler jobs create app-engine`

Create a Cloud Scheduler job with an App Engine target

Create a Cloud Scheduler job with an App Engine target.

**Synopsis:**
```
gcloud scheduler jobs create app-engine (JOB : --location=LOCATION)
    --schedule=SCHEDULE [--attempt-deadline=ATTEMPT_DEADLINE]
    [--description=DESCRIPTION] [--headers=[KEY=VALUE,...]]
    [--http-method=HTTP_METHOD; default="post"]
    [--max-backoff=MAX_BACKOFF; default="3600s"]
    [--max-doublings=MAX_DOUBLINGS; default=5]
    [--max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--max-retry-duration=MAX_RETRY_DURATION]
    [--min-backoff=MIN_BACKOFF; default="5s"]
    [--relative-url=RELATIVE_URL; default="/"] [--service=SERVICE]
    [--time-zone=TIME_ZONE; default="Etc/UTC"] [--version=VERSION]
    [--message-body=MESSAGE_BODY | --message-body-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--schedule` | SCHEDULE |  | Schedule on which the job will be executed. As a general rule, execution n + 1 of a job will not begin until execution n has finished. Cloud Scheduler will never allow two simultaneously outstanding executions. For example, this implies that if the n+1 execution is scheduled to run at 16:00 but the n execution takes until 16:15, the n+1 execution will not start until 16:15. A scheduled start time will be delayed if the previous execution has not ended when its scheduled time occurs. Learn more about the cron job format (https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules). If --retry-count > 0 and a job attempt fails, the job will be tried a total of --retry-count times, with exponential backoff, until the job succeeds or the number of retries is exhausted. Note that the next scheduled execution time might be skipped if the retries continue through that time. For more information, see Retry jobs (https://cloud.google.com/scheduler/docs/configuring/retry-jobs). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attempt-deadline` | ATTEMPT_DEADLINE |  | The deadline for job attempts. If the request handler doesn't respond by this dealine, the request is cancelled and the attempt is marked as failed. For example, 20s. |
| `--description` | DESCRIPTION |  | Human-readable description of the job. |
| `--headers` | [KEY=VALUE,...] |  | KEY=VALUE pairs of HTTP headers to include in the request. Cannot be repeated. For example: --headers Accept-Language=en-us,Accept=text/plain |
| `--http-method` | one of: delete, get, head, post, put | post | HTTP method to use for the request. HTTP_METHOD must be one of: delete, get, head, post, put. |
| `--max-backoff` | MAX_BACKOFF | 3600s | Maximum amount of time to wait before retrying a job after it fails. For example, 60s. Default is 3600s (1 hour). |
| `--max-doublings` | MAX_DOUBLINGS | 5 | Maximum number of times that the interval between failed job retries will be doubled before the increase becomes constant. |
| `--max-retry-attempts` | MAX_RETRY_ATTEMPTS |  | Number of times to retry the request if it fails or times out. Must be in range 0-5 inclusive. Default is 0. |
| `--max-retry-duration` | MAX_RETRY_DURATION |  | Time limit for retrying a failed job, measured from when the job was first run. If specified with --max-retry-attempts greater than 0, the job will be retried until both limits are reached. Default is 0 seconds (which means unlimited); however, if --max-retry-attempts is also 0, a job attempt won't be retried if it fails. |
| `--min-backoff` | MIN_BACKOFF | 5s | Minimum amount of time to wait before retrying a job after it fails. For example, 10s. Default is 5s. |
| `--relative-url` | RELATIVE_URL | / | Relative URL to use for the request (beginning with "/"). |
| `--service` | SERVICE |  | ID of the App Engine service to send the request to. |
| `--time-zone` | TIME_ZONE | Etc/UTC | Specifies the time zone to be used in interpreting --schedule. The value of this field must be a time zone name from the tz database (https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). Note that some time zones include a provision for daylight savings time. The rules for daylight saving time are determined by the chosen time zone. For UTC use the string "utc". Default is "utc". |
| `--version` | VERSION |  | Version of the App Engine service to send the request to. |


**Examples:**
```bash
The following command creates a job that sends a request to the
'/cron-handler' path in you App Engine app every 3 hours:

    $ gcloud scheduler jobs create app-engine my-job \
        --schedule="0 */3 * * *" --relative-url="/cron-handler"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/create/app-engine)

---
### `gcloud scheduler jobs create http`

Create a Cloud Scheduler job that triggers an action via HTTP

Create a Cloud Scheduler job that triggers an action via HTTP.

**Synopsis:**
```
gcloud scheduler jobs create http (JOB : --location=LOCATION)
    --schedule=SCHEDULE --uri=URI [--attempt-deadline=ATTEMPT_DEADLINE]
    [--description=DESCRIPTION] [--headers=[KEY=VALUE,...]]
    [--http-method=HTTP_METHOD; default="post"]
    [--max-backoff=MAX_BACKOFF; default="3600s"]
    [--max-doublings=MAX_DOUBLINGS; default=5]
    [--max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--max-retry-duration=MAX_RETRY_DURATION]
    [--min-backoff=MIN_BACKOFF; default="5s"]
    [--time-zone=TIME_ZONE; default="Etc/UTC"]
    [--message-body=MESSAGE_BODY | --message-body-from-file=PATH_TO_FILE]
    [[--oauth-service-account-email=OAUTH_SERVICE_ACCOUNT_EMAIL
      : --oauth-token-scope=OAUTH_TOKEN_SCOPE]
      | [--oidc-service-account-email=OIDC_SERVICE_ACCOUNT_EMAIL
      : --oidc-token-audience=OIDC_TOKEN_AUDIENCE]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--schedule` | SCHEDULE |  | Schedule on which the job will be executed. As a general rule, execution n + 1 of a job will not begin until execution n has finished. Cloud Scheduler will never allow two simultaneously outstanding executions. For example, this implies that if the n+1 execution is scheduled to run at 16:00 but the n execution takes until 16:15, the n+1 execution will not start until 16:15. A scheduled start time will be delayed if the previous execution has not ended when its scheduled time occurs. Learn more about the cron job format (https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules). If --retry-count > 0 and a job attempt fails, the job will be tried a total of --retry-count times, with exponential backoff, until the job succeeds or the number of retries is exhausted. Note that the next scheduled execution time might be skipped if the retries continue through that time. For more information, see Retry jobs (https://cloud.google.com/scheduler/docs/configuring/retry-jobs). |
| `--uri` | URI |  | The full URI path that the request will be sent to. This string must begin with either "http://" or "https://". For example, http://acme.com or https://acme.com/sales:8080. Cloud Scheduler will encode some characters for safety and compatibility. The maximum allowed URL length is 2083 characters after encoding. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attempt-deadline` | ATTEMPT_DEADLINE |  | The deadline for job attempts. If the request handler doesn't respond by this dealine, the request is cancelled and the attempt is marked as failed. For example, 20s. |
| `--description` | DESCRIPTION |  | Human-readable description of the job. |
| `--headers` | [KEY=VALUE,...] |  | KEY=VALUE pairs of HTTP headers to include in the request. Cannot be repeated. For example: --headers Accept-Language=en-us,Accept=text/plain |
| `--http-method` | one of: delete, get, head, post, put | post | HTTP method to use for the request. HTTP_METHOD must be one of: delete, get, head, post, put. |
| `--max-backoff` | MAX_BACKOFF | 3600s | Maximum amount of time to wait before retrying a job after it fails. For example, 60s. Default is 3600s (1 hour). |
| `--max-doublings` | MAX_DOUBLINGS | 5 | Maximum number of times that the interval between failed job retries will be doubled before the increase becomes constant. |
| `--max-retry-attempts` | MAX_RETRY_ATTEMPTS |  | Number of times to retry the request if it fails or times out. Must be in range 0-5 inclusive. Default is 0. |
| `--max-retry-duration` | MAX_RETRY_DURATION |  | Time limit for retrying a failed job, measured from when the job was first run. If specified with --max-retry-attempts greater than 0, the job will be retried until both limits are reached. Default is 0 seconds (which means unlimited); however, if --max-retry-attempts is also 0, a job attempt won't be retried if it fails. |
| `--min-backoff` | MIN_BACKOFF | 5s | Minimum amount of time to wait before retrying a job after it fails. For example, 10s. Default is 5s. |
| `--time-zone` | TIME_ZONE | Etc/UTC | Specifies the time zone to be used in interpreting --schedule. The value of this field must be a time zone name from the tz database (https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). Note that some time zones include a provision for daylight savings time. The rules for daylight saving time are determined by the chosen time zone. For UTC use the string "utc". Default is "utc". |


**Examples:**
```bash
The following command creates a job that sends a HTTP GET request to
'http://example.com/path' every 3 hours:

    $ gcloud scheduler jobs create http my-job \
        --schedule="0 */3 * * *" --uri="http://example.com/path" \
        --http-method=GET
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/create/http)

---
### `gcloud scheduler jobs create pubsub`

Create a Cloud Scheduler job with a Pub/Sub target

Create a Cloud Scheduler job with a Pub/Sub target.

**Synopsis:**
```
gcloud scheduler jobs create pubsub (JOB : --location=LOCATION)
    --schedule=SCHEDULE --topic=TOPIC
    (--attributes=ATTRIBUTES --message-body=MESSAGE_BODY
      | --message-body-from-file=PATH_TO_FILE) [--description=DESCRIPTION]
    [--max-backoff=MAX_BACKOFF; default="3600s"]
    [--max-doublings=MAX_DOUBLINGS; default=5]
    [--max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--max-retry-duration=MAX_RETRY_DURATION]
    [--min-backoff=MIN_BACKOFF; default="5s"]
    [--time-zone=TIME_ZONE; default="Etc/UTC"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--schedule` | SCHEDULE |  | Schedule on which the job will be executed. As a general rule, execution n + 1 of a job will not begin until execution n has finished. Cloud Scheduler will never allow two simultaneously outstanding executions. For example, this implies that if the n+1 execution is scheduled to run at 16:00 but the n execution takes until 16:15, the n+1 execution will not start until 16:15. A scheduled start time will be delayed if the previous execution has not ended when its scheduled time occurs. Learn more about the cron job format (https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules). If --retry-count > 0 and a job attempt fails, the job will be tried a total of --retry-count times, with exponential backoff, until the job succeeds or the number of retries is exhausted. Note that the next scheduled execution time might be skipped if the retries continue through that time. For more information, see Retry jobs (https://cloud.google.com/scheduler/docs/configuring/retry-jobs). |
| `--topic` | TOPIC |  | Name of the Google Cloud Pub/Sub topic to publish to when the job runs. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Human-readable description of the job. |
| `--max-backoff` | MAX_BACKOFF | 3600s | Maximum amount of time to wait before retrying a job after it fails. For example, 60s. Default is 3600s (1 hour). |
| `--max-doublings` | MAX_DOUBLINGS | 5 | Maximum number of times that the interval between failed job retries will be doubled before the increase becomes constant. |
| `--max-retry-attempts` | MAX_RETRY_ATTEMPTS |  | Number of times to retry the request if it fails or times out. Must be in range 0-5 inclusive. Default is 0. |
| `--max-retry-duration` | MAX_RETRY_DURATION |  | Time limit for retrying a failed job, measured from when the job was first run. If specified with --max-retry-attempts greater than 0, the job will be retried until both limits are reached. Default is 0 seconds (which means unlimited); however, if --max-retry-attempts is also 0, a job attempt won't be retried if it fails. |
| `--min-backoff` | MIN_BACKOFF | 5s | Minimum amount of time to wait before retrying a job after it fails. For example, 10s. Default is 5s. |
| `--time-zone` | TIME_ZONE | Etc/UTC | Specifies the time zone to be used in interpreting --schedule. The value of this field must be a time zone name from the tz database (https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). Note that some time zones include a provision for daylight savings time. The rules for daylight saving time are determined by the chosen time zone. For UTC use the string "utc". Default is "utc". |


**Examples:**
```bash
The following command creates a job that publishes a message with the body
'Hello' to the Pub/Sub topic 'cron-topic' every 3 hours:

    $ gcloud scheduler jobs create pubsub my-job \
        --schedule="0 */3 * * *" --topic=cron-topic \
        --message-body="Hello"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/create/pubsub)

---

## `gcloud scheduler jobs update` — update Cloud Scheduler jobs for various types of targets
### `gcloud scheduler jobs update app-engine`

Update a Cloud Scheduler job with an App Engine target

Update a Cloud Scheduler job with an App Engine target.

**Synopsis:**
```
gcloud scheduler jobs update app-engine (JOB : --location=LOCATION)
    [--attempt-deadline=ATTEMPT_DEADLINE] [--description=DESCRIPTION]
    [--http-method=HTTP_METHOD; default="post"] [--schedule=SCHEDULE]
    [--version=VERSION]
    [--clear-headers | --remove-headers=[REMOVE_HEADERS,...]
      --update-headers=[KEY=VALUE,...]]
    [--clear-max-backoff | --max-backoff=MAX_BACKOFF; default="3600s"]
    [--clear-max-doublings | --max-doublings=MAX_DOUBLINGS; default=5]
    [--clear-max-retry-attempts | --max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--clear-max-retry-duration | --max-retry-duration=MAX_RETRY_DURATION]
    [--clear-message-body | --message-body=MESSAGE_BODY
      | --message-body-from-file=PATH_TO_FILE]
    [--clear-min-backoff | --min-backoff=MIN_BACKOFF; default="5s"]
    [--clear-relative-url | --relative-url=RELATIVE_URL; default="/"]
    [--clear-service | --service=SERVICE; default="default"]
    [--clear-time-zone | --time-zone=TIME_ZONE; default="Etc/UTC"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attempt-deadline` | ATTEMPT_DEADLINE |  | The deadline for job attempts. If the request handler doesn't respond by this dealine, the request is cancelled and the attempt is marked as failed. For example, 20s. |
| `--description` | DESCRIPTION |  | Human-readable description of the job. |
| `--http-method` | one of: delete, get, head, post, put | post | HTTP method to use for the request. HTTP_METHOD must be one of: delete, get, head, post, put. |
| `--schedule` | SCHEDULE |  | Schedule on which the job will be executed. As a general rule, execution n + 1 of a job will not begin until execution n has finished. Cloud Scheduler will never allow two simultaneously outstanding executions. For example, this implies that if the n+1 execution is scheduled to run at 16:00 but the n execution takes until 16:15, the n+1 execution will not start until 16:15. A scheduled start time will be delayed if the previous execution has not ended when its scheduled time occurs. Learn more about the cron job format (https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules). If --retry-count > 0 and a job attempt fails, the job will be tried a total of --retry-count times, with exponential backoff, until the job succeeds or the number of retries is exhausted. Note that the next scheduled execution time might be skipped if the retries continue through that time. For more information, see Retry jobs (https://cloud.google.com/scheduler/docs/configuring/retry-jobs). |
| `--version` | VERSION |  | Version of the App Engine service to send the request to. |


**Examples:**
```bash
Update my-job's retry attempt limit:

    $ gcloud scheduler jobs update app-engine my-job \
        --max-retry-attempts=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/update/app-engine)

---
### `gcloud scheduler jobs update http`

Update a Cloud Scheduler job that triggers an action via HTTP

Update a Cloud Scheduler job that triggers an action via HTTP.

**Synopsis:**
```
gcloud scheduler jobs update http (JOB : --location=LOCATION)
    [--attempt-deadline=ATTEMPT_DEADLINE] [--description=DESCRIPTION]
    [--http-method=HTTP_METHOD; default="post"] [--schedule=SCHEDULE]
    [--uri=URI]
    [--clear-auth-token
      | [--oauth-service-account-email=OAUTH_SERVICE_ACCOUNT_EMAIL
      : --oauth-token-scope=OAUTH_TOKEN_SCOPE]
      | [--oidc-service-account-email=OIDC_SERVICE_ACCOUNT_EMAIL
      : --oidc-token-audience=OIDC_TOKEN_AUDIENCE]]
    [--clear-headers | --remove-headers=[REMOVE_HEADERS,...]
      --update-headers=[KEY=VALUE,...]]
    [--clear-max-backoff | --max-backoff=MAX_BACKOFF; default="3600s"]
    [--clear-max-doublings | --max-doublings=MAX_DOUBLINGS; default=5]
    [--clear-max-retry-attempts | --max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--clear-max-retry-duration | --max-retry-duration=MAX_RETRY_DURATION]
    [--clear-message-body | --message-body=MESSAGE_BODY
      | --message-body-from-file=PATH_TO_FILE]
    [--clear-min-backoff | --min-backoff=MIN_BACKOFF; default="5s"]
    [--clear-time-zone | --time-zone=TIME_ZONE; default="Etc/UTC"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attempt-deadline` | ATTEMPT_DEADLINE |  | The deadline for job attempts. If the request handler doesn't respond by this dealine, the request is cancelled and the attempt is marked as failed. For example, 20s. |
| `--description` | DESCRIPTION |  | Human-readable description of the job. |
| `--http-method` | one of: delete, get, head, post, put | post | HTTP method to use for the request. HTTP_METHOD must be one of: delete, get, head, post, put. |
| `--schedule` | SCHEDULE |  | Schedule on which the job will be executed. As a general rule, execution n + 1 of a job will not begin until execution n has finished. Cloud Scheduler will never allow two simultaneously outstanding executions. For example, this implies that if the n+1 execution is scheduled to run at 16:00 but the n execution takes until 16:15, the n+1 execution will not start until 16:15. A scheduled start time will be delayed if the previous execution has not ended when its scheduled time occurs. Learn more about the cron job format (https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules). If --retry-count > 0 and a job attempt fails, the job will be tried a total of --retry-count times, with exponential backoff, until the job succeeds or the number of retries is exhausted. Note that the next scheduled execution time might be skipped if the retries continue through that time. For more information, see Retry jobs (https://cloud.google.com/scheduler/docs/configuring/retry-jobs). |
| `--uri` | URI |  | The full URI path that the request will be sent to. This string must begin with either "http://" or "https://". For example, http://acme.com or https://acme.com/sales:8080. Cloud Scheduler will encode some characters for safety and compatibility. The maximum allowed URL length is 2083 characters after encoding. |


**Examples:**
```bash
Update my-job's retry attempt limit:

    $ gcloud scheduler jobs update http my-job --max-retry-attempts=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/update/http)

---
### `gcloud scheduler jobs update pubsub`

Update a Cloud Scheduler job with a Pub/Sub target

Update a Cloud Scheduler job with a Pub/Sub target.

**Synopsis:**
```
gcloud scheduler jobs update pubsub (JOB : --location=LOCATION)
    [--description=DESCRIPTION] [--schedule=SCHEDULE] [--topic=TOPIC]
    [--clear-attributes | --remove-attributes=[REMOVE_ATTRIBUTES,...]
      --update-attributes=[KEY=VALUE,...]]
    [--clear-max-backoff | --max-backoff=MAX_BACKOFF; default="3600s"]
    [--clear-max-doublings | --max-doublings=MAX_DOUBLINGS; default=5]
    [--clear-max-retry-attempts | --max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--clear-max-retry-duration | --max-retry-duration=MAX_RETRY_DURATION]
    [--clear-min-backoff | --min-backoff=MIN_BACKOFF; default="5s"]
    [--clear-time-zone | --time-zone=TIME_ZONE; default="Etc/UTC"]
    [--message-body=MESSAGE_BODY | --message-body-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the job. By default, uses the location of the current
     project's App Engine app if there is an associated app.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + defaults to App Engine's app location if not provided & an app
       exists.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Human-readable description of the job. |
| `--schedule` | SCHEDULE |  | Schedule on which the job will be executed. As a general rule, execution n + 1 of a job will not begin until execution n has finished. Cloud Scheduler will never allow two simultaneously outstanding executions. For example, this implies that if the n+1 execution is scheduled to run at 16:00 but the n execution takes until 16:15, the n+1 execution will not start until 16:15. A scheduled start time will be delayed if the previous execution has not ended when its scheduled time occurs. Learn more about the cron job format (https://cloud.google.com/scheduler/docs/configuring/cron-job-schedules). If --retry-count > 0 and a job attempt fails, the job will be tried a total of --retry-count times, with exponential backoff, until the job succeeds or the number of retries is exhausted. Note that the next scheduled execution time might be skipped if the retries continue through that time. For more information, see Retry jobs (https://cloud.google.com/scheduler/docs/configuring/retry-jobs). |
| `--topic` | TOPIC |  | Name of the Google Cloud Pub/Sub topic to publish to when the job runs. |


**Examples:**
```bash
Update my-job's retry attempt limit:

    $ gcloud scheduler jobs update pubsub my-job --max-retry-attempts=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/jobs/update/pubsub)

---
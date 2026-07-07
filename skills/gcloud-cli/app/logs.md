# gcloud app logs

manage your App Engine logs

### `gcloud app logs read`

Reads log entries for the current App Engine app

Display the latest log entries from stdout, stderr and crash log for the
current Google App Engine app in a human readable format. This command
requires that the caller have the logging.logEntries.list permission.

**Synopsis:**
```
gcloud app logs read [--level=LEVEL; default="any"]
    [--limit=LIMIT; default=200]
    [--logs=APP_LOG,[APP_LOG,...];
      default="stderr,stdout,crash.log,nginx.request,request_log"]
    [--service=SERVICE, -s SERVICE] [--version=VERSION, -v VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--level` | one of: critical, error, warning, info, debug, any | any | Filter entries with severity equal to or higher than a given level. LEVEL must be one of: critical, error, warning, info, debug, any. |
| `--limit` | LIMIT | 200 | Number of log entries to show. |
| `--logs` | APP_LOG,[APP_LOG,...] | stderr,stdout,crash.log,nginx.request,request_log | Filter entries from a particular set of logs. Must be a comma-separated list of log names (request_log, stdout, stderr, etc). |
| `--service` | SERVICE, -s SERVICE |  | Limit to specific service. |
| `--version` | VERSION, -v VERSION |  | Limit to specific version. |


**Examples:**
```bash
To display the latest entries for the current app, run:

    $ gcloud app logs read

To show only the entries with severity at warning or higher, run:

    $ gcloud app logs read --level=warning

To show only the entries with a specific version, run:

    $ gcloud app logs read --version=v1

To show only the 10 latest log entries for the default service, run:

    $ gcloud app logs read --limit=10 --service=default

To show only the logs from the request log for standard apps, run:

    $ gcloud app logs read --logs=request_log

To show only the logs from the request log for Flex apps, run:

    $ gcloud app logs read --logs=nginx.request
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/logs/read)

---
### `gcloud app logs tail`

Streams logs for App Engine apps

Streams logs for App Engine apps.

**Synopsis:**
```
gcloud app logs tail [--level=LEVEL; default="any"]
    [--logs=APP_LOG,[APP_LOG,...];
      default="stderr,stdout,crash.log,nginx.request,request_log"]
    [--service=SERVICE, -s SERVICE] [--version=VERSION, -v VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--level` | one of: critical, error, warning, info, debug, any | any | Filter entries with severity equal to or higher than a given level. LEVEL must be one of: critical, error, warning, info, debug, any. |
| `--logs` | APP_LOG,[APP_LOG,...] | stderr,stdout,crash.log,nginx.request,request_log | Filter entries from a particular set of logs. Must be a comma-separated list of log names (request_log, stdout, stderr, etc). |
| `--service` | SERVICE, -s SERVICE |  | Limit to specific service. |
| `--version` | VERSION, -v VERSION |  | Limit to specific version. |


**Examples:**
```bash
To stream logs from a serving app, run:

    $ gcloud app logs tail

To show only logs with a specific service, version, and level, run:

    $ gcloud app logs tail --service=s1 --version=v1 --level=warning

To show only the logs from the request log for Standard apps, run:

    $ gcloud app logs tail --logs=request_log

To show only the logs from the request log for Flex apps, run:

    $ gcloud app logs tail --logs=nginx.request
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/logs/tail)

---
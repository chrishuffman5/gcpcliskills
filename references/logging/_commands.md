# gcloud logging (top-level commands)

### `gcloud logging copy`

Copy log entries

gcloud logging copy starts the process to copy log entries from a log
bucket to a destination.

**Synopsis:**
```
gcloud logging copy BUCKET_ID DESTINATION --location=LOCATION
    [--log-filter=LOG_FILTER]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUCKET_ID
   Id of the log bucket to copy logs from. Example: my-bucket

DESTINATION
   Destination to copy logs to. Example: Cloud Storage bucket:
   storage.googleapis.com/my-cloud-storage-bucket
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the log bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--log-filter` | LOG_FILTER |  | A filter specifying which log entries to copy. The filter must be no more than 20k characters. An empty filter matches all log entries. |


**Examples:**
```bash
To start a copy log entries operation, run:

    $ gcloud logging copy BUCKET_ID DESTINATION --location=LOCATION

To copy log entries in a specific time window, run:

    $ gcloud logging copy BUCKET_ID DESTINATION --location=LOCATION \
        --log-filter='timestamp<="2021-05-31T23:59:59Z" AND
     timestamp>="2021-05-31T00:00:00Z"'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/copy)

---
### `gcloud logging read`

Read log entries

gcloud logging read reads log entries. Log entries matching log-filter are
returned in order of decreasing timestamps, most-recent entries first. If
the log entries come from multiple logs, then entries from different logs
might be intermingled in the results.

**Synopsis:**
```
gcloud logging read [LOG_FILTER] [--freshness=FRESHNESS; default="1d"]
    [--order=ORDER; default="desc"]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [--resource-names=[RESOURCE,...]
      | --bucket=BUCKET --location=LOCATION --view=VIEW] [--limit=LIMIT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[LOG_FILTER]
   Filter expression that specifies the log entries to return. Detailed
   information about filters can be found at:
   https://cloud.google.com/logging/docs/view/logging-query-language
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--freshness` | FRESHNESS | 1d | Return entries that are not older than this value. Works only with DESC ordering and filters without a timestamp. See $ gcloud topic datetimes for information on duration formats. |
| `--order` | one of: desc, asc | desc | Ordering of returned log entries based on timestamp field. ORDER must be one of: desc, asc. |


**Examples:**
```bash
To read log entries from Google Compute Engine instances, run:

    $ gcloud logging read "resource.type=gce_instance"

To read log entries with severity ERROR or higher, run:

    $ gcloud logging read "severity>=ERROR"

To read log entries written in a specific time window, run:

    $ gcloud logging read \
        'timestamp<="2015-05-31T23:59:59Z" AND
     timestamp>="2015-05-31T00:00:00Z"'

To read up to 10 log entries in your project's syslog log from Compute
Engine instances containing payloads that include the word SyncAddress and
format the output in JSON format, run:

    $ gcloud logging read \
        "resource.type=gce_instance AND \
    logName=projects/[PROJECT_ID]/logs/syslog AND \
    textPayload:SyncAddress" --limit=10 --format=json

To read a log entry from a folder, run:

    $ gcloud logging read "resource.type=global" --folder=[FOLDER_ID] \
        --limit=1

To read a log entry from a global log bucket, run:

    $ gcloud logging read --bucket=<bucket-id> --location=[LOCATION] \
        --limit=1

To read a log entry from the global _Required log bucket using the bucket's
_Default log view:

    $ gcloud logging read "" --bucket=_Required --location=global \
        --view=_Default --limit=1

To read a log entry from a log bucket using the bucket's _AllLogs log view:

    $ gcloud logging read "" --bucket=[BUCKET_ID] \
        --location=[LOCATION] --view=_AllLogs --limit=1

To read a log entry from a log bucket using a custom log view that you have
created for the bucket:

    $ gcloud logging read "" --bucket=[BUCKET_ID] \
        --location=[LOCATION] --view=[VIEW_ID] --limit=1

To read log entries from multiple resources, specify them as a
comma-delimeted sequence with --resource-names. Each resource name can be
specified either as a top-level resource (e.g., projects/[PROJECT_ID],
folders/[FOLDER_ID], etc.) or as a Log View resource (e.g.,
projects/[PROJECT_ID]/locations/[LOCATION]/buckets/[BUCKET_NAME]/views/[VIEW_ID]).

    $ gcloud logging read "" --resource-names=[RESOURCE-1],[RESOURCE-2]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/read)

---
### `gcloud logging write`

Write a log entry

Write a log entry. If the destination log does not exist, it will be
created. By default, all log entries written with this command are written
with the "global" resource type.

gcloud logging write should be used for simple testing purposes. Check
Cloud Logging agent for a proper way to send log entries:
https://cloud.google.com/logging/docs/agent/

**Synopsis:**
```
gcloud logging write LOG_NAME MESSAGE
    [--monitored-resource-labels=[KEY=VALUE, ...,...]]
    [--monitored-resource-type=MONITORED_RESOURCE_TYPE; default="global"]
    [--payload-type=PAYLOAD_TYPE; default="text"]
    [--severity=SEVERITY; default="DEFAULT"]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOG_NAME
   Name of the log where the log entry will be written.

MESSAGE
   Message to put in the log entry. It can be JSON if you include
   --payload-type=json.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--monitored-resource-labels` | [KEY=VALUE, ...,...] |  | Monitored Resource labels to add to the payload |
| `--monitored-resource-type` | MONITORED_RESOURCE_TYPE | global | Monitored Resource type to add to the payload |
| `--payload-type` | one of: text, json | text | Type of the log entry payload. PAYLOAD_TYPE must be one of: text, json. |
| `--severity` | one of: DEFAULT, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY | DEFAULT | Severity level of the log entry. SEVERITY must be one of: DEFAULT, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY. |


**Examples:**
```bash
To create a log entry in a given log, run:

    $ gcloud logging write LOG_NAME "A simple entry"

To create a high severity log entry, run:

    $ gcloud logging write LOG_NAME "Urgent message" --severity=ALERT

To create a structured log, run:

    $ gcloud logging write LOG_NAME '{"key": "value"}' \
        --payload-type=json

To create a log entry with a custom resource type, run:

    $ gcloud logging write LOG_NAME "A simple entry" \
        --monitored-resource-type=gce_instance \
        --monitored-resource-labels=zone=us-centra1-a,instance_id=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/write)

---
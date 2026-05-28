# gcloud eventarc audit-logs-provider

explore provider serviceNames and methodNames for event type google.cloud.audit.log.v1.written in Eventarc


## `gcloud eventarc audit-logs-provider method-names` — explore values for the methodName attribute for event type google.cloud.audit.log.v1.written
### `gcloud eventarc audit-logs-provider method-names list`

List values for the methodName attribute for event type google.cloud.audit.log.v1.written

List values for the methodName attribute for event type
google.cloud.audit.log.v1.written.

**Synopsis:**
```
gcloud eventarc audit-logs-provider method-names list
    --service-name=SERVICE_NAME [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-name` | SERVICE_NAME |  | The value of the serviceName CloudEvents attribute. |


**Examples:**
```bash
To list methodName values for serviceName storage.googleapis.com, run:

    $ gcloud eventarc audit-logs-provider method-names list \
         --service-name=storage.googleapis.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/audit-logs-provider/method-names/list)

---

## `gcloud eventarc audit-logs-provider service-names` — explore values for the serviceName attribute for event type google.cloud.audit.log.v1.written
### `gcloud eventarc audit-logs-provider service-names list`

List values for the serviceName attribute for event type google.cloud.audit.log.v1.written

List values for the serviceName attribute for event type
google.cloud.audit.log.v1.written.

**Synopsis:**
```
gcloud eventarc audit-logs-provider service-names list
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list serviceName values for event type
google.cloud.audit.log.v1.written, run:

    $ gcloud eventarc audit-logs-provider service-names list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/audit-logs-provider/service-names/list)

---
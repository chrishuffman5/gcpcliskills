# gcloud logging logs

manages your project's logs

### `gcloud logging logs delete`

Delete all entries from a log in the global _Default log bucket

Delete all entries from a log in the global _Default log bucket. With no
entries, the log will not appear in the list of your project's logs.
However, you can write new entries to the log.

**Synopsis:**
```
gcloud logging logs delete LOG_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOG_NAME
   Log name.
```

**Examples:**
```bash
To delete all entries from log 'my-log' in the global _Default log bucket:

    $ gcloud logging logs delete my-log
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/logs/delete)

---
### `gcloud logging logs list`

List your project's logs

Only logs that contain log entries are listed.

**Synopsis:**
```
gcloud logging logs list [--bucket=BUCKET --location=LOCATION --view=VIEW]
    [--filter=EXPRESSION] [--limit=LIMIT] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | _[view resource.]_ Id of the log bucket. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[view resource.]_ Location of the log bucket. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--view` | VIEW |  | _[view resource.]_ Id of the view. This flag argument must be specified if any of the other arguments in this group are specified. |


**Examples:**
```bash
To list all logs in current project:

    $ gcloud logging logs list

To list all logs for a view:

    $ gcloud logging logs list --bucket=[BUCKET_ID] \
        --location=[LOCATION] --view=[VIEW_ID]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/logs/list)

---
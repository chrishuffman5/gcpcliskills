# gcloud functions runtimes

list runtimes available to Google Cloud Functions

### `gcloud functions runtimes list`

List runtimes available to Google Cloud Functions

List runtimes available to Google Cloud Functions.

**Synopsis:**
```
gcloud functions runtimes list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Only show runtimes within the region. Overrides the default functions/region property value for this command invocation. |


**Examples:**
```bash
To list the available runtimes, run:

    $ gcloud functions runtimes list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/runtimes/list)

---
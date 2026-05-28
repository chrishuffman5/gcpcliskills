# gcloud app runtimes

list runtimes available to Google App Engine

### `gcloud app runtimes list`

List the available runtimes

This command lists all the available runtimes and their current stages, for
example, GA, BETA or END OF SUPPORT.

**Synopsis:**
```
gcloud app runtimes list --environment=ENVIRONMENT [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | Environment for the application. ENVIRONMENT must be (only one value is supported): standard. |


**Examples:**
```bash
To list all the runtimes in the App Engine standard environment, run:

    $ gcloud app runtimes list --environment=standard
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/runtimes/list)

---
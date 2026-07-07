# gcloud oracle-database db-versions

manage Db Version resources

### `gcloud oracle-database db-versions list`

List all DbVersions

List all DbVersions.

**Synopsis:**
```
gcloud oracle-database db-versions list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DbVersions for a given DbSystemShape and StorageManagement with
db-system-shape and storage-management in the location us-east4, run:

    $ gcloud oracle-database db-versions list --location=us-east4 \
        --filter="db-system-shape=db-system-shape AND \
    storage-management=storage-management"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/db-versions/list)

---
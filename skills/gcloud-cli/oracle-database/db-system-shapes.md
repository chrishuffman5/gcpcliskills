# gcloud oracle-database db-system-shapes

manage Db System Shape resources

### `gcloud oracle-database db-system-shapes list`

List all DbSystemShapes

List all DbSystemShapes.

**Synopsis:**
```
gcloud oracle-database db-system-shapes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all DbSystemShapes in the location us-east4, run:

    $ gcloud oracle-database db-system-shapes list --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/db-system-shapes/list)

---
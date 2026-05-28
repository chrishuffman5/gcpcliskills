# gcloud filestore regions

list regions where Filestore is available

### `gcloud filestore regions list`

List all Filestore regions

List all Filestore regions.

**Synopsis:**
```
gcloud filestore regions list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five Filestore regions sorted
alphabetically by name in descending order:

    $ gcloud filestore regions list --limit=5 --sort-by=~name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/regions/list)

---
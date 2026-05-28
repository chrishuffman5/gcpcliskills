# gcloud filestore zones

list zones where Filestore is available

### `gcloud filestore zones list`

List all Filestore zones

List all Filestore zones.

**Synopsis:**
```
gcloud filestore zones list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five Filestore zones sorted
alphabetically by name in descending order:

    $ gcloud filestore zones list --limit=5 --sort-by=~name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/zones/list)

---
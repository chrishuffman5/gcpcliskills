# gcloud redis zones

manage Cloud Memorystore Redis zones

### `gcloud redis zones list`

List Memorystore Redis zones

List all zones where Memorystore Redis API is available.

**Synopsis:**
```
gcloud redis zones list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | If provided, returns only resources from the given region. Use region ID only, not the full URI of the region. This flag is the equivalent of: --filter="region:REGION". Run gcloud topic filters for more information. |


**Examples:**
```bash
To list all the zones where Redis instances can be created, run:

    $ gcloud redis zones list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/zones/list)

---
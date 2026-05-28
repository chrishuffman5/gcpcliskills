# gcloud logging resource-descriptors

get information about resource descriptors

### `gcloud logging resource-descriptors list`

List all available resource descriptors

List all available resource descriptors that are used by Cloud Logging.
Each log entry must be associated with a valid resource descriptor.

**Synopsis:**
```
gcloud logging resource-descriptors list [--filter=EXPRESSION]
    [--limit=LIMIT] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all resource descriptors:

    $ gcloud logging resource-descriptors list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/resource-descriptors/list)

---
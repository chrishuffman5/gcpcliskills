# gcloud scheduler locations

get information about Cloud Scheduler locations

### `gcloud scheduler locations describe`

Show details about a location

Show details about a location.

**Synopsis:**
```
gcloud scheduler locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOCATION
   The Cloud location to describe.
```

**Examples:**
```bash
To describe a location:

    $ gcloud scheduler locations describe my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/locations/describe)

---
### `gcloud scheduler locations list`

Lists the locations where Cloud Scheduler is available

Lists the locations where Cloud Scheduler is available.

**Synopsis:**
```
gcloud scheduler locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the locations where Cloud Scheduler is available:

    $ gcloud scheduler locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/locations/list)

---
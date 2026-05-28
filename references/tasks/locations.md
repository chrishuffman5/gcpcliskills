# gcloud tasks locations

get information about Cloud Tasks locations

### `gcloud tasks locations describe`

Show details about a location

Show details about a location.

**Synopsis:**
```
gcloud tasks locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOCATION
   The Cloud location to describe.
```

**Examples:**
```bash
To describe a location:

    $ gcloud tasks locations describe my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/locations/describe)

---
### `gcloud tasks locations list`

Lists the locations where Cloud Tasks is available

Lists the locations where Cloud Tasks is available.

**Synopsis:**
```
gcloud tasks locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the locations where Cloud Tasks is available:

    $ gcloud tasks locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/tasks/locations/list)

---
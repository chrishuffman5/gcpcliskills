# gcloud redis regions

manage Cloud Memorystore Redis regions

### `gcloud redis regions describe`

Show metadata for a Memorystore Redis region

Display all metadata associated with a Redis region given a valid region
name.

This command can fail for the following reasons:
  o The region specified does not exist.
  o The active account does not have permission to access the given
    region.

**Synopsis:**
```
gcloud redis regions describe REGION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Region resource - Arguments and flags that specify the Memorystore Redis
region you want to describe. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument region on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REGION
     ID of the region or fully qualified identifier for the region.

     To set the region attribute:
     + provide the argument region on the command line.
```

**Examples:**
```bash
To display the metadata for the region us-central1, run:

    $ gcloud redis regions describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/regions/describe)

---
### `gcloud redis regions list`

List Memorystore Redis regions

List all regions where Memorystore Redis API is available.

**Synopsis:**
```
gcloud redis regions list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the regions where Redis instances can be created, run:

    $ gcloud redis regions list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/redis/regions/list)

---
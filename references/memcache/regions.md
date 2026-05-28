# gcloud memcache regions

manage Cloud Memorystore Memcached regions

### `gcloud memcache regions describe`

Display metadata for a Memorystore Memcached region

Display all metadata associated with a Memorystore Memcached region given a
valid region name.

This command can fail for the following reasons:
  o The region specified does not exist.
  o The active account does not have permission to access the given
    region.

**Synopsis:**
```
gcloud memcache regions describe [REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Region resource - Arguments and flags that specify the Memorystore
Memcached region to describe. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument region on the command line with a fully
   specified name;
 * set the property memcache/region with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [REGION]
     ID of the region or fully qualified identifier for the region.

     To set the region attribute:
     + provide the argument region on the command line;
     + set the property memcache/region.
```

**Examples:**
```bash
To display the metadata for the region us-central1, run:

    $ gcloud memcache regions describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/regions/describe)

---
### `gcloud memcache regions list`

List Memorystore Memcached regions

List all regions where Memorystore Memcached API is available.

**Synopsis:**
```
gcloud memcache regions list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the regions where you can create Memcached instances, run:

    $ gcloud memcache regions list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memcache/regions/list)

---
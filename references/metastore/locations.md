# gcloud metastore locations

get information about Dataproc Metastore locations

### `gcloud metastore locations describe`

Show metadata for a Dataproc Metastore location

Display all metadata associated with a Metastore location given a valid
location name.

**Synopsis:**
```
gcloud metastore locations describe [LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - Dataproc Metastore location to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument location on the command line with a fully
   specified name;
 * set the property metastore/location with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [LOCATION]
     ID of the location or fully qualified identifier for the location.

     To set the location attribute:
     + provide the argument location on the command line;
     + set the property metastore/location.
```

**Examples:**
```bash
To display the metadata for a location named us-central1 in the default
project, run:

    $ gcloud metastore locations describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/locations/describe)

---
### `gcloud metastore locations list`

List Dataproc Metastore locations

List all Metastore locations.

**Synopsis:**
```
gcloud metastore locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the locations where you can create Dataproc Metastore services,
run:

    $ gcloud metastore locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/metastore/locations/list)

---
# gcloud filestore locations

list locations where Filestore is available

### `gcloud filestore locations describe`

Describe a Filestore location

Describe a Filestore location.

**Synopsis:**
```
gcloud filestore locations describe ZONE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The location to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.
```

**Examples:**
```bash
The following command shows the details for the Filestore location named
NAME.

    $ gcloud filestore locations describe NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/locations/describe)

---
### `gcloud filestore locations list`

List all Filestore locations

List all Filestore locations.

**Synopsis:**
```
gcloud filestore locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists a maximum of five Filestore locations sorted
alphabetically by name in descending order:

    $ gcloud filestore locations list --limit=5 --sort-by=~name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/filestore/locations/list)

---
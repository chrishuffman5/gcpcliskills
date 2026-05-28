# gcloud netapp locations

get and list locations where Cloud NetApp Files is available

### `gcloud netapp locations describe`

Describe a Cloud NetApp Files location

Describe a Cloud NetApp Files location.

**Synopsis:**
```
gcloud netapp locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The location to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument location on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOCATION
     ID of the location or fully qualified identifier for the location.

     To set the location attribute:
     + provide the argument location on the command line.
```

**Examples:**
```bash
The following command shows the details for the NetApp Files location named
NAME.

    $ gcloud netapp locations describe NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/locations/describe)

---
### `gcloud netapp locations list`

List all Cloud NetApp Files locations

Lists all Cloud NetApp Files locations.

**Synopsis:**
```
gcloud netapp locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists NetApp Files locations.

    $ gcloud netapp locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/netapp/locations/list)

---
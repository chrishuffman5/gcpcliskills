# gcloud apphub locations

manage App Hub Locations

### `gcloud apphub locations describe`

Describe an Apphub location

Describe an Apphub location.

**Synopsis:**
```
gcloud apphub locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - Location. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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
To describe a specific apphub location with the name my-location, run:

    $ gcloud apphub locations describe my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/locations/describe)

---
### `gcloud apphub locations list`

List Apphub locations

List Apphub locations.

**Synopsis:**
```
gcloud apphub locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all apphub locations, run:

    $ gcloud apphub locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/locations/list)

---
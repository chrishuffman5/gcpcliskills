# gcloud design-center locations

manage Design Center Locations

### `gcloud design-center locations describe`

Describe a Design Center location

Describe a Design Center location.

**Synopsis:**
```
gcloud design-center locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
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
To describe a specific design center location with the name my-location in
project my-project, run:

    $ gcloud design-center locations describe my-location \
        --project=my-project

Or run:

    $ gcloud design-center locations describe \
        projects/my-project/locations/my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/locations/describe)

---
### `gcloud design-center locations list`

List Design Center locations

List Design Center locations.

**Synopsis:**
```
gcloud design-center locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all design center locations in project my-project, run:

    $ gcloud design-center locations list --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/locations/list)

---
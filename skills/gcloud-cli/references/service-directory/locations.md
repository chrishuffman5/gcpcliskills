# gcloud service-directory locations

manage Service Directory locations

### `gcloud service-directory locations describe`

Describes a location

Describes a location.

**Synopsis:**
```
gcloud service-directory locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The Service Directory location to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument location on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  LOCATION
     ID of the location or fully qualified identifier for the location.

     To set the location attribute:
     + provide the argument location on the command line.
```

**Examples:**
```bash
To describe a Service Directory location, run:

    $ gcloud service-directory locations describe location us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/locations/describe)

---
### `gcloud service-directory locations list`

Lists locations

Lists locations.

**Synopsis:**
```
gcloud service-directory locations list [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe a Service Directory location, run:

    $ gcloud service-directory locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/locations/list)

---
# gcloud memorystore locations

manage Memorystore for Valkey locations

### `gcloud memorystore locations describe`

Show metadata for a Memorystore for Valkey location

Display all metadata associated with a Memorystore for Valkey location
given a valid location name.

This command can fail for the following reasons:
  o The location specified does not exist.
  o The active account does not have permission to access the given
    location.

**Synopsis:**
```
gcloud memorystore locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - Arguments and flags that specify the Memorystore for
Valkey location you want to describe. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

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
To display the metadata for the location us-central1, run:

    $ gcloud memorystore locations describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/locations/describe)

---
### `gcloud memorystore locations list`

List Memorystore for Valkey locations

List all locations where Memorystore for Valkey API is available.

**Synopsis:**
```
gcloud memorystore locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the locations where Memorystore for Valkey instances can be
created, run:

    $ gcloud memorystore locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/memorystore/locations/list)

---
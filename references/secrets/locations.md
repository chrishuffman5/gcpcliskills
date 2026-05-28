# gcloud secrets locations

manage locations of users' secrets

### `gcloud secrets locations describe`

Describe a location

Describe a location available for storing secrets.

**Synopsis:**
```
gcloud secrets locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The location to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument LOCATION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LOCATION
     ID of the location or fully qualified identifier for the location.

     To set the location attribute:
     + provide the argument LOCATION on the command line.
```

**Examples:**
```bash
Describe the location 'us-central1':

    $ gcloud secrets locations describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/locations/describe)

---
### `gcloud secrets locations list`

List all available locations

List all available locations in which secrets can be replicated.

**Synopsis:**
```
gcloud secrets locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
List available secrets locations:

    $ gcloud secrets locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/locations/list)

---
# gcloud datastream locations

manage Datastream location resources

### `gcloud datastream locations describe`

Show details about the location

Show details about the location.

**Synopsis:**
```
gcloud datastream locations describe LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The location you want to describe. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

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
To show details about a location, run:

    $ gcloud datastream locations describe my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/locations/describe)

---
### `gcloud datastream locations fetch-static-ips`

List Datastream static ips per location

List Datastream static IPs.

**Synopsis:**
```
gcloud datastream locations fetch-static-ips LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - The location you want to list static ips of. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
To list the static IPs, run:

    $ gcloud datastream locations fetch-static-ips my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/locations/fetch-static-ips)

---
### `gcloud datastream locations list`

List Datastream locations

List Datastream locations.

**Synopsis:**
```
gcloud datastream locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the locations, run:

    $ gcloud datastream locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/locations/list)

---
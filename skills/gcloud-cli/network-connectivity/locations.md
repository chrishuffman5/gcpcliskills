# gcloud network-connectivity locations

get information about supported Network Connectivity Center locations

### `gcloud network-connectivity locations describe`

Describe a Network Connectivity Center location

Retrieve details about a location.

**Synopsis:**
```
gcloud network-connectivity locations describe LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Location resource - Name of the location to describe. This represents a
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
To describe location us-central1, run:

    $ gcloud network-connectivity locations describe us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/locations/describe)

---
### `gcloud network-connectivity locations list`

List Network Connectivity Center locations

Retrieve and display a list of locations.

Network Connectivity Center includes two general types of spokes: those
that use the site-to-site data transfer feature and those that don't. To
get a list of the locations that support one of these features, use the
--filter flag (see examples). The full list of location features can be
found here:
https://cloud.google.com/network-connectivity/docs/reference/networkconnectivity/rest/Shared.Types/LocationFeature

To specify the maximum number of locations to return, use the --limit flag.

**Synopsis:**
```
gcloud network-connectivity locations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all locations, run:

    $ gcloud network-connectivity locations list

To list locations that support the site-to-site data transfer feature, run:

    $ gcloud network-connectivity locations list \
        --filter="metadata.locationFeatures=SITE_TO_SITE_SPOKES"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/locations/list)

---
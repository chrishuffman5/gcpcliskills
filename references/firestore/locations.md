# gcloud firestore locations

the set of commands to manage Locations for Cloud Firestore

### `gcloud firestore locations list`

List locations available to Google Cloud Firestore

**Synopsis:**
```
gcloud firestore locations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Firestore locations with table.

    $ gcloud firestore locations list \
      --format="table(locationId, displayName)"

To list Firestore locations with a filter.

    $ gcloud firestore locations list --filter="locationId:us-west1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/locations/list)

---
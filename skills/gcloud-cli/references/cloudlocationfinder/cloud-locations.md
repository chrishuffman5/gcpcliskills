# gcloud cloudlocationfinder cloud-locations

manage Cloud Location resources

### `gcloud cloudlocationfinder cloud-locations describe`

Describe a Cloud Location

**Synopsis:**
```
gcloud cloudlocationfinder cloud-locations describe
    (CLOUD_LOCATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CloudLocation resource - Name of the resource. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument cloud_location on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLOUD_LOCATION
     ID of the cloudLocation or fully qualified identifier for the
     cloudLocation.

     To set the cloud_location attribute:
     + provide the argument cloud_location on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the cloudLocation resource.

     To set the location attribute:
     + provide the argument cloud_location on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the Cloud Location with name "gcp-us-central1", run:

    $ gcloud cloudlocationfinder cloud-locations describe gcp-us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/cloudlocationfinder/cloud-locations/describe)

---
### `gcloud cloudlocationfinder cloud-locations list`

List cloudLocations

Request for listing Cloudlocations.

**Synopsis:**
```
gcloud cloudlocationfinder cloud-locations list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + location is always global. |


**Examples:**
```bash
To list CloudLocations, run:

    $ gcloud cloudlocationfinder cloud-locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/cloudlocationfinder/cloud-locations/list)

---
### `gcloud cloudlocationfinder cloud-locations search`

Search cloudLocations

Search Cloudlocations.

**Synopsis:**
```
gcloud cloudlocationfinder cloud-locations search
    --source-cloud-location=SOURCE_CLOUD_LOCATION [--limit=LIMIT]
    [--location=LOCATION] [--page-size=PAGE_SIZE] [--query=QUERY]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-cloud-location` | SOURCE_CLOUD_LOCATION |  | _[This must be specified.]_ ID of the source_cloud_location or fully qualified identifier for the source_cloud_location. To set the cloud_location attribute: + provide the argument --source-cloud-location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--limit` | LIMIT |  | Maximum number of resources to return. |
| `--page-size` | PAGE_SIZE |  | _[+ location is always global.]_ Maximum number of resources per page. |
| `--query` | QUERY |  | _[+ location is always global.]_ Query to use for searching Cloudlocations. |


**Examples:**
```bash
To search CloudLocations, run:

    $ gcloud cloudlocationfinder cloud-locations search \
      --source-cloud-location=aws-us-east-1 \
      --query=display_name="us-east4"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/cloudlocationfinder/cloud-locations/search)

---
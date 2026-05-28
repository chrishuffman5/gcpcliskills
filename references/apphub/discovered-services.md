# gcloud apphub discovered-services

manage App Hub Discovered Services

### `gcloud apphub discovered-services describe`

Describe an Apphub discovered service

Describe an Apphub discovered service.

**Synopsis:**
```
gcloud apphub discovered-services describe
    (DISCOVERED_SERVICE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DiscoveredService resource - The Discovered Service ID. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument discovered_service on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISCOVERED_SERVICE
     ID of the discoveredService or fully qualified identifier for the
     discoveredService.

     To set the discovered_service attribute:
     + provide the argument discovered_service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the discoveredService.

     To set the location attribute:
     + provide the argument discovered_service on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the DiscoveredService my-discovered-service in location
us-east1, run:

    $ gcloud apphub discovered-services describe my-discovered-service \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/discovered-services/describe)

---
### `gcloud apphub discovered-services list`

List Apphub discovered services

List Apphub discovered services.

**Synopsis:**
```
gcloud apphub discovered-services list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list DiscoveredServices that could be added to an application in
location us-east1, run:

    $ gcloud apphub discovered-services list --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/discovered-services/list)

---
### `gcloud apphub discovered-services lookup`

Lookup an Apphub discovered service with URI

Lookup an Apphub discovered service with URI.

**Synopsis:**
```
gcloud apphub discovered-services lookup --location=LOCATION --uri=URI
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--uri` | URI |  | _[This must be specified.]_ Google Cloud Platform resource URI to look up service for. |


**Examples:**
```bash
To lookup a discovered service with uri my-service-uri in location us-east1
run:

    $ gcloud apphub discovered-services lookup --location=us-east1 \
         --uri=my-service-uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/discovered-services/lookup)

---
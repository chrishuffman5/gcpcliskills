# gcloud apphub discovered-workloads

manage App Hub Discovered Workloads

### `gcloud apphub discovered-workloads describe`

Describe an Apphub discovered workload

Describe an Apphub discovered workload.

**Synopsis:**
```
gcloud apphub discovered-workloads describe
    (DISCOVERED_WORKLOAD : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DiscoveredWorkload resource - The Discovered Workload ID. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument discovered_workload on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISCOVERED_WORKLOAD
     ID of the discoveredWorkload or fully qualified identifier for the
     discoveredWorkload.

     To set the discovered_workload attribute:
     + provide the argument discovered_workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the discoveredWorkload.

     To set the location attribute:
     + provide the argument discovered_workload on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the DiscoveredWorkload my-discovered-workload in location
us-east1, run:

    $ gcloud apphub discovered-workloads describe \
        my-discovered-workload --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/discovered-workloads/describe)

---
### `gcloud apphub discovered-workloads list`

List Apphub discovered workloads that could be added to an application

List Apphub discovered workloads that could be added to an application.

**Synopsis:**
```
gcloud apphub discovered-workloads list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list DiscoveredWorkloads that could be added to an application in
location us-east1, run:

    $ gcloud apphub discovered-workloads list --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/discovered-workloads/list)

---
### `gcloud apphub discovered-workloads lookup`

Lookup an Apphub discovered workload with URI

Lookup an Apphub discovered workload with URI.

**Synopsis:**
```
gcloud apphub discovered-workloads lookup --location=LOCATION --uri=URI
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--uri` | URI |  | _[This must be specified.]_ Google Cloud Platform resource URI to look up workload for. |


**Examples:**
```bash
To lookup a discovered workload with uri my-workload-uri in location
us-east1 run:

    $ gcloud apphub discovered-workloads lookup --location=us-east1 \
         --uri=my-workload-uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/discovered-workloads/lookup)

---
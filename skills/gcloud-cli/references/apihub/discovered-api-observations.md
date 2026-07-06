# gcloud apihub discovered-api-observations

manage Discovered Api Observation resources

This file also covers the nested command group `gcloud apihub discovered-api-observations discovered-api-operations` (manage Discovered Api Operation resources).

### `gcloud apihub discovered-api-observations describe`

Describe a Discovered Api Observation

Describe a discovered api observation.

**Synopsis:**
```
gcloud apihub discovered-api-observations describe
    (DISCOVERED_API_OBSERVATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DiscoveredApiObservation resource - The name of the
DiscoveredApiObservation to retrieve. Format:
projects/{project}/locations/{location}/discoveredApiObservations/{discovered_api_observation}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument discovered_api_observation on the command line
   with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISCOVERED_API_OBSERVATION
     ID of the discoveredApiObservation or fully qualified identifier for
     the discoveredApiObservation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the discoveredApiObservation resource.
```

**Examples:**
```bash
To describe a discovered API observation with the ID my-observation, run:

    $ gcloud apihub discovered-api-observations describe my-observation \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/discovered-api-observations/describe)

---
### `gcloud apihub discovered-api-observations list`

List Discovered Api Observations

List discovered api observations.

**Synopsis:**
```
gcloud apihub discovered-api-observations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ Location resource - The parent, which owns this collection of ApiObservations. Format: projects/{project}/locations/{location}. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all discovered API observations in project my-project and location
us-central1, run:

    $ gcloud apihub discovered-api-observations list \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/discovered-api-observations/list)

---
### `gcloud apihub discovered-api-observations discovered-api-operations describe`

Describe a Discovered Api Operation

Describe a discovered api operation.

**Synopsis:**
```
gcloud apihub discovered-api-observations discovered-api-operations
    describe
    (DISCOVERED_API_OPERATION :
      --discovered-api-observation=DISCOVERED_API_OBSERVATION
      --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DiscoveredApiOperation resource - The name of the DiscoveredApiOperation
to retrieve. Format:
projects/{project}/locations/{location}/discoveredApiObservations/{discovered_api_observation}/discoveredApiOperations/{discovered_api_operation}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument discovered_api_operation on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DISCOVERED_API_OPERATION
     ID of the discoveredApiOperation or fully qualified identifier for
     the discoveredApiOperation.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --discovered-api-observation=DISCOVERED_API_OBSERVATION
     The discoveredApiObservation id of the discoveredApiOperation
     resource.

  --location=LOCATION
     The location id of the discoveredApiOperation resource.
```

**Examples:**
```bash
To describe a discovered API operation with the ID my-operation for
observation my-observation, run:

    $ gcloud apihub discovered-api-observations \
        discovered-api-operations describe my-operation \
        --discovered-api-observation=my-observation \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/discovered-api-observations/discovered-api-operations/describe)

---
### `gcloud apihub discovered-api-observations discovered-api-operations list`

List Discovered Api Operations

List discovered api operations.

**Synopsis:**
```
gcloud apihub discovered-api-observations discovered-api-operations list
    (--discovered-api-observation=DISCOVERED_API_OBSERVATION
      : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--discovered-api-observation` | DISCOVERED_API_OBSERVATION |  | _[This must be specified.]_ DiscoveredApiObservation resource - The parent, which owns this collection of DiscoveredApiOperations. Format: projects/{project}/locations/{location}/discoveredApiObservations/{discovered_api_observation}. ID of the discoveredApiObservation or fully qualified identifier for the discoveredApiObservation. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | The location id of the discoveredApiObservation resource. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all discovered API operations for observation my-observation, run:

    $ gcloud apihub discovered-api-observations \
        discovered-api-operations list \
        --discovered-api-observation=my-observation \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/discovered-api-observations/discovered-api-operations/list)

---

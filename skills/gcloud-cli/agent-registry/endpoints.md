# gcloud agent-registry endpoints

manage Endpoint resources

Endpoints are read-only consumer-side projections of registered Services — discovery only (describe / list).

### `gcloud agent-registry endpoints describe`

Retrieve endpoint details

Get the full configuration for a specific endpoint.

**Synopsis:**
```
gcloud agent-registry endpoints describe (ENDPOINT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - Name of the resource. Format:
projects/{project}/locations/{location}/endpoints/{endpoint}.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the endpoint resource.
```

**Examples:**
```bash
To describe endpoint 'my-endpoint' in location 'us-central1', run:

    $ gcloud agent-registry endpoints describe my-endpoint --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/endpoints/describe)

---
### `gcloud agent-registry endpoints list`

Enumerate service endpoints

Lists active endpoints associated with services in a specified location.

**Synopsis:**
```
gcloud agent-registry endpoints list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location (`projects/{project}/locations/{location}`). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter expression to each resource item to be listed. Flag interaction order: `--flatten`, `--sort-by`, `--filter`, `--limit`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service-determined | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by; prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list endpoints in location 'us-central1', run:

    $ gcloud agent-registry endpoints list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/agent-registry/endpoints/list)

---

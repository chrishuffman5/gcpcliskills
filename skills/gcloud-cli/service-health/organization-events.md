# gcloud service-health organization-events

represents events that may affect products used across the organization

### `gcloud service-health organization-events describe`

Get details of an event affecting an organization

Retrieves a resource containing information about an event impacting an organization. For service health incident events, use location `global`.

**Synopsis:**
```
gcloud service-health organization-events describe
    (ORGANIZATION_EVENT : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OrganizationEvent resource - Name of the resource, in the format
organizations/{organization_id}/locations/global/organizationEvents/{event_id},
where organization_id is the numeric ID of the organization (see "Getting
your organization resource ID" in the Resource Manager docs) and event_id
is the organization event to retrieve.

This must be specified.

  ORGANIZATION_EVENT
     ID of the organizationEvent or fully qualified identifier for the
     organizationEvent.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location to use when working with Service Health resources. For
     service health incident events, use global.

     To set the location attribute:
     + provide the argument organization_event on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property servicehealth/location.

  --organization=ORGANIZATION
     The organization id of the organizationEvent resource.

     To set the organization attribute:
     + provide the argument organization_event on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To get details of an organization event, run:

    $ gcloud service-health organization-events describe my-event \
        --organization=123456789 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-health/organization-events/describe)

---
### `gcloud service-health organization-events list`

List events under a given organization and location

Retrieves organization events within a specified organization and location. For service health incident events, set location to `global`.

**Synopsis:**
```
gcloud service-health organization-events list [--view=VIEW]
    [--location=LOCATION --organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | `servicehealth/location` property | The location id of the location resource. Set to `global` for service health incident events. |
| `--organization` | ORGANIZATION |  | The organization id (numeric organization ID) of the location resource. |
| `--view` | VIEW | `organization-event-view-basic` | Organization event fields to include in the response. Choices: `organization-event-view-basic` (default), `organization-event-view-full`. |
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. Applied after `--flatten`, before `--sort-by` and `--limit`. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list organization events in location global, run:

    $ gcloud service-health organization-events list \
        --organization=123456789 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-health/organization-events/list)

---

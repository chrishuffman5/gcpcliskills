# gcloud service-health events

represents events that may affect Google Cloud products

### `gcloud service-health events describe`

Get details of an event affecting a project

Retrieves a resource containing information about an event. For service health incident events, use location `global`.

**Synopsis:**
```
gcloud service-health events describe (EVENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Event resource - Name of the resource, in the format
projects/{project_id}/locations/{location}/events/{event_id}. The
arguments in this group can be used to specify the attributes of this
resource.

To set the project attribute:
 * provide the argument event on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EVENT
     ID of the event or fully qualified identifier for the event.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location to use when working with Service Health resources. For
     service health incident events, use global.

     To set the location attribute:
     + provide the argument event on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property servicehealth/location.
```

**Examples:**
```bash
To get details of an event, run:

    $ gcloud service-health events describe my-event \
        --project=my-project --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-health/events/describe)

---
### `gcloud service-health events list`

List events under a given project and location

Lists service health events for a specified project and location. To retrieve service health incident events, set location to `global`.

**Synopsis:**
```
gcloud service-health events list [--location=LOCATION] [--view=VIEW]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | `servicehealth/location` property | ID of the location or fully qualified identifier for the location. Set to `global` for service health incident events. Can also be set via the `servicehealth/location` property. |
| `--view` | VIEW | `event-view-basic` | Event fields to include in the response. Choices: `event-view-basic` (excludes the `updates` field), `event-view-full` (includes all fields). |
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, the item is listed. See `gcloud topic filters` for details. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. Applied after `--flatten`, `--sort-by`, and `--filter`. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page for services that support paging. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list events under a project in location global, run:

    $ gcloud service-health events list \
        --project=my-project --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-health/events/list)

---

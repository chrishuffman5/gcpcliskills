# gcloud service-health organization-impacts

represents impact to assets at organizational level

### `gcloud service-health organization-impacts describe`

Get details of an asset impact by an event under an organization

Retrieves a resource containing information about impact to an asset under an organization affected by a service health event. For service health incident events, use location `global`.

**Synopsis:**
```
gcloud service-health organization-impacts describe
    (ORGANIZATION_IMPACT : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OrganizationImpact resource - Name of the resource, in the format
organizations/{organization_id}/locations/global/organizationImpacts/{organization_impact_id}.

This must be specified.

  ORGANIZATION_IMPACT
     ID of the organizationImpact or fully qualified identifier for the
     organizationImpact.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location to use when working with Service Health resources. For
     service health incident events, use global.

     To set the location attribute:
     + provide the argument organization_impact on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property servicehealth/location.

  --organization=ORGANIZATION
     The organization id of the organizationImpact resource.

     To set the organization attribute:
     + provide the argument organization_impact on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To get details of an organization impact, run:

    $ gcloud service-health organization-impacts describe my-impact \
        --organization=123456789 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-health/organization-impacts/describe)

---
### `gcloud service-health organization-impacts list`

List assets impacted by events under an organization

Lists assets impacted by organization events under a given organization and location. To retrieve projects impacted by service health incident events, use location `global`.

**Synopsis:**
```
gcloud service-health organization-impacts list [--location=LOCATION]
    [--organization=ORGANIZATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | `servicehealth/location` property | The location to get organization impacts from. Set this field to `global`. |
| `--organization` | ORGANIZATION |  | The organization id (numeric ID of the organization containing the event). |
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed; items evaluating to True are returned. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. |
| `--page-size` | PAGE_SIZE | service default / unlimited | Maximum number of resources per page. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. Prefix a field with `~` for descending order. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output. |

**Examples:**
```bash
To list all organization impacts in location global for organization
123456789, run:

    $ gcloud service-health organization-impacts list \
        --organization=123456789 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-health/organization-impacts/list)

---

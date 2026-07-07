# gcloud access-context-manager supported-services

retrieve VPC Service Controls Supported Services

### `gcloud access-context-manager supported-services describe`

Gets information about a VPC Service Controls Supported Service

Get service information allowed in an access policy object.

**Synopsis:**
```
gcloud access-context-manager supported-services describe SERVICE_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Supported service resource - VPC Service Controls supported service. This
represents a Cloud resource.

This must be specified.

  SERVICE_NAME
     ID of the supported-service or fully qualified identifier for the
     supported-service.

     To set the service_name attribute:
     + provide the argument service_name on the command line.
```

**Examples:**
```bash
To get VPC Service Controls support information for
bigquery.googleapis.com, run:

    $ gcloud access-context-manager supported-services describe \
        bigquery.googleapis.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/supported-services/describe)

---
### `gcloud access-context-manager supported-services list`

Lists all VPC Service Controls supported services

Lists the services that VPC Service Controls supports. The services that
are in this list fully support VPC Service Controls or the integration of
this service with VPC Service Controls is in Preview stage
(https://cloud.google.com/products#product-launch-stages), or the service
integration is scheduled to be shut down and removed which is in
[Deprecation stage]
(https://cloud.google.com/products#product-launch-stages). Services that
aren't in this list don't support VPC Service Controls and aren't
guaranteed to function properly in a VPC Service Controls environment.

**Synopsis:**
```
gcloud access-context-manager supported-services list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list VPC Service Controls supported services, run:

    $ gcloud access-context-manager supported-services list

This command prints out a list of all supported services in a tabular form:

    NAME                    TITLE                SERVICE_SUPPORT_STAGE  AVAILABLE_ON_RESTRICTED_VIP KNOWN_LIMITATIONS
    vpcsc_supported_service VPC-SC Supported API GA                     True                        False
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/supported-services/list)

---
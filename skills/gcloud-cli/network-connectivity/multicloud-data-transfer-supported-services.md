# gcloud network-connectivity multicloud-data-transfer-supported-services

manage Multicloud Data Transfer Supported Service resources

### `gcloud network-connectivity multicloud-data-transfer-supported-services describe`

Describe multicloudDataTransferSupportedService

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-supported-services
    describe
    (MULTICLOUD_DATA_TRANSFER_SUPPORTED_SERVICE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MulticloudDataTransferSupportedService resource - The name of the service.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicloud_data_transfer_supported_service on
   the command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICLOUD_DATA_TRANSFER_SUPPORTED_SERVICE
     ID of the multicloudDataTransferSupportedService or fully qualified
     identifier for the multicloudDataTransferSupportedService.

     To set the multicloud_data_transfer_supported_service attribute:
     + provide the argument multicloud_data_transfer_supported_service
       on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the multicloudDataTransferSupportedService
     resource.

     To set the location attribute:
     + provide the argument multicloud_data_transfer_supported_service
       on the command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the multicloudDataTransferSupportedService, run:

$ gcloud network-connectivity \        multicloud-data-transfer-supported-services describe \
    compute-engine --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-supported-services/describe)

---
### `gcloud network-connectivity multicloud-data-transfer-supported-services list`

List multicloudDataTransferSupportedServices

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-supported-services
    list --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all multicloudDataTransferSupportedServices, run:

$ gcloud network-connectivity \        multicloud-data-transfer-supported-services list \
    --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-supported-services/list)

---
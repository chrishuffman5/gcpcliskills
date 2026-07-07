# gcloud network-connectivity multicloud-data-transfer-configs

manage Multicloud Data Transfer Config resources

### `gcloud network-connectivity multicloud-data-transfer-configs create`

Create a multicloudDataTransferConfig

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs create
    (MULTICLOUD_DATA_TRANSFER_CONFIG : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--etag=ETAG] [--labels=[LABELS,...]]
    [--request-id=REQUEST_ID] [--services=[SERVICES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MulticloudDataTransferConfig resource - Identifier. The name of the
MulticloudDataTransferConfig resource. Format:
projects/{project}/locations/{location}/multicloudDataTransferConfigs/{multicloud_data_transfer_config}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicloud_data_transfer_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICLOUD_DATA_TRANSFER_CONFIG
     ID of the multicloudDataTransferConfig or fully qualified identifier
     for the multicloudDataTransferConfig.

     To set the multicloud_data_transfer_config attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the multicloudDataTransferConfig resource.

     To set the location attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of this resource. |
| `--etag` | ETAG |  | The etag is computed by the server, and might be sent with update and delete requests so that the client has an up-to-date value before proceeding. |
| `--labels` | [LABELS,...] |  | User-defined labels. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | A request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server can ignore the request if it has already been completed. The server waits for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, can ignore the second request. This prevents clients from accidentally creating duplicate MulticloudDataTransferConfig resources. The request ID must be a valid UUID with the exception that zero UUID (00000000-0000-0000-0000-000000000000) isn't supported. |
| `--services` | [SERVICES,...] |  | Maps services to their current or planned states. Service names are keys, and the associated values describe the state of the service. If a state change is expected, the value is either ADDING or DELETING, depending on the actions taken. Sample output: "services": { "big-query": { "states": [ { "effectiveTime": "2024-12-12T08:00:00Z" "state": "ADDING", }, ] }, "cloud-storage": { "states": [ { "state": "ACTIVE", } ] } }. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --services=string JSON Example: --services='{"string": {}}' File Example: --services=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create the multicloudDataTransferConfig, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        create config-1 --location=europe-west1 \
    --description="Multicloud Data Transfer Config description" \
    --services=compute-engine,cloud-storage
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/create)

---
### `gcloud network-connectivity multicloud-data-transfer-configs delete`

Delete a multicloudDataTransferConfig

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs delete
    (MULTICLOUD_DATA_TRANSFER_CONFIG : --location=LOCATION) [--async]
    [--etag=ETAG] [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MulticloudDataTransferConfig resource - The name of the
MulticloudDataTransferConfig resource to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument multicloud_data_transfer_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICLOUD_DATA_TRANSFER_CONFIG
     ID of the multicloudDataTransferConfig or fully qualified identifier
     for the multicloudDataTransferConfig.

     To set the multicloud_data_transfer_config attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the multicloudDataTransferConfig resource.

     To set the location attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The etag is computed by the server, and might be sent with update and delete requests so that the client has an up-to-date value before proceeding. |
| `--request-id` | REQUEST_ID |  | A request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server can ignore the request if it has already been completed. The server waits for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, can ignore the second request. This prevents clients from accidentally creating duplicate MulticloudDataTransferConfig resources. The request ID must be a valid UUID with the exception that zero UUID (00000000-0000-0000-0000-000000000000) isn't supported. |


**Examples:**
```bash
To delete the multicloudDataTransferConfig, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        delete config-1 --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/delete)

---
### `gcloud network-connectivity multicloud-data-transfer-configs describe`

Describe a multicloudDataTransferConfig

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs describe
    (MULTICLOUD_DATA_TRANSFER_CONFIG : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MulticloudDataTransferConfig resource - The name of the
MulticloudDataTransferConfig resource to get. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument multicloud_data_transfer_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICLOUD_DATA_TRANSFER_CONFIG
     ID of the multicloudDataTransferConfig or fully qualified identifier
     for the multicloudDataTransferConfig.

     To set the multicloud_data_transfer_config attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the multicloudDataTransferConfig resource.

     To set the location attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the multicloudDataTransferConfig, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        describe config-1 --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/describe)

---
### `gcloud network-connectivity multicloud-data-transfer-configs list`

List multicloudDataTransferConfigs

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs list
    --location=LOCATION [--return-partial-success] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--return-partial-success` |  |  | If true, allows partial responses for multi-regional aggregated list requests. |


**Examples:**
```bash
To list all multicloudDataTransferConfigs, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        list --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/list)

---
### `gcloud network-connectivity multicloud-data-transfer-configs update`

Update a multicloudDataTransferConfig

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs update
    (MULTICLOUD_DATA_TRANSFER_CONFIG : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--etag=ETAG] [--request-id=REQUEST_ID]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS]
    [--services=[SERVICES,...]
      | --update-services=[UPDATE_SERVICES,...] --clear-services
      | --remove-services=REMOVE_SERVICES] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MulticloudDataTransferConfig resource - Identifier. The name of the
MulticloudDataTransferConfig resource. Format:
projects/{project}/locations/{location}/multicloudDataTransferConfigs/{multicloud_data_transfer_config}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicloud_data_transfer_config on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICLOUD_DATA_TRANSFER_CONFIG
     ID of the multicloudDataTransferConfig or fully qualified identifier
     for the multicloudDataTransferConfig.

     To set the multicloud_data_transfer_config attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the multicloudDataTransferConfig resource.

     To set the location attribute:
     + provide the argument multicloud_data_transfer_config on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of this resource. |
| `--etag` | ETAG |  | The etag is computed by the server, and might be sent with update and delete requests so that the client has an up-to-date value before proceeding. |
| `--request-id` | REQUEST_ID |  | A request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server can ignore the request if it has already been completed. The server waits for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, can ignore the second request. This prevents clients from accidentally creating duplicate MulticloudDataTransferConfig resources. The request ID must be a valid UUID with the exception that zero UUID (00000000-0000-0000-0000-000000000000) isn't supported. |


**Examples:**
```bash
To update the multicloudDataTransferConfig, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        update config-1 --location=europe-west1 \
    --description="Multicloud Data Transfer Config description \
    updated" --update-services=cloud-run
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/update)

---

## `gcloud network-connectivity multicloud-data-transfer-configs destinations` — manage Destination resources
### `gcloud network-connectivity multicloud-data-transfer-configs destinations create`

Create a destination

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs destinations
    create
    (DESTINATION : --location=LOCATION
      --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG)
    --endpoints=[asn=ASN],[csp=CSP] --ip-prefix=IP_PREFIX [--async]
    [--description=DESCRIPTION] [--etag=ETAG] [--labels=[LABELS,...]]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Destination resource - Identifier. The name of the Destination resource.
Format:
projects/{project}/locations/{location}/multicloudDataTransferConfigs/{multicloud_data_transfer_config}/destinations/{destination}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument destination on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DESTINATION
     ID of the destination or fully qualified identifier for the
     destination.

     To set the destination attribute:
     + provide the argument destination on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the destination resource.

     To set the location attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG
     The multicloudDataTransferConfig id of the destination resource.

     To set the multicloud-data-transfer-config attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --multicloud-data-transfer-config on the
       command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--endpoints` | [asn=ASN],[csp=CSP] |  | Required, The list of DestinationEndpoint resources configured for the IP prefix. asn The ASN of the remote IP prefix. csp The CSP of the remote IP prefix. Shorthand Example: --endpoints=asn=int,csp=string --endpoints=asn=int,csp=string JSON Example: --endpoints='[{"asn": int, "csp": "string"}]' File Example: --endpoints=path_to_file.(yaml\|json) |
| `--ip-prefix` | IP_PREFIX |  | The IP prefix that represents your workload on another CSP. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of this resource. |
| `--etag` | ETAG |  | The etag is computed by the server, and might be sent with update and delete requests so that the client has an up-to-date value before proceeding. |
| `--labels` | [LABELS,...] |  | User-defined labels. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | A request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server can ignore the request if it has already been completed. The server waits for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, can ignore the second request. This prevents clients from accidentally creating duplicate Destination resources. The request ID must be a valid UUID with the exception that zero UUID (00000000-0000-0000-0000-000000000000) isn't supported. |


**Examples:**
```bash
To create the destination, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        destinations create destination-1 \
    --multicloud-data-transfer-config=config-1 \
    --location=europe-west1 \
    --description="Multicloud Data Transfer destination \
    description" --ip-prefix="10.1.1.0/24" \
    --endpoints=asn=8075,csp=microsoft
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/destinations/create)

---
### `gcloud network-connectivity multicloud-data-transfer-configs destinations delete`

Delete a destination

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs destinations
    delete
    (DESTINATION : --location=LOCATION
      --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG)
    [--async] [--etag=ETAG] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Destination resource - The name of the Destination resource to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument destination on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DESTINATION
     ID of the destination or fully qualified identifier for the
     destination.

     To set the destination attribute:
     + provide the argument destination on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the destination resource.

     To set the location attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG
     The multicloudDataTransferConfig id of the destination resource.

     To set the multicloud-data-transfer-config attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --multicloud-data-transfer-config on the
       command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The etag is computed by the server, and might be sent with update and delete requests so that the client has an up-to-date value before proceeding. |
| `--request-id` | REQUEST_ID |  | A request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server can ignore the request if it has already been completed. The server waits for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, can ignore the second request. The request ID must be a valid UUID with the exception that zero UUID (00000000-0000-0000-0000-000000000000) isn't supported. |


**Examples:**
```bash
To delete the destination, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        destinations delete destination-1 \
    --multicloud-data-transfer-config=config-1 \
    --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/destinations/delete)

---
### `gcloud network-connectivity multicloud-data-transfer-configs destinations describe`

Describe a destination

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs destinations
    describe
    (DESTINATION : --location=LOCATION
      --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Destination resource - The name of the Destination resource to get. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument destination on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DESTINATION
     ID of the destination or fully qualified identifier for the
     destination.

     To set the destination attribute:
     + provide the argument destination on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the destination resource.

     To set the location attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG
     The multicloudDataTransferConfig id of the destination resource.

     To set the multicloud-data-transfer-config attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --multicloud-data-transfer-config on the
       command line.
```

**Examples:**
```bash
To describe the destination, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        destinations describe destination-1 \
    --multicloud-data-transfer-config=config-1 \
    --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/destinations/describe)

---
### `gcloud network-connectivity multicloud-data-transfer-configs destinations list`

List destinations

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs destinations
    list
    (--multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG
      : --location=LOCATION) [--return-partial-success]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicloud-data-transfer-config` | MULTICLOUD_DATA_TRANSFER_CONFIG |  | _[This must be specified.]_ ID of the multicloudDataTransferConfig or fully qualified identifier for the multicloudDataTransferConfig. To set the multicloud-data-transfer-config attribute: + provide the argument --multicloud-data-transfer-config on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the multicloudDataTransferConfig resource. To set the location attribute: + provide the argument --multicloud-data-transfer-config on the command line with a fully specified name; + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--return-partial-success` |  |  | If true, allow partial responses for multi-regional aggregated list requests. |


**Examples:**
```bash
To list all destinations, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        destinations list --multicloud-data-transfer-config=config-1 \
    --location=europe-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/destinations/list)

---
### `gcloud network-connectivity multicloud-data-transfer-configs destinations update`

Update a destination

**Synopsis:**
```
gcloud network-connectivity multicloud-data-transfer-configs destinations
    update
    (DESTINATION : --location=LOCATION
      --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG)
    [--async] [--description=DESCRIPTION] [--etag=ETAG]
    [--request-id=REQUEST_ID]
    [--endpoints=[asn=ASN],[csp=CSP]
      | --add-endpoints=[asn=ASN],[csp=CSP] --clear-endpoints
      | --remove-endpoints=[asn=ASN],[csp=CSP]]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Destination resource - Identifier. The name of the Destination resource.
Format:
projects/{project}/locations/{location}/multicloudDataTransferConfigs/{multicloud_data_transfer_config}/destinations/{destination}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument destination on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DESTINATION
     ID of the destination or fully qualified identifier for the
     destination.

     To set the destination attribute:
     + provide the argument destination on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the destination resource.

     To set the location attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --multicloud-data-transfer-config=MULTICLOUD_DATA_TRANSFER_CONFIG
     The multicloudDataTransferConfig id of the destination resource.

     To set the multicloud-data-transfer-config attribute:
     + provide the argument destination on the command line with a fully
       specified name;
     + provide the argument --multicloud-data-transfer-config on the
       command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of this resource. |
| `--etag` | ETAG |  | The etag is computed by the server, and might be sent with update and delete requests so that the client has an up-to-date value before proceeding. |
| `--request-id` | REQUEST_ID |  | A request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server can ignore the request if it has already been completed. The server waits for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, can ignore the second request. The request ID must be a valid UUID with the exception that zero UUID (00000000-0000-0000-0000-000000000000) isn't supported. |


**Examples:**
```bash
To update the destination, run:

$ gcloud network-connectivity multicloud-data-transfer-configs \        destinations update destination-1 \
    --multicloud-data-transfer-config=config-1 \
    --location=europe-west1 \
    --description="Multicloud Data Transfer destination description \
    updated" --endpoints=asn=16509,csp=aws
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/multicloud-data-transfer-configs/destinations/update)

---
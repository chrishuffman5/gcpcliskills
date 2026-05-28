# gcloud network-connectivity regional-endpoints

manage Network Connectivity RegionalEndpoints

### `gcloud network-connectivity regional-endpoints create`

Create a new regional endpoint

Create a new regional endpoint with the given name.

**Synopsis:**
```
gcloud network-connectivity regional-endpoints create
    (REGIONAL_ENDPOINT : --region=REGION)
    --target-google-api=TARGET_GOOGLE_API [--address=ADDRESS] [--async]
    [--description=DESCRIPTION] [--enable-global-access]
    [--labels=[KEY=VALUE,...]] [--network=NETWORK]
    [--subnetwork=SUBNETWORK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RegionalEndpoint resource - Name of the regional endpoint to be created.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument regional_endpoint on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REGIONAL_ENDPOINT
     ID of the regionalEndpoint or fully qualified identifier for the
     regionalEndpoint.

     To set the regional_endpoint attribute:
     + provide the argument regional_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument regional_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-google-api` | TARGET_GOOGLE_API |  | The service endpoint the regional endpoint will connect to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--address` | ADDRESS |  | The IP Address of the Regional Endpoint. When no address is provided, an IP from the subnetwork is allocated. Use one of the following formats: * IPv4 address as in 10.0.0.1 * Address resource URI as in projects/{project}/regions/{region}/addresses/{address_name} for an IPv4 or IPv6 address. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the regional endpoint. |
| `--enable-global-access` |  |  | Whether the REGIONAL or GLOBAL access is enabled. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--network` | NETWORK |  | Consumer's VPC network that this regional endpoint belongs to. |
| `--subnetwork` | SUBNETWORK |  | The name of the subnetwork from which the IP address will be allocated. |


**Examples:**
```bash
To create a regional endpoint with the name 'my-regional-endpoint' in
us-central1 targeting my-target-endpoint, run:

    $ gcloud network-connectivity regional-endpoints create \
        my-regional-endpoint --region=us-central1 \
        [--address=my-address] [--network=my-network] \
        [--subnetwork=my-subnet] \
        --target-google-api=my-target-endpoint [--enable-global-access]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/regional-endpoints/create)

---
### `gcloud network-connectivity regional-endpoints delete`

Delete a regional endpoint

Delete the specified regional endpoint.

**Synopsis:**
```
gcloud network-connectivity regional-endpoints delete
    (REGIONAL_ENDPOINT : --region=REGION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RegionalEndpoint resource - Name of the regional endpoint to be deleted.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument regional_endpoint on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REGIONAL_ENDPOINT
     ID of the regionalEndpoint or fully qualified identifier for the
     regionalEndpoint.

     To set the regional_endpoint attribute:
     + provide the argument regional_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument regional_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a regional endpoint named 'my-regional-endpoint' in us-central1:

    $ gcloud network-connectivity regional-endpoints delete \
        my-regional-endpoint --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/regional-endpoints/delete)

---
### `gcloud network-connectivity regional-endpoints describe`

Describe a regional endpoint

Retrieve and display details about a regional endpoint.

**Synopsis:**
```
gcloud network-connectivity regional-endpoints describe
    (REGIONAL_ENDPOINT : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RegionalEndpoint resource - Name of the regional endpoint to be described.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument regional_endpoint on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REGIONAL_ENDPOINT
     ID of the regionalEndpoint or fully qualified identifier for the
     regionalEndpoint.

     To set the regional_endpoint attribute:
     + provide the argument regional_endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument regional_endpoint on the command line with a
       fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
Display details about a regional endpoint named 'my-regional-endpoint' in
us-central1:

    $ gcloud network-connectivity regional-endpoints describe \
        my-regional-endpoint --region=us-central1 [--project=my-project]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/regional-endpoints/describe)

---
### `gcloud network-connectivity regional-endpoints list`

List regional endpoints

Retrieve and display a list of all regional endpoints in the specified
project.

**Synopsis:**
```
gcloud network-connectivity regional-endpoints list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all regional endpoints in us-central1, run:

    $ gcloud network-connectivity regional-endpoints list \
        --region=us-central1 [--project=my-project]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/regional-endpoints/list)

---
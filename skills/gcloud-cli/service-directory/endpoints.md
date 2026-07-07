# gcloud service-directory endpoints

manage Service Directory endpoints

### `gcloud service-directory endpoints create`

Creates an endpoint

Creates an endpoint.

**Synopsis:**
```
gcloud service-directory endpoints create
    (ENDPOINT
      : --location=LOCATION --namespace=NAMESPACE --service=SERVICE)
    [--address=ADDRESS] [--annotations=[KEY=VALUE,...]] [--network=NETWORK]
    [--port=PORT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The Service Directory endpoint to create. The endpoint
id must be 1-63 characters long and match the regular expression
[a-z](?:[-a-z0-9]{0,61}[a-z0-9])? which means the first character must be
a lowercase letter, and all following characters must be a dash, lowercase
letter, or digit, except the last character, which cannot be a dash. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the endpoint.

     To set the location attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the endpoint.

     To set the namespace attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

  --service=SERVICE
     The name of the service for the endpoint.

     To set the service attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--address` | ADDRESS |  | IPv4 or IPv6 address of the endpoint. The default is empty string. |
| `--annotations` | [KEY=VALUE,...] |  | Annotations for the endpoint. Annotations take the form of key/value string pairs. Keys are composed of an optional prefix and a name segment, separated by a slash(/). Prefixes and names must be composed of alphanumeric characters, dashes, and dots. Names may also use underscores. There are no character restrictions on what may go into the value of an annotation. The entire dictionary is limited to 512 characters, spread across all key-value pairs. |
| `--network` | NETWORK |  | Specifies the Google Compute Engine Network (VPC) of the Endpoint. Network and Project existence is not checked. Example: projects/<PROJECT_NUM>/locations/global/networks/<NETWORK_NAME> The default is empty string. |
| `--port` | PORT |  | Port that the endpoint is running on, must be in the range of [0, 65535]. The default is 0. |


**Examples:**
```bash
To create a Service Directory endpoint, run:

    $ gcloud service-directory endpoints create my-endpoint \
        --service=my-service --namespace=my-namespace \
        --location=us-east1 --address=1.2.3.4 --port=5 \
        --annotations=a=b,c=d \
        --network=projects/123456789/locations/global/networks/default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/endpoints/create)

---
### `gcloud service-directory endpoints delete`

Deletes an endpoint

Deletes an endpoint.

**Synopsis:**
```
gcloud service-directory endpoints delete
    (ENDPOINT
      : --location=LOCATION --namespace=NAMESPACE --service=SERVICE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The Service Directory endpoint to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the endpoint.

     To set the location attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the endpoint.

     To set the namespace attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

  --service=SERVICE
     The name of the service for the endpoint.

     To set the service attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Examples:**
```bash
To delete a Service Directory endpoint, run:

    $ gcloud service-directory endpoints delete my-endpoint \
        --service=my-service --namespace=my-namespace \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/endpoints/delete)

---
### `gcloud service-directory endpoints describe`

Describes an endpoint

Describes an endpoint.

**Synopsis:**
```
gcloud service-directory endpoints describe
    (ENDPOINT
      : --location=LOCATION --namespace=NAMESPACE --service=SERVICE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The Service Directory endpoint to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the endpoint.

     To set the location attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the endpoint.

     To set the namespace attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

  --service=SERVICE
     The name of the service for the endpoint.

     To set the service attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Examples:**
```bash
To describe a Service Directory endpoint, run:

    $ gcloud service-directory endpoints describe my-endpoint \
        --service=my-service --namespace=my-namespace \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/endpoints/describe)

---
### `gcloud service-directory endpoints list`

Lists endpoints

Lists endpoints.

**Synopsis:**
```
gcloud service-directory endpoints list
    (--service=SERVICE : --location=LOCATION --namespace=NAMESPACE)
    [--filter=EXPRESSION] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | _[This must be specified.]_ ID of the service or fully qualified identifier for the service. To set the service attribute: + provide the argument --service on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The name of the region for the service. To set the location attribute: + provide the argument --service on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--namespace` | NAMESPACE |  | _[This must be specified.]_ The name of the namespace for the service. To set the namespace attribute: + provide the argument --service on the command line with a fully specified name; + provide the argument --namespace on the command line. |


**Examples:**
```bash
To list Service Directory endpoints, run:

    $ gcloud service-directory endpoints list --service=my-service \
        --namespace=my-namespace --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/endpoints/list)

---
### `gcloud service-directory endpoints update`

Updates an endpoint

Updates an endpoint.

**Synopsis:**
```
gcloud service-directory endpoints update
    (ENDPOINT
      : --location=LOCATION --namespace=NAMESPACE --service=SERVICE)
    [--address=ADDRESS] [--annotations=[KEY=VALUE,...]] [--port=PORT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - The Service Directory endpoint to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The name of the region for the endpoint.

     To set the location attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The name of the namespace for the endpoint.

     To set the namespace attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

  --service=SERVICE
     The name of the service for the endpoint.

     To set the service attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --service on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--address` | ADDRESS |  | IPv4 or IPv6 address of the endpoint. The default is empty string. |
| `--annotations` | [KEY=VALUE,...] |  | Annotations for the endpoint. Annotations take the form of key/value string pairs. Keys are composed of an optional prefix and a name segment, separated by a slash(/). Prefixes and names must be composed of alphanumeric characters, dashes, and dots. Names may also use underscores. There are no character restrictions on what may go into the value of an annotation. The entire dictionary is limited to 512 characters, spread across all key-value pairs. |
| `--port` | PORT |  | Port that the endpoint is running on, must be in the range of [0, 65535]. The default is 0. |


**Examples:**
```bash
To update a Service Directory endpoint, run:

    $ gcloud service-directory endpoints update my-endpoint \
        --service=my-service --namespace=my-namespace \
        --location=us-east1 --address=1.2.3.4 --port=5 \
        --annotations=a=b,c=d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/service-directory/endpoints/update)

---
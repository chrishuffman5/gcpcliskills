# gcloud beyondcorp security-gateways

manage Security Gateway resources

### `gcloud beyondcorp security-gateways create`

Create securityGateways

Create a securityGateway

**Synopsis:**
```
gcloud beyondcorp security-gateways create
    (SECURITY_GATEWAY : --location=LOCATION) [--async]
    [--display-name=DISPLAY_NAME] [--hubs=[HUBS,...]]
    [--request-id=REQUEST_ID]
    [--resource-override-path=RESOURCE_OVERRIDE_PATH]
    [--proxy-protocol-config-allowed-client-headers=[PROXY_PROTOCOL_CONFIG_ALLOWED_CLIENT_HEADERS,
      ...] --proxy-protocol-config-client-ip
      --proxy-protocol-config-gateway-identity=PROXY_PROTOCOL_CONFIG_GATEWAY_IDENTITY --proxy-protocol-config-metadata-headers=[PROXY_PROTOCOL_CONFIG_METADATA_HEADERS,
      ...] --contextual-headers-output-type=CONTEXTUAL_HEADERS_OUTPUT_TYPE
      --device-info-output-type=DEVICE_INFO_OUTPUT_TYPE
      --group-info-output-type=GROUP_INFO_OUTPUT_TYPE
      --user-info-output-type=USER_INFO_OUTPUT_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SecurityGateway resource - Identifier. Name of the resource. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument security_gateway on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECURITY_GATEWAY
     ID of the securityGateway or fully qualified identifier for the
     securityGateway.

     To set the security_gateway attribute:
     + provide the argument security_gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the securityGateway resource. We support only
     global location.

     To set the location attribute:
     + provide the argument security_gateway on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | An arbitrary user-provided name for the SecurityGateway. Cannot exceed 64 characters. |
| `--hubs` | [HUBS,...] |  | Map of Hubs that represents regional data path deployment with Google Cloud Platform region as a key. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --hubs=string JSON Example: --hubs='{"string": {}}' File Example: --hubs=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. |


**Examples:**
```bash
To create the securityGateway, run:

    $ gcloud beyondcorp security-gateways create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/create)

---
### `gcloud beyondcorp security-gateways delete`

Delete securityGateways

Delete a securityGateway

**Synopsis:**
```
gcloud beyondcorp security-gateways delete
    (SECURITY_GATEWAY : --location=LOCATION) [--async]
    [--request-id=REQUEST_ID] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SecurityGateway resource - BeyondCorp SecurityGateway name using the form:
projects/{project_id}/locations/{location_id}/securityGateways/{security_gateway_id}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument security_gateway on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECURITY_GATEWAY
     ID of the securityGateway or fully qualified identifier for the
     securityGateway.

     To set the security_gateway attribute:
     + provide the argument security_gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the securityGateway resource. We support only
     global location.

     To set the location attribute:
     + provide the argument security_gateway on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--validate-only` |  |  | If set, validates request by executing a dry-run which would not alter the resource in any way. |


**Examples:**
```bash
To delete the securityGateway, run:

    $ gcloud beyondcorp security-gateways delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/delete)

---
### `gcloud beyondcorp security-gateways describe`

Describe securityGateways

Describe a securityGateway

**Synopsis:**
```
gcloud beyondcorp security-gateways describe
    (SECURITY_GATEWAY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SecurityGateway resource - The resource name of the PartnerTenant using
the form:
projects/{project_id}/locations/{location_id}/securityGateway/{security_gateway_id}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument security_gateway on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECURITY_GATEWAY
     ID of the securityGateway or fully qualified identifier for the
     securityGateway.

     To set the security_gateway attribute:
     + provide the argument security_gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the securityGateway resource. We support only
     global location.

     To set the location attribute:
     + provide the argument security_gateway on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the securityGateway, run:

    $ gcloud beyondcorp security-gateways describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/describe)

---
### `gcloud beyondcorp security-gateways get-iam-policy`

Get the IAM policy for a security gateway

Gets the IAM policy for the given security gateway.

**Synopsis:**
```
gcloud beyondcorp security-gateways get-iam-policy
    (SECURITY_GATEWAY : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SecurityGateway resource - The security gateway for which to get the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument security_gateway on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECURITY_GATEWAY
     ID of the securityGateway or fully qualified identifier for the
     securityGateway.

     To set the security_gateway attribute:
     + provide the argument security_gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the securityGateway resource. We support only
     global location.

     To set the location attribute:
     + provide the argument security_gateway on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the IAM policy for a security gateway my-security-gateway run:

    $ gcloud beyondcorp security-gateways get-iam-policy \
        my-security-gateway --project=consumer-project-id \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/get-iam-policy)

---
### `gcloud beyondcorp security-gateways list`

List securityGateways

**Synopsis:**
```
gcloud beyondcorp security-gateways list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all securityGateways, run:

    $ gcloud beyondcorp security-gateways list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/list)

---
### `gcloud beyondcorp security-gateways set-iam-policy`

Set the IAM policy for a security gateway

Sets the IAM policy for the given security gateway.

**Synopsis:**
```
gcloud beyondcorp security-gateways set-iam-policy
    (SECURITY_GATEWAY : --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SecurityGateway resource - The security gateway for which to set the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument security_gateway on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECURITY_GATEWAY
     ID of the securityGateway or fully qualified identifier for the
     securityGateway.

     To set the security_gateway attribute:
     + provide the argument security_gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the securityGateway resource. We support only
     global location.

     To set the location attribute:
     + provide the argument security_gateway on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the security gateway with ID
my-security-gateway:

    $ gcloud beyondcorp security-gateways set-iam-policy \
        my-security-gateway policy.json --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/set-iam-policy)

---
### `gcloud beyondcorp security-gateways update`

Update securityGateways

Update a securityGateway

**Synopsis:**
```
gcloud beyondcorp security-gateways update
    (SECURITY_GATEWAY : --location=LOCATION) [--async]
    [--display-name=DISPLAY_NAME] [--request-id=REQUEST_ID]
    [--clear-proxy-protocol-config --[no-]proxy-protocol-config-client-ip
      --proxy-protocol-config-gateway-identity=PROXY_PROTOCOL_CONFIG_GATEWAY_IDENTITY --contextual-headers-output-type=CONTEXTUAL_HEADERS_OUTPUT_TYPE --device-info-output-type=DEVICE_INFO_OUTPUT_TYPE --group-info-output-type=GROUP_INFO_OUTPUT_TYPE --user-info-output-type=USER_INFO_OUTPUT_TYPE --proxy-protocol-config-allowed-client-headers=[PROXY_PROTOCOL_CONFIG_ALLOWED_CLIENT_HEADERS,
      ...]
      | --add-proxy-protocol-config-allowed-client-headers=[ADD_PROXY_PROTOCOL_CONFIG_ALLOWED_CLIENT_HEADERS,
      ...] --clear-proxy-protocol-config-allowed-client-headers
      | --remove-proxy-protocol-config-allowed-client-headers=[REMOVE_PROXY_PROTOCOL_CONFIG_ALLOWED_CLIENT_HEADERS,
      ...]
      --proxy-protocol-config-metadata-headers=[PROXY_PROTOCOL_CONFIG_METADATA_HEADERS,
      ...]
      | --update-proxy-protocol-config-metadata-headers=[UPDATE_PROXY_PROTOCOL_CONFIG_METADATA_HEADERS,
      ...] --clear-proxy-protocol-config-metadata-headers
      | --remove-proxy-protocol-config-metadata-headers=REMOVE_PROXY_PROTOCOL_CONFIG_METADATA_HEADERS]
    [--clear-service-discovery
      --resource-override-path=RESOURCE_OVERRIDE_PATH]
    [--hubs=[HUBS,...] | --update-hubs=[UPDATE_HUBS,...] --clear-hubs
      | --remove-hubs=REMOVE_HUBS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SecurityGateway resource - Identifier. Name of the resource. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument security_gateway on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECURITY_GATEWAY
     ID of the securityGateway or fully qualified identifier for the
     securityGateway.

     To set the security_gateway attribute:
     + provide the argument security_gateway on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the securityGateway resource. We support only
     global location.

     To set the location attribute:
     + provide the argument security_gateway on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | An arbitrary user-provided name for the SecurityGateway. Cannot exceed 64 characters. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request timed out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To update the securityGateway, run:

    $ gcloud beyondcorp security-gateways update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/update)

---

## `gcloud beyondcorp security-gateways applications` — manage Application resources
### `gcloud beyondcorp security-gateways applications create`

Create applications

Create an application

**Synopsis:**
```
gcloud beyondcorp security-gateways applications create
    (APPLICATION : --location=LOCATION --security-gateway=SECURITY_GATEWAY)
    [--async] [--display-name=DISPLAY_NAME]
    [--endpoint-matchers=[hostname=HOSTNAME],[ports=PORTS]]
    [--request-id=REQUEST_ID] [--schema=SCHEMA]
    [--upstreams=[egressPolicy=EGRESSPOLICY],
      [external=EXTERNAL],[network=NETWORK],[proxyProtocol=PROXYPROTOCOL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - Identifier. Name of the resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource. We support only global
     location.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --security-gateway=SECURITY_GATEWAY
     The securityGateway id of the application resource.

     To set the security-gateway attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --security-gateway on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | An arbitrary user-provided name for the application resource. Cannot exceed 64 characters. |
| `--endpoint-matchers` | [hostname=HOSTNAME],[ports=PORTS] |  | An array of conditions to match the application's network endpoint. Each element in the array is an EndpointMatcher object, which defines a specific combination of a hostname pattern and one or more ports. The application is considered matched if at least one of the EndpointMatcher conditions in this array is met (the conditions are combined using OR logic). Each EndpointMatcher must contain a hostname pattern, such as "example.com", and one or more port numbers specified as a string, such as "443". Hostname and port number examples: ".example.com", "443" "example.com" and "22" "example.com" and "22,33". hostname Hostname of the application. ports The ports of the application. Shorthand Example: --endpoint-matchers=hostname=string,ports=[int] --endpoint-matchers=hostname=string,ports=[int] JSON Example: --endpoint-matchers='[{"hostname": "string", "ports": [int]}]' File Example: --endpoint-matchers=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. |
| `--schema` | one of: api-gateway Service Discovery API endpoint when Service Discovery is enabled in Gateway |  | Type of the external application. SCHEMA must be one of: api-gateway Service Discovery API endpoint when Service Discovery is enabled in Gateway. proxy-gateway Proxy which routes traffic to actual applications, like Netscaler Gateway. |
| `--upstreams` | [egressPolicy=EGRESSPOLICY],[external=EXTERNAL],[network=NETWORK],[proxyProtocol=PROXYPROTOCOL] |  | Which upstream resources to forward traffic to. egressPolicy Routing policy information. regions List of the regions where the application sends traffic. external List of the external endpoints to forward traffic to. endpoints List of the endpoints to forward traffic to. hostname Hostname of the endpoint. port Port of the endpoint. network Network to forward traffic to. name Network name is of the format: projects/{project}/global/networks/{network}. proxyProtocol Enables proxy protocol configuration for the upstream. allowedClientHeaders List of the allowed client header names. clientIp Client IP configuration. The client IP address is included if true. contextualHeaders Configuration for the contextual headers. deviceInfo The device information configuration. outputType The output type details for the delegated device. groupInfo Group details. outputType The output type of the delegated group information. outputType Default output type for all enabled headers. userInfo User details. outputType The delegated user's information. gatewayIdentity The security gateway identity configuration. metadataHeaders Custom resource specific headers along with the values. The names should conform to RFC 9110: >Field names can contain alphanumeric characters, hyphens, and periods, can contain only ASCII-printable characters and tabs, and must start with a letter. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --upstreams=egressPolicy={regions=[string]},external={endpoints=[{hostname=string,port=int}]},network={name=string},proxyProtocol={allowedClientHeaders=[string],clientIp=boolean,contextualHeaders={deviceInfo={outputType=string},groupInfo={outputType=string},outputType=string,userInfo={outputType=string}},gatewayIdentity=string,metadataHeaders={string=string}} --upstreams=egressPolicy={regions=[string]},external={endpoints=[{hostname=string,port=int}]},network={name=string},proxyProtocol={allowedClientHeaders=[string],clientIp=boolean,contextualHeaders={deviceInfo={outputType=string},groupInfo={outputType=string},outputType=string,userInfo={outputType=string}},gatewayIdentity=string,metadataHeaders={string=string}} JSON Example: --upstreams='[{"egressPolicy": {"regions": ["string"]}, "external": {"endpoints": [{"hostname": "string", "port": int}]}, "network": {"name": "string"}, "proxyProtocol": {"allowedClientHeaders": ["string"], "clientIp": boolean, "contextualHeaders": {"deviceInfo": {"outputType": "string"}, "groupInfo": {"outputType": "string"}, "outputType": "string", "userInfo": {"outputType": "string"}}, "gatewayIdentity": "string", "metadataHeaders": {"string": "string"}}}]' File Example: --upstreams=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create the application, run:

    $ gcloud beyondcorp security-gateways applications create
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/create)

---
### `gcloud beyondcorp security-gateways applications delete`

Delete applications

Delete an application

**Synopsis:**
```
gcloud beyondcorp security-gateways applications delete
    (APPLICATION : --location=LOCATION --security-gateway=SECURITY_GATEWAY)
    [--async] [--request-id=REQUEST_ID] [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - Name of the resource. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource. We support only global
     location.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --security-gateway=SECURITY_GATEWAY
     The securityGateway id of the application resource.

     To set the security-gateway attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --security-gateway on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--validate-only` |  |  | If set, validates request by executing a dry-run which would not alter the resource in any way. |


**Examples:**
```bash
To delete the application, run:

    $ gcloud beyondcorp security-gateways applications delete
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/delete)

---
### `gcloud beyondcorp security-gateways applications describe`

Describe applications

Describe an application

**Synopsis:**
```
gcloud beyondcorp security-gateways applications describe
    (APPLICATION : --location=LOCATION --security-gateway=SECURITY_GATEWAY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The resource name of the Application using the
form:
projects/{project_id}/locations/global/securityGateway/{security_gateway_id}/applications/{application_id}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource. We support only global
     location.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --security-gateway=SECURITY_GATEWAY
     The securityGateway id of the application resource.

     To set the security-gateway attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --security-gateway on the command line.
```

**Examples:**
```bash
To describe the application, run:

    $ gcloud beyondcorp security-gateways applications describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/describe)

---
### `gcloud beyondcorp security-gateways applications get-iam-policy`

Get the IAM policy for a security gateway application

Gets the IAM policy for the given security gateway application.

**Synopsis:**
```
gcloud beyondcorp security-gateways applications get-iam-policy
    (APPLICATION : --location=LOCATION --security-gateway=SECURITY_GATEWAY)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The security gateway application for which to get
the IAM policy. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource. We support only global
     location.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --security-gateway=SECURITY_GATEWAY
     The securityGateway id of the application resource.

     To set the security-gateway attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --security-gateway on the command line.
```

**Examples:**
```bash
To get the IAM policy for a security gateway application
my-security-gateway-application run:

    $ gcloud beyondcorp security-gateways applications get-iam-policy \
        my-security-gateway-application --project=consumer-project-id \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/get-iam-policy)

---
### `gcloud beyondcorp security-gateways applications list`

List applications

**Synopsis:**
```
gcloud beyondcorp security-gateways applications list
    (--security-gateway=SECURITY_GATEWAY : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-gateway` | SECURITY_GATEWAY |  | _[This must be specified.]_ ID of the securityGateway or fully qualified identifier for the securityGateway. To set the security-gateway attribute: + provide the argument --security-gateway on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the securityGateway resource. We support only global location. To set the location attribute: + provide the argument --security-gateway on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all applications, run:

    $ gcloud beyondcorp security-gateways applications list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/list)

---
### `gcloud beyondcorp security-gateways applications set-iam-policy`

Set the IAM policy for a security gateway application

Sets the IAM policy for the given security gateway application.

**Synopsis:**
```
gcloud beyondcorp security-gateways applications set-iam-policy
    (APPLICATION : --location=LOCATION --security-gateway=SECURITY_GATEWAY)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The security gateway application for which to set
the IAM policy. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource. We support only global
     location.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --security-gateway=SECURITY_GATEWAY
     The securityGateway id of the application resource.

     To set the security-gateway attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --security-gateway on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the security gateway application with ID
my-security-gateway-application:

    $ gcloud beyondcorp security-gateways applications set-iam-policy \
        my-security-gateway-application policy.json --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/set-iam-policy)

---
### `gcloud beyondcorp security-gateways applications update`

Update applications

Update an application

**Synopsis:**
```
gcloud beyondcorp security-gateways applications update
    (APPLICATION : --location=LOCATION --security-gateway=SECURITY_GATEWAY)
    [--async] [--display-name=DISPLAY_NAME] [--request-id=REQUEST_ID]
    [--schema=SCHEMA]
    [--endpoint-matchers=[hostname=HOSTNAME],[ports=PORTS]
      | --add-endpoint-matchers=[hostname=HOSTNAME],[ports=PORTS]
      --clear-endpoint-matchers
      | --remove-endpoint-matchers=[hostname=HOSTNAME],[ports=PORTS]]
    [--upstreams=[egressPolicy=EGRESSPOLICY],
      [external=EXTERNAL],[network=NETWORK],[proxyProtocol=PROXYPROTOCOL]
      | --add-upstreams=[egressPolicy=EGRESSPOLICY],
      [external=EXTERNAL],[network=NETWORK],[proxyProtocol=PROXYPROTOCOL]
      --clear-upstreams
      | --remove-upstreams=[egressPolicy=EGRESSPOLICY],
      [external=EXTERNAL],[network=NETWORK],[proxyProtocol=PROXYPROTOCOL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - Identifier. Name of the resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource. We support only global
     location.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --security-gateway=SECURITY_GATEWAY
     The securityGateway id of the application resource.

     To set the security-gateway attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --security-gateway on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | An arbitrary user-provided name for the application resource. Cannot exceed 64 characters. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request timed out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--schema` | one of: api-gateway Service Discovery API endpoint when Service Discovery is enabled in Gateway |  | Type of the external application. SCHEMA must be one of: api-gateway Service Discovery API endpoint when Service Discovery is enabled in Gateway. proxy-gateway Proxy which routes traffic to actual applications, like Netscaler Gateway. |


**Examples:**
```bash
To update the application, run:

    $ gcloud beyondcorp security-gateways applications update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp/security-gateways/applications/update)

---
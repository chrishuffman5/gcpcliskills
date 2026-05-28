# gcloud compute health-checks

read and manipulate health checks for load balanced instances

### `gcloud compute health-checks delete`

Delete health checks

gcloud compute health-checks delete deletes one or more Compute Engine
health checks.

**Synopsis:**
```
gcloud compute health-checks delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the health checks to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the health checks are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the health checks to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/delete)

---
### `gcloud compute health-checks describe`

Display detailed information about a health check

gcloud compute health-checks describe displays all data associated with a
Google Compute Engine health check in a project.

**Synopsis:**
```
gcloud compute health-checks describe NAME [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the health check to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the health check is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the health check to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/describe)

---
### `gcloud compute health-checks list`

List Google Compute Engine health checks

gcloud compute health-checks list displays all Google Compute Engine health
checks in a project.

**Synopsis:**
```
gcloud compute health-checks list [NAME ...] [--protocol=PROTOCOL]
    [--regexp=REGEXP, -r REGEXP] [--global | --regions=[REGION,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--protocol` | PROTOCOL |  | If protocol is specified, only health checks for that protocol are listed, and protocol-specific columns are added to the output. By default, health checks for all protocols are listed. |
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all health checks in a project in table form, run:

    $ gcloud compute health-checks list

To list the URIs of all health checks in a project, run:

    $ gcloud compute health-checks list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/list)

---

## `gcloud compute health-checks create` — create (non-legacy) health checks for load balanced instances
### `gcloud compute health-checks create grpc`

Create a gRPC health check to monitor load balanced instances

gcloud compute health-checks create grpc is used to create a non-legacy
health check using the gRPC protocol. You can use this health check for
Google Cloud load balancers or for managed instance group autohealing. For
more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create grpc NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--grpc-service-name=GRPC_SERVICE_NAME]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2]
    [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION] [--port=PORT --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the gRPC health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the gRPC health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--grpc-service-name` | GRPC_SERVICE_NAME |  | An optional gRPC service name string of up to 1024 characters to include in the gRPC health check request. Only ASCII characters are allowed. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/grpc)

---
### `gcloud compute health-checks create grpc-with-tls`

Create a gRPC with TLS health check to monitor load balanced instances

gcloud compute health-checks create grpc-with-tls is used to create a
non-legacy health check using the gRPC with TLS protocol. You can use this
health check for Google Cloud load balancers or for managed instance group
autohealing. For more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create grpc-with-tls NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--grpc-service-name=GRPC_SERVICE_NAME]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2]
    [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION] [--port=PORT --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the gRPC with TLS health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the gRPC with TLS health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--grpc-service-name` | GRPC_SERVICE_NAME |  | An optional gRPC service name string of up to 1024 characters to include in the gRPC health check request. Only ASCII characters are allowed. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/grpc-with-tls)

---
### `gcloud compute health-checks create http`

Create a HTTP health check to monitor load balanced instances

gcloud compute health-checks create http is used to create a non-legacy
health check using the HTTP protocol. You can use this health check for
Google Cloud load balancers or for managed instance group autohealing. For
more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create http NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2] [--host=HOST]
    [--proxy-header=PROXY_HEADER; default="NONE"]
    [--request-path=REQUEST_PATH; default="/"] [--response=RESPONSE]
    [--source-regions=REGION,...,[...]] [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION]
    [--port=PORT; default=80 --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the HTTP health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--host` | HOST |  | The value of the host header used for the health check. If unspecified, Google Cloud sets the host header to the IP address of the load balancer's forwarding rule. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request-path` | REQUEST_PATH | / | The request path that this health check monitors. For example, /healthcheck. The default value is ``/''. |
| `--response` | RESPONSE |  | When empty, status code of the response determines health. When not empty, presence of specified string in first 1024 characters of response body determines health. Only ASCII characters allowed. |
| `--source-regions` | REGION,...,[...] |  | Define the list of Google Cloud regions from which health checks are performed. This option is supported only for global health checks that will be referenced by DNS routing policies. If specified, the --check-interval field should be at least 30 seconds. The --proxy-header and --request fields (for TCP health checks) are not supported with this option. If --source-regions is specified for a health check, then that health check cannot be used by a backend service or by a managed instance group (for autohealing). |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/http)

---
### `gcloud compute health-checks create http2`

Create a HTTP2 health check to monitor load balanced instances

gcloud compute health-checks create http2 is used to create a non-legacy
health check using the HTTP/2 protocol. You can use this health check for
Google Cloud load balancers or for managed instance group autohealing. For
more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create http2 NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2] [--host=HOST]
    [--proxy-header=PROXY_HEADER; default="NONE"]
    [--request-path=REQUEST_PATH; default="/"] [--response=RESPONSE]
    [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION]
    [--port=PORT; default=80 --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP2 health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the HTTP2 health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--host` | HOST |  | The value of the host header used for the health check. If unspecified, Google Cloud sets the host header to the IP address of the load balancer's forwarding rule. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request-path` | REQUEST_PATH | / | The request path that this health check monitors. For example, /healthcheck. The default value is ``/''. |
| `--response` | RESPONSE |  | When empty, status code of the response determines health. When not empty, presence of specified string in first 1024 characters of response body determines health. Only ASCII characters allowed. |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


**Examples:**
```bash
To create a HTTP2 health check with default options, run:

    $ gcloud compute health-checks create http2 my-health-check-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/http2)

---
### `gcloud compute health-checks create https`

Create a HTTPS health check to monitor load balanced instances

gcloud compute health-checks create https is used to create a non-legacy
health check using the HTTPS protocol. You can use this health check for
Google Cloud load balancers or for managed instance group autohealing. For
more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create https NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2] [--host=HOST]
    [--proxy-header=PROXY_HEADER; default="NONE"]
    [--request-path=REQUEST_PATH; default="/"] [--response=RESPONSE]
    [--source-regions=REGION,...,[...]] [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION]
    [--port=PORT; default=80 --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTPS health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the HTTPS health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--host` | HOST |  | The value of the host header used for the health check. If unspecified, Google Cloud sets the host header to the IP address of the load balancer's forwarding rule. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request-path` | REQUEST_PATH | / | The request path that this health check monitors. For example, /healthcheck. The default value is ``/''. |
| `--response` | RESPONSE |  | When empty, status code of the response determines health. When not empty, presence of specified string in first 1024 characters of response body determines health. Only ASCII characters allowed. |
| `--source-regions` | REGION,...,[...] |  | Define the list of Google Cloud regions from which health checks are performed. This option is supported only for global health checks that will be referenced by DNS routing policies. If specified, the --check-interval field should be at least 30 seconds. The --proxy-header and --request fields (for TCP health checks) are not supported with this option. If --source-regions is specified for a health check, then that health check cannot be used by a backend service or by a managed instance group (for autohealing). |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/https)

---
### `gcloud compute health-checks create ssl`

Create a SSL health check to monitor load balanced instances

gcloud compute health-checks create ssl is used to create a non-legacy
health check using the SSL protocol. You can use this health check for
Google Cloud load balancers or for managed instance group autohealing. For
more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create ssl NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2]
    [--proxy-header=PROXY_HEADER; default="NONE"] [--request=REQUEST]
    [--response=RESPONSE] [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION]
    [--port=PORT; default=80 --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the SSL health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the SSL health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request` | REQUEST |  | An optional string of up to 1024 characters to send once the health check TCP connection has been established. The health checker then looks for a reply of the string provided in the --response field. If --response is not configured, the health checker does not wait for a response and regards the probe as successful if the TCP or SSL handshake was successful. |
| `--response` | RESPONSE |  | An optional string of up to 1024 characters that the health checker expects to receive from the instance. If the response is not received exactly, the health check probe fails. If --response is configured, but not --request, the health checker will wait for a response anyway. Unless your system automatically sends out a message in response to a successful handshake, only configure --response to match an explicit --request. |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/ssl)

---
### `gcloud compute health-checks create tcp`

Create a TCP health check to monitor load balanced instances

gcloud compute health-checks create tcp is used to create a non-legacy
health check using the TCP protocol. You can use this health check for
Google Cloud load balancers or for managed instance group autohealing. For
more information, see the health checks overview at:
https://cloud.google.com/load-balancing/docs/health-check-concepts

**Synopsis:**
```
gcloud compute health-checks create tcp NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION] [--enable-logging]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2]
    [--proxy-header=PROXY_HEADER; default="NONE"] [--request=REQUEST]
    [--response=RESPONSE] [--source-regions=REGION,...,[...]]
    [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [--global | --region=REGION]
    [--port=PORT; default=80 --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the TCP health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional string description for the TCP health check. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request` | REQUEST |  | An optional string of up to 1024 characters to send once the health check TCP connection has been established. The health checker then looks for a reply of the string provided in the --response field. If --response is not configured, the health checker does not wait for a response and regards the probe as successful if the TCP or SSL handshake was successful. |
| `--response` | RESPONSE |  | An optional string of up to 1024 characters that the health checker expects to receive from the instance. If the response is not received exactly, the health check probe fails. If --response is configured, but not --request, the health checker will wait for a response anyway. Unless your system automatically sends out a message in response to a successful handshake, only configure --response to match an explicit --request. |
| `--source-regions` | REGION,...,[...] |  | Define the list of Google Cloud regions from which health checks are performed. This option is supported only for global health checks that will be referenced by DNS routing policies. If specified, the --check-interval field should be at least 30 seconds. The --proxy-header and --request fields (for TCP health checks) are not supported with this option. If --source-regions is specified for a health check, then that health check cannot be used by a backend service or by a managed instance group (for autohealing). |
| `--timeout` | TIMEOUT | 5s | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/create/tcp)

---

## `gcloud compute health-checks update` — update health checks for load balanced instances
### `gcloud compute health-checks update grpc`

Update a gRPC health check

gcloud compute health-checks update grpc is used to update an existing gRPC
health check. Only arguments passed in will be updated on the health check.
Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update grpc NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--grpc-service-name=GRPC_SERVICE_NAME]
    [--healthy-threshold=HEALTHY_THRESHOLD] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION] [--port=PORT --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the gRPC health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the gRPC health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--grpc-service-name` | GRPC_SERVICE_NAME |  | An optional gRPC service name string of up to 1024 characters to include in the gRPC health check request. Pass in an empty string to unset. Only ASCII characters are allowed. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/grpc)

---
### `gcloud compute health-checks update grpc-with-tls`

Update a gRPC with TLS health check

gcloud compute health-checks update grpc-with-tls is used to update an
existing gRPC with TLS health check. Only arguments passed in will be
updated on the health check. Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update grpc-with-tls NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--grpc-service-name=GRPC_SERVICE_NAME]
    [--healthy-threshold=HEALTHY_THRESHOLD] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION] [--port=PORT --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the gRPC with TLS health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the gRPC with TLS health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--grpc-service-name` | GRPC_SERVICE_NAME |  | An optional gRPC service name string of up to 1024 characters to include in the gRPC health check request. Pass in an empty string to unset. Only ASCII characters are allowed. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/grpc-with-tls)

---
### `gcloud compute health-checks update http`

Update a HTTP health check

gcloud compute health-checks update http is used to update an existing HTTP
health check. Only arguments passed in will be updated on the health check.
Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update http NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--healthy-threshold=HEALTHY_THRESHOLD]
    [--host=HOST] [--proxy-header=PROXY_HEADER]
    [--request-path=REQUEST_PATH] [--response=RESPONSE]
    [--source-regions=REGION,...,[...]] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION]
    [--port=PORT --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the HTTP health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--host` | HOST |  | The value of the host header used in this HTTP health check request. The host header is empty by default. When empty, the health check will set the host header to the IP address of the backend VM or endpoint. You can set the host header to an empty value to return to this default behavior. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request-path` | REQUEST_PATH |  | The request path that this health check monitors. For example, /healthcheck. |
| `--response` | RESPONSE |  | When empty, status code of the response determines health. When not empty, presence of specified string in first 1024 characters of response body determines health. Only ASCII characters allowed. |
| `--source-regions` | REGION,...,[...] |  | Define the list of Google Cloud regions from which health checks are performed. This option is supported only for global health checks that will be referenced by DNS routing policies. If specified, the --check-interval field should be at least 30 seconds. The --proxy-header and --request fields (for TCP health checks) are not supported with this option. If --source-regions is specified for a health check, then that health check cannot be used by a backend service or by a managed instance group (for autohealing). |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |
| `--port, --port` |  |  | _[These flags configure the port that the health check monitors. If both]_ --port=PORT The TCP port number that this health check monitors. --port-name=PORT_NAME The port name that this health check monitors. By default, this is empty. Setting this to an empty string will clear any existing port-name value. --use-serving-port If given, use the "serving port" for health checks: + When health checking network endpoints in a Network Endpoint Group, use the port specified with each endpoint. --use-serving-port must be used when using a Network Endpoint Group as a backend as this flag specifies the portSpecification option for a Health Check object. + When health checking other backends, use the port or named port of the backend service. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/http)

---
### `gcloud compute health-checks update http2`

Update a HTTP2 health check

gcloud compute health-checks update http2 is used to update an existing
HTTP2 health check. Only arguments passed in will be updated on the health
check. Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update http2 NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--healthy-threshold=HEALTHY_THRESHOLD]
    [--host=HOST] [--proxy-header=PROXY_HEADER]
    [--request-path=REQUEST_PATH] [--response=RESPONSE] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION]
    [--port=PORT --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP2 health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the HTTP2 health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--host` | HOST |  | The value of the host header used in this HTTP health check request. The host header is empty by default. When empty, the health check will set the host header to the IP address of the backend VM or endpoint. You can set the host header to an empty value to return to this default behavior. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request-path` | REQUEST_PATH |  | The request path that this health check monitors. For example, /healthcheck. |
| `--response` | RESPONSE |  | When empty, status code of the response determines health. When not empty, presence of specified string in first 1024 characters of response body determines health. Only ASCII characters allowed. |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |
| `--port, --port` |  |  | _[These flags configure the port that the health check monitors. If both]_ --port=PORT The TCP port number that this health check monitors. --port-name=PORT_NAME The port name that this health check monitors. By default, this is empty. Setting this to an empty string will clear any existing port-name value. --use-serving-port If given, use the "serving port" for health checks: + When health checking network endpoints in a Network Endpoint Group, use the port specified with each endpoint. --use-serving-port must be used when using a Network Endpoint Group as a backend as this flag specifies the portSpecification option for a Health Check object. + When health checking other backends, use the port or named port of the backend service. |


**Examples:**
```bash
To update health check interval to 10s, run:

    $ gcloud compute health-checks update http2 my-health-check-name \
        --check-interval=10s
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/http2)

---
### `gcloud compute health-checks update https`

Update a HTTPS health check

gcloud compute health-checks update https is used to update an existing
HTTPS health check. Only arguments passed in will be updated on the health
check. Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update https NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--healthy-threshold=HEALTHY_THRESHOLD]
    [--host=HOST] [--proxy-header=PROXY_HEADER]
    [--request-path=REQUEST_PATH] [--response=RESPONSE]
    [--source-regions=REGION,...,[...]] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION]
    [--port=PORT --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTPS health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the HTTPS health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--host` | HOST |  | The value of the host header used in this HTTP health check request. The host header is empty by default. When empty, the health check will set the host header to the IP address of the backend VM or endpoint. You can set the host header to an empty value to return to this default behavior. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request-path` | REQUEST_PATH |  | The request path that this health check monitors. For example, /healthcheck. |
| `--response` | RESPONSE |  | When empty, status code of the response determines health. When not empty, presence of specified string in first 1024 characters of response body determines health. Only ASCII characters allowed. |
| `--source-regions` | REGION,...,[...] |  | Define the list of Google Cloud regions from which health checks are performed. This option is supported only for global health checks that will be referenced by DNS routing policies. If specified, the --check-interval field should be at least 30 seconds. The --proxy-header and --request fields (for TCP health checks) are not supported with this option. If --source-regions is specified for a health check, then that health check cannot be used by a backend service or by a managed instance group (for autohealing). |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |
| `--port, --port` |  |  | _[These flags configure the port that the health check monitors. If both]_ --port=PORT The TCP port number that this health check monitors. --port-name=PORT_NAME The port name that this health check monitors. By default, this is empty. Setting this to an empty string will clear any existing port-name value. --use-serving-port If given, use the "serving port" for health checks: + When health checking network endpoints in a Network Endpoint Group, use the port specified with each endpoint. --use-serving-port must be used when using a Network Endpoint Group as a backend as this flag specifies the portSpecification option for a Health Check object. + When health checking other backends, use the port or named port of the backend service. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/https)

---
### `gcloud compute health-checks update ssl`

Update a SSL health check

gcloud compute health-checks update ssl is used to update an existing SSL
health check. Only arguments passed in will be updated on the health check.
Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update ssl NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--healthy-threshold=HEALTHY_THRESHOLD]
    [--proxy-header=PROXY_HEADER] [--request=REQUEST] [--response=RESPONSE]
    [--timeout=TIMEOUT] [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION]
    [--port=PORT --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the SSL health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the SSL health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request` | REQUEST |  | An optional string of up to 1024 characters to send once the health check TCP connection has been established. The health checker then looks for a reply of the string provided in the --response field. If --response is not configured, the health checker does not wait for a response and regards the probe as successful if the TCP or SSL handshake was successful. Setting this to an empty string will clear any existing request value. |
| `--response` | RESPONSE |  | An optional string of up to 1024 characters that the health checker expects to receive from the instance. If the response is not received exactly, the health check probe fails. If --response is configured, but not --request, the health checker will wait for a response anyway. Unless your system automatically sends out a message in response to a successful handshake, only configure --response to match an explicit --request. Setting this to an empty string will clear any existing response value. |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |
| `--port, --port` |  |  | _[These flags configure the port that the health check monitors. If both]_ --port=PORT The TCP port number that this health check monitors. --port-name=PORT_NAME The port name that this health check monitors. By default, this is empty. Setting this to an empty string will clear any existing port-name value. --use-serving-port If given, use the "serving port" for health checks: + When health checking network endpoints in a Network Endpoint Group, use the port specified with each endpoint. --use-serving-port must be used when using a Network Endpoint Group as a backend as this flag specifies the portSpecification option for a Health Check object. + When health checking other backends, use the port or named port of the backend service. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/ssl)

---
### `gcloud compute health-checks update tcp`

Update a TCP health check

gcloud compute health-checks update tcp is used to update an existing TCP
health check. Only arguments passed in will be updated on the health check.
Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute health-checks update tcp NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--enable-logging] [--healthy-threshold=HEALTHY_THRESHOLD]
    [--proxy-header=PROXY_HEADER] [--request=REQUEST] [--response=RESPONSE]
    [--source-regions=REGION,...,[...]] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD]
    [--global | --region=REGION]
    [--port=PORT --port-name=PORT_NAME --use-serving-port]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the TCP health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the TCP health check. Pass in an empty string to unset. |
| `--enable-logging` |  |  | Enable logging of health check probe results to Stackdriver. Logging is disabled by default. Use --no-enable-logging to disable logging. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Adds the header "PROXY UNKNOWN\r\n". |
| `--request` | REQUEST |  | An optional string of up to 1024 characters to send once the health check TCP connection has been established. The health checker then looks for a reply of the string provided in the --response field. If --response is not configured, the health checker does not wait for a response and regards the probe as successful if the TCP or SSL handshake was successful. Setting this to an empty string will clear any existing request value. |
| `--response` | RESPONSE |  | An optional string of up to 1024 characters that the health checker expects to receive from the instance. If the response is not received exactly, the health check probe fails. If --response is configured, but not --request, the health checker will wait for a response anyway. Unless your system automatically sends out a message in response to a successful handshake, only configure --response to match an explicit --request. Setting this to an empty string will clear any existing response value. |
| `--source-regions` | REGION,...,[...] |  | Define the list of Google Cloud regions from which health checks are performed. This option is supported only for global health checks that will be referenced by DNS routing policies. If specified, the --check-interval field should be at least 30 seconds. The --proxy-header and --request fields (for TCP health checks) are not supported with this option. If --source-regions is specified for a health check, then that health check cannot be used by a backend service or by a managed instance group (for autohealing). |
| `--timeout` | TIMEOUT |  | If Google Compute Engine doesn't receive a healthy response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |
| `--port, --port` |  |  | _[These flags configure the port that the health check monitors. If both]_ --port=PORT The TCP port number that this health check monitors. --port-name=PORT_NAME The port name that this health check monitors. By default, this is empty. Setting this to an empty string will clear any existing port-name value. --use-serving-port If given, use the "serving port" for health checks: + When health checking network endpoints in a Network Endpoint Group, use the port specified with each endpoint. --use-serving-port must be used when using a Network Endpoint Group as a backend as this flag specifies the portSpecification option for a Health Check object. + When health checking other backends, use the port or named port of the backend service. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/health-checks/update/tcp)

---
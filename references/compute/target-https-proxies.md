# gcloud compute target-https-proxies

list, create, and delete target HTTPS proxies

### `gcloud compute target-https-proxies create`

Create a target HTTPS proxy

gcloud compute target-https-proxies create is used to create target HTTPS
proxies. A target HTTPS proxy is referenced by one or more forwarding rules
which specify the network traffic that the proxy is responsible for
routing. The target HTTPS proxy points to a URL map that defines the rules
for routing the requests. The URL map's job is to map URLs to backend
services which handle the actual requests. The target HTTPS proxy also
points to at most 15 SSL certificates used for server-side authentication.
The target HTTPS proxy can be associated with at most one SSL policy.

**Synopsis:**
```
gcloud compute target-https-proxies create NAME --url-map=URL_MAP
    [--certificate-map=CERTIFICATE_MAP] [--description=DESCRIPTION]
    [--http-keep-alive-timeout-sec=HTTP_KEEP_ALIVE_TIMEOUT_SEC]
    [--quic-override=QUIC_OVERRIDE; default="NONE"]
    [--server-tls-policy=SERVER_TLS_POLICY] [--ssl-policy=SSL_POLICY]
    [--tls-early-data=TLS_EARLY_DATA]
    [--certificate-manager-certificates=[CERTIFICATE_MANAGER_CERTIFICATES,
      ...] | --ssl-certificates=SSL_CERTIFICATE,[...]]
    [--global | --region=REGION]
    [--global-ssl-certificates
      | --ssl-certificates-region=SSL_CERTIFICATES_REGION]
    [--global-ssl-policy | --ssl-policy-region=SSL_POLICY_REGION]
    [--global-url-map | --url-map-region=URL_MAP_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTPS proxy to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--url-map` | URL_MAP |  | A reference to a URL map resource. A URL map defines the mapping of URLs to backend services. Before you can refer to a URL map, you must create the URL map. To delete a URL map that a target proxy is referring to, you must first delete the target HTTPS proxy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate-map` | CERTIFICATE_MAP |  | _[* default value of location is [global].]_ ID of the certificate map or fully qualified identifier for the certificate map. To set the map attribute: + provide the argument --certificate-map on the command line. |
| `--description` | DESCRIPTION |  | _[* default value of location is [global].]_ An optional, textual description for the target HTTPS proxy. |
| `--http-keep-alive-timeout-sec` | HTTP_KEEP_ALIVE_TIMEOUT_SEC |  | _[* default value of location is [global].]_ Represents the maximum amount of time that a TCP connection can be idle between the (downstream) client and the target HTTP proxy. If an HTTP keepalive timeout is not specified, the default value is 610 seconds. For global external Application Load Balancers, the minimum allowed value is 5 seconds and the maximum allowed value is 1200 seconds. |
| `--quic-override` | one of: DISABLE Disallows load balancer to negotiate QUIC with clients | NONE | _[* default value of location is [global].]_ Controls whether load balancer may negotiate QUIC with clients. QUIC is a new transport which reduces latency compared to that of TCP. See https://www.chromium.org/quic for more details. QUIC_OVERRIDE must be one of: DISABLE Disallows load balancer to negotiate QUIC with clients. ENABLE Allows load balancer to negotiate QUIC with clients. NONE Allows Google to control when QUIC is rolled out. |
| `--server-tls-policy` | SERVER_TLS_POLICY |  | _[* default value of location is [global].]_ ID of the server_tls_policy or fully qualified identifier for the server_tls_policy. To set the server_tls_policy attribute: + provide the argument --server-tls-policy on the command line. |
| `--ssl-policy` | SSL_POLICY |  | _[* default value of location is [global].]_ A reference to an SSL policy resource that defines the server-side support for SSL features and affects the connections between clients and load balancers that are using the HTTPS proxy. The SSL policy must exist and cannot be deleted while referenced by a target HTTPS proxy. |
| `--tls-early-data` | one of: DISABLED TLS 1.3 Early Data is not advertised, and any (invalid) attempts to send Early Data will be rejected |  | _[* default value of location is [global].]_ TLS 1.3 Early Data ("0-RTT" or "zero round trip") allows clients to include HTTP request data alongside a TLS handshake. This can improve application performance, especially on networks where connection interruptions may be common, such as on mobile. This applies to both HTTP over TCP (ie: HTTP/1.1 and HTTP/2) and HTTP/3 over QUIC. TLS_EARLY_DATA must be one of: DISABLED TLS 1.3 Early Data is not advertised, and any (invalid) attempts to send Early Data will be rejected. PERMISSIVE Enables TLS 1.3 Early Data for requests with safe HTTP methods (GET, HEAD, OPTIONS, TRACE). This mode does not enforce any other limitations for requests with Early Data. The application owner should validate that Early Data is acceptable for a given request path. STRICT Enables TLS 1.3 Early Data for requests with safe HTTP methods, and HTTP requests that do not have query parameters. Requests that send Early Data containing non-idempotent HTTP methods or with query parameters will be rejected with a HTTP 425. |
| `--ssl-certificates` | SSL_CERTIFICATE,[...] |  | _[command line.]_ References to at most 15 SSL certificate resources that are used for server-side authentication. The first SSL certificate in this list is considered the primary SSL certificate associated with the load balancer. The SSL certificates must exist and cannot be deleted while referenced by a target HTTPS proxy. |
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target HTTPS proxy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target HTTPS proxy to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--global-ssl-certificates` |  |  | _[At most one of these can be specified:]_ If set, the ssl certificates are global. |
| `--ssl-certificates-region` | SSL_CERTIFICATES_REGION |  | _[At most one of these can be specified:]_ Region of the ssl certificates to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--global-ssl-policy` |  |  | _[At most one of these can be specified:]_ If set, the SSL policy is global. |
| `--ssl-policy-region` | SSL_POLICY_REGION |  | _[At most one of these can be specified:]_ Region of the SSL policy to operate on. Overrides the default compute/region property value for this command invocation. |
| `--global-url-map` |  |  | _[At most one of these can be specified:]_ If set, the URL map is global. |
| `--url-map-region` | URL_MAP_REGION |  | _[At most one of these can be specified:]_ Region of the URL map to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
If there is an already-created URL map with the name URL_MAP and a SSL
certificate named SSL_CERTIFICATE, create a global target HTTPS proxy
pointing to this map by running:

    $ gcloud compute target-https-proxies create PROXY_NAME \
        --url-map=URL_MAP --ssl-certificates=SSL_CERTIFICATE

Create a regional target HTTPS proxy by running:

    $ gcloud compute target-https-proxies create PROXY_NAME \
        --url-map=URL_MAP --ssl-certificates=SSL_CERTIFICATE \
        --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/create)

---
### `gcloud compute target-https-proxies delete`

Delete target HTTPS proxies

gcloud compute target-https-proxies delete deletes one or more target HTTPS
proxies.

**Synopsis:**
```
gcloud compute target-https-proxies delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target HTTPS proxies to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target HTTPS proxies are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target HTTPS proxies to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
Delete a global target HTTPS proxy by running:

    $ gcloud compute target-https-proxies delete PROXY_NAME

Delete a regional target HTTPS proxy by running:

    $ gcloud compute target-https-proxies delete PROXY_NAME \
        --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/delete)

---
### `gcloud compute target-https-proxies describe`

Display detailed information about a target HTTPS proxy

gcloud compute target-https-proxies describe displays all data associated
with a target HTTPS proxy in a project.

**Synopsis:**
```
gcloud compute target-https-proxies describe NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTPS proxy to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target HTTPS proxy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target HTTPS proxy to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe a global target HTTPS proxy, run:

    $ gcloud compute target-https-proxies describe PROXY_NAME

To describe a regional target HTTPS proxy, run:

    $ gcloud compute target-https-proxies describe PROXY_NAME \
        --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/describe)

---
### `gcloud compute target-https-proxies export`

Export a target HTTPS proxy

Exports a target HTTPS proxy's configuration to a file. This configuration
can be imported at a later time.

**Synopsis:**
```
gcloud compute target-https-proxies export NAME [--destination=DESTINATION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTPS proxy to export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\TargetHttpsProxy.yaml. |


**Examples:**
```bash
A target HTTPS proxy can be exported by running:

    $ gcloud compute target-https-proxies export NAME \
        --destination=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/export)

---
### `gcloud compute target-https-proxies import`

Import a target HTTPS proxy

Imports a target HTTPS proxy's configuration from a file.

**Synopsis:**
```
gcloud compute target-https-proxies import NAME [--source=SOURCE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTPS proxy to import.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\TargetHttpsProxy.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
A global target HTTPS proxy can be imported by running:

    $ gcloud compute target-https-proxies import NAME \
        --source=<path-to-file>

A regional target HTTPS proxy can be imported by running:

    $ gcloud compute target-https-proxies import NAME \
        --source=<path-to-file> --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/import)

---
### `gcloud compute target-https-proxies list`

List Google Compute Engine target HTTPS proxies

gcloud compute target-https-proxies list displays all Google Compute Engine
target HTTPS proxies in a project.

By default, global target HTTPS proxies and target HTTPS proxies from all
regions are listed. The results can be narrowed down by providing the
--global or --regions flag.

**Synopsis:**
```
gcloud compute target-https-proxies list [NAME ...]
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
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all target HTTPS proxies in a project in table form, run:

    $ gcloud compute target-https-proxies list

To list the URIs of all target HTTPS proxies in a project, run:

    $ gcloud compute target-https-proxies list --uri

To list all global target HTTPS proxies in a project, run:

    $ gcloud compute target-https-proxies list --global

To list all target HTTPS proxies in the us-central1 and europe-west1
regions, given they are regional resources, run:

    $ gcloud compute target-https-proxies list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/list)

---
### `gcloud compute target-https-proxies update`

Update a target HTTPS proxy

gcloud compute target-https-proxies update is used to change the SSL
certificate and/or URL map of existing target HTTPS proxies. A target HTTPS
proxy is referenced by one or more forwarding rules which specify the
network traffic that the proxy is responsible for routing. The target HTTPS
proxy in turn points to a URL map that defines the rules for routing the
requests. The URL map's job is to map URLs to backend services which handle
the actual requests. The target HTTPS proxy also points to at most 15 SSL
certificates used for server-side authentication. The target HTTPS proxy
can be associated with at most one SSL policy.

**Synopsis:**
```
gcloud compute target-https-proxies update NAME
    [--quic-override=QUIC_OVERRIDE] [--tls-early-data=TLS_EARLY_DATA]
    [--url-map=URL_MAP]
    [--certificate-manager-certificates=[CERTIFICATE_MANAGER_CERTIFICATES,
      ...] | --clear-ssl-certificates
      | --ssl-certificates=SSL_CERTIFICATE,[...] --global-ssl-certificates
      | --ssl-certificates-region=SSL_CERTIFICATES_REGION
      | --certificate-map=CERTIFICATE_MAP | --clear-certificate-map]
    [--clear-http-keep-alive-timeout-sec
      | --http-keep-alive-timeout-sec=HTTP_KEEP_ALIVE_TIMEOUT_SEC]
    [--clear-server-tls-policy | --server-tls-policy=SERVER_TLS_POLICY]
    [--clear-ssl-policy | --ssl-policy=SSL_POLICY --global-ssl-policy
      | --ssl-policy-region=SSL_POLICY_REGION] [--global | --region=REGION]
    [--global-url-map | --url-map-region=URL_MAP_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTPS proxy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--quic-override` | one of: DISABLE Disallows load balancer to negotiate QUIC with clients |  | Controls whether load balancer may negotiate QUIC with clients. QUIC is a new transport which reduces latency compared to that of TCP. See https://www.chromium.org/quic for more details. QUIC_OVERRIDE must be one of: DISABLE Disallows load balancer to negotiate QUIC with clients. ENABLE Allows load balancer to negotiate QUIC with clients. NONE Allows Google to control when QUIC is rolled out. |
| `--tls-early-data` | one of: DISABLED TLS 1.3 Early Data is not advertised, and any (invalid) attempts to send Early Data will be rejected |  | TLS 1.3 Early Data ("0-RTT" or "zero round trip") allows clients to include HTTP request data alongside a TLS handshake. This can improve application performance, especially on networks where connection interruptions may be common, such as on mobile. This applies to both HTTP over TCP (ie: HTTP/1.1 and HTTP/2) and HTTP/3 over QUIC. TLS_EARLY_DATA must be one of: DISABLED TLS 1.3 Early Data is not advertised, and any (invalid) attempts to send Early Data will be rejected. PERMISSIVE Enables TLS 1.3 Early Data for requests with safe HTTP methods (GET, HEAD, OPTIONS, TRACE). This mode does not enforce any other limitations for requests with Early Data. The application owner should validate that Early Data is acceptable for a given request path. STRICT Enables TLS 1.3 Early Data for requests with safe HTTP methods, and HTTP requests that do not have query parameters. Requests that send Early Data containing non-idempotent HTTP methods or with query parameters will be rejected with a HTTP 425. |
| `--url-map` | URL_MAP |  | A reference to a URL map resource. A URL map defines the mapping of URLs to backend services. Before you can refer to a URL map, you must create the URL map. To delete a URL map that a target proxy is referring to, you must first delete the target HTTPS proxy. |


**Examples:**
```bash
Update the URL map of a global target HTTPS proxy by running:

    $ gcloud compute target-https-proxies update PROXY_NAME \
        --url-map=URL_MAP

Update the SSL certificate of a global target HTTPS proxy by running:

    $ gcloud compute target-https-proxies update PROXY_NAME \
        --ssl-certificates=SSL_CERTIFIFCATE

Update the URL map of a global target HTTPS proxy by running:

    $ gcloud compute target-https-proxies update PROXY_NAME \
        --url-map=URL_MAP --region=REGION_NAME

Update the SSL certificate of a global target HTTPS proxy by running:

    $ gcloud compute target-https-proxies update PROXY_NAME \
        --ssl-certificates=SSL_CERTIFIFCATE --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-https-proxies/update)

---
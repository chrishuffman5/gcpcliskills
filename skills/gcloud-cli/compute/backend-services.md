# gcloud compute backend-services

list, create, and delete backend services

### `gcloud compute backend-services add-backend`

Add a backend to a backend service

gcloud compute backend-services add-backend adds a backend to a Google
Cloud load balancer or Traffic Director. Depending on the load balancing
scheme of the backend service, backends can be instance groups (managed or
unmanaged), zonal network endpoint groups (zonal NEGs), serverless NEGs, or
an internet NEG. For more information, see the backend services overview
(https://cloud.google.com/load-balancing/docs/backend-service).

For most load balancers, you can define how Google Cloud measures capacity
by selecting a balancing mode. For more information, see traffic
distribution
(https://cloud.google.com/load-balancing/docs/backend-service#traffic_distribution).

To modify a backend, use the gcloud compute backend-services update-backend
or gcloud compute backend-services edit command.

**Synopsis:**
```
gcloud compute backend-services add-backend BACKEND_SERVICE_NAME
    ([--instance-group=INSTANCE_GROUP
      : --instance-group-region=INSTANCE_GROUP_REGION
      | --instance-group-zone=INSTANCE_GROUP_ZONE]
      | [--network-endpoint-group=NETWORK_ENDPOINT_GROUP
      : --global-network-endpoint-group
      | --network-endpoint-group-region=NETWORK_ENDPOINT_GROUP_REGION
      | --network-endpoint-group-zone=NETWORK_ENDPOINT_GROUP_ZONE])
    [--balancing-mode=BALANCING_MODE] [--capacity-scaler=CAPACITY_SCALER]
    [--description=DESCRIPTION] [--failover]
    [--max-utilization=MAX_UTILIZATION] [--preference=PREFERENCE]
    [--custom-metrics=[CUSTOM_METRICS,...]
      | --custom-metrics-file=[CUSTOM_METRICS,...]]
    [--global | --region=REGION]
    [--max-connections=MAX_CONNECTIONS
      | --max-connections-per-endpoint=MAX_CONNECTIONS_PER_ENDPOINT
      | --max-connections-per-instance=MAX_CONNECTIONS_PER_INSTANCE
      | --max-rate=MAX_RATE | --max-rate-per-endpoint=MAX_RATE_PER_ENDPOINT
      | --max-rate-per-instance=MAX_RATE_PER_INSTANCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-group` | INSTANCE_GROUP |  | _[Instance Group]_ Name of the instance group to add to the backend service. For details on valid instance names, refer to the criteria documented under the field 'name' at: https://cloud.google.com/compute/docs/reference/rest/v1/instances This flag argument must be specified if any of the other arguments in this group are specified. |
| `--network-endpoint-group` | NETWORK_ENDPOINT_GROUP |  | _[Network Endpoint Group]_ Name of the network endpoint group to add to the backend service. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--balancing-mode` | one of: CONNECTION Available if the backend service's load balancing scheme is either INTERNAL or EXTERNAL |  | Defines how to measure whether a backend can handle additional traffic or is fully loaded. For more information, see https://cloud.google.com/load-balancing/docs/backend-service#balancing-mode. This cannot be used when the endpoint type of an attached network endpoint group is INTERNET_IP_PORT, INTERNET_FQDN_PORT, or SERVERLESS. BALANCING_MODE must be one of: CONNECTION Available if the backend service's load balancing scheme is either INTERNAL or EXTERNAL. Available if the backend service's protocol is one of SSL, TCP, or UDP. Spreads load based on how many concurrent connections the backend can handle. For backend services with --load-balancing-scheme EXTERNAL, you must specify exactly one of these additional parameters: --max-connections, --max-connections-per-instance, or --max-connections-per-endpoint. For backend services where --load-balancing-scheme is INTERNAL, you must omit all of these parameters. CUSTOM_METRICS Spreads load based on custom defined and reported metrics. RATE Available if the backend service's load balancing scheme is INTERNAL_MANAGED, INTERNAL_SELF_MANAGED, or EXTERNAL. Available if the backend service's protocol is one of HTTP, HTTPS, or HTTP/2. Spreads load based on how many HTTP requests per second (RPS) the backend can handle. You must specify exactly one of these additional parameters: --max-rate, --max-rate-per-instance, or --max-rate-per-endpoint. UTILIZATION Available if the backend service's load balancing scheme is INTERNAL_MANAGED, INTERNAL_SELF_MANAGED, or EXTERNAL. Available only for managed or unmanaged instance group backends. Spreads load based on the backend utilization of instances in a backend instance group. The following additional parameters may be specified: --max-utilization, --max-rate, --max-rate-per-instance, --max-connections, --max-connections-per-instance. For valid combinations, see --max-utilization. |
| `--capacity-scaler` | CAPACITY_SCALER |  | Scales down the target capacity (max utilization, max rate, or max connections) without changing the target capacity. For usage guidelines and examples, see Capacity scaler (https://cloud.google.com/load-balancing/docs/backend-service#capacity_scaler). This cannot be used when the endpoint type of an attached network endpoint group is INTERNET_IP_PORT, INTERNET_FQDN_PORT, or SERVERLESS. |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--failover` |  |  | Designates whether this is a failover backend. More than one failover backend can be configured for a given BackendService. Not compatible with the --global flag |
| `--max-utilization` | MAX_UTILIZATION |  | Defines the maximum target for average utilization of the backend instance group. Supported values are 0.0 (0%) through 1.0 (100%). This is an optional parameter for the UTILIZATION balancing mode. You can use this parameter with other parameters for defining target capacity. For usage guidelines, see Balancing mode combinations (https://cloud.google.com/load-balancing/docs/backend-service#balancing-mode-combos). |
| `--preference` | one of: DEFAULT This is the default setting |  | This parameter specifies whether a backend should be fully utilized before sending traffic to backends with the default preference. This parameter cannot be used with regional managed instance groups and when the endpoint type of an attached network endpoint group is INTERNET_IP_PORT, INTERNET_FQDN_PORT, or SERVERLESS. PREFERENCE must be one of: DEFAULT This is the default setting. If the designated preferred backends don't have enough capacity, backends in the default category are used. Traffic is distributed between default backends based on the load balancing algorithm used. PREFERRED Backends with this preference setting are used up to their capacity limits first, while optimizing overall network latency. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/add-backend)

---
### `gcloud compute backend-services add-iam-policy-binding`

Add an IAM policy binding to a Compute Engine backend service

Add an IAM policy binding to a Compute Engine backend service.

**Synopsis:**
```
gcloud compute backend-services add-iam-policy-binding BACKEND_SERVICE_NAME
    --member=PRINCIPAL --role=ROLE [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To add an IAM policy binding for the role of
'compute.loadBalancerServiceUser' for the user 'test-user@gmail.com' with
backend service 'my-backend-service' and region 'REGION', run:

    $ gcloud compute backend-services add-iam-policy-binding \
      my-backend-service --region=REGION \
      --member='user:test-user@gmail.com' \
      --role='roles/compute.loadBalancerServiceUser'

    $ gcloud compute backend-services add-iam-policy-binding \
      my-backend-service --global \
      --member='user:test-user@gmail.com' \
      --role='roles/compute.loadBalancerServiceUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/add-iam-policy-binding)

---
### `gcloud compute backend-services add-service-bindings`

Add service bindings to a backend service

Add service bindings to a backend service.

**Synopsis:**
```
gcloud compute backend-services add-service-bindings BACKEND_SERVICE_NAME
    --service-bindings=SERVICE_BINDING,[...] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-bindings` | SERVICE_BINDING,[...] |  | List of service binding names to be added to the backend service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To add a service binding to a backend service, run:

    $ gcloud compute backend-services add-service-bindings NAME \
        --service-bindings=SERVICE_BINDING1 --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/add-service-bindings)

---
### `gcloud compute backend-services add-signed-url-key`

Add Cloud CDN Signed URL key to a backend service

gcloud compute backend-services add-signed-url-key is used to add a new
Cloud CDN Signed URL key to a backend service.

Cloud CDN Signed URLs give you a way to serve responses from the globally
distributed CDN cache, even if the request needs to be authorized.

Signed URLs are a mechanism to temporarily give a client access to a
private resource without requiring additional authorization. To achieve
this, the full request URL that should be allowed is hashed and
cryptographically signed. By using the signed URL you give it, that one
request will be considered authorized to receive the requested content.

Generally, a signed URL can be used by anyone who has it. However, it is
usually only intended to be used by the client that was directly given the
URL. To mitigate this, they expire at a time chosen by the issuer. To
minimize the risk of a signed URL being shared, it is recommended that the
signed URL be set to expire as soon as possible.

A 128-bit secret key is used for signing the URLs.

**Synopsis:**
```
gcloud compute backend-services add-signed-url-key BACKEND_SERVICE_NAME
    --key-file=LOCAL_FILE_PATH --key-name=KEY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-file` | LOCAL_FILE_PATH |  | The file containing the RFC 4648 Section 5 base64url encoded 128-bit secret key for Cloud CDN Signed URL. It is vital that the key is strongly random. One way to generate such a key is with the following command: head -c 16 /dev/random \| base64 \| tr +/ -_ > [KEY_FILE_NAME] |
| `--key-name` | KEY_NAME |  | Name of the Cloud CDN Signed URL key. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/add-signed-url-key)

---
### `gcloud compute backend-services create`

Create a backend service

gcloud compute backend-services create creates a backend service for a
Google Cloud load balancer or Traffic Director. A backend service defines
how to distribute traffic to backends. Depending on the load balancing
scheme of the backend service, backends can be instance groups (managed or
unmanaged), zonal network endpoint groups (zonal NEGs), serverless NEGs, or
an internet NEG. For more information, see the backend services overview
(https://cloud.google.com/load-balancing/docs/backend-service).

After you create a backend service, you add backends by using gcloud
compute backend-services add-backend or gcloud compute backend-services
edit.

**Synopsis:**
```
gcloud compute backend-services create BACKEND_SERVICE_NAME
    [--affinity-cookie-name=AFFINITY_COOKIE_NAME]
    [--affinity-cookie-path=AFFINITY_COOKIE_PATH]
    [--affinity-cookie-ttl=AFFINITY_COOKIE_TTL]
    [--bypass-cache-on-request-headers=BYPASS_CACHE_ON_REQUEST_HEADERS]
    [--no-cache-key-include-host]
    [--cache-key-include-http-header=[HEADER_FIELD_NAME,...]]
    [--cache-key-include-named-cookie=[NAMED_COOKIE,...]]
    [--no-cache-key-include-protocol] [--no-cache-key-include-query-string]
    [--cache-mode=CACHE_MODE] [--client-ttl=CLIENT_TTL]
    [--compression-mode=COMPRESSION_MODE] [--connection-drain-on-failover]
    [--connection-draining-timeout=CONNECTION_DRAINING_TIMEOUT]
    [--connection-persistence-on-unhealthy-backends=CONNECTION_PERSISTENCE_ON_UNHEALTHY_BACKENDS]
    [--custom-request-header=CUSTOM_REQUEST_HEADER]
    [--custom-response-header=CUSTOM_RESPONSE_HEADER]
    [--default-ttl=DEFAULT_TTL] [--description=DESCRIPTION]
    [--drop-traffic-if-unhealthy] [--[no-]enable-cdn]
    [--[no-]enable-logging] [--[no-]enable-strong-affinity]
    [--failover-ratio=FAILOVER_RATIO] [--health-checks=HEALTH_CHECK,[...]]
    [--http-health-checks=HTTP_HEALTH_CHECK,[...]]
    [--https-health-checks=HTTPS_HEALTH_CHECK,[...]]
    [--iap=disabled|enabled,[oauth2-client-id=OAUTH2-CLIENT-ID,
      oauth2-client-secret=OAUTH2-CLIENT-SECRET]]
    [--idle-timeout-sec=IDLE_TIMEOUT_SEC]
    [--ip-address-selection-policy=IP_ADDRESS_SELECTION_POLICY]
    [--load-balancing-scheme=LOAD_BALANCING_SCHEME; default="EXTERNAL"]
    [--locality-lb-policy=LOCALITY_LB_POLICY]
    [--logging-optional=LOGGING_OPTIONAL]
    [--logging-optional-fields=[LOGGING_OPTIONAL_FIELDS,...]]
    [--logging-sample-rate=LOGGING_SAMPLE_RATE] [--max-ttl=MAX_TTL]
    [--[no-]negative-caching] [--negative-caching-policy=[[CODE=TTL],...]]
    [--network=NETWORK] [--port-name=PORT_NAME] [--protocol=PROTOCOL]
    [--[no-]request-coalescing] [--resource-manager-tags=[KEY=VALUE,...]]
    [--serve-while-stale=SERVE_WHILE_STALE]
    [--service-bindings=SERVICE_BINDING,[...]]
    [--service-lb-policy=SERVICE_LOAD_BALANCING_POLICY]
    [--session-affinity=SESSION_AFFINITY]
    [--signed-url-cache-max-age=SIGNED_URL_CACHE_MAX_AGE]
    [--subsetting-policy=SUBSETTING_POLICY; default="NONE"]
    [--timeout=TIMEOUT; default="30s"]
    [--tls-settings=[authenticationConfig=AUTHENTICATIONCONFIG],[sni=SNI]]
    [--tracking-mode=TRACKING_MODE]
    [--cache-key-query-string-blacklist=[QUERY_STRING,...]
      | --cache-key-query-string-whitelist=QUERY_STRING,[...]]
    [--custom-metrics=[CUSTOM_METRICS,...]
      | --custom-metrics-file=[CUSTOM_METRICS,...]]
    [--global | --region=REGION]
    [--global-health-checks | --health-checks-region=HEALTH_CHECKS_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--affinity-cookie-name` | AFFINITY_COOKIE_NAME |  | If --session-affinity is set to HTTP_COOKIE or STRONG_COOKIE_AFFINITY, this flag sets the name of the cookie. |
| `--affinity-cookie-path` | AFFINITY_COOKIE_PATH |  | If --session-affinity is set to HTTP_COOKIE or STRONG_COOKIE_AFFINITY, this flag sets the path of the cookie. |
| `--affinity-cookie-ttl` | AFFINITY_COOKIE_TTL |  | If --session-affinity is set to GENERATED_COOKIE, HTTP_COOKIE, or STRONG_COOKIE_AFFINITY, this flag sets the TTL, in seconds, of the resulting cookie. A setting of 0 indicates that the cookie should be a session cookie. See $ gcloud topic datetimes for information on duration formats. |
| `--bypass-cache-on-request-headers` | BYPASS_CACHE_ON_REQUEST_HEADERS |  | Bypass the cache when the specified request headers are matched - e.g. Pragma or Authorization headers. Up to 5 headers can be specified. The cache is bypassed for all cdnPolicy.cacheMode settings. Note that requests that include these headers will always fill from origin, and may result in a large number of cache misses if the specified headers are common to many requests. Values are case-insensitive. The header name must be a valid HTTP header field token (per RFC 7230). For the list of restricted headers, see the list of required header name properties in How custom headers work (https://cloud.google.com/load-balancing/docs/custom-headers#how_custom_headers_work). A header name must not appear more than once in the list of added headers. |
| `--cache-key-include-host` |  |  | Enable including host in cache key. If enabled, requests to different hosts will be cached separately. Can only be applied for global resources. Enabled by default, use --no-cache-key-include-host to disable. |
| `--cache-key-include-http-header` | [HEADER_FIELD_NAME,...] |  | Specifies a comma-separated list of HTTP headers, by field name, to include in cache keys. Only the request URL is included in the cache key by default. |
| `--cache-key-include-named-cookie` | [NAMED_COOKIE,...] |  | Specifies a comma-separated list of HTTP cookie names to include in cache keys. The name=value pair are used in the cache key Cloud CDN generates. Cookies are not included in cache keys by default. |
| `--cache-key-include-protocol` |  |  | Enable including protocol in cache key. If enabled, http and https requests will be cached separately. Can only be applied for global resources. Enabled by default, use --no-cache-key-include-protocol to disable. |
| `--cache-key-include-query-string` |  |  | Enable including query string in cache key. If enabled, the query string parameters will be included according to --cache-key-query-string-whitelist and --cache-key-query-string-blacklist. If neither is set, the entire query string will be included. If disabled, then the entire query string will be excluded. Can only be applied for global resources. Enabled by default, use --no-cache-key-include-query-string to disable. |
| `--cache-mode` | one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS) |  | Specifies the cache setting for all responses from this backend. CACHE_MODE must be one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS). Requests and responses that are marked as uncacheable, as well as dynamic content (including HTML), aren't cached. FORCE_CACHE_ALL Cache all content, ignoring any "private", "no-store" or "no-cache" directives in Cache-Control response headers. Warning: this may result in Cloud CDN caching private, per-user (user identifiable) content. You should only enable this on backends that are not serving private or dynamic content, such as storage buckets. USE_ORIGIN_HEADERS Require the origin to set valid caching headers to cache content. Responses without these headers aren't cached at Google's edge, and require a full trip to the origin on every request, potentially impacting performance and increasing load on the origin server. |
| `--client-ttl` | CLIENT_TTL |  | Specifies a separate client (for example, browser client) TTL, separate from the TTL for Cloud CDN's edge caches. This allows you to set a shorter TTL for browsers/clients, and to have those clients revalidate content against Cloud CDN on a more regular basis, without requiring revalidation at the origin. The value of clientTtl cannot be set to a value greater than that of maxTtl, but can be equal. Any cacheable response has its max-age/s-maxage directives adjusted down to the client TTL value if necessary; an Expires header will be replaced with a suitable max-age directive. The maximum allowed value is 31,622,400s (1 year). When creating a new backend with CACHE_ALL_STATIC and the field is unset, or when switching to that mode and the field is unset, a default value of 3600 is used. When the cache mode is set to "USE_ORIGIN_HEADERS", you must omit this field. |
| `--compression-mode` | one of: DISABLED, AUTOMATIC |  | Compress text responses using Brotli or gzip compression, based on the client's Accept-Encoding header. Two modes are supported: AUTOMATIC (recommended) - automatically uses the best compression based on the Accept-Encoding header sent by the client. In most cases, this will result in Brotli compression being favored. DISABLED - disables compression. Existing compressed responses cached by Cloud CDN will not be served to clients. COMPRESSION_MODE must be one of: DISABLED, AUTOMATIC. |
| `--connection-drain-on-failover` |  |  | Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. Only applicable when the backend service protocol is TCP. Not applicable to any other load balancer. Enabled by default, this option instructs the load balancer to allow established TCP connections to persist for up to 300 seconds on instances or endpoints in primary backends during failover, and on instances or endpoints in failover backends during failback. For details, see: Connection draining on failover and failback for internal passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/internal/failover-overview#connection_draining) and Connection draining on failover and failback for external passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/network/networklb-failover-overview#connection_draining). |
| `--connection-draining-timeout` | CONNECTION_DRAINING_TIMEOUT |  | Connection draining timeout to be used during removal of VMs from instance groups. This guarantees that for the specified time all existing connections to a VM will remain untouched, but no new connections will be accepted. Set timeout to zero to disable connection draining. Enable feature by specifying a timeout of up to one hour. If the flag is omitted API default value (0s) will be used. See $ gcloud topic datetimes for information on duration formats. |
| `--connection-persistence-on-unhealthy-backends` | one of: DEFAULT_FOR_PROTOCOL, NEVER_PERSIST, ALWAYS_PERSIST |  | Specifies connection persistence when backends are unhealthy. The default value is DEFAULT_FOR_PROTOCOL. CONNECTION_PERSISTENCE_ON_UNHEALTHY_BACKENDS must be one of: DEFAULT_FOR_PROTOCOL, NEVER_PERSIST, ALWAYS_PERSIST. |
| `--custom-request-header` | CUSTOM_REQUEST_HEADER |  | Specifies a HTTP Header to be added by your load balancer. This flag can be repeated to specify multiple headers. For example: $ gcloud compute backend-services create NAME \ --custom-request-header "header-name: value" \ --custom-request-header "another-header:" |
| `--custom-response-header` | CUSTOM_RESPONSE_HEADER |  | Custom headers that the external Application Load Balancer adds to proxied responses. For the list of headers, see Creating custom headers (https://cloud.google.com/load-balancing/docs/custom-headers). Variables are not case-sensitive. |
| `--default-ttl` | DEFAULT_TTL |  | Specifies the default TTL for cached content served by this origin for responses that do not have an existing valid TTL (max-age or s-maxage). The default value is 3600s for cache modes that allow a default TTL to be defined. The value of defaultTtl cannot be set to a value greater than that of maxTtl, but can be equal. When the cacheMode is set to FORCE_CACHE_ALL, the defaultTtl overwrites the TTL set in all responses. A TTL of "0" means Always revalidate. The maximum allowed value is 31,622,400s (1 year). Infrequently accessed objects may be evicted from the cache before the defined TTL. When creating a new backend with CACHE_ALL_STATIC or FORCE_CACHE_ALL and the field is unset, or when updating an existing backend to use these modes and the field is unset, a default value of 3600 is used. When the cache mode is set to "USE_ORIGIN_HEADERS", you must omit this field. |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend service. |
| `--drop-traffic-if-unhealthy` |  |  | Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. Not applicable to any other load balancer. This option instructs the load balancer to drop packets when all instances or endpoints in primary and failover backends do not pass their load balancer health checks. For details, see: Dropping traffic when all backend VMs are unhealthy for internal passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/internal/failover-overview#drop_traffic) and Dropping traffic when all backend VMs are unhealthy for external passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/network/networklb-failover-overview#drop_traffic). |
| `--[no-]enable-cdn` |  |  | Enable or disable Cloud CDN for the backend service. Only available for backend services with --load-balancing-scheme=EXTERNAL or EXTERNAL_MANAGED that use a --protocol of HTTP, HTTPS, HTTP2 or H2C. Cloud CDN caches HTTP responses at the edge of Google's network. Cloud CDN is disabled by default. Use --enable-cdn to enable and --no-enable-cdn to disable. |
| `--[no-]enable-logging` |  |  | The logging options for the load balancer traffic served by this backend service. If logging is enabled, logs will be exported to Cloud Logging. Disabled by default. This field cannot be specified for global external proxy Network Load Balancers. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--[no-]enable-strong-affinity` |  |  | Enable or disable strong session affinity. This is only available for loadbalancingScheme EXTERNAL. Use --enable-strong-affinity to enable and --no-enable-strong-affinity to disable. |
| `--failover-ratio` | FAILOVER_RATIO |  | Applicable only to backend service-based external passthrough Network load balancers and internal passthrough Network load balancers as part of a failover policy. Not applicable to any other load balancer. This option defines the ratio used to control when failover and failback occur. For details, see: Failover ratio for internal passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/internal/failover-overview#failover_ratio) and Failover ratio for external passthrough Network Load Balancer overview (https://cloud.google.com/load-balancing/docs/network/networklb-failover-overview#failover_ratio). |
| `--health-checks` | HEALTH_CHECK,[...] |  | Specifies a list of health check objects for checking the health of the backend service. Currently at most one health check can be specified. Health checks need not be for the same protocol as that of the backend service. |
| `--http-health-checks` | HTTP_HEALTH_CHECK,[...] |  | Specifies a list of legacy HTTP health check objects for checking the health of the backend service. Legacy health checks are not recommended for backend services. It is possible to use a legacy health check on a backend service for an Application Load Balancer if that backend service uses instance groups. For more information, refer to this guide: https://cloud.google.com/load-balancing/docs/health-check-concepts#lb_guide. |
| `--https-health-checks` | HTTPS_HEALTH_CHECK,[...] |  | Specifies a list of legacy HTTPS health check objects for checking the health of the backend service. Legacy health checks are not recommended for backend services. It is possible to use a legacy health check on a backend service for an Application Load Balancer if that backend service uses instance groups. For more information, refer to this guide: https://cloud.google.com/load-balancing/docs/health-check-concepts#lb_guide. |
| `--iap` | disabled\|enabled,[oauth2-client-id=OAUTH2-CLIENT-ID,oauth2-client-secret=OAUTH2-CLIENT-SECRET] |  | Configure Identity Aware Proxy (IAP) for external HTTP(S) load balancing. You can configure IAP to be enabled or disabled (default). If enabled, you can provide values for oauth2-client-id and oauth2-client-secret. For example, --iap=enabled,oauth2-client-id=foo,oauth2-client-secret=bar turns IAP on, and --iap=disabled turns it off. For more information, see https://cloud.google.com/iap/. |
| `--idle-timeout-sec` | IDLE_TIMEOUT_SEC |  | Specifies how long to keep a connection tracking table entry while there is no matching traffic (in seconds). Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. |
| `--ip-address-selection-policy` | one of: IPV4_ONLY, PREFER_IPV6, IPV6_ONLY |  | Specifies a preference for traffic sent from the proxy to the backend (or from the client to the backend for proxyless gRPC). Can only be set if load balancing scheme is INTERNAL_SELF_MANAGED, INTERNAL_MANAGED or EXTERNAL_MANAGED. The possible values are: IPV4_ONLY Only send IPv4 traffic to the backends of the backend service, regardless of traffic from the client to the proxy. Only IPv4 health checks are used to check the health of the backends. PREFER_IPV6 Prioritize the connection to the endpoint's IPv6 address over its IPv4 address (provided there is a healthy IPv6 address). IPV6_ONLY Only send IPv6 traffic to the backends of the backend service, regardless of traffic from the client to the proxy. Only IPv6 health checks are used to check the health of the backends. IP_ADDRESS_SELECTION_POLICY must be one of: IPV4_ONLY, PREFER_IPV6, IPV6_ONLY. |
| `--load-balancing-scheme` | one of: INTERNAL, EXTERNAL, INTERNAL_SELF_MANAGED, EXTERNAL_MANAGED, INTERNAL_MANAGED | EXTERNAL | Specifies the load balancer type. Choose EXTERNAL for the classic Application Load Balancers, the external passthrough Network Load Balancers, and the global external proxy Network Load Balancers. Choose EXTERNAL_MANAGED for the Envoy-based global and regional external Application Load Balancers, and the regional external proxy Network Load Balancers. Choose INTERNAL for the internal passthrough Network Load Balancers. Choose INTERNAL_MANAGED for Envoy-based internal load balancers such as the internal Application Load Balancers and the internal proxy Network Load Balancers. Choose INTERNAL_SELF_MANAGED for Traffic Director. For more information, refer to this guide: https://cloud.google.com/load-balancing/docs/choosing-load-balancer. LOAD_BALANCING_SCHEME must be one of: INTERNAL, EXTERNAL, INTERNAL_SELF_MANAGED, EXTERNAL_MANAGED, INTERNAL_MANAGED. |
| `--locality-lb-policy` | one of: INVALID_LB_POLICY, ROUND_ROBIN, LEAST_REQUEST, RING_HASH, RANDOM, ORIGINAL_DESTINATION, MAGLEV, WEIGHTED_MAGLEV, WEIGHTED_ROUND_ROBIN, WEIGHTED_GCP_RENDEZVOUS |  | The load balancing algorithm used within the scope of the locality. LOCALITY_LB_POLICY must be one of: INVALID_LB_POLICY, ROUND_ROBIN, LEAST_REQUEST, RING_HASH, RANDOM, ORIGINAL_DESTINATION, MAGLEV, WEIGHTED_MAGLEV, WEIGHTED_ROUND_ROBIN, WEIGHTED_GCP_RENDEZVOUS. |
| `--logging-optional` | one of: EXCLUDE_ALL_OPTIONAL, INCLUDE_ALL_OPTIONAL, CUSTOM |  | This field can only be specified if logging is enabled for the backend service. Configures whether all, none, or a subset of optional fields should be added to the reported logs. Default is EXCLUDE_ALL_OPTIONAL. This field can only be specified for internal and external passthrough Network Load Balancers. LOGGING_OPTIONAL must be one of: EXCLUDE_ALL_OPTIONAL, INCLUDE_ALL_OPTIONAL, CUSTOM. |
| `--logging-optional-fields` | [LOGGING_OPTIONAL_FIELDS,...] |  | This field can only be specified if logging is enabled for the backend service and "--logging-optional" was set to CUSTOM. Contains a comma-separated list of optional fields you want to include in the logs. For example: serverInstance, serverGkeDetails.cluster, serverGkeDetails.pod.podNamespace. This can only be specified for internal and external passthrough Network Load Balancers. |
| `--logging-sample-rate` | LOGGING_SAMPLE_RATE |  | This field can only be specified if logging is enabled for the backend service. The value of the field must be a float in the range [0, 1]. This configures the sampling rate of requests to the load balancer where 1.0 means all logged requests are reported and 0.0 means no logged requests are reported. The default value is 1.0 when logging is enabled and 0.0 otherwise. |
| `--max-ttl` | MAX_TTL |  | Specifies the maximum allowed TTL for cached content served by this origin. The default value is 86400 for cache modes that support a max TTL. Cache directives that attempt to set a max-age or s-maxage higher than this, or an Expires header more than maxTtl seconds in the future, are capped at the value of maxTtl, as if it were the value of an s-maxage Cache-Control directive. A TTL of "0" means Always revalidate. The maximum allowed value is 31,622,400s (1 year). Infrequently accessed objects may be evicted from the cache before the defined TTL. When creating a new backend with CACHE_ALL_STATIC and the field is unset, or when updating an existing backend to use these modes and the field is unset, a default value of 86400 is used. When the cache mode is set to "USE_ORIGIN_HEADERS" or "FORCE_CACHE_ALL", you must omit this field. |
| `--[no-]negative-caching` |  |  | Negative caching allows per-status code cache TTLs to be set, in order to apply fine-grained caching for common errors or redirects. This can reduce the load on your origin and improve the end-user experience by reducing response latency. Negative caching applies to a set of 3xx, 4xx, and 5xx status codes that are typically useful to cache. Status codes not listed here cannot have their TTL explicitly set and aren't cached, in order to avoid cache poisoning attacks. HTTP success codes (HTTP 2xx) are handled by the values of defaultTtl and maxTtl. When the cache mode is set to CACHE_ALL_STATIC or USE_ORIGIN_HEADERS, these values apply to responses with the specified response code that lack any cache-control or expires headers. When the cache mode is set to FORCE_CACHE_ALL, these values apply to all responses with the specified response code, and override any caching headers. Cloud CDN applies the following default TTLs to these status codes: * HTTP 300 (Multiple Choice), 301, 308 (Permanent Redirects): 10m * HTTP 404 (Not Found), 410 (Gone), 451 (Unavailable For Legal Reasons): 120s * HTTP 405 (Method Not Found), 421 (Misdirected Request), 501 (Not Implemented): 60s These defaults can be overridden in cdnPolicy.negativeCachingPolicy. Use --negative-caching to enable and --no-negative-caching to disable. |
| `--negative-caching-policy` | [[CODE=TTL],...] |  | Sets a cache TTL for the specified HTTP status code. NegativeCaching must be enabled to config the negativeCachingPolicy. If you omit the policy and leave negativeCaching enabled, Cloud CDN's default cache TTLs are used. Note that when specifying an explicit negative caching policy, make sure that you specify a cache TTL for all response codes that you want to cache. Cloud CDN doesn't apply any default negative caching when a policy exists. CODE is the HTTP status code to define a TTL against. Only HTTP status codes 300, 301, 308, 404, 405, 410, 421, 451, and 501 can be specified as values, and you cannot specify a status code more than once. TTL is the time to live (in seconds) for which to cache responses for the specified CODE. The maximum allowed value is 1800s (30 minutes), noting that infrequently accessed objects may be evicted from the cache before the defined TTL. |
| `--network` | NETWORK |  | Network that this backend service applies to. It can only be set if the load-balancing-scheme is INTERNAL. |
| `--port-name` | PORT_NAME |  | Backend services for Application Load Balancers and proxy Network Load Balancers must reference exactly one named port if using instance group backends. Each instance group backend exports one or more named ports, which map a user-configurable name to a port number. The backend service's named port subscribes to one named port on each instance group. The resolved port number can differ among instance group backends, based on each instance group's named port list. When omitted, a backend service subscribes to a named port called http. The named port for a backend service is either ignored or cannot be set for these load balancing configurations: * For any load balancer, if the backends are not instance groups (for example, GCE_VM_IP_PORT NEGs). * For any type of backend on a backend service for internal or external passthrough Network Load Balancers. See also https://cloud.google.com/load-balancing/docs/backend-service#named_ports. |
| `--protocol` | one of: TCP, UDP, UNSPECIFIED |  | Protocol for incoming requests. If the load-balancing-scheme is INTERNAL (Internal passthrough Network Load Balancer), the protocol must be one of: TCP, UDP, UNSPECIFIED. If the load-balancing-scheme is INTERNAL_SELF_MANAGED (Traffic Director), the protocol must be one of: HTTP, HTTPS, HTTP2, GRPC, H2C. If the load-balancing-scheme is INTERNAL_MANAGED (Internal Application Load Balancer), the protocol must be one of: HTTP, HTTPS, HTTP2, H2C. If the load-balancing-scheme is INTERNAL_MANAGED (Internal proxy Network Load Balancer), the protocol must be only TCP. If the load-balancing-scheme is EXTERNAL and region is not set (Classic Application Load Balancer and Classic proxy Network Load Balancer), the protocol must be one of: HTTP, HTTPS, HTTP2, TCP, SSL. If the load-balancing-scheme is EXTERNAL and region is set (External passthrough Network Load Balancer), the protocol must be one of: TCP, UDP, UNSPECIFIED. If the load-balancing-scheme is EXTERNAL_MANAGED (Global external Application Load Balancer and regional external Application Load Balancer), the protocol must be one of: HTTP, HTTPS, HTTP2, H2C. If the load-balancing-scheme is EXTERNAL_MANAGED (Global external proxy Network Load Balancer), the protocol must be one of: TCP, SSL. If the load-balancing-scheme is EXTERNAL_MANAGED (Regional external proxy Network Load Balancer), the protocol must be only TCP. |
| `--[no-]request-coalescing` |  |  | Enables request coalescing to the backend (recommended). Request coalescing (or collapsing) combines multiple concurrent cache fill requests into a small number of requests to the origin. This can improve performance by putting less load on the origin and backend infrastructure. However, coalescing adds a small amount of latency when multiple requests to the same URL are processed, so for latency-critical applications it may not be desirable. Defaults to true. Use --request-coalescing to enable and --no-request-coalescing to disable. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the backend service. |
| `--serve-while-stale` | SERVE_WHILE_STALE |  | Serve existing content from the cache (if available) when revalidating content with the origin; this allows content to be served more quickly, and also allows content to continue to be served if the backend is down or reporting errors. This setting defines the default serve-stale duration for any cached responses that do not specify a stale-while-revalidate directive. Stale responses that exceed the TTL configured here will not be served without first being revalidated with the origin. The default limit is 86400s (1 day), which will allow stale content to be served up to this limit beyond the max-age (or s-max-age) of a cached response. The maximum allowed value is 604800 (1 week). Set this to zero (0) to disable serve-while-stale. |
| `--service-bindings` | SERVICE_BINDING,[...] |  | List of service bindings to be attached to this backend service. Can only be set if load balancing scheme is INTERNAL_SELF_MANAGED. If set, lists of backends and health checks must be both empty. |
| `--service-lb-policy` | SERVICE_LOAD_BALANCING_POLICY |  | Service load balancing policy to be applied to this backend service. Can only be set if load balancing scheme is EXTERNAL_MANAGED, INTERNAL_MANAGED, or INTERNAL_SELF_MANAGED. Only available for global backend services. |
| `--session-affinity` | one of: CLIENT_IP Route requests to instances based on the hash of the client's IP address |  | The type of session affinity to use. Supports both TCP and UDP. SESSION_AFFINITY must be one of: CLIENT_IP Route requests to instances based on the hash of the client's IP address. CLIENT_IP_NO_DESTINATION Directs a particular client's request to the same backend VM based on a hash created on the client's IP address only. This is used in L4 ILB as Next-Hop scenarios. It differs from the Client-IP option in that Client-IP uses a hash based on both client-IP's address and destination address. CLIENT_IP_PORT_PROTO (Applicable if --load-balancing-scheme is INTERNAL) Connections from the same client IP with the same IP protocol and port will go to the same backend VM while that VM remains healthy. CLIENT_IP_PROTO (Applicable if --load-balancing-scheme is INTERNAL) Connections from the same client IP with the same IP protocol will go to the same backend VM while that VM remains healthy. GENERATED_COOKIE (Applicable if --load-balancing-scheme is INTERNAL_MANAGED, INTERNAL_SELF_MANAGED, EXTERNAL_MANAGED, or EXTERNAL) If the --load-balancing-scheme is EXTERNAL or EXTERNAL_MANAGED, routes requests to backend VMs or endpoints in a NEG, based on the contents of the GCLB cookie set by the load balancer. Only applicable when --protocol is HTTP, HTTPS,HTTP2 or H2C. If the --load-balancing-scheme is INTERNAL_MANAGED or INTERNAL_SELF_MANAGED, routes requests to backend VMs or endpoints in a NEG, based on the contents of the GCILB cookie set by the proxy. (If no cookie is present, the proxy chooses a backend VM or endpoint and sends a Set-Cookie response for future requests.) If the --load-balancing-scheme is INTERNAL_SELF_MANAGED, routes requests to backend VMs or endpoints in a NEG, based on the contents of a cookie set by Traffic Director. This session affinity is only valid if the load balancing locality policy is either RING_HASH or MAGLEV. HEADER_FIELD (Applicable if --load-balancing-scheme is INTERNAL_MANAGED, EXTERNAL_MANAGED, or INTERNAL_SELF_MANAGED) Route requests to backend VMs or endpoints in a NEG based on the value of the HTTP header named in the --custom-request-header flag. This session affinity is only valid if the load balancing locality policy is either RING_HASH or MAGLEV and the backend service's consistent hash specifies the name of the HTTP header. HTTP_COOKIE (Applicable if --load-balancing-scheme is INTERNAL_MANAGED, EXTERNAL_MANAGED or INTERNAL_SELF_MANAGED) Route requests to backend VMs or endpoints in a NEG, based on an HTTP cookie in the --affinity-cookie-name flag (with the optional --affinity-cookie-ttl flag). If the client has not provided the cookie, the proxy generates the cookie and returns it to the client in a Set-Cookie header. This session affinity is only valid if the load balancing locality policy is either RING_HASH or MAGLEV and the backend service's consistent hash specifies the HTTP cookie. NONE Session affinity is disabled. STRONG_COOKIE_AFFINITY (Applicable if --load-balancing-scheme is INTERNAL_MANAGED or EXTERNAL_MANAGED) Strong cookie-based affinity, based on an HTTP cookie named in the --affinity-cookie-name flag (with the optional --affinity-cookie-ttl flag). Connections bearing the same cookie will be served by the same backend VM while that VM remains healthy, as long as the cookie has not expired. If the --affinity-cookie-ttl flag is set to 0, the cookie will be treated as a session cookie. |
| `--signed-url-cache-max-age` | SIGNED_URL_CACHE_MAX_AGE |  | The amount of time up to which the response to a signed URL request will be cached in the CDN. After this time period, the Signed URL will be revalidated before being served. Cloud CDN will internally act as though all responses from this backend had a Cache-Control: public, max-age=[TTL] header, regardless of any existing Cache-Control header. The actual headers served in responses will not be altered. If unspecified, the default value is 3600s. For example, specifying 12h will cause the responses to signed URL requests to be cached in the CDN up to 12 hours. See $ gcloud topic datetimes for information on duration formats. This flag only affects signed URL requests. |
| `--subsetting-policy` | one of: NONE, CONSISTENT_HASH_SUBSETTING | NONE | Specifies the algorithm used for subsetting. Default value is NONE which implies that subsetting is disabled. For Layer 4 Internal Load Balancing, if subsetting is enabled, only the algorithm CONSISTENT_HASH_SUBSETTING can be specified. SUBSETTING_POLICY must be one of: NONE, CONSISTENT_HASH_SUBSETTING. |
| `--timeout` | TIMEOUT | 30s | Applicable to all load balancing products except passthrough Network Load Balancers. For internal passthrough Network Load Balancers (load-balancing-scheme set to INTERNAL) and external passthrough Network Load Balancers (global not set and load-balancing-scheme set to EXTERNAL), timeout is ignored. If the protocol is HTTP, HTTPS, HTTP2 or H2C, timeout is a request/response timeout for HTTP(S) traffic, meaning the amount of time that the load balancer waits for a backend to return a full response to a request. If WebSockets traffic is supported, the timeout parameter sets the maximum amount of time that a WebSocket can be open (idle or not). For example, for HTTP, HTTPS, HTTP2 or H2C traffic, specifying a timeout of 10s means that backends have 10 seconds to respond to the load balancer's requests. The load balancer retries the HTTP GET request one time if the backend closes the connection or times out before sending response headers to the load balancer. If the backend sends response headers or if the request sent to the backend is not an HTTP GET request, the load balancer does not retry. If the backend does not reply at all, the load balancer returns a 502 Bad Gateway error to the client. If the protocol is SSL or TCP, timeout is an idle timeout. The full range of timeout values allowed is 1 - 2,147,483,647 seconds. |
| `--tls-settings` | [authenticationConfig=AUTHENTICATIONCONFIG],[sni=SNI] |  | Configuration for Backend Authenticated TLS and mTLS. May only be specified when the backend protocol is SSL, HTTPS or HTTP2. Example: $ gcloud compute backend-services create \ --tls-settings='sni=example.com,authenticationConfig=${AUTH_CONF\ IG_NAME}' |
| `--tracking-mode` | one of: PER_CONNECTION, PER_SESSION |  | Specifies the connection key used for connection tracking. The default value is PER_CONNECTION. Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. For details, see: Connection tracking mode for internal passthrough Network Load Balancers balancing (https://cloud.google.com/load-balancing/docs/internal#tracking-mode) and Connection tracking mode for external passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#tracking-mode). TRACKING_MODE must be one of: PER_CONNECTION, PER_SESSION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/create)

---
### `gcloud compute backend-services delete`

Delete backend services

gcloud compute backend-services delete deletes one or more backend
services.

**Synopsis:**
```
gcloud compute backend-services delete BACKEND_SERVICE_NAME
    [BACKEND_SERVICE_NAME ...] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME [BACKEND_SERVICE_NAME ...]
   Names of the backend services to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend services are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend services to delete. Overrides the default compute/region property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/delete)

---
### `gcloud compute backend-services delete-signed-url-key`

Delete Cloud CDN Signed URL key from a backend service

gcloud compute backend-services delete-signed-url-key is used to delete an
existing Cloud CDN Signed URL key from a backend service.

Cloud CDN Signed URLs give you a way to serve responses from the globally
distributed CDN cache, even if the request needs to be authorized.

Signed URLs are a mechanism to temporarily give a client access to a
private resource without requiring additional authorization. To achieve
this, the full request URL that should be allowed is hashed and
cryptographically signed. By using the signed URL you give it, that one
request will be considered authorized to receive the requested content.

Generally, a signed URL can be used by anyone who has it. However, it is
usually only intended to be used by the client that was directly given the
URL. To mitigate this, they expire at a time chosen by the issuer. To
minimize the risk of a signed URL being shared, it is recommended that the
signed URL be set to expire as soon as possible.

A 128-bit secret key is used for signing the URLs.

**Synopsis:**
```
gcloud compute backend-services delete-signed-url-key BACKEND_SERVICE_NAME
    --key-name=KEY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-name` | KEY_NAME |  | Name of the Cloud CDN Signed URL key. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/delete-signed-url-key)

---
### `gcloud compute backend-services describe`

Display detailed information about a backend service

gcloud compute backend-services describe displays all data associated with
a backend service in a project.

**Synopsis:**
```
gcloud compute backend-services describe BACKEND_SERVICE_NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to describe. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To get details about a global backend service, run:

    $ gcloud compute backend-services describe --global

To get details about a regional backend service in the us-central1 regions,
run:

    $ gcloud compute backend-services describe --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/describe)

---
### `gcloud compute backend-services edit`

Modify a backend service

gcloud compute backend-services edit modifies a backend service of a Google
Cloud load balancer or Traffic Director. The backend service resource is
fetched from the server and presented in a text editor that displays the
configurable fields.

The specific editor is defined by the EDITOR environment variable.

The name of each backend corresponds to the name of an instance group,
zonal NEG, serverless NEG, or internet NEG.

To add, remove, or swap backends, use the gcloud compute backend-services
remove-backend and gcloud compute backend-services add-backend commands.

**Synopsis:**
```
gcloud compute backend-services edit BACKEND_SERVICE_NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/edit)

---
### `gcloud compute backend-services export`

Export a backend service

Exports a backend service's configuration to a file. This configuration can
be imported at a later time.

**Synopsis:**
```
gcloud compute backend-services export BACKEND_SERVICE_NAME
    [--destination=DESTINATION] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\BackendService.yaml. |


**Examples:**
```bash
A backend service can be exported by running:

    $ gcloud compute backend-services export NAME \
        --destination=<path-to-file> --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/export)

---
### `gcloud compute backend-services get-health`

Get backend health statuses from a backend service

gcloud compute backend-services get-health is used to request the current
health status of instances in a backend service. Every group in the service
is checked and the health status of each configured instance is printed.

If a group contains names of instances that don't exist or instances that
haven't yet been pushed to the load-balancing system, they will not show
up. Those that are listed as HEALTHY are able to receive load-balanced
traffic. Those that are marked as UNHEALTHY are either failing the
configured health-check or not responding to it.

Since the health checks are performed continuously and in a distributed
manner, the state returned by this command is the most recent result of a
vote of several redundant health checks. Backend services that do not have
a valid global forwarding rule referencing it will not be health checked
and so will have no health status.

**Synopsis:**
```
gcloud compute backend-services get-health BACKEND_SERVICE_NAME
    [--global | --region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/get-health)

---
### `gcloud compute backend-services get-iam-policy`

Get the IAM policy for a Compute Engine backend service

gcloud compute backend-services get-iam-policy displays the IAM policy
associated with a Compute Engine backend service in a project. If formatted
as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute backend-services get-iam-policy BACKEND_SERVICE_NAME
    [--global | --region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To print the IAM policy for a given backend service, run:

    $ gcloud compute backend-services get-iam-policy \
        my-backend-service --region=REGION

    $ gcloud compute backend-services get-iam-policy \
        my-backend-service --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/get-iam-policy)

---
### `gcloud compute backend-services import`

Import a backend service

Imports a backend service's configuration from a file.

**Synopsis:**
```
gcloud compute backend-services import BACKEND_SERVICE_NAME
    [--source=SOURCE] [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to import.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\BackendService.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
A backend service can be imported by running:

    $ gcloud compute backend-services import NAME \
        --source=<path-to-file> --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/import)

---
### `gcloud compute backend-services list`

List Google Compute Engine backend services

gcloud compute backend-services list displays all Google Compute Engine
backend services in a project.

By default, global backend services and backend services from all regions
are listed. The results can be narrowed down by providing the --global or
--regions flag.

**Synopsis:**
```
gcloud compute backend-services list [NAME ...]
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
To list all backend services in a project in table form, run:

    $ gcloud compute backend-services list

To list the URIs of all backend services in a project, run:

    $ gcloud compute backend-services list --uri

To list all global backend services in a project, run:

    $ gcloud compute backend-services list --global

To list all backend services in the us-central1 and europe-west1 regions,
given they are regional resources, run:

    $ gcloud compute backend-services list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/list)

---
### `gcloud compute backend-services list-usable`

List usable backend services

gcloud compute backend-services list-usable retrieves the list of backend
service resources in the specified project for which you have
compute.backendService.get and compute.backendService.use permissions. This
command is useful when you're creating load balancers in a Shared VPC
environment and you want to use cross-project service referencing
(https://cloud.google.com/load-balancing/docs/https#cross-project). You can
use this command to find out which backend services in other projects are
available to you for referencing.

**Synopsis:**
```
gcloud compute backend-services list-usable [BACKEND_SERVICE_NAME]
    [--global | --region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[BACKEND_SERVICE_NAME]
   Name of the backend service to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To list all global backend services in a project, run:

    $ gcloud compute backend-services list-usable --global

To list all backend services in a region, run:

    $ gcloud compute backend-services list-usable --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/list-usable)

---
### `gcloud compute backend-services remove-backend`

Remove a backend from a backend service

gcloud compute backend-services remove-backend is used to remove a backend
from a backend service.

Before removing a backend, it is a good idea to "drain" the backend first.
A backend can be drained by setting its capacity scaler to zero through
'gcloud compute backend-services edit'.

**Synopsis:**
```
gcloud compute backend-services remove-backend BACKEND_SERVICE_NAME
    ([--instance-group=INSTANCE_GROUP
      : --instance-group-region=INSTANCE_GROUP_REGION
      | --instance-group-zone=INSTANCE_GROUP_ZONE]
      | [--network-endpoint-group=NETWORK_ENDPOINT_GROUP
      : --global-network-endpoint-group
      | --network-endpoint-group-region=NETWORK_ENDPOINT_GROUP_REGION
      | --network-endpoint-group-zone=NETWORK_ENDPOINT_GROUP_ZONE])
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-group` | INSTANCE_GROUP |  | _[Instance Group]_ Name of the instance group to remove from the backend service. For details on valid instance names, refer to the criteria documented under the field 'name' at: https://cloud.google.com/compute/docs/reference/rest/v1/instances This flag argument must be specified if any of the other arguments in this group are specified. |
| `--network-endpoint-group` | NETWORK_ENDPOINT_GROUP |  | _[Network Endpoint Group]_ Name of the network endpoint group to remove from the backend service. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/remove-backend)

---
### `gcloud compute backend-services remove-iam-policy-binding`

Remove an IAM policy binding from a Compute Engine backend service

Remove an IAM policy binding from a Compute Engine backend service.

**Synopsis:**
```
gcloud compute backend-services remove-iam-policy-binding
    BACKEND_SERVICE_NAME --member=PRINCIPAL --role=ROLE
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/compute.loadBalancerServiceUser' for the user 'test-user@gmail.com'
with backend service 'my-backend-service' and region 'REGION', run:

    $ gcloud compute backend-services remove-iam-policy-binding \
      my-backend-service --region=REGION \
      --member='user:test-user@gmail.com' \
      --role='roles/compute.loadBalancerServiceUser'

    $ gcloud compute backend-services remove-iam-policy-binding \
      my-backend-service --global \
      --member='user:test-user@gmail.com' \
      --role='roles/compute.loadBalancerServiceUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/remove-iam-policy-binding)

---
### `gcloud compute backend-services remove-service-bindings`

Remove service bindings from a backend service

Remove service bindings from a backend service.

**Synopsis:**
```
gcloud compute backend-services remove-service-bindings
    BACKEND_SERVICE_NAME --service-bindings=SERVICE_BINDING,[...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-bindings` | SERVICE_BINDING,[...] |  | List of service binding names to be removed from the backend service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To remove a service binding from a backend service, run:

    $ gcloud compute backend-services remove-service-bindings NAME \
        --service-bindings=SERVICE_BINDING1 --global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/remove-service-bindings)

---
### `gcloud compute backend-services set-iam-policy`

Set the IAM policy binding for a Compute Engine backend service

Sets the IAM policy for the given backend service as defined in a JSON or
YAML file.

**Synopsis:**
```
gcloud compute backend-services set-iam-policy BACKEND_SERVICE_NAME
    POLICY_FILE [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the backend service is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the backend service to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the backend service my-backend-service:

    $ gcloud compute backend-services set-iam-policy \
        my-backend-service policy.json --region=REGION

    $ gcloud compute backend-services set-iam-policy \
        my-backend-service policy.json --global

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/set-iam-policy)

---
### `gcloud compute backend-services update`

Update a backend service

gcloud compute backend-services update is used to update backend services.

**Synopsis:**
```
gcloud compute backend-services update BACKEND_SERVICE_NAME
    [--affinity-cookie-name=AFFINITY_COOKIE_NAME]
    [--affinity-cookie-path=AFFINITY_COOKIE_PATH]
    [--affinity-cookie-ttl=AFFINITY_COOKIE_TTL] [--cache-key-include-host]
    [--cache-key-include-http-header=[HEADER_FIELD_NAME,...]]
    [--cache-key-include-named-cookie=[NAMED_COOKIE,...]]
    [--cache-key-include-protocol] [--cache-key-include-query-string]
    [--cache-mode=CACHE_MODE] [--compression-mode=COMPRESSION_MODE]
    [--connection-drain-on-failover]
    [--connection-draining-timeout=CONNECTION_DRAINING_TIMEOUT]
    [--connection-persistence-on-unhealthy-backends=CONNECTION_PERSISTENCE_ON_UNHEALTHY_BACKENDS]
    [--description=DESCRIPTION] [--drop-traffic-if-unhealthy]
    [--edge-security-policy=EDGE_SECURITY_POLICY] [--[no-]enable-cdn]
    [--[no-]enable-logging] [--[no-]enable-strong-affinity]
    [--external-managed-migration-testing-percentage=EXTERNAL_MANAGED_MIGRATION_TESTING_PERCENTAGE]
    [--failover-ratio=FAILOVER_RATIO] [--health-checks=HEALTH_CHECK,[...]]
    [--no-health-checks] [--http-health-checks=HTTP_HEALTH_CHECK,[...]]
    [--https-health-checks=HTTPS_HEALTH_CHECK,[...]]
    [--iap=disabled|enabled,[oauth2-client-id=OAUTH2-CLIENT-ID,
      oauth2-client-secret=OAUTH2-CLIENT-SECRET]]
    [--idle-timeout-sec=IDLE_TIMEOUT_SEC]
    [--ip-address-selection-policy=IP_ADDRESS_SELECTION_POLICY]
    [--load-balancing-scheme=LOAD_BALANCING_SCHEME]
    [--logging-optional=LOGGING_OPTIONAL]
    [--logging-optional-fields=[LOGGING_OPTIONAL_FIELDS,...]]
    [--logging-sample-rate=LOGGING_SAMPLE_RATE] [--port-name=PORT_NAME]
    [--protocol=PROTOCOL] [--[no-]request-coalescing]
    [--security-policy=SECURITY_POLICY]
    [--session-affinity=SESSION_AFFINITY]
    [--signed-url-cache-max-age=SIGNED_URL_CACHE_MAX_AGE]
    [--subsetting-policy=SUBSETTING_POLICY; default="NONE"]
    [--timeout=TIMEOUT] [--tracking-mode=TRACKING_MODE]
    [--bypass-cache-on-request-headers=BYPASS_CACHE_ON_REQUEST_HEADERS
      | --no-bypass-cache-on-request-headers]
    [--cache-key-query-string-blacklist=[QUERY_STRING,...]
      | --cache-key-query-string-whitelist=QUERY_STRING,[...]]
    [--clear-custom-metrics | --custom-metrics=[CUSTOM_METRICS,...]
      | --custom-metrics-file=[CUSTOM_METRICS,...]]
    [--clear-external-managed-migration-state
      | --external-managed-migration-state=EXTERNAL_MANAGED_MIGRATION_STATE]
    [--client-ttl=CLIENT_TTL | --no-client-ttl]
    [--custom-request-header=CUSTOM_REQUEST_HEADER
      | --no-custom-request-headers]
    [--custom-response-header=CUSTOM_RESPONSE_HEADER
      | --no-custom-response-headers]
    [--default-ttl=DEFAULT_TTL | --no-default-ttl]
    [--global | --region=REGION]
    [--global-health-checks | --health-checks-region=HEALTH_CHECKS_REGION]
    [--locality-lb-policy=LOCALITY_LB_POLICY | --no-locality-lb-policy]
    [--max-ttl=MAX_TTL | --no-max-ttl]
    [--[no-]negative-caching | --no-negative-caching-policies
      | --negative-caching-policy=[[CODE=TTL],...]]
    [--serve-while-stale=SERVE_WHILE_STALE | --no-serve-while-stale]
    [--service-bindings=SERVICE_BINDING,[...] | --no-service-bindings]
    [--service-lb-policy=SERVICE_LOAD_BALANCING_POLICY
      | --no-service-lb-policy]
    [--tls-settings=[authenticationConfig=AUTHENTICATIONCONFIG],[sni=SNI]
      | --no-tls-settings] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--affinity-cookie-name` | AFFINITY_COOKIE_NAME |  | If --session-affinity is set to HTTP_COOKIE or STRONG_COOKIE_AFFINITY, this flag sets the name of the cookie. |
| `--affinity-cookie-path` | AFFINITY_COOKIE_PATH |  | If --session-affinity is set to HTTP_COOKIE or STRONG_COOKIE_AFFINITY, this flag sets the path of the cookie. |
| `--affinity-cookie-ttl` | AFFINITY_COOKIE_TTL |  | If --session-affinity is set to GENERATED_COOKIE, HTTP_COOKIE, or STRONG_COOKIE_AFFINITY, this flag sets the TTL, in seconds, of the resulting cookie. A setting of 0 indicates that the cookie should be a session cookie. See $ gcloud topic datetimes for information on duration formats. |
| `--cache-key-include-host` |  |  | Enable including host in cache key. If enabled, requests to different hosts will be cached separately. Can only be applied for global resources. |
| `--cache-key-include-http-header` | [HEADER_FIELD_NAME,...] |  | Specifies a comma-separated list of HTTP headers, by field name, to include in cache keys. Only the request URL is included in the cache key by default. |
| `--cache-key-include-named-cookie` | [NAMED_COOKIE,...] |  | Specifies a comma-separated list of HTTP cookie names to include in cache keys. The name=value pair are used in the cache key Cloud CDN generates. Cookies are not included in cache keys by default. |
| `--cache-key-include-protocol` |  |  | Enable including protocol in cache key. If enabled, http and https requests will be cached separately. Can only be applied for global resources. |
| `--cache-key-include-query-string` |  |  | Enable including query string in cache key. If enabled, the query string parameters will be included according to --cache-key-query-string-whitelist and --cache-key-query-string-blacklist. If disabled, the entire query string will be excluded. Use "--cache-key-query-string-blacklist=" (sets the blacklist to the empty list) to include the entire query string. Can only be applied for global resources. |
| `--cache-mode` | one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS) |  | Specifies the cache setting for all responses from this backend. CACHE_MODE must be one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS). Requests and responses that are marked as uncacheable, as well as dynamic content (including HTML), aren't cached. FORCE_CACHE_ALL Cache all content, ignoring any "private", "no-store" or "no-cache" directives in Cache-Control response headers. Warning: this may result in Cloud CDN caching private, per-user (user identifiable) content. You should only enable this on backends that are not serving private or dynamic content, such as storage buckets. USE_ORIGIN_HEADERS Require the origin to set valid caching headers to cache content. Responses without these headers aren't cached at Google's edge, and require a full trip to the origin on every request, potentially impacting performance and increasing load on the origin server. |
| `--compression-mode` | one of: DISABLED, AUTOMATIC |  | Compress text responses using Brotli or gzip compression, based on the client's Accept-Encoding header. Two modes are supported: AUTOMATIC (recommended) - automatically uses the best compression based on the Accept-Encoding header sent by the client. In most cases, this will result in Brotli compression being favored. DISABLED - disables compression. Existing compressed responses cached by Cloud CDN will not be served to clients. COMPRESSION_MODE must be one of: DISABLED, AUTOMATIC. |
| `--connection-drain-on-failover` |  |  | Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. Only applicable when the backend service protocol is TCP. Not applicable to any other load balancer. Enabled by default, this option instructs the load balancer to allow established TCP connections to persist for up to 300 seconds on instances or endpoints in primary backends during failover, and on instances or endpoints in failover backends during failback. For details, see: Connection draining on failover and failback for internal passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/internal/failover-overview#connection_draining) and Connection draining on failover and failback for external passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/network/networklb-failover-overview#connection_draining). |
| `--connection-draining-timeout` | CONNECTION_DRAINING_TIMEOUT |  | Connection draining timeout to be used during removal of VMs from instance groups. This guarantees that for the specified time all existing connections to a VM will remain untouched, but no new connections will be accepted. Set timeout to zero to disable connection draining. Enable feature by specifying a timeout of up to one hour. If the flag is omitted API default value (0s) will be used. See $ gcloud topic datetimes for information on duration formats. |
| `--connection-persistence-on-unhealthy-backends` | one of: DEFAULT_FOR_PROTOCOL, NEVER_PERSIST, ALWAYS_PERSIST |  | Specifies connection persistence when backends are unhealthy. The default value is DEFAULT_FOR_PROTOCOL. CONNECTION_PERSISTENCE_ON_UNHEALTHY_BACKENDS must be one of: DEFAULT_FOR_PROTOCOL, NEVER_PERSIST, ALWAYS_PERSIST. |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend service. |
| `--drop-traffic-if-unhealthy` |  |  | Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. Not applicable to any other load balancer. This option instructs the load balancer to drop packets when all instances or endpoints in primary and failover backends do not pass their load balancer health checks. For details, see: Dropping traffic when all backend VMs are unhealthy for internal passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/internal/failover-overview#drop_traffic) and Dropping traffic when all backend VMs are unhealthy for external passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/network/networklb-failover-overview#drop_traffic). |
| `--edge-security-policy` | EDGE_SECURITY_POLICY |  | The edge security policy that will be set for this backend service. To remove the policy from this backend service set the policy to an empty string. |
| `--[no-]enable-cdn` |  |  | Enable or disable Cloud CDN for the backend service. Only available for backend services with --load-balancing-scheme=EXTERNAL or EXTERNAL_MANAGED that use a --protocol of HTTP, HTTPS, HTTP2 or H2C. Cloud CDN caches HTTP responses at the edge of Google's network. Cloud CDN is disabled by default. Use --enable-cdn to enable and --no-enable-cdn to disable. |
| `--[no-]enable-logging` |  |  | The logging options for the load balancer traffic served by this backend service. If logging is enabled, logs will be exported to Cloud Logging. Disabled by default. This field cannot be specified for global external proxy Network Load Balancers. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--[no-]enable-strong-affinity` |  |  | Enable or disable strong session affinity. This is only available for loadbalancingScheme EXTERNAL. Use --enable-strong-affinity to enable and --no-enable-strong-affinity to disable. |
| `--external-managed-migration-testing-percentage` | EXTERNAL_MANAGED_MIGRATION_TESTING_PERCENTAGE |  | Determines the fraction of requests that should be processed by the Global external Application Load Balancer. The value of this field must be in the range [0, 100]. |
| `--failover-ratio` | FAILOVER_RATIO |  | Applicable only to backend service-based external passthrough Network load balancers and internal passthrough Network load balancers as part of a failover policy. Not applicable to any other load balancer. This option defines the ratio used to control when failover and failback occur. For details, see: Failover ratio for internal passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/internal/failover-overview#failover_ratio) and Failover ratio for external passthrough Network Load Balancer overview (https://cloud.google.com/load-balancing/docs/network/networklb-failover-overview#failover_ratio). |
| `--health-checks` | HEALTH_CHECK,[...] |  | Specifies a list of health check objects for checking the health of the backend service. Currently at most one health check can be specified. Health checks need not be for the same protocol as that of the backend service. |
| `--no-health-checks` |  |  | Removes all health checks for the backend service if the backend service has no backends attached. |
| `--http-health-checks` | HTTP_HEALTH_CHECK,[...] |  | Specifies a list of legacy HTTP health check objects for checking the health of the backend service. Legacy health checks are not recommended for backend services. It is possible to use a legacy health check on a backend service for an Application Load Balancer if that backend service uses instance groups. For more information, refer to this guide: https://cloud.google.com/load-balancing/docs/health-check-concepts#lb_guide. |
| `--https-health-checks` | HTTPS_HEALTH_CHECK,[...] |  | Specifies a list of legacy HTTPS health check objects for checking the health of the backend service. Legacy health checks are not recommended for backend services. It is possible to use a legacy health check on a backend service for an Application Load Balancer if that backend service uses instance groups. For more information, refer to this guide: https://cloud.google.com/load-balancing/docs/health-check-concepts#lb_guide. |
| `--iap` | disabled\|enabled,[oauth2-client-id=OAUTH2-CLIENT-ID,oauth2-client-secret=OAUTH2-CLIENT-SECRET] |  | Change the Identity Aware Proxy (IAP) service configuration for the backend service. You can set IAP to 'enabled' or 'disabled', or modify the OAuth2 client configuration (oauth2-client-id and oauth2-client-secret) used by IAP. If any fields are unspecified, their values will not be modified. For instance, if IAP is enabled, '--iap=disabled' will disable IAP, and a subsequent '--iap=enabled' will then enable it with the same OAuth2 client configuration as the first time it was enabled. See https://cloud.google.com/iap/ for more information about this feature. |
| `--idle-timeout-sec` | IDLE_TIMEOUT_SEC |  | Specifies how long to keep a connection tracking table entry while there is no matching traffic (in seconds). Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. |
| `--ip-address-selection-policy` | one of: IPV4_ONLY, PREFER_IPV6, IPV6_ONLY |  | Specifies a preference for traffic sent from the proxy to the backend (or from the client to the backend for proxyless gRPC). Can only be set if load balancing scheme is INTERNAL_SELF_MANAGED, INTERNAL_MANAGED or EXTERNAL_MANAGED. The possible values are: IPV4_ONLY Only send IPv4 traffic to the backends of the backend service, regardless of traffic from the client to the proxy. Only IPv4 health checks are used to check the health of the backends. PREFER_IPV6 Prioritize the connection to the endpoint's IPv6 address over its IPv4 address (provided there is a healthy IPv6 address). IPV6_ONLY Only send IPv6 traffic to the backends of the backend service, regardless of traffic from the client to the proxy. Only IPv6 health checks are used to check the health of the backends. IP_ADDRESS_SELECTION_POLICY must be one of: IPV4_ONLY, PREFER_IPV6, IPV6_ONLY. |
| `--load-balancing-scheme` | one of: EXTERNAL, EXTERNAL_MANAGED |  | Only for the Global external Application Load Balancer migration. The value of this field must be EXTERNAL or EXTERNAL_MANAGED. LOAD_BALANCING_SCHEME must be one of: EXTERNAL, EXTERNAL_MANAGED. |
| `--logging-optional` | one of: EXCLUDE_ALL_OPTIONAL, INCLUDE_ALL_OPTIONAL, CUSTOM |  | This field can only be specified if logging is enabled for the backend service. Configures whether all, none, or a subset of optional fields should be added to the reported logs. Default is EXCLUDE_ALL_OPTIONAL. This field can only be specified for internal and external passthrough Network Load Balancers. LOGGING_OPTIONAL must be one of: EXCLUDE_ALL_OPTIONAL, INCLUDE_ALL_OPTIONAL, CUSTOM. |
| `--logging-optional-fields` | [LOGGING_OPTIONAL_FIELDS,...] |  | This field can only be specified if logging is enabled for the backend service and "--logging-optional" was set to CUSTOM. Contains a comma-separated list of optional fields you want to include in the logs. For example: serverInstance, serverGkeDetails.cluster, serverGkeDetails.pod.podNamespace. This can only be specified for internal and external passthrough Network Load Balancers. |
| `--logging-sample-rate` | LOGGING_SAMPLE_RATE |  | This field can only be specified if logging is enabled for the backend service. The value of the field must be a float in the range [0, 1]. This configures the sampling rate of requests to the load balancer where 1.0 means all logged requests are reported and 0.0 means no logged requests are reported. The default value is 1.0 when logging is enabled and 0.0 otherwise. |
| `--port-name` | PORT_NAME |  | Backend services for Application Load Balancers and proxy Network Load Balancers must reference exactly one named port if using instance group backends. Each instance group backend exports one or more named ports, which map a user-configurable name to a port number. The backend service's named port subscribes to one named port on each instance group. The resolved port number can differ among instance group backends, based on each instance group's named port list. When omitted, a backend service subscribes to a named port called http. The named port for a backend service is either ignored or cannot be set for these load balancing configurations: * For any load balancer, if the backends are not instance groups (for example, GCE_VM_IP_PORT NEGs). * For any type of backend on a backend service for internal or external passthrough Network Load Balancers. See also https://cloud.google.com/load-balancing/docs/backend-service#named_ports. |
| `--protocol` | one of: TCP, UDP, UNSPECIFIED |  | Protocol for incoming requests. If the load-balancing-scheme is INTERNAL (Internal passthrough Network Load Balancer), the protocol must be one of: TCP, UDP, UNSPECIFIED. If the load-balancing-scheme is INTERNAL_SELF_MANAGED (Traffic Director), the protocol must be one of: HTTP, HTTPS, HTTP2, GRPC, H2C. If the load-balancing-scheme is INTERNAL_MANAGED (Internal Application Load Balancer), the protocol must be one of: HTTP, HTTPS, HTTP2, H2C. If the load-balancing-scheme is INTERNAL_MANAGED (Internal proxy Network Load Balancer), the protocol must be only TCP. If the load-balancing-scheme is EXTERNAL and region is not set (Classic Application Load Balancer and Classic proxy Network Load Balancer), the protocol must be one of: HTTP, HTTPS, HTTP2, TCP, SSL. If the load-balancing-scheme is EXTERNAL and region is set (External passthrough Network Load Balancer), the protocol must be one of: TCP, UDP, UNSPECIFIED. If the load-balancing-scheme is EXTERNAL_MANAGED (Global external Application Load Balancer and regional external Application Load Balancer), the protocol must be one of: HTTP, HTTPS, HTTP2, H2C. If the load-balancing-scheme is EXTERNAL_MANAGED (Global external proxy Network Load Balancer), the protocol must be one of: TCP, SSL. If the load-balancing-scheme is EXTERNAL_MANAGED (Regional external proxy Network Load Balancer), the protocol must be only TCP. |
| `--[no-]request-coalescing` |  |  | Enables request coalescing to the backend (recommended). Request coalescing (or collapsing) combines multiple concurrent cache fill requests into a small number of requests to the origin. This can improve performance by putting less load on the origin and backend infrastructure. However, coalescing adds a small amount of latency when multiple requests to the same URL are processed, so for latency-critical applications it may not be desirable. Defaults to true. Use --request-coalescing to enable and --no-request-coalescing to disable. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that will be set for this backend service. |
| `--session-affinity` | one of: CLIENT_IP Route requests to instances based on the hash of the client's IP address |  | The type of session affinity to use. Supports both TCP and UDP. SESSION_AFFINITY must be one of: CLIENT_IP Route requests to instances based on the hash of the client's IP address. CLIENT_IP_NO_DESTINATION Directs a particular client's request to the same backend VM based on a hash created on the client's IP address only. This is used in L4 ILB as Next-Hop scenarios. It differs from the Client-IP option in that Client-IP uses a hash based on both client-IP's address and destination address. CLIENT_IP_PORT_PROTO (Applicable if --load-balancing-scheme is INTERNAL) Connections from the same client IP with the same IP protocol and port will go to the same backend VM while that VM remains healthy. CLIENT_IP_PROTO (Applicable if --load-balancing-scheme is INTERNAL) Connections from the same client IP with the same IP protocol will go to the same backend VM while that VM remains healthy. GENERATED_COOKIE (Applicable if --load-balancing-scheme is INTERNAL_MANAGED, INTERNAL_SELF_MANAGED, EXTERNAL_MANAGED, or EXTERNAL) If the --load-balancing-scheme is EXTERNAL or EXTERNAL_MANAGED, routes requests to backend VMs or endpoints in a NEG, based on the contents of the GCLB cookie set by the load balancer. Only applicable when --protocol is HTTP, HTTPS,HTTP2 or H2C. If the --load-balancing-scheme is INTERNAL_MANAGED or INTERNAL_SELF_MANAGED, routes requests to backend VMs or endpoints in a NEG, based on the contents of the GCILB cookie set by the proxy. (If no cookie is present, the proxy chooses a backend VM or endpoint and sends a Set-Cookie response for future requests.) If the --load-balancing-scheme is INTERNAL_SELF_MANAGED, routes requests to backend VMs or endpoints in a NEG, based on the contents of a cookie set by Traffic Director. This session affinity is only valid if the load balancing locality policy is either RING_HASH or MAGLEV. HEADER_FIELD (Applicable if --load-balancing-scheme is INTERNAL_MANAGED, EXTERNAL_MANAGED, or INTERNAL_SELF_MANAGED) Route requests to backend VMs or endpoints in a NEG based on the value of the HTTP header named in the --custom-request-header flag. This session affinity is only valid if the load balancing locality policy is either RING_HASH or MAGLEV and the backend service's consistent hash specifies the name of the HTTP header. HTTP_COOKIE (Applicable if --load-balancing-scheme is INTERNAL_MANAGED, EXTERNAL_MANAGED or INTERNAL_SELF_MANAGED) Route requests to backend VMs or endpoints in a NEG, based on an HTTP cookie in the --affinity-cookie-name flag (with the optional --affinity-cookie-ttl flag). If the client has not provided the cookie, the proxy generates the cookie and returns it to the client in a Set-Cookie header. This session affinity is only valid if the load balancing locality policy is either RING_HASH or MAGLEV and the backend service's consistent hash specifies the HTTP cookie. NONE Session affinity is disabled. STRONG_COOKIE_AFFINITY (Applicable if --load-balancing-scheme is INTERNAL_MANAGED or EXTERNAL_MANAGED) Strong cookie-based affinity, based on an HTTP cookie named in the --affinity-cookie-name flag (with the optional --affinity-cookie-ttl flag). Connections bearing the same cookie will be served by the same backend VM while that VM remains healthy, as long as the cookie has not expired. If the --affinity-cookie-ttl flag is set to 0, the cookie will be treated as a session cookie. |
| `--signed-url-cache-max-age` | SIGNED_URL_CACHE_MAX_AGE |  | The amount of time up to which the response to a signed URL request will be cached in the CDN. After this time period, the Signed URL will be revalidated before being served. Cloud CDN will internally act as though all responses from this backend had a Cache-Control: public, max-age=[TTL] header, regardless of any existing Cache-Control header. The actual headers served in responses will not be altered. For example, specifying 12h will cause the responses to signed URL requests to be cached in the CDN up to 12 hours. See $ gcloud topic datetimes for information on duration formats. This flag only affects signed URL requests. |
| `--subsetting-policy` | one of: NONE, CONSISTENT_HASH_SUBSETTING | NONE | Specifies the algorithm used for subsetting. Default value is NONE which implies that subsetting is disabled. For Layer 4 Internal Load Balancing, if subsetting is enabled, only the algorithm CONSISTENT_HASH_SUBSETTING can be specified. SUBSETTING_POLICY must be one of: NONE, CONSISTENT_HASH_SUBSETTING. |
| `--timeout` | TIMEOUT |  | Applicable to all load balancing products except passthrough Network Load Balancers. For internal passthrough Network Load Balancers (load-balancing-scheme set to INTERNAL) and external passthrough Network Load Balancers (global not set and load-balancing-scheme set to EXTERNAL), timeout is ignored. If the protocol is HTTP, HTTPS, HTTP2 or H2C, timeout is a request/response timeout for HTTP(S) traffic, meaning the amount of time that the load balancer waits for a backend to return a full response to a request. If WebSockets traffic is supported, the timeout parameter sets the maximum amount of time that a WebSocket can be open (idle or not). For example, for HTTP, HTTPS, HTTP2 or H2C traffic, specifying a timeout of 10s means that backends have 10 seconds to respond to the load balancer's requests. The load balancer retries the HTTP GET request one time if the backend closes the connection or times out before sending response headers to the load balancer. If the backend sends response headers or if the request sent to the backend is not an HTTP GET request, the load balancer does not retry. If the backend does not reply at all, the load balancer returns a 502 Bad Gateway error to the client. If the protocol is SSL or TCP, timeout is an idle timeout. The full range of timeout values allowed is 1 - 2,147,483,647 seconds. |
| `--tracking-mode` | one of: PER_CONNECTION, PER_SESSION |  | Specifies the connection key used for connection tracking. The default value is PER_CONNECTION. Applicable only for backend service-based external and internal passthrough Network Load Balancers as part of a connection tracking policy. For details, see: Connection tracking mode for internal passthrough Network Load Balancers balancing (https://cloud.google.com/load-balancing/docs/internal#tracking-mode) and Connection tracking mode for external passthrough Network Load Balancers (https://cloud.google.com/load-balancing/docs/network/networklb-backend-service#tracking-mode). TRACKING_MODE must be one of: PER_CONNECTION, PER_SESSION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/update)

---
### `gcloud compute backend-services update-backend`

Update an existing backend of a load balancer or Traffic Director

gcloud compute backend-services update-backend updates attributes of a
backend that is already associated with a backend service. Configurable
attributes depend on the load balancing scheme and the type of backend
(instance group, zonal NEG, serverless NEG, or internet NEG). For more
information, see traffic distribution
(https://cloud.google.com/load-balancing/docs/backend-service#traffic_distribution).
and the Failover for Internal TCP/UDP Load Balancing overview
(https://cloud.google.com/load-balancing/docs/internal/failover-overview).

To add, remove, or swap backends, use the gcloud compute backend-services
remove-backend and gcloud compute backend-services add-backend commands.

**Synopsis:**
```
gcloud compute backend-services update-backend BACKEND_SERVICE_NAME
    ([--instance-group=INSTANCE_GROUP
      : --instance-group-region=INSTANCE_GROUP_REGION
      | --instance-group-zone=INSTANCE_GROUP_ZONE]
      | [--network-endpoint-group=NETWORK_ENDPOINT_GROUP
      : --network-endpoint-group-zone=NETWORK_ENDPOINT_GROUP_ZONE])
    [--balancing-mode=BALANCING_MODE] [--capacity-scaler=CAPACITY_SCALER]
    [--description=DESCRIPTION] [--failover]
    [--max-utilization=MAX_UTILIZATION] [--preference=PREFERENCE]
    [--clear-custom-metrics | --custom-metrics=[CUSTOM_METRICS,...]
      | --custom-metrics-file=[CUSTOM_METRICS,...]]
    [--global | --region=REGION]
    [--max-connections=MAX_CONNECTIONS
      | --max-connections-per-endpoint=MAX_CONNECTIONS_PER_ENDPOINT
      | --max-connections-per-instance=MAX_CONNECTIONS_PER_INSTANCE
      | --max-rate=MAX_RATE | --max-rate-per-endpoint=MAX_RATE_PER_ENDPOINT
      | --max-rate-per-instance=MAX_RATE_PER_INSTANCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_SERVICE_NAME
   Name of the backend service to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-group` | INSTANCE_GROUP |  | _[Instance Group]_ Name of the instance group to update in the backend service. For details on valid instance names, refer to the criteria documented under the field 'name' at: https://cloud.google.com/compute/docs/reference/rest/v1/instances This flag argument must be specified if any of the other arguments in this group are specified. |
| `--network-endpoint-group` | NETWORK_ENDPOINT_GROUP |  | _[Network Endpoint Group]_ Name of the network endpoint group to update in the backend service. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--network-endpoint-group-zone` | NETWORK_ENDPOINT_GROUP_ZONE |  | _[Network Endpoint Group]_ Zone of the network endpoint group to update in the backend service. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--balancing-mode` | one of: CONNECTION Available if the backend service's load balancing scheme is either INTERNAL or EXTERNAL |  | Defines how to measure whether a backend can handle additional traffic or is fully loaded. For more information, see https://cloud.google.com/load-balancing/docs/backend-service#balancing-mode. BALANCING_MODE must be one of: CONNECTION Available if the backend service's load balancing scheme is either INTERNAL or EXTERNAL. Available if the backend service's protocol is one of SSL, TCP, or UDP. Spreads load based on how many concurrent connections the backend can handle. For backend services with --load-balancing-scheme EXTERNAL, you must specify exactly one of these additional parameters: --max-connections, --max-connections-per-instance, or --max-connections-per-endpoint. For backend services where --load-balancing-scheme is INTERNAL, you must omit all of these parameters. CUSTOM_METRICS Spreads load based on custom defined and reported metrics. RATE Available if the backend service's load balancing scheme is INTERNAL_MANAGED, INTERNAL_SELF_MANAGED, or EXTERNAL. Available if the backend service's protocol is one of HTTP, HTTPS, or HTTP/2. Spreads load based on how many HTTP requests per second (RPS) the backend can handle. You must specify exactly one of these additional parameters: --max-rate, --max-rate-per-instance, or --max-rate-per-endpoint. UTILIZATION Available if the backend service's load balancing scheme is INTERNAL_MANAGED, INTERNAL_SELF_MANAGED, or EXTERNAL. Available only for managed or unmanaged instance group backends. Spreads load based on the backend utilization of instances in a backend instance group. The following additional parameters may be specified: --max-utilization, --max-rate, --max-rate-per-instance, --max-connections, --max-connections-per-instance. For valid combinations, see --max-utilization. |
| `--capacity-scaler` | CAPACITY_SCALER |  | Scales down the target capacity (max utilization, max rate, or max connections) without changing the target capacity. For usage guidelines and examples, see Capacity scaler (https://cloud.google.com/load-balancing/docs/backend-service#capacity_scaler). |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--failover` |  |  | Designates whether this is a failover backend. More than one failover backend can be configured for a given BackendService. Not compatible with the --global flag |
| `--max-utilization` | MAX_UTILIZATION |  | Defines the maximum target for average utilization of the backend instance group. Supported values are 0.0 (0%) through 1.0 (100%). This is an optional parameter for the UTILIZATION balancing mode. You can use this parameter with other parameters for defining target capacity. For usage guidelines, see Balancing mode combinations (https://cloud.google.com/load-balancing/docs/backend-service#balancing-mode-combos). |
| `--preference` | one of: DEFAULT This is the default setting |  | This parameter specifies whether a backend should be fully utilized before sending traffic to backends with the default preference. This parameter cannot be used with regional managed instance groups and when the endpoint type of an attached network endpoint group is INTERNET_IP_PORT, INTERNET_FQDN_PORT, or SERVERLESS. PREFERENCE must be one of: DEFAULT This is the default setting. If the designated preferred backends don't have enough capacity, backends in the default category are used. Traffic is distributed between default backends based on the load balancing algorithm used. PREFERRED Backends with this preference setting are used up to their capacity limits first, while optimizing overall network latency. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-services/update-backend)

---
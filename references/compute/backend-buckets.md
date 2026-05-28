# gcloud compute backend-buckets

read and manipulate backend buckets

### `gcloud compute backend-buckets add-iam-policy-binding`

Add an IAM policy binding to a Compute Engine backend bucket

Add an IAM policy binding to a Compute Engine backend bucket.

**Synopsis:**
```
gcloud compute backend-buckets add-iam-policy-binding BACKEND_BUCKET
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend bucket resource - The backend bucket for which to add the IAM
policy to. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_bucket on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_BUCKET
     ID of the backend bucket or fully qualified identifier for the
     backend bucket.

     To set the backend_bucket attribute:
     + provide the argument backend_bucket on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of
'compute.loadBalancerServiceUser' for the user 'test-user@gmail.com' with
backend bucket 'my-backend-bucket' run:

    $ gcloud compute backend-buckets add-iam-policy-binding \
        my-backend-bucket --member='user:test-user@gmail.com' \
        --role='roles/compute.loadBalancerServiceUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/add-iam-policy-binding)

---
### `gcloud compute backend-buckets add-signed-url-key`

Add Cloud CDN Signed URL key to a backend bucket

gcloud compute backend-buckets add-signed-url-key is used to add a new
Cloud CDN Signed URL key to a backend bucket.

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
gcloud compute backend-buckets add-signed-url-key BACKEND_BUCKET_NAME
    --key-file=LOCAL_FILE_PATH --key-name=KEY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_BUCKET_NAME
   Name of the backend bucket to add CDN signed URL key to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-file` | LOCAL_FILE_PATH |  | The file containing the RFC 4648 Section 5 base64url encoded 128-bit secret key for Cloud CDN Signed URL. It is vital that the key is strongly random. One way to generate such a key is with the following command: head -c 16 /dev/random \| base64 \| tr +/ -_ > [KEY_FILE_NAME] |
| `--key-name` | KEY_NAME |  | Name of the Cloud CDN Signed URL key. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/add-signed-url-key)

---
### `gcloud compute backend-buckets create`

Create a backend bucket

gcloud compute backend-buckets create is used to create backend buckets.
Backend buckets define Google Cloud Storage buckets that can serve content.
URL maps define which requests are sent to which backend buckets.

**Synopsis:**
```
gcloud compute backend-buckets create BACKEND_BUCKET_NAME
    --gcs-bucket-name=GCS_BUCKET_NAME
    [--bypass-cache-on-request-headers=BYPASS_CACHE_ON_REQUEST_HEADERS]
    [--cache-key-include-http-header=[HEADER_FIELD_NAME,...]]
    [--cache-key-query-string-whitelist=[QUERY_STRING,...]]
    [--cache-mode=CACHE_MODE] [--client-ttl=CLIENT_TTL]
    [--compression-mode=COMPRESSION_MODE]
    [--custom-response-header=CUSTOM_RESPONSE_HEADER]
    [--default-ttl=DEFAULT_TTL] [--description=DESCRIPTION]
    [--[no-]enable-cdn] [--load-balancing-scheme=LOAD_BALANCING_SCHEME]
    [--max-ttl=MAX_TTL] [--[no-]negative-caching]
    [--negative-caching-policy=[[CODE=TTL],...]]
    [--[no-]request-coalescing] [--resource-manager-tags=[KEY=VALUE,...]]
    [--serve-while-stale=SERVE_WHILE_STALE]
    [--signed-url-cache-max-age=SIGNED_URL_CACHE_MAX_AGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_BUCKET_NAME
   Name of the backend bucket to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-bucket-name` | GCS_BUCKET_NAME |  | The name of the Google Cloud Storage bucket to serve from. The storage bucket must be in the same project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bypass-cache-on-request-headers` | BYPASS_CACHE_ON_REQUEST_HEADERS |  | Bypass the cache when the specified request headers are matched - e.g. Pragma or Authorization headers. Up to 5 headers can be specified. The cache is bypassed for all cdnPolicy.cacheMode settings. Note that requests that include these headers will always fill from origin, and may result in a large number of cache misses if the specified headers are common to many requests. Values are case-insensitive. The header name must be a valid HTTP header field token (per RFC 7230). For the list of restricted headers, see the list of required header name properties in How custom headers work (https://cloud.google.com/load-balancing/docs/custom-headers#how_custom_headers_work). A header name must not appear more than once in the list of added headers. |
| `--cache-key-include-http-header` | [HEADER_FIELD_NAME,...] |  | Specifies a comma-separated list of HTTP headers, by field name, to include in cache keys. Only the request URL is included in the cache key by default. |
| `--cache-key-query-string-whitelist` | [QUERY_STRING,...] |  | Specifies a comma-separated list of query string parameters to include in cache keys. Default parameters are always included. '&' and '=' are percent encoded and not treated as delimiters. |
| `--cache-mode` | one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS) |  | Specifies the cache setting for all responses from this backend. CACHE_MODE must be one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS). Requests and responses that are marked as uncacheable, as well as dynamic content (including HTML), aren't cached. FORCE_CACHE_ALL Cache all content, ignoring any "private", "no-store" or "no-cache" directives in Cache-Control response headers. Warning: this may result in Cloud CDN caching private, per-user (user identifiable) content. You should only enable this on backends that are not serving private or dynamic content, such as storage buckets. USE_ORIGIN_HEADERS Require the origin to set valid caching headers to cache content. Responses without these headers aren't cached at Google's edge, and require a full trip to the origin on every request, potentially impacting performance and increasing load on the origin server. |
| `--client-ttl` | CLIENT_TTL |  | Specifies a separate client (for example, browser client) TTL, separate from the TTL for Cloud CDN's edge caches. This allows you to set a shorter TTL for browsers/clients, and to have those clients revalidate content against Cloud CDN on a more regular basis, without requiring revalidation at the origin. The value of clientTtl cannot be set to a value greater than that of maxTtl, but can be equal. Any cacheable response has its max-age/s-maxage directives adjusted down to the client TTL value if necessary; an Expires header will be replaced with a suitable max-age directive. The maximum allowed value is 31,622,400s (1 year). When creating a new backend with CACHE_ALL_STATIC and the field is unset, or when switching to that mode and the field is unset, a default value of 3600 is used. When the cache mode is set to "USE_ORIGIN_HEADERS", you must omit this field. |
| `--compression-mode` | one of: DISABLED, AUTOMATIC |  | Compress text responses using Brotli or gzip compression, based on the client's Accept-Encoding header. Two modes are supported: AUTOMATIC (recommended) - automatically uses the best compression based on the Accept-Encoding header sent by the client. In most cases, this will result in Brotli compression being favored. DISABLED - disables compression. Existing compressed responses cached by Cloud CDN will not be served to clients. COMPRESSION_MODE must be one of: DISABLED, AUTOMATIC. |
| `--custom-response-header` | CUSTOM_RESPONSE_HEADER |  | Custom headers that the external Application Load Balancer adds to proxied responses. For the list of headers, see Creating custom headers (https://cloud.google.com/load-balancing/docs/custom-headers). Variables are not case-sensitive. |
| `--default-ttl` | DEFAULT_TTL |  | Specifies the default TTL for cached content served by this origin for responses that do not have an existing valid TTL (max-age or s-maxage). The default value is 3600s for cache modes that allow a default TTL to be defined. The value of defaultTtl cannot be set to a value greater than that of maxTtl, but can be equal. When the cacheMode is set to FORCE_CACHE_ALL, the defaultTtl overwrites the TTL set in all responses. A TTL of "0" means Always revalidate. The maximum allowed value is 31,622,400s (1 year). Infrequently accessed objects may be evicted from the cache before the defined TTL. When creating a new backend with CACHE_ALL_STATIC or FORCE_CACHE_ALL and the field is unset, or when updating an existing backend to use these modes and the field is unset, a default value of 3600 is used. When the cache mode is set to "USE_ORIGIN_HEADERS", you must omit this field. |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend bucket. |
| `--[no-]enable-cdn` |  |  | Enable Cloud CDN for the backend bucket. Cloud CDN can cache HTTP responses from a backend bucket at the edge of the network, close to users. Use --enable-cdn to enable and --no-enable-cdn to disable. |
| `--load-balancing-scheme` | LOAD_BALANCING_SCHEME |  | The load balancing scheme of the backend bucket. If left blank, the backend bucket will be compatible with Global External Application Load Balancer or Classic Application Load Balancer. LOAD_BALANCING_SCHEME must be (only one value is supported): INTERNAL_MANAGED. |
| `--max-ttl` | MAX_TTL |  | Specifies the maximum allowed TTL for cached content served by this origin. The default value is 86400 for cache modes that support a max TTL. Cache directives that attempt to set a max-age or s-maxage higher than this, or an Expires header more than maxTtl seconds in the future, are capped at the value of maxTtl, as if it were the value of an s-maxage Cache-Control directive. A TTL of "0" means Always revalidate. The maximum allowed value is 31,622,400s (1 year). Infrequently accessed objects may be evicted from the cache before the defined TTL. When creating a new backend with CACHE_ALL_STATIC and the field is unset, or when updating an existing backend to use these modes and the field is unset, a default value of 86400 is used. When the cache mode is set to "USE_ORIGIN_HEADERS" or "FORCE_CACHE_ALL", you must omit this field. |
| `--[no-]negative-caching` |  |  | Negative caching allows per-status code cache TTLs to be set, in order to apply fine-grained caching for common errors or redirects. This can reduce the load on your origin and improve the end-user experience by reducing response latency. Negative caching applies to a set of 3xx, 4xx, and 5xx status codes that are typically useful to cache. Status codes not listed here cannot have their TTL explicitly set and aren't cached, in order to avoid cache poisoning attacks. HTTP success codes (HTTP 2xx) are handled by the values of defaultTtl and maxTtl. When the cache mode is set to CACHE_ALL_STATIC or USE_ORIGIN_HEADERS, these values apply to responses with the specified response code that lack any cache-control or expires headers. When the cache mode is set to FORCE_CACHE_ALL, these values apply to all responses with the specified response code, and override any caching headers. Cloud CDN applies the following default TTLs to these status codes: * HTTP 300 (Multiple Choice), 301, 308 (Permanent Redirects): 10m * HTTP 404 (Not Found), 410 (Gone), 451 (Unavailable For Legal Reasons): 120s * HTTP 405 (Method Not Found), 421 (Misdirected Request), 501 (Not Implemented): 60s These defaults can be overridden in cdnPolicy.negativeCachingPolicy. Use --negative-caching to enable and --no-negative-caching to disable. |
| `--negative-caching-policy` | [[CODE=TTL],...] |  | Sets a cache TTL for the specified HTTP status code. NegativeCaching must be enabled to config the negativeCachingPolicy. If you omit the policy and leave negativeCaching enabled, Cloud CDN's default cache TTLs are used. Note that when specifying an explicit negative caching policy, make sure that you specify a cache TTL for all response codes that you want to cache. Cloud CDN doesn't apply any default negative caching when a policy exists. CODE is the HTTP status code to define a TTL against. Only HTTP status codes 300, 301, 308, 404, 405, 410, 421, 451, and 501 can be specified as values, and you cannot specify a status code more than once. TTL is the time to live (in seconds) for which to cache responses for the specified CODE. The maximum allowed value is 1800s (30 minutes), noting that infrequently accessed objects may be evicted from the cache before the defined TTL. |
| `--[no-]request-coalescing` |  |  | Enables request coalescing to the backend (recommended). Request coalescing (or collapsing) combines multiple concurrent cache fill requests into a small number of requests to the origin. This can improve performance by putting less load on the origin and backend infrastructure. However, coalescing adds a small amount of latency when multiple requests to the same URL are processed, so for latency-critical applications it may not be desirable. Defaults to true. Use --request-coalescing to enable and --no-request-coalescing to disable. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | Comma-separated list of Resource Manager tags to apply to the backend bucket. |
| `--serve-while-stale` | SERVE_WHILE_STALE |  | Serve existing content from the cache (if available) when revalidating content with the origin; this allows content to be served more quickly, and also allows content to continue to be served if the backend is down or reporting errors. This setting defines the default serve-stale duration for any cached responses that do not specify a stale-while-revalidate directive. Stale responses that exceed the TTL configured here will not be served without first being revalidated with the origin. The default limit is 86400s (1 day), which will allow stale content to be served up to this limit beyond the max-age (or s-max-age) of a cached response. The maximum allowed value is 604800 (1 week). Set this to zero (0) to disable serve-while-stale. |
| `--signed-url-cache-max-age` | SIGNED_URL_CACHE_MAX_AGE |  | The amount of time up to which the response to a signed URL request will be cached in the CDN. After this time period, the Signed URL will be revalidated before being served. Cloud CDN will internally act as though all responses from this backend had a Cache-Control: public, max-age=[TTL] header, regardless of any existing Cache-Control header. The actual headers served in responses will not be altered. If unspecified, the default value is 3600s. For example, specifying 12h will cause the responses to signed URL requests to be cached in the CDN up to 12 hours. See $ gcloud topic datetimes for information on duration formats. This flag only affects signed URL requests. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/create)

---
### `gcloud compute backend-buckets delete`

Delete backend buckets

gcloud compute backend-buckets delete deletes one or more backend buckets.

**Synopsis:**
```
gcloud compute backend-buckets delete BACKEND_BUCKET_NAME
    [BACKEND_BUCKET_NAME ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_BUCKET_NAME [BACKEND_BUCKET_NAME ...]
   Names of the backend buckets to delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/delete)

---
### `gcloud compute backend-buckets delete-signed-url-key`

Delete Cloud CDN Signed URL key from a backend bucket

gcloud compute backend-buckets delete-signed-url-key deletes an existing
Cloud CDN Signed URL key from a backend bucket.

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
gcloud compute backend-buckets delete-signed-url-key BACKEND_BUCKET_NAME
    --key-name=KEY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_BUCKET_NAME
   Name of the backend bucket to delete CDN signed URL key from.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-name` | KEY_NAME |  | Name of the Cloud CDN Signed URL key. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/delete-signed-url-key)

---
### `gcloud compute backend-buckets describe`

Describe a backend bucket

gcloud compute backend-buckets describe displays all data associated with a
backend bucket in a project.

**Synopsis:**
```
gcloud compute backend-buckets describe BACKEND_BUCKET_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_BUCKET_NAME
   Name of the backend bucket to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/describe)

---
### `gcloud compute backend-buckets get-iam-policy`

Get the IAM policy for a Compute Engine backend bucket

gcloud compute backend-buckets get-iam-policy displays the IAM policy
associated with a Compute Engine backend bucket in a project. If formatted
as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute backend-buckets get-iam-policy BACKEND_BUCKET
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend bucket resource - The network to display the IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_bucket on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_BUCKET
     ID of the backend bucket or fully qualified identifier for the
     backend bucket.

     To set the backend_bucket attribute:
     + provide the argument backend_bucket on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given backend bucket, run:

    $ gcloud compute backend-buckets get-iam-policy my-backend-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/get-iam-policy)

---
### `gcloud compute backend-buckets list`

List Google Compute Engine backend buckets

gcloud compute backend-buckets list displays all Google Compute Engine
backend buckets in a project.

**Synopsis:**
```
gcloud compute backend-buckets list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all backend buckets in a project in table form, run:

    $ gcloud compute backend-buckets list

To list the URIs of all backend buckets in a project, run:

    $ gcloud compute backend-buckets list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/list)

---
### `gcloud compute backend-buckets remove-iam-policy-binding`

Remove an IAM policy binding from a Compute Engine backend bucket

Remove an IAM policy binding from a Compute Engine backend bucket.

**Synopsis:**
```
gcloud compute backend-buckets remove-iam-policy-binding BACKEND_BUCKET
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend bucket resource - The backend bucket for which to remove the IAM
policy from. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_bucket on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_BUCKET
     ID of the backend bucket or fully qualified identifier for the
     backend bucket.

     To set the backend_bucket attribute:
     + provide the argument backend_bucket on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/compute.loadBalancerServiceUser' for the user 'test-user@gmail.com'
with backend bucket 'my-backend-bucket' run:

    $ gcloud compute backend-buckets remove-iam-policy-binding \
        my-backend-bucket --member='user:test-user@gmail.com' \
        --role='roles/compute.loadBalancerServiceUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/remove-iam-policy-binding)

---
### `gcloud compute backend-buckets set-iam-policy`

Set the IAM policy binding for a Compute Engine backend bucket

Sets the IAM policy for the given backend bucket as defined in a JSON or
YAML file.

**Synopsis:**
```
gcloud compute backend-buckets set-iam-policy BACKEND_BUCKET POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backend bucket resource - The backend bucket to set the IAM policy for.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backend_bucket on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKEND_BUCKET
     ID of the backend bucket or fully qualified identifier for the
     backend bucket.

     To set the backend_bucket attribute:
     + provide the argument backend_bucket on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file called
'policy.json' and sets it for the backend bucket called
'my-backend-bucket':

    $ gcloud compute backend-buckets set-iam-policy my-backend-bucket \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/set-iam-policy)

---
### `gcloud compute backend-buckets update`

Update a backend bucket

gcloud compute backend-buckets update is used to update backend buckets.

**Synopsis:**
```
gcloud compute backend-buckets update BACKEND_BUCKET_NAME
    [--cache-key-include-http-header=[HEADER_FIELD_NAME,...]]
    [--cache-key-query-string-whitelist=[QUERY_STRING,...]]
    [--cache-mode=CACHE_MODE] [--compression-mode=COMPRESSION_MODE]
    [--description=DESCRIPTION]
    [--edge-security-policy=EDGE_SECURITY_POLICY] [--[no-]enable-cdn]
    [--gcs-bucket-name=GCS_BUCKET_NAME] [--[no-]request-coalescing]
    [--signed-url-cache-max-age=SIGNED_URL_CACHE_MAX_AGE]
    [--bypass-cache-on-request-headers=BYPASS_CACHE_ON_REQUEST_HEADERS
      | --no-bypass-cache-on-request-headers]
    [--client-ttl=CLIENT_TTL | --no-client-ttl]
    [--custom-response-header=CUSTOM_RESPONSE_HEADER
      | --no-custom-response-headers]
    [--default-ttl=DEFAULT_TTL | --no-default-ttl]
    [--max-ttl=MAX_TTL | --no-max-ttl]
    [--[no-]negative-caching | --no-negative-caching-policies
      | --negative-caching-policy=[[CODE=TTL],...]]
    [--serve-while-stale=SERVE_WHILE_STALE | --no-serve-while-stale]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BACKEND_BUCKET_NAME
   Name of the backend bucket to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cache-key-include-http-header` | [HEADER_FIELD_NAME,...] |  | Specifies a comma-separated list of HTTP headers, by field name, to include in cache keys. Only the request URL is included in the cache key by default. |
| `--cache-key-query-string-whitelist` | [QUERY_STRING,...] |  | Specifies a comma-separated list of query string parameters to include in cache keys. Default parameters are always included. '&' and '=' are percent encoded and not treated as delimiters. |
| `--cache-mode` | one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS) |  | Specifies the cache setting for all responses from this backend. CACHE_MODE must be one of: CACHE_ALL_STATIC Automatically cache static content, including common image formats, media (video and audio), web assets (JavaScript and CSS). Requests and responses that are marked as uncacheable, as well as dynamic content (including HTML), aren't cached. FORCE_CACHE_ALL Cache all content, ignoring any "private", "no-store" or "no-cache" directives in Cache-Control response headers. Warning: this may result in Cloud CDN caching private, per-user (user identifiable) content. You should only enable this on backends that are not serving private or dynamic content, such as storage buckets. USE_ORIGIN_HEADERS Require the origin to set valid caching headers to cache content. Responses without these headers aren't cached at Google's edge, and require a full trip to the origin on every request, potentially impacting performance and increasing load on the origin server. |
| `--compression-mode` | one of: DISABLED, AUTOMATIC |  | Compress text responses using Brotli or gzip compression, based on the client's Accept-Encoding header. Two modes are supported: AUTOMATIC (recommended) - automatically uses the best compression based on the Accept-Encoding header sent by the client. In most cases, this will result in Brotli compression being favored. DISABLED - disables compression. Existing compressed responses cached by Cloud CDN will not be served to clients. COMPRESSION_MODE must be one of: DISABLED, AUTOMATIC. |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend bucket. |
| `--edge-security-policy` | EDGE_SECURITY_POLICY |  | The edge security policy that will be set for this backend bucket. To remove the policy from this backend bucket set the policy to an empty string. |
| `--[no-]enable-cdn` |  |  | Enable Cloud CDN for the backend bucket. Cloud CDN can cache HTTP responses from a backend bucket at the edge of the network, close to users. Use --enable-cdn to enable and --no-enable-cdn to disable. |
| `--gcs-bucket-name` | GCS_BUCKET_NAME |  | The name of the Google Cloud Storage bucket to serve from. The storage bucket must be in the same project. |
| `--[no-]request-coalescing` |  |  | Enables request coalescing to the backend (recommended). Request coalescing (or collapsing) combines multiple concurrent cache fill requests into a small number of requests to the origin. This can improve performance by putting less load on the origin and backend infrastructure. However, coalescing adds a small amount of latency when multiple requests to the same URL are processed, so for latency-critical applications it may not be desirable. Defaults to true. Use --request-coalescing to enable and --no-request-coalescing to disable. |
| `--signed-url-cache-max-age` | SIGNED_URL_CACHE_MAX_AGE |  | The amount of time up to which the response to a signed URL request will be cached in the CDN. After this time period, the Signed URL will be revalidated before being served. Cloud CDN will internally act as though all responses from this backend had a Cache-Control: public, max-age=[TTL] header, regardless of any existing Cache-Control header. The actual headers served in responses will not be altered. For example, specifying 12h will cause the responses to signed URL requests to be cached in the CDN up to 12 hours. See $ gcloud topic datetimes for information on duration formats. This flag only affects signed URL requests. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/backend-buckets/update)

---
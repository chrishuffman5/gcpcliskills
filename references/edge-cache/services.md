# gcloud edge-cache services

interact with and manage EdgeCacheService resources

### `gcloud edge-cache services delete`

Delete an EdgeCacheService resource

Delete an EdgeCacheService resource.

**Synopsis:**
```
gcloud edge-cache services delete (SERVICE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The EdgeCacheService resource to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an EdgeCacheService resource named 'my-service', run:

    $ gcloud edge-cache services delete my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/delete)

---
### `gcloud edge-cache services describe`

Show details about an EdgeCacheService resource

Show details about an EdgeCacheService resource.

**Synopsis:**
```
gcloud edge-cache services describe (SERVICE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The EdgeCacheService resource you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Examples:**
```bash
To show details about an EdgeCacheService resource named 'my-service', run:

    $ gcloud edge-cache services describe my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/describe)

---
### `gcloud edge-cache services export`

Export an EdgeCacheService resource

Export an EdgeCacheService resource to YAML.

**Synopsis:**
```
gcloud edge-cache services export (SERVICE : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The EdgeCacheService resource you want to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export an existing EdgeCacheService resource named 'my-service', run:

    $ gcloud edge-cache services export my-service \
        --destination=my-service.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/export)

---
### `gcloud edge-cache services import`

Import an EdgeCacheService resource

Import an EdgeCacheService resource. If the named EdgeCacheService resource
already exists, the resource will be updated to match the imported resource
configuration.

If the named EdgeCacheService resource does not already exist, a new
EdgeCacheService resource will be created with that name.

**Synopsis:**
```
gcloud edge-cache services import (SERVICE : --location=LOCATION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The EdgeCacheService resource you want to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import an EdgeCacheService resource named 'my-service' from a YAML file,
run:

    $ gcloud edge-cache services import my-service \
        --source=my-service.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/import)

---
### `gcloud edge-cache services invalidate-cache`

Invalidate the cache for an EdgeCacheService resource

Invalidate the cache entries associated with an EdgeCacheService resource.

**Synopsis:**
```
gcloud edge-cache services invalidate-cache (SERVICE : --location=LOCATION)
    (--host=HOST --path=PATH --tags=[TAGS,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The EdgeCacheService resource you want to invalidate
the cache for. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host` | HOST |  | _[At least one of these must be specified:]_ The hostname to invalidate against. You can specify an exact or wildcard host - e.g. "video.example.com" or ".example.com" - based on host component. |
| `--path` | PATH |  | _[At least one of these must be specified:]_ The path to invalidate against. You can specify an exact or wildcard host - e.g. "/videos/hls/139123.mp4" or "/manifests/" - based on path component. |
| `--tags` | [TAGS,...] |  | _[At least one of these must be specified:]_ A list of cache tags used to identify cached objects. + Cache tags are specified when the response is first cached, by setting the "Cache-Tag" response header at the origin. + By default, all objects have a cache tag representing the HTTP status code of the response, the MIME content-type, and the origin. + Multiple cache tags in the same revalidation request are treated as boolean OR - e.g. tag1 OR tag2 OR tag3. + If a host and/or path are also specified, these are treated as boolean AND with any tags. Up to 10 tags may be specified in a single invalidation request. |


**Examples:**
```bash
To invalidate content via a tag, or tags for a given host for an
EdgeCacheService named 'my-service':

    $ gcloud edge-cache services invalidate-cache my-service \
        --tags="status=404" --host="media.example.com"

To invalidate all content under a specific path, specify an exact path, or
a prefix. Prefixes are denoted with a trailing * character.

    $ gcloud edge-cache services invalidate-cache my-service \
        --path="/static/*"

You can optionally combine this with a status code. For example, to
invalidate all cached HTTP 404s:

    $ gcloud edge-cache services invalidate-cache my-service \
        --tags="status=404" --path="/static/*"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/invalidate-cache)

---
### `gcloud edge-cache services list`

List all EdgeCacheService resources in a project

List EdgeCacheService resources.

**Synopsis:**
```
gcloud edge-cache services list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list existing EdgeCacheService resources, run:

    $ gcloud edge-cache services list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/list)

---
### `gcloud edge-cache services update`

Update an EdgeCacheService resource

Update an existing EdgeCacheService resource.

**Synopsis:**
```
gcloud edge-cache services update (SERVICE : --location=LOCATION) [--async]
    [--description=DESCRIPTION]
    [--edge-security-policy=EDGE_SECURITY_POLICY]
    [--edge-ssl-certificate=[EDGE_SSL_CERTIFICATE,...]] [--enable-logging]
    [--labels=[KEY=VALUE,...]] [--logging-sample-rate=LOGGING_SAMPLE_RATE]
    [--require-tls] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The name of the EdgeCacheService resource to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + use global location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Human-readable description of the resource. |
| `--edge-security-policy` | EDGE_SECURITY_POLICY |  | Resource URL that points at the Cloud Armor edge security policy that is applied on each request against the EdgeCacheService. Security Policies should be specified as relative resource URLs - for example projects/my-project/locations/global/securityPolicies/my-policy Note that only security policies with a type of EDGE can be attached to an EdgeCacheService. |
| `--edge-ssl-certificate` | [EDGE_SSL_CERTIFICATE,...] |  | URLs to sslCertificate resources that are used to authenticate connections between users and the EdgeCacheService. Certificates should be specified as relative resource URLs - for example projects/my-project/locations/global/certificates/my-cert Note that only "global" certificates with a "scope" of EDGE_CACHE can be attached to an EdgeCacheService. You may specify up to 5 SSL certificates per Service. |
| `--enable-logging` |  |  | Specifies whether to enable logging for traffic served by this service. Defaults to false. |
| `--labels` | [KEY=VALUE,...] |  | List of KEY=VALUE labels to attach to this resource. |
| `--logging-sample-rate` | LOGGING_SAMPLE_RATE |  | Configures the sampling rate of requests, where 1.0 means all logged requests are reported and 0.0 means no logged requests are reported. The default value is 1.0, and the value of the field must be in [0, 1]. This field can only be specified if logging is enabled for this service. |
| `--require-tls` |  |  | Require TLS (HTTPS) for all clients connecting to this service. Clients who connect over HTTP (port 80) will receive a HTTP 301 to the same URL over HTTPS (port 443). You must have at least one (1) edgeSslCertificate specified to enable this. |


**Examples:**
```bash
To update an EdgeCacheService resource called 'my-service' run:

    $ gcloud edge-cache services update my-service \
        --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cache/services/update)

---
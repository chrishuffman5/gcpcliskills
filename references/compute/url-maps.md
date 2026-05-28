# gcloud compute url-maps

list, create, and delete URL maps

### `gcloud compute url-maps add-host-rule`

Add a rule to a URL map to map hosts to a path matcher

gcloud compute url-maps add-host-rule is used to add a mapping of hosts to
a path matcher in a URL map. The mapping will match the host component of
HTTP requests to path matchers which in turn map the request to a backend
service. Before adding a host rule, at least one path matcher must exist in
the URL map to take care of the path component of the requests. gcloud
compute url-maps add-path-matcher or gcloud compute url-maps edit can be
used to add path matchers.

**Synopsis:**
```
gcloud compute url-maps add-host-rule URL_MAP --hosts=HOST,[HOST,...]
    --path-matcher-name=PATH_MATCHER_NAME [--description=DESCRIPTION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hosts` | HOST,[HOST,...] |  | The set of hosts to match requests against. Each host must be a fully qualified domain name (FQDN) with the exception that the host can begin with a ``*'' or ``*-''. ``*'' acts as a glob and will match any string of atoms to the left where an atom is separated by dots (``.'') or dashes (``-''). |
| `--path-matcher-name` | PATH_MATCHER_NAME |  | The name of the path matcher to use if a request matches this host rule. The path matcher must already exist in the URL map (see gcloud compute url-maps add-path-matcher). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the host rule. |


**Examples:**
```bash
To create a host rule mapping the *-foo.example.com and example.com hosts
to the www path matcher, run:

    $ gcloud compute url-maps add-host-rule MY-URL-MAP \
        --hosts='*-foo.example.com,example.com' --path-matcher-name=www
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/add-host-rule)

---
### `gcloud compute url-maps add-path-matcher`

Add a path matcher to a URL map

gcloud compute url-maps add-path-matcher is used to add a path matcher to a
URL map. A path matcher maps HTTP request paths to backend services or
backend buckets. Each path matcher must be referenced by at least one host
rule. This command can create a new host rule through the --new-hosts flag
or it can reconfigure an existing host rule to point to the newly added
path matcher using --existing-host. In the latter case, if a path matcher
is orphaned as a result of the operation, this command will fail unless
--delete-orphaned-path-matcher is provided. Path matcher constraints can be
found here
(https://cloud.google.com/load-balancing/docs/url-map-concepts#pm-constraints).

**Synopsis:**
```
gcloud compute url-maps add-path-matcher URL_MAP
    --path-matcher-name=PATH_MATCHER_NAME
    (--default-backend-bucket=DEFAULT_BACKEND_BUCKET
      | --default-service=DEFAULT_SERVICE)
    [--backend-bucket-path-rules=PATH=BUCKET,[PATH=BUCKET,...]]
    [--backend-service-path-rules=PATH=SERVICE,[...]]
    [--delete-orphaned-path-matcher] [--description=DESCRIPTION]
    [--path-rules=PATH=SERVICE,[...]]
    [--existing-host=EXISTING_HOST | --new-hosts=NEW_HOST,[NEW_HOST,...]]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--path-matcher-name` | PATH_MATCHER_NAME |  | The name to assign to the path matcher. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-bucket-path-rules` | PATH=BUCKET,[PATH=BUCKET,...] |  | Rules for mapping request paths to backend buckets. |
| `--backend-service-path-rules` | PATH=SERVICE,[...] |  | Rules for mapping request paths to services. |
| `--delete-orphaned-path-matcher` |  |  | If provided and a path matcher is orphaned as a result of this command, the command removes the orphaned path matcher instead of failing. |
| `--description` | DESCRIPTION |  | An optional, textual description for the path matcher. |
| `--path-rules` | PATH=SERVICE,[...] |  | Rules for mapping request paths to services. |


**Examples:**
```bash
To create a rule for mapping the path /search/* to the hypothetical
search-service, /static/* to the static-bucket backend bucket and /images/*
to the images-service under the hosts example.com and *.example.com, run:

    $ gcloud compute url-maps add-path-matcher MY-URL-MAP \
        --path-matcher-name=MY-MATCHER \
        --default-service=MY-DEFAULT-SERVICE \
        --backend-service-path-rules='/search/*=search_service,/images/*\
    =images-service' \
        --backend-bucket-path-rules='/static/*=static-bucket' \
        --new-hosts=example.com '*.example.com'

Note that a default service or default backend bucket must be provided to
handle paths for which there is no mapping.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/add-path-matcher)

---
### `gcloud compute url-maps create`

Create a URL map

gcloud compute url-maps create is used to create URL maps which map HTTP
and HTTPS request URLs to backend services and backend buckets. Mappings
are done using a longest-match strategy.

There are two components to a mapping: a host rule and a path matcher. A
host rule maps one or more hosts to a path matcher. A path matcher maps
request paths to backend services or backend buckets. For example, a host
rule can map the hosts *.google.com and google.com to a path matcher called
www. The www path matcher in turn can map the path /search/* to the search
backend service, the path /static/* to the static backend bucket and
everything else to a default backend service or default backend bucket.

Host rules and patch matchers can be added to the URL map after the map is
created by using gcloud compute url-maps edit or by using gcloud compute
url-maps add-path-matcher and gcloud compute url-maps add-host-rule.

**Synopsis:**
```
gcloud compute url-maps create URL_MAP
    (--default-backend-bucket=DEFAULT_BACKEND_BUCKET
      | --default-service=DEFAULT_SERVICE) [--description=DESCRIPTION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--default-backend-bucket` | DEFAULT_BACKEND_BUCKET |  | _[Exactly one of these must be specified:]_ A backend bucket that will be used for requests for which this URL map has no mappings. Exactly one of --default-service or --default-backend-bucket is required. |
| `--default-service` | DEFAULT_SERVICE |  | _[Exactly one of these must be specified:]_ A backend service that will be used for requests for which this URL map has no mappings. Exactly one of --default-service or --default-backend-bucket is required. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the URL map. |


**Examples:**
```bash
To create a global URL map with a default service, run:

    $ gcloud compute url-maps create URL_MAP_NAME \
        --default-service=BACKEND_SERVICE_NAME

To create a regional URL map with a default service, run:

    $ gcloud compute url-maps create URL_MAP_NAME \
        --default-service=BACKEND_SERVICE_NAME --region=REGION_NAME

To create a global URL map with a default backend bucket, run:

    $ gcloud compute url-maps create URL_MAP_NAME \
        --default-backend-bucket=BACKEND_BUCKET_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/create)

---
### `gcloud compute url-maps delete`

Delete URL maps

gcloud compute url-maps delete deletes one or more URL maps.

**Synopsis:**
```
gcloud compute url-maps delete URL_MAP [URL_MAP ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP [URL_MAP ...]
   Names of the URL maps to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the URL maps are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the URL maps to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/delete)

---
### `gcloud compute url-maps describe`

Describe a URL map

gcloud compute url-maps describe displays all data associated with a URL
map in a project.

**Synopsis:**
```
gcloud compute url-maps describe URL_MAP [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the URL map is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the URL map to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/describe)

---
### `gcloud compute url-maps edit`

Modify URL maps

gcloud compute url-maps edit can be used to modify a URL map. The URL map
resource is fetched from the server and presented in a text editor. After
the file is saved and closed, this command will update the resource. Only
fields that can be modified are displayed in the editor.

The editor used to modify the resource is chosen by inspecting the EDITOR
environment variable.

**Synopsis:**
```
gcloud compute url-maps edit URL_MAP [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the URL map is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the URL map to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/edit)

---
### `gcloud compute url-maps export`

Export a URL map

Exports a URL map's configuration to a file. This configuration can be
imported at a later time.

**Synopsis:**
```
gcloud compute url-maps export URL_MAP [--destination=DESTINATION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\UrlMap.yaml. |


**Examples:**
```bash
A URL map can be exported by running:

    $ gcloud compute url-maps export NAME --destination=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/export)

---
### `gcloud compute url-maps import`

Import a URL map

Imports a URL map's configuration from a file.

**Synopsis:**
```
gcloud compute url-maps import URL_MAP [--source=SOURCE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to import.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\UrlMap.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
A URL map can be imported by running:

    $ gcloud compute url-maps import NAME --source=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/import)

---
### `gcloud compute url-maps invalidate-cdn-cache`

Invalidate specified objects for a URL map in Cloud CDN caches

gcloud compute url-maps invalidate-cdn-cache requests that Cloud CDN stop
using cached content for resources at a particular URL path or set of URL
paths.

gcloud compute url-maps invalidate-cdn-cache may succeed even if no content
is cached for some or all URLs with the given path.

**Synopsis:**
```
gcloud compute url-maps invalidate-cdn-cache URLMAP [--async] [--global]
    [--host=HOST] [--path=PATH] [--tags=TAGS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLMAP
   Name of the URL map to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--global` |  |  | (Default) The URL map is global. Regional URL maps are not supported. |
| `--host` | HOST |  | If set, this invalidation will apply only to requests to the specified host. |
| `--path` | PATH |  | A path specifying which objects to invalidate. PATH must start with ``/'' and the only place a ``*'' is allowed is at the end following a ``/''. It will be matched against URL paths, which do not include scheme, host, or any text after the first ``?'' or ``#'' (and those characters are not allowed here). For example, for the URL https://example.com/whatever/x.html?a=b, the path is /whatever/x.html. If PATH ends with ``*'', the preceding string is a prefix, and all URLs whose paths begin with it will be invalidated. If PATH doesn't end with ``*'', then only URLs with exactly that path will be invalidated. Examples: * ``'', ``*'', anything that doesn't start with ``/'': error * ``/'': just the root URL * ``/*'': everything * ``/x/y'': ``/x/y'' only (and not ``/x/y/'') * ``/x/y/'': ``/x/y/'' only (and not ``/x/y'') * ``/x/y/*'': ``/x/y/'' and everything under it |
| `--tags` | TAGS |  | A single tag or a comma-delimited list of tags. When multiple tags are specified, the invalidation applies them using boolean OR logic. Example: * --tags=abcd,user123 |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/invalidate-cdn-cache)

---
### `gcloud compute url-maps list`

List Google Compute Engine URL maps

gcloud compute url-maps list displays all Google Compute Engine URL maps in
a project.

By default, global URL maps and URL maps from all regions are listed. The
results can be narrowed down by providing the --global or --regions flag.

**Synopsis:**
```
gcloud compute url-maps list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--global | --regions=[REGION,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
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
To list all URL maps in a project in table form, run:

    $ gcloud compute url-maps list

To list the URIs of all URL maps in a project, run:

    $ gcloud compute url-maps list --uri

To list all global URL maps in a project, run:

    $ gcloud compute url-maps list --global

To list all URL maps in the us-central1 and europe-west1 regions, given
they are regional resources, run:

    $ gcloud compute url-maps list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/list)

---
### `gcloud compute url-maps list-cdn-cache-invalidations`

List Cloud CDN cache invalidations for a URL map

List Cloud CDN cache invalidations for a URL map. A cache invalidation
instructs Cloud CDN to stop using cached content. You can list
invalidations to check which have completed.

**Synopsis:**
```
gcloud compute url-maps list-cdn-cache-invalidations URL_MAP [--global]
    [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | (Default) The URL map is global. Regional URL maps are not supported. |
| `--limit` | LIMIT |  | The maximum number of invalidations to list. This has an upper limit of 1000. For more results, use Cloud Logging. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/list-cdn-cache-invalidations)

---
### `gcloud compute url-maps remove-host-rule`

Remove a host rule from a URL map

gcloud compute url-maps remove-host-rule is used to remove a host rule from
a URL map. When a host rule is removed, its path matcher is only removed if
it is not referenced by any other host rules and
--delete-orphaned-path-matcher is provided.

**Synopsis:**
```
gcloud compute url-maps remove-host-rule URL_MAP --host=HOST
    [--delete-orphaned-path-matcher] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--host` | HOST |  | One of the hosts in the host rule to remove. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delete-orphaned-path-matcher` |  |  | If provided and a path matcher is orphaned as a result of this command, the command removes the orphaned path matcher instead of failing. |


**Examples:**
```bash
To remove a host rule that contains the host example.com from the URL map
named MY-URL-MAP, you can use this command:

    $ gcloud compute url-maps remove-host-rule MY-URL-MAP \
        --host=example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/remove-host-rule)

---
### `gcloud compute url-maps remove-path-matcher`

Remove a path matcher from a URL map

gcloud compute url-maps remove-path-matcher is used to remove a path
matcher from a URL map. When a path matcher is removed, all host rules that
refer to the path matcher are also removed.

**Synopsis:**
```
gcloud compute url-maps remove-path-matcher URL_MAP
    --path-matcher-name=PATH_MATCHER_NAME [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--path-matcher-name` | PATH_MATCHER_NAME |  | The name of the path matcher to remove. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the URL map is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the URL map to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To remove the path matcher named MY-MATCHER from the URL map named
MY-URL-MAP, you can use this command:

    $ gcloud compute url-maps remove-path-matcher MY-URL-MAP \
        --path-matcher-name=MY-MATCHER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/remove-path-matcher)

---
### `gcloud compute url-maps set-default-service`

Change the default service or default bucket of a URL map

gcloud compute url-maps set-default-service is used to change the default
service or default bucket of a URL map. The default service or default
bucket is used for any requests for which there is no mapping in the URL
map.

**Synopsis:**
```
gcloud compute url-maps set-default-service URL_MAP
    (--default-backend-bucket=DEFAULT_BACKEND_BUCKET
      | --default-service=DEFAULT_SERVICE) [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL_MAP
   Name of the URL map to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--default-backend-bucket` | DEFAULT_BACKEND_BUCKET |  | _[Exactly one of these must be specified:]_ A backend bucket that will be used for requests for which this URL map has no mappings. |
| `--default-service` | DEFAULT_SERVICE |  | _[Exactly one of these must be specified:]_ A backend service that will be used for requests for which this URL map has no mappings. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the URL map is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the URL map to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/set-default-service)

---
### `gcloud compute url-maps validate`

Validate a URL map

Runs static validation for the UrlMap. In particular, the tests of the
provided UrlMap will be run. Calling this method does NOT create or update
the UrlMap.

**Synopsis:**
```
gcloud compute url-maps validate
    [--load-balancing-scheme=LOAD_BALANCING_SCHEME] [--source=SOURCE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--load-balancing-scheme` | one of: EXTERNAL, EXTERNAL_MANAGED |  | Specifies the load balancer type this validation request is for. Use EXTERNAL_MANAGED for global external Application Load Balancer. Use EXTERNAL for classic Application Load Balancer. Other load balancer types are not supported. For more information, refer to Choosing a load balancer (https://cloud.google.com/load-balancing/docs/choosing-load-balancer/). If unspecified, the load balancing scheme will be inferred from the backend service resources this URL map references. If that can not be inferred (for example, this URL map only references backend buckets, or this URL map is for rewrites and redirects only and doesn't reference any backends), EXTERNAL will be used as the default type. If specified, the scheme must not conflict with the load balancing scheme of the backend service resources this URL map references. LOAD_BALANCING_SCHEME must be one of: EXTERNAL, EXTERNAL_MANAGED. |
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\UrlMap.yaml. |


**Examples:**
```bash
A URL map can be validated by running:

    $ gcloud compute url-maps validate --source=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/url-maps/validate)

---
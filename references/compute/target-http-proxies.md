# gcloud compute target-http-proxies

list, create, and delete target HTTP proxies

### `gcloud compute target-http-proxies create`

Create a target HTTP proxy

gcloud compute target-http-proxies create is used to create target HTTP
proxies. A target HTTP proxy is referenced by one or more forwarding rules
which specify the network traffic that the proxy is responsible for
routing. The target HTTP proxy points to a URL map that defines the rules
for routing the requests. The URL map's job is to map URLs to backend
services which handle the actual requests.

**Synopsis:**
```
gcloud compute target-http-proxies create NAME --url-map=URL_MAP
    [--description=DESCRIPTION]
    [--http-keep-alive-timeout-sec=HTTP_KEEP_ALIVE_TIMEOUT_SEC]
    [--global | --region=REGION]
    [--global-url-map | --url-map-region=URL_MAP_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTP proxy to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--url-map` | URL_MAP |  | A reference to a URL map resource. A URL map defines the mapping of URLs to backend services. Before you can refer to a URL map, you must create the URL map. To delete a URL map that a target proxy is referring to, you must first delete the target HTTP proxy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the target HTTP proxy. |
| `--http-keep-alive-timeout-sec` | HTTP_KEEP_ALIVE_TIMEOUT_SEC |  | Represents the maximum amount of time that a TCP connection can be idle between the (downstream) client and the target HTTP proxy. If an HTTP keepalive timeout is not specified, the default value is 610 seconds. For global external Application Load Balancers, the minimum allowed value is 5 seconds and the maximum allowed value is 1200 seconds. |


**Examples:**
```bash
If there is an already-created URL map with the name URL_MAP, create a
global target HTTP proxy pointing to this map by running:

    $ gcloud compute target-http-proxies create PROXY_NAME \
        --url-map=URL_MAP

Create a regional target HTTP proxy by running:

    $ gcloud compute target-http-proxies create PROXY_NAME \
        --url-map=URL_MAP --region=REGION_NAME

To create a proxy with a textual description, run:

    $ gcloud compute target-http-proxies create PROXY_NAME \
        --url-map=URL_MAP --description="default proxy"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/create)

---
### `gcloud compute target-http-proxies delete`

Delete target HTTP proxies

gcloud compute target-http-proxies delete deletes one or more target HTTP
proxies.

**Synopsis:**
```
gcloud compute target-http-proxies delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target HTTP proxies to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target HTTP proxies are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target HTTP proxies to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
Delete a global target HTTP proxy by running:

    $ gcloud compute target-http-proxies delete PROXY_NAME

Delete a regional target HTTP proxy by running:

    $ gcloud compute target-http-proxies delete PROXY_NAME \
        --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/delete)

---
### `gcloud compute target-http-proxies describe`

Display detailed information about a target HTTP proxy

gcloud compute target-http-proxies describe displays all data associated
with a target HTTP proxy in a project.

**Synopsis:**
```
gcloud compute target-http-proxies describe NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTP proxy to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target HTTP proxy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target HTTP proxy to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe a global target HTTP proxy, run:

    $ gcloud compute target-http-proxies describe PROXY_NAME

To describe a regional target HTTP proxy, run:

    $ gcloud compute target-http-proxies describe PROXY_NAME \
        --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/describe)

---
### `gcloud compute target-http-proxies export`

Export a target HTTP proxy

Exports a target HTTP proxy's configuration to a file. This configuration
can be imported at a later time.

**Synopsis:**
```
gcloud compute target-http-proxies export NAME [--destination=DESTINATION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTP proxy to export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\TargetHttpProxy.yaml. |


**Examples:**
```bash
A target HTTP proxy can be exported by running:

    $ gcloud compute target-http-proxies export NAME \
        --destination=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/export)

---
### `gcloud compute target-http-proxies import`

Import a target HTTP proxy

Imports a target HTTP proxy's configuration from a file.

**Synopsis:**
```
gcloud compute target-http-proxies import NAME [--source=SOURCE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTP proxy to import.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\TargetHttpProxy.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
A target HTTP proxy can be imported by running:

    $ gcloud compute target-http-proxies import NAME \
        --source=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/import)

---
### `gcloud compute target-http-proxies list`

List Google Compute Engine target HTTP proxies

gcloud compute target-http-proxies list displays all Google Compute Engine
target HTTP proxies in a project.

By default, global target HTTP proxies and target HTTP proxies from all
regions are listed. The results can be narrowed down by providing the
--global or --regions flag.

**Synopsis:**
```
gcloud compute target-http-proxies list [NAME ...]
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
To list all target HTTP proxies in a project in table form, run:

    $ gcloud compute target-http-proxies list

To list the URIs of all target HTTP proxies in a project, run:

    $ gcloud compute target-http-proxies list --uri

To list all global target HTTP proxies in a project, run:

    $ gcloud compute target-http-proxies list --global

To list all target HTTP proxies in the us-central1 and europe-west1
regions, given they are regional resources, run:

    $ gcloud compute target-http-proxies list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/list)

---
### `gcloud compute target-http-proxies update`

Update a target HTTP proxy

gcloud compute target-http-proxies update is used to change the URL map of
existing target HTTP proxies. A target HTTP proxy is referenced by one or
more forwarding rules which specify the network traffic that the proxy is
responsible for routing. The target HTTP proxy points to a URL map that
defines the rules for routing the requests. The URL map's job is to map
URLs to backend services which handle the actual requests.

**Synopsis:**
```
gcloud compute target-http-proxies update NAME --url-map=URL_MAP
    [--clear-http-keep-alive-timeout-sec
      | --http-keep-alive-timeout-sec=HTTP_KEEP_ALIVE_TIMEOUT_SEC]
    [--global | --region=REGION]
    [--global-url-map | --url-map-region=URL_MAP_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target HTTP proxy to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--url-map` | URL_MAP |  | A reference to a URL map resource. A URL map defines the mapping of URLs to backend services. Before you can refer to a URL map, you must create the URL map. To delete a URL map that a target proxy is referring to, you must first delete the target HTTP proxy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clear-http-keep-alive-timeout-sec` |  |  | _[At most one of these can be specified:]_ Clears the previously configured HTTP keepalive timeout. |
| `--http-keep-alive-timeout-sec` | HTTP_KEEP_ALIVE_TIMEOUT_SEC |  | _[At most one of these can be specified:]_ Represents the maximum amount of time that a TCP connection can be idle between the (downstream) client and the target HTTP proxy. If an HTTP keepalive timeout is not specified, the default value is 610 seconds. For global external Application Load Balancers, the minimum allowed value is 5 seconds and the maximum allowed value is 1200 seconds. |
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target HTTP proxy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target HTTP proxy to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--global-url-map` |  |  | _[At most one of these can be specified:]_ If set, the URL map is global. |
| `--url-map-region` | URL_MAP_REGION |  | _[At most one of these can be specified:]_ Region of the URL map to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
If there is an already-created URL map with the name URL_MAP, update a
global target HTTP proxy pointing to this map by running:

    $ gcloud compute target-http-proxies update PROXY_NAME \
        --url-map=URL_MAP

Update a regional target HTTP proxy by running:

    $ gcloud compute target-http-proxies update PROXY_NAME \
        --url-map=URL_MAP --region=REGION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-http-proxies/update)

---
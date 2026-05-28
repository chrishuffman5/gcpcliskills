# gcloud compute target-grpc-proxies

manage Compute Engine target gRPC proxy resources

### `gcloud compute target-grpc-proxies create`

Create a target gRPC proxy

gcloud compute target-grpc-proxies create is used to create target gRPC
proxies. A target gRPC proxy is a component of load balancers intended for
load balancing gRPC traffic. Global forwarding rules reference a target
gRPC proxy. The Target gRPC proxy references a URL map which specifies how
traffic routes to gRPC backend services.

**Synopsis:**
```
gcloud compute target-grpc-proxies create NAME --url-map=URL_MAP
    [--description=DESCRIPTION] [--validate-for-proxyless]
    [--global-url-map | --url-map-region=URL_MAP_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target gRPC proxy to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--url-map` | URL_MAP |  | A reference to a URL map resource. A URL map defines the mapping of URLs to backend services. Before you can refer to a URL map, you must create the URL map. To delete a URL map that a target proxy is referring to, you must first delete the target gRPC proxy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the target gRPC proxy. |
| `--validate-for-proxyless` |  |  | If specified, configuration in the associated urlMap and the BackendServices is checked to allow only the features that are supported in the latest release of gRPC. If unspecified, no such configuration checks are performed. This may cause unexpected behavior in gRPC applications if unsupported features are configured. |


**Examples:**
```bash
If there is an already-created URL map with the name URL_MAP, create a
global target gRPC proxy pointing to this map by running:

    $ gcloud compute target-grpc-proxies create PROXY_NAME \
        --url-map=URL_MAP

To create a proxy with a textual description, run:

    $ gcloud compute target-grpc-proxies create PROXY_NAME \
        --url-map=URL_MAP --description="default proxy"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-grpc-proxies/create)

---
### `gcloud compute target-grpc-proxies delete`

Delete one or more target gRPC proxy

gcloud compute target-grpc-proxies delete deletes one or more target gRPC
proxies.

**Synopsis:**
```
gcloud compute target-grpc-proxies delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target gRPC proxies to delete.
```

**Examples:**
```bash
Delete a global target gRPC proxy by running:

    $ gcloud compute target-grpc-proxies delete PROXY_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-grpc-proxies/delete)

---
### `gcloud compute target-grpc-proxies describe`

Display detailed information about a target gRPC proxy

gcloud compute target-grpc-proxies describe displays all data associated
with a Compute Engine target gRPC proxy.

**Synopsis:**
```
gcloud compute target-grpc-proxies describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target gRPC proxy to describe.
```

**Examples:**
```bash
To describe a global target gRPC proxy, run:

    $ gcloud compute target-grpc-proxies describe PROXY_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-grpc-proxies/describe)

---
### `gcloud compute target-grpc-proxies list`

List Google Compute Engine target gRPC proxies

gcloud compute target-grpc-proxies list displays all Google Compute Engine
target gRPC proxies in a project.

**Synopsis:**
```
gcloud compute target-grpc-proxies list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
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
To list all target gRPC proxies in a project in table form, run:

    $ gcloud compute target-grpc-proxies list

To list the URIs of all target gRPC proxies in a project, run:

    $ gcloud compute target-grpc-proxies list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-grpc-proxies/list)

---
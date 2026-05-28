# gcloud compute target-tcp-proxies

list, create, and delete target TCP proxies

### `gcloud compute target-tcp-proxies create`

Create a target TCP proxy

gcloud compute target-tcp-proxies create is used to create target TCP
proxies. A target TCP proxy is referenced by one or more forwarding rules
which define which packets the proxy is responsible for routing. The target
TCP proxy points to a backend service which handle the actual requests.

**Synopsis:**
```
gcloud compute target-tcp-proxies create NAME
    --backend-service=BACKEND_SERVICE [--description=DESCRIPTION]
    [--[no-]proxy-bind] [--proxy-header=PROXY_HEADER; default="NONE"]
    [--backend-service-region=BACKEND_SERVICE_REGION
      | --global-backend-service] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target TCP proxy to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-service` | BACKEND_SERVICE |  | A backend service that will be used for connections to the target TCP proxy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the target TCP proxy. |
| `--[no-]proxy-bind` |  |  | This field only applies when the forwarding rule that references this target proxy has a --load-balancing-scheme set to INTERNAL_SELF_MANAGED. When this field is set to true, Envoy proxies set up inbound traffic interception and bind to the IP address and port specified in the forwarding rule. This is generally useful when using Traffic Director to configure Envoy as a gateway or middle proxy (in other words, not a sidecar proxy). The Envoy proxy listens for inbound requests and handles requests when it receives them. Use --proxy-bind to enable and --no-proxy-bind to disable. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Enables PROXY protocol (version 1) for passing client connection information. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-tcp-proxies/create)

---
### `gcloud compute target-tcp-proxies delete`

Delete target TCP proxies

gcloud compute target-tcp-proxies delete deletes one or more target TCP
proxies.

**Synopsis:**
```
gcloud compute target-tcp-proxies delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target TCP proxies to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target TCP proxies are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target TCP proxies to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-tcp-proxies/delete)

---
### `gcloud compute target-tcp-proxies describe`

Display detailed information about a target TCP proxy

gcloud compute target-tcp-proxies describe displays all data associated
with a target TCP proxy in a project.

**Synopsis:**
```
gcloud compute target-tcp-proxies describe NAME
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target TCP proxy to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the target TCP proxy is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the target TCP proxy to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-tcp-proxies/describe)

---
### `gcloud compute target-tcp-proxies list`

List Google Compute Engine target TCP proxies

gcloud compute target-tcp-proxies list displays all Google Compute Engine
target TCP proxies in a project.

By default, global target TCP proxies and target TCP proxies from all
regions are listed. The results can be narrowed down by providing the
--global or --regions flag.

**Synopsis:**
```
gcloud compute target-tcp-proxies list [NAME ...]
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
To list all target TCP proxies in a project in table form, run:

    $ gcloud compute target-tcp-proxies list

To list the URIs of all target TCP proxies in a project, run:

    $ gcloud compute target-tcp-proxies list --uri

To list all global target TCP proxies in a project, run:

    $ gcloud compute target-tcp-proxies list --global

To list all target TCP proxies in the us-central1 and europe-west1 regions,
given they are regional resources, run:

    $ gcloud compute target-tcp-proxies list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-tcp-proxies/list)

---
### `gcloud compute target-tcp-proxies update`

Update a target TCP proxy

gcloud compute target-tcp-proxies update is used to change the backend
service or proxy header of existing target TCP proxies. A target TCP proxy
is referenced by one or more forwarding rules which define which packets
the proxy is responsible for routing. The target TCP proxy in turn points
to a backend service which will handle the requests.

**Synopsis:**
```
gcloud compute target-tcp-proxies update NAME
    [--backend-service=BACKEND_SERVICE] [--proxy-header=PROXY_HEADER]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target TCP proxy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-service` | BACKEND_SERVICE |  | A backend service that will be used for connections to the target TCP proxy. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Enables PROXY protocol (version 1) for passing client connection information. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-tcp-proxies/update)

---
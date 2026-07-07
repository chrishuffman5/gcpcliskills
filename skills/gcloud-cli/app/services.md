# gcloud app services

view and manage your App Engine services

### `gcloud app services browse`

Open the specified service(s) in a browser

Open the specified service(s) in a browser.

**Synopsis:**
```
gcloud app services browse SERVICES [SERVICES ...] [--no-launch-browser]
    [--version=VERSION, -v VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICES [SERVICES ...]
   The services to open (optionally filtered by the --version flag).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--launch-browser` |  |  | Launch a browser if possible. When disabled, only displays the URL. Enabled by default, use --no-launch-browser to disable. |
| `--version` | VERSION, -v VERSION |  | If specified, open services with a given version. If not specified, use a version based on the service's traffic split . |


**Examples:**
```bash
To show the url for the default service in the browser, run:

    $ gcloud app services browse default

To show version v1 of service myService in the browser, run:

    $ gcloud app services browse myService --version="v1"

To show multiple services side-by-side, run:

    $ gcloud app services browse default otherService

To show multiple services side-by-side with a specific version, run:

    $ gcloud app services browse s1 s2 --version=v1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/services/browse)

---
### `gcloud app services delete`

Delete services in the current project

Delete services in the current project.

**Synopsis:**
```
gcloud app services delete SERVICES [SERVICES ...] [--version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICES [SERVICES ...]
   The service(s) to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Delete a specific version of the given service(s). |


**Examples:**
```bash
To delete a service (and all of its accompanying versions) in the current
project, run:

    $ gcloud app services delete service1

To delete multiple services (and all of their accompanying versions) in the
current project, run:

    $ gcloud app services delete service1 service2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/services/delete)

---
### `gcloud app services describe`

Display all data about an existing service

Display all data about an existing service.

**Synopsis:**
```
gcloud app services describe SERVICE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   The service to describe.
```

**Examples:**
```bash
To show all the data about service s1, run

    $ gcloud app services describe s1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/services/describe)

---
### `gcloud app services list`

List your existing services

This command lists all services that are currently deployed to the App
Engine server.

**Synopsis:**
```
gcloud app services list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all services in the current project, run:

    $ gcloud app services list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/services/list)

---
### `gcloud app services set-traffic`

Set traffic splitting settings

This command sets the traffic split of versions across a service or a
project.

**Synopsis:**
```
gcloud app services set-traffic [SERVICES ...] --splits=SPLITS,[SPLITS,...]
    [--migrate] [--split-by=SPLIT_BY; default="ip"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SERVICES ...]
   The services to modify.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--splits` | SPLITS,[SPLITS,...] |  | Key-value pairs describing what proportion of traffic should go to each version. The split values are added together and used as weights. The exact values do not matter, only their relation to each other. For example, v1=2,v2=2 is equivalent to v1=.5,v2=.5 |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--migrate` |  |  | The migrate flag determines whether or not to use traffic migration during the operation. Traffic migration will attempt to automatically migrate traffic from the previous version to the new version, giving the autoscaler time to respond. See the documentation here: https://cloud.google.com/appengine/docs/python/console/trafficmigration for more information. |
| `--split-by` | one of: cookie, ip, random | ip | Whether to split traffic based on cookie, IP address or random. SPLIT_BY must be one of: cookie, ip, random. |


**Examples:**
```bash
To send all traffic to 'v2' of service 's1', run:

    $ gcloud app services set-traffic s1 --splits=v2=1

To split traffic evenly between 'v1' and 'v2' of service 's1', run:

    $ gcloud app services set-traffic s1 --splits=v2=.5,v1=.5

To split traffic across all services:

    $ gcloud app services set-traffic --splits=v2=.5,v1=.5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/services/set-traffic)

---
### `gcloud app services update`

Update service-level settings

Update ingress traffic settings for an app.

**Synopsis:**
```
gcloud app services update [SERVICES ...] --ingress=INGRESS
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SERVICES ...]
   The services to modify.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ingress` | one of: all, internal-only, internal-and-cloud-load-balancing |  | Control what traffic can reach the app. INGRESS must be one of: all, internal-only, internal-and-cloud-load-balancing. |


**Examples:**
```bash
To update ingress traffic settings for the default service, run:

    $ gcloud app services update default --ingress=internal-only
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/services/update)

---
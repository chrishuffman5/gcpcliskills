# gcloud compute https-health-checks

read and manipulate HTTPS health checks for load balanced instances

### `gcloud compute https-health-checks create`

Create a legacy HTTPS health check

Though you can use legacy HTTPS health checks in certain Google Cloud
Platform load balancing configurations and for managed instance group
autohealing, you should consider a non-legacy HTTPS health check created
with health-checks create https instead.

For more information about the differences between legacy and non-legacy
health checks see:
https://cloud.google.com/load-balancing/docs/health-check-concepts#category_and_protocol

For information about what type of health check to use for a particular
load balancer, see:
https://cloud.google.com/load-balancing/docs/health-check-concepts#lb_guide

**Synopsis:**
```
gcloud compute https-health-checks create NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2] [--host=HOST]
    [--port=PORT; default=443] [--request-path=REQUEST_PATH; default="/"]
    [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
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
| `--description` | DESCRIPTION |  | An optional, textual description for the HTTPS health check. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--host` | HOST |  | The value of the host header used in this HTTPS health check request. By default, this is empty and Compute Engine automatically sets the host header in health requests to the same external IP address as the forwarding rule associated with the target pool. |
| `--port` | PORT | 443 | The TCP port number that this health check monitors. The default value is 443. |
| `--request-path` | REQUEST_PATH | / | The request path that this health check monitors. For example, /healthcheck. The default value is ``/''. |
| `--timeout` | TIMEOUT | 5s | If Compute Engine doesn't receive an HTTPS 200 response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/https-health-checks/create)

---
### `gcloud compute https-health-checks delete`

Delete HTTPS health checks

gcloud compute https-health-checks delete deletes one or more Compute
Engine HTTPS health checks.

**Synopsis:**
```
gcloud compute https-health-checks delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the HTTPS health checks to delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/https-health-checks/delete)

---
### `gcloud compute https-health-checks describe`

Display detailed information about an HTTPS health check

gcloud compute https-health-checks describe displays all data associated
with a Google Compute Engine HTTPS health check in a project.

**Synopsis:**
```
gcloud compute https-health-checks describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTPS health check to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/https-health-checks/describe)

---
### `gcloud compute https-health-checks list`

List Google Compute Engine HTTPS health checks

gcloud compute https-health-checks list displays all Google Compute Engine
HTTPS health checks in a project.

**Synopsis:**
```
gcloud compute https-health-checks list [NAME ...]
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
To list all HTTPS health checks in a project in table form, run:

    $ gcloud compute https-health-checks list

To list the URIs of all HTTPS health checks in a project, run:

    $ gcloud compute https-health-checks list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/https-health-checks/list)

---
### `gcloud compute https-health-checks update`

Update a legacy HTTPS health check

gcloud compute https-health-checks update is used to update an existing
legacy HTTPS health check. Only arguments passed in will be updated on the
health check. Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute https-health-checks update NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--healthy-threshold=HEALTHY_THRESHOLD] [--host=HOST] [--port=PORT]
    [--request-path=REQUEST_PATH] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD] [GCLOUD_WIDE_FLAG ...]
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
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--host` | HOST |  | The value of the host header used in this HTTPS health check request. By default, this is empty and Compute Engine automatically sets the host header in health requests to the same external IP address as the forwarding rule associated with the target pool. Setting this to an empty string will clear any existing host value. |
| `--port` | PORT |  | The TCP port number that this health check monitors. |
| `--request-path` | REQUEST_PATH |  | The request path that this health check monitors. For example, /healthcheck. |
| `--timeout` | TIMEOUT |  | If Compute Engine doesn't receive an HTTPS 200 response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/https-health-checks/update)

---
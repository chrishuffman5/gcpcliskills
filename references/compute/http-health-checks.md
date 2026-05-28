# gcloud compute http-health-checks

read and manipulate HTTP health checks for load balanced instances

### `gcloud compute http-health-checks create`

Create a legacy HTTP health check

Legacy HTTP health checks are required if you want to implement health
checking for a target pool backend of an external passthrough Network Load
Balancer. Though you can use legacy HTTP health checks in certain other
Google Cloud Platform load balancing configurations and for managed
instance group autohealing, you should consider a non-legacy HTTP health
check created with health-checks create http instead.

For more information about the differences between legacy and non-legacy
health checks see:
https://cloud.google.com/load-balancing/docs/health-check-concepts#category_and_protocol

For information about what type of health check to use for a particular
load balancer, see:
https://cloud.google.com/load-balancing/docs/health-check-concepts#lb_guide

**Synopsis:**
```
gcloud compute http-health-checks create NAME
    [--check-interval=CHECK_INTERVAL; default="5s"]
    [--description=DESCRIPTION]
    [--healthy-threshold=HEALTHY_THRESHOLD; default=2] [--host=HOST]
    [--port=PORT; default=80] [--request-path=REQUEST_PATH; default="/"]
    [--timeout=TIMEOUT; default="5s"]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD; default=2]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP health check to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL | 5s | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | An optional, textual description for the HTTP health check. |
| `--healthy-threshold` | HEALTHY_THRESHOLD | 2 | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. The default is 2. |
| `--host` | HOST |  | The value of the host header used in this HTTP health check request. By default, this is empty and Compute Engine automatically sets the host header in health requests to the same external IP address as the forwarding rule associated with the target pool. |
| `--port` | PORT | 80 | The TCP port number that this health check monitors. The default value is 80. |
| `--request-path` | REQUEST_PATH | / | The request path that this health check monitors. For example, /healthcheck. The default value is ``/''. |
| `--timeout` | TIMEOUT | 5s | If Compute Engine doesn't receive an HTTP 200 response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. The default value is 5s. See $ gcloud topic datetimes for information on duration formats. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD | 2 | The number of consecutive health check failures before a healthy instance is marked as unhealthy. The default is 2. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/http-health-checks/create)

---
### `gcloud compute http-health-checks delete`

Delete HTTP health checks

gcloud compute http-health-checks delete deletes one or more Compute Engine
HTTP health checks.

**Synopsis:**
```
gcloud compute http-health-checks delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the HTTP health checks to delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/http-health-checks/delete)

---
### `gcloud compute http-health-checks describe`

Display detailed information about an HTTP health check

gcloud compute http-health-checks describe displays all data associated
with a Google Compute Engine HTTP health check in a project.

**Synopsis:**
```
gcloud compute http-health-checks describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP health check to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/http-health-checks/describe)

---
### `gcloud compute http-health-checks list`

List Google Compute Engine health checks

gcloud compute http-health-checks list displays all Google Compute Engine
health checks in a project.

**Synopsis:**
```
gcloud compute http-health-checks list [NAME ...]
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
To list all health checks in a project in table form, run:

    $ gcloud compute http-health-checks list

To list the URIs of all health checks in a project, run:

    $ gcloud compute http-health-checks list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/http-health-checks/list)

---
### `gcloud compute http-health-checks update`

Update a legacy HTTP health check

gcloud compute http-health-checks update is used to update an existing
legacy HTTP health check. Only arguments passed in will be updated on the
health check. Other attributes will remain unaffected.

**Synopsis:**
```
gcloud compute http-health-checks update NAME
    [--check-interval=CHECK_INTERVAL] [--description=DESCRIPTION]
    [--healthy-threshold=HEALTHY_THRESHOLD] [--host=HOST] [--port=PORT]
    [--request-path=REQUEST_PATH] [--timeout=TIMEOUT]
    [--unhealthy-threshold=UNHEALTHY_THRESHOLD] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the HTTP health check to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--check-interval` | CHECK_INTERVAL |  | How often to perform a health check for an instance. For example, specifying 10s will run the check every 10 seconds. See $ gcloud topic datetimes for information on duration formats. |
| `--description` | DESCRIPTION |  | A textual description for the HTTP health check. Pass in an empty string to unset. |
| `--healthy-threshold` | HEALTHY_THRESHOLD |  | The number of consecutive successful health checks before an unhealthy instance is marked as healthy. |
| `--host` | HOST |  | The value of the host header used in this HTTP health check request. By default, this is empty and Compute Engine automatically sets the host header in health requests to the same external IP address as the forwarding rule associated with the target pool. Setting this to an empty string will clear any existing host value. |
| `--port` | PORT |  | The TCP port number that this health check monitors. |
| `--request-path` | REQUEST_PATH |  | The request path that this health check monitors. For example, /healthcheck. |
| `--timeout` | TIMEOUT |  | If Compute Engine doesn't receive an HTTP 200 response from the instance by the time specified by the value of this flag, the health check request is considered a failure. For example, specifying 10s will cause the check to wait for 10 seconds before considering the request a failure. Valid units for this flag are ``s'' for seconds and ``m'' for minutes. |
| `--unhealthy-threshold` | UNHEALTHY_THRESHOLD |  | The number of consecutive health check failures before a healthy instance is marked as unhealthy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/http-health-checks/update)

---
# gcloud app versions

view and manage your App Engine versions

### `gcloud app versions browse`

Open the specified versions in a browser

Open the specified versions in a browser.

**Synopsis:**
```
gcloud app versions browse VERSIONS [VERSIONS ...] [--no-launch-browser]
    [--service=SERVICE, -s SERVICE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSIONS [VERSIONS ...]
   The versions to open (optionally filtered by the --service flag).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--launch-browser` |  |  | Launch a browser if possible. When disabled, only displays the URL. Enabled by default, use --no-launch-browser to disable. |
| `--service` | SERVICE, -s SERVICE |  | If specified, only open versions from the given service. If not specified, use the default service. |


**Examples:**
```bash
To show version v1 for the default service in the browser, run:

    $ gcloud app versions browse v1

To show version v1 of a specific service in the browser, run:

    $ gcloud app versions browse v1 --service="myService"

To show multiple versions side-by-side, run:

    $ gcloud app versions browse v1 v2 --service="myService"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/browse)

---
### `gcloud app versions delete`

Delete a specified version

You cannot delete a version of a service that is currently receiving
traffic.

**Synopsis:**
```
gcloud app versions delete VERSIONS [VERSIONS ...]
    [--service=SERVICE, -s SERVICE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSIONS [VERSIONS ...]
   The versions to delete (optionally filtered by the --service flag).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only delete versions from the given service. |


**Examples:**
```bash
To delete a specific version of a specific service, run:

    $ gcloud app versions delete --service=myService v1

To delete a named version across all services, run:

    $ gcloud app versions delete v1

To delete multiple versions of a specific service, run:

    $ gcloud app versions delete --service=myService v1 v2

To delete multiple named versions across all services, run:

    $ gcloud app versions delete v1 v2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/delete)

---
### `gcloud app versions describe`

Display all data about an existing version

Display all data about an existing version.

**Synopsis:**
```
gcloud app versions describe VERSION --service=SERVICE, -s SERVICE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   The ID of the version to show.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | The service corresponding to the version to show. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/describe)

---
### `gcloud app versions list`

List your existing versions

This command lists all the versions of all services that are currently
deployed to the App Engine server.

**Synopsis:**
```
gcloud app versions list [--hide-no-traffic]
    [--service=SERVICE, -s SERVICE] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hide-no-traffic` |  |  | Only show versions that are receiving traffic. |
| `--service` | SERVICE, -s SERVICE |  | Only show versions from this service. |


**Examples:**
```bash
To list all services and versions, run:

    $ gcloud app versions list

To list all versions for a specific service, run:

    $ gcloud app versions list --service=service1

To list only versions that are receiving traffic, run:

    $ gcloud app versions list --hide-no-traffic

To list all version information in JSON, run:

    $ gcloud app versions list --format="json"

To list versions created after a specific date, run:

    $ gcloud app versions list \
        --filter="version.createTime.date('%Y-%m-%d', Z)>'2017-11-03'"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/list)

---
### `gcloud app versions migrate`

Migrate traffic from one version to another for a set of services

Migrate traffic from one version to another for a set of services.

**Synopsis:**
```
gcloud app versions migrate VERSION [--service=SERVICE, -s SERVICE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   The version to migrate to.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only migrate versions from the given service. |


**Examples:**
```bash
This only works for automatically scaled Standard versions. To migrate from
one version to another for all services where there is a version v2 and
shut down the previous version, run:

    $ gcloud app versions migrate v2

To migrate from one version to another for a specific service, run:

    $ gcloud app versions migrate v2 --service="s1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/migrate)

---
### `gcloud app versions start`

Start serving specified versions

This command starts serving the specified versions. It may only be used if
the scaling module for your service has been set to manual.

**Synopsis:**
```
gcloud app versions start VERSIONS [VERSIONS ...]
    [--service=SERVICE, -s SERVICE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSIONS [VERSIONS ...]
   The versions to start. (optionally filtered by the --service flag).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only start versions from the given service. |


**Examples:**
```bash
To start a specific version across all services, run:

    $ gcloud app versions start v1

To start multiple named versions across all services, run:

    $ gcloud app versions start v1 v2

To start a single version on a single service, run:

    $ gcloud app versions start --service=servicename v1

To start multiple versions in a single service, run:

    $ gcloud app versions start --service=servicename v1 v2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/start)

---
### `gcloud app versions stop`

Stop serving specified versions

This command stops serving the specified versions. It may only be used if
the scaling module for your service has been set to manual.

**Synopsis:**
```
gcloud app versions stop VERSIONS [VERSIONS ...]
    [--service=SERVICE, -s SERVICE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSIONS [VERSIONS ...]
   The versions to stop (optionally filtered by the --service flag).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE, -s SERVICE |  | If specified, only stop versions from the given service. |


**Examples:**
```bash
To stop a specific version across all services, run:

    $ gcloud app versions stop v1

To stop multiple named versions across all services, run:

    $ gcloud app versions stop v1 v2

To stop a single version on a single service, run:

    $ gcloud app versions stop --service=servicename v1

To stop multiple versions in a single service, run:

    $ gcloud app versions stop --service=servicename v1 v2

Note that that last example may be more simply written using the services
stop command (see its documentation for details).
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/versions/stop)

---
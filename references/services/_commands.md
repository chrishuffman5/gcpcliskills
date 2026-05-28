# gcloud services (top-level commands)

### `gcloud services disable`

Disable a service for consumption for a project

This command disables one or more previously-enabled services for
consumption.

To see a list of the enabled services for a project, run:

    $ gcloud services list

More information on listing services can be found at:
https://cloud.google.com/service-usage/docs/list-services and on disabling
a service at: https://cloud.google.com/service-usage/docs/enable-disable

**Synopsis:**
```
gcloud services disable SERVICE [SERVICE ...] [--async] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE [SERVICE ...]
   The name of the service(s) to disable.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If specified, the disable call will proceed even if there are enabled services which depend on the service to be disabled or disable the service used in last 30 days or was enabled in recent 3 days. Forcing the call means that the services which depend on the service to be disabled will also be disabled. |


**Examples:**
```bash
To disable a service called my-consumed-service for the active project,
run:

    $ gcloud services disable my-consumed-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud services disable my-consumed-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/disable)

---
### `gcloud services enable`

Enables a service for consumption for a project

This command enables a service for consumption for a project.

    To see a list of available services for a project, run:

    $ gcloud services list --available

More information on listing services can be found at:
https://cloud.google.com/service-usage/docs/list-services and on disabling
a service at: https://cloud.google.com/service-usage/docs/enable-disable

**Synopsis:**
```
gcloud services enable SERVICE [SERVICE ...] [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE [SERVICE ...]
   The name of the service(s) to enable.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enable a service called my-consumed-service on the current project, run:

    $ gcloud services enable my-consumed-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud services enable my-consumed-service --async

To enable services called service1, service2, and service3 on the current
project, run:

    $ gcloud services enable service1 service2 service3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/enable)

---
### `gcloud services list`

List services for a project

This command lists the services that are enabled or available to be enabled
by a project. You can choose the mode in which the command will list
services by using exactly one of the --enabled or --available flags.
--enabled is the default.

**Synopsis:**
```
gcloud services list [--available | --enabled] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=200]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--available` |  |  | _[At most one of these can be specified:]_ Return the services available to the project to enable. This list will include any services that the project has already enabled. |
| `--enabled` |  |  | _[At most one of these can be specified:]_ (DEFAULT) Return the services which the project has enabled. |


**Examples:**
```bash
To list the services for the current project has enabled for consumption,
run:

    $ gcloud services list --enabled

To list the services for the current project can enable for consumption,
run:

    $ gcloud services list --available

To list the services for project my-project has enabled for consumption,
run:

    $ gcloud services list --enabled --project=my-project

To list the services the project my-project can enable for consumption,
run:

    $ gcloud services list --available --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/list)

---
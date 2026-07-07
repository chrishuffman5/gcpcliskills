# gcloud endpoints configs

view configurations for various services

### `gcloud endpoints configs describe`

Describes the configuration for a given version of a service

This command prints out the configuration for the given version of a given
service. You specify the name of the service and the ID of the
configuration, and the command will print out the specified config.

**Synopsis:**
```
gcloud endpoints configs describe CONFIG_ID [--service=SERVICE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONFIG_ID
   The configuration ID to retrieve.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | The name of the service from which to retrieve the configuration.. |


**Examples:**
```bash
To print the configuration with ID 2017-01-01R0 for the service called
my-service, run:

    $ gcloud endpoints configs describe --service=my-service 2017-01-01R0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/configs/describe)

---
### `gcloud endpoints configs list`

Lists the configurations for a given service

This command lists all the configurations for a given service by ID.

To get more detailed information about a specific configuration, run:

    $ gcloud endpoints configs describe

**Synopsis:**
```
gcloud endpoints configs list --service=SERVICE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | The name of service for which to list existing configurations. |


**Examples:**
```bash
To list the configurations for a service named my-service, run:

    $ gcloud endpoints configs list --service=my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/endpoints/configs/list)

---
# gcloud backup-dr service-config

manage Backup and DR Service configuration

### `gcloud backup-dr service-config init`

Initialize a Backup and DR Service configuration

Initialize a Backup and DR Service configuration.

**Synopsis:**
```
gcloud backup-dr service-config init --location=LOCATION
    --resource-type=RESOURCE_TYPE [--no-async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--resource-type` | RESOURCE_TYPE |  | _[This must be specified.]_ The resource type to which the default service configuration will be applied. Examples include, "compute.<UNIVERSE_DOMAIN>.com/Instance" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Wait for the operation in progress to complete. |


**Examples:**
```bash
To initialize a new service configuration in location MY_LOCATION and
project MY_PROJECT for resource type MY_RESOURCE_TYPE, run:

    $ gcloud backup-dr service-config init --project=MY_PROJECT \
        --location=MY_LOCATION --resource-type=MY_RESOURCE_TYPE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/service-config/init)

---
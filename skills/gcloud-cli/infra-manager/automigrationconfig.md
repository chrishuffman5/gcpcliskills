# gcloud infra-manager automigrationconfig

manage auto migration config resources

### `gcloud infra-manager automigrationconfig describe`

Describe an AutoMigrationConfig

Describe an AutoMigrationConfig.

**Synopsis:**
```
gcloud infra-manager automigrationconfig describe [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To describe an AutoMigrationConfig for location us-central1:        $ gcloud infra-manager automigrationconfig describe \
       --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/automigrationconfig/describe)

---
### `gcloud infra-manager automigrationconfig disable-auto-migration`

Disable AutoMigrationConfig

Disable AutoMigrationConfig.

**Synopsis:**
```
gcloud infra-manager automigrationconfig disable-auto-migration [--async]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To disable AutoMigrationConfig for location us-central1:        $ gcloud infra-manager automigrationconfig disable-auto-migration \
       --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/automigrationconfig/disable-auto-migration)

---
### `gcloud infra-manager automigrationconfig enable-auto-migration`

Enable AutoMigrationConfig

Enable AutoMigrationConfig.

**Synopsis:**
```
gcloud infra-manager automigrationconfig enable-auto-migration [--async]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enable AutoMigrationConfig for location us-central1:        $ gcloud infra-manager automigrationconfig enable-auto-migration \
       --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/automigrationconfig/enable-auto-migration)

---
# gcloud recommender insight-type-config

manage Cloud resource insight type configuration

### `gcloud recommender insight-type-config describe`

Describe an insight type configuration

Describe an insight type configuration based on a given entity (project,
organization, billing account), location, and insight type.

**Synopsis:**
```
gcloud recommender insight-type-config describe INSIGHT_TYPE
    --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSIGHT_TYPE
   Insight type to use for this invocation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location to use for this invocation. |


**Examples:**
```bash
To describe an insight type configuration, run:

    $ gcloud recommender insight-type-config describe ${INSIGHT_TYPE} \
        --project=${PROJECT} --location=${LOCATION}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/insight-type-config/describe)

---
### `gcloud recommender insight-type-config update`

Update an insight type configuration

Update an insight type configuration based on a given entity (project,
organization, billing account), location, and insight type.

**Synopsis:**
```
gcloud recommender insight-type-config update INSIGHT_TYPE --etag=ETAG
    --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--annotations=KEY=VALUE,[KEY=VALUE,...]]
    [--config-file=CONFIG_FILE] [--display-name=DISPLAY_NAME]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSIGHT_TYPE
   Insight type to use for this invocation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag of the insight type configuration. |
| `--location` | LOCATION |  | Location to use for this invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | KEY=VALUE,[KEY=VALUE,...] |  | Store small amounts of arbitrary data on the insight type configuration. |
| `--config-file` | CONFIG_FILE |  | Generation configuration file for the insight type configuration. |
| `--display-name` | DISPLAY_NAME |  | Display name of the insight type configuration. |
| `--validate-only` |  |  | If true, validate the request and preview the change, but do not actually update it. |


**Examples:**
```bash
To update an insight type configuration, run:

    $ gcloud recommender insight-type-config update ${INSIGHT_TYPE} \
         --project=${PROJECT} --location=${LOCATION} --etag=\"123\" \
         --config-file=config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/insight-type-config/update)

---
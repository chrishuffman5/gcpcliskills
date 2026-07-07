# gcloud recommender recommender-config

manage Cloud resource recommender configuration

### `gcloud recommender recommender-config describe`

Describe a recommender configuration

Describe a recommender configuration based on a given entity (project,
organization, billing account), location, and recommender.

**Synopsis:**
```
gcloud recommender recommender-config describe RECOMMENDER
    --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDER
   Recommender to use for this invocation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location to use for this invocation. |


**Examples:**
```bash
To describe a recommender configuration, run:

    $ gcloud recommender recommender-config describe ${RECOMMENDER} \
        --project=${PROJECT} --location=${LOCATION}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommender-config/describe)

---
### `gcloud recommender recommender-config update`

Update a recommender configuration

Update a recommender configuration based on a given entity (project,
organization, billing account), location, and recommender.

**Synopsis:**
```
gcloud recommender recommender-config update RECOMMENDER --etag=ETAG
    --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--annotations=KEY=VALUE,[KEY=VALUE,...]]
    [--config-file=CONFIG_FILE] [--display-name=DISPLAY_NAME]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDER
   Recommender to use for this invocation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag of the recommender configuration. |
| `--location` | LOCATION |  | Location to use for this invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | KEY=VALUE,[KEY=VALUE,...] |  | Store small amounts of arbitrary data on the recommender configuration. |
| `--config-file` | CONFIG_FILE |  | Generation configuration file for the recommender configuration. |
| `--display-name` | DISPLAY_NAME |  | Display name of the recommender configuration. |
| `--validate-only` |  |  | If true, validate the request and preview the change, but do not actually update it. |


**Examples:**
```bash
To update a recommender configuration, run:

    $ gcloud recommender recommender-config update ${RECOMMENDER} \
         --project=${PROJECT} --location=${LOCATION} --etag=\"123\" \
         --config-file=config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommender-config/update)

---
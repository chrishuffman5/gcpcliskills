# gcloud recommender insights

manage Cloud resource insights

### `gcloud recommender insights describe`

Describe an insight

Describe an insight. This currently supports the following parent entities:
project, billing account, folder, and organization.

**Synopsis:**
```
gcloud recommender insights describe INSIGHT --insight-type=INSIGHT_TYPE
    --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSIGHT
   insight to describe
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--insight-type` | INSIGHT_TYPE |  | Insight type to describe insights |
| `--location` | LOCATION |  | Location |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Examples:**
```bash
To describe an insight:

    $ gcloud recommender insights describe \
        --insight-type=${INSIGHT_TYPE} --project=${PROJECT} \
        --location=${LOCATION}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/insights/describe)

---
### `gcloud recommender insights list`

List insights for a Google Cloud entity

This command lists all insights for a given Google Cloud entity, location,
and insight type. Supported insight-types can be found here:
https://cloud.google.com/recommender/docs/insights/insight-types. Currently
the following Google Cloud entity types are supported: project,
billing_account, folder, and organization.

**Synopsis:**
```
gcloud recommender insights list --insight-type=INSIGHT_TYPE
    --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--insight-type` | INSIGHT_TYPE |  | Insight type to list insights for. Supported insight-types can be found here: https://cloud.google.com/recommender/docs/insights/insight-types |
| `--location` | LOCATION |  | Location to list insights for. |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Examples:**
```bash
To list all insights for a billing account:

    $ gcloud recommender insights list --project=project-id \
        --location=global --insight-type=google.compute.firewall.Insight
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/insights/list)

---
### `gcloud recommender insights mark-accepted`

Mark an insight's state as ACCEPTED

Mark an insight's state as ACCEPTED. Can be applied to insights in ACTIVE
or ACCEPTED state. The following are currently supported: project,
billing_account, folder, and organization.

**Synopsis:**
```
gcloud recommender insights mark-accepted INSIGHT --etag=etag
    --insight-type=INSIGHT_TYPE --location=LOCATION
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--state-metadata=KEY=VALUE,[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSIGHT
   Insight id which will be marked as accepted
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | etag |  | Etag of a insight |
| `--insight-type` | INSIGHT_TYPE |  | Insight Type of the insights |
| `--location` | LOCATION |  | Location |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--state-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | State metadata for recommendation, in format of --state-metadata=key1=value1,key2=value2 |


**Examples:**
```bash
To mark an insight as ACCEPTED:

    $ gcloud recommender insights mark-accepted abcd-1234 \
        --project=project-id --location=global \
        --insight-type=google.compute.firewall.Insight --etag=abc123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/insights/mark-accepted)

---
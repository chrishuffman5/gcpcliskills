# gcloud recommender recommendations

manage Cloud resource recommendations

### `gcloud recommender recommendations describe`

Describe a recommendation for a Cloud project

Describe a recommendation. This currently supports the following parent
entities: project, billing account, folder, and organization.

**Synopsis:**
```
gcloud recommender recommendations describe RECOMMENDATION
    --location=LOCATION --recommender=RECOMMENDER
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDATION
   Recommendation to describe
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location |
| `--recommender` | RECOMMENDER |  | Recommender of the recommendations |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Examples:**
```bash
To describe a recommendation:

    $ gcloud recommender recommendations describe RECOMMENDATION_ID \
         --project=${PROJECT} --location=${LOCATION} \
         --recommender=${RECOMMENDER}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommendations/describe)

---
### `gcloud recommender recommendations list`

List operations for a recommendation

This command lists all recommendations for a given Google Cloud entity ID,
location, and recommender. Supported recommenders can be found here:
https://cloud.google.com/recommender/docs/recommenders. The following
Google Cloud entity types are supported: project, billing_account, folder
and organization.

**Synopsis:**
```
gcloud recommender recommendations list --location=LOCATION
    --recommender=RECOMMENDER
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location to list recommendations for. |
| `--recommender` | RECOMMENDER |  | Recommender to list recommendations for. Supported recommenders can be found here: https://cloud.google.com/recommender/docs/recommenders. |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Examples:**
```bash
Lists recommendations for a Cloud project.        $ gcloud recommender recommendations list --project=project-id \
        --location=global \
        --recommender=google.compute.instance.MachineTypeRecommender
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommendations/list)

---
### `gcloud recommender recommendations mark-claimed`

Mark a recommendation's state as CLAIMED

Mark a recommendation's state as CLAIMED. Can be applied to recommendations
in CLAIMED, SUCCEEDED, FAILED, or ACTIVE state. Users can use this method
to indicate to the Recommender API that they are starting to apply the
recommendation themselves. This stops the recommendation content from being
updated.

**Synopsis:**
```
gcloud recommender recommendations mark-claimed RECOMMENDATION --etag=ETAG
    --location=LOCATION --recommender=RECOMMENDER
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--state-metadata=KEY=VALUE,[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDATION
   Recommendation id which will be marked as claimed
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag of a recommendation |
| `--location` | LOCATION |  | Location |
| `--recommender` | RECOMMENDER |  | Recommender of recommendation |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--state-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | State metadata for recommendation, in format of --state-metadata=key1=value1,key2=value2 |


**Examples:**
```bash
To mark a recommendation as CLAIMED:

    $ gcloud recommender recommendations mark-claimed abcd-1234 \
        --project=project-id --location=global \
        --recommender=google.compute.instance.MachineTypeRecommender \
        --etag=abc123 --state-metadata=key1=value1,key2=value2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommendations/mark-claimed)

---
### `gcloud recommender recommendations mark-dismissed`

Mark recommendation's state as DISMISSED

Mark recommendation's state as DISMISSED. Can be applied to recommendations
in ACTIVE state. The following parent resources are supported: project,
billing account, folder, and organization as parent resources for
recommendations.

**Synopsis:**
```
gcloud recommender recommendations mark-dismissed RECOMMENDATION
    --etag=ETAG --location=LOCATION --recommender=RECOMMENDER
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDATION
   Recommendation ID which will be marked as dismissed
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag of a recommendation |
| `--location` | LOCATION |  | Location |
| `--recommender` | RECOMMENDER |  | Recommender of the recommendations |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Examples:**
```bash
To mark a recommendation as DISMISSED:

    $ gcloud recommender recommendations mark-dismissed abcd-1234 \
        --project=project-id --location=global \
        --recommender=google.compute.instance.MachineTypeRecommender \
        --etag=abc123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommendations/mark-dismissed)

---
### `gcloud recommender recommendations mark-failed`

Mark a recommendation's state as FAILED

Mark a recommendation's state as FAILED. Can be applied to recommendations
in ACTIVE, CLAIMED, SUCCEEDED, or FAILED state.

**Synopsis:**
```
gcloud recommender recommendations mark-failed RECOMMENDATION --etag=ETAG
    --location=LOCATION --recommender=RECOMMENDER
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--state-metadata=KEY=VALUE,[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDATION
   Recommendation id which will be marked as FAILED.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag of a recommendation. |
| `--location` | LOCATION |  | Location. |
| `--recommender` | RECOMMENDER |  | Recommender of recommendation. |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--state-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | State metadata for recommendation, in format of --state-metadata=key1=value1,key2=value2 |


**Examples:**
```bash
To mark a recommendation as FAILED:

    $ gcloud recommender recommendations mark-failed abcd-1234 \
        --project=project-id --location=global \
        --recommender=google.compute.instance.MachineTypeRecommender \
        --etag=abc123 --state-metadata=key1=value1,key2=value2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommendations/mark-failed)

---
### `gcloud recommender recommendations mark-succeeded`

Mark a recommendation's state as SUCCEEDED

Mark a recommendation's state as SUCCEEDED. Can be applied to
recommendations in ACTIVE, CLAIMED, SUCCEEDED, or FAILED state.

**Synopsis:**
```
gcloud recommender recommendations mark-succeeded RECOMMENDATION
    --etag=ETAG --location=LOCATION --recommender=RECOMMENDER
    (--billing-account=BILLING_ACCOUNT | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID)
    [--state-metadata=KEY=VALUE,[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RECOMMENDATION
   Recommendation id which will be marked as succeeded
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag of a recommendation |
| `--location` | LOCATION |  | Location |
| `--recommender` | RECOMMENDER |  | Recommender of recommendation |
| `--folder, --organization` |  |  | _[mutually exclusive flags are supported, --project, --billing-account,]_ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--state-metadata` | KEY=VALUE,[KEY=VALUE,...] |  | State metadata for recommendation, in format of --state-metadata=key1=value1,key2=value2 |


**Examples:**
```bash
To mark a recommendation as SUCCEEDED:

    $ gcloud recommender recommendations mark-succeeded abcd-1234 \
        --project=project-id --location=global \
        --recommender=google.compute.instance.MachineTypeRecommender \
        --etag=abc123 --state-metadata=key1=value1,key2=value2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recommender/recommendations/mark-succeeded)

---
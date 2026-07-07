# gcloud ai tensorboards

manage Vertex AI Tensorboards

### `gcloud ai tensorboards create`

Create a new Vertex AI Tensorboard

Create a new Vertex AI Tensorboard.

**Synopsis:**
```
gcloud ai tensorboards create --display-name=DISPLAY_NAME
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--region=REGION]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the tensorboard. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the tensorboard. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Tensorboard with the display name my tensorboard:

    $ gcloud ai tensorboards create --display-name="my tensorboard"

You may also provide a description:

    $ gcloud ai tensorboards create --description="my description"

You may also provide labels:

    $ gcloud ai tensorboards create --labels="label1=value1" \
      --labels="label2=value2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/tensorboards/create)

---
### `gcloud ai tensorboards delete`

Delete an existing Vertex AI Tensorboard

Delete an existing Vertex AI Tensorboard.

**Synopsis:**
```
gcloud ai tensorboards delete (TENSORBOARD : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tensorboard resource - The tensorboard to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tensorboard on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TENSORBOARD
     ID of the tensorboard or fully qualified identifier for the
     tensorboard.

     To set the name attribute:
     + provide the argument tensorboard on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the tensorboard.

     To set the region attribute:
     + provide the argument tensorboard on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To delete a Tensorboard 12345 in region us-central1 and project my-project:

    $ gcloud ai tensorboards delete \
      projects/my-project/locations/us-central1/tensorboards/12345

Or with flags:

    $ gcloud ai tensorboards delete 12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/tensorboards/delete)

---
### `gcloud ai tensorboards describe`

Gets detailed Tensorboard information about the given Tensorboard id

Gets detailed Tensorboard information about the given Tensorboard id.

**Synopsis:**
```
gcloud ai tensorboards describe (TENSORBOARD : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tensorboard resource - The tensorboard to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tensorboard on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TENSORBOARD
     ID of the tensorboard or fully qualified identifier for the
     tensorboard.

     To set the name attribute:
     + provide the argument tensorboard on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the tensorboard.

     To set the region attribute:
     + provide the argument tensorboard on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To describe a Tensorboard 12345 in region us-central1 and project
my-project:

    $ gcloud ai tensorboards describe \
      projects/my-project/locations/us-central1/tensorboards/12345

Or with flags:

    $ gcloud ai tensorboards describe 12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/tensorboards/describe)

---
### `gcloud ai tensorboards list`

Lists the Tensorboards of the given project and region

Lists the Tensorboards of the given project and region.

**Synopsis:**
```
gcloud ai tensorboards list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
To list Tensorboards:

    $ gcloud ai tensorboards list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/tensorboards/list)

---
### `gcloud ai tensorboards update`

Update an existing Vertex AI Tensorboard

Update an existing Vertex AI Tensorboard.

**Synopsis:**
```
gcloud ai tensorboards update (TENSORBOARD : --region=REGION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tensorboard resource - The tensorboard to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tensorboard on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TENSORBOARD
     ID of the tensorboard or fully qualified identifier for the
     tensorboard.

     To set the name attribute:
     + provide the argument tensorboard on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the tensorboard.

     To set the region attribute:
     + provide the argument tensorboard on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the tensorboard. |
| `--display-name` | DISPLAY_NAME |  | Display name of the tensorboard. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Tensorboard 12345, in region us-central1 and project
my-project, with the display name updated display name:

    $ gcloud ai tensorboards update \
      projects/my-project/locations/us-central1/tensorboards/12345 \
      --display-name="updated display name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/tensorboards/update)

---
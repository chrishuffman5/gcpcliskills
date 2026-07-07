# gcloud ai indexes

manage Vertex AI indexes

### `gcloud ai indexes create`

Create a new Vertex AI index

**Synopsis:**
```
gcloud ai indexes create --display-name=DISPLAY_NAME
    --metadata-file=METADATA_FILE [--description=DESCRIPTION]
    [--encryption-kms-key-name=ENCRYPTION_KMS_KEY_NAME]
    [--index-update-method=INDEX_UPDATE_METHOD] [--labels=[KEY=VALUE,...]]
    [--metadata-schema-uri=METADATA_SCHEMA_URI] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the index. |
| `--metadata-file` | METADATA_FILE |  | Path to a local JSON file that contains the additional metadata information about the index. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the index. |
| `--encryption-kms-key-name` | ENCRYPTION_KMS_KEY_NAME |  | The Cloud KMS resource identifier of the customer managed encryption key used to protect a resource. Has the form: projects/my-project/locations/my-region/keyRings/my-kr/cryptoKeys/my-key. The key needs to be in the same region as where the compute resource is created. |
| `--index-update-method` | one of: batch-update can update index with gcloud ai indexes update usingdatapoints files on Cloud Storage |  | The update method to use with this index. Choose stream-update or batch-update (case insensitive). If not set, batch update will be used by default. INDEX_UPDATE_METHOD must be one of: batch-update can update index with gcloud ai indexes update usingdatapoints files on Cloud Storage. stream-update can update datapoints with upsert-datapoints and`delete-datapoints and will be applied nearly real-time. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--metadata-schema-uri` | METADATA_SCHEMA_URI |  | Points to a YAML file stored on Google Cloud Storage describing additional information about index. |


**Examples:**
```bash
To create an index under project example in region us-central1, encrypted
with KMS key kms-key-name, run:

    $ gcloud ai indexes create --display-name=index --description=test \
        --metadata-file=path/to/your/metadata.json --project=example \
        --region=us-central1 --encryption-kms-key-name=kms-key-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/create)

---
### `gcloud ai indexes delete`

Delete an existing Vertex AI index

**Synopsis:**
```
gcloud ai indexes delete (INDEX : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Index to delete. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

     To set the name attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index.

     To set the region attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To delete an index 123 of project example in region us-central1, run:

    $ gcloud ai indexes delete 123 --project=example --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/delete)

---
### `gcloud ai indexes describe`

Gets detailed index information about the given index id

**Synopsis:**
```
gcloud ai indexes describe (INDEX : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Index to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

     To set the name attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index.

     To set the region attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
Describe an index 123 of project example in region us-central1, run:

    $ gcloud ai indexes describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/describe)

---
### `gcloud ai indexes list`

Lists the indexes of the given project and region

**Synopsis:**
```
gcloud ai indexes list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
Lists the indexes of project example in region us-central1, run:

    $ gcloud ai indexes list --project=example --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/list)

---
### `gcloud ai indexes remove-datapoints`

Remove data points from the specified index

**Synopsis:**
```
gcloud ai indexes remove-datapoints (INDEX : --region=REGION)
    (--datapoint-ids=[DATAPOINT_IDS,...]
      | --datapoints-from-file=DATAPOINTS_FROM_FILE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Index to remove data points from. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

     To set the name attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index.

     To set the region attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--datapoint-ids` | [DATAPOINT_IDS,...] |  | _[Exactly one of these must be specified:]_ List of index datapoint ids to be removed from the index. |
| `--datapoints-from-file` | DATAPOINTS_FROM_FILE |  | _[Exactly one of these must be specified:]_ Path to a local JSON file that contains the data points that need to be added to the index. |


**Examples:**
```bash
To remove datapoints from an index '123', run:

    $ gcloud ai indexes remove-datapoints 123 \
        --datapoint-ids=example1,example2 --project=example \
        --region=us-central1

Or put datapoint ids in a json file and run:

    $ gcloud ai indexes remove-datapoints 123 \
        --datapoints-from-file=example.json --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/remove-datapoints)

---
### `gcloud ai indexes update`

Update an Vertex AI index

**Synopsis:**
```
gcloud ai indexes update (INDEX : --region=REGION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--metadata-file=METADATA_FILE] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Index to update. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

     To set the name attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index.

     To set the region attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the index. |
| `--display-name` | DISPLAY_NAME |  | Display name of the index. |
| `--metadata-file` | METADATA_FILE |  | Path to a local JSON file that contains the additional metadata information about the index. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update index 123 under project example in region us-central1, run:

    $ gcloud ai indexes update --display-name=new-name \
        --metadata-file=path/to/your/metadata.json --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/update)

---
### `gcloud ai indexes upsert-datapoints`

Upsert data points into the specified index

**Synopsis:**
```
gcloud ai indexes upsert-datapoints (INDEX : --region=REGION)
    --datapoints-from-file=DATAPOINTS_FROM_FILE
    [--update-mask=[UPDATE_MASK_PATH,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Index resource - Index to upsert data points from. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INDEX
     ID of the index or fully qualified identifier for the index.

     To set the name attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the index.

     To set the region attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--datapoints-from-file` | DATAPOINTS_FROM_FILE |  | Path to a local JSON file that contains the data points that need to be added to the index. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-mask` | [UPDATE_MASK_PATH,...] |  | Update mask is used to specify the fields to be overwritten in the datapoints by the update. The fields specified in the update_mask are relative to each IndexDatapoint inside datapoints, not the full request. Updatable fields: * Use --update-mask=all_restricts to update both restricts and numeric_restricts. |


**Examples:**
```bash
To upsert datapoints into an index '123', run:

    $ gcloud ai indexes upsert-datapoints 123 \
        --datapoints-from-file=example.json --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/indexes/upsert-datapoints)

---
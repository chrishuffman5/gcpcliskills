# gcloud healthcare dicom-stores

manage Cloud Healthcare API DICOM stores

### `gcloud healthcare dicom-stores add-iam-policy-binding`

Add an IAM policy binding to a Cloud Healthcare API DICOM store

Adds an IAM policy binding to a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores add-iam-policy-binding
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to add an IAM
policy binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the dicom store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores add-iam-policy-binding \
        test-dicom-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/add-iam-policy-binding)

---
### `gcloud healthcare dicom-stores create`

Create a Cloud Healthcare API DICOM store

Create a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores create
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    [--pubsub-topic=PUBSUB_TOPIC] [--send-for-bulk-import]
    [--stream-configs=STREAM_CONFIGS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pubsub-topic` | PUBSUB_TOPIC |  | Google Cloud Pub/Sub topic to send updates to. Note: A topic must be created before publishing or subscribing to it. For instructions on creating topics, refer to: https://cloud.google.com/pubsub/docs/admin#create_a_topic |
| `--send-for-bulk-import` |  |  | Indicates whether or not to send Cloud Pub/Sub notifications on bulk import. Only supported for DICOM imports. |
| `--stream-configs` | STREAM_CONFIGS |  | Configuration that indicates the BigQuery destinations for streaming instances of a DICOM store. To specify StreamConfigs, list all BigQuery destinations into one string separated by comma. (e.g., --stream-configs bq://{bigqueryProjectId1}.{bigqueryDatasetId1}.{bigqueryTableId1},bq://{bigqueryProjectId2}.{bigqueryDatasetId2}.{bigqueryTableId2}). |


**Examples:**
```bash
To create a dicom store called 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores create test-dicom-store \
        --dataset=test-dataset

To create a dicom store with the Cloud Pub/Sub topic 'test-pubsub-topic',
run:

    $ gcloud healthcare dicom-stores create test-dicom-store \
        --dataset=test-dataset \
        --pubsub-topic=projects/my-project/topics/test-pubsub-topic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/create)

---
### `gcloud healthcare dicom-stores deidentify`

De-identify data from the source store and write it to the destination store

De-identify data from the source store and write it to the destination
store.

**Synopsis:**
```
gcloud healthcare dicom-stores deidentify
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    --destination-store=DESTINATION_STORE [--async]
    [--dicom-filter-tags=[DICOM_FILTER_TAGS,...]]
    [--text-redaction-mode=TEXT_REDACTION_MODE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Source Cloud Healthcare API DICOM store to
deidentify. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-store` | DESTINATION_STORE |  | The name of the DICOM store to which the redacted data should be written (e.g., projects/{projectId}/locations/{locationId}/datasets/{datasetId}/dicomStores/{dicomStoreId}). The destination DICOM store must already exist, or the request will fail. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--dicom-filter-tags` | [DICOM_FILTER_TAGS,...] |  | Tags to be filtered. Tags must be DICOM Data Elements, File Meta Elements, or Directory Structuring Elements, as defined at: http://dicom.nema.org/medical/dicom/current/output/html/part06.html#table_6-1,. They may be provided by "Keyword" or "Tag". For example "PatientID", "0010,0010". |
| `--text-redaction-mode` | TEXT_REDACTION_MODE |  | Determines how to redact text from image. TEXT_REDACTION_MODE must be (only one value is supported): all Redact all text. |


**Examples:**
```bash
To generate a de-identified version of the DICOM store 'test-dicom-store',
run the command below.

    $ gcloud healthcare dicom-stores deidentify test-dicom-store \
        --destination-store=projects/{projectId}/locations/us-central1/\
    datasets/{datasetId}/dicomStores/test-deid-dicom-store \
        --dicom-filter-tags=MediaStorageSOPClassUID,SeriesInstanceUID,\
    StudyInstanceUID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/deidentify)

---
### `gcloud healthcare dicom-stores delete`

Delete a Cloud Healthcare API DICOM store

Delete a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores delete
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To delete the dicom-store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores delete test-dicom-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/delete)

---
### `gcloud healthcare dicom-stores describe`

Describe a Cloud Healthcare API DICOM store

Describe a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores describe
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To describe the dicom-store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores describe test-dicom-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/describe)

---
### `gcloud healthcare dicom-stores get-iam-policy`

Retrieve the IAM policy for a Cloud Healthcare API DICOM store

Retrieve the IAM policy for a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores get-iam-policy
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store whose IAM policy to
fetch. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To print the IAM policy for the dicom store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores get-iam-policy test-dicom-store \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/get-iam-policy)

---
### `gcloud healthcare dicom-stores list`

List Cloud Healthcare API DICOM stores

List Cloud Healthcare API DICOM stores.

**Synopsis:**
```
gcloud healthcare dicom-stores list
    (--dataset=DATASET : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dataset` | DATASET |  | _[This must be specified.]_ ID of the dataset or fully qualified identifier for the dataset. To set the dataset attribute: + provide the argument --dataset on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location. To set the location attribute: + provide the argument --dataset on the command line with a fully specified name; + provide the argument --location on the command line; + set the property healthcare/location. |


**Examples:**
```bash
To list the dicom stores in 'test-dataset', run:

    $ gcloud healthcare dicom-stores list --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/list)

---
### `gcloud healthcare dicom-stores metrics`

Get the metrics for a Cloud Healthcare API DICOM store

Gets the metrics for a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores metrics
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to get metrics for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To get metrics for the DICOM store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores metrics test-dicom-store \
         --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/metrics)

---
### `gcloud healthcare dicom-stores remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Healthcare API DICOM store

Removes an IAM policy binding from a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores remove-iam-policy-binding
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to remove an IAM
policy binding from. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the dicom store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores remove-iam-policy-binding \
        test-dicom-store --dataset=test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/remove-iam-policy-binding)

---
### `gcloud healthcare dicom-stores set-iam-policy`

Set the IAM policy for a Cloud Healthcare API DICOM store

Set the IAM policy for a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores set-iam-policy
    (DICOM_STORE : --dataset=DATASET --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store whose IAM policy to
set. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the dicom store 'test-dicom-store':

    $ gcloud healthcare dicom-stores set-iam-policy test-dicom-store \
        policy.json --dataset=test-dataset

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/set-iam-policy)

---
### `gcloud healthcare dicom-stores update`

Update a Cloud Healthcare API DICOM store

Update a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores update
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    [--pubsub-topic=PUBSUB_TOPIC] [--send-for-bulk-import]
    [--stream-configs=STREAM_CONFIGS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM to update. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pubsub-topic` | PUBSUB_TOPIC |  | Google Cloud Pub/Sub topic to send updates to. Note: A topic must be created before publishing or subscribing to it. For instructions on creating topics, refer to: https://cloud.google.com/pubsub/docs/admin#create_a_topic |
| `--send-for-bulk-import` |  |  | Indicates whether or not to send Cloud Pub/Sub notifications on bulk import. Only supported for DICOM imports. |
| `--stream-configs` | STREAM_CONFIGS |  | Configuration that indicates the BigQuery destinations for streaming instances of a DICOM store. To specify StreamConfigs, list all BigQuery destinations into one string separated by comma. (e.g., --stream-configs bq://{bigqueryProjectId1}.{bigqueryDatasetId1}.{bigqueryTableId1},bq://{bigqueryProjectId2}.{bigqueryDatasetId2}.{bigqueryTableId2}). |


**Examples:**
```bash
To update the Cloud Pub/Sub topic on a dicom store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores update test-dicom-store \
        --pubsub-topic=projects/my-project/topics/test-pubsub-topic \
        --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/update)

---

## `gcloud healthcare dicom-stores export` — manage Cloud Healthcare API DICOM store exports
### `gcloud healthcare dicom-stores export bq`

Export a Cloud Healthcare API API DICOM store to BigQuery

Export a Cloud Healthcare API API DICOM store to BigQuery.

**Synopsis:**
```
gcloud healthcare dicom-stores export bq
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    --bq-table=BQ_TABLE [--async] [--overwrite-table]
    [--write-disposition=WRITE_DISPOSITION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bq-table` | BQ_TABLE |  | The BigQuery table where the DICOM store should be written. If this table does not exist, a new table with the given name will be created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--overwrite-table` |  |  | If the destination table already exists and this flag is TRUE, the table will be overwritten by the contents of the DICOM store. If the flag is not set and the destination table already exists, the export call returns an error. |
| `--write-disposition` | one of: write-append Append data to the existing table |  | Determines whether the existing table in the destination is to be overwritten or appended to. WRITE_DISPOSITION must be one of: write-append Append data to the existing table. write-empty Only export data if the destination table is empty. write-truncate Erase all existing data in a table before writing the instances. |


**Examples:**
```bash
To export the dicom-store test-dicom-store to the BigQuery table testtable
in the dataset testdataset, overwriting any existing table, run:

    $ gcloud healthcare dicom-stores export bq test-dicom-store \
        --bq-table=bq://my-project.testdataset.testtable \
        --dataset=test-dataset --write-disposition=write-truncate

To export the dicom-store test-dicom-store to the BigQuery table testtable
in the dataset testdataset, appending any existing table, run:

    $ gcloud healthcare dicom-stores export bq test-dicom-store \
        --bq-table=bq://my-project.testdataset.testtable \
        --dataset=test-dataset --write-disposition=write-append
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/export/bq)

---
### `gcloud healthcare dicom-stores export gcs`

Export a Cloud Healthcare API DICOM store to Google Cloud Storage

Export a Cloud Healthcare API DICOM store to Google Cloud Storage.

**Synopsis:**
```
gcloud healthcare dicom-stores export gcs
    (DICOM_STORE : --dataset=DATASET --location=LOCATION)
    --gcs-uri-prefix=GCS_URI_PREFIX [--async] [--mime-type=MIME_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri-prefix` | GCS_URI_PREFIX |  | URI for a Google Cloud Storage directory to which result files should be written (for example, gs://bucket-id/path/to/destination/dir). If there is no trailing slash, the service will append one when composing the object path. The user is responsible for creating the Google Cloud Storage bucket referenced in uri_prefix. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--mime-type` | MIME_TYPE |  | 'MIME types supported by DICOM spec. Each file will be written in the following format: .../{study_id}/{series_id}/{instance_id}[/{frame_number}].{extension} The frame_number component will exist only for multi-frame instances. Refer to the DICOM conformance statement for permissible MIME types: https://cloud.google.com/healthcare/docs/dicom#wado-rs The following extensions will be used for output files: * application/dicom -> .dcm * image/jpeg -> .jpg * image/png -> .png If unspecified, the instances will be exported in their original DICOM format.' |


**Examples:**
```bash
To export the dicom-store 'test-dicom-store' to the existing bucket
'testGcsBucket' in the folder 'someFolder', with the mime-type
'application/dicom', run:

    $ gcloud healthcare dicom-stores export gcs test-dicom-store \
        --gcs-uri-prefix=gs://testGcsBucket/someFolder \
        --mime-type=application/dicom --dataset=test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/export/gcs)

---

## `gcloud healthcare dicom-stores import` — manage Cloud Healthcare API DICOM store imports
### `gcloud healthcare dicom-stores import gcs`

Import DICOM objects into a Cloud Healthcare API DICOM store

Import DICOM objects into a Cloud Healthcare API DICOM store.

**Synopsis:**
```
gcloud healthcare dicom-stores import gcs
    (DICOM_STORE : --dataset=DATASET --location=LOCATION) --gcs-uri=GCS_URI
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DicomStore resource - Cloud Healthcare API DICOM store into which the data
is imported. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dicom_store on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DICOM_STORE
     ID of the dicomStore or fully qualified identifier for the
     dicomStore.

     To set the dicom_store attribute:
     + provide the argument dicom_store on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --dataset=DATASET
     Cloud Healthcare dataset.

     To set the dataset attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --dataset on the command line.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dicom_store on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | Google Cloud Storage URI containing DICOM object data. It must match individual DICOM files or use wildcards to import multiple files from one or more directories. * Use * to match 0 or more non-separator characters. For example, gs://BUCKET/DIRECTORY/Example*.dcm matches Example.dcm and Example22.dcm in DIRECTORY. * Use ** to match 0 or more characters (including separators). Must be used at the end of a path and with no other wildcards in the path. Can also be used with a filename extension (such as .dcm), which imports all files with the filename extension in the specified directory and its subdirectories. For example, gs://BUCKET/DIRECTORY/**.dcm imports all files with the .dcm filename extension in DIRECTORY and its subdirectories. * Use ? to match 1 character. For example, gs://BUCKET/DIRECTORY/Example?.dcm matches Example1.dcm but does not match Example.dcm or Example01.dcm. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To import the DICOM objects from the existing bucket 'testGcsBucket' in the
folder 'someFolder' into the DICOM store 'test-dicom-store', run:

    $ gcloud healthcare dicom-stores import gcs test-dicom-store \
        --gcs-uri="gs://testGcsBucket/someFolder/*" \
        --dataset=test-dataset

Note that '' matches any files within a folder, and '**' also recursively
matches files within sub-folders.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/dicom-stores/import/gcs)

---
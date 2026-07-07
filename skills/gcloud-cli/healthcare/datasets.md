# gcloud healthcare datasets

manage Cloud Healthcare API datasets

### `gcloud healthcare datasets add-iam-policy-binding`

Add an IAM policy binding to a Cloud Healthcare API dataset

Add an IAM policy binding to a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets add-iam-policy-binding
    (DATASET : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset to add an IAM policy
binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
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
'test-user@gmail.com' on the dataset 'test-dataset', run:

    $ gcloud healthcare datasets add-iam-policy-binding test-dataset \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/add-iam-policy-binding)

---
### `gcloud healthcare datasets create`

Create a Cloud Healthcare API dataset

Create a new Cloud Healthcare API dataset

**Synopsis:**
```
gcloud healthcare datasets create (DATASET : --location=LOCATION) [--async]
    [--encryption-key=ENCRYPTION_KEY] [--time-zone=TIME_ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset to create. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--encryption-key` | ENCRYPTION_KEY |  | KMS encryption key that is used to secure this dataset and its sub-resources. The key used for encryption and the dataset must be in the same location. If empty, the default Google encryption key will be used to secure this dataset. The format is projects/{projectId}/locations/{locationId}/keyRings/{keyRingId}/cryptoKeys/{keyId}. |
| `--time-zone` | TIME_ZONE |  | Default timezone used by this dataset. |


**Examples:**
```bash
To create a dataset called 'test-dataset' in us-central1, run:

    $ gcloud healthcare datasets create test-dataset

To create a dataset in a different region (ex: asia-northeast1), run:

    $ gcloud healthcare datasets create test-dataset \
        --location=asia-northeast1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/create)

---
### `gcloud healthcare datasets deidentify`

Create a new Cloud Healthcare API dataset containing de-identified data from the source dataset

Create a new Cloud Healthcare API dataset containing de-identified data
from the source dataset.

**Synopsis:**
```
gcloud healthcare datasets deidentify (DATASET : --location=LOCATION)
    --destination-dataset=DESTINATION_DATASET [--async]
    [--default-fhir-config] [--dicom-filter-tags=[DICOM_FILTER_TAGS,...]]
    [--text-redaction-mode=TEXT_REDACTION_MODE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Source Cloud Healthcare API dataset to deidentify. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-dataset` | DESTINATION_DATASET |  | The name of the dataset resource to which the redacted data should be written (e.g., projects/{projectId}/locations/{locationId}/datasets/{datasetId}). The new dataset must not exist, or the request will fail. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--default-fhir-config` |  |  | Deidentify FHIR data with default configurations. |
| `--dicom-filter-tags` | [DICOM_FILTER_TAGS,...] |  | Tags to be filtered. Tags must be DICOM Data Elements, File Meta Elements, or Directory Structuring Elements, as defined at: http://dicom.nema.org/medical/dicom/current/output/html/part06.html#table_6-1,. They may be provided by "Keyword" or "Tag". For example "PatientID", "0010,0010". |
| `--text-redaction-mode` | TEXT_REDACTION_MODE |  | Determines how to redact text from image. TEXT_REDACTION_MODE must be (only one value is supported): all Redact all text. |


**Examples:**
```bash
To generate a de-identified version of the dataset 'test-dataset', run the
command below. To skip the FHIR stores, omit the --default-fhir-config
flag, and to skip DICOM stores, omit the --dicom-filter-tags flag.

    $ gcloud healthcare datasets deidentify test-dataset \
        --destination-dataset=projects/{projectId}/locations/\
    us-central1/datasets/test-deid-dataset --default-fhir-config \
        --dicom-filter-tags=MediaStorageSOPClassUID,SeriesInstanceUID,\
    StudyInstanceUID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/deidentify)

---
### `gcloud healthcare datasets delete`

Delete a Cloud Healthcare API dataset

Deletes a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets delete (DATASET : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To delete the dataset 'test-dataset', run:

    $ gcloud healthcare datasets delete test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/delete)

---
### `gcloud healthcare datasets describe`

Describe a Cloud Healthcare API dataset

Describe a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets describe (DATASET : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To describe the dataset 'test-dataset', run:

    $ gcloud healthcare datasets describe test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/describe)

---
### `gcloud healthcare datasets get-iam-policy`

Retrieve the IAM policy for a Cloud Healthcare API dataset

Retrieve the IAM policy for a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets get-iam-policy (DATASET : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset whose IAM policy to fetch.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Examples:**
```bash
To print the IAM policy for the dataset 'test-dataset', run:

    $ gcloud healthcare datasets get-iam-policy test-dataset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/get-iam-policy)

---
### `gcloud healthcare datasets list`

List Cloud Healthcare API datasets

List Cloud Healthcare API datasets.

**Synopsis:**
```
gcloud healthcare datasets list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property healthcare/location. |


**Examples:**
```bash
To list the datasets in us-central1, run:

    $ gcloud healthcare datasets list

To list the datasets in europe-west2, run:

    $ gcloud healthcare datasets list --location=europe-west2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/list)

---
### `gcloud healthcare datasets remove-iam-policy-binding`

Remove an IAM policy binding to a Cloud Healthcare API dataset

Remove an IAM policy binding to a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets remove-iam-policy-binding
    (DATASET : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset to remove an IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
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
'test-user@gmail.com' on the dataset 'test-dataset', run:

    $ gcloud healthcare datasets remove-iam-policy-binding \
        test-dataset --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/remove-iam-policy-binding)

---
### `gcloud healthcare datasets set-iam-policy`

Set the IAM policy for a Cloud Healthcare API dataset

Set the IAM policy for a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets set-iam-policy (DATASET : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset whose IAM policy to set.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
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
'policy.json' and set it for the dataset 'my-dataset':

    $ gcloud healthcare datasets set-iam-policy my-dataset policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/set-iam-policy)

---
### `gcloud healthcare datasets update`

Update a Cloud Healthcare API dataset

Update a Cloud Healthcare API dataset.

**Synopsis:**
```
gcloud healthcare datasets update (DATASET : --location=LOCATION)
    [--time-zone=TIME_ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Dataset resource - Cloud Healthcare API dataset you want to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument dataset on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATASET
     ID of the dataset or fully qualified identifier for the dataset.

     To set the dataset attribute:
     + provide the argument dataset on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location.

     To set the location attribute:
     + provide the argument dataset on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property healthcare/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--time-zone` | TIME_ZONE |  | Default timezone used by this dataset. |


**Examples:**
```bash
To update the dataset 'test-dataset', run:

    $ gcloud healthcare datasets update test-dataset --time-zone=PDT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/healthcare/datasets/update)

---
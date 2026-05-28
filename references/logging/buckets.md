# gcloud logging buckets

manage Cloud Logging buckets

### `gcloud logging buckets create`

Create a bucket

After creating a bucket, use a log sink to route logs into the bucket.

**Synopsis:**
```
gcloud logging buckets create BUCKET_ID --location=LOCATION [--async]
    [--cmek-kms-key-name=CMEK_KMS_KEY_NAME] [--description=DESCRIPTION]
    [--enable-analytics] [--index=[KEY=VALUE, ...,...]]
    [--restricted-fields=[RESTRICTED_FIELD,...]]
    [--retention-days=RETENTION_DAYS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUCKET_ID
   ID of the bucket to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location in which to create the bucket. Once the bucket is created, the location cannot be changed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cmek-kms-key-name` | CMEK_KMS_KEY_NAME |  | A valid kms_key_name will enable CMEK for the bucket. |
| `--description` | DESCRIPTION |  | A textual description for the bucket. |
| `--enable-analytics` |  |  | Whether to opt the bucket into Log Analytics. Once opted in, the bucket cannot be opted out of Log Analytics. |
| `--index` | [KEY=VALUE, ...,...] |  | Specify an index to be added to the log bucket. This flag can be repeated. The fieldPath and type attributes are required. For example: --index=fieldPath=jsonPayload.foo,type=INDEX_TYPE_STRING. The following keys are accepted: fieldPath The LogEntry field path to index. For example: jsonPayload.request.status. Paths are limited to 800 characters and can include only letters, digits, underscores, hyphens, and periods. type The type of data in this index. For example: INDEX_TYPE_STRING Supported types are INDEX_TYPE_STRING and INDEX_TYPE_INTEGER. |
| `--restricted-fields` | [RESTRICTED_FIELD,...] |  | Comma-separated list of field paths that require permission checks in this bucket. The following fields and their children are eligible: textPayload, jsonPayload, protoPayload, httpRequest, labels, sourceLocation. |
| `--retention-days` | RETENTION_DAYS |  | The period logs will be retained, after which logs will automatically be deleted. The default is 30 days. |


**Examples:**
```bash
To create a bucket 'my-bucket' in location 'global', run:

    $ gcloud logging buckets create my-bucket --location=global \
        --description="my custom bucket"

To create a bucket with extended retention, run:

    $ gcloud logging buckets create my-bucket --location=global \
        --retention-days=365

To create a bucket in cloud region 'us-central1', run:

    $ gcloud logging buckets create my-bucket --location=us-central1

To create a bucket with custom index of 'jsonPayload.foo', run:

    $ gcloud logging buckets create my-bucket \
        --index=fieldPath=jsonPayload.foo,type=INDEX_TYPE_STRING

To create a bucket with custom CMEK, run:

    $ gcloud logging buckets create my-bucket --location=us-central1 \
        --cmek-kms-key-name=CMEK_KMS_KEY_NAME

To asynchronously create a bucket enrolled into Log Analytics, run:

    $ gcloud logging buckets create my-bucket --location=global \
        --async --enable-analytics
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/buckets/create)

---
### `gcloud logging buckets delete`

Delete a bucket

**Synopsis:**
```
gcloud logging buckets delete BUCKET_ID --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUCKET_ID
   ID of the bucket to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the bucket to delete. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the bucket to delete. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the bucket to delete. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the bucket to delete. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To delete bucket 'my-bucket' in location 'global', run:

    $ gcloud logging buckets delete my-bucket --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/buckets/delete)

---
### `gcloud logging buckets describe`

Display information about a bucket

Display information about a bucket.

**Synopsis:**
```
gcloud logging buckets describe BUCKET_ID --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUCKET_ID
   The id of the bucket to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the bucket to describe. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the bucket to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the bucket to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the bucket to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a bucket in a project, run:

    $ gcloud logging buckets describe my-bucket --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/buckets/describe)

---
### `gcloud logging buckets list`

List the defined buckets

List the buckets for a project.

**Synopsis:**
```
gcloud logging buckets list [--location=LOCATION]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location from which to list buckets. By default, buckets in all locations will be listed |


**Examples:**
```bash
To list the buckets in a project, run:

    $ gcloud logging buckets list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/buckets/list)

---
### `gcloud logging buckets undelete`

Undelete a bucket

**Synopsis:**
```
gcloud logging buckets undelete BUCKET_ID --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUCKET_ID
   ID of the bucket to undelete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the bucket to undelete. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the bucket to undelete. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the bucket to undelete. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the bucket to undelete. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To undelete bucket 'my-bucket' in location 'global', run:

    $ gcloud logging buckets undelete my-bucket --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/buckets/undelete)

---
### `gcloud logging buckets update`

Update a bucket

Update the properties of a bucket.

**Synopsis:**
```
gcloud logging buckets update BUCKET_ID --location=LOCATION
    [--add-index=[KEY=VALUE, ...,...]] [--async] [--clear-indexes]
    [--cmek-kms-key-name=CMEK_KMS_KEY_NAME] [--description=DESCRIPTION]
    [--enable-analytics] [--locked] [--remove-indexes=[FIELD PATH,...]]
    [--restricted-fields=[RESTRICTED_FIELD,...]]
    [--retention-days=RETENTION_DAYS] [--update-index=[KEY=VALUE, ...,...]]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUCKET_ID
   The id of the bucket to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-index` | [KEY=VALUE, ...,...] |  | Add an index to be added to the log bucket. This flag can be repeated. The fieldPath and type attributes are required. For example: --index=fieldPath=jsonPayload.foo,type=INDEX_TYPE_STRING. The following keys are accepted: fieldPath The LogEntry field path to index. For example: jsonPayload.request.status. Paths are limited to 800 characters and can include only letters, digits, underscores, hyphens, and periods. type The type of data in this index. For example: INDEX_TYPE_STRING Supported types are strings and integers. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--clear-indexes` |  |  | Remove all logging indexes from the bucket. |
| `--cmek-kms-key-name` | CMEK_KMS_KEY_NAME |  | A valid kms_key_name will enable CMEK for the bucket. |
| `--description` | DESCRIPTION |  | A new description for the bucket. |
| `--enable-analytics` |  |  | Whether to opt the bucket into Log Analytics. Once opted in, the bucket cannot be opted out of Log Analytics. |
| `--locked` |  |  | Lock the bucket and prevent it from being modified or deleted (unless it is empty). |
| `--remove-indexes` | [FIELD PATH,...] |  | Specify the field path of the logging index(es) to delete. |
| `--restricted-fields` | [RESTRICTED_FIELD,...] |  | A new set of restricted fields for the bucket. |
| `--retention-days` | RETENTION_DAYS |  | A new retention period for the bucket. |
| `--update-index` | [KEY=VALUE, ...,...] |  | Update an index to be added to the log bucket. This will update the type of the index, and also update its createTime to the new update time. This flag can be repeated. The fieldPath and type attributes are required. For example: --index=fieldPath=jsonPayload.foo,type=INDEX_TYPE_STRING. The following keys are accepted: fieldPath The LogEntry field path to index. For example: jsonPayload.request.status. Paths are limited to 800 characters and can include only letters, digits, underscores, hyphens, and periods. type The type of data in this index. For example: INDEX_TYPE_STRING Supported types are strings and integers. |


**Examples:**
```bash
To update a bucket in your project, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --description=my-new-description

To update a bucket in your project and remove all indexes, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --clear-indexes

To update a bucket in your project and remove an index, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --remove-indexes=jsonPayload.foo2

To update a bucket in your project and add an index, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --add-index=fieldPath=jsonPayload.foo2,type=INDEX_TYPE_STRING

To update a bucket in your project and update an existing index, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --update-index=fieldPath=jsonPayload.foo,type=INDEX_TYPE_INTEGER

To update a bucket in your project and update existing cmek, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --cmek-kms-key-name=CMEK_KEY_NAME

To asynchronously enroll a bucket in your project into Log Analytics, run:

    $ gcloud logging buckets update my-bucket --location=global \
       --async --enable-analytics
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/buckets/update)

---
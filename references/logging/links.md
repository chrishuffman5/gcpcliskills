# gcloud logging links

manage linked datasets

### `gcloud logging links create`

Create a linked dataset on an analytics log bucket

Create a linked dataset for a log bucket.

**Synopsis:**
```
gcloud logging links create LINK_ID --bucket=BUCKET --location=LOCATION
    [--async] [--description=DESCRIPTION]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LINK_ID
   ID of the linked dataset to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that will hold the linked dataset |
| `--location` | LOCATION |  | Location of the bucket that will hold the linked datasert. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A textual description for the linked dataset. |


**Examples:**
```bash
To create a linked dataset in a project, run:

    $ gcloud logging links create my-link --bucket=my-bucket \
       --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/links/create)

---
### `gcloud logging links delete`

Delete a linked dataset

Delete a bucket's linked dataset.

**Synopsis:**
```
gcloud logging links delete LINK_ID --bucket=BUCKET --location=LOCATION
    [--async]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LINK_ID
   ID of the linked dataset to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of bucket |
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a bucket's linked dataset, run:

    $ gcloud logging links delete my-link --bucket=my-bucket \
       --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/links/delete)

---
### `gcloud logging links describe`

Display information about a linked dataset

Display information about a linked dataset.

**Synopsis:**
```
gcloud logging links describe LINK_ID --bucket=BUCKET --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LINK_ID
   Id of the linked dataset to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of bucket |
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the linked dataset to describe. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the linked dataset to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the linked dataset to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the linked dataset to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a linked dataset in a project, run:

    $ gcloud logging links describe my-link --bucket=my-bucket \
       --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/links/describe)

---
### `gcloud logging links list`

List created linked datasets on the specified bucket

List the linked datasets created for a bucket.

**Synopsis:**
```
gcloud logging links list --bucket=BUCKET --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of bucket |
| `--location` | LOCATION |  | Location of the specified bucket |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the linked datasets to list. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the linked datasets to list. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the linked datasets to list. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the linked datasets to list. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list the linked datasets created for a bucket, run:

    $ gcloud logging links list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/links/list)

---
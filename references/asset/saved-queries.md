# gcloud asset saved-queries

manage Cloud Asset Inventory saved queries

### `gcloud asset saved-queries create`

Create a Cloud Asset Inventory saved query

Create a new Cloud Asset Inventory saved query.

**Synopsis:**
```
gcloud asset saved-queries create QUERY_ID
    --query-file-path=QUERY_FILE_PATH
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUERY_ID
   Saved query identifier being created. It must be unique under the
   specified parent resource project/folder/organization.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--query-file-path` | QUERY_FILE_PATH |  | Path to JSON or YAML file that contains the query. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A string describing the query. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a new saved 'query-id-1' in project 'p1' with the content of the
query stored locally in query.json, run:

    $ gcloud asset saved-queries create query-id-1 --project=p1 \
        --query-file-path=./query-content.json \
        --description="This is an example saved query with query id \
    query-id-1" --labels="key1=val1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/saved-queries/create)

---
### `gcloud asset saved-queries delete`

Delete a Cloud Asset Inventory saved query

Delete a Cloud Asset Inventory saved query.

**Synopsis:**
```
gcloud asset saved-queries delete QUERY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUERY_ID
   Asset saved query identifier to be deleted. It must be unique under the
   specified parent resource project/folder/organization.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the saved query. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the saved query. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the saved query. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To delete a saved query with id 'query1' in project 'p1', run:

    $ gcloud asset saved-queries delete query1 --project=p1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/saved-queries/delete)

---
### `gcloud asset saved-queries describe`

Describe a Cloud Asset Inventory saved query

Describe a Cloud Asset Inventory saved query.

**Synopsis:**
```
gcloud asset saved-queries describe QUERY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUERY_ID
   Asset Saved Query identifier being described. It must be unique under
   the specified parent resource: project/folder/organization.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the saved query. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the saved query. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the saved query. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a saved query with query id 'query1' in project 'p1', run:

    $ gcloud asset saved-queries describe query1 --project=p1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/saved-queries/describe)

---
### `gcloud asset saved-queries list`

List Cloud Asset Inventory saved query

List Cloud Asset Inventory saved queries under a parent resource.

**Synopsis:**
```
gcloud asset saved-queries list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the saved query. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the saved query. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the saved query. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list saved queries in organization 'org1', run:

    $ gcloud asset saved-queries list --organization=org1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/saved-queries/list)

---
### `gcloud asset saved-queries update`

Update an existing Cloud Asset Inventory saved query

Update an existing Cloud Asset Inventory saved query.

**Synopsis:**
```
gcloud asset saved-queries update QUERY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--description=DESCRIPTION]
    [--query-file-path=QUERY_FILE_PATH] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUERY_ID
   Saved query identifier being updated. It must be unique under the
   specified parent resource project/folder/organization.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the saved query. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the saved query. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the saved query. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A string describing the query. |
| `--query-file-path` | QUERY_FILE_PATH |  | Path to JSON or YAML file that contains the query. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the content of an existing saved query, run:

    $ gcloud asset saved-queries update query-id-1 --project=p1 \
        --query-file-path=./query-content.json \
        --description="updating a query with query id query-id-1" \
        --update-labels="key1=val1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/saved-queries/update)

---
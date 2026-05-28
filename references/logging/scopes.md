# gcloud logging scopes

manages Cloud Logging log scopes

### `gcloud logging scopes create`

Create a log scope

After creating a log scope, you can use it to view logs in 1 or more
resources.

**Synopsis:**
```
gcloud logging scopes create LOG_SCOPE_ID
    --resource-names=[RESOURCE_NAMES,...] [--description=DESCRIPTION]
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOG_SCOPE_ID
   ID of the log scope to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-names` | [RESOURCE_NAMES,...] |  | Comma-separated list of resource names in this log scope. It could be one or more parent resources or one or more views. A log scope can include a maximum of 50 projects and a maximum of 100 resources in total. For example, projects/[PROJECT_ID], projects/[PROJECT_ID]/locations/[LOCATION_ID]/buckets/[BUCKET_ID]/views/[VIEW_ID] |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A textual description for the log scope. |


**Examples:**
```bash
To create a log scope in a project, run:

    $ gcloud logging scopes create my-scope \
        --resource-names=projects/my-project

To create a log scope in a project with a description, run:

    $ gcloud logging scopes create my-scope \
        --resource-names=projects/my-project --description="my
    custom log scope"

To create a log scope that contains more than 1 resource, such as projects
and views, run:

    $ gcloud logging scopes create my-scope \
        --resource-names=projects/my-project,projects/my-project2, \
        projects/my-project/locations/global/buckets/my-bucket/views/\
    my-view1, \
        projects/my-project/locations/global/buckets/my-bucket/views/\
    my-view2,
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/scopes/create)

---
### `gcloud logging scopes delete`

Delete a log scope

**Synopsis:**
```
gcloud logging scopes delete LOG_SCOPE_ID
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOG_SCOPE_ID
   ID of the log scope to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the log scope to delete. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the log scope to delete. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the log scope to delete. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To delete a log scope, run:

    $ gcloud logging scopes delete my-scope
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/scopes/delete)

---
### `gcloud logging scopes describe`

Display information about a log scope

Display information about a log scope.

**Synopsis:**
```
gcloud logging scopes describe LOG_SCOPE_ID
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOG_SCOPE_ID
   The ID of the log scope to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the log scope to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the log scope to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the log scope to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a log scope in a project, run:

    $ gcloud logging scopes describe my-scope --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/scopes/describe)

---
### `gcloud logging scopes list`

List the defined log scopes

List the log scopes for a project.

**Synopsis:**
```
gcloud logging scopes list
    [--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the log scopes to list. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the log scopes to list. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the log scopes to list. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list the log scopes in a project, run:

    $ gcloud logging scopes list --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/scopes/list)

---
### `gcloud logging scopes update`

Update a log scope

Update the properties of a log scope.

**Synopsis:**
```
gcloud logging scopes update LOG_SCOPE_ID [--description=DESCRIPTION]
    [--resource-names=[RESOURCE_NAMES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOG_SCOPE_ID
   The ID of the log scope to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A new description for the log scope. |
| `--resource-names` | [RESOURCE_NAMES,...] |  | A new set of resource names for the log scope. |


**Examples:**
```bash
To update the description of a log scope in a project, run:

    $ gcloud logging scopes update my-scope \
       --description=my-new-description --project=my-project

To update the resource name of a log scope in a project. Ensure that you
provide all the resource names including the existing ones. For example, if
the log scope has the resource name my-project, and you want to update the
log scope to have the resource name another-project, run the following:

    $ gcloud logging scopes update my-scope \
       --resource-names=projects/my-project,projects/another-project \
       --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/scopes/update)

---
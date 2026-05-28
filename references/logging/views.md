# gcloud logging views

manage log views

### `gcloud logging views add-iam-policy-binding`

Add IAM policy binding to a log view

Add IAM policy binding to a log view.

**Synopsis:**
```
gcloud logging views add-iam-policy-binding VIEW_ID --bucket=BUCKET
    --location=LOCATION --member=PRINCIPAL --role=ROLE
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   ID of the view that contains the IAM policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that contains the view. |
| `--location` | LOCATION |  | Location of the bucket that contains the view. |
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the view that contains the IAM policy. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the view that contains the IAM policy. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the view that contains the IAM policy. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the view that contains the IAM policy. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role 'roles/my-role' for the user
'my-user@gmail.com' on my-view, run:

    $ gcloud logging views add-iam-policy-binding my-view \
        --member='user:my-user@gmail.com' --role='roles/my-role' \
        --bucket=my-bucket --location=global

To add a binding with a condition, run:

    $ gcloud logging views add-iam-policy-binding my-view \
        --member='user:my-user@gmail.com' --role='roles/my-role' \
        --bucket=my-bucket --location=global \
        --condition=expression=[expression],title=[title],\
    description=[description]

See https://cloud.google.com/iam/docs/managing-policies for details about
IAM policies and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/add-iam-policy-binding)

---
### `gcloud logging views create`

Create a log view on a log bucket

**Synopsis:**
```
gcloud logging views create VIEW_ID --bucket=BUCKET --location=LOCATION
    [--description=DESCRIPTION] [--log-filter=LOG_FILTER]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   ID of the view to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that will hold the view |
| `--location` | LOCATION |  | Location of the bucket that will hold the view. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A textual description for the view. |
| `--log-filter` | LOG_FILTER |  | A filter for the view. |


**Examples:**
```bash
To create a view that matches all Google Compute Engine logs in a bucket,
run:

    $ gcloud logging views create my-view --bucket=my-bucket \
        --location=global --log-filter='resource.type="gce_instance"'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/create)

---
### `gcloud logging views delete`

Delete a view

Deletes a view on a bucket.

**Synopsis:**
```
gcloud logging views delete VIEW_ID --bucket=BUCKET --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   ID of the view to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of bucket |
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the view to delete. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the view to delete. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the view to delete. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the view to delete. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To delete a view on a bucket, run:

    $ gcloud logging views delete my-view --bucket=my-bucket \
       --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/delete)

---
### `gcloud logging views describe`

Display information about a view

Displays information about a log view.

**Synopsis:**
```
gcloud logging views describe VIEW_ID --bucket=BUCKET --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   Id of the view to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of bucket |
| `--location` | LOCATION |  | Location of the bucket. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the view to describe. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the view to describe. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the view to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the view to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a view in a project, run:

    $ gcloud logging views describe my-view --bucket=my-bucket \
       --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/describe)

---
### `gcloud logging views get-iam-policy`

Display the IAM policy for a view

Get the IAM policy for a view.

**Synopsis:**
```
gcloud logging views get-iam-policy VIEW_ID --bucket=BUCKET
    --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   ID of the view to fetch IAM policy
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that holds the view. |
| `--location` | LOCATION |  | Location of the bucket that contains the view |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the view to fetch IAM policy. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the view to fetch IAM policy. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the view to fetch IAM policy. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the view to fetch IAM policy. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a view in a project, run:

    $ gcloud logging views get-iam-policy my-view --bucket=my-bucket \
       --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/get-iam-policy)

---
### `gcloud logging views list`

List the defined views

Lists the views defined on a bucket.

**Synopsis:**
```
gcloud logging views list --bucket=BUCKET --location=LOCATION
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
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the views to list. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the views to list. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the views to list. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the views to list. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list the views defined on a bucket, run:

    $ gcloud logging views list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/list)

---
### `gcloud logging views remove-iam-policy-binding`

Remove IAM policy binding to a log view

Remove IAM policy binding to a log view.

**Synopsis:**
```
gcloud logging views remove-iam-policy-binding VIEW_ID --bucket=BUCKET
    --location=LOCATION --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   ID of the view that contains the IAM policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that contains the view. |
| `--location` | LOCATION |  | Location of the bucket that contains the view. |
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the view that contains the IAM policy. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the view that contains the IAM policy. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the view that contains the IAM policy. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the view that contains the IAM policy. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To remove an IAM policy binding for the role 'roles/my-role' for the user
'my-user@gmail.com' on my-view, run:

    $ gcloud logging views remove-iam-policy-binding my-view \
        --member='user:my-user@gmail.com' --role='roles/my-role' \
        --bucket=my-bucket --location=global

To remove a binding with a condition, run:

    $ gcloud logging views remove-iam-policy-binding my-view \
        --member='user:my-user@gmail.com' --role='roles/my-role' \
        --bucket=my-bucket --location=global \
        --condition=expression=[expression],title=[title],\
    description=[description]

See https://cloud.google.com/iam/docs/managing-policies for details about
IAM policies and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/remove-iam-policy-binding)

---
### `gcloud logging views set-iam-policy`

Set IAM policy for a view

Set an IAM policy for a view.

**Synopsis:**
```
gcloud logging views set-iam-policy VIEW_ID POLICY_FILE --bucket=BUCKET
    --location=LOCATION
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   ID of the view to set IAM policy.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that contains the view. |
| `--location` | LOCATION |  | Location of the bucket that contains the view. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | BILLING_ACCOUNT_ID |  | _[At most one of these can be specified:]_ Billing account of the view to set IAM policy. |
| `--folder` | FOLDER_ID |  | _[At most one of these can be specified:]_ Folder of the view to set IAM policy. |
| `--organization` | ORGANIZATION_ID |  | _[At most one of these can be specified:]_ Organization of the view to set IAM policy. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the view to set IAM policy. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To set the IAM policy using a json file 'my_policy.json' for the view
my-view in my-bucket in the global location, run:

    $ gcloud logging views set-iam-policy my-view \
        /path/to/my_policy.json --bucket=my-bucket --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/set-iam-policy)

---
### `gcloud logging views update`

Update a view

Updates the properties of a view.

**Synopsis:**
```
gcloud logging views update VIEW_ID --bucket=BUCKET --location=LOCATION
    [--description=DESCRIPTION] [--log-filter=LOG_FILTER]
    [--billing-account=BILLING_ACCOUNT_ID | --folder=FOLDER_ID
      | --organization=ORGANIZATION_ID | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VIEW_ID
   Id of the view to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bucket` | BUCKET |  | ID of the bucket that holds the view |
| `--location` | LOCATION |  | Location of the bucket that contains the view. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | New description for the view. |
| `--log-filter` | LOG_FILTER |  | New filter for the view. |


**Examples:**
```bash
To update a view in your project, run:

    $ gcloud logging views update my-view --bucket=my-bucket \
       --location=global --description=my-new-description
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/views/update)

---
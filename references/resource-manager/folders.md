# gcloud resource-manager folders

manage Cloud Folders

### `gcloud resource-manager folders add-iam-policy-binding`

Add IAM policy binding for a folder

Adds a policy binding to the IAM policy of a folder, given a folder ID and
the binding. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud resource-manager folders add-iam-policy-binding FOLDER
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Folder resource - The ID of the folder to add the IAM binding. This
represents a Cloud resource.

This must be specified.

  FOLDER
     ID of the folder or fully qualified identifier for the folder.

     To set the folder attribute:
     + provide the argument folder on the command line.
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
'test-user@gmail.com' on the folder 'folder-id', run:

    $ gcloud resource-manager folders add-iam-policy-binding folder-id \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/storage.objectAdmin' and the user 'test-user@gmail.com'
on the folder 'folder-id', run:

    $ gcloud resource-manager folders add-iam-policy-binding folder-id \
        --member='user:test-user@gmail.com' \
        --role='roles/storage.objectAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/add-iam-policy-binding)

---
### `gcloud resource-manager folders create`

Create a new folder

Creates a new folder in the given parent folder or organization.

**Synopsis:**
```
gcloud resource-manager folders create --display-name=DISPLAY_NAME
    [--async] [--folder=FOLDER_ID] [--organization=ORGANIZATION_ID]
    [--tags=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly display name to use for the new folder. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--folder` | FOLDER_ID |  | ID for the folder to use as a parent |
| `--organization` | ORGANIZATION_ID |  | ID for the organization to use as a parent |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing Note: Currently this field is in Preview. |


**Examples:**
```bash
The following command creates a folder with the name abc into a folder with
the ID 2345:

    $ gcloud resource-manager folders create --display-name=abc \
        --folder=2345

The following command creates a folder with the name abc into an
organization with ID 1234:

    $ gcloud resource-manager folders create --display-name=abc \
        --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/create)

---
### `gcloud resource-manager folders delete`

Delete a folder

Delete a folder, given a valid folder ID.

This command can fail for the following reasons:
  o There is no folder with the given ID.
  o The active account does not have permission to delete the given
    folder.
  o The folder to be deleted is not empty.

**Synopsis:**
```
gcloud resource-manager folders delete FOLDER_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder you want to delete.
```

**Examples:**
```bash
The following command deletes a folder with the ID 123456789:

    $ gcloud resource-manager folders delete 123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/delete)

---
### `gcloud resource-manager folders describe`

Show metadata for a folder

Shows metadata for a folder, given a valid folder ID.

This command can fail for the following reasons:
  o The folder specified does not exist.
  o The active account does not have permission to access the given
    folder.

**Synopsis:**
```
gcloud resource-manager folders describe FOLDER_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder you want to describe.
```

**Examples:**
```bash
The following command prints metadata for a folder with the ID 3589215982:

    $ gcloud resource-manager folders describe 3589215982
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/describe)

---
### `gcloud resource-manager folders get-ancestors-iam-policy`

Get IAM policies for a folder and its ancestors

Get IAM policies for a folder and its ancestors, given a folder ID.

**Synopsis:**
```
gcloud resource-manager folders get-ancestors-iam-policy FOLDER_ID
    [--include-deny] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Folder resource - ID for the folder you want to get IAM policy for. This
represents a Cloud resource.

This must be specified.

  FOLDER_ID
     ID of the folder or fully qualified identifier for the folder.

     To set the folder attribute:
     + provide the argument folder_id on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--include-deny` |  |  | Include deny policies on the project and its ancestors in the result |


**Examples:**
```bash
To get IAM policies for folder 3589215982 and its ancestors, run:

    $ gcloud resource-manager folders get-ancestors-iam-policy 3589215982
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/get-ancestors-iam-policy)

---
### `gcloud resource-manager folders get-iam-policy`

Get IAM policy for a folder

Gets the IAM policy for a folder, given a folder ID.

**Synopsis:**
```
gcloud resource-manager folders get-iam-policy FOLDER_ID
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder whose policy you want to get.
```

**Examples:**
```bash
The following command prints the IAM policy for a folder with the ID
3589215982:

    $ gcloud resource-manager folders get-iam-policy 3589215982
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/get-iam-policy)

---
### `gcloud resource-manager folders list`

List folders accessible by the active account

List all folders to which the user has access under the specified parent
(either an Organization or a Folder). Exactly one of --folder or
--organization must be provided.

**Synopsis:**
```
gcloud resource-manager folders list [--folder=FOLDER_ID]
    [--organization=ORGANIZATION_ID] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | ID for the folder to list folders under |
| `--organization` | ORGANIZATION_ID |  | ID for the organization to list folders under |


**Examples:**
```bash
The following command lists folders under org with ID 123456789:

    $ gcloud resource-manager folders list --organization=123456789

The following command lists folders under folder with ID 123456789:

    $ gcloud resource-manager folders list --folder=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/list)

---
### `gcloud resource-manager folders move`

Move a folder to a new position within the same organization

Move the given folder under a new parent folder or under the organization.
Exactly one of --folder or --organization must be provided.

This command can fail for the following reasons:
  o There is no folder with the given ID.
  o There is no parent with the given type and ID.
  o The new parent is not in the same organization of the given folder.
  o Permission missing for performing this move.

**Synopsis:**
```
gcloud resource-manager folders move FOLDER_ID [--async]
    [--folder=FOLDER_ID] [--organization=ORGANIZATION_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder you want to move.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--folder` | FOLDER_ID |  | ID for the folder to use as a parent |
| `--organization` | ORGANIZATION_ID |  | ID for the organization to use as a parent |


**Examples:**
```bash
The following command moves a folder with the ID 123456789 into a folder
with the ID 2345:

    $ gcloud resource-manager folders move 123456789 --folder=2345

The following command moves a folder with the ID 123456789 into an
organization with ID 1234:

    $ gcloud resource-manager folders move 123456789 --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/move)

---
### `gcloud resource-manager folders remove-iam-policy-binding`

Remove IAM policy binding for a folder

Removes a policy binding to the IAM policy of a folder, given a folder ID
and the binding. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud resource-manager folders remove-iam-policy-binding FOLDER
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Folder resource - The ID of the folder to remove the IAM binding. This
represents a Cloud resource.

This must be specified.

  FOLDER
     ID of the folder or fully qualified identifier for the folder.

     To set the folder attribute:
     + provide the argument folder on the command line.
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
'test-user@gmail.com' on the folder 'folder-id', run:

    $ gcloud resource-manager folders remove-iam-policy-binding \
        folder-id --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2019-01-01T00:00:00Z")',
title='expires_end_of_2018', and description='Expires at midnight on
2018-12-31' for the role of 'roles/storage.objectAdmin' for the user
'test-user@gmail.com' on the folder 'folder-id', run:

    $ gcloud resource-manager folders remove-iam-policy-binding \
        folder-id --member='user:test-user@gmail.com' \
        --role='roles/storage.objectAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/storage.objectAdmin' and for the user 'test-user@gmail.com' on
the folder 'folder-id', run:

    $ gcloud resource-manager folders remove-iam-policy-binding \
        folder-id --member='user:test-user@gmail.com' \
        --role='roles/storage.objectAdmin' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/remove-iam-policy-binding)

---
### `gcloud resource-manager folders set-iam-policy`

Set IAM policy for a folder

Sets the IAM policy for a folder, given a folder ID and a file encoded in
JSON or YAML that contains the IAM policy.

**Synopsis:**
```
gcloud resource-manager folders set-iam-policy FOLDER_ID POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder whose policy you want to set.

POLICY_FILE
   JSON or YAML file with the IAM policy.
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for a folder with the ID 3589215982:

    $ gcloud resource-manager folders set-iam-policy 3589215982 \
        policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/set-iam-policy)

---
### `gcloud resource-manager folders undelete`

Undelete a folder

Undeletes the folder with the given folder ID.

This command can fail for the following reasons:
  o There is no folder with the given ID.
  o The active account does not have Owner or Editor permissions for the
    given folder.
  o When the folder to be undeleted has the same display name as an
    active folder under this folder's parent.

**Synopsis:**
```
gcloud resource-manager folders undelete FOLDER_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder you want to undelete.
```

**Examples:**
```bash
The following command undeletes the folder with the ID 3589215982:

    $ gcloud resource-manager folders undelete 3589215982
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/undelete)

---
### `gcloud resource-manager folders update`

Update the display name of a folder

Updates the given folder with new folder name.

This command can fail for the following reasons:
  o There is no folder with the given ID.
  o The active account does not have permission to update the given
    folder.
  o The new display name is taken by another folder under this folder's
    parent.

**Synopsis:**
```
gcloud resource-manager folders update FOLDER_ID
    --display-name=DISPLAY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FOLDER_ID
   ID for the folder you want to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | New display name for the folder (unique under the same parent). |


**Examples:**
```bash
The following command updates a folder with the ID 123456789 to have the
name "Foo Bar and Grill":

    $ gcloud resource-manager folders update 123456789 \
        --display-name="Foo Bar and Grill"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/folders/update)

---
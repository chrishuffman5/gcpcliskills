# gcloud projects (top-level commands)

### `gcloud projects add-iam-policy-binding`

Add IAM policy binding for a project

Adds a policy binding to the IAM policy of a project, given a project ID
and the binding. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud projects add-iam-policy-binding PROJECT_ID --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Project resource - The project to add the IAM policy binding. This
represents a Cloud resource.

This must be specified.

  PROJECT_ID
     ID of the project or fully qualified identifier for the project.

     To set the project_id attribute:
     + provide the argument project_id on the command line.
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
To add an IAM policy binding for the role of roles/editor for the user
test-user@gmail.com on a project with identifier example-project-id-1, run:

    $ gcloud projects add-iam-policy-binding example-project-id-1 \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding for the role of roles/editor to the service
account test-proj1@example.domain.com on a project with identifier
example-project-id-1, run:

    $ gcloud projects add-iam-policy-binding example-project-id-1 \
        --member='serviceAccount:test-proj1@example.domain.com' \
        --role='roles/editor'

To add an IAM policy binding that expires at the end of the year 2021 for
the role of roles/browser and the user test-user@gmail.com on a project
with identifier example-project-id-1, run:

    $ gcloud projects add-iam-policy-binding example-project-id-1 \
        --member='user:test-user@gmail.com' --role='roles/browser' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2021,descrip\
    tion=Expires at midnight on 2021-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/add-iam-policy-binding)

---
### `gcloud projects create`

Create a new project

Creates a new project with the given project ID. By default, projects are
not created under a parent resource. To do so, use either the
--organization or --folder flag.

**Synopsis:**
```
gcloud projects create [PROJECT_ID] [--no-enable-cloud-apis]
    [--folder=FOLDER_ID] [--labels=[KEY=VALUE,...]] [--name=NAME]
    [--organization=ORGANIZATION_ID] [--set-as-default]
    [--tags=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[PROJECT_ID]
   ID for the project you want to create.

   Project IDs are immutable and can be set only during project creation.
   They must start with a lowercase letter and can have lowercase ASCII
   letters, digits or hyphens. Project IDs must be between 6 and 30
   characters.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-cloud-apis` |  |  | Enable cloudapis.googleapis.com during creation. Enabled by default, use --no-enable-cloud-apis to disable. |
| `--folder` | FOLDER_ID |  | ID for the folder to use as a parent |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--name` | NAME |  | Name for the project you want to create. If not specified, will use project id as name. |
| `--organization` | ORGANIZATION_ID |  | ID for the organization to use as a parent |
| `--set-as-default` |  |  | Set newly created project as [core/project] property. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing Note: Currently this field is in Preview. |


**Examples:**
```bash
The following command creates a project with ID example-foo-bar-1, name
Happy project and label type=happy:

    $ gcloud projects create example-foo-bar-1 --name="Happy project" \
        --labels=type=happy

By default, projects are not created under a parent resource. The following
command creates a project with ID example-2 with parent folders/12345:

    $ gcloud projects create example-2 --folder=12345

The following command creates a project with ID example-3 with parent
organizations/2048:

    $ gcloud projects create example-3 --organization=2048
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/create)

---
### `gcloud projects delete`

Delete a project

Deletes the project with the given project ID.

This command can fail for the following reasons:
  o The project specified does not exist.
  o The active account does not have IAM role role/owner or another IAM
    role with the resourcemanager.projects.delete permission for the given
    project.

See Access control for projects using IAM
(https://cloud.google.com/resource-manager/docs/access-control-proj) for
more information.

**Synopsis:**
```
gcloud projects delete PROJECT_ID_OR_NUMBER [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID_OR_NUMBER
   ID or number for the project you want to delete.
```

**Examples:**
```bash
The following command deletes the project with the ID example-foo-bar-1:

    $ gcloud projects delete example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/delete)

---
### `gcloud projects describe`

Show metadata for a project

Shows metadata for a project given a valid project ID.

This command can fail for the following reasons:
  o The project specified does not exist.
  o The active account does not have permission to access the given
    project.

**Synopsis:**
```
gcloud projects describe PROJECT_ID_OR_NUMBER [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID_OR_NUMBER
   ID or number for the project you want to describe.
```

**Examples:**
```bash
The following command prints metadata for a project with the ID
example-foo-bar-1:

    $ gcloud projects describe example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/describe)

---
### `gcloud projects get-ancestors`

Get the ancestors for a project

gcloud projects get-ancestors displays the ancestors for a project.
Projects may be grouped under folders and an organization. This comand will
print the folder and organization hierarchy for the given project.

**Synopsis:**
```
gcloud projects get-ancestors PROJECT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Project resource - The project for which to display ancestors. This
represents a Cloud resource.

This must be specified.

  PROJECT_ID
     ID of the project or fully qualified identifier for the project.

     To set the project_id attribute:
     + provide the argument project_id on the command line.
```

**Examples:**
```bash
To print the ancestors for a project with ID my-project, run:

    $ gcloud projects get-ancestors my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/get-ancestors)

---
### `gcloud projects get-ancestors-iam-policy`

Get IAM policies for a project and its ancestors

Get IAM policies for a project and its ancestors, given a project ID.

**Synopsis:**
```
gcloud projects get-ancestors-iam-policy PROJECT_ID [--include-deny]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Project resource - ID for the project you want to get IAM policy for. This
represents a Cloud resource.

This must be specified.

  PROJECT_ID
     ID of the project or fully qualified identifier for the project.

     To set the project_id attribute:
     + provide the argument project_id on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--include-deny` |  |  | Include deny policies on the project and its ancestors in the result |


**Examples:**
```bash
To get IAM policies for project example-project-id-1 and its ancestors,
run:

    $ gcloud projects get-ancestors-iam-policy example-project-id-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/get-ancestors-iam-policy)

---
### `gcloud projects get-iam-policy`

Get IAM policy for a project

Gets the IAM policy for a project, given a project ID.

**Synopsis:**
```
gcloud projects get-iam-policy PROJECT_ID_OR_NUMBER [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID_OR_NUMBER
   ID or number for the project you want to get IAM policy for.
```

**Examples:**
```bash
The following command prints the IAM policy for a project with the ID
example-project-id-1:

    $ gcloud projects get-iam-policy example-project-id-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/get-iam-policy)

---
### `gcloud projects list`

List projects accessible by the active account

Lists all active projects, where the active account has Owner, Editor,
Browser or Viewer permissions. Projects are listed in alphabetical order by
project name. Projects that have been deleted or are pending deletion are
not included.

You can specify the maximum number of projects to list using the --limit
flag.

**Synopsis:**
```
gcloud projects list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists the last five created projects, sorted
alphabetically by project ID:

    $ gcloud projects list --sort-by=projectId --limit=5

To list projects that have been marked for deletion:

    $ gcloud projects list --filter='lifecycleState:DELETE_REQUESTED'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/list)

---
### `gcloud projects remove-iam-policy-binding`

Remove IAM policy binding for a project

Removes a policy binding to the IAM policy of a project, given a project ID
and the binding. One binding consists of a member, a role and an optional
condition.

**Synopsis:**
```
gcloud projects remove-iam-policy-binding PROJECT_ID --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Project resource - The project to remove the IAM policy binding from. This
represents a Cloud resource.

This must be specified.

  PROJECT_ID
     ID of the project or fully qualified identifier for the project.

     To set the project_id attribute:
     + provide the argument project_id on the command line.
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
To remove an IAM policy binding for the role of roles/editor for the user
test-user@gmail.com on project with identifier example-project-id-1, run:

    $ gcloud projects remove-iam-policy-binding example-project-id-1 \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of roles/editor from all
authenticated users on project example-project-id-1, run:

    $ gcloud projects remove-iam-policy-binding example-project-id-1 \
        --member='allAuthenticatedUsers' --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2019-01-01T00:00:00Z")',
title='expires_end_of_2018', and description=Expires at midnight on
2018-12-31 for the role of roles/browser for the user test-user@gmail.com
on project with identifier example-project-id-1, run:

    $ gcloud projects remove-iam-policy-binding example-project-id-1 \
        --member='user:test-user@gmail.com' --role='roles/browser' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of roles/browser and for the user test-user@gmail.com on project with
identifier example-project-id-1, run:

    $ gcloud projects remove-iam-policy-binding example-project-id-1 \
        --member='user:test-user@gmail.com' --role='roles/browser' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/remove-iam-policy-binding)

---
### `gcloud projects set-iam-policy`

Set IAM policy for a project

Sets the IAM policy for a project, given a project ID and a file encoded in
JSON or YAML that contains the IAM policy.

**Synopsis:**
```
gcloud projects set-iam-policy PROJECT_ID_OR_NUMBER POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID_OR_NUMBER
   ID or number for the project you want to set IAM policy for.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for a project with the ID example-project-id-1:

    $ gcloud projects set-iam-policy example-project-id-1 policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/set-iam-policy)

---
### `gcloud projects undelete`

Undelete a project

Undeletes the project with the given project ID.

This command can fail for the following reasons:
  o There is no project with the given ID.
  o The active account does not have Owner or Editor permissions for the
    given project.

**Synopsis:**
```
gcloud projects undelete PROJECT_ID_OR_NUMBER [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID_OR_NUMBER
   ID or number for the project you want to undelete.
```

**Examples:**
```bash
The following command undeletes the project with the ID example-foo-bar-1:

    $ gcloud projects undelete example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/undelete)

---
### `gcloud projects update`

Update the name of a project

Update the name of the given project.

This command can fail for the following reasons:
  o There is no project with the given ID.
  o The active account does not have Owner or Editor permissions for the
    given project.

**Synopsis:**
```
gcloud projects update PROJECT_ID --name=NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   ID for the project you want to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | New name for the project. |


**Examples:**
```bash
The following command updates a project with the ID example-foo-bar-1 to
have the name Foo Bar & Grill:

    $ gcloud projects update example-foo-bar-1 --name="Foo Bar & Grill"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/projects/update)

---
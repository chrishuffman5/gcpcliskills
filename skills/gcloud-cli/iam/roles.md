# gcloud iam roles

create and manipulate roles

### `gcloud iam roles copy`

Create a role from an existing role

This command creates a role from an existing role.

**Synopsis:**
```
gcloud iam roles copy [--dest-organization=DEST_ORGANIZATION]
    [--dest-project=DEST_PROJECT] [--destination=DESTINATION]
    [--source=SOURCE] [--source-organization=SOURCE_ORGANIZATION]
    [--source-project=SOURCE_PROJECT] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dest-organization` | DEST_ORGANIZATION |  | The organization of the destination role. |
| `--dest-project` | DEST_PROJECT |  | The project of the destination role. |
| `--destination` | DESTINATION |  | The destination role ID for the new custom role. For example: viewer. |
| `--source` | SOURCE |  | The source role ID. For predefined roles, for example: roles/viewer. For custom roles, for example: myCompanyAdmin. |
| `--source-organization` | SOURCE_ORGANIZATION |  | The organization of the source role if it is an custom role. |
| `--source-project` | SOURCE_PROJECT |  | The project of the source role if it is an custom role. |


**Examples:**
```bash
To create a copy of an existing role spanner.databaseAdmin into an
organization with 1234567, run:

    $ gcloud iam roles copy --source="roles/spanner.databaseAdmin" \
        --destination=CustomViewer --dest-organization=1234567

To create a copy of an existing role spanner.databaseAdmin into a project
with PROJECT_ID, run:

    $ gcloud iam roles copy --source="roles/spanner.databaseAdmin" \
        --destination=CustomSpannerDbAdmin --dest-project=PROJECT_ID

To modify the newly created role see the roles update command.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/copy)

---
### `gcloud iam roles create`

Create a custom role for a project or an organization

This command creates a custom role with the provided information.

**Synopsis:**
```
gcloud iam roles create ROLE_ID
    (--organization=ORGANIZATION | --project=PROJECT_ID)
    [--file=FILE | --description=DESCRIPTION
      --permissions=PERMISSIONS --stage=STAGE --title=TITLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ROLE_ID
   ID of the custom role to create. You must also specify the
   --organization or --project flag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization of the role you want to create. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the role you want to create. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | _[At most one of these can be specified:]_ The JSON or YAML file with the IAM Role to create. See https://cloud.google.com/iam/reference/rest/v1/projects.roles. |


**Examples:**
```bash
To create a custom role ProjectUpdater from a YAML file, run:

    $ gcloud iam roles create ProjectUpdater --organization=12345 \
        --file=role_file_path

To create a custom role ProjectUpdater with flags, run:

    $ gcloud iam roles create ProjectUpdater --project=myproject \
        --title=ProjectUpdater \
        --description="Have access to get and update the project" \
        --permissions=resourcemanager.projects.get,\
    resourcemanager.projects.update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/create)

---
### `gcloud iam roles delete`

Delete a custom role from an organization or a project

This command deletes a role.

This command can fail for the following reasons:
  o The role specified does not exist.
  o The active user does not have permission to access the given role.

**Synopsis:**
```
gcloud iam roles delete ROLE_ID
    (--organization=ORGANIZATION | --project=PROJECT_ID)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ROLE_ID
   ID of the custom role to delete. You must also specify the
   --organization or --project flag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization of the role you want to delete. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the role you want to delete. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To delete the role ProjectUpdater of the organization 1234567, run:

    $ gcloud iam roles delete ProjectUpdater --organization=1234567

To delete the role ProjectUpdater of the project myproject, run:

    $ gcloud iam roles delete ProjectUpdater --project=myproject
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/delete)

---
### `gcloud iam roles describe`

Show metadata for a role

This command shows metadata for a role.

This command can fail for the following reasons:
  o The role specified does not exist.
  o The active user does not have permission to access the given role.

**Synopsis:**
```
gcloud iam roles describe ROLE_ID
    [--organization=ORGANIZATION | --project=PROJECT_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ROLE_ID
   ID of the role to describe. Curated roles example: roles/viewer. Custom
   roles example: CustomRole. For custom roles, you must also specify the
   --organization or --project flag.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ Organization of the role you want to describe. |
| `--project` | PROJECT_ID |  | _[At most one of these can be specified:]_ Project of the role you want to describe. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To print metadata for the role spanner.databaseAdmin of the organization
1234567, run:

    $ gcloud iam roles describe roles/spanner.databaseAdmin \
        --organization=1234567

To print metadata for the role spanner.databaseAdmin of the project
myproject, run:

    $ gcloud iam roles describe roles/spanner.databaseAdmin \
        --project=myproject

To print metadata for a predefined role, spanner.databaseAdmin, run:

    $ gcloud iam roles describe roles/spanner.databaseAdmin
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/describe)

---
### `gcloud iam roles list`

List predefined roles, or the custom roles for an organization or project

When an organization or project is specified, this command lists the custom
roles that are defined for that organization or project.

Otherwise, this command lists IAM's predefined roles.

**Synopsis:**
```
gcloud iam roles list [--show-deleted]
    [--organization=ORGANIZATION | --project=PROJECT_ID]
    [--filter=EXPRESSION] [--limit=LIMIT] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Show deleted roles by specifying this flag. |


**Examples:**
```bash
To list custom roles for the organization 12345, run:

    $ gcloud iam roles list --organization=12345

To list custom roles for the project myproject, run:

    $ gcloud iam roles list --project=myproject

To list all predefined roles, run:

    $ gcloud iam roles list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/list)

---
### `gcloud iam roles undelete`

Undelete a custom role from an organization or a project

This command undeletes a role. Roles that have been deleted for certain
long time can't be undeleted.

This command can fail for the following reasons:
  o The role specified does not exist.
  o The active user does not have permission to access the given role.

**Synopsis:**
```
gcloud iam roles undelete ROLE_ID
    (--organization=ORGANIZATION | --project=PROJECT_ID)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ROLE_ID
   ID of the custom role to undelete. You must also specify the
   --organization or --project flag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization of the role you want to undelete. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the role you want to undelete. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To undelete the role ProjectUpdater of the organization 1234567, run:

    $ gcloud iam roles undelete ProjectUpdater --organization=1234567

To undelete the role ProjectUpdater of the project myproject, run:

    $ gcloud iam roles undelete ProjectUpdater --project=myproject
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/undelete)

---
### `gcloud iam roles update`

Update an IAM custom role

This command updates an IAM custom role.

**Synopsis:**
```
gcloud iam roles update ROLE_ID
    (--organization=ORGANIZATION | --project=PROJECT_ID) [--file=FILE]
    [--add-permissions=ADD_PERMISSIONS --description=DESCRIPTION
      --permissions=PERMISSIONS
      --remove-permissions=REMOVE_PERMISSIONS --stage=STAGE --title=TITLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ROLE_ID
   ID of the custom role to update. You must also specify the
   --organization or --project flag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization of the role you want to update. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project of the role you want to update. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | The YAML file you want to use to update a role. Can not be specified with other flags except role-id. |


**Examples:**
```bash
To update the role ProjectUpdater from a YAML file, run:

    $ gcloud iam roles update ProjectUpdater --organization=123 \
        --file=role_file_path

To update the role ProjectUpdater with flags, run:

    $ gcloud iam roles update ProjectUpdater --project=myproject \
        --permissions=permission1,permission2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/roles/update)

---
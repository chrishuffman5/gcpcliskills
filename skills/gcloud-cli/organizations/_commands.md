# gcloud organizations (top-level commands)

### `gcloud organizations add-iam-policy-binding`

Add IAM policy binding for an organization

Adds a policy binding to the IAM policy of an organization, given an
organization ID and the binding. One binding consists of a member, a role,
and an optional condition.

**Synopsis:**
```
gcloud organizations add-iam-policy-binding ORGANIZATION --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Organization resource - The organization to add the IAM policy binding.
This represents a Cloud resource.

This must be specified.

  ORGANIZATION
     ID of the organization or fully qualified identifier for the
     organization.

     To set the organization attribute:
     + provide the argument organization on the command line.
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
To add an IAM policy binding with the role of 'roles/editor' for the user
'test-user@example.com' on an organization with identifier
'example-organization-id-1', run:

    $ gcloud organizations add-iam-policy-binding \
      example-organization-id-1 \
      --member='user:test-user@example.com' --role='roles/editor'

To add an IAM policy binding with the role of 'roles/editor' for the
service account 'my-iam-account@my-project.iam.gserviceaccount.com' on an
organization with identifier 'example-organization-id-1', run:

    $ gcloud organizations add-iam-policy-binding \
      example-organization-id-1 \
      --member='serviceAccount:my-iam-account@my-project.iam.gservicea\
    ccount.com' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/browser' and the user 'test-user@example.com' on an
organization with identifier 'example-organization-id-1', run:

    $ gcloud organizations add-iam-policy-binding \
      example-organization-id-1 \
      --member='user:test-user@example.com' --role='roles/browser' \
      --condition='expression=request.time <
    timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/organizations/add-iam-policy-binding)

---
### `gcloud organizations describe`

Show metadata for an organization

Shows metadata for an organization, given a valid organization ID. If an
organization domain is supplied instead, this command will attempt to find
the organization by domain name.

This command can fail for the following reasons:
  o The organization specified does not exist.
  o The active account does not have permission to access the given
    organization.
  o The domain name supplied does not correspond to a unique organization
    ID.

**Synopsis:**
```
gcloud organizations describe ORGANIZATION_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORGANIZATION_ID
   ID or domain for the organization you want to describe.
```

**Examples:**
```bash
The following command prints metadata for an organization with the ID
3589215982:

    $ gcloud organizations describe 3589215982

The following command prints metadata for an organization associated with
the domain example.com:

    $ gcloud organizations describe example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/organizations/describe)

---
### `gcloud organizations get-iam-policy`

Get IAM policy for an organization

Gets the IAM policy for an organization, given an organization ID.

If a domain is supplied instead of an organization ID, this command will
attempt to look up the organization ID associated with that domain.

**Synopsis:**
```
gcloud organizations get-iam-policy ORGANIZATION_ID [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORGANIZATION_ID
   ID or domain for the organization whose policy you want to get.
```

**Examples:**
```bash
The following command prints the IAM policy for an organization with the ID
123456789:

    $ gcloud organizations get-iam-policy 123456789

The following command prints the IAM policy for the organzation associated
with the domain example.com:

    $ gcloud organizations get-iam-policy example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/organizations/get-iam-policy)

---
### `gcloud organizations list`

List organizations accessible by the active account

Lists all organizations to which the user has access. Organizations are
listed in an unspecified order.

**Synopsis:**
```
gcloud organizations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/organizations/list)

---
### `gcloud organizations remove-iam-policy-binding`

Remove IAM policy binding for an organization

Removes a policy binding from the IAM policy of an organization, given an
organization ID and the binding. One binding consists of a member, a role,
and an optional condition.

**Synopsis:**
```
gcloud organizations remove-iam-policy-binding ORGANIZATION
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Organization resource - The organization to remove the IAM policy binding.
This represents a Cloud resource.

This must be specified.

  ORGANIZATION
     ID of the organization or fully qualified identifier for the
     organization.

     To set the organization attribute:
     + provide the argument organization on the command line.
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
'test-user@gmail.com' on organization with identifier
'example-organization-id-1', run:

    $ gcloud organizations remove-iam-policy-binding \
      example-organization-id-1 --member='user:test-user@gmail.com' \
      --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on organization 'example-organization-id-1', run:

    $ gcloud organizations remove-iam-policy-binding \
      example-organization-id-1 --member='allAuthenticatedUsers' \
      --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2019-01-01T00:00:00Z")',
title='expires_end_of_2018', and description='Expires at midnight on
2018-12-31' for the role of 'roles/browser' for the user
'test-user@gmail.com' on organization with identifier
'example-organization-id-1', run:

    $ gcloud organizations remove-iam-policy-binding \
      example-organization-id-1 --member='user:test-user@gmail.com' \
      --role='roles/browser' \
      --condition='expression=request.time <
    timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/browser' and for the user 'test-user@gmail.com' on organization
with identifier 'example-organization-id-1', run:

    $ gcloud organizations remove-iam-policy-binding \
      example-organization-id-1 --member='user:test-user@gmail.com' \
      --role='roles/browser' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/organizations/remove-iam-policy-binding)

---
### `gcloud organizations set-iam-policy`

Set IAM policy for an organization

Given an organization ID and a file encoded in JSON or YAML that contains
the IAM policy, this command will set the IAM policy for that organization.

**Synopsis:**
```
gcloud organizations set-iam-policy ORGANIZATION_ID POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORGANIZATION_ID
   ID or domain for the organization whose IAM policy you want to set.

POLICY_FILE
   JSON or YAML file containing the IAM policy.
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for an organization with the ID 123456789:

    $ gcloud organizations set-iam-policy 123456789 policy.json

The following command reads an IAM policy defined in a JSON file
policy.json and sets it for the organization associated with the domain
example.com:

    $ gcloud organizations set-iam-policy example.com policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/organizations/set-iam-policy)

---
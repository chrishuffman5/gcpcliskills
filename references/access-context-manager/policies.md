# gcloud access-context-manager policies

manage Access Context Manager policies

### `gcloud access-context-manager policies add-iam-policy-binding`

Add IAM policy binding for an access policy

Adds a policy binding to the IAM policy of an access policy. The binding
consists of a role, identity, and access policy.

**Synopsis:**
```
gcloud access-context-manager policies add-iam-policy-binding [POLICY]
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy to add the IAM binding. This
represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
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
To add an IAM policy binding for the role of roles/notebooks.admin for the
user 'test-user@gmail.com' on the access policy 'accessPolicies/123', run:

    $ gcloud access-context-manager policies add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/notebooks.admin' accessPolicies/123

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/add-iam-policy-binding)

---
### `gcloud access-context-manager policies create`

Create a new access policy

Create a new Access Context Manager policy. An Access Context Manager
policy, also known as an access policy, is a container for access levels
and VPC Service Controls service perimeters.

You can optionally specify either a folder or a project as a scope of an
access policy. A scoped policy only allows projects under that scope to be
restricted by any service perimeters defined with that policy. The scope
must be within the organization that this policy is associated with. You
can specify only one folder or project as the scope for an access policy.
If you don't specify a scope, then the scope extends to the entire
organization and any projects within the organization can be added to
service perimeters in this policy.

This command only creates an access policy. Access levels and service
perimeters need to be created explicitly.

**Synopsis:**
```
gcloud access-context-manager policies create --organization=ORGANIZATION
    --title=TITLE [--async] [--scopes=[SCOPES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | Parent organization for the access policies. |
| `--title` | TITLE |  | Short human-readable title of the access policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--scopes` | [SCOPES,...] |  | Folder or project on which this policy is applicable. You can specify only one folder or project as the scope and the scope must exist within the specified organization. If you don't specify a scope, the policy applies to the entire organization. |


**Examples:**
```bash
To create an access policy that applies to the entire organization, run:

    $ gcloud access-context-manager policies create \
        --organization=organizations/123 --title="My Policy"

To create an access policy that applies to the folder with the ID 345, run:

    $ gcloud access-context-manager policies create \
        --organization=organizations/123 --scopes=folders/345 \
        --title="My Folder Policy"

Only projects within this folder can be added to service perimeters within
this policy.

To create an access policy that applies only to the project with the
project number 567, run:

    $ gcloud access-context-manager policies create \
        --organization=organizations/123 --scopes=projects/567 \
        --title="My Project Policy"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/create)

---
### `gcloud access-context-manager policies delete`

Delete an access policy

Delete a given access policy.

**Synopsis:**
```
gcloud access-context-manager policies delete [POLICY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy you want to delete. This represents a
Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/delete)

---
### `gcloud access-context-manager policies describe`

Show details about an access policy

Show details about a given access policy.

**Synopsis:**
```
gcloud access-context-manager policies describe [POLICY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access level you want to show details about. This
represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/describe)

---
### `gcloud access-context-manager policies get-iam-policy`

Get the IAM policy for an access policy

gcloud access-context-manager policies get-iam-policy Displays the IAM
policy associated with an access policy. If formatted as JSON, the output
can be edited and used as a policy file for set-iam-policy. The output
includes an "etag" field identifying the version emitted and allowing
detection of concurrent policy updates; see $ {parent} set-iam-policy for
additional details.

**Synopsis:**
```
gcloud access-context-manager policies get-iam-policy [POLICY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy for which to display the IAM policy.
This represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Examples:**
```bash
To print the IAM policy for a given access policy, run:

    $ gcloud access-context-manager policies get-iam-policy \
        accessPolicies/1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/get-iam-policy)

---
### `gcloud access-context-manager policies list`

List access policies

List access policies.

**Synopsis:**
```
gcloud access-context-manager policies list --organization=ORGANIZATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ ID of the organization or fully qualified identifier for the organization. To set the organization attribute: + provide the argument --organization on the command line. |


**Examples:**
```bash
To list access policies, run the following command:

    $ gcloud access-context-manager policies list

This command prints a list of Access Policies in a tabular form:

    NAME      ORGANIZATION SCOPE        TITLE      ETAG
    MY_POLICY 12345        projects/123 My Policy  123abcdef
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/list)

---
### `gcloud access-context-manager policies remove-iam-policy-binding`

Remove IAM policy binding for an access policy

Removes a policy binding to the IAM policy of an access policy, given an
access policy ID and the binding.

**Synopsis:**
```
gcloud access-context-manager policies remove-iam-policy-binding [POLICY]
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy to remove the IAM binding. This
represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
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
'test-user@gmail.com' on the access policy 'accessPolicies/123', run:

    $ gcloud access-context-manager policies remove-iam-policy-binding \
        accessPolicies/123 --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/remove-iam-policy-binding)

---
### `gcloud access-context-manager policies set-iam-policy`

Set IAM policy for an access policy

Sets the IAM policy for a access policy, given access policy ID and a file
encoded in JSON or YAML that contains the IAM policy.

**Synopsis:**
```
gcloud access-context-manager policies set-iam-policy [POLICY] POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy to set the IAM policy for. This
represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for the access policy with the ID
accessPolicies/1234:

    $ gcloud access-context-manager policies set-iam-policy \
        accessPolicies/1234 policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/set-iam-policy)

---
### `gcloud access-context-manager policies update`

Update an existing access policy

Update an existing access policy.

**Synopsis:**
```
gcloud access-context-manager policies update [POLICY] [--title=TITLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy to update. This represents a Cloud
resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--title` | TITLE |  | Short human-readable title of the access policy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/policies/update)

---
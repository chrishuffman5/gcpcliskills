# gcloud resource-manager tags

create and manipulate tag keys, values and bindings


## `gcloud resource-manager tags bindings` — create and manipulate TagBindings
### `gcloud resource-manager tags bindings create`

Creates a TagBinding resource

Creates a TagBinding given the TagValue and the parent cloud resource the
TagValue will be attached to. The TagValue can be represented with its
numeric id or its namespaced name of
{parent_namespace}/{tag_key_short_name}/{tag_value_short_name}. The parent
resource should be represented with its full resource name. See:
https://cloud.google.com/apis/design/resource_names#full_resource_name.

**Synopsis:**
```
gcloud resource-manager tags bindings create --parent=PARENT
    --tag-value=TAG_VALUE [--async] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Full resource name of the resource to attach to the tagValue. |
| `--tag-value` | TAG_VALUE |  | Tag value name or namespaced name. The name should be in the form tagValues/{numeric_id}. The namespaced name should be in the form {org_id}/{tag_key_short_name}/{short_name} where short_name must be 1-63 characters, beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with dashes (-), underscores (), dots (.), and alphanumerics between. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | Region or zone of the resource to bind to the TagValue. This field is not required if the resource is a global resource like projects, folders and organizations. |


**Examples:**
```bash
To create a TagBinding between tagValues/123 and Project with name
//cloudresourcemanager.googleapis.com/projects/1234 run:

    $ gcloud resource-manager tags bindings create \
        --tag-value=tagValues/123 \
        --parent=//cloudresourcemanager.googleapis.com/projects/1234

To create a TagBinding between TagValue test under TagKey env and Project
with name //cloudresourcemanager.googleapis.com/projects/1234 run:

    $ gcloud resource-manager tags bindings create \
        --tag-value=789/env/test \
        --parent=//cloudresourcemanager.googleapis.com/projects/1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/bindings/create)

---
### `gcloud resource-manager tags bindings delete`

Deletes a TagBinding

Deletes a TagBinding given the TagValue and the parent resource that the
TagValue is attached to. The parent must be given as the full resource
name. See:
https://cloud.google.com/apis/design/resource_names#full_resource_name. The
TagValue can be represented with its numeric id or its namespaced name of
{parent_namespace}/{tag_key_short_name}/{tag_value_short_name}.

**Synopsis:**
```
gcloud resource-manager tags bindings delete --parent=PARENT
    --tag-value=TAG_VALUE [--async] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Full resource name of the resource attached to the tagValue. |
| `--tag-value` | TAG_VALUE |  | Tag value name or namespaced name. The name should be in the form tagValues/{numeric_id}. The namespaced name should be in the form {org_id}/{tag_key_short_name}/{short_name} where short_name must be 1-63 characters, beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with dashes (-), underscores (), dots (.), and alphanumerics between. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | Region or zone of the resource to unbind from the TagValue. This field is not required if the resource is a global resource like projects, folders and organizations. |


**Examples:**
```bash
To delete a TagBinding between tagValue/111 and Project with name
//cloudresourcemanager.googleapis.com/projects/1234 run:

    $ gcloud resource-manager tags bindings delete \
        --tag-value=tagValue/123 \
        --parent=//cloudresourcemanager.googleapis.com/projects/1234

To delete a binding between TagValue test under TagKey env that lives under
organizations/789 and Project with name
//cloudresourcemanager.googleapis.com/projects/1234 run:

    $ gcloud resource-manager tags bindings delete \
        --tag-value=789/env/test \
        --parent=//cloudresourcemanager.googleapis.com/projects/1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/bindings/delete)

---
### `gcloud resource-manager tags bindings list`

Lists TagBindings bound to the specified resource

When specifying a parent resource, the full name of the parent resource
must be used. See:
https://cloud.google.com/apis/design/resource_names#full_resource_name.

**Synopsis:**
```
gcloud resource-manager tags bindings list --parent=PARENT [--effective]
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Full resource name attached to the binding |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--effective` |  |  | Show all effective TagBindings on the resource. TagBindings applied at a higher level will be inherited to all descendants. |
| `--location` | LOCATION |  | Region or zone of the resource for listing TagBindings. This field should not be set if the resource is a global resource like projects, folders and organizations. |


**Examples:**
```bash
To list TagBindings for
'//cloudresourcemanager.googleapis.com/projects/123' run:

    $ gcloud resource-manager tags bindings list \
        --parent=//cloudresourcemanager.googleapis.com/projects/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/bindings/list)

---

## `gcloud resource-manager tags holds` — create and manipulate TagHolds
### `gcloud resource-manager tags holds create`

Create a TagHold resource

Create a TagHold under a TagValue, indicating that the TagValue is being
used by a holder (cloud resource) from an (optional) origin. The TagValue
can be represented with its numeric id or its namespaced name of
{parent_namespace}/{tag_key_short_name}/{tag_value_short_name}.

**Synopsis:**
```
gcloud resource-manager tags holds create PARENT --holder=HOLDER
    [--help-link=HELP_LINK] [--location=LOCATION] [--origin=ORIGIN]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PARENT
   Tag value name or namespaced name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--holder` | HOLDER |  | The name of the resource where the TagValue is being used. Must be less than 200 characters. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--help-link` | HELP_LINK |  | A URL where an end user can learn more about removing this hold. |
| `--location` | LOCATION |  | Region or zone where the TagHold will be stored. If not provided, the TagHold will be stored in a "global" region. |
| `--origin` | ORIGIN |  | An optional string representing the origin of this request. This field should include human-understandable information to distinguish origins from each other. Must be less than 200 characters. |


**Examples:**
```bash
To create a TagHold on tagValues/123, with holder cloud-resource-holder,
origin creator-origin, in region us-central1-a, with help link
www.example.help.link.com, run:

    $ gcloud resource-manager tags holds create tagValues/123 \
      --holder=cloud-resource-holder --origin=creator-origin \
      --help-link=www.example.help.link.com --location=us-central1-a

To create a TagHold under TagValue test under TagKey env in organization id
789, with holder cloud-resource-holder, run:

    $ gcloud resource-manager tags holds create 789/env/test \
      --holder=cloud-resource-holder
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/holds/create)

---
### `gcloud resource-manager tags holds delete`

Delete a TagHold

Delete a TagHold given its full name, specified as
tagValues/{tag_value_id}/tagHolds/{tag_hold_id}.

**Synopsis:**
```
gcloud resource-manager tags holds delete TAG_HOLD_NAME
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TAG_HOLD_NAME
   TagHold given its full name, specified as
   tagValues/{tag_value_id}/tagHolds/{tag_hold_id}
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Region where the TagHold is stored. If not provided, the API will attempt to find and delete the specified TagHold from the "global" region. |


**Examples:**
```bash
To delete a TagHold under tagValue/111 with id abc-123-def in region
us-central1-a, run:

    $ gcloud resource-manager tags holds delete \
        tagValue/111/tagHolds/abc-123-def --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/holds/delete)

---
### `gcloud resource-manager tags holds list`

List TagHolds under the specified TagValue

List TagHolds under a TagValue. The TagValue can be represented with its
numeric id or its namespaced name of
{parent_namespace}/{tag_key_short_name}/{tag_value_short_name}. Limited to
TagHolds stored in a single --location: if none is provided, the API will
assume the "global" location. Optional filters are --holder and --origin:
if provided, returned TagHolds' holder and origin fields must match the
exact flag value.

**Synopsis:**
```
gcloud resource-manager tags holds list PARENT [--holder=HOLDER]
    [--location=LOCATION] [--origin=ORIGIN] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PARENT
   TagValue resource name or namespaced name to list TagHolds for. This
   field should be in the form tagValues/<id> or
   <parent_namespace>/<tagkey_short_name>/<short_name>.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--holder` | HOLDER |  | The holder field of the TagHold to match exactly. If not provided, the API will return all matching TagHolds disregarding the holder field. |
| `--location` | LOCATION |  | Region where the matching TagHolds are stored. If not provided, the API will attempt to retrieve matching TagHolds from the "global" region. |
| `--origin` | ORIGIN |  | The origin field of the TagHold to match exactly. If not provided, the API will return all matching TagHolds disregarding the origin field. |


**Examples:**
```bash
To list TagHolds for tagValues/456 in us-central1-a, run:

    $ gcloud resource-manager tags holds list tagValues/456 \
        --location=us-central1-a

To list TagHolds for tagValues/456, with holder cloud-holder-resource and
origin creator-origin, run:

    $ gcloud resource-manager tags holds list tagValues/456 \
        --holder=cloud-holder-resource --origin=creator-origin
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/holds/list)

---

## `gcloud resource-manager tags keys` — create and manipulate TagKeys
### `gcloud resource-manager tags keys add-iam-policy-binding`

Adds a policy binding to the IAM policy of a TagKey

Adds the IAM policy binding for a TagKey resource given the binding and an
identifier for the TagKey. The identifier can be the TagKey's parent/short
name or the TagKey's ID in the form: tagKeys/{numeric_id}.

**Synopsis:**
```
gcloud resource-manager tags keys add-iam-policy-binding RESOURCE_NAME
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
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
'test-user@gmail.com' on the Tag Key 'tagKeys/123', run:

    $ gcloud resource-manager tags keys add-iam-policy-binding \
        tagKeys/123 --member='user:test-user@gmail.com' \
        --role='roles/editor'

To add an IAM policy binding for a Tag Key with the name 'env' under
'organization/456' for the role of 'roles/resourcemanager.tagUser' for the
user 'test-user@gmail.com', run:

    $ gcloud resource-manager tags keys add-iam-policy-binding 456/env \
        --member='user:test-user@gmail.com' \
        --role='roles/resourcemanager.tagUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/add-iam-policy-binding)

---
### `gcloud resource-manager tags keys create`

Creates a TagKey resource under the specified tag parent

**Synopsis:**
```
gcloud resource-manager tags keys create (SHORT_NAME --parent=PARENT)
    [--async] [--description=DESCRIPTION] [--purpose=PURPOSE]
    [--purpose-data=[network=NETWORK],[organization=ORGANIZATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TagKey.

This must be specified.

  SHORT_NAME
     User specified, friendly name of the TagKey or TagValue. The field
     must be 1-63 characters, beginning and ending with an alphanumeric
     character ([a-z0-9A-Z]) with dashes (-), underscores ( _ ), dots (.),
     and alphanumerics between.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --parent=PARENT
     Parent of the TagKey in the form of organizations/{org_id}.

     This flag argument must be specified if any of the other arguments in
     this group are specified.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-assigned description of the TagKey or TagValue. Must not exceed 256 characters. |
| `--purpose` | one of: GCE_FIREWALL, DATA_GOVERNANCE |  | Purpose specifier of the TagKey that can only be set on creation. Specifying this field adds additional validation from the policy system that corresponds to the purpose. PURPOSE must be one of: GCE_FIREWALL, DATA_GOVERNANCE. |
| `--purpose-data` | [network=NETWORK],[organization=ORGANIZATION] |  | Purpose data of the TagKey that can only be set on creation. This data is validated by the policy system that corresponds to the purpose. |


**Examples:**
```bash
To create a TagKey with the name env under 'organizations/123' with
description 'description', run:

    $ gcloud resource-manager tags keys create env \
    --parent=organizations/123 --description=description
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/create)

---
### `gcloud resource-manager tags keys delete`

Deletes the specified TagKey resource

Deletes the TagKey resource given the TagKey's parent and short name or the
TagKey's numeric id.

**Synopsis:**
```
gcloud resource-manager tags keys delete RESOURCE_NAME [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a TagKey with id 123, run:

    $ gcloud resource-manager tags keys delete tagKeys/123

To delete a TagKey named env under organization 456, run:

    $ gcloud resource-manager tags keys delete 456/env
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/delete)

---
### `gcloud resource-manager tags keys describe`

Describes a TagKey resource

Gets metadata for a TagKey resource given the TagKey's resource name or
namespaced name.

**Synopsis:**
```
gcloud resource-manager tags keys describe RESOURCE_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Examples:**
```bash
To describe a TagKey with id '123', run:

    $ gcloud resource-manager tags keys describe tagkeys/123

To describe a TagKey with the name 'env' under organizations '456', run:

    $ gcloud resource-manager tags keys describe 456/env
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/describe)

---
### `gcloud resource-manager tags keys get-iam-policy`

Gets the IAM policy for a TagKey resource

Returns the IAM policy for a TagKey resource given the TagKey's display
name and parent or the TagKey's numeric id.

**Synopsis:**
```
gcloud resource-manager tags keys get-iam-policy RESOURCE_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Examples:**
```bash
To get the IAM policy for a TagKey with id '123', run:

    $ gcloud resource-manager tags keys get-iam-policy tagKeys/123

To get the IAM policy for a TagKey with the name 'env' under
'organizations/456', run:

    $ gcloud resource-manager tags keys get-iam-policy 456/env
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/get-iam-policy)

---
### `gcloud resource-manager tags keys list`

Lists TagKeys under the specified parent resource

**Synopsis:**
```
gcloud resource-manager tags keys list --parent=PARENT
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Parent of the TagKey in the form of organizations/{org_id}. |


**Examples:**
```bash
To list all the TagKeys under 'organizations/123', run:

    $ gcloud resource-manager tags keys list --parent='organizations/123'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/list)

---
### `gcloud resource-manager tags keys remove-iam-policy-binding`

Removes a policy binding from the IAM policy of a TagKey

Removes an IAM policy binding for a TagKey resource given the binding and
an identifier for the TagKey. The identifier can be the TagKey's
parent/short name or the TagKey's ID in the form: tagKeys/{numeric_id}.

**Synopsis:**
```
gcloud resource-manager tags keys remove-iam-policy-binding RESOURCE_NAME
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
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
'test-user@gmail.com' on the tagKey 'tagKeys/123', run:

    $ gcloud resource-manager tags keys remove-iam-policy-binding \
        tagKeys/123 --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding for a TagKey with the name 'env' under
'organization/456' for the role of 'roles/resourcemanager.tagUser' for the
user 'test-user@gmail.com', run:

    $ gcloud resource-manager tags keys remove-iam-policy-binding \
        456/env --member='user:test-user@gmail.com' \
        --role='roles/resourcemanager.tagUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/remove-iam-policy-binding)

---
### `gcloud resource-manager tags keys set-iam-policy`

Sets IAM policy for a TagKey resource

Sets the IAM policy for a TagKey resource given the TagKey's display name
and parent or the TagKey's numeric id and a file encoded in JSON or YAML
that contains the IAM policy.

**Synopsis:**
```
gcloud resource-manager tags keys set-iam-policy RESOURCE_NAME POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.
   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for a TagKey with id '123' and IAM policy defined in
a YAML file '/path/to/my_policy.yaml', run:

    $ gcloud resource-manager tags keys set-iam-policy tagKeys/123 \
        /path/to/my_policy.yaml

To set the IAM policy for a tagKey with the short_name 'env' under
'organization/456' and IAM policy defined in a JSON file
'/path/to/my_policy.json', run:

    $ gcloud resource-manager tags keys set-iam-policy 456/env \
        /path/to/my_policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/set-iam-policy)

---
### `gcloud resource-manager tags keys update`

Updates the specified TagKey resource's description

Updates the TagKey's description given the TagKey's parent and short name
or the TagKey's numeric id.

**Synopsis:**
```
gcloud resource-manager tags keys update RESOURCE_NAME [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-assigned description of the TagKey or TagValue. Must not exceed 256 characters. |


**Examples:**
```bash
To update a TagKey with id 123, run:

    $ gcloud resource-manager tags keys update tagKeys/123 \
        --description=foobar --allowed-values-regex=.*

To update a TagKey named env under organization 456, run:

    $ gcloud resource-manager tags keys update 456/env \
        --description=foobar --allowed-values-regex=.*
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/keys/update)

---

## `gcloud resource-manager tags values` — create and manipulate TagValues
### `gcloud resource-manager tags values add-iam-policy-binding`

Adds a policy binding to the IAM policy of a TagValue

Adds the IAM policy binding for a TagValue resource given the binding and
an identifier for the TagValue. The identifier can be the TagValue's
namespaced name in the form
<parent_namespace>/<tagkey_short_name>/<tagvalue_short_name> or the
TagValue's ID in the form: tagValues/{numeric_id}.

**Synopsis:**
```
gcloud resource-manager tags values add-iam-policy-binding RESOURCE_NAME
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
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
'test-user@gmail.com' on the Tag Value 'tagValues/111', run:

    $ gcloud resource-manager tags values add-iam-policy-binding \
        tagValues/111 --member='user:test-user@gmail.com' \
        --role='roles/editor'

To add an IAM policy binding for a Tag Value with the name 'dev' under
'organization/456/env' for the role of 'roles/resourcemanager.tagUser' for
the user 'test-user@gmail.com', run:

    $ gcloud resource-manager tags values add-iam-policy-binding \
        456/env/dev --member='user:test-user@gmail.com' \
        --role='roles/resourcemanager.tagUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/add-iam-policy-binding)

---
### `gcloud resource-manager tags values create`

Creates a TagValue resource

Creates a TagValue resource given the short_name and description (optional)
as well as the parent, the of the TagValue. The parent of the TagValue can
be a TagKey or TagValue. The parent can be specified by its numeric ID or
its namespaced name.

**Synopsis:**
```
gcloud resource-manager tags values create (SHORT_NAME --parent=PARENT)
    [--async] [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TagValue.

This must be specified.

  SHORT_NAME
     User specified, friendly name of the TagKey or TagValue. The field
     must be 1-63 characters, beginning and ending with an alphanumeric
     character ([a-z0-9A-Z]) with dashes (-), underscores ( _ ), dots (.),
     and alphanumerics between.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --parent=PARENT
     Parent of the TagValue in either in the form of tagKeys/{id} or
     {org_id}/{tagkey_short_name}

     This flag argument must be specified if any of the other arguments in
     this group are specified.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-assigned description of the TagKey or TagValue. Must not exceed 256 characters. |


**Examples:**
```bash
To create a TagValue with the short name test and the description
descriptio under a TagKey with a short name env under organizations/123,
run:

    $ gcloud resource-manager tags values create test --parent=123/env \
        --description=description

To create a TagValue with the short name test under TagKey with id 456,
run:

    $ gcloud resource-manager tags values create test \
        --parent=tagKeys/456 --description=description
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/create)

---
### `gcloud resource-manager tags values delete`

Deletes the specified TagValue resource

Deletes the TagValue resource given the TagValue's parent and short name or
the TagValue's numeric id.

**Synopsis:**
```
gcloud resource-manager tags values delete RESOURCE_NAME [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a TagValue with id 123, run:

    $ gcloud resource-manager tags values delete tagValues/123

To delete a TagValue named dev with tagKey env under organization 456, run:

    $ gcloud resource-manager tags values delete 456/env/dev
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/delete)

---
### `gcloud resource-manager tags values describe`

Describes a TagValue resource

Gets metadata for a TagValue resource given the TagValue's resource name or
namespaced name.

**Synopsis:**
```
gcloud resource-manager tags values describe RESOURCE_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Examples:**
```bash
To describe a TagValue with id 123, run:

    $ gcloud resource-manager tags values describe tagValues/123

To describe a TagValue with name dev with the tagKey env under
organizations 456, run:

    $ gcloud resource-manager tags values describe 456/env/dev
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/describe)

---
### `gcloud resource-manager tags values get-iam-policy`

Gets the IAM policy for a TagValue resource

Returns the IAM policy for a TagValue resource given the TagValue's short
name and parent or the TagValue's numeric id.

**Synopsis:**
```
gcloud resource-manager tags values get-iam-policy RESOURCE_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Examples:**
```bash
To get the IAM policy for a TagValue with id '123', run:

    $ gcloud resource-manager tags values get-iam-policy tagValues/123

To get the IAM policy for a TagValue with the name 'dev' under
'organizations/456' and tagKey parent 'env', run:

    $ gcloud resource-manager tags values get-iam-policy 456/env/dev
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/get-iam-policy)

---
### `gcloud resource-manager tags values list`

Lists TagValues under the specified parent resource

**Synopsis:**
```
gcloud resource-manager tags values list --parent=PARENT
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Parent of the TagValue in either in the form of tagKeys/{id} or {org_id}/{tagkey_short_name} |


**Examples:**
```bash
To list all the TagValues under organizations/123/env, run:

    $ gcloud resource-manager tags values list --parent=123/env
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/list)

---
### `gcloud resource-manager tags values remove-iam-policy-binding`

Removes a policy binding from the IAM policy of a TagValue

Removes an IAM policy binding for a TagValue resource given the binding and
an identifier for the TagValue. The identifier can be the TagValue's
namespaced name in the form
<parent_namespace>/<tagkey_short_name>/<tagvalue_short_name> or the
TagValue's ID in the form: tagValues/{numeric_id}.

**Synopsis:**
```
gcloud resource-manager tags values remove-iam-policy-binding RESOURCE_NAME
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
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
'test-user@gmail.com' on the tagValue 'tagValues/111', run:

    $ gcloud resource-manager tags values remove-iam-policy-binding \
        tagValues/111 --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding for a TagValue with the name 'dev' under
'organization/456/env' for the role of 'roles/resourcemanager.tagUser' for
the user 'test-user@gmail.com', run:

    $ gcloud resource-manager tags values remove-iam-policy-binding \
        456/env/dev --member='user:test-user@gmail.com' \
        --role='roles/resourcemanager.tagUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/remove-iam-policy-binding)

---
### `gcloud resource-manager tags values set-iam-policy`

Sets IAM policy for a TagValue resource

Sets the IAM policy for a TagValue resource given the TagValue's short name
name and parent or the TagValue's numeric id and a file encoded in JSON or
YAML that contains the IAM policy.

**Synopsis:**
```
gcloud resource-manager tags values set-iam-policy RESOURCE_NAME
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.
   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for a TagValue with id '111' and IAM policy defined
in a YAML file '/path/to/my_policy.yaml', run:

    $ gcloud resource-manager tags values set-iam-policy tagValues/111 \
        /path/to/my_policy.yaml

To set the IAM policy for a tagValue with the short_name 'dev' under
'organization/456' and tag key short name 'env' and IAM policy defined in a
JSON file '/path/to/my_policy.json', run:

    $ gcloud resource-manager tags values set-iam-policy 456/env/dev \
        /path/to/my_policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/set-iam-policy)

---
### `gcloud resource-manager tags values update`

Updates the specified TagValue resource's description

Updates the TagValue's description given the TagValue's namespaced name
<parent_namespace>/<tagkey_short_name>/<short_name> or the TagValue's
numeric id tagValues/<id>

**Synopsis:**
```
gcloud resource-manager tags values update RESOURCE_NAME [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE_NAME
   Resource name or namespaced name. The resource name should be in the
   form {resource_type}/{numeric_id}. The namespaced name should be in the
   form {org_id}/{short_name} where short_name must be 1-63 characters,
   beginning and ending with an alphanumeric character ([a-z0-9A-Z]) with
   dashes (-), underscores ( _ ), dots (.), and alphanumerics between.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | User-assigned description of the TagKey or TagValue. Must not exceed 256 characters. |


**Examples:**
```bash
To update a TagValue with id 123, run:

    $ gcloud resource-manager tags values update tagValues/123 \
        --description="foobar"

To update a TagValue named dev with the tagKey env under organization 456,
run:

    $ gcloud resource-manager tags values update 465/env/dev \
        --description="foobar"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/tags/values/update)

---
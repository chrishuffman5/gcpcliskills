# gcloud kms ekm-config

update and retrieve the EkmConfig

### `gcloud kms ekm-config add-iam-policy-binding`

Add IAM policy binding to an EkmConfig

Adds a policy binding to the IAM policy of a kms EkmConfig. A binding
consists of at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud kms ekm-config add-iam-policy-binding --location=LOCATION
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--member` | PRINCIPAL |  | _[This must be specified.]_ The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | _[This must be specified.]_ Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
test-user@gmail.com on the EkmConfig with location us-central1, run:

    $ gcloud kms ekm-config add-iam-policy-binding \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2022 for
the role of 'roles/editor' and the user test-user@gmail.com and location
us-central1, run:

    $ gcloud kms ekm-config add-iam-policy-binding \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor' --condition='expression=request.time <
    timestamp("2023-01-01T00:00:00Z"),title=expires_end_of_2022,description=Expires
    at midnight on 2022-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-config/add-iam-policy-binding)

---
### `gcloud kms ekm-config describe`

Describe the EkmConfig

gcloud kms ekm-config describe can be used to retrieve the EkmConfig.

**Synopsis:**
```
gcloud kms ekm-config describe --location=LOCATION [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
The following command retrieves the EkmConfig in us-east1 for the current
project:

    $ gcloud kms ekm-config describe --location=us-east1

The following command retrieves the EkmConfig for its project foo and
location us-east1:

    $ gcloud kms ekm-config describe \
        --location="projects/foo/locations/us-east1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-config/describe)

---
### `gcloud kms ekm-config get-iam-policy`

Get the IAM policy for an EkmConfig

Gets the IAM policy for the given location.

Returns an empty policy if the resource does not have a policy set.

**Synopsis:**
```
gcloud kms ekm-config get-iam-policy --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
The following command gets the IAM policy for the EkmConfig within the
location us-central1:

    $ gcloud kms ekm-config get-iam-policy --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-config/get-iam-policy)

---
### `gcloud kms ekm-config remove-iam-policy-binding`

Remove IAM policy binding from an EkmConfig

Removes a policy binding from the IAM policy of a kms EkmConfig. A binding
consists of at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud kms ekm-config remove-iam-policy-binding --location=LOCATION
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--member` | PRINCIPAL |  | _[This must be specified.]_ The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | _[This must be specified.]_ The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on the EkmConfig with location us-central1, run:

    $ gcloud kms ekm-config remove-iam-policy-binding \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2023-01-01T00:00:00Z")',
title='expires_end_of_2022', and description='Expires at midnight on
2022-12-31' for the role of 'roles/editor' for the user
'test-user@gmail.com' on the EkmConfig with location us-central1, run:

    $ gcloud kms ekm-config remove-iam-policy-binding \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor' --condition='expression=request.time <
    timestamp("2023-01-01T00:00:00Z"),title=expires_end_of_2022,description=Expires
    at midnight on 2022-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/editor' and for the user 'test-user@gmail.com' on the EkmConfig
with location us-central1, run:

    $ gcloud kms ekm-config remove-iam-policy-binding laplace \
        --location='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/editor' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-config/remove-iam-policy-binding)

---
### `gcloud kms ekm-config set-iam-policy`

Set the IAM policy for an EkmConfig

Sets the IAM policy for the EkmConfig in a location as defined in a JSON or
YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud kms ekm-config set-iam-policy POLICY_FILE --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   JSON or YAML file with the IAM policy
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the EkmConfig with location us-central1:

    $ gcloud kms ekm-config set-iam-policy policy.json \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-config/set-iam-policy)

---
### `gcloud kms ekm-config update`

Update the EkmConfig

gcloud kms ekm-config update can be used to update the EkmConfig. Applies
to all CryptoKeys and CryptoKeyVersions with a protection level of external
vpc.

**Synopsis:**
```
gcloud kms ekm-config update --location=LOCATION
    [--default-ekm-connection=DEFAULT_EKM_CONNECTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--default-ekm-connection` | DEFAULT_EKM_CONNECTION |  | The resource name of the EkmConnection to be used as the default EkmConnection for all external-vpc CryptoKeys in a project and location. Can be an empty string to remove the default EkmConnection. |


**Examples:**
```bash
The following command sets the default ekm-connection to laplace for its
project foo and location us-east1:

    $ gcloud kms ekm-config update --location=us-east1 \
        --default-ekm-connection="projects/foo/locations/us-east1/ekmCon\
    nections/laplace"

The following command removes the default-ekm-connection in us-east1 for
the current project:

    $ gcloud kms ekm-config update --location=us-east1 \
        --default-ekm-connection=""
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-config/update)

---
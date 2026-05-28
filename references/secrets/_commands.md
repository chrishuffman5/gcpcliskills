# gcloud secrets (top-level commands)

### `gcloud secrets add-iam-policy-binding`

Add IAM policy binding to a secret

Add an IAM policy binding to the IAM policy of a secret. One binding
consists of a member and a role.

**Synopsis:**
```
gcloud secrets add-iam-policy-binding SECRET --member=PRINCIPAL --role=ROLE
    [--location=LOCATION]
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - Name of the secret for which to add the IAM policy
binding. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of
'roles/secretmanager.secretAccessor' for the user 'test-user@gmail.com' on
my-secret, run:

    $ gcloud secrets add-iam-policy-binding my-secret \
        --member='user:test-user@gmail.com' \
        --role='roles/secretmanager.secretAccessor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/add-iam-policy-binding)

---
### `gcloud secrets create`

Create a new secret

Create a secret with the given name and creates a secret version with the
given data, if any. If a secret already exists with the given name, this
command will return an error.

**Synopsis:**
```
gcloud secrets create SECRET [--data-file=PATH] [--labels=[KEY=VALUE,...]]
    [--location=LOCATION] [--regional-kms-key-name=KMS-KEY-NAME]
    [--set-annotations=[KEY=VALUE,...]] [--tags=[KEY=VALUE,...]]
    [--topics=[TOPICS,...]] [--version-destroy-ttl=VERSION-DESTROY-TTL]
    [--expire-time=EXPIRE-TIME | --ttl=TTL]
    [--next-rotation-time=NEXT_ROTATION_TIME
      --rotation-period=ROTATION_PERIOD]
    [--replication-policy-file=REPLICATION-POLICY-FILE
      | --kms-key-name=KMS-KEY-NAME
      --locations=[LOCATION,...] --replication-policy=POLICY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to create. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-file` | PATH |  | File path from which to read secret data. Set this to "-" to read the secret data from stdin. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--regional-kms-key-name` | KMS-KEY-NAME |  | _[+ provide the argument --location on the command line.]_ Regional KMS key with which to encrypt and decrypt the secret. Only valid for regional secrets. |
| `--tags` | [KEY=VALUE,...] |  | _[Annotations will be removed first.]_ List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |
| `--topics` | [TOPICS,...] |  | _[Annotations will be removed first.]_ List of Pub/Sub topics to configure on the secret. |
| `--version-destroy-ttl` | VERSION-DESTROY-TTL |  | _[Annotations will be removed first.]_ Secret Version Time To Live (TTL) after destruction request. For secret with TTL>0, version destruction does not happen immediately on calling destroy; instead, the version goes to a disabled state and destruction happens after the TTL expires. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
Create a secret with an automatic replication policy without creating any
versions:

    $ gcloud secrets create my-secret

Create a new secret named 'my-secret' with an automatic replication policy
and data from a file:

    $ gcloud secrets create my-secret --data-file=/tmp/secret

Create a new secret named 'my-secret' in 'us-central1' with data from a
file:

    $ gcloud secrets create my-secret --data-file=/tmp/secret \
        --replication-policy=user-managed --locations=us-central1

Create a new secret named 'my-secret' in 'us-central1' and 'us-east1' with
the value "s3cr3t":

    $ printf "s3cr3t" | gcloud secrets create my-secret --data-file=- \
        --replication-policy=user-managed \
        --locations=us-central1,us-east1

Create a new secret named 'my-secret' in 'us-central1' and 'us-east1' with
the value "s3cr3t" in PowerShell (Note: PowerShell will add a newline to
the resulting secret):

    $ Write-Output "s3cr3t" | gcloud secrets create my-secret \
        --data-file=- --replication-policy=user-managed \
        --locations=us-central1,us-east1

Create a secret with an automatic replication policy and a next rotation
time:

    $ gcloud secrets create my-secret \
        --next-rotation-time="2030-01-01T15:30:00-05:00"

Create a secret with an automatic replication policy and a rotation period:

    $ gcloud secrets create my-secret \
        --next-rotation-time="2030-01-01T15:30:00-05:00" \
        --rotation-period="7200s"

Create a secret with delayed secret version destroy enabled:

    $ gcloud secrets create my-secret --version-destroy-ttl="86400s"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/create)

---
### `gcloud secrets delete`

Delete a secret

Delete a secret and destroy all secret versions. This action is
irreversible. If the given secret does not exist, this command will
succeed, but the operation will be a no-op.

**Synopsis:**
```
gcloud secrets delete SECRET [--etag=ETAG] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to delete. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Current entity tag (ETag) of the secret. If specified, the secret is deleted only if the ETag provided matches the current secret's ETag. |


**Examples:**
```bash
Delete a secret my-secret:

    $ gcloud secrets delete my-secret

Delete a secret my-secret using an etag:

    $ gcloud secrets delete my-secret --etag=123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/delete)

---
### `gcloud secrets describe`

Describe a secret's metadata

Describe a secret's metadata.

**Synopsis:**
```
gcloud secrets describe SECRET [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
Describe metadata of the secret named 'my-secret':

    $ gcloud secrets describe my-secret
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/describe)

---
### `gcloud secrets get-iam-policy`

Get the IAM policy for the secret

Displays the IAM policy associated with the secret. If formatted as JSON,
the output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates.

Run gcloud secrets set-iam-policy for additional details.

**Synopsis:**
```
gcloud secrets get-iam-policy SECRET [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - Name of the secret from which to get IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To print the IAM policy for secret named 'my-secret', run:

    $ gcloud secrets get-iam-policy my-secret
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/get-iam-policy)

---
### `gcloud secrets list`

List all secret names

List all secret names. This command only returns the secret's names, not
their secret data. To learn about retrieving a secret's data, run $ gcloud
secrets versions access --help.

**Synopsis:**
```
gcloud secrets list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
List secret names.

    $ gcloud secrets list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/list)

---
### `gcloud secrets remove-iam-policy-binding`

Remove IAM policy binding for a secret

Removes a policy binding from the IAM policy of a secret. One binding
consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.

**Synopsis:**
```
gcloud secrets remove-iam-policy-binding SECRET --member=PRINCIPAL
    --role=ROLE [--location=LOCATION]
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - Name of the secret from which to remove IAM policy
binding. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/viewer' for the user
'test-user@gmail.com' on the my-secret, run:

    $ gcloud secrets remove-iam-policy-binding my-secret \
        --member='user:test-user@gmail.com' --role='roles/viewer'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/remove-iam-policy-binding)

---
### `gcloud secrets set-iam-policy`

Set the IAM policy binding for a secret

Sets the IAM policy for the given secret as defined in a JSON or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud secrets set-iam-policy SECRET POLICY_FILE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - Name of the secret for which to set the IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the secret 'my-secret':

    $ gcloud secrets set-iam-policy my-secret policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/set-iam-policy)

---
### `gcloud secrets update`

Update a secret's metadata

Update a secret's metadata (e.g. labels). This command will return an error
if given a secret that does not exist.

**Synopsis:**
```
gcloud secrets update SECRET [--etag=ETAG] [--location=LOCATION]
    [--update-labels=[KEY=VALUE,...]]
    [--add-topics=[ADD-TOPICS,...] | --clear-topics
      | --remove-topics=[REMOVE-TOPICS,...]]
    [--clear-annotations | --remove-annotations=[KEY,...]
      | --update-annotations=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-version-aliases | --remove-version-aliases=[KEY,...]
      | --update-version-aliases=[KEY=VALUE,...]]
    [--expire-time=EXPIRE-TIME | --remove-expiration | --ttl=TTL]
    [--next-rotation-time=NEXT_ROTATION_TIME --remove-next-rotation-time
      --remove-rotation-period
      --remove-rotation-schedule --rotation-period=ROTATION_PERIOD]
    [--regional-kms-key-name=REGIONAL-KMS-KEY-NAME
      | --remove-regional-kms-key-name]
    [--remove-version-destroy-ttl
      | --version-destroy-ttl=VERSION-DESTROY-TTL] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to update. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Current entity tag (ETag) of the secret. If specified, the secret is updated only if the ETag provided matches the current secret's ETag. |
| `--update-labels` | [KEY=VALUE,...] |  | _[+ provide the argument --location on the command line.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update the label of a secret named my-secret.

    $ gcloud secrets update my-secret --update-labels=foo=bar

Update the label of a secret using an etag.

    $ gcloud secrets update my-secret --update-labels=foo=bar --etag=123

Update a secret to have a next-rotation-time:

    $ gcloud secrets update my-secret \
        --next-rotation-time="2030-01-01T15:30:00-05:00"

Update a secret to have a next-rotation-time and rotation-period:

    $ gcloud secrets update my-secret \
        --next-rotation-time="2030-01-01T15:30:00-05:00" \
        --rotation-period="7200s"

Update a secret to remove the next-rotation-time:

    $ gcloud secrets update my-secret --remove-next-rotation-time

Update a secret to clear rotation policy:

    $ gcloud secrets update my-secret --remove-rotation-schedule

Update version destroy ttl of a secret:

    $ gcloud secrets update my-secret --version-destroy-ttl="86400s"

Disable delayed secret version destroy:

    $ gcloud secrets update my-secret --remove-version-destroy-ttl
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/update)

---
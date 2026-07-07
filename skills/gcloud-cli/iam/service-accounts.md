# gcloud iam service-accounts

create and manipulate service accounts

### `gcloud iam service-accounts add-iam-policy-binding`

Add an IAM policy binding to an IAM service account

Add an IAM policy binding to an IAM service account. A binding consists of
at least one member, a role, and an optional condition. Adding a binding to
a service account grants the specified member the specified role on the
service account.

When managing IAM roles, you can treat a service account either as a
resource or as an identity. This command adds an IAM policy binding to a
service account resource. There are other gcloud commands to manage IAM
policies for other types of resources. For example, to manage IAM policies
on a project, use the $ gcloud projects commands.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts add-iam-policy-binding SERVICE_ACCOUNT
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceAccount resource - The service account to which the IAM policy
binding is being added. Note that the user, group or service account in
the --member flag is being granted access to this service account. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_account on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_ACCOUNT
     ID of the serviceAccount or fully qualified identifier for the
     serviceAccount.

     To set the service_account attribute:
     + provide the argument service_account on the command line.
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
'test-user@gmail.com' on a service account with identifier
'my-iam-account@my-project.iam.gserviceaccount.com', run:

    $ gcloud iam service-accounts add-iam-policy-binding \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding for the role of 'roles/editor' to the service
account 'test-proj1@example.domain.com', run:

    $ gcloud iam service-accounts add-iam-policy-binding \
        test-proj1@example.domain.com \
        --member='serviceAccount:test-proj1@example.domain.com' \
        --role='roles/editor'

To add an IAM policy binding for the role of 'roles/editor' for all
authenticated users on a service account with identifier
'my-iam-account@my-project.iam.gserviceaccount.com', run:

    $ gcloud iam service-accounts add-iam-policy-binding \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --member='allAuthenticatedUsers' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/iam.serviceAccountAdmin' and the user
'test-user@gmail.com' on a service account with identifier
'my-iam-account@my-project.iam.gserviceaccount.com', run:

    $ gcloud iam service-accounts add-iam-policy-binding \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --member='user:test-user@gmail.com' \
        --role='roles/iam.serviceAccountAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/add-iam-policy-binding)

---
### `gcloud iam service-accounts create`

Create a service account for a project

This command creates a service account with the provided name. For
subsequent commands regarding service accounts, this service account should
be referred to by the email account in the response.

**Synopsis:**
```
gcloud iam service-accounts create NAME [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The internal name of the new service account. Used to generate an
   IAM_ACCOUNT (an IAM internal email address used as an identifier of
   service account), which must be passed to subsequent commands.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A textual description for the account. |
| `--display-name` | DISPLAY_NAME |  | A textual name to display for the account. |


**Examples:**
```bash
To create a service account for your project, run:

    $ gcloud iam service-accounts create some-account-name \
        --display-name="My Service Account"

To work with this service account in subsequent IAM commands, use the email
resulting from this call as the IAM_ACCOUNT argument.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/create)

---
### `gcloud iam service-accounts delete`

Delete a service account from a project

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts delete SERVICE_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_ACCOUNT
   The service account to delete. The account should be formatted either
   as a numeric service account ID or as an email, like this:
   123456789876543212345 or my-iam-account@somedomain.com.
```

**Examples:**
```bash
To delete an service account from your project, run:

    $ gcloud iam service-accounts delete \
        my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/delete)

---
### `gcloud iam service-accounts describe`

Show metadata for a service account from a project

This command shows metadata for a service account.

This call can fail for the following reasons:
  o The specified service account does not exist. In this case, you
    receive a PERMISSION_DENIED error.
  o The active user does not have permission to access the given service
    account.

**Synopsis:**
```
gcloud iam service-accounts describe SERVICE_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_ACCOUNT
   The service account to describe. The account should be formatted either
   as a numeric service account ID or as an email, like this:
   123456789876543212345 or my-iam-account@somedomain.com.
```

**Examples:**
```bash
To print metadata for a service account from your project, run:

    $ gcloud iam service-accounts describe \
        my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/describe)

---
### `gcloud iam service-accounts disable`

Disable an IAM service account

Disable an IAM service account. After the service account is disabled,
credential generation and API requests using this service account will
fail. Using gcloud iam service-accounts enable to re-enable it.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts disable SERVICE_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceAccount resource - The IAM service account to disable. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_account on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_ACCOUNT
     ID of the serviceAccount or fully qualified identifier for the
     serviceAccount.

     To set the service_account attribute:
     + provide the argument service_account on the command line.
```

**Examples:**
```bash
To disable a service account from your project, run:

    $ gcloud iam service-accounts disable \
        my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/disable)

---
### `gcloud iam service-accounts enable`

Enable an IAM service account

Enable an IAM service account.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts enable SERVICE_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceAccount resource - The IAM service account to enable. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_account on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_ACCOUNT
     ID of the serviceAccount or fully qualified identifier for the
     serviceAccount.

     To set the service_account attribute:
     + provide the argument service_account on the command line.
```

**Examples:**
```bash
To enable a service account from your project, run:

    $ gcloud iam service-accounts enable \
        my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/enable)

---
### `gcloud iam service-accounts get-iam-policy`

Get the IAM policy for a service account

This command gets the IAM policy for a service account. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ gcloud
iam service-accounts set-iam-policy for additional details.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

When managing IAM roles, you can treat a service account either as a
resource or as an identity. This command is to get the iam policy of a
service account resource. There are other gcloud commands to manage IAM
policies for other types of resources. For example, to manage IAM policies
on a project, use the $ gcloud projects commands.

**Synopsis:**
```
gcloud iam service-accounts get-iam-policy SERVICE_ACCOUNT
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_ACCOUNT
   The service account whose policy to get. The account should be
   formatted either as a numeric service account ID or as an email, like
   this: 123456789876543212345 or my-iam-account@somedomain.com.
```

**Examples:**
```bash
To print the IAM policy for a given service account, run:

    $ gcloud iam service-accounts get-iam-policy \
        my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/get-iam-policy)

---
### `gcloud iam service-accounts list`

List all of a project's service accounts

List all of a project's service accounts.

**Synopsis:**
```
gcloud iam service-accounts list [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all service accounts in the current project, run:

    $ gcloud iam service-accounts list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/list)

---
### `gcloud iam service-accounts remove-iam-policy-binding`

Remove IAM policy binding from a service account

Remove an IAM policy binding from the IAM policy of a service account. A
binding consists of at least one member, a role, and an optional condition.

When managing IAM roles, you can treat a service account either as a
resource or as an identity. This command is to remove a policy binding from
a service account resource. There are other gcloud commands to manage IAM
policies for other types of resources. For example, to manage IAM policies
on a project, use the $ gcloud projects commands.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts remove-iam-policy-binding SERVICE_ACCOUNT
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceAccount resource - The service account to remove the IAM policy
binding from. Note that the user, group or service account in the --member
flag is having its access revoked. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument service_account on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_ACCOUNT
     ID of the serviceAccount or fully qualified identifier for the
     serviceAccount.

     To set the service_account attribute:
     + provide the argument service_account on the command line.
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
'test-user@gmail.com' on a service account with identifier
'my-iam-account@my-project.iam.gserviceaccount.com', run:

    $ gcloud iam service-accounts remove-iam-policy-binding \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on service account
'my-iam-account@my-project.iam.gserviceaccount.com', run:

    $ gcloud iam service-accounts remove-iam-policy-binding \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --member='allAuthenticatedUsers' --role='roles/editor'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/iam.serviceAccountAdmin' and the user
'test-user@gmail.com' on a service account with identifier
'my-iam-account@my-project.iam.gserviceaccount.com', run:

    $ gcloud iam service-accounts remove-iam-policy-binding \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --member='user:test-user@gmail.com' \
        --role='roles/iam.serviceAccountAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/remove-iam-policy-binding)

---
### `gcloud iam service-accounts set-iam-policy`

Set IAM policy for a service account

This command replaces the existing IAM policy for a service account, given
an IAM_ACCOUNT and a file encoded in JSON or YAML that contains the IAM
policy. If the given policy file specifies an "etag" value, then the
replacement will succeed only if the policy already in place matches that
etag. (An etag obtained via $ gcloud iam service-accounts get-iam-policy
will prevent the replacement if the policy for the service account has been
subsequently updated.) A policy file that does not contain an etag value
will replace any existing policy for the service account.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

When managing IAM roles, you can treat a service account either as a
resource or as an identity. This command is to set the iam policy of a
service account resource. There are other gcloud commands to manage IAM
policies for other types of resources. For example, to manage IAM policies
on a project, use the $ gcloud projects commands.

**Synopsis:**
```
gcloud iam service-accounts set-iam-policy SERVICE_ACCOUNT POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE_ACCOUNT
   The service account whose policy to set. The account should be
   formatted either as a numeric service account ID or as an email, like
   this: 123456789876543212345 or my-iam-account@somedomain.com.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.
```

**Examples:**
```bash
The following command will read an IAM policy from 'policy.json' and set it
for a service account with
'my-iam-account@my-project.iam.gserviceaccount.com' as the identifier:

    $ gcloud iam service-accounts set-iam-policy \
        my-iam-account@my-project.iam.gserviceaccount.com policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/set-iam-policy)

---
### `gcloud iam service-accounts sign-blob`

Sign a blob with a managed service account key

This command signs a file containing arbitrary binary data (a blob) using a
system-managed service account key.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts sign-blob INPUT-FILE OUTPUT-FILE
    --iam-account=IAM_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT-FILE
   A path to the blob file to be signed.

OUTPUT-FILE
   A path the resulting signed blob will be written to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iam-account` | IAM_ACCOUNT |  | The service account to sign as. |


**Examples:**
```bash
To sign a blob file with a system-managed service account key, run:

    $ gcloud iam service-accounts sign-blob \
        --iam-account=my-iam-account@my-project.iam.gserviceaccount.com \
    input.bin output.bin
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/sign-blob)

---
### `gcloud iam service-accounts sign-jwt`

Sign a JWT with a managed service account key

This command signs a JWT using a system-managed service account key.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts sign-jwt INPUT-FILE OUTPUT-FILE
    --iam-account=IAM_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT-FILE
   A path to the file containing the JSON JWT Claim set to be signed.

OUTPUT-FILE
   A path the resulting signed JWT will be written to.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iam-account` | IAM_ACCOUNT |  | The service account to sign as. |


**Examples:**
```bash
To create a sign JWT with a system-managed service account key, run:

    $ gcloud iam service-accounts sign-jwt \
        --iam-account=my-iam-account@my-project.iam.gserviceaccount.com \
    input.json output.jwt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/sign-jwt)

---
### `gcloud iam service-accounts undelete`

Undelete a service account for a project

Undelete a service account for a project.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts undelete ACCOUNT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ACCOUNT_ID
   The deleted service account's unique ID must be provided when using the
   undelete command. Unique IDs are a 21 digit number, such as
   103271949540120710052.
```

**Examples:**
```bash
The following command undeletes a service account with unique id
103271949540120710052:

    $ gcloud iam service-accounts undelete 103271949540120710052
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/undelete)

---
### `gcloud iam service-accounts update`

Update an IAM service account

Update an IAM service account.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts update SERVICE_ACCOUNT
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ServiceAccount resource - The service account to update. The account
should be formatted either as a numeric service account ID or as an email,
like this: 123456789876543212345 or my-iam-account@somedomain.com. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_account on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_ACCOUNT
     ID of the serviceAccount or fully qualified identifier for the
     serviceAccount.

     To set the service_account attribute:
     + provide the argument service_account on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The new textual description for the account. |
| `--display-name` | DISPLAY_NAME |  | The new textual name to display for the account. |


**Examples:**
```bash
To update the description and display name for a service account, run:

    $ gcloud iam service-accounts update \
        my-iam-account@my-project.iam.gserviceaccount.com \
        --description="Updated description." \
        --display-name="Updated Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/update)

---

## `gcloud iam service-accounts keys` — manage service account keys
### `gcloud iam service-accounts keys create`

Create a service account key

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts keys create OUTPUT-FILE
    --iam-account=IAM_ACCOUNT
    [--key-file-type=KEY_FILE_TYPE; default="json"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OUTPUT-FILE
   The path where the resulting private key should be written. File system
   write permission will be checked on the specified path prior to the key
   creation.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iam-account` | IAM_ACCOUNT |  | The service account for which to create a key. To list all service accounts in the project, run: $ gcloud iam service-accounts list |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-file-type` | one of: json, p12 | json | The type of key to create. KEY_FILE_TYPE must be one of: json, p12. |


**Examples:**
```bash
To create a new service account key and save the private portion of the key
locally, run:

    $ gcloud iam service-accounts keys create key.json \
        --iam-account=my-iam-account@my-project.iam.gserviceaccount.com
```

**Notes:** The option --key-file-type=p12 is available here only for legacy reasons; all new use cases are encouraged to use the default 'json' format.

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys/create)

---
### `gcloud iam service-accounts keys delete`

Delete a service account key

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts keys delete KEY-ID --iam-account=IAM_ACCOUNT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
KEY-ID
   The key to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iam-account` | IAM_ACCOUNT |  | The service account from which to delete a key. To list all service accounts in the project, run: $ gcloud iam service-accounts list |


**Examples:**
```bash
To delete a key with ID b4f1037aeef9ab37deee9 for the service account
my-iam-account@my-project.iam.gserviceaccount.com, run:

    $ gcloud iam service-accounts keys delete b4f1037aeef9ab37deee9 \
        --iam-account=my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys/delete)

---
### `gcloud iam service-accounts keys disable`

Disable a service account key

Disable a service account key.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts keys disable
    (IAM_KEY : --iam-account=IAM_ACCOUNT) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IamKey resource - The id of the key to disable. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument iam_key on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IAM_KEY
     ID of the iamKey or fully qualified identifier for the iamKey.

     To set the iam_key attribute:
     + provide the argument iam_key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --iam-account=IAM_ACCOUNT
     The name of the IAM ServiceAccount.

     To set the iam-account attribute:
     + provide the argument iam_key on the command line with a fully
       specified name;
     + provide the argument --iam-account on the command line.
```

**Examples:**
```bash
To disable a key with ID b4f1037aeef9ab37deee9 for the service account
my-iam-account@my-project.iam.gserviceaccount.com, run:

    gcloud iam service-accounts keys disable b4f1037aeef9ab37deee9 --iam-account=my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys/disable)

---
### `gcloud iam service-accounts keys enable`

Enable a service account key

Enable a service account key.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts keys enable
    (IAM_KEY : --iam-account=IAM_ACCOUNT) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IamKey resource - The id of the key to disable. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument iam_key on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  IAM_KEY
     ID of the iamKey or fully qualified identifier for the iamKey.

     To set the iam_key attribute:
     + provide the argument iam_key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --iam-account=IAM_ACCOUNT
     The name of the IAM ServiceAccount.

     To set the iam-account attribute:
     + provide the argument iam_key on the command line with a fully
       specified name;
     + provide the argument --iam-account on the command line.
```

**Examples:**
```bash
To enable a key with ID b4f1037aeef9ab37deee9 for the service account
my-iam-account@my-project.iam.gserviceaccount.com, run:

    gcloud iam service-accounts keys enable b4f1037aeef9ab37deee9 --iam-account=my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys/enable)

---
### `gcloud iam service-accounts keys list`

List the keys for a service account

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts keys list --iam-account=IAM_ACCOUNT
    [--created-before=CREATED_BEFORE]
    [--managed-by=MANAGED_BY; default="any"] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iam-account` | IAM_ACCOUNT |  | A textual name to display for the account. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--created-before` | CREATED_BEFORE |  | Return only keys created before the specified time. Common time formats are accepted. This is equivalent to --filter="validAfterTime<DATE_TIME". See $ gcloud topic datetimes for information on time formats. |
| `--managed-by` | one of: user, system, any | any | The types of keys to list. MANAGED_BY must be one of: user, system, any. |


**Examples:**
```bash
To list all user-managed keys created before noon on July 19th, 2015 (to
perform key rotation, for example), run:

    $ gcloud iam service-accounts keys list \
        --iam-account=my-iam-account@my-project.iam.gserviceaccount.com \
    --managed-by=user --created-before=2015-07-19T12:00:00Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys/list)

---
### `gcloud iam service-accounts keys upload`

Upload a public key for an IAM service account

Upload a public key for an IAM service account.

If the service account does not exist, this command returns a
PERMISSION_DENIED error.

**Synopsis:**
```
gcloud iam service-accounts keys upload PUBLIC_KEY_FILE
    --iam-account=IAM_ACCOUNT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PUBLIC_KEY_FILE
   Path of the file containing the public key. Note that only public key
   data in the format of RSA_X509_PEM is supported. See
   https://cloud.google.com/iot/docs/concepts/device-security#public_key_format
   for more information.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--iam-account` | IAM_ACCOUNT |  | _[This must be specified.]_ ID of the iamAccount or fully qualified identifier for the iamAccount. To set the iam-account attribute: + provide the argument --iam-account on the command line. |


**Examples:**
```bash
The following command uploads a public key certificate to a service
account:        gcloud iam service-accounts keys upload test_data/public_key.cert --iam-account=my-iam-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/service-accounts/keys/upload)

---
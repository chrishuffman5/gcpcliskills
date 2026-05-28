# gcloud storage managed-folders

manage Cloud Storage managed folders

### `gcloud storage managed-folders add-iam-policy-binding`

Add an IAM policy binding to a managed folder

Add an IAM policy binding to a managed folder. For more information, see
Cloud Identity and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage managed-folders add-iam-policy-binding URL
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   URL of the managed folder to add IAM policy binding to.
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
To grant a single role to a single principal for a managed folder
managed-folder in a bucket bucket:

    $ gcloud storage managed-folders add-iam-policy-binding \
        gs://bucket/managed-folder --member=user:john.doe@example.com \
        --role=roles/storage.objectCreator

To make objects in gs://bucket/managed-folder publicly readable:

    $ gcloud storage managed-folders add-iam-policy-binding \
        gs://bucket/managed-folder --member=allUsers \
        --role=roles/storage.objectViewer

To specify a custom role for a principal on gs://bucket/managed-folder:

    $ gcloud storage managed-folders add-iam-policy-binding \
        gs://bucket/managed-folder --member=user:john.doe@example.com \
        --role=roles/customRoleName
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/add-iam-policy-binding)

---
### `gcloud storage managed-folders create`

Create managed folders

Create managed folders.

**Synopsis:**
```
gcloud storage managed-folders create URL [URL ...]
    [--additional-headers=HEADER=VALUE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs of the folders to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |


**Examples:**
```bash
The following command creates a managed folder called folder/ in a bucket
named my-bucket:

    $ gcloud storage managed-folders create gs://my-bucket/folder/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/create)

---
### `gcloud storage managed-folders delete`

Delete managed folders

Delete managed folders.

**Synopsis:**
```
gcloud storage managed-folders delete URL [URL ...]
    [--additional-headers=HEADER=VALUE] [--continue-on-error, -c]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs of the managed folders to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |


**Examples:**
```bash
The following command deletes a managed folder named folder in a bucket
called my-bucket:

    $ gcloud storage managed-folders delete gs://my-bucket/folder/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/delete)

---
### `gcloud storage managed-folders describe`

Describe managed folders

Describe managed folders.

**Synopsis:**
```
gcloud storage managed-folders describe URL
    [--additional-headers=HEADER=VALUE] [--raw] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   The URL of the managed folder to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
The following command shows information about a managed folder named folder
in a bucket called my-bucket:

    $ gcloud storage managed-folders describe gs://my-bucket/folder/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/describe)

---
### `gcloud storage managed-folders get-iam-policy`

Get the IAM policy for a managed folder

Get the IAM policy for a managed folder. For more information, see Cloud
Identity and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage managed-folders get-iam-policy URL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   URL of the managed folder to get the IAM policy of.
```

**Examples:**
```bash
To get the IAM policy for a managed folder managed-folder in a bucket
bucket:

    $ gcloud storage managed-folders get-iam-policy \
        gs://bucket/managed-folder/

To output the IAM policy for gs://bucket/managed-folder to a file:

    $ gcloud storage managed-folders get-iam-policy \
        gs://bucket/managed-folder/ > policy.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/get-iam-policy)

---
### `gcloud storage managed-folders list`

List managed folders

List managed folders.

**Synopsis:**
```
gcloud storage managed-folders list URL [URL ...]
    [--additional-headers=HEADER=VALUE] [--raw] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs of the resources to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
The following command lists all managed folders in a bucket:

    $ gcloud storage managed-folders list gs://my-bucket/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/list)

---
### `gcloud storage managed-folders remove-iam-policy-binding`

Remove an IAM policy binding from a managed folder

Remove a policy binding from the IAM policy of a managed folder, given a
managed folder URL and the binding. For more information, see Cloud
Identity and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage managed-folders remove-iam-policy-binding URL
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   URL of managed folder to remove IAM policy binding from.
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
To remove an IAM policy binding from the role of
roles/storage.objectCreator for the user john.doe@example.com on a managed
folder managed-folder in a bucket bucket:

    $ gcloud storage managed-folders remove-iam-policy-binding \
        gs://bucket/managed-folder --member=user:john.doe@example.com \
        --role=roles/storage.objectCreator
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/remove-iam-policy-binding)

---
### `gcloud storage managed-folders set-iam-policy`

Set the IAM policy for a managed folder

Set the IAM policy for a managed folder. For more information, see Cloud
Identity and Access Management
(https://cloud.google.com/storage/docs/access-control/iam).

**Synopsis:**
```
gcloud storage managed-folders set-iam-policy URLS [URLS ...] POLICY_FILE
    [--continue-on-error, -c] [--etag=ETAG, -e ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   URLs for managed folders to apply the IAM policy to.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--etag` | ETAG, -e ETAG |  | Custom etag to set on IAM policy. API will reject etags that do not match this value, making it useful as a precondition during concurrent operations. |


**Examples:**
```bash
To set the IAM policy in POLICY-FILE on a managed folder managed-folder in
a bucket bucket:

    $ gcloud storage managed-folders set-iam-policy \
        gs://bucket/managed-folder POLICY-FILE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/managed-folders/set-iam-policy)

---
# gcloud bigtable authorized-views

manage Cloud Bigtable Authorized Views

### `gcloud bigtable authorized-views add-iam-policy-binding`

Add an IAM policy binding to a Cloud Bigtable authorized view

Add an IAM policy binding to a Cloud Bigtable authorized view. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable authorized-views add-iam-policy-binding
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to add the IAM
policy binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
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
test-user@gmail.com with authorized view my-authorized-view in instance
my-instance and table my-table, run:

    $ gcloud bigtable authorized-views add-iam-policy-binding \
        my-authorized-view --instance=`my-instance` --table=`my-table` \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To add an IAM policy binding which expires at the end of the year 2020 for
the role of roles/bigtable.admin and the user test-user@gmail.com with
authorized view my-authorized-view in instance my-instance and table
my-table, run:

    $ gcloud bigtable authorized-views add-iam-policy-binding \
        my-authorized-view --instance=`my-instance` --table=`my-table` \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,\
    description=Expires at midnight on 2020-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/add-iam-policy-binding)

---
### `gcloud bigtable authorized-views create`

Create a new Cloud Bigtable authorized view

Create a new Cloud Bigtable authorized view.

**Synopsis:**
```
gcloud bigtable authorized-views create
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE) [--async]
    [--definition-file=DEFINITION_FILE] [--pre-encoded]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--definition-file` | DEFINITION_FILE |  | Path to a JSON or YAML file containing a valid authorized view protobuf. The name field is ignored. The name is deduced from the other command line arguments. Example: { "subsetView": { "rowPrefixes": ["store1#"], "familySubsets": { "column_family_name": { "qualifiers":["address"], "qualifierPrefixes":["tel"] } } }, "deletionProtection": true } |
| `--pre-encoded` |  |  | By default, Base64 encoding is applied to all binary fields ("rowPrefixes", "qualifiers" and "qualifierPrefixes") in the JSON or YAML definition file. Use this to indicate that all binary fields are already Base64-encoded and should be used directly. |


**Examples:**
```bash
To create an authorized view my-authorized-view in instance my-instance and
table my-table, using the definition file authorized_view.json:

    $ gcloud bigtable authorized-views create my-authorized-view \
        --instance=test-instance --table=test-table \
        --definition-file=authorized_view.json

To create an authorized view my-authorized-view in instance my-instance and
table my-table, using the pre-encoded definition file
authorized_view_pre_encoded.json:

    $ gcloud bigtable authorized-views create my-authorized-view \
        --instance=test-instance --table=test-table \
        --definition-file=authorized_view_pre_encoded.json --pre-encoded
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/create)

---
### `gcloud bigtable authorized-views delete`

Delete a Cloud Bigtable authorized view

Delete new Cloud Bigtable authorized view.

**Synopsis:**
```
gcloud bigtable authorized-views delete
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Examples:**
```bash
To delete the authorized view my-authorized-view in instance my-instance
and table my-table:

    $ gcloud bigtable authorized-views delete my-authorized-view \
        --instance=test-instance --table=test-table
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/delete)

---
### `gcloud bigtable authorized-views describe`

Describe a Cloud Bigtable authorized view

Describe a Cloud Bigtable authorized view.

**Synopsis:**
```
gcloud bigtable authorized-views describe
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Examples:**
```bash
To describe the authorized view my-authorized-view in instance my-instance
and table my-table:

    $ gcloud bigtable authorized-views describe my-authorized-view \
        --instance=test-instance --table=test-table
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/describe)

---
### `gcloud bigtable authorized-views get-iam-policy`

Get an IAM policy on a Cloud Bigtable authorized view

Get an IAM policy on a Cloud Bigtable authorized view.

**Synopsis:**
```
gcloud bigtable authorized-views get-iam-policy
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to get the IAM
policy for. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Examples:**
```bash
To get the IAM policy on the authorized view my-authorized-view in instance
my-instance and table my-table, run:

    $ gcloud bigtable authorized-views get-iam-policy \
        my-authorized-view --instance=`my-instance` --table=`my-table`

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/get-iam-policy)

---
### `gcloud bigtable authorized-views list`

List all authorized views of a Cloud Bigtable table

List all authorized views of a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable authorized-views list (--table=TABLE : --instance=INSTANCE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--table` | TABLE |  | _[This must be specified.]_ ID of the table or fully qualified identifier for the table. To set the table attribute: + provide the argument --table on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--instance` | INSTANCE |  | _[This must be specified.]_ Name of the Bigtable instance. To set the instance attribute: + provide the argument --table on the command line with a fully specified name; + provide the argument --instance on the command line. |


**Examples:**
```bash
To list the authorized views in instance my-instance and table my-table:

    $ gcloud bigtable authorized-views list --instance=test-instance \
        --table=test-table
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/list)

---
### `gcloud bigtable authorized-views remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Bigtable authorized view

Remove an IAM policy binding from a Cloud Bigtable authorized view. One
binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable authorized-views remove-iam-policy-binding
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to remove the
IAM policy binding from. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
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
test-user@gmail.com with authorized view my-authorized-view in instance
my-instance and table my-table, run:

    $ gcloud bigtable authorized-views remove-iam-policy-binding \
        my-authorized-view --instance=`my-instance` --table=`my-table` \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To remove an IAM policy binding which expires at the end of the year 2020
for the role of roles/bigtable.admin and the user test-user@gmail.com with
authorized view my-authorized-view in instance my-instance and cluster
my-cluster, run:

    $ gcloud bigtable authorized-views remove-iam-policy-binding \
        my-authorized-view --instance=`my-instance` --table=`my-table` \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,\
    description=Expires at midnight on 2020-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/remove-iam-policy-binding)

---
### `gcloud bigtable authorized-views set-iam-policy`

Set an IAM policy on a Cloud Bigtable authorized view

Set an IAM policy on a Cloud Bigtable authorized view.

**Synopsis:**
```
gcloud bigtable authorized-views set-iam-policy
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to set the IAM
policy on. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy from file my-policy on the authorized view
my-authorized-view in instance my-instance and table my-table, run:

    $ gcloud bigtable authorized-views set-iam-policy \
        my-authorized-view --instance=`my-instance` --table=`my-table` \
        my-policy

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/set-iam-policy)

---
### `gcloud bigtable authorized-views update`

Update an existing Cloud Bigtable authorized view

Update an existing Cloud Bigtable authorized view.

**Synopsis:**
```
gcloud bigtable authorized-views update
    (AUTHORIZED_VIEW : --instance=INSTANCE --table=TABLE) [--async]
    [--definition-file=DEFINITION_FILE] [--ignore-warnings]
    [--no-interactive] [--pre-encoded] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized view resource - Cloud Bigtable authorized view to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authorized_view on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZED_VIEW
     ID of the authorized-view or fully qualified identifier for the
     authorized-view.

     To set the authorized_view attribute:
     + provide the argument authorized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument authorized_view on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--definition-file` | DEFINITION_FILE |  | Path to a JSON or YAML file containing a valid authorized view protobuf. The name field is ignored. The name is deduced from the other command line arguments. Example: { "subsetView": { "rowPrefixes": ["store1"], "familySubsets": { "column_family_name": { "qualifiers":["address"], "qualifierPrefixes":["tel"] } } }, "deletionProtection": true } |
| `--ignore-warnings` |  |  | If true, changes that make the authorized view more restrictive are allowed. |
| `--interactive` |  |  | If provided, a diff is displayed with a prompt to proceed or cancel the update. Enabled by default, use --no-interactive to disable. |
| `--pre-encoded` |  |  | By default, Base64 encoding is applied to all binary fields ("rowPrefixes", "qualifiers" and "qualifierPrefixes") in the JSON or YAML definition file. Use this to indicate that all binary fields are already Base64-encoded and should be used directly. |


**Examples:**
```bash
To update the authorized view my-authorized-view in instance my-instance
and table my-table, using the definition file authorized_view.json:

    $ gcloud bigtable authorized-views update my-authorized-view \
        --instance=test-instance --table=test-table \
        --definition-file=authorized_view.json

To update the authorized view my-authorized-view in instance my-instance
and table my-table, using the pre-encoded definition file
authorized_view_pre_encoded.json:

    $ gcloud bigtable authorized-views update my-authorized-view \
        --instance=test-instance --table=test-table \
        --definition-file=authorized_view_pre_encoded.json --pre-encoded

To update the authorized view my-authorized-view in instance my-instance
and table my-table, using the definition file authorized_view.json and skip
the prompt to proceed or cancel the update:

    $ gcloud bigtable authorized-views update my-authorized-view \
        --instance=test-instance --table=test-table \
        --definition-file=authorized_view.json --no-interactive
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/authorized-views/update)

---
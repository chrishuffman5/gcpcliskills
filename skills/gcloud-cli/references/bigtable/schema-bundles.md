# gcloud bigtable schema-bundles

manage Bigtable schema bundles

### `gcloud bigtable schema-bundles add-iam-policy-binding`

Add an IAM policy binding to a Bigtable schema bundle

Add an IAM policy binding to a Bigtable schema bundle. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable schema-bundles add-iam-policy-binding
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE) --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to add the IAM policy
binding to. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
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
222larabrown@gmail.com with schema bundle my-schema-bundle in instance
my-instance and table my-table, run:

    $ gcloud bigtable schema-bundles add-iam-policy-binding \
        my-schema-bundle --instance=`my-instance` --table=`my-table` \
        --member=`user:222larabrown@gmail.com` --role=`roles/editor`

To add an IAM policy binding which expires at the end of the year 2025 for
the role of roles/bigtable.admin and the user 222larabrown@gmail.com with
schema bundle my-schema-bundle in instance my-instance and table my-table,
run:

    $ gcloud bigtable schema-bundles add-iam-policy-binding \
        my-schema-bundle --instance=`my-instance` --table=`my-table` \
        --member=`user:222larabrown@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,\
    description=Expires at midnight on 2020-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/add-iam-policy-binding)

---
### `gcloud bigtable schema-bundles create`

Create a new Bigtable schema bundle

Create a new Bigtable schema bundle.

**Synopsis:**
```
gcloud bigtable schema-bundles create
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE)
    --proto-descriptors-file=PROTO_DESCRIPTORS_FILE [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to create. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--proto-descriptors-file` | PROTO_DESCRIPTORS_FILE |  | Path of a file that contains a protobuf-serialized google.protobuf.FileDescriptorSet message. If specified, the schema bundle contains the protobuf schema. To generate the file, install and run protoc with the following command: protoc --proto_path=IMPORT_PATH --include_imports --descriptor_set_out=DESCRIPTOR_OUTPUT_LOCATION path/to/file.proto where the --proto_path option specificies where to look for .proto files when resolving import directives (the current directory is used if you do not provide a value), and the --descriptor_set_out option specifies where you want the generated FileDescriptorSet to be written. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a schema bundle my-schema-bundle in instance my-instance and
table my-table, using the descriptor file my-descriptor-file.pb:

    $ gcloud bigtable schema-bundles create my-schema-bundle \
        --instance=test-instance --table=test-table \
        --proto-descriptors-file=my-descriptor-file.pb
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/create)

---
### `gcloud bigtable schema-bundles delete`

Delete a Bigtable schema bundle

Delete a Bigtable schema bundle.

**Synopsis:**
```
gcloud bigtable schema-bundles delete
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Examples:**
```bash
To delete the schema bundle my-schema-bundle in instance my-instance and
table my-table:

    $ gcloud bigtable schema-bundles delete my-schema-bundle \
        --instance=test-instance --table=test-table
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/delete)

---
### `gcloud bigtable schema-bundles describe`

Describe a Bigtable schema bundle

Describe a Bigtable schema bundle.

**Synopsis:**
```
gcloud bigtable schema-bundles describe
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Examples:**
```bash
To describe the schema bundle my-schema-bundle in instance my-instance and
table my-table:

    $ gcloud bigtable schema-bundles describe my-schema-bundle \
        --instance=test-instance --table=test-table
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/describe)

---
### `gcloud bigtable schema-bundles get-iam-policy`

Get an IAM policy on a Bigtable schema bundle

Get an IAM policy on a Bigtable schema bundle.

**Synopsis:**
```
gcloud bigtable schema-bundles get-iam-policy
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to get the IAM policy for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Examples:**
```bash
To get the IAM policy on the schema bundle my-schema-bundle in instance
my-instance and table my-table, run:

    $ gcloud bigtable schema-bundles get-iam-policy my-schema-bundle \
        --instance=`my-instance` --table=`my-table`

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/get-iam-policy)

---
### `gcloud bigtable schema-bundles list`

List all schema bundles of a Bigtable table

List all schema bundles of a Bigtable table.

**Synopsis:**
```
gcloud bigtable schema-bundles list (--table=TABLE : --instance=INSTANCE)
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
To list the schema bundles in instance my-instance and table my-table:

    $ gcloud bigtable schema-bundles list --instance=my-instance \
        --table=my-table

To list all schema bundles that match the given filter:

    $ gcloud bigtable schema-bundles list --instance=my-instance \
        --table=my-table --filter="name=( `NAME` ... )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/list)

---
### `gcloud bigtable schema-bundles remove-iam-policy-binding`

Remove an IAM policy binding from a Bigtable schema bundle

Remove an IAM policy binding from a Bigtable schema bundle. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable schema-bundles remove-iam-policy-binding
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE) --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to remove the IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
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
222larabrown@gmail.com with schema bundle my-schema-bundle in instance
my-instance and table my-table, run:

    $ gcloud bigtable schema-bundles remove-iam-policy-binding \
        my-schema-bundle --instance=`my-instance` --table=`my-table` \
        --member=`user:222larabrown@gmail.com` --role=`roles/editor`

To remove an IAM policy binding which expires at the end of the year 2025
for the role of roles/bigtable.admin and the user 222larabrown@gmail.com
with schema bundle my-schema-bundle in instance my-instance and table
my-table, run:

    $ gcloud bigtable schema-bundles remove-iam-policy-binding \
        my-schema-bundle --instance=`my-instance` --table=`my-table` \
        --member=`user:222larabrown@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,\
    description=Expires at midnight on 2020-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/remove-iam-policy-binding)

---
### `gcloud bigtable schema-bundles set-iam-policy`

Set an IAM policy on a Bigtable schema bundle

Set an IAM policy on a Bigtable schema bundle.

**Synopsis:**
```
gcloud bigtable schema-bundles set-iam-policy
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to set the IAM policy on.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
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
To set the IAM policy from file my-policy on the schema bundle
my-schema-bundle in instance my-instance and table my-table, run:

    $ gcloud bigtable schema-bundles set-iam-policy my-schema-bundle \
        --instance=`my-instance` --table=`my-table` my-policy

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/set-iam-policy)

---
### `gcloud bigtable schema-bundles update`

Update an existing Bigtable schema bundle

Update an existing Bigtable schema bundle.

**Synopsis:**
```
gcloud bigtable schema-bundles update
    (SCHEMA_BUNDLE : --instance=INSTANCE --table=TABLE)
    --proto-descriptors-file=PROTO_DESCRIPTORS_FILE [--async]
    [--ignore-warnings] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Schema bundle resource - Bigtable schema bundle to update. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument schema_bundle on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCHEMA_BUNDLE
     ID of the schema-bundle or fully qualified identifier for the
     schema-bundle.

     To set the schema_bundle attribute:
     + provide the argument schema_bundle on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.

  --table=TABLE
     Name of the Bigtable table.

     To set the table attribute:
     + provide the argument schema_bundle on the command line with a
       fully specified name;
     + provide the argument --table on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--proto-descriptors-file` | PROTO_DESCRIPTORS_FILE |  | Path of a file that contains a protobuf-serialized google.protobuf.FileDescriptorSet message. If specified, the schema bundle contains the protobuf schema. To generate the file, install and run protoc with the following command: protoc --proto_path=IMPORT_PATH --include_imports --descriptor_set_out=DESCRIPTOR_OUTPUT_LOCATION path/to/file.proto where the --proto_path option specificies where to look for .proto files when resolving import directives (the current directory is used if you do not provide a value), and the --descriptor_set_out option specifies where you want the generated FileDescriptorSet to be written. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ignore-warnings` |  |  | If true, backwards incompatible changes will be allowed. |


**Examples:**
```bash
To update a schema bundle my-schema-bundle in instance my-instance and
table my-table, using the descriptor file my-descriptor-file.pb:

    $ gcloud bigtable schema-bundles update my-schema-bundle \
        --instance=my-instance --table=my-table \
        --proto-descriptors-file=my-descriptor-file.pb
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/schema-bundles/update)

---
# gcloud bigtable tables

query Cloud Bigtable tables

### `gcloud bigtable tables add-iam-policy-binding`

Add an IAM policy binding to a Cloud Bigtable table

Add an IAM policy binding to a Cloud Bigtable table. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable tables add-iam-policy-binding (TABLE : --instance=INSTANCE)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to add the IAM policy binding to.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
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
test-user@gmail.com with table my-table in instance my-instance, run:

    $ gcloud bigtable tables add-iam-policy-binding my-table \
        --instance=`my-instance` --member=`user:test-user@gmail.com` \
        --role=`roles/editor`

To add an IAM policy binding which expires at the end of the year 2019 for
the role of roles/bigtable.admin and the user test-user@gmail.com with
table my-table in instance my-instance, run:

    $ gcloud bigtable tables add-iam-policy-binding my-table \
        --instance=`my-instance` --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2020-01-01T00:00:00Z"),title=expires_end_of_2019,\
    description=Expires at midnight on 2019-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/add-iam-policy-binding)

---
### `gcloud bigtable tables create`

Create a new Cloud Bigtable table

Create a new Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable tables create (TABLE : --instance=INSTANCE)
    --column-families=[COLUMN_FAMILIES,...]
    [--change-stream-retention-period=CHANGE_STREAM_RETENTION_PERIOD]
    [--deletion-protection]
    [--row-key-schema-definition-file=ROW_KEY_SCHEMA_DEFINITION_FILE]
    [--row-key-schema-pre-encoded-bytes] [--splits=[SPLITS,...]]
    [--automated-backup-retention-period=AUTOMATED_BACKUP_RETENTION_PERIOD
      | --enable-automated-backup] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--column-families` | [COLUMN_FAMILIES,...] |  | A double-quote (") wrapped list of family name and corresponding garbage collection rules concatenated by :, where the rules are optional. For example: "family_1,family_2:maxage=5d&&maxversions=2,family_3:maxage=10d\|\|maxversions=5" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--change-stream-retention-period` | CHANGE_STREAM_RETENTION_PERIOD |  | The length of time to retain change stream data for the table, in the range of [1 day, 7 days]. Acceptable units are days (d), hours (h), minutes (m), and seconds (s). Passing in a value for this option enables a change stream for the table. Examples: 5d or 48h. |
| `--deletion-protection` |  |  | Once specified, the table is deletion protected. |
| `--row-key-schema-definition-file` | ROW_KEY_SCHEMA_DEFINITION_FILE |  | The row key schema for the table. The schema is defined in a YAML or JSON file, equivalent to the StructType protobuf message. Example YAML: encoding: delimitedBytes: delimiter: '#' fields: - fieldName: field1 type: bytesType: encoding: raw: {} - fieldName: field2 type: bytesType: encoding: raw: {} |
| `--row-key-schema-pre-encoded-bytes` |  |  | By default, Base64 encoding is applied to all binary fields in the YAML/JSON file (for example, encoding.delimitedBytes.delimiter). Use this to indicate that all binary fields are already encoded in the YAML/JSON file and should not be encoded again. |
| `--splits` | [SPLITS,...] |  | Row keys where the table should initially be split. For example: car,key |


**Examples:**
```bash
To create a table my-table in instance my-instance with a column family
my-family, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family"

To create a table that has a column family named my-instance, a garbage
collection policy that lets data expire after 864,000 seconds, and initial
table splits on row keys car and key, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family:maxage=864000s" --splits=car,key

To create a table my-table in instance my-instance that lets data in column
family my-family1 expire after 10 days and keeps a maximum of 5 cells per
column in column family my-family-2 if the data is less than 5 days old,
run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family-1:maxage=10d,my-family-2:maxversion\
    s=5||maxage=5d"

To create a table my-table that has one column family my-family that lets
data expire after 10 days, and to enable a change stream for the table to
be kept for 7 days, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family:maxage=10d" \
        --change-stream-retention-period=7d

To create a deletion-protected table my-table in instance my-instance with
a column family my-family, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family" --deletion-protection

To create a table my-table without deletion protection in instance
my-instance with a column family my-family, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family" --no-deletion-protection

To create a table my-table with the default automated backup policy
(retention_period=7d, frequency=1d) enabled in instance my-instance with a
column family my-family, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family" --enable-automated-backup

To create a table my-table with a custom automated backup policy configured
to retain backups for 30 days in instance my-instance with a column family
my-family, run:

    $ gcloud bigtable tables create my-table --instance=my-instance \
        --column-families="my-family" \
        --automated-backup-retention_period=30d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/create)

---
### `gcloud bigtable tables delete`

Delete a Cloud Bigtable table

Delete a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable tables delete (TABLE : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To delete the table my-table in instance my-instance, run:

    $ gcloud bigtable tables delete my-table --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/delete)

---
### `gcloud bigtable tables describe`

Retrieve information about a table

Retrieve information about a table.

**Synopsis:**
```
gcloud bigtable tables describe (TABLE : --instance=INSTANCE)
    [--view=VIEW; default="schema"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: encryption Only populates name and fields related to the table's encryption status | schema | The view to be applied to the returned table's fields. VIEW must be one of: encryption Only populates name and fields related to the table's encryption status. full Populates all fields. name Only populates name. replication Only populates name and fields related to the table's replication. schema Only populates name and fields related to the table's schema. stats Only populates name and fields related to the table's statistics (e.g. TableStats and ColumnFamilyStats). |


**Examples:**
```bash
To describe a table, run:

    $ gcloud bigtable tables describe TABLE_NAME --instance=INSTANCE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/describe)

---
### `gcloud bigtable tables get-iam-policy`

Get an IAM policy on a Cloud Bigtable table

Get an IAM policy on a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable tables get-iam-policy (TABLE : --instance=INSTANCE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to get the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To get the IAM policy on the table my-table in instance my-instance, run:

    $ gcloud bigtable tables get-iam-policy my-table \
        --instance=`my-instance`

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/get-iam-policy)

---
### `gcloud bigtable tables list`

List existing Bigtable instance tables

**Synopsis:**
```
gcloud bigtable tables list --instances=[INSTANCE,...]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instances` | [INSTANCE,...] |  | ID of the instances. |


**Examples:**
```bash
To list all tables in an instance, run:

    $ gcloud bigtable tables list --instances=INSTANCE_NAME

To list all tables in several instances, run:        $ gcloud bigtable tables list \
        --instances=INSTANCE_NAME1,INSTANCE_NAME2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/list)

---
### `gcloud bigtable tables remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Bigtable table

Remove an IAM policy binding from a Cloud Bigtable table. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable tables remove-iam-policy-binding
    (TABLE : --instance=INSTANCE) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to remove the IAM policy binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
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
test-user@gmail.com with table my-table in instance my-instance, run:

    $ gcloud bigtable tables remove-iam-policy-binding my-table \
        --instance=`my-instance` --member=`user:test-user@gmail.com` \
        --role=`roles/editor`

To remove an IAM policy binding which expires at the end of the year 2019
for the role of roles/bigtable.admin and the user test-user@gmail.com with
table my-table in instance my-instance, run:

    $ gcloud bigtable tables remove-iam-policy-binding my-table \
        --instance=`my-instance` --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2020-01-01T00:00:00Z"),title=expires_end_of_2019,\
    description=Expires at midnight on 2019-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/remove-iam-policy-binding)

---
### `gcloud bigtable tables restore`

Restore a Cloud Bigtable backup to a new table

This command restores a Cloud Bigtable backup to a new table.

**Synopsis:**
```
gcloud bigtable tables restore
    (--destination=DESTINATION
      : --destination-instance=DESTINATION_INSTANCE)
    (--source=SOURCE
      : --source-cluster=SOURCE_CLUSTER --source-instance=SOURCE_INSTANCE)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | _[This must be specified.]_ ID of the table or fully qualified identifier for the table. To set the destination attribute: + provide the argument --destination on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--destination-instance` | DESTINATION_INSTANCE |  | _[This must be specified.]_ Name of the Bigtable instance. To set the instance attribute: + provide the argument --destination on the command line with a fully specified name; + provide the argument --destination-instance on the command line; + provide the argument --source-instance on the command line. |
| `--source` | SOURCE |  | _[This must be specified.]_ ID of the backup or fully qualified identifier for the backup. To set the source attribute: + provide the argument --source on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--source-cluster` | SOURCE_CLUSTER |  | _[This must be specified.]_ Name of the Bigtable cluster. To set the cluster attribute: + provide the argument --source on the command line with a fully specified name; + provide the argument --source-cluster on the command line. |
| `--source-instance` | SOURCE_INSTANCE |  | _[This must be specified.]_ Name of the Bigtable instance. To set the instance attribute: + provide the argument --source on the command line with a fully specified name; + provide the argument --source-instance on the command line; + provide the argument --destination-instance on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restore table 'table2' from backup 'backup1', run:

    $ gcloud bigtable tables restore --source-instance=instance1 \
        --source-cluster=cluster1 --source=backup1 \
        --destination-instance=instance1 --destination=table2

To restore table 'table2' from backup 'backup1' in a different project,
run:

    $ gcloud bigtable tables restore \
        --source=projects/project1/instances/instance1/clusters/\
    cluster1/backups/backup1 \
        --destination=projects/project2/instances/instance2/tables/\
    table2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/restore)

---
### `gcloud bigtable tables set-iam-policy`

Set an IAM policy on a Cloud Bigtable table

Set an IAM policy on a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable tables set-iam-policy (TABLE : --instance=INSTANCE)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to set the IAM policy on. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy from file my-policy on the table my-table in instance
my-instance, run:

    $ gcloud bigtable tables set-iam-policy my-table \
        --instance=`my-instance` my-policy

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/set-iam-policy)

---
### `gcloud bigtable tables undelete`

Undelete a previously deleted Cloud Bigtable table

Undelete a previously deleted Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable tables undelete (TABLE : --instance=INSTANCE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to undelete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To undelete the table my-table in instance my-instance, run:

    $ gcloud bigtable tables undelete my-table --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/undelete)

---
### `gcloud bigtable tables update`

Update an existing Cloud Bigtable table

Update an existing new Cloud Bigtable table with the specified
configuration.

**Synopsis:**
```
gcloud bigtable tables update (TABLE : --instance=INSTANCE) [--async]
    [--deletion-protection] [--row-key-schema-pre-encoded-bytes]
    [--automated-backup-retention-period=AUTOMATED_BACKUP_RETENTION_PERIOD
      | --disable-automated-backup | --enable-automated-backup]
    [--change-stream-retention-period=CHANGE_STREAM_RETENTION_PERIOD
      | --clear-change-stream-retention-period]
    [--clear-row-key-schema
      | --row-key-schema-definition-file=ROW_KEY_SCHEMA_DEFINITION_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Table resource - Cloud Bigtable table to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument table on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TABLE
     ID of the table or fully qualified identifier for the table.

     To set the table attribute:
     + provide the argument table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument table on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--deletion-protection` |  |  | Once specified, the table is deletion protected. |
| `--row-key-schema-pre-encoded-bytes` |  |  | By default, Base64 encoding is applied to all binary fields in the YAML/JSON file (for example, encoding.delimitedBytes.delimiter). Use this to indicate that all binary fields are already encoded in the YAML/JSON file and should not be encoded again. This field is only used when row-key-schema-definition-file is set. It is ignored if clear-row-key-schema is set. |


**Examples:**
```bash
To enable deletion protection, run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --deletion-protection

To disable deletion protection, run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --no-deletion-protection

To enable a change stream with a retention period of 1 day, or to update
your table's change stream retention period to 1 day, run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --change-stream-retention-period=1d

To disable a change stream, run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --clear-change-stream-retention-period

To enable the default automated backup policy on a table, or update a table
to use the default policy (retention_period=7d, frequency=1d), run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --enable-automated-backup

To disable automated backup: run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --disable-automated-backup

To enable or update a custom automated backup policy and configure it to
retain backups for 30 days, run:

    $ gcloud bigtable tables update my-table --instance=my-instance \
        --automated-backup-retention_period=30d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/tables/update)

---
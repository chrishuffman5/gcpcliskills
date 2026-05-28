# gcloud spanner databases

manage Cloud Spanner databases

### `gcloud spanner databases add-iam-policy-binding`

Add IAM policy binding to a Cloud Spanner database

Add an IAM policy binding to a Cloud Spanner database. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud spanner databases add-iam-policy-binding
    (DATABASE : --instance=INSTANCE) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to which to add the IAM
policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
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
'test-user@gmail.com' with database 'my-database' and instance
'my-instance', run:

    $ gcloud spanner databases add-iam-policy-binding my-database \
        --instance='my-instance' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/spanner.databaseAdmin' and the user
'test-user@gmail.com' with database 'my-database' and instance
'my-instance', run:

    $ gcloud spanner databases add-iam-policy-binding my-database \
        --instance='my-instance' --member='user:test-user@gmail.com' \
        --role='roles/spanner.databaseAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/add-iam-policy-binding)

---
### `gcloud spanner databases change-quorum`

Change quorum of a Cloud Spanner database

Change quorum of a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases change-quorum (DATABASE : --instance=INSTANCE)
    (--dual-region | --serving-location=SERVING_LOCATION --single-region)
    [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to change quorum. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dual-region` |  |  | _[Command-line flag for dual-region quorum change:]_ Switch to dual-region quorum type. |
| `--serving-location` | SERVING_LOCATION |  | _[Command-line flags for single-region quorum change:]_ The cloud Spanner location. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--single-region` |  |  | _[Command-line flags for single-region quorum change:]_ Switch to single-region quorum type. This flag argument must be specified if any of the other arguments in this group are specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Used for optimistic concurrency control. |


**Examples:**
```bash
To trigger change quorum from single-region mode to dual-region mode, run:

    $ gcloud spanner databases change-quorum my-database-id \
        --instance=my-instance-id --dual-region

To trigger change quorum from dual-region mode to single-region mode with
serving location as asia-south1, run:

    $ gcloud spanner databases change-quorum my-database-id \
        --instance=my-instance-id --single-region \
        --serving-location=asia-south1

To trigger change quorum using etag specified, run:

    $ gcloud spanner databases change-quorum my-database-id \
        --instance=my-instance-id --dual-region --etag=ETAG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/change-quorum)

---
### `gcloud spanner databases create`

Create a Cloud Spanner database

Create a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases create (DATABASE : --instance=INSTANCE) [--async]
    [--database-dialect=DATABASE_DIALECT] [--ddl=DDL] [--ddl-file=DDL_FILE]
    [--proto-descriptors-file=PROTO_DESCRIPTORS_FILE]
    [--kms-keys=[KMS_KEYS,...] | [--kms-key=KMS_KEY
      : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--database-dialect` | one of: POSTGRESQL, GOOGLE_STANDARD_SQL |  | The SQL dialect of the Cloud Spanner Database. GOOGLE_STANDARD_SQL is the default. DATABASE_DIALECT must be one of: POSTGRESQL, GOOGLE_STANDARD_SQL. |
| `--ddl` | DDL |  | Semi-colon separated DDL (data definition language) statements to run inside the newly created database. If there is an error in any statement, the database is not created. This option is not supported for the PostgreSQL dialect. Full DDL specification is at https://cloud.google.com/spanner/docs/data-definition-language |
| `--ddl-file` | DDL_FILE |  | Path of a file that contains semi-colon separated DDL (data definition language) statements to run inside the newly created database. If there is an error in any statement, the database is not created. This option is not supported for the PostgreSQL dialect. Full DDL specification is at https://cloud.google.com/spanner/docs/data-definition-language. If --ddl_file is set, --ddl is ignored. One line comments starting with -- are ignored. |
| `--proto-descriptors-file` | PROTO_DESCRIPTORS_FILE |  | Path of a file that contains a protobuf-serialized google.protobuf.FileDescriptorSet message. To generate it, install and run protoc with --include_imports and --descriptor_set_out. |


**Examples:**
```bash
To create an empty Cloud Spanner database, run:

    $ gcloud spanner databases create testdb --instance=my-instance-id

To create a Cloud Spanner database with populated schema, run:

    $ gcloud spanner databases create testdb --instance=my-instance-id \
        --ddl='CREATE TABLE mytable (a INT64, b INT64) PRIMARY KEY(a)'

To create a Cloud Spanner database with the PostgreSQL dialect, run:

    $ gcloud spanner databases create testdb --instance=my-instance-id \
        --database-dialect=POSTGRESQL
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/create)

---
### `gcloud spanner databases delete`

Delete a Cloud Spanner database

Delete a Cloud Spanner database.

Note: Cloud Spanner might continue to accept requests for a few seconds
after the database has been deleted.

**Synopsis:**
```
gcloud spanner databases delete (DATABASE : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To delete a Cloud Spanner database, run:

    $ gcloud spanner databases delete my-database-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/delete)

---
### `gcloud spanner databases describe`

Describe a Cloud Spanner database

Describe a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases describe (DATABASE : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To describe a Cloud Spanner database, run:

    $ gcloud spanner databases describe my-database-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/describe)

---
### `gcloud spanner databases execute-sql`

Executes a SQL query against a Cloud Spanner database

Executes a SQL query against a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases execute-sql (DATABASE : --instance=INSTANCE)
    --sql=SQL [--database-role=DATABASE_ROLE] [--enable-partitioned-dml]
    [--priority=PRIORITY] [--query-mode=QUERY_MODE; default="NORMAL"]
    [--timeout=TIMEOUT; default="10m"]
    [--read-timestamp=TIMESTAMP | --strong] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to execute the SQL query
against. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--sql` | SQL |  | The SQL query to issue to the database. Cloud Spanner SQL is described at https://cloud.google.com/spanner/docs/query-syntax |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-role` | DATABASE_ROLE |  | Database role user assumes while accessing the database. |
| `--enable-partitioned-dml` |  |  | Execute DML statement using Partitioned DML |
| `--priority` | one of: high, low, medium, unspecified |  | The priority for the execute SQL request. PRIORITY must be one of: high, low, medium, unspecified. |
| `--query-mode` | one of: NORMAL Returns only the query result, without any information about the query plan | NORMAL | Mode in which the query must be processed. QUERY_MODE must be one of: NORMAL Returns only the query result, without any information about the query plan. PLAN Returns only the query plan, without any result rows or execution statistics information. PROFILE Returns the query plan, overall execution statistics, operator-level execution statistics, along with the result rows. WITH_PLAN_AND_STATS Returns the query plan, overall (but not operator-level) execution statistics, along with the results. WITH_STATS Returns the overall (but not operator-level) execution statistics along with the results. |
| `--timeout` | TIMEOUT | 10m | Maximum time to wait for the SQL query to complete. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To execute a SQL SELECT statement against example-database under
example-instance, run:

    $ gcloud spanner databases execute-sql example-database \
        --instance=example-instance \
        --sql='SELECT * FROM MyTable WHERE MyKey = 1'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/execute-sql)

---
### `gcloud spanner databases get-iam-policy`

Get the IAM policy for a Cloud Spanner database

Get the IAM policy for a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases get-iam-policy (DATABASE : --instance=INSTANCE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to get IAM policy binding
for. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To print the IAM policy for a given Cloud Spanner database, run:

    $ gcloud spanner databases get-iam-policy my-database-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/get-iam-policy)

---
### `gcloud spanner databases list`

List the Cloud Spanner databases contained within the given instance

List the Cloud Spanner databases contained within the given instance.

**Synopsis:**
```
gcloud spanner databases list [--instance=INSTANCE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[* set the property core/project.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line; + set the property spanner/instance. |


**Examples:**
```bash
To list the Cloud Spanner databases in an instance, run:

    $ gcloud spanner databases list --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/list)

---
### `gcloud spanner databases remove-iam-policy-binding`

Remove IAM policy binding of a Cloud Spanner database

Remove an IAM policy binding of a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases remove-iam-policy-binding
    (DATABASE : --instance=INSTANCE) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to remove the IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
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
'test-user@gmail.com' with database 'my-database' and instance
'my-instance', run:

    $ gcloud spanner databases remove-iam-policy-binding my-database \
        --instance='my-instance' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/spanner.databaseAdmin' and the user
'test-user@gmail.com' with database 'my-database' and instance
'my-instance', run:

    $ gcloud spanner databases remove-iam-policy-binding my-database \
        --instance='my-instance' --member='user:test-user@gmail.com' \
        --role='roles/spanner.databaseAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/remove-iam-policy-binding)

---
### `gcloud spanner databases restore`

Restore a Cloud Spanner database

Restores from a backup to a new Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases restore
    (--destination-database=DESTINATION_DATABASE
      : --destination-instance=DESTINATION_INSTANCE)
    (--source-backup=SOURCE_BACKUP : --source-instance=SOURCE_INSTANCE)
    [--async]
    [--encryption-type=ENCRYPTION_TYPE --kms-keys=[KMS_KEYS,...]
      | [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-database` | DESTINATION_DATABASE |  | _[This must be specified.]_ ID of the database or fully qualified identifier for the database. To set the database attribute: + provide the argument --destination-database on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--destination-instance` | DESTINATION_INSTANCE |  | _[This must be specified.]_ The Cloud Spanner instance for the database. To set the instance attribute: + provide the argument --destination-database on the command line with a fully specified name; + provide the argument --destination-instance on the command line; + set the property spanner/instance. |
| `--source-backup` | SOURCE_BACKUP |  | _[This must be specified.]_ ID of the backup or fully qualified identifier for the backup. To set the backup attribute: + provide the argument --source-backup on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--source-instance` | SOURCE_INSTANCE |  | _[This must be specified.]_ The Cloud Spanner instance for the backup. To set the instance attribute: + provide the argument --source-backup on the command line with a fully specified name; + provide the argument --source-instance on the command line; + set the property spanner/instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--encryption-type` | one of: customer-managed-encryption Use the provided Cloud KMS key for encryption |  | The encryption type of the restored database. ENCRYPTION_TYPE must be one of: customer-managed-encryption Use the provided Cloud KMS key for encryption. If this option is selected, kms-key must be set. google-default-encryption Use Google default encryption. use-config-default-or-backup-encryption Use the default encryption configuration if one exists, otherwise use the same encryption configuration as the backup. |


**Examples:**
```bash
To restore a backup, run:

    $ gcloud spanner databases restore --source-backup=BACKUP_ID \
        --source-instance=SOURCE_INSTANCE \
        --destination-database=DATABASE \
        --destination-instance=INSTANCE_NAME

To restore a backup using relative names, run:

    $ gcloud spanner databases restore \
        --source-backup=projects/PROJECT_ID/instances/\
    SOURCE_INSTANCE_ID/backups/BACKUP_ID \
        --destination-database=projects/PROJECT_ID/instances/\
    SOURCE_INSTANCE_ID/databases/DATABASE_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/restore)

---
### `gcloud spanner databases set-iam-policy`

Set the IAM policy for a Cloud Spanner database

Set the IAM policy for a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases set-iam-policy (DATABASE : --instance=INSTANCE)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to set IAM policy binding
for. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.

POLICY_FILE
   Name of JSON or YAML file with the IAM policy.
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for a spanner database with the ID my-database-id:

    $ gcloud spanner databases set-iam-policy my-database-id \
        --instance=my-instance-id policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/set-iam-policy)

---
### `gcloud spanner databases update`

Update a Cloud Spanner database

Update a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases update (DATABASE : --instance=INSTANCE) [--async]
    [--[no-]enable-drop-protection | --kms-keys=KMS_KEY,[KMS_KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enable database deletion protection on a Cloud Spanner database
'my-database', run:

    $ gcloud spanner databases update my-database \
        --enable-drop-protection

To disable database deletion protection on a Cloud Spanner database
'my-database', run:

    $ gcloud spanner databases update my-database \
        --no-enable-drop-protection

To update KMS key references for a Cloud Spanner database 'my-database',
run:

    $ gcloud spanner databases update my-database --kms-keys="KEY1,KEY2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/update)

---

## `gcloud spanner databases ddl` — manage the DDL for Cloud Spanner databases
### `gcloud spanner databases ddl describe`

Describe the DDL for a Cloud Spanner database

Describe the DDL for a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases ddl describe (DATABASE : --instance=INSTANCE)
    [--include-proto-descriptors] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database of which the ddl to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--include-proto-descriptors` |  |  | Include debug string of proto bundle descriptors in the output. The output is information only and not meant to be parsed. |


**Examples:**
```bash
To describe the DDL for a given Cloud Spanner database, run:

    $ gcloud spanner databases ddl describe my-database-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/ddl/describe)

---
### `gcloud spanner databases ddl update`

Update the DDL for a Cloud Spanner database

Update the DDL for a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner databases ddl update (DATABASE : --instance=INSTANCE)
    [--async] [--ddl=DDL] [--ddl-file=DDL_FILE]
    [--proto-descriptors-file=PROTO_DESCRIPTORS_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database of which the ddl to update.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--ddl` | DDL |  | Semi-colon separated DDL (data definition language) statements to run inside the database. If a statement fails, all subsequent statements in the batch are automatically cancelled. |
| `--ddl-file` | DDL_FILE |  | Path of a file containing semi-colon separated DDL (data definition language) statements to run inside the database. If a statement fails, all subsequent statements in the batch are automatically cancelled. If --ddl_file is set, --ddl is ignored. One line comments starting with -- are ignored. |
| `--proto-descriptors-file` | PROTO_DESCRIPTORS_FILE |  | Path of a file that contains a protobuf-serialized google.protobuf.FileDescriptorSet message. To generate it, install and run protoc with --include_imports and --descriptor_set_out. |


**Examples:**
```bash
To add a column to a table in the given Cloud Spanner database, run:

    $ gcloud spanner databases ddl update my-database-id \
        --instance=my-instance-id \
        --ddl='ALTER TABLE test_table ADD COLUMN a INT64'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/ddl/update)

---

## `gcloud spanner databases roles` — manage Cloud Spanner database roles
### `gcloud spanner databases roles list`

List the Cloud Spanner database roles defined in the given database

List the Cloud Spanner database roles defined in the given database.

**Synopsis:**
```
gcloud spanner databases roles list
    (--database=DATABASE : --instance=INSTANCE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | _[This must be specified.]_ ID of the database or fully qualified identifier for the database. To set the database attribute: + provide the argument --database on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--instance` | INSTANCE |  | _[This must be specified.]_ The Cloud Spanner instance for the database. To set the instance attribute: + provide the argument --database on the command line with a fully specified name; + provide the argument --instance on the command line; + set the property spanner/instance. |


**Examples:**
```bash
To list the Cloud Spanner database roles in a database, run:

    $ gcloud spanner databases roles list --instance=my-instance-id \
        --database=my-database-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/roles/list)

---

## `gcloud spanner databases sessions` — manage the sessions for Cloud Spanner databases
### `gcloud spanner databases sessions delete`

Delete a Cloud Spanner session

Delete a Cloud Spanner session.

**Synopsis:**
```
gcloud spanner databases sessions delete
    (SESSION : --database=DATABASE --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Session resource - The Cloud Spanner session to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument session on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SESSION
     ID of the session or fully qualified identifier for the session.

     To set the session attribute:
     + provide the argument session on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --database=DATABASE
     The Cloud Spanner database for the session.

     To set the database attribute:
     + provide the argument session on the command line with a fully
       specified name;
     + provide the argument --database on the command line.

  --instance=INSTANCE
     The Cloud Spanner instance for the session.

     To set the instance attribute:
     + provide the argument session on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To delete a Cloud Spanner session, run:

    $ gcloud spanner databases sessions delete my-session-id \
        --instance=my-instance-id --database=my-database-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/sessions/delete)

---
### `gcloud spanner databases sessions list`

List the Cloud Spanner sessions contained within the given database

List the Cloud Spanner sessions contained within the given database.

**Synopsis:**
```
gcloud spanner databases sessions list
    (--database=DATABASE : --instance=INSTANCE)
    [--server-filter=SERVER_FILTER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | _[This must be specified.]_ ID of the database or fully qualified identifier for the database. To set the database attribute: + provide the argument --database on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--instance` | INSTANCE |  | _[This must be specified.]_ The Cloud Spanner instance for the database. To set the instance attribute: + provide the argument --database on the command line with a fully specified name; + provide the argument --instance on the command line; + set the property spanner/instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--server-filter` | SERVER_FILTER |  | An expression for filtering the results of the request on the server. Filter rules are case insensitive. The fields eligible for filtering are: * labels.key where key is the name of a label. |


**Examples:**
```bash
To list the sessions for a given Cloud Spanner database, run:

    $ gcloud spanner databases sessions list --instance=my-instance-id \
        --database=my-database-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/sessions/list)

---

## `gcloud spanner databases splits` — manage the split points for Spanner databases
### `gcloud spanner databases splits add`

Add split points to a Spanner database

Add split points to a Spanner database.

**Synopsis:**
```
gcloud spanner databases splits add (DATABASE : --instance=INSTANCE)
    --splits-file=SPLITS_FILE [--initiator=INITIATOR]
    [--split-expiration-date=SPLIT_EXPIRATION_DATE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database on which to add split
points. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--splits-file` | SPLITS_FILE |  | The path of a file containing split points to add to the database. Separate split points in the file with a new line. The file format is <ObjectType>[space]<ObjectName>[space]<Split Value>, where the ObjectType is one of TABLE or INDEX and the Split Value is the split point key. For index, the split point key is the index key with or without a full table key prefix. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--initiator` | INITIATOR |  | The tag to identify the initiator of the split points. |
| `--split-expiration-date` | SPLIT_EXPIRATION_DATE |  | The date when the split points become system managed and becomes eligible for merging. The default is 10 days from the date of creation. The maximum is 30 days from the date of creation. |


**Examples:**
```bash
To add split points to the given Spanner database, run:

    $ gcloud spanner databases splits add my-database-id \
        --instance=my-instance-id --splits-file=path/to/splits.txt \
        --initiator=my-initiator-string \
        --split-expiration-date=2024-08-15T15:55:10Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/splits/add)

---
### `gcloud spanner databases splits list`

List split points that are added by a user to a Spanner database

List split points that are added by a user to a Spanner database.

**Synopsis:**
```
gcloud spanner databases splits list (DATABASE : --instance=INSTANCE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database on which to list split
points. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To list the user added split points of the given Spanner database, run:

    $ gcloud spanner databases splits list my-database-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/databases/splits/list)

---
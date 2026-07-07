# gcloud spanner backups

manage Cloud Spanner backups

### `gcloud spanner backups add-iam-policy-binding`

Add IAM policy binding to a Cloud Spanner backup

Add an IAM policy binding to a Cloud Spanner backup. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud spanner backups add-iam-policy-binding
    (BACKUP : --instance=INSTANCE) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Spanner backup to which to add the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
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
To add an IAM policy binding for the role of 'roles/spanner.backupAdmin'
for the user 'test-user@gmail.com' with backup 'example-backup' and
instance 'example-instance', run:

    $ gcloud spanner backups add-iam-policy-binding example-backup \
        --instance='example-instance' \
        --member='user:test-user@gmail.com' \
        --role='roles/spanner.backupAdmin'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/spanner.backupAdmin' and the user 'test-user@gmail.com'
with backup 'example-backup' and instance 'example-instance', run:

    $ gcloud spanner backups add-iam-policy-binding example-backup \
        --instance='example-instance' \
        --member='user:test-user@gmail.com' \
        --role='roles/spanner.backupAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/add-iam-policy-binding)

---
### `gcloud spanner backups copy`

Copies a backup of a Cloud Spanner database

Copies a backup of a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner backups copy
    (--destination-backup=DESTINATION_BACKUP
      : --destination-instance=DESTINATION_INSTANCE)
    (--expiration-date=EXPIRATION_DATE
      | --retention-period=RETENTION_PERIOD)
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
| `--destination-backup` | DESTINATION_BACKUP |  | _[This must be specified.]_ ID of the backup or fully qualified identifier for the backup. To set the backup attribute: + provide the argument --destination-backup on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--destination-instance` | DESTINATION_INSTANCE |  | _[This must be specified.]_ The Cloud Spanner instance for the backup. To set the instance attribute: + provide the argument --destination-backup on the command line with a fully specified name; + provide the argument --destination-instance on the command line; + set the property spanner/instance. |
| `--expiration-date` | EXPIRATION_DATE |  | _[Exactly one of these must be specified:]_ Expiration time of the backup, must be at least 6 hours and at most 366 days from the time when the source backup is created. See $ gcloud topic datetimes for information on date/time formats. |
| `--retention-period` | RETENTION_PERIOD |  | _[Exactly one of these must be specified:]_ Retention period of the backup relative from now, must be at least 6 hours and at most 366 days from the time when the source backup is created. See $ gcloud topic datetimes for information on duration formats. |
| `--source-backup` | SOURCE_BACKUP |  | _[This must be specified.]_ ID of the backup or fully qualified identifier for the backup. To set the backup attribute: + provide the argument --source-backup on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--source-instance` | SOURCE_INSTANCE |  | _[This must be specified.]_ The Cloud Spanner instance for the backup. To set the instance attribute: + provide the argument --source-backup on the command line with a fully specified name; + provide the argument --source-instance on the command line; + set the property spanner/instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--encryption-type` | one of: customer-managed-encryption Use the provided Cloud KMS key for encryption |  | The encryption type of the copied backup. ENCRYPTION_TYPE must be one of: customer-managed-encryption Use the provided Cloud KMS key for encryption. If this option is selected, kms-key must be set. google-default-encryption Use Google default encryption. use-config-default-or-backup-encryption Use the default encryption configuration if one exists. otherwise use the same encryption configuration as the source backup. |


**Examples:**
```bash
To copy a backup within the same project, run:

    $ gcloud spanner backups copy --source-instance=SOURCE_INSTANCE_ID \
        --source-backup=SOURCE_BACKUP_ID \
        --destination-instance=DESTINATION_INSTANCE_ID \
        --destination-backup=DESTINATION_BACKUP_ID \
        --expiration-date=2020-03-29T10:49:41Z

To copy a backup to a different project, run:

    $ gcloud spanner backups copy \
        --source-backup=projects/SOURCE_PROJECT_ID/instances/\
    SOURCE_INSTANCE_ID/backups/SOURCE_BACKUP_ID \
        --destination-backup=projects/DESTINATION_PROJECT_ID/instances/\
    DESTINATION_INSTANCE_ID/backups/DESTINATION_BACKUP_ID \
        --expiration-date=2020-03-29T10:49:41Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/copy)

---
### `gcloud spanner backups create`

Creates a backup of a Cloud Spanner database

Creates a backup of a Cloud Spanner database.

**Synopsis:**
```
gcloud spanner backups create (BACKUP : --instance=INSTANCE)
    --database=DATABASE
    (--expiration-date=EXPIRATION_DATE
      | --retention-period=RETENTION_PERIOD) [--async]
    [--version-time=TIMESTAMP]
    [--encryption-type=ENCRYPTION_TYPE --kms-keys=[KMS_KEYS,...]
      | [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Spanner backup to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the backup.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | ID of the database from which the backup will be created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--version-time` | TIMESTAMP |  | The backup will contain an externally consistent copy of the database at the timestamp specified by --version-time. If --version-time is not specified, the system will use the creation time of the backup. |
| `--encryption-type` | one of: customer-managed-encryption Use the provided Cloud KMS key for encryption.If this option is selected, kms-key must be set |  | The encryption type of the backup. ENCRYPTION_TYPE must be one of: customer-managed-encryption Use the provided Cloud KMS key for encryption.If this option is selected, kms-key must be set. google-default-encryption Use Google default encryption. use-database-encryption Use the same encryption configuration as the database. |


**Examples:**
```bash
To create a backup asynchronously, run:

    $ gcloud spanner backups create BACKUP_ID --instance=INSTANCE_NAME \
        --database=DATABASE --expiration-date=2020-03-29T10:49:41Z \
        --async

To create a backup synchronously, run:

    $ gcloud spanner backups create BACKUP_ID --instance=INSTANCE_NAME \
        --database=DATABASE --retention-period=2w
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/create)

---
### `gcloud spanner backups delete`

Delete an existing backup

Delete an existing backup.

**Synopsis:**
```
gcloud spanner backups delete (BACKUP : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Spanner backup to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To delete a backup, run:

    $ gcloud spanner backups delete BACKUP_NAME --instance=INSTANCE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/delete)

---
### `gcloud spanner backups describe`

Retrieves information about a backup

Retrieves information about a backup.

**Synopsis:**
```
gcloud spanner backups describe (BACKUP : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Spanner backup to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To describe a backup, run:

    $ gcloud spanner backups describe BACKUP_ID --instance=INSTANCE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/describe)

---
### `gcloud spanner backups get-iam-policy`

Get the IAM policy for a Cloud Spanner backup

gcloud spanner backups get-iam-policy displays the IAM policy associated
with a Cloud Spanner database. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy. The output includes an
"etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ {parent} set-iam-policy for additional
details.

**Synopsis:**
```
gcloud spanner backups get-iam-policy (BACKUP : --instance=INSTANCE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Spanner backup for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To print the IAM policy for a given Cloud Spanner backup, run:

    $ gcloud spanner backups get-iam-policy example-backup \
        --instance=example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/get-iam-policy)

---
### `gcloud spanner backups list`

List existing Cloud Spanner Cloud Spanner backups

List existing Cloud Spanner Cloud Spanner backups.

**Synopsis:**
```
gcloud spanner backups list [--database=DATABASE] [--instance=INSTANCE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | ID of the source database. The database flag will take precedence over filters added for database. |


**Examples:**
```bash
To list existing backups for the instance, run:

    $ gcloud spanner backups list --instance=INSTANCE_NAME

To list existing backups for a database, run:

    $ gcloud spanner backups list --instance=INSTANCE_NAME \
        --database=DATABASE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/list)

---
### `gcloud spanner backups remove-iam-policy-binding`

Remove IAM policy binding of a Cloud Spanner backup

Remove an IAM policy binding of a Cloud Spanner backup. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud spanner backups remove-iam-policy-binding
    (BACKUP : --instance=INSTANCE) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Spanner backup to remove the IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
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
To remove an IAM policy binding for the role of 'roles/spanner.backupAdmin'
for the user 'test-user@gmail.com' with backup 'example-backup' and
instance 'example-instance', run:

    $ gcloud spanner backups remove-iam-policy-binding example-backup \
        --instance='example-instance' \
        --member='user:test-user@gmail.com' \
        --role='roles/spanner.backupAdmin'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/spanner.backupAdmin' and the user
'test-user@gmail.com' with backup 'example-backup' and instance
'example-instance', run:

    $ gcloud spanner backups remove-iam-policy-binding example-backup \
        --instance='example-instance' \
        --member='user:test-user@gmail.com' \
        --role='roles/spanner.backupAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/remove-iam-policy-binding)

---
### `gcloud spanner backups set-iam-policy`

Set the IAM policy for a Cloud Spanner backup

Set the IAM policy for a Cloud Spanner backup given a backup ID and a file
encoded in JSON or YAML that contains the IAM policy.

**Synopsis:**
```
gcloud spanner backups set-iam-policy (BACKUP : --instance=INSTANCE)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Spanner backup to set the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for a spanner instance with the ID
example-instance:

    $ gcloud spanner backups set-iam-policy example-backup \
        --instance=example-instance policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/set-iam-policy)

---
### `gcloud spanner backups update-metadata`

Updates the metadata of a Cloud Spanner a backup

Updates the metadata of a Cloud Spanner a backup.

**Synopsis:**
```
gcloud spanner backups update-metadata (BACKUP : --instance=INSTANCE)
    (--expiration-date=EXPIRATION_DATE
      | --retention-period=RETENTION_PERIOD) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Spanner backup to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Cloud Spanner instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--expiration-date` | EXPIRATION_DATE |  | _[Exactly one of these must be specified:]_ Expiration time of the backup, must be at least 6 hours and at most 366 days from the time of creation. See $ gcloud topic datetimes for information on date/time formats. |
| `--retention-period` | RETENTION_PERIOD |  | _[Exactly one of these must be specified:]_ Retention period of the backup relative from now, must be at least 6 hours and at most a year from the time of creation. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To update the backup metadata with an exact expiration date, run:

    $ gcloud spanner backups update-metadata BACKUP_ID \
        --instance=INSTANCE_NAME --expiration-date=2020-03-29T10:49:41Z

To update the backup metadata with a retention period, run:

    $ gcloud spanner backups update-metadata BACKUP_ID \
        --instance=INSTANCE_NAME --retention-period=2w
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/backups/update-metadata)

---
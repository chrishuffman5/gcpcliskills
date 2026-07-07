# gcloud bigtable backups

manage Cloud Bigtable backups

### `gcloud bigtable backups add-iam-policy-binding`

Add an IAM policy binding to a Cloud Bigtable Backup

Add an IAM policy binding to a Cloud Bigtable Backup. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable backups add-iam-policy-binding
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable Backup to add the IAM policy binding to.
The arguments in this group can be used to specify the attributes of this
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
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
test-user@gmail.com with backup my-backup in instance my-instance and
cluster my-cluster, run:

    $ gcloud bigtable backups add-iam-policy-binding my-backup \
        --instance=`my-instance` --cluster=`my-cluster` \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To add an IAM policy binding which expires at the end of the year 2020 for
the role of roles/bigtable.admin and the user test-user@gmail.com with
backup my-backup in instance my-instance and cluster my-cluster, run:

    $ gcloud bigtable backups add-iam-policy-binding my-backup \
        --instance=`my-instance` --cluster=`my-cluster` \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,\
    description=Expires at midnight on 2020-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/add-iam-policy-binding)

---
### `gcloud bigtable backups copy`

Copy a Cloud Bigtable backup to a new backup

This command creates a copy of a Cloud Bigtable backup.

**Synopsis:**
```
gcloud bigtable backups copy
    (--destination-backup=DESTINATION_BACKUP
      : --destination-cluster=DESTINATION_CLUSTER
      --destination-instance=DESTINATION_INSTANCE
      --destination-project=DESTINATION_PROJECT)
    (--expiration-date=EXPIRATION_DATE
      | --retention-period=RETENTION_PERIOD)
    (--source-backup=SOURCE_BACKUP : --source-cluster=SOURCE_CLUSTER
      --source-instance=SOURCE_INSTANCE --source-project=SOURCE_PROJECT)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-backup` | DESTINATION_BACKUP |  | _[This must be specified.]_ ID of the backup or fully qualified identifier for the backup. To set the backup attribute: + provide the argument --destination-backup on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--destination-cluster` | DESTINATION_CLUSTER |  | _[This must be specified.]_ Bigtable cluster for the backup. To set the cluster attribute: + provide the argument --destination-backup on the command line with a fully specified name; + provide the argument --destination-cluster on the command line. |
| `--destination-instance` | DESTINATION_INSTANCE |  | _[This must be specified.]_ Bigtable instance for the backup. To set the instance attribute: + provide the argument --destination-backup on the command line with a fully specified name; + provide the argument --destination-instance on the command line; + provide the argument --source-instance on the command line. |
| `--destination-project` | DESTINATION_PROJECT |  | _[This must be specified.]_ Project ID of the Google Cloud project for the backup. To set the project attribute: + provide the argument --destination-backup on the command line with a fully specified name; + provide the argument --destination-project on the command line; + provide the argument --source-project on the command line; + provide the argument --project on the command line; + set the property core/project. |
| `--expiration-date` | EXPIRATION_DATE |  | _[Exactly one of these must be specified:]_ Expiration time of the backup, must be at least 6 hours and at most 30 days from the time the source backup is created. See $ gcloud topic datetimes for information on date/time formats. |
| `--retention-period` | RETENTION_PERIOD |  | _[Exactly one of these must be specified:]_ Retention period of the backup relative from now, must be at least 6 hours and at most 30 days from the time the source backup is created. See $ gcloud topic datetimes for information on duration formats. |
| `--source-backup` | SOURCE_BACKUP |  | _[This must be specified.]_ ID of the backup or fully qualified identifier for the backup. To set the backup attribute: + provide the argument --source-backup on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--source-cluster` | SOURCE_CLUSTER |  | _[This must be specified.]_ Bigtable cluster for the backup. To set the cluster attribute: + provide the argument --source-backup on the command line with a fully specified name; + provide the argument --source-cluster on the command line. |
| `--source-instance` | SOURCE_INSTANCE |  | _[This must be specified.]_ Bigtable instance for the backup. To set the instance attribute: + provide the argument --source-backup on the command line with a fully specified name; + provide the argument --source-instance on the command line; + provide the argument --destination-instance on the command line. |
| `--source-project` | SOURCE_PROJECT |  | _[This must be specified.]_ Project ID of the Google Cloud project for the backup. To set the project attribute: + provide the argument --source-backup on the command line with a fully specified name; + provide the argument --source-project on the command line; + provide the argument --destination-project on the command line; + provide the argument --project on the command line; + set the property core/project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To copy a backup within the same project, run:

    $ gcloud bigtable backups copy --source-instance=SOURCE_INSTANCE \
        --source-cluster=SOURCE_CLUSTER --source-backup=SOURCE_BACKUP \
        --destination-instance=DESTINATION_INSTANCE \
        --destination-cluster=DESTINATION_CLUSTER \
        --destination-backup=DESTINATION_BACKUP \
        --expiration-date=2023-09-01T10:49:41Z

To copy a backup to a different project, run:

    $ gcloud bigtable backups copy \
        --source-backup=projects/SOURCE_PROJECT/instances/\
    SOURCE_INSTANCE/clusters/SOURCE_CLUSTER/backups/SOURCE_BACKUP \
        --destination-backup=projects/DESTINATION_PROJECT/instances/\
    DESTINATION_INSTANCE/clusters/DESTINATION_CLUSTER/backups/\
    DESTINATION_BACKUP --expiration-date=2022-08-01T10:49:41Z

To set retention period and run asyncronously, run:

    $ gcloud bigtable backups copy \
        --source-backup=projects/SOURCE_PROJECT/instances/\
    SOURCE_INSTANCE/clusters/SOURCE_CLUSTER/backups/SOURCE_BACKUP \
        --destination-backup=projects/DESTINATION_PROJECT/instances/\
    DESTINATION_INSTANCE/clusters/DESTINATION_CLUSTER/backups/\
    DESTINATION_BACKUP --retention-period=2w --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/copy)

---
### `gcloud bigtable backups create`

Creates a backup of a Cloud Bigtable table

Creates a backup of a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable backups create
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) --table=TABLE
    (--expiration-date=EXPIRATION_DATE
      | --retention-period=RETENTION_PERIOD) [--async]
    [--backup-type=BACKUP_TYPE]
    [--hot-to-standard-time=HOT_TO_STANDARD_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The Cloud Bigtable backup to create. The arguments in
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--table` | TABLE |  | ID of the table from which the backup will be created. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--backup-type` | one of: backup-type-unspecified, hot, standard |  | Type of the backup; whether the backup is a standard backup or a hot backup. BACKUP_TYPE must be one of: backup-type-unspecified, hot, standard. |
| `--hot-to-standard-time` | HOT_TO_STANDARD_TIME |  | Time at which a hot backup will be converted to a standard backup relative from now; must be: * At least 24 hours Only applies for hot backups. See $ gcloud topic datetimes for information on date/time formats. |


**Examples:**
```bash
To create a backup BACKUP_NAME asyncronously from table TABLE_NAME which
expires at 2019-03-30T10:49:41Z, run:

    $ gcloud bigtable backups create BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --table=TABLE_NAME --expiration-date=2019-03-30T10:49:41Z \
        --async

To create a backup BACKUP_NAME syncronously from table TABLE_NAME which
expires in 2 weeks from now, run:

    $ gcloud bigtable backups create BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --table=TABLE_NAME --retention-period=2w

To create a hot backup BACKUP_NAME from table TABLE_NAME which expires in 2
weeks from now, run:

    $ gcloud bigtable backups create BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --table=TABLE_NAME --retention-period=2w --backup-type=HOT

To create a hot backup BACKUP_NAME from table TABLE_NAME which will be
converted to a standard backup at 2019-03-31T10:49:41Z and expires in 2
weeks from now, run:

    $ gcloud bigtable backups create BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --table=TABLE_NAME --retention-period=2w --backup-type=HOT \
        --hot-to-standard-time=2019-03-31T10:49:41Z

To create a hot backup BACKUP_NAME from table TABLE_NAME which will be
converted to a standard backup in 1 week from now and expires in 2 weeks
from now, run:

    $ gcloud bigtable backups create BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --table=TABLE_NAME --retention-period=2w --backup-type=HOT \
        --hot-to-standard-time=+P1w
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/create)

---
### `gcloud bigtable backups delete`

Delete an existing backup

Delete an existing backup.

**Synopsis:**
```
gcloud bigtable backups delete
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable backup to delete. The arguments in this
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To delete a backup, run:

    $ gcloud bigtable backups delete BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/delete)

---
### `gcloud bigtable backups describe`

Retrieves information about a backup

Retrieves information about a backup.

**Synopsis:**
```
gcloud bigtable backups describe
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable backup to describe. The arguments in this
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To describe a backup, run:

    $ gcloud bigtable backups describe BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/describe)

---
### `gcloud bigtable backups get-iam-policy`

Get an IAM policy on a Cloud Bigtable Backup

Get an IAM policy on a Cloud Bigtable Backup.

**Synopsis:**
```
gcloud bigtable backups get-iam-policy
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable Backup to get the IAM policy for. The
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To get the IAM policy on the backup my-backup in instance my-instance and
cluster my-cluster, run:

    $ gcloud bigtable backups get-iam-policy my-backup \
        --instance=`my-instance` --cluster=`my-cluster`

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/get-iam-policy)

---
### `gcloud bigtable backups list`

List existing Bigtable backups

List existing Bigtable backups.

**Synopsis:**
```
gcloud bigtable backups list [--cluster=CLUSTER] [--instance=INSTANCE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[specified name.]_ ID of the cluster or fully qualified identifier for the cluster. To set the cluster attribute: + provide the argument --cluster on the command line. |
| `--instance` | INSTANCE |  | _[* set the property core/project.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line. |


**Examples:**
```bash
To list all backups in an instance, run:

    $ gcloud bigtable backups list --instance=INSTANCE_NAME

To list all backups in a cluster, run:

    $ gcloud bigtable backups list --instance=INSTANCE_NAME \
        --cluster=CLUSTER_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/list)

---
### `gcloud bigtable backups remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Bigtable Backup

Remove an IAM policy binding from a Cloud Bigtable Backup. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable backups remove-iam-policy-binding
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable Backup to remove the IAM policy binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
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
test-user@gmail.com with backup my-backup in instance my-instance and
cluster my-cluster, run:

    $ gcloud bigtable backups remove-iam-policy-binding my-backup \
        --instance=`my-instance` --cluster=`my-cluster` \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To remove an IAM policy binding which expires at the end of the year 2020
for the role of roles/bigtable.admin and the user test-user@gmail.com with
backup my-backup in instance my-instance and cluster my-cluster, run:

    $ gcloud bigtable backups remove-iam-policy-binding my-backup \
        --instance=`my-instance` --cluster=`my-cluster` \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2021-01-01T00:00:00Z"),title=expires_end_of_2020,\
    description=Expires at midnight on 2020-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/remove-iam-policy-binding)

---
### `gcloud bigtable backups set-iam-policy`

Set an IAM policy on a Cloud Bigtable Backup

Set an IAM policy on a Cloud Bigtable Backup.

**Synopsis:**
```
gcloud bigtable backups set-iam-policy
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable Backup to set the IAM policy on. The
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
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
To set the IAM policy from file my-policy on the backup my-backup in
instance my-instance and cluster my-cluster, run:

    $ gcloud bigtable backups set-iam-policy my-backup \
        --instance=`my-instance` --cluster=`my-cluster` my-policy

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/set-iam-policy)

---
### `gcloud bigtable backups update`

Update a backup, only supported for the following fields: --expiration-date and --retention-period

Update a backup, only supported for the following fields: --expiration-date
and --retention-period.

**Synopsis:**
```
gcloud bigtable backups update
    (BACKUP : --cluster=CLUSTER --instance=INSTANCE)
    [--hot-to-standard-time=HOT_TO_STANDARD_TIME]
    [--expiration-date=EXPIRATION_DATE
      | --retention-period=RETENTION_PERIOD] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - Cloud Bigtable backup to update. The arguments in this
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

  --cluster=CLUSTER
     Name of the Bigtable cluster.

     To set the cluster attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --cluster on the command line.

  --instance=INSTANCE
     Name of the Bigtable instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hot-to-standard-time` | HOT_TO_STANDARD_TIME |  | Time at which a hot backup will be converted to a standard backup; must be at least 24 hours from backup creation time. Only applies for hot backups. See $ gcloud topic datetimes for information on date/time formats. See $ gcloud bigtable backups describe for creation time. |


**Examples:**
```bash
To update the expire time of backup BACKUP_NAME to 7 days from now, run:

    $ gcloud bigtable backups update BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --retention-period=7d

To update the hot-to-standard time of backup BACKUP_NAME to
2019-03-31T10:49:41Z, run:

    $ gcloud bigtable backups update BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --hot-to-standard-time=2019-03-31T10:49:41Z

To update the hot-to-standard time of backup BACKUP_NAME to 7 days from
now, run:

    $ gcloud bigtable backups update BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --hot-to-standard-time=+P7d

To clear the hot-to-standard time of backup BACKUP_NAME, run:

    $ gcloud bigtable backups update BACKUP_NAME \
        --instance=INSTANCE_NAME --cluster=CLUSTER_NAME \
        --hot-to-standard-time=''
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/backups/update)

---
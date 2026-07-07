# gcloud compute snapshots

list, describe, and delete Compute Engine snapshots

### `gcloud compute snapshots add-iam-policy-binding`

Add IAM policy binding to a Compute Engine snapshot

Add an IAM policy binding to the IAM policy of a Compute Engine snapshot.
One binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud compute snapshots add-iam-policy-binding SNAPSHOT_NAME
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The snapshot for which to add IAM policy binding to.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument snapshot_name on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNAPSHOT_NAME
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot_name attribute:
     + provide the argument snapshot_name on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/compute.securityAdmin'
for the user 'test-user@gmail.com' with snapshot 'my-snapshot', run:

    $ gcloud compute snapshots add-iam-policy-binding my-snapshot \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with snapshot 'my-snapshot', run:

    $ gcloud compute snapshots add-iam-policy-binding my-snapshot \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/add-iam-policy-binding)

---
### `gcloud compute snapshots add-labels`

Add labels to Google Compute Engine snapshots

gcloud compute snapshots add-labels adds labels to a Google Compute Engine
snapshot.

**Synopsis:**
```
gcloud compute snapshots add-labels SNAPSHOT_NAME --labels=[KEY=VALUE,...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_NAME
   Name of the snapshot to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | A list of labels to add. |


**Examples:**
```bash
To add key-value pairs k0=v0 and k1=v1 to 'example-snapshot'

    $ gcloud compute snapshots add-labels example-snapshot \
        --labels=k0=v0,k1=v1

Labels can be used to identify the snapshot and to filter them. To find a
snapshot labeled with key-value pair k1, v2

    $ gcloud compute snapshots list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute snapshots describe example-snapshot \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/add-labels)

---
### `gcloud compute snapshots create`

Create Compute Engine snapshots

gcloud compute snapshots create creates snapshot of persistent disk.
Snapshots are useful for backing up persistent disk data and for creating
custom images. For more information, see
https://cloud.google.com/compute/docs/disks/create-snapshots.

**Synopsis:**
```
gcloud compute snapshots create NAME [--async] [--chain-name=CHAIN_NAME]
    [--csek-key-file=FILE] [--description=DESCRIPTION] [--guest-flush]
    [--labels=[KEY=VALUE,...]] [--snapshot-type=SNAPSHOT_TYPE]
    [--source-disk=SOURCE_DISK]
    [--source-disk-for-recovery-checkpoint=SOURCE_DISK_FOR_RECOVERY_CHECKPOINT]
    [--source-disk-for-recovery-checkpoint-region=SOURCE_DISK_FOR_RECOVERY_CHECKPOINT_REGION]
    [--source-disk-key-file=FILE]
    [--source-instant-snapshot=SOURCE_INSTANT_SNAPSHOT]
    [--source-instant-snapshot-key-file=FILE] [--storage-location=LOCATION]
    [--source-disk-region=SOURCE_DISK_REGION
      | --source-disk-zone=SOURCE_DISK_ZONE]
    [--source-instant-snapshot-region=SOURCE_INSTANT_SNAPSHOT_REGION
      | --source-instant-snapshot-zone=SOURCE_INSTANT_SNAPSHOT_ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the snapshot.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--chain-name` | CHAIN_NAME |  | Create the new snapshot in the snapshot chain labeled with the specified name. The chain name must be 1-63 characters long and comply with RFC1035. Use this flag only if you are an advanced service owner who needs to create separate snapshot chains, for example, for chargeback tracking. When you describe your snapshot resource, this field is visible only if it has a non-empty value. |
| `--csek-key-file` | FILE |  | Path to a Customer-Supplied Encryption Key (CSEK) key file that maps Compute Engine resources to user managed keys to be used when creating, mounting, or taking snapshots of disks. If you pass - as value of the flag, the CSEK is read from stdin. See https://cloud.google.com/compute/docs/disks/customer-supplied-encryption for more details. |
| `--description` | DESCRIPTION |  | Text to describe the new snapshot. |
| `--guest-flush` |  |  | Create an application-consistent snapshot by informing the OS to prepare for the snapshot process. Currently only supported for creating snapshots of disks attached to Windows instances. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--snapshot-type` | one of: ARCHIVE, STANDARD |  | Type of snapshot. If a snapshot type is not specified, a STANDARD snapshot will be created. SNAPSHOT_TYPE must be one of: ARCHIVE, STANDARD. |
| `--source-disk` | SOURCE_DISK |  | Source disk used to create the snapshot. To create a snapshot from a source disk in a different project, specify the full path to the source disk. For example: https://www.googleapis.com/compute/v1/projects/MY-PROJECT/zones/MY-ZONE/disks/MY-DISK |
| `--source-disk-for-recovery-checkpoint` | SOURCE_DISK_FOR_RECOVERY_CHECKPOINT |  | Source disk whose recovery checkpoint used to create the snapshot. To create a snapshot from the recovery checkpoint of a source disk in a different project, specify the full path to the source disk. For example: projects/MY-PROJECT/regions/MY-REGION/disks/MY-DISK |
| `--source-disk-for-recovery-checkpoint-region` | SOURCE_DISK_FOR_RECOVERY_CHECKPOINT_REGION |  | Region of the source disk for recovery checkpoint to operate on. Overrides the default compute/region property value for this command invocation. |
| `--source-disk-key-file` | FILE |  | Path to the customer-supplied encryption key of the source disk. Required if the source disk is protected by a customer-supplied encryption key. |
| `--source-instant-snapshot` | SOURCE_INSTANT_SNAPSHOT |  | The name or URL of the source instant snapshot. If the name is provided, the instant snapshot's zone or region must be specified with --source-instant-snapshot-zone or --source-instant-snapshot-region accordingly. To create a snapshot from an instant snapshot in a different project, specify the full path to the instant snapshot. If the URL is provided, format should be: https://www.googleapis.com/compute/v1/projects/MY-PROJECT/zones/MY-ZONE/instantSnapshots/MY-INSTANT-SNAPSHOT |
| `--source-instant-snapshot-key-file` | FILE |  | Path to the customer-supplied encryption key of the source instant snapshot. Required if the source instant snapshot is protected by a customer-supplied encryption key. |
| `--storage-location` | LOCATION |  | Google Cloud Storage location, either regional or multi-regional, where snapshot content is to be stored. If absent, a nearby regional or multi-regional location is chosen automatically. |


**Examples:**
```bash
To create a snapshot 'my-snap' from a disk 'my-disk' in zone 'us-east1-a',
run:

    $ gcloud compute snapshots create my-snap --source-disk=my-disk \
      --source-disk-zone=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/create)

---
### `gcloud compute snapshots delete`

Delete Compute Engine snapshots

gcloud compute snapshots delete deletes one or more Compute Engine
snapshots.

**Synopsis:**
```
gcloud compute snapshots delete SNAPSHOT_NAME [SNAPSHOT_NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_NAME [SNAPSHOT_NAME ...]
   Names of the snapshots to delete.
```

**Examples:**
```bash
To delete Compute Engine snapshots with the names 'snapshot-1' and
'snapshot-2', run:

    $ gcloud compute snapshots delete snapshot-1 snapshot-2

To list all snapshots that were created before a specific date, use the
--filter flag with the gcloud compute snapshots list command.

    $ gcloud compute snapshots list \
        --filter="creationTimestamp<'2017-01-01'"

For more information on how to use --filter with the list command, run $
gcloud topic filters.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/delete)

---
### `gcloud compute snapshots describe`

Describe a Compute Engine snapshot

gcloud compute snapshots describe displays all data associated with a
Compute Engine snapshot in a project.

Given an existing snapshot is queried, successful output of this command
looks like the following:

    creationTimestamp: '2018-05-07T10:45:46.988-07:00'
    diskSizeGb: '500'
    id: '1234567891234567890'
    kind: compute#snapshot
    labelFingerprint: 12345abcdWW=
    name: zs9utdhb8r1x
    selfLink: https://www.googleapis.com/compute/v1/projects/test-project-name/global/snapshots/snapshot-number
    sourceDisk: https://www.googleapis.com/compute/v1/projects/test-project-name/zones/us-central1-c/disks/test
    sourceDiskId: '1234567891234567890'
    status: READY
    storageBytes: '0'
    storageBytesStatus: UP_TO_DATE

**Synopsis:**
```
gcloud compute snapshots describe SNAPSHOT_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_NAME
   Name of the snapshot to describe.
```

**Examples:**
```bash
To run gcloud compute snapshots describe, you'll need the name of a
snapshot. To list existing snapshots by name, run:

    $ gcloud compute snapshots list

To display specific details of an existing Compute Engine snapshot (like
its creation time, status, and storage details), run:

    $ gcloud compute snapshots describe SNAPSHOT_NAME \
        --format="table(creationTimestamp, status, storageBytesStatus)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/describe)

---
### `gcloud compute snapshots get-iam-policy`

Get the IAM policy for a Compute Engine snapshot

gcloud compute snapshots get-iam-policy displays the IAM policy associated
with a snapshot. If formatted as JSON, the output can be edited and used as
a policy file for set-iam-policy. The output includes an "etag" field
identifying the version emitted and allowing detection of concurrent policy
updates; see $ {parent} set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute snapshots get-iam-policy SNAPSHOT_NAME [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The snapshot to display the IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument snapshot_name on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNAPSHOT_NAME
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot_name attribute:
     + provide the argument snapshot_name on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given snapshot, run:

    $ gcloud compute snapshots get-iam-policy my-snapshot
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/get-iam-policy)

---
### `gcloud compute snapshots list`

List Google Compute Engine snapshots

gcloud compute snapshots list displays all Google Compute Engine snapshots
in a project.

**Synopsis:**
```
gcloud compute snapshots list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all snapshots in a project in table form, run:

    $ gcloud compute snapshots list

To list the URIs of all snapshots in a project, run:

    $ gcloud compute snapshots list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/list)

---
### `gcloud compute snapshots remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine snapshot

Remove an IAM policy binding from the IAM policy of a Compute Engine
snapshot. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud compute snapshots remove-iam-policy-binding SNAPSHOT_NAME
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The snapshot for which to remove IAM policy binding
from. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument snapshot_name on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNAPSHOT_NAME
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot_name attribute:
     + provide the argument snapshot_name on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/compute.securityAdmin' for the user 'test-user@gmail.com' with
snapshot 'my-snapshot', run:

    $ gcloud compute snapshots remove-iam-policy-binding my-snapshot \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with snapshot 'my-snapshot', run:

    $ gcloud compute snapshots remove-iam-policy-binding my-snapshot \
        --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/remove-iam-policy-binding)

---
### `gcloud compute snapshots remove-labels`

Remove labels from Google Compute Engine snapshots

gcloud compute snapshots remove-labels removes labels from a Google Compute
Engine snapshot.

**Synopsis:**
```
gcloud compute snapshots remove-labels SNAPSHOT_NAME
    (--all | --labels=KEY,[KEY,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_NAME
   Name of the snapshot to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[Exactly one of these must be specified:]_ Remove all labels from the resource. |
| `--labels` | KEY,[KEY,...] |  | _[Exactly one of these must be specified:]_ A comma-separated list of label keys to remove from the resource. |


**Examples:**
```bash
To remove existing labels with key k0 and k1 from 'example-snapshot'

    $ gcloud compute snapshots remove-labels example-snapshot \
        --labels=k0,k1

Labels can be used to identify the snapshot and to filter them. To find a
snapshot labeled with key-value pair k1, v2

    $ gcloud compute snapshots list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute snapshots describe example-snapshot \
        --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/remove-labels)

---
### `gcloud compute snapshots set-iam-policy`

Set the IAM policy for a Compute Engine snapshot

Sets the IAM policy for the given snapshot as defined in a JSON or YAML
file.

**Synopsis:**
```
gcloud compute snapshots set-iam-policy SNAPSHOT_NAME POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - The snapshot to set the IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument snapshot_name on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNAPSHOT_NAME
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot_name attribute:
     + provide the argument snapshot_name on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the snapshot my-snapshot:

    $ gcloud compute snapshots set-iam-policy my-snapshot policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/set-iam-policy)

---
### `gcloud compute snapshots update`

Update a Compute Engine snapshot

gcloud compute snapshots update updates labels for a Compute Engine
snapshot.

**Synopsis:**
```
gcloud compute snapshots update SNAPSHOT_NAME
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT_NAME
   Name of the snapshot to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels k0 and k1 and remove labels with key k3, run:

    $ gcloud compute snapshots update example-snapshot \
        --update-labels=k0=value1,k1=value2 --remove-labels=k3

    `_k0_` and `_k1_` will be added as new labels if not already present.

Labels can be used to identify the snapshot and to filter them like:

    $ gcloud compute snapshots list --filter='labels.k1:value2'

To list only the labels when describing a resource, use --format:

    $ gcloud compute snapshots describe example-snapshot \
        --format="default(labels)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/snapshots/update)

---
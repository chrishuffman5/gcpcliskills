# gcloud bigtable instances

manage Cloud Bigtable instances

### `gcloud bigtable instances add-iam-policy-binding`

Add an IAM policy binding to a Cloud Bigtable instance

Add an IAM policy binding to a Cloud Bigtable instance. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable instances add-iam-policy-binding INSTANCE
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Cloud Bigtable instance to which to add the IAM
policy binding. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
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
test-user@gmail.com with instance my-instance, run:

    $ gcloud bigtable instances add-iam-policy-binding my-instance \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To add an IAM policy binding which expires at the end of the year 2018 for
the role of roles/bigtable.admin and the user test-user@gmail.com with
instance my-instance, run:

    $ gcloud bigtable instances add-iam-policy-binding my-instance \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,\
    description=Expires at midnight on 2018-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/add-iam-policy-binding)

---
### `gcloud bigtable instances create`

Create a new Bigtable instance

Create a new Bigtable instance.

**Synopsis:**
```
gcloud bigtable instances create INSTANCE --display-name=DISPLAY_NAME
    [--async] [--cluster=CLUSTER]
    [--cluster-config=[id=ID,zone=ZONE,[nodes=NODES],
      [node-scaling-factor=NODE_SCALING_FACTOR],[kms-key=KMS_KEY],
      [autoscaling-min-nodes=AUTOSCALING_MIN_NODES,
      autoscaling-max-nodes=AUTOSCALING_MAX_NODES,
      autoscaling-cpu-target=AUTOSCALING_CPU_TARGET,
      autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET],...]]
    [--cluster-num-nodes=CLUSTER_NUM_NODES]
    [--cluster-storage-type=CLUSTER_STORAGE_TYPE; default="ssd"]
    [--cluster-zone=CLUSTER_ZONE]
    [--instance-type=INSTANCE_TYPE; default="PRODUCTION"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name of the instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cluster` | CLUSTER |  | (DEPRECATED) ID of the cluster The --cluster argument is deprecated; use --cluster-config instead. |
| `--cluster-config` | one of: node-scaling-factor-1x, node-scaling-factor-2x |  | Repeatable. Specify cluster config as a key-value dictionary. This is the recommended argument for specifying cluster configurations. Keys can be: *id*: Required. The ID of the cluster. *zone*: Required. ID of the zone where the cluster is located. Supported zones are listed at https://cloud.google.com/bigtable/docs/locations. *nodes*: The number of nodes in the cluster. Default=1. *node-scaling-factor*: The node scaling factor for the cluster. Default=node-scaling-factor-1x. NODE_SCALING_FACTOR must be one of: node-scaling-factor-1x, node-scaling-factor-2x. *kms-key*: The Cloud KMS (Key Management Service) cryptokey that will be used to protect the cluster. *autoscaling-min-nodes*: The minimum number of nodes for autoscaling. *autoscaling-max-nodes*: The maximum number of nodes for autoscaling. *autoscaling-cpu-target*: The target CPU utilization percentage for autoscaling. Accepted values are from 10 to 80. *autoscaling-storage-target*: The target storage utilization gibibytes per node for autoscaling. Accepted values are from 2560 to 5120 for SSD clusters and 8192 to 16384 for HDD clusters. If this argument is specified, the deprecated arguments for configuring a single cluster will be ignored, including --cluster, --cluster-zone, --cluster-num-nodes. See EXAMPLES section. |
| `--cluster-num-nodes` | CLUSTER_NUM_NODES |  | (DEPRECATED) Number of nodes to serve. The --cluster-num-nodes argument is deprecated; use --cluster-config instead. |
| `--cluster-storage-type` | one of: hdd, ssd | ssd | Storage class for the cluster. CLUSTER_STORAGE_TYPE must be one of: hdd, ssd. |
| `--cluster-zone` | CLUSTER_ZONE |  | (DEPRECATED) ID of the zone where the cluster is located. Supported zones are listed at https://cloud.google.com/bigtable/docs/locations. The --cluster-zone argument is deprecated; use --cluster-config instead. |
| `--instance-type` | one of: DEVELOPMENT Development instances are low-cost instances meant for development and testing only | PRODUCTION | (DEPRECATED) The type of instance to create. The --instance-type argument is deprecated. DEVELOPMENT instances are no longer offered. All instances are of type PRODUCTION. INSTANCE_TYPE must be one of: DEVELOPMENT Development instances are low-cost instances meant for development and testing only. They do not provide high availability and no service level agreement applies. PRODUCTION Production instances provide high availability and are suitable for applications in production. Production instances created with the --instance-type argument have 3 nodes if a value is not provided for --cluster-num-nodes. |


**Examples:**
```bash
To create an instance with id my-instance-id with a cluster located in
us-east1-c, run:

    $ gcloud bigtable instances create my-instance-id \
        --display-name="My Instance" \
        --cluster-config=id=my-cluster-id,zone=us-east1-c

To create an instance with multiple clusters, run:

    $ gcloud bigtable instances create my-instance-id \
        --display-name="My Instance" \
        --cluster-config=id=my-cluster-id-1,zone=us-east1-c \
        --cluster-config=id=my-cluster-id-2,zone=us-west1-c,nodes=3

To create an instance with HDD storage and 10 nodes, run:

    $ gcloud bigtable instances create my-hdd-instance \
        --display-name="HDD Instance" --cluster-storage-type=HDD \
        --cluster-config=id=my-cluster-id,zone=us-east1-c,nodes=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/create)

---
### `gcloud bigtable instances delete`

Delete an existing Bigtable instance

Delete an existing Bigtable instance.

**Synopsis:**
```
gcloud bigtable instances delete INSTANCE [INSTANCE ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instances to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE [INSTANCE ...]
     IDs of the instances or fully qualified identifiers for the
     instances.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Examples:**
```bash
To delete an instance, run:

    $ gcloud bigtable instances delete my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/delete)

---
### `gcloud bigtable instances describe`

Describe an existing Bigtable instance

Describe an existing Bigtable instance.

**Synopsis:**
```
gcloud bigtable instances describe INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Examples:**
```bash
To view an instance's description, run:

    $ gcloud bigtable instances describe my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/describe)

---
### `gcloud bigtable instances get-iam-policy`

Get the IAM policy for a Cloud Bigtable instance

Get the IAM policy for a Cloud Bigtable instance.

**Synopsis:**
```
gcloud bigtable instances get-iam-policy INSTANCE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to get the IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Examples:**
```bash
To print the IAM policy for an instance, run:

    $ gcloud bigtable instances get-iam-policy my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/get-iam-policy)

---
### `gcloud bigtable instances list`

List existing Bigtable instances

List existing Bigtable instances.

**Synopsis:**
```
gcloud bigtable instances list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all instances, run:

    $ gcloud bigtable instances list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/list)

---
### `gcloud bigtable instances remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Bigtable instance

Remove an IAM policy binding from a Cloud Bigtable instance. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable instances remove-iam-policy-binding INSTANCE
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Cloud Bigtable instance to remove the IAM policy
binding from. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
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
test-user@gmail.com with instance my-instance, run:

    $ gcloud bigtable instances remove-iam-policy-binding my-instance \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To remove an IAM policy binding which expires at the end of the year 2018
for the role of roles/bigtable.admin and the user test-user@gmail.com with
instance my-instance, run:

    $ gcloud bigtable instances remove-iam-policy-binding my-instance \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,\
    description=Expires at midnight on 2018-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/remove-iam-policy-binding)

---
### `gcloud bigtable instances set-iam-policy`

Set IAM policy for an instance

Set the IAM policy for a Cloud Bigtable instance.

**Synopsis:**
```
gcloud bigtable instances set-iam-policy INSTANCE POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to set the IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy from 'policy.json' and set it
for an instance with 'my-instance-id' as the identifier:

    $ gcloud bigtable instances set-iam-policy my-instance-id policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/set-iam-policy)

---
### `gcloud bigtable instances update`

Modify an existing Bigtable instance

Modify an existing Bigtable instance.

**Synopsis:**
```
gcloud bigtable instances update INSTANCE [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name of the instance. |


**Examples:**
```bash
To update the display name for an instance, run:

    $ gcloud bigtable instances update my-instance-id \
        --display-name="Updated Instance Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/update)

---
### `gcloud bigtable instances upgrade`

Upgrade an existing instance's type from development to production

Upgrade an existing instance's type from development to production.

**Synopsis:**
```
gcloud bigtable instances upgrade INSTANCE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The instance to upgrade. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To upgrade a DEVELOPMENT instance to PRODUCTION, run:

    $ gcloud bigtable instances upgrade my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/upgrade)

---

## `gcloud bigtable instances tables` — query Cloud Bigtable tables
### `gcloud bigtable instances tables add-iam-policy-binding`

Add an IAM policy binding to a Cloud Bigtable table

Add an IAM policy binding to a Cloud Bigtable table. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable instances tables add-iam-policy-binding
    (TABLE : --instance=INSTANCE) --member=PRINCIPAL --role=ROLE
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

    $ gcloud bigtable instances tables add-iam-policy-binding my-table \
        --instance=`my-instance` --member=`user:test-user@gmail.com` \
        --role=`roles/editor`

To add an IAM policy binding which expires at the end of the year 2019 for
the role of roles/bigtable.admin and the user test-user@gmail.com with
table my-table in instance my-instance, run:

    $ gcloud bigtable instances tables add-iam-policy-binding my-table \
        --instance=`my-instance` --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2020-01-01T00:00:00Z"),title=expires_end_of_2019,\
    description=Expires at midnight on 2019-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/add-iam-policy-binding)

---
### `gcloud bigtable instances tables create`

Create a new Cloud Bigtable table

Create a new Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable instances tables create (TABLE : --instance=INSTANCE)
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

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance --column-families="my-family"

To create a table that has a column family named my-instance, a garbage
collection policy that lets data expire after 864,000 seconds, and initial
table splits on row keys car and key, run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance \
        --column-families="my-family:maxage=864000s" --splits=car,key

To create a table my-table in instance my-instance that lets data in column
family my-family1 expire after 10 days and keeps a maximum of 5 cells per
column in column family my-family-2 if the data is less than 5 days old,
run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance \
        --column-families="my-family-1:maxage=10d,my-family-2:maxversion\
    s=5||maxage=5d"

To create a table my-table that has one column family my-family that lets
data expire after 10 days, and to enable a change stream for the table to
be kept for 7 days, run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance \
        --column-families="my-family:maxage=10d" \
        --change-stream-retention-period=7d

To create a deletion-protected table my-table in instance my-instance with
a column family my-family, run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance --column-families="my-family" \
        --deletion-protection

To create a table my-table without deletion protection in instance
my-instance with a column family my-family, run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance --column-families="my-family" \
        --no-deletion-protection

To create a table my-table with the default automated backup policy
(retention_period=7d, frequency=1d) enabled in instance my-instance with a
column family my-family, run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance --column-families="my-family" \
        --enable-automated-backup

To create a table my-table with a custom automated backup policy configured
to retain backups for 30 days in instance my-instance with a column family
my-family, run:

    $ gcloud bigtable instances tables create my-table \
        --instance=my-instance --column-families="my-family" \
        --automated-backup-retention_period=30d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/create)

---
### `gcloud bigtable instances tables delete`

Delete a Cloud Bigtable table

Delete a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable instances tables delete (TABLE : --instance=INSTANCE)
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

    $ gcloud bigtable instances tables delete my-table \
        --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/delete)

---
### `gcloud bigtable instances tables describe`

Retrieve information about a table

Retrieve information about a table.

**Synopsis:**
```
gcloud bigtable instances tables describe (TABLE : --instance=INSTANCE)
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

    $ gcloud bigtable instances tables describe TABLE_NAME \
        --instance=INSTANCE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/describe)

---
### `gcloud bigtable instances tables get-iam-policy`

Get an IAM policy on a Cloud Bigtable table

Get an IAM policy on a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable instances tables get-iam-policy
    (TABLE : --instance=INSTANCE) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
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

    $ gcloud bigtable instances tables get-iam-policy my-table \
        --instance=`my-instance`

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/get-iam-policy)

---
### `gcloud bigtable instances tables list`

List existing Bigtable instance tables

**Synopsis:**
```
gcloud bigtable instances tables list --instances=[INSTANCE,...]
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

    $ gcloud bigtable instances tables list --instances=INSTANCE_NAME

To list all tables in several instances, run:        $ gcloud bigtable instances tables list \
        --instances=INSTANCE_NAME1,INSTANCE_NAME2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/list)

---
### `gcloud bigtable instances tables remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Bigtable table

Remove an IAM policy binding from a Cloud Bigtable table. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud bigtable instances tables remove-iam-policy-binding
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

    $ gcloud bigtable instances tables remove-iam-policy-binding \
        my-table --instance=`my-instance` \
        --member=`user:test-user@gmail.com` --role=`roles/editor`

To remove an IAM policy binding which expires at the end of the year 2019
for the role of roles/bigtable.admin and the user test-user@gmail.com with
table my-table in instance my-instance, run:

    $ gcloud bigtable instances tables remove-iam-policy-binding \
        my-table --instance=`my-instance` \
        --member=`user:test-user@gmail.com` \
        --role=`roles/bigtable.admin` \
        --condition=`expression=request.time < \
        timestamp("2020-01-01T00:00:00Z"),title=expires_end_of_2019,\
    description=Expires at midnight on 2019-12-31`

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/remove-iam-policy-binding)

---
### `gcloud bigtable instances tables restore`

Restore a Cloud Bigtable backup to a new table

This command restores a Cloud Bigtable backup to a new table.

**Synopsis:**
```
gcloud bigtable instances tables restore
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

    $ gcloud bigtable instances tables restore \
        --source-instance=instance1 --source-cluster=cluster1 \
        --source=backup1 --destination-instance=instance1 \
        --destination=table2

To restore table 'table2' from backup 'backup1' in a different project,
run:

    $ gcloud bigtable instances tables restore \
        --source=projects/project1/instances/instance1/clusters/\
    cluster1/backups/backup1 \
        --destination=projects/project2/instances/instance2/tables/\
    table2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/restore)

---
### `gcloud bigtable instances tables set-iam-policy`

Set an IAM policy on a Cloud Bigtable table

Set an IAM policy on a Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable instances tables set-iam-policy
    (TABLE : --instance=INSTANCE) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
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

    $ gcloud bigtable instances tables set-iam-policy my-table \
        --instance=`my-instance` my-policy

See https://cloud.google.com/iam/docs/managing-policies for more
information.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/set-iam-policy)

---
### `gcloud bigtable instances tables undelete`

Undelete a previously deleted Cloud Bigtable table

Undelete a previously deleted Cloud Bigtable table.

**Synopsis:**
```
gcloud bigtable instances tables undelete (TABLE : --instance=INSTANCE)
    [--async] [GCLOUD_WIDE_FLAG ...]
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

    $ gcloud bigtable instances tables undelete my-table \
        --instance=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/undelete)

---
### `gcloud bigtable instances tables update`

Update an existing Cloud Bigtable table

Update an existing new Cloud Bigtable table with the specified
configuration.

**Synopsis:**
```
gcloud bigtable instances tables update (TABLE : --instance=INSTANCE)
    [--async] [--deletion-protection] [--row-key-schema-pre-encoded-bytes]
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

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --deletion-protection

To disable deletion protection, run:

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --no-deletion-protection

To enable a change stream with a retention period of 1 day, or to update
your table's change stream retention period to 1 day, run:

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --change-stream-retention-period=1d

To disable a change stream, run:

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --clear-change-stream-retention-period

To enable the default automated backup policy on a table, or update a table
to use the default policy (retention_period=7d, frequency=1d), run:

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --enable-automated-backup

To disable automated backup: run:

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --disable-automated-backup

To enable or update a custom automated backup policy and configure it to
retain backups for 30 days, run:

    $ gcloud bigtable instances tables update my-table \
        --instance=my-instance --automated-backup-retention_period=30d
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/instances/tables/update)

---
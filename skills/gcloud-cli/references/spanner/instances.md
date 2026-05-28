# gcloud spanner instances

manage Cloud Spanner instances

### `gcloud spanner instances add-iam-policy-binding`

Add IAM policy binding to a Cloud Spanner instance

Add an IAM policy binding to a Cloud Spanner instance. One binding consists
of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud spanner instances add-iam-policy-binding [INSTANCE]
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Cloud Spanner instance to which to add the IAM
policy binding. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * set the property spanner/instance with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [INSTANCE]
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line;
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
'test-user@gmail.com' with instance 'my-instance', run:

    $ gcloud spanner instances add-iam-policy-binding my-instance \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/spanner.admin' and the user 'test-user@gmail.com' with
instance 'my-instance', run:

    $ gcloud spanner instances add-iam-policy-binding my-instance \
        --member='user:test-user@gmail.com' \
        --role='roles/spanner.admin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/add-iam-policy-binding)

---
### `gcloud spanner instances create`

Create a Cloud Spanner instance

Create a Cloud Spanner instance.

**Synopsis:**
```
gcloud spanner instances create INSTANCE --config=CONFIG
    --description=DESCRIPTION [--async]
    [--default-backup-schedule-type=DEFAULT_BACKUP_SCHEDULE_TYPE]
    [--edition=EDITION] [--expire-behavior=EXPIRE_BEHAVIOR]
    [--instance-type=INSTANCE_TYPE]
    [--nodes=NODES | --processing-units=PROCESSING_UNITS
      | [--autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET
      (--autoscaling-high-priority-cpu-target=AUTOSCALING_HIGH_PRIORITY_CPU_TARGET --autoscaling-total-cpu-target=AUTOSCALING_TOTAL_CPU_TARGET) (--autoscaling-max-nodes=AUTOSCALING_MAX_NODES --autoscaling-min-nodes=AUTOSCALING_MIN_NODES | --autoscaling-max-processing-units=AUTOSCALING_MAX_PROCESSING_UNITS --autoscaling-min-processing-units=AUTOSCALING_MIN_PROCESSING_UNITS) : --asymmetric-autoscaling-option=[disable_high_priority_cpu_autoscaling=DISABLE_HIGH_PRIORITY_CPU_AUTOSCALING],
      [disable_total_cpu_autoscaling=DISABLE_TOTAL_CPU_AUTOSCALING],
      [high_priority_cpu_target=HIGH_PRIORITY_CPU_TARGET],
      [location=LOCATION],[max_nodes=MAX_NODES],
      [max_processing_units=MAX_PROCESSING_UNITS],[min_nodes=MIN_NODES],
      [min_processing_units=MIN_PROCESSING_UNITS],
      [total_cpu_target=TOTAL_CPU_TARGET] --[no-]disable-downscaling]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud Spanner instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | Instance configuration defines the geographic placement and replication of the databases in that instance. Available configurations can be found by running "gcloud spanner instance-configs list" |
| `--description` | DESCRIPTION |  | Description of the instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--default-backup-schedule-type` | one of: AUTOMATIC A default backup schedule is created automatically when a new database is created in an instance |  | The default backup schedule type that is used in the instance. DEFAULT_BACKUP_SCHEDULE_TYPE must be one of: AUTOMATIC A default backup schedule is created automatically when a new database is created in an instance. You can edit or delete the default backup schedule once it's created. The default backup schedule creates a full backup every 24 hours. These full backups are retained for 7 days. DEFAULT_BACKUP_SCHEDULE_TYPE_UNSPECIFIED Not specified. NONE No default backup schedule is created automatically when a new database is created in an instance. |
| `--edition` | one of: EDITION_UNSPECIFIED Spanner's legacy pricing model |  | Spanner edition. EDITION must be one of: EDITION_UNSPECIFIED Spanner's legacy pricing model. For more information, see the Spanner editions overview (https://cloud.google.com/spanner/docs/editions-overview) ENTERPRISE Enterprise edition ENTERPRISE_PLUS Enterprise Plus edition STANDARD Standard edition |
| `--expire-behavior` | one of: free-to-provisioned When the free trial instance expires, upgrade the instance to a provisioned instance |  | The expire behavior of a free trial instance. EXPIRE_BEHAVIOR must be one of: free-to-provisioned When the free trial instance expires, upgrade the instance to a provisioned instance. remove-after-grace-period When the free trial instance expires, disable the instance, and delete it after the grace period passes if it has not been upgraded to a provisioned instance. |
| `--instance-type` | one of: free-instance Free trial instances provide no guarantees for dedicated resources, both node_count and processing_units should be 0 |  | Specifies the type for this instance. INSTANCE_TYPE must be one of: free-instance Free trial instances provide no guarantees for dedicated resources, both node_count and processing_units should be 0. They come with stricter usage limits and limited support. provisioned Provisioned instances have dedicated resources, standard usage limits, and support. |


**Examples:**
```bash
To create a Cloud Spanner instance, run:

    $ gcloud spanner instances create my-instance-id \
        --config=regional-us-east1 \
        --description=my-instance-display-name --nodes=3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/create)

---
### `gcloud spanner instances delete`

Delete a Cloud Spanner instance

Delete a Cloud Spanner instance.

**Synopsis:**
```
gcloud spanner instances delete INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud Spanner instance ID.
```

**Examples:**
```bash
To delete a Cloud Spanner instance, run:

    $ gcloud spanner instances delete my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/delete)

---
### `gcloud spanner instances describe`

Describe a Cloud Spanner instance

Describe a Cloud Spanner instance.

**Synopsis:**
```
gcloud spanner instances describe INSTANCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud Spanner instance ID.
```

**Examples:**
```bash
To describe a Cloud Spanner instance, run:

    $ gcloud spanner instances describe my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/describe)

---
### `gcloud spanner instances get-iam-policy`

Get the IAM policy for a Cloud Spanner instance

gcloud spanner instances get-iam-policy displays the IAM policy associated
with a Cloud Spanner instance. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy. The output includes an
"etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ {parent} set-iam-policy for additional
details.

**Synopsis:**
```
gcloud spanner instances get-iam-policy [INSTANCE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Cloud Spanner instance for which to display the
IAM policy. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * set the property spanner/instance with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [INSTANCE]
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line;
     + set the property spanner/instance.
```

**Examples:**
```bash
To print the IAM policy for a given Cloud Spanner instance, run:

    $ gcloud spanner instances get-iam-policy my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/get-iam-policy)

---
### `gcloud spanner instances get-locations`

Get the location of every replica in a Cloud Spanner instance

Get the location of every replica in a Cloud Spanner instance.

**Synopsis:**
```
gcloud spanner instances get-locations INSTANCE [--verbose]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud Spanner instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--verbose` |  |  | Indicates that both regions and types of replicas be returned. |


**Examples:**
```bash
To get the location of every replica in a Cloud Spanner instance in this
project, run:

    $ gcloud spanner instances get-locations my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/get-locations)

---
### `gcloud spanner instances list`

List the Cloud Spanner instances in this project

List the Cloud Spanner instances in this project.

**Synopsis:**
```
gcloud spanner instances list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Cloud Spanner instances in this project, run:

    $ gcloud spanner instances list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/list)

---
### `gcloud spanner instances move`

Move the Cloud Spanner instance to the specified instance configuration

Move the Cloud Spanner instance to the specified instance configuration.

**Synopsis:**
```
gcloud spanner instances move INSTANCE --target-config=TARGET_CONFIG
    [--target-database-move-configs=[^:^database-id=DATABASE_ID:kms-key-names=KEY1,
      KEY2,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud Spanner instance ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-config` | TARGET_CONFIG |  | Target Instance configuration to move the instances. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--target-database-move-configs` | [^:^database-id=DATABASE_ID:kms-key-names=KEY1,KEY2,...] |  | Database level configurations for each database to be moved. Currently only used for CMEK-enabled databases to specificy the target database KMS keys. Sets target_database_move_configs value. database-id Required, sets database-id value. kms-key-names Sets kms-key-names value. Shorthand Example: --target-database-move-configs=database-id=string,kms-key-names=string --target-database-move-configs=database-id=string,kms-key-names=string JSON Example: --target-database-move-configs='[{"database-id": "string", "kms-key-names": "string"}]' File Example: --target-database-move-configs=path_to_file.(yaml\|json) |


**Examples:**
```bash
To move the Cloud Spanner instance, which has two CMEK-enabled databases
db1 and db2 and a database db3 with Google-managed encryption keys, to the
target instance configuration nam3 (us-east4, us-east1, us-central1), run:        $ gcloud spanner instances move my-instance-id \
        --target-config=nam3 \
        --target-database-move-configs=^:^database-id=db1:kms-key-names=\
    projects/myproject/locations/us-east4/keyRings/mykeyring/\
    cryptoKeys/cmek-key,projects/myproject/locations/us-east1/keyRings/\
    mykeyring/cryptoKeys/cmek-key,projects/myproject/locations/\
    us-central1/keyRings/mykeyring/cryptoKeys/cmek-key \
        --target-database-move-configs=^:^database-id=db2:kms-key-names=\
    projects/myproject/locations/us-east4/keyRings/mykeyring/\
    cryptoKeys/cmek-key,projects/myproject/locations/us-east1/keyRings/\
    mykeyring/cryptoKeys/cmek-key,projects/myproject/locations/\
    us-central1/keyRings/mykeyring/cryptoKeys/cmek-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/move)

---
### `gcloud spanner instances remove-iam-policy-binding`

Remove IAM policy binding of a Cloud Spanner instance

Remove an IAM policy binding of a Cloud Spanner instance. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud spanner instances remove-iam-policy-binding [INSTANCE]
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Cloud Spanner instance to remove the IAM policy
binding from. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * set the property spanner/instance with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [INSTANCE]
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line;
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
'test-user@gmail.com' with instance 'my-instance', run:

    $ gcloud spanner instances remove-iam-policy-binding my-instance \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/spanner.admin' and the user 'test-user@gmail.com'
with instance 'my-instance', run:

    $ gcloud spanner instances remove-iam-policy-binding my-instance \
        --member='user:test-user@gmail.com' \
        --role='roles/spanner.admin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/remove-iam-policy-binding)

---
### `gcloud spanner instances set-iam-policy`

Set the IAM policy for a Cloud Spanner instance

Set the IAM policy for a Cloud Spanner instance given a instance ID and a
file encoded in JSON or YAML that contains the IAM policy.

**Synopsis:**
```
gcloud spanner instances set-iam-policy [INSTANCE] POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Instance resource - The Spanner instance to set the IAM policy for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument instance on the command line with a fully
   specified name;
 * set the property spanner/instance with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [INSTANCE]
     ID of the instance or fully qualified identifier for the instance.

     To set the instance attribute:
     + provide the argument instance on the command line;
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

    $ gcloud spanner instances set-iam-policy example-instance \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/set-iam-policy)

---
### `gcloud spanner instances update`

Update a Cloud Spanner instance

Update a Cloud Spanner instance.

**Synopsis:**
```
gcloud spanner instances update INSTANCE [--async]
    [--default-backup-schedule-type=DEFAULT_BACKUP_SCHEDULE_TYPE]
    [--description=DESCRIPTION] [--edition=EDITION]
    [--expire-behavior=EXPIRE_BEHAVIOR] [--instance-type=INSTANCE_TYPE]
    [--nodes=NODES | --processing-units=PROCESSING_UNITS
      | --autoscaling-storage-target=AUTOSCALING_STORAGE_TARGET
      --[no-]disable-downscaling
      --asymmetric-autoscaling-option=[disable_high_priority_cpu_autoscaling=DISABLE_HIGH_PRIORITY_CPU_AUTOSCALING],
      [disable_total_cpu_autoscaling=DISABLE_TOTAL_CPU_AUTOSCALING],
      [high_priority_cpu_target=HIGH_PRIORITY_CPU_TARGET],
      [location=LOCATION],[max_nodes=MAX_NODES],
      [max_processing_units=MAX_PROCESSING_UNITS],[min_nodes=MIN_NODES],
      [min_processing_units=MIN_PROCESSING_UNITS],
      [total_cpu_target=TOTAL_CPU_TARGET]
      | --clear-asymmetric-autoscaling-option=LOCATION,[LOCATION,...]
      --autoscaling-high-priority-cpu-target=AUTOSCALING_HIGH_PRIORITY_CPU_TARGET --autoscaling-total-cpu-target=AUTOSCALING_TOTAL_CPU_TARGET --autoscaling-max-nodes=AUTOSCALING_MAX_NODES --autoscaling-min-nodes=AUTOSCALING_MIN_NODES | --autoscaling-max-processing-units=AUTOSCALING_MAX_PROCESSING_UNITS --autoscaling-min-processing-units=AUTOSCALING_MIN_PROCESSING_UNITS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   Cloud Spanner instance ID.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--default-backup-schedule-type` | one of: AUTOMATIC A default backup schedule is created automatically when a new database is created in an instance |  | The default backup schedule type that is used in the instance. DEFAULT_BACKUP_SCHEDULE_TYPE must be one of: AUTOMATIC A default backup schedule is created automatically when a new database is created in an instance. You can edit or delete the default backup schedule once it's created. The default backup schedule creates a full backup every 24 hours. These full backups are retained for 7 days. DEFAULT_BACKUP_SCHEDULE_TYPE_UNSPECIFIED Not specified. NONE No default backup schedule is created automatically when a new database is created in an instance. |
| `--description` | DESCRIPTION |  | Description of the instance. |
| `--edition` | EDITION |  | Spanner edition. You can upgrade your Standard edition instance to the ENTERPRISE edition or ENTERPRISE_PLUS edition. You can also upgrade your Enterprise edition instance to the ENTERPRISE_PLUS edition. You can downgrade your ENTERPRISE_PLUS edition instance to the ENTERPRISE or STANDARD edition. You can also downgrade your ENTERPRISE edition instance to the STANDARD edition. You must stop using the higher-tier edition features in order to downgrade. Otherwise, downgrade fails. For more information, see Spanner editions overview (https://cloud.google.com/spanner/docs/editions-overview). |
| `--expire-behavior` | one of: free-to-provisioned When the free trial instance expires, upgrade the instance to a provisioned instance |  | The expire behavior of a free trial instance. EXPIRE_BEHAVIOR must be one of: free-to-provisioned When the free trial instance expires, upgrade the instance to a provisioned instance. remove-after-grace-period When the free trial instance expires, disable the instance, and delete it after the grace period passes if it has not been upgraded to a provisioned instance. |
| `--instance-type` | one of: free-instance Free trial instances provide no guarantees for dedicated resources, both node_count and processing_units should be 0 |  | Specifies the type for this instance. INSTANCE_TYPE must be one of: free-instance Free trial instances provide no guarantees for dedicated resources, both node_count and processing_units should be 0. They come with stricter usage limits and limited support. provisioned Provisioned instances have dedicated resources, standard usage limits, and support. |


**Examples:**
```bash
To update the display name of a Cloud Spanner instance, run:

    $ gcloud spanner instances update my-instance-id \
        --description=my-new-display-name

To update the node count of a Cloud Spanner instance, run:

    $ gcloud spanner instances update my-instance-id --nodes=1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instances/update)

---
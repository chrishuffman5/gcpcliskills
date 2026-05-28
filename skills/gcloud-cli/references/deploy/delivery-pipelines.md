# gcloud deploy delivery-pipelines

create and manage Delivery Pipeline resources for Cloud Deploy

### `gcloud deploy delivery-pipelines add-iam-policy-binding`

Add IAM policy binding for a Cloud Deploy delivery pipeline

Adds a policy binding to the IAM policy of a Cloud Deploy delivery
pipeline. One binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy delivery-pipelines add-iam-policy-binding
    [[DELIVERY_PIPELINE] --region=REGION] --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The delivery pipeline for which to add the
IAM policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery_pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the delivery_pipeline.

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
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
To add an IAM policy binding for the role of 'roles/clouddeploy.operator'
for the user 'test-user@gmail.com' on 'my-pipeline' with the region
'us-central1', run:

    $ gcloud deploy delivery-pipelines add-iam-policy-binding \
        my-pipeline --region='us-central1' \
        --member='user:test-user@gmail.com' \
        --role='roles/clouddeploy.operator'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/add-iam-policy-binding)

---
### `gcloud deploy delivery-pipelines delete`

Delete a delivery pipeline

Delete a delivery pipeline.

**Synopsis:**
```
gcloud deploy delivery-pipelines delete
    [[DELIVERY_PIPELINE] --region=REGION] [--async] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The Cloud Deploy delivery pipeline to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery_pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the delivery_pipeline.

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If true, the delivery pipeline with sub-resources will be deleted and its sub-resources will also be deleted. |


**Examples:**
```bash
The following command will delete delivery pipeline 'test-pipeline', in
region 'us-central1', but only if the delivery pipeline doesn't have any
sub-resources (targets, releases or rollouts):

    $ gcloud deploy delivery-pipelines delete test-pipeline \
        --region=us-central1

The following command will delete delivery pipeline 'test-pipeline', in
region 'us-central1' and its sub-resources (targets, releases or rollouts):

    $ gcloud deploy delivery-pipelines delete test-pipeline \
        --region=us-central1 --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/delete)

---
### `gcloud deploy delivery-pipelines describe`

Show details about a delivery pipeline

The output contains the following sections:

Delivery Pipeline:

  o detail of the delivery pipeline to be described.

Targets:

  o target name.

  o active release in the target.

  o timestamp of the last successful deployment.

  o list of the rollouts that require approval.

**Synopsis:**
```
gcloud deploy delivery-pipelines describe
    [[DELIVERY_PIPELINE] --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The name of the Delivery Pipeline. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the delivery_pipeline. Alternatively, set the
     property [deploy/region].

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To describe a delivery pipeline called 'test-pipeline' in region
'us-central1', run:

    $ gcloud deploy delivery-pipelines describe test-pipeline \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/describe)

---
### `gcloud deploy delivery-pipelines export`

Returns the .yaml definition of the specified delivery pipeline

The exported yaml definition can be applied by 'deploy apply' command.

**Synopsis:**
```
gcloud deploy delivery-pipelines export
    [[DELIVERY_PIPELINE] --region=REGION] [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The name of the Delivery Pipeline. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery-pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     The Cloud region for the delivery_pipeline. Alternatively, set the
     property [deploy/region].

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |


**Examples:**
```bash
To return the .yaml definition of the delivery pipeline 'test-pipeline', in
region 'us-central1', run:

    $ gcloud deploy delivery-pipelines export test-pipeline \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/export)

---
### `gcloud deploy delivery-pipelines get-iam-policy`

Get the IAM policy for a Cloud Deploy delivery pipeline

gcloud deploy delivery-pipelines get-iam-policy displays the IAM policy
associated with a Cloud Deploy delivery pipeline. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates; see $ gcloud deploy
delivery-pipelines set-iam-policy for additional details.

**Synopsis:**
```
gcloud deploy delivery-pipelines get-iam-policy
    [[DELIVERY_PIPELINE] --region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The delivery pipeline for which to display
the IAM policy. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery_pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the delivery_pipeline.

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To print the IAM policy for delivery pipeline my-pipeline, run:

    $ gcloud deploy delivery-pipelines get-iam-policy my-pipeline \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/get-iam-policy)

---
### `gcloud deploy delivery-pipelines list`

List Cloud Deploy delivery pipelines

List your Cloud Deploy delivery pipelines.

**Synopsis:**
```
gcloud deploy delivery-pipelines list [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the region attribute: + provide the argument --region on the command line; + set the property deploy/region. |


**Examples:**
```bash
To list the delivery pipelines in region 'us-central1', run:

    $ gcloud deploy delivery-pipelines list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/list)

---
### `gcloud deploy delivery-pipelines remove-iam-policy-binding`

Remove an IAM policy binding for a Cloud Deploy delivery pipeline

Removes a policy binding to the IAM policy of a Cloud Deploy delivery
pipeline. One binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy delivery-pipelines remove-iam-policy-binding
    [[DELIVERY_PIPELINE] --region=REGION] --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The delivery pipeline for which to remove the
IAM policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery_pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the delivery_pipeline.

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
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
To remove an IAM policy binding for the role of
'roles/clouddeploy.operator' for the user 'test-user@gmail.com' on
'my-pipeline' with the region 'us-central1', run:

    $ gcloud deploy delivery-pipelines remove-iam-policy-binding \
        my-pipeline --region='us-central1' \
        --member='user:test-user@gmail.com' \
        --role='roles/clouddeploy.operator'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/remove-iam-policy-binding)

---
### `gcloud deploy delivery-pipelines set-iam-policy`

Set the IAM policy for a Cloud Deploy delivery pipeline

Set the IAM policy associated with a Cloud Deploy delivery pipeline.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy delivery-pipelines set-iam-policy
    [[DELIVERY_PIPELINE] --region=REGION] POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Delivery pipeline resource - The delivery pipeline for which to set the
IAM policy.. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument delivery_pipeline on the command line with a
   fully specified name;
 * set the property deploy/delivery_pipeline with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [DELIVERY_PIPELINE]
     ID of the delivery_pipeline or fully qualified identifier for the
     delivery_pipeline.

     To set the delivery_pipeline attribute:
     + provide the argument delivery_pipeline on the command line;
     + set the property deploy/delivery_pipeline.

  --region=REGION
     Location of the delivery_pipeline.

     To set the region attribute:
     + provide the argument delivery_pipeline on the command line with a
       fully specified name;
     + set the property deploy/delivery_pipeline with a fully specified
       name;
     + provide the argument --region on the command line;
     + set the property deploy/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
policy.json and set it for a delivery pipeline with identifier my-pipeline

    $ gcloud deploy delivery-pipelines set-iam-policy my-pipeline \
        policy.json --region=us-central1

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/delivery-pipelines/set-iam-policy)

---
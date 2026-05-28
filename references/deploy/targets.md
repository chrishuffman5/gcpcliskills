# gcloud deploy targets

create and manage Target resources for Cloud Deploy

### `gcloud deploy targets add-iam-policy-binding`

Add IAM policy binding for a Cloud Deploy target

Adds a policy binding to the IAM policy of a Cloud Deploy target. One
binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy targets add-iam-policy-binding (TARGET : --region=REGION)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The target for which to add the IAM policy binding. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the target.

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
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
for the user 'test-user@gmail.com' on 'my-target' with the region
'us-central1', run:

    $ gcloud deploy targets add-iam-policy-binding my-target \
        --region='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/clouddeploy.operator'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/add-iam-policy-binding)

---
### `gcloud deploy targets delete`

Deletes a Cloud Deploy target

Deletes a Cloud Deploy target.

**Synopsis:**
```
gcloud deploy targets delete (TARGET : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The name of the Target. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the target. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To delete a target called 'test-target' in region 'us-central1', run:

    $ gcloud deploy targets delete test-target --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/delete)

---
### `gcloud deploy targets describe`

Describes details specific to the individual target, delivery pipeline qualified

The output contains four sections:

Target:

    detail of the target to be described.

Latest Release:

    the detail of the active release in the target.

Latest Rollout:

    the detail of the active rollout in the target.

Deployed:

    timestamp of the last successful deployment.

Pending Approvals:

    list of the rollouts that require approval.

**Synopsis:**
```
gcloud deploy targets describe (TARGET : --region=REGION)
    [--delivery-pipeline=DELIVERY_PIPELINE] [--list-all-pipelines]
    [--skip-pipeline-lookup] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The name of the Target. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the target. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | The name of the Cloud Deploy delivery pipeline |
| `--list-all-pipelines` |  |  | List all Delivery Pipelines associated with a target. Usage: $ gcloud deploy targets describe --list-all-pipelines |
| `--skip-pipeline-lookup` |  |  | If set, skip fetching details of associated pipelines when describing a target. Usage: $ gcloud deploy targets describe --skip-pipeline-lookup |


**Examples:**
```bash
To describe a target called 'test' for delivery pipeline 'test-pipeline' in
region 'us-central1', run:

    $ gcloud deploy targets describe test \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/describe)

---
### `gcloud deploy targets export`

Returns the .yaml definition of the specified target

The exported YAML definition can be applied by 'deploy apply' command.

**Synopsis:**
```
gcloud deploy targets export (TARGET : --region=REGION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The name of the Target. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the target. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |


**Examples:**
```bash
To return the .yaml definition of the target 'test-target' in region
'us-central1', run:

    $ gcloud deploy targets export test-target --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/export)

---
### `gcloud deploy targets get-iam-policy`

Get the IAM policy for a Cloud Deploy target

gcloud deploy targets get-iam-policy displays the IAM policy associated
with a Cloud Deploy target. If formatted as JSON, the output can be edited
and used as a policy file for set-iam-policy. The output includes an "etag"
field identifying the version emitted and allowing detection of concurrent
policy updates; see $ gcloud deploy targets set-iam-policy for additional
details.

**Synopsis:**
```
gcloud deploy targets get-iam-policy (TARGET : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The target for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the target.

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To print the IAM policy for a target my-target, run:

    $ gcloud deploy targets get-iam-policy my-target --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/get-iam-policy)

---
### `gcloud deploy targets list`

List Cloud Deploy targets

List Cloud Deploy targets.

**Synopsis:**
```
gcloud deploy targets list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the region attribute: + provide the argument --region on the command line; + set the property deploy/region. |


**Examples:**
```bash
To list the targets in region 'us-central1', run:

    $ gcloud deploy targets list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/list)

---
### `gcloud deploy targets redeploy`

Redeploy the last release to a target

Redeploy the last rollout that has a state of SUCCESSFUL or FAILED to a
target. If rollout-id is not specified, a rollout ID will be generated.

**Synopsis:**
```
gcloud deploy targets redeploy (TARGET : --region=REGION)
    --delivery-pipeline=DELIVERY_PIPELINE [--annotations=[KEY=VALUE,...]]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--override-deploy-policies=[POLICY,...]] [--rollout-id=ROLLOUT_ID]
    [--starting-phase-id=STARTING_PHASE_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The name of the Target. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the target. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | The name of the Cloud Deploy delivery pipeline |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations to apply to the rollout. Annotations take the form of key/value string pairs. Examples: Add annotations: $ gcloud deploy targets redeploy \ --annotations="from_target=test,status=stable" |
| `--description` | DESCRIPTION |  | Description of rollout created during a rollback. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the rollout. Labels take the form of key/value string pairs. Examples: Add labels: $ gcloud deploy targets redeploy --labels="commit=abc123,author=foo" |
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |
| `--rollout-id` | ROLLOUT_ID |  | ID to assign to the generated rollout for promotion. |
| `--starting-phase-id` | STARTING_PHASE_ID |  | If set, starts the created rollout at the specified phase. Start rollout at stable phase: $ gcloud deploy targets redeploy --starting-phase-id=stable |


**Examples:**
```bash
To redeploy a target prod for delivery pipeline test-pipeline in region
us-central1, run:

    $ gcloud deploy targets redeploy prod \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/redeploy)

---
### `gcloud deploy targets remove-iam-policy-binding`

Remove an IAM policy binding for a Cloud Deploy target

Removes a policy binding to the IAM policy of a Cloud Deploy target. One
binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy targets remove-iam-policy-binding (TARGET : --region=REGION)
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The target for which to remove the IAM policy binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the target.

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
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
'my-target' with the region 'us-central1', run:

    $ gcloud deploy targets remove-iam-policy-binding my-target \
        --region='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/clouddeploy.operator'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/remove-iam-policy-binding)

---
### `gcloud deploy targets rollback`

Rollbacks a target to a prior rollout

If release is not specified, the command rollbacks the target with the last
successful deployed release. If optional rollout-id parameter is not
specified, a generated rollout ID will be used.

**Synopsis:**
```
gcloud deploy targets rollback (TARGET : --region=REGION)
    --delivery-pipeline=DELIVERY_PIPELINE [--annotations=[KEY=VALUE,...]]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--override-deploy-policies=[POLICY,...]] [--release=RELEASE]
    [--rollout-id=ROLLOUT_ID] [--starting-phase-id=STARTING_PHASE_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The name of the Target. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the target. Alternatively, set the property
     [deploy/region].

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delivery-pipeline` | DELIVERY_PIPELINE |  | The name of the Cloud Deploy delivery pipeline |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations to apply to the rollback. Annotations take the form of key/value string pairs. Examples: Add annotations: $ gcloud deploy targets rollback \ --annotations="from_target=test,status=stable" |
| `--description` | DESCRIPTION |  | Description of rollout created during a rollback. |
| `--labels` | [KEY=VALUE,...] |  | Labels to apply to the rollback. Labels take the form of key/value string pairs. Examples: Add labels: $ gcloud deploy targets rollback --labels="commit=abc123,author=foo" |
| `--override-deploy-policies` | [POLICY,...] |  | Deploy policies to override |
| `--release` | RELEASE |  | Name of the release to rollback to. |
| `--rollout-id` | ROLLOUT_ID |  | ID to assign to the generated rollout for promotion. |
| `--starting-phase-id` | STARTING_PHASE_ID |  | If set, starts the created rollout at the specified phase. Start rollout at stable phase: $ gcloud deploy targets rollback --starting-phase-id=stable |


**Examples:**
```bash
To rollback a target 'prod' for delivery pipeline 'test-pipeline' in region
'us-central1', run:

    $ gcloud deploy targets rollback prod \
        --delivery-pipeline=test-pipeline --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/rollback)

---
### `gcloud deploy targets set-iam-policy`

Set the IAM policy for a Cloud Deploy target

Set the IAM policy associated with a Cloud Deploy target.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy targets set-iam-policy (TARGET : --region=REGION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Target resource - The target for which to set the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument target on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TARGET
     ID of the target or fully qualified identifier for the target.

     To set the target attribute:
     + provide the argument target on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the target.

     To set the region attribute:
     + provide the argument target on the command line with a fully
       specified name;
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
policy.json and set it for a target with identifier my-target

    $ gcloud deploy targets set-iam-policy my-target policy.json \
        --region=us-central1

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/targets/set-iam-policy)

---
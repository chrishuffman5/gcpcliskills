# gcloud deploy deploy-policies

create and manage Deploy Policy resources for Google Cloud Deploy

### `gcloud deploy deploy-policies add-iam-policy-binding`

Add IAM policy binding for a Cloud Deploy Policy

Adds a policy binding to the IAM policy of a Cloud Deploy Policy. One
binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy deploy-policies add-iam-policy-binding
    (DEPLOY_POLICY : --region=REGION) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The deploy policy for which to add the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the deploy policy.

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
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
To add an IAM policy binding for the role of roles/clouddeploy.policyAdmin
for the user test-user@gmail.com on holiday-policy with the region
us-central1, run:

    $ gcloud deploy deploy-policies add-iam-policy-binding \
        holiday-policy --region='us-central1' \
        --member='user:test-user@gmail.com' \
        --role='roles/clouddeploy.policyAdmin'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/add-iam-policy-binding)

---
### `gcloud deploy deploy-policies delete`

Delete a deploy policy

Delete a deploy policy for a specified region.

**Synopsis:**
```
gcloud deploy deploy-policies delete (DEPLOY_POLICY : --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The name of the deploy policy to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the deploy policy.

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command will delete deploy policy test-policy, in region
us-central1:

    $ gcloud deploy deploy-policies delete test-policy \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/delete)

---
### `gcloud deploy deploy-policies describe`

Show details about a deploy policy

Show details about a deploy policy.

**Synopsis:**
```
gcloud deploy deploy-policies describe (DEPLOY_POLICY : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The name of the Deploy Policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the deploy policy. Alternatively, set the
     property [deploy/region].

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To describe a deploy policy called 'test-policy' in region 'us-central1',
run:

    $ gcloud deploy deploy-policies describe test-policy \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/describe)

---
### `gcloud deploy deploy-policies export`

Returns the .yaml definition of the specified deploy policy

The exported yaml definition can be applied by deploy apply command.

**Synopsis:**
```
gcloud deploy deploy-policies export (DEPLOY_POLICY : --region=REGION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The name of the Deploy Policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the deploy policy. Alternatively, set the
     property [deploy/region].

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |


**Examples:**
```bash
To return the .yaml definition of the deploy policy test-policy, in region
us-central1, run:

    $ gcloud deploy deploy-policies export test-policy \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/export)

---
### `gcloud deploy deploy-policies get-iam-policy`

Get the IAM policy for a Cloud Deploy Policy

gcloud deploy deploy-policies get-iam-policy displays the IAM policy
associated with a Cloud Deploy Policy. If formatted as JSON, the output can
be edited and used as a policy file for set-iam-policy. The output includes
an "etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ gcloud deploy deploy-policies
set-iam-policy for additional details.

**Synopsis:**
```
gcloud deploy deploy-policies get-iam-policy
    (DEPLOY_POLICY : --region=REGION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The deploy policy for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the deploy policy.

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property deploy/region.
```

**Examples:**
```bash
To print the IAM policy for a deploy policy my-holiday-policy in region
us-central1, run:

    $ gcloud deploy deploy-policies get-iam-policy my-holiday-policy \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/get-iam-policy)

---
### `gcloud deploy deploy-policies remove-iam-policy-binding`

Remove an IAM policy binding for a Cloud Deploy Policy

Removes a policy binding to the IAM policy of a Cloud Deploy Policy. One
binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy deploy-policies remove-iam-policy-binding
    (DEPLOY_POLICY : --region=REGION) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The deploy policy for which to remove the IAM
policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the deploy policy.

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
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
roles/roles/clouddeploy.policyAdmin for the user test-user@gmail.com on
holiday-policy with the region us-central1, run:

    $ gcloud deploy deploy-policies remove-iam-policy-binding \
        holiday-policy --region='us-central1' \
        --member='user:test-user@gmail.com' \
        --role='roles/roles/clouddeploy.policyAdmin'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/remove-iam-policy-binding)

---
### `gcloud deploy deploy-policies set-iam-policy`

Set the IAM policy for a Cloud Deploy Policy

Set the IAM policy associated with a Cloud Deploy Policy.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud deploy deploy-policies set-iam-policy
    (DEPLOY_POLICY : --region=REGION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Deploy policy resource - The deploy policy for which to set the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument deploy_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DEPLOY_POLICY
     ID of the deploy policy or fully qualified identifier for the deploy
     policy.

     To set the deploy_policy attribute:
     + provide the argument deploy_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Location of the deploy policy.

     To set the region attribute:
     + provide the argument deploy_policy on the command line with a
       fully specified name;
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
policy.json and set it for a deploy policy with identifier
my-holiday-policy in region us-central1:

    $ gcloud deploy deploy-policies set-iam-policy my-holiday-policy \
        policy.json --region=us-central1

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/deploy/deploy-policies/set-iam-policy)

---
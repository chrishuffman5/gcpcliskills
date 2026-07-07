# gcloud iap tcp

manage IAP TCP resources


## `gcloud iap tcp dest-groups` — manage IAP TCP Destination Group resources
### `gcloud iap tcp dest-groups add-iam-policy-binding`

Add IAM policy binding to an IAP TCP Tunnel Destination Group resource

Adds a policy binding to the IAM policy of an IAP TCP Tunnel Destination
Group resource. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud iap tcp dest-groups add-iam-policy-binding --dest-group=DEST_GROUP
    --member=PRINCIPAL --region=REGION --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dest-group` | DEST_GROUP |  | Name of the Destination Group. |
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--region` | REGION |  | Region of the Destination Group. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of
'roles/iap.tunnelResourceAccessor' for the user 'test-user@gmail.com' in
the group 'my-group' located in the region 'us-west1', run:

    $ gcloud iap tcp dest-groups add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/iap.tunnelResourceAccessor' \
        --dest-group='my-group' --region='us-west1'

To add an IAM policy binding for the role of
'roles/iap.tunnelResourceAccessor' for all authenticated users in the group
'my-group' located in the region 'us-west1', run:

    $ gcloud iap tcp dest-groups add-iam-policy-binding \
        --member='allAuthenticatedUsers' \
        --role='roles/iap.tunnelResourceAccessor' \
        --dest-group='my-group' --region='us-west1'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/iap.tunnelResourceAccessor' and the user
'test-user@gmail.com' in the group 'my-group' located in the region
'us-west1', run:

    $ gcloud iap tcp dest-groups add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/iap.tunnelResourceAccessor' \
        --condition='expression=request.time <
        timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,
        description=Expires at midnight on 2018-12-31' --dest-group='my-group' --region='us-west1'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/add-iam-policy-binding)

---
### `gcloud iap tcp dest-groups create`

Create the IAP TCP Destination Group resource

Create the IAP TCP Destination Group resource.

**Synopsis:**
```
gcloud iap tcp dest-groups create GROUP_NAME --region=REGION
    [--fqdn-list=FQDN_LIST] [--ip-range-list=IP_RANGE_LIST]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GROUP_NAME
   Name of the Destination Group.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the Destination Group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fqdn-list` | FQDN_LIST |  | List of FQDNs in the Destination Group. |
| `--ip-range-list` | IP_RANGE_LIST |  | List of ip-ranges in the Destination Group. |


**Examples:**
```bash
To create a DestGroup with name GROUP_NAME, in region REGION in the current
project run:

    $ gcloud iap tcp dest-groups create GROUP_NAME --region=REGION

To create a DestGroup with name GROUP_NAME, in region REGION with ip ranges
CIDR1, CIDR2 in the current project run:

    $ gcloud iap tcp dest-groups create GROUP_NAME --region=REGION \
        --ip-range-list=CIDR1,CIDR2

To create a DestGroup with name GROUP_NAME, in region REGION with fqdns
FQDN1, FQDN2 in the current project run:

    $ gcloud iap tcp dest-groups create GROUP_NAME --region=REGION \
        --fqdn-list=FQDN1,FQDN2

To create a DestGroup with name GROUP_NAME, in region REGION with fqdns
FQDN1, FQDN2 and ip ranges CIDR1,CIDR2 in the project PROJECT_ID run:

    $ gcloud iap tcp dest-groups create GROUP_NAME --region=REGION \
        --fqdn-list=FQDN1,FQDN2 --ip-range-list=CIDR1,CIDR2 \
        --project=PROJECT_ID

GROUP_NAME can only contain lower-case letters (a-z) and dashes (-).
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/create)

---
### `gcloud iap tcp dest-groups delete`

Delete the IAP TCP Destination Group resource

Delete the IAP TCP Destination Group resource.

**Synopsis:**
```
gcloud iap tcp dest-groups delete GROUP_NAME --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GROUP_NAME
   Name of the Destination Group.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the Destination Group. |


**Examples:**
```bash
To delete a DestGroup with name GROUP_NAME, in region REGION in the current
project run:

    $ gcloud iap tcp dest-groups delete DEST_GROUP_NAME --region=REGION

To delete a DestGroup with name GROUP_NAME, in region REGION in the project
PROJECT_ID run:

    $ gcloud iap tcp dest-groups delete DEST_GROUP_NAME \
        --region=REGION --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/delete)

---
### `gcloud iap tcp dest-groups describe`

Describe the IAP TCP Destination Group resource

Describe the IAP TCP Destination Group resource.

**Synopsis:**
```
gcloud iap tcp dest-groups describe GROUP_NAME --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GROUP_NAME
   Name of the Destination Group.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the Destination Group. |


**Examples:**
```bash
To get a DestGroup with name GROUP_NAME, in region REGION in the current
project run:

    $ gcloud iap tcp dest-groups describe DEST_GROUP_NAME --region=REGION

To get a DestGroup with name GROUP_NAME, in region REGION in the project
PROJECT run:

    $ gcloud iap tcp dest-groups describe DEST_GROUP_NAME \
        --region=REGION --project=PROJECT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/describe)

---
### `gcloud iap tcp dest-groups get-iam-policy`

Get IAM policy for an IAP TCP Destination Group resource

gcloud iap tcp dest-groups get-iam-policy displays the IAM policy
associated with an IAP TCP Destination Group resource. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ gcloud
iap tcp dest-groups set-iam-policy for additional details.

**Synopsis:**
```
gcloud iap tcp dest-groups get-iam-policy --dest-group=DEST_GROUP
    --region=REGION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dest-group` | DEST_GROUP |  | Name of the Destination Group. |
| `--region` | REGION |  | Region of the Destination Group. |


**Examples:**
```bash
To get the IAM policy for the TCP Destination Group resource with name
'my-group' and located in the region 'us-west1' within the active project,
run:

    $ gcloud iap tcp dest-groups get-iam-policy \
        --dest-group='my-group' --region='us-west1'

To get the IAM policy for the TCP Destination Group resource with name
'my-group' and located in the region 'us-west1' within project 'project',
run:

    $ gcloud iap tcp dest-groups get-iam-policy \
        --dest-group='my-group' --region='us-west1' --project='project'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/get-iam-policy)

---
### `gcloud iap tcp dest-groups list`

Lists the IAP TCP Destination Group resource

Lists the IAP TCP Destination Group resource.

**Synopsis:**
```
gcloud iap tcp dest-groups list [--region=REGION; default="-"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION | - | Region of the Destination Group, will list all regions by default |


**Examples:**
```bash
To list all Destination Groups in the current project run:

    $ gcloud iap tcp dest-groups list

To list all Destination Groups in region REGION in the current project run:

    $ gcloud iap tcp dest-groups list --region=REGION

To limit the results returned by the server to be at most PAGE_SIZE, run:

    $ gcloud iap tcp dest-groups list --page-size=PAGE_SIZE

To list at most 5 Destination Groups sorted alphabetically by project ID,
run:

    $ gcloud iap tcp dest-groups list --sort-by=projectId --limit=5

To list all Destination Groups in the project PROJECT run:

    $ gcloud iap tcp dest-groups list --project=PROJECT

To list all Destination Groups that have cidr CIDR run:

    $ gcloud iap tcp dest-groups list --filter="cidrs=CIDR"

To list all Destination Groups that have FQDN FQDN run:

    $ gcloud iap tcp dest-groups list --filter="fqdns=FQDN"

To list all Destination Groups that have name NAME run:

    $ gcloud iap tcp dest-groups list --filter="name=NAME"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/list)

---
### `gcloud iap tcp dest-groups remove-iam-policy-binding`

Remove IAM policy binding from an IAP TCP Destination Group resource

Removes a policy binding from the IAM policy of an IAP TCP Destination
Group resource. One binding consists of a member, a role and an optional
condition.

**Synopsis:**
```
gcloud iap tcp dest-groups remove-iam-policy-binding
    --dest-group=DEST_GROUP --member=PRINCIPAL --region=REGION --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dest-group` | DEST_GROUP |  | Name of the Destination Group. |
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--region` | REGION |  | Region of the Destination Group. |
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
'roles/iap.tunnelResourceAccessor' for the user 'test-user@gmail.com' in
the group 'my-group' located in the region 'us-west1', run:

    $ gcloud iap tcp dest-groups remove-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/iap.tunnelResourceAccessor' \
        --dest-group='my-group' --region='us-west1'

To remove an IAM policy binding for the role of
'roles/iap.tunnelResourceAccessor' from all authenticated users in the
group 'my-group' located in the region 'us-west1', run:

    $ gcloud iap tcp dest-groups remove-iam-policy-binding \
        --member='allAuthenticatedUsers' \
        --role='roles/iap.tunnelResourceAccessor' \
        --dest-group='my-group' --region='us-west1'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/iap.tunnelResourceAccessor' for the user
'test-user@gmail.com' in the group 'my-group' located in the region
'us-west1', run:

    $ gcloud iap tcp dest-groups remove-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/iap.tunnelResourceAccessor' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,
     description=Expires at midnight on 2018-12-31' \
        --dest-group='my-group' --region='us-west1'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/iap.tunnelResourceAccessor' and for the user
'test-user@gmail.com' in the group 'my-group' located in the region
'us-west1', run:

    $ gcloud iap tcp dest-groups remove-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/iap.tunnelResourceAccessor' \
        --dest-group='my-group' --region='us-west1'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/remove-iam-policy-binding)

---
### `gcloud iap tcp dest-groups set-iam-policy`

Set the IAM policy for an IAP TCP Destination Group resource

This command replaces the existing IAM policy for an IAP TCP Destination
Group resource, given a file encoded in JSON or YAML that contains the IAM
policy. If the given policy file specifies an "etag" value, then the
replacement will succeed only if the policy already in place matches that
etag. (An etag obtained via $ gcloud iap tcp dest-groups get-iam-policy
will prevent the replacement if the policy for the resource has been
subsequently updated.) A policy file that does not contain an etag value
will replace any existing policy for the resource.

**Synopsis:**
```
gcloud iap tcp dest-groups set-iam-policy POLICY_FILE
    --dest-group=DEST_GROUP --region=REGION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   JSON or YAML file containing the IAM policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dest-group` | DEST_GROUP |  | Name of the Destination Group. |
| `--region` | REGION |  | Region of the Destination Group. |


**Examples:**
```bash
To set the IAM policy for the TCP Destination Group resource within the
active project in the group 'my-group' located in the region 'us-west1',
run:

    $ gcloud iap tcp dest-groups set-iam-policy POLICY_FILE \
        --dest-group=='my-group' --region='us-west1'

To set the IAM policy for the TCP Destination Group resource within project
PROJECT_ID in the group 'my-group' located in the region 'us-west1', run:

    $ gcloud iap tcp dest-groups set-iam-policy POLICY_FILE \
        --project=PROJECT_ID --dest-group=='my-group' \
        --region='us-west1'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/set-iam-policy)

---
### `gcloud iap tcp dest-groups update`

Update the IAP TCP Destination Group resource

Update the IAP TCP Destination Group resource.

**Synopsis:**
```
gcloud iap tcp dest-groups update GROUP_NAME --region=REGION
    (--fqdn-list=FQDN_LIST --ip-range-list=IP_RANGE_LIST)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GROUP_NAME
   Name of the Destination Group.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the Destination Group. |


**Examples:**
```bash
To update a DestGroup with name GROUP_NAME, in region REGION with ip ranges
CIDR1, CIDR2 in the current project run:

    $ gcloud iap tcp dest-groups update DEST_GROUP_NAME \
        --region=REGION --ip-range-list=CIDR1,CIDR2

To update a DestGroup with name GROUP_NAME, in region REGION with fqdns
FQDN1, FQDN2 in the current project run:

    $ gcloud iap tcp dest-groups update DEST_GROUP_NAME \
        --region=REGION --fqdn-list=FQDN1,FQDN2

To update a DestGroup with name GROUP_NAME, in region REGION with fqdns
FQDN1, FQDN2 and ip ranges CIDR1, CIDR2 in the project PROJECT_ID run:

    $ gcloud iap tcp dest-groups update DEST_GROUP_NAME \
        --region=REGION --fqdn-list=FQDN1,FQDN2 \
        --ip-range-list=CIDR1,CIDR2 --project=PROJECT_ID

To clear the fqdn list in a DestGroup with name GROUP_NAME, in region
REGION in the current project run:

    $ gcloud iap tcp dest-groups update DEST_GROUP_NAME \
        --region=REGION --fqdn-list=""

To clear the ip range list in a DestGroup with name GROUP_NAME, in region
REGION in the current project run:

    $ gcloud iap tcp dest-groups update DEST_GROUP_NAME \
        --region=REGION --ip-range-list=""
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/tcp/dest-groups/update)

---
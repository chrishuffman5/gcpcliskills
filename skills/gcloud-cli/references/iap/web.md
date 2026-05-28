# gcloud iap web

manage IAP web policies

### `gcloud iap web add-iam-policy-binding`

Add IAM policy binding to an IAP IAM resource

Adds a policy binding to the IAM policy of an IAP IAM resource. One binding
consists of a member, a role, and an optional condition. See $ gcloud iap
web get-iam-policy for examples of how to specify an IAP IAM resource.

**Synopsis:**
```
gcloud iap web add-iam-policy-binding --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [--region=REGION
      --resource-type=RESOURCE_TYPE --service=SERVICE --version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
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
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region name. Should only be specified with |
| `--resource-type` | backend-services if it is a regional scoped. Not |  | _[At most one of these can be specified:]_ applicable for global scoped backend services. |
| `--resource-type` | one of: app-engine, backend-services, forwarding-rule |  | _[At most one of these can be specified:]_ Resource type of the IAP resource. RESOURCE_TYPE must be one of: app-engine, backend-services, forwarding-rule. |
| `--service` | SERVICE |  | _[At most one of these can be specified:]_ Service name. |
| `--version` | VERSION |  | _[At most one of these can be specified:]_ Service version. Should only be specified with |
| `--resource-type` | app-engine. |  | _[At most one of these can be specified:]_ |


**Examples:**
```bash
See $ gcloud iap web get-iam-policy for examples of how to specify an IAP
IAM resource.

To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on IAP IAM resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web add-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on regional IAP IAM resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web add-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/editor' \
        --region=REGION

To add an IAM policy binding for the role of 'roles/editor' for all
authenticated users on IAP IAM resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web add-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='allAuthenticatedUsers' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/browser' and the user 'test-user@gmail.com' on IAP IAM
resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web add-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/browser' \
        --condition='expression=request.time <
        timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,
        description=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/web/add-iam-policy-binding)

---
### `gcloud iap web disable`

Disable Cloud Identity-Aware Proxy (Cloud IAP) on an IAP resource

This command disables Cloud Identity-Aware Proxy on an IAP resource.
Disabling IAP does not clear the OAuth 2.0 credentials.

**Synopsis:**
```
gcloud iap web disable
    [--resource-type=RESOURCE_TYPE : --region=REGION --service=SERVICE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-type` | one of: app-engine, backend-services |  | Resource type of the IAP resource. RESOURCE_TYPE must be one of: app-engine, backend-services. |
| `--region` | REGION |  | Region name. Not applicable for app-engine. Optional when resource-type is compute. |
| `--service` | SERVICE |  | Service name. Required with --resource-type=backend-services. |


**Examples:**
```bash
To disable IAP on an App Engine application, run:

    $ gcloud iap web disable --resource-type=app-engine

To disable IAP on a global backend service, run:

    $ gcloud iap web disable --resource-type=backend-services \
        --service=SERVICE_ID

To disable IAP on a region backend service, run:

    $ gcloud iap web disable --resource-type=backend-services \
        --service=SERVICE_ID --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/web/disable)

---
### `gcloud iap web enable`

Enable Cloud Identity-Aware Proxy (Cloud IAP) on an IAP resource

This command enables Cloud Identity-Aware Proxy on an IAP resource. OAuth
2.0 credentials must be set, or must have been previously set, to enable
IAP.

**Synopsis:**
```
gcloud iap web enable
    [--oauth2-client-id=OAUTH2_CLIENT_ID
      --oauth2-client-secret=OAUTH2_CLIENT_SECRET]
    [--resource-type=RESOURCE_TYPE : --region=REGION --service=SERVICE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--oauth2-client-id` | OAUTH2_CLIENT_ID |  | OAuth 2.0 client ID to use. |
| `--oauth2-client-secret` | OAUTH2_CLIENT_SECRET |  | OAuth 2.0 client secret to use. |
| `--resource-type` | one of: app-engine, backend-services |  | Resource type of the IAP resource. RESOURCE_TYPE must be one of: app-engine, backend-services. |
| `--region` | REGION |  | Region name. Not applicable for app-engine. Optional when resource-type is compute. |
| `--service` | SERVICE |  | Service name. Required with --resource-type=backend-services. |


**Examples:**
```bash
To enable IAP on an App Engine application, run:

    $ gcloud iap web enable --resource-type=app-engine \
        --oauth2-client-id=CLIENT_ID --oauth2-client-secret=SECRET

To enable IAP on a global backend service, run:

    $ gcloud iap web enable --resource-type=backend-services \
        --oauth2-client-id=CLIENT_ID --oauth2-client-secret=SECRET \
        --service=SERVICE_ID

To enable IAP on a region backend service, run:

    $ gcloud iap web enable --resource-type=backend-services \
        --oauth2-client-id=CLIENT_ID --oauth2-client-secret=SECRET \
        --service=SERVICE_ID --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/web/enable)

---
### `gcloud iap web get-iam-policy`

Get IAM policy for an IAP IAM resource

gcloud iap web get-iam-policy displays the IAM policy associated with an
IAP IAM resource. If formatted as JSON, the output can be edited and used
as a policy file for set-iam-policy. The output includes an "etag" field
identifying the version emitted and allowing detection of concurrent policy
updates; see $ gcloud iap web set-iam-policy for additional details.

**Synopsis:**
```
gcloud iap web get-iam-policy
    [--region=REGION
      --resource-type=RESOURCE_TYPE --service=SERVICE --version=VERSION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region name. Should only be specified with --resource-type=backend-services if it is a regional scoped. Not applicable for global scoped backend services. |
| `--resource-type` | one of: app-engine, backend-services, forwarding-rule |  | Resource type of the IAP resource. RESOURCE_TYPE must be one of: app-engine, backend-services, forwarding-rule. |
| `--service` | SERVICE |  | Service name. |
| `--version` | VERSION |  | Service version. Should only be specified with --resource-type=app-engine. |


**Examples:**
```bash
To get the IAM policy for the web accesses to the IAP protected resources
within the active project, run:

    $ gcloud iap web get-iam-policy

To get the IAM policy for the web accesses to the IAP protected resources
within a project, run:

    $ gcloud iap web get-iam-policy --project=PROJECT_ID

To get the IAM policy for the web accesses to the IAP protected resources
within an App Engine application, run:

    $ gcloud iap web get-iam-policy --resource-type=app-engine

To get the IAM policy for the web accesses to the IAP protected resources
within an App Engine service, run:

    $ gcloud iap web get-iam-policy --resource-type=app-engine \
        --service=SERVICE_ID

To get the IAM policy for the web accesses to the IAP protected resources
within an App Engine service version, run:

    $ gcloud iap web get-iam-policy --resource-type=app-engine \
        --service=SERVICE_ID --version=VERSION

To get the IAM policy for the web accesses to the IAP protected resources
within all backend services, run:

    $ gcloud iap web get-iam-policy --resource-type=backend-services

To get the IAM policy for the web accesses to the IAP protected resources
within a backend service, run:

    $ gcloud iap web get-iam-policy --resource-type=backend-services \
        --service=SERVICE_ID

To get the IAM policy for the web accesses to the IAP protected resources
within a regional backend service, run:

    $ gcloud iap web get-iam-policy --resource-type=backend-services \
        --service=SERVICE_ID --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/web/get-iam-policy)

---
### `gcloud iap web remove-iam-policy-binding`

Remove IAM policy binding from an IAP IAM resource

Removes a policy binding from the IAM policy of an IAP IAM resource. One
binding consists of a member, a role and an optional condition. See $
gcloud iap web get-iam-policy for examples of how to specify an IAP IAM
resource.

**Synopsis:**
```
gcloud iap web remove-iam-policy-binding --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE]
    [--region=REGION
      --resource-type=RESOURCE_TYPE --service=SERVICE --version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
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
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region name. Should only be specified with |
| `--resource-type` | backend-services if it is a regional scoped. Not |  | _[At most one of these can be specified:]_ applicable for global scoped backend services. |
| `--resource-type` | one of: app-engine, backend-services, forwarding-rule |  | _[At most one of these can be specified:]_ Resource type of the IAP resource. RESOURCE_TYPE must be one of: app-engine, backend-services, forwarding-rule. |
| `--service` | SERVICE |  | _[At most one of these can be specified:]_ Service name. |
| `--version` | VERSION |  | _[At most one of these can be specified:]_ Service version. Should only be specified with |
| `--resource-type` | app-engine. |  | _[At most one of these can be specified:]_ |


**Examples:**
```bash
See $ gcloud iap web get-iam-policy for examples of how to specify an IAP
IAM resource.

To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on IAP IAM resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web remove-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on regional IAP IAM resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web remove-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/editor' \
        --region=REGION

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on IAP IAM resource IAP_IAM_RESOURCE,run:

    $ gcloud iap web remove-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='allAuthenticatedUsers' --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2019-01-01T00:00:00Z")',
title='expires_end_of_2018', and description='Expires at midnight on
2018-12-31' for the role of 'roles/browser' for the user
'test-user@gmail.com' on IAP IAM resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web remove-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/browser' \
        --condition='expression=request.time <
        timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,
        description=Expires at midnight on 2018-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/browser' and for the user 'test-user@gmail.com' on IAP IAM
resource IAP_IAM_RESOURCE, run:

    $ gcloud iap web remove-iam-policy-binding \
        --resource-type=IAP_IAM_RESOURCE \
        --member='user:test-user@gmail.com' --role='roles/browser' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/web/remove-iam-policy-binding)

---
### `gcloud iap web set-iam-policy`

Set the IAM policy for an IAP IAM resource

This command replaces the existing IAM policy for an IAP IAM resource,
given a file encoded in JSON or YAML that contains the IAM policy. If the
given policy file specifies an "etag" value, then the replacement will
succeed only if the policy already in place matches that etag. (An etag
obtained via $ gcloud iap web get-iam-policy will prevent the replacement
if the policy for the resource has been subsequently updated.) A policy
file that does not contain an etag value will replace any existing policy
for the resource.

**Synopsis:**
```
gcloud iap web set-iam-policy POLICY_FILE
    [--region=REGION
      --resource-type=RESOURCE_TYPE --service=SERVICE --version=VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   JSON or YAML file containing the IAM policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region name. Should only be specified with --resource-type=backend-services if it is a regional scoped. Not applicable for global scoped backend services. |
| `--resource-type` | one of: app-engine, backend-services, forwarding-rule |  | Resource type of the IAP resource. RESOURCE_TYPE must be one of: app-engine, backend-services, forwarding-rule. |
| `--service` | SERVICE |  | Service name. |
| `--version` | VERSION |  | Service version. Should only be specified with --resource-type=app-engine. |


**Examples:**
```bash
To set the IAM policy for the web accesses to the IAP protected resources
within the active project, run:

    $ gcloud iap web set-iam-policy POLICY_FILE

To set the IAM policy for the web accesses to the IAP protected resources
within a project, run:

    $ gcloud iap web set-iam-policy POLICY_FILE --project=PROJECT_ID

To set the IAM policy for the web accesses to the IAP protected resources
within an App Engine application, run:

    $ gcloud iap web set-iam-policy POLICY_FILE \
        --resource-type=app-engine

To set the IAM policy for the web accesses to the IAP protected resources
within an App Engine service, run:

    $ gcloud iap web set-iam-policy POLICY_FILE \
        --resource-type=app-engine --service=SERVICE_ID

To set the IAM policy for the web accesses to the IAP protected resources
within an App Engine service version, run:

    $ gcloud iap web set-iam-policy POLICY_FILE \
        --resource-type=app-engine --service=SERVICE_ID \
        --version=VERSION

To set the IAM policy for the web accesses to the IAP protected resources
within all backend services, run:

    $ gcloud iap web set-iam-policy POLICY_FILE \
        --resource-type=backend-services

To set the IAM policy for the web accesses to the IAP protected resources
within a backend service, run:

    $ gcloud iap web set-iam-policy POLICY_FILE \
        --resource-type=backend-services --service=SERVICE_ID

To set the IAM policy for the web accesses to the IAP protected resources
within a regional backend service, run:

    $ gcloud iap web set-iam-policy POLICY_FILE \
        --resource-type=backend-services --service=SERVICE_ID \
        --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/web/set-iam-policy)

---
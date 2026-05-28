# gcloud kms ekm-connections

create and manage ekm connections

### `gcloud kms ekm-connections add-iam-policy-binding`

Add IAM policy binding for a kms ekm connection

Adds a policy binding to the IAM policy of a kms ekm connection. A binding
consists of at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud kms ekm-connections add-iam-policy-binding
    (EKM_CONNECTION : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekm connection resource - The ekm connection to add the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekm connection or fully qualified identifier for the ekm
     connection.

     To set the ekm_connection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
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
'test-user@gmail.com' on the ekm connection laplace with location global,
run:

    $ gcloud kms ekm-connections add-iam-policy-binding laplace \
        --location='global' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2022 for
the role of 'roles/editor' and the user 'test-user@gmail.com' on the
laplace fellowship and location global, run:

    $ gcloud kms ekm-connections add-iam-policy-binding laplace \
        --location='global' --member='user:test-user@gmail.com' \
        --role='roles/editor' \
        --condition='expression=request.time <
     timestamp("2023-01-01T00:00:00Z"),title=expires_end_of_2022,descrip\
    tion=Expires at midnight on 2022-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/add-iam-policy-binding)

---
### `gcloud kms ekm-connections create`

Create a new ekm connection

Creates a new connection within the given location.

**Synopsis:**
```
gcloud kms ekm-connections create (EKM_CONNECTION : --location=LOCATION)
    --hostname=HOSTNAME
    --server-certificates-files=[SERVER_CERTIFICATES,...]
    --service-directory-service=SERVICE_DIRECTORY_SERVICE
    [--endpoint-filter=ENDPOINT_FILTER]
    [--crypto-space-path=CRYPTO_SPACE_PATH
      --key-management-mode=KEY_MANAGEMENT_MODE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekmconnection resource - The KMS ekm connection resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekmconnection or fully qualified identifier for the
     ekmconnection.

     To set the ekmconnection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the ekmconnection.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hostname` | HOSTNAME |  | The hostname of the EKM replica used at TLS and HTTP layers. |
| `--server-certificates-files` | [SERVER_CERTIFICATES,...] |  | A list of filenames of leaf server certificates used to authenticate HTTPS connections to the EKM replica in PEM format. If files are not in PEM, the assumed format will be DER. |
| `--service-directory-service` | SERVICE_DIRECTORY_SERVICE |  | The resource name of the Service Directory service pointing to an EKM replica. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--endpoint-filter` | ENDPOINT_FILTER |  | The filter applied to the endpoints of the resolved service. If no filter is specified, all endpoints will be considered. |


**Examples:**
```bash
The following command creates an ekm connection named laplace within the
location us-central1:

    $ gcloud kms ekm-connections create laplace --location=us-central1 \
        --service-directory-service="foo" \
        --endpoint-filter="foo > bar" --hostname="hostname.foo" \
        --server-certificates-files=foo.pem,bar.pem

The following command creates an ekm connection named laplace within the
location us-central1 in cloud-kms key management mode with the required
crypto-space-path :

    $ gcloud kms ekm-connections create laplace --location=us-central1 \
        --service-directory-service="foo" \
        --endpoint-filter="foo > bar" --hostname="hostname.foo" \
        --key-management-mode=cloud-kms --crypto-space-path="foo" \
        --server-certificates-files=foo.pem,bar.pem
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/create)

---
### `gcloud kms ekm-connections describe`

Get metadata for an ekmconnection

Returns metadata for the given ekmconnection.

**Synopsis:**
```
gcloud kms ekm-connections describe (EKM_CONNECTION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekmconnection resource - The KMS ekm connection resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekmconnection or fully qualified identifier for the
     ekmconnection.

     To set the ekmconnection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the ekmconnection.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command returns the metadata for the ekmconnection laplace in
the location us-east1:

    $ gcloud kms ekm-connections describe laplace --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/describe)

---
### `gcloud kms ekm-connections get-iam-policy`

Get the IAM policy for an ekm connection

Displays the IAM policy associated with an ekm connection. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ gcloud
kms ekm-connections set-iam-policy for additional details.

**Synopsis:**
```
gcloud kms ekm-connections get-iam-policy
    (EKM_CONNECTION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekm connection resource - The ekm connection for which to get the IAM
policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekm connection or fully qualified identifier for the ekm
     connection.

     To set the ekm_connection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given ekm connection, run:

    $ gcloud kms ekm-connections get-iam-policy --location=my-location \
        my-ekmconnection
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/get-iam-policy)

---
### `gcloud kms ekm-connections list`

List ekmconnections within a location

Lists all ekmconnections within the given location.

**Synopsis:**
```
gcloud kms ekm-connections list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
The following command lists a maximum of five ekmconnections in the
location global:

    $ gcloud kms ekm-connections list --location=global --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/list)

---
### `gcloud kms ekm-connections remove-iam-policy-binding`

Remove IAM policy binding for a kms ekm connection

Removes a policy binding from the IAM policy of a kms ekm connection. A
binding consists of at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud kms ekm-connections remove-iam-policy-binding
    (EKM_CONNECTION : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekm connection resource - The ekm connection to remove the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekm connection or fully qualified identifier for the ekm
     connection.

     To set the ekm_connection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
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
'test-user@gmail.com' on the ekm connection laplace with location global,
run:

    $ gcloud kms ekm-connections remove-iam-policy-binding laplace \
        --location='global' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2023-01-01T00:00:00Z")',
title='expires_end_of_2022', and description='Expires at midnight on
2022-12-31' for the role of 'roles/editor' for the user
'test-user@gmail.com' on the ekm connection laplace with location global,
run:

    $ gcloud kms ekm-connections remove-iam-policy-binding laplace \
        --location='global' --member='user:test-user@gmail.com' \
        --role='roles/editor' \
        --condition='expression=request.time <
     timestamp("2023-01-01T00:00:00Z"),title=expires_end_of_2022,descrip\
    tion=Expires at midnight on 2022-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/editor' and for the user 'test-user@gmail.com' on the ekm
connection laplace with location global, run:

    $ gcloud kms ekm-connections remove-iam-policy-binding laplace \
        --location='global' --member='user:test-user@gmail.com' \
        --role='roles/editor' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/remove-iam-policy-binding)

---
### `gcloud kms ekm-connections set-iam-policy`

Set the IAM policy binding for a KMS ekm connection

Sets the IAM policy for the given ekm connection as defined in a JSON or
YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud kms ekm-connections set-iam-policy
    (EKM_CONNECTION : --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekm connection resource - The ekm connection for which to set the IAM
policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekm connection or fully qualified identifier for the ekm
     connection.

     To set the ekm_connection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the ekm connection 'laplace' with the location
'global':

    $ gcloud kms ekm-connections set-iam-policy laplace policy.json \
        --location=global

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/set-iam-policy)

---
### `gcloud kms ekm-connections update`

Update an ekmconnection

gcloud kms ekm-connections update can be used to update the ekmconnection.
Updates can be made to the ekmconnection's service resolver's fields.

**Synopsis:**
```
gcloud kms ekm-connections update (EKM_CONNECTION : --location=LOCATION)
    [--endpoint-filter=ENDPOINT_FILTER] [--hostname=HOSTNAME]
    [--server-certificates-files=[SERVER_CERTIFICATES,...]]
    [--service-directory-service=SERVICE_DIRECTORY_SERVICE]
    [--crypto-space-path=CRYPTO_SPACE_PATH
      --key-management-mode=KEY_MANAGEMENT_MODE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Ekmconnection resource - The KMS ekm connection resource. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument ekm_connection on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  EKM_CONNECTION
     ID of the ekmconnection or fully qualified identifier for the
     ekmconnection.

     To set the ekmconnection attribute:
     + provide the argument ekm_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the ekmconnection.

     To set the location attribute:
     + provide the argument ekm_connection on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--endpoint-filter` | ENDPOINT_FILTER |  | The filter applied to the endpoints of the resolved service. If no filter is specified, all endpoints will be considered. |
| `--hostname` | HOSTNAME |  | The hostname of the EKM replica used at TLS and HTTP layers. |
| `--server-certificates-files` | [SERVER_CERTIFICATES,...] |  | A list of filenames of leaf server certificates used to authenticate HTTPS connections to the EKM replica in PEM format. If files are not in PEM, the assumed format will be DER. |
| `--service-directory-service` | SERVICE_DIRECTORY_SERVICE |  | The resource name of the Service Directory service pointing to an EKM replica. |


**Examples:**
```bash
The following command updates an ekm-connection named laplace service
resolver's hostname within location us-east1:

    $ gcloud kms ekm-connections update laplace --location=us-east1 \
        --hostname=newhostname.foo

The following command updates an ekm-connection named laplace service
resolver's service_directory_service, endpoint_filter, hostname, and
server_certificates within location us-east1:

    $ gcloud kms ekm-connections update laplace --location=us-east1 \
        --service-directory-service="foo" \
        --endpoint-filter="foo > bar" --hostname="newhostname.foo" \
        --server-certificates-files=foo.pem,bar.pem

The following command updates an ekm-connection named laplace
key_management_mode within location us-east1:

    $ gcloud kms ekm-connections update laplace --location=us-east1 \
        --key-management-mode=manual
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/ekm-connections/update)

---
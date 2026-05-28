# gcloud privateca pools

manage CA pools

### `gcloud privateca pools add-iam-policy-binding`

Add IAM policy binding for a CA pool

Adds a policy binding to the IAM policy of a CA pool. One binding consists
of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud privateca pools add-iam-policy-binding (POOL : --location=LOCATION)
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA Pool resource - The CA pool for which to add the IAM policy binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument pool on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POOL
     ID of the CA Pool or fully qualified identifier for the CA Pool.

     To set the pool attribute:
     + provide the argument pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA Pool.

     To set the location attribute:
     + provide the argument pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
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
To add an IAM policy binding for the role of
'roles/privateca.certificateManager' for the user 'test-user@gmail.com' on
the CA pool 'my-pool' with the location 'us-west1', run:

    $ gcloud privateca pools add-iam-policy-binding my-pool \
        --location='us-west1' --member='user:test-user@gmail.com' \
        --role='roles/privateca.certificateManager'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/add-iam-policy-binding)

---
### `gcloud privateca pools create`

Create a new CA Pool

**Synopsis:**
```
gcloud privateca pools create (CA_POOL : --location=LOCATION)
    [--encryption-key=ENCRYPTION_KEY] [--issuance-policy=ISSUANCE_POLICY]
    [--labels=[KEY=VALUE,...]] [--no-publish-ca-cert] [--no-publish-crl]
    [--publishing-encoding-format=PUBLISHING_ENCODING_FORMAT;
      default="pem"] [--tier=TIER; default="enterprise"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA POOL resource - The ca pool to create. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument CA_POOL on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CA_POOL
     ID of the CA_POOL or fully qualified identifier for the CA_POOL.

     To set the pool attribute:
     + provide the argument CA_POOL on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA_POOL.

     To set the location attribute:
     + provide the argument CA_POOL on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--encryption-key` | ENCRYPTION_KEY |  | The full resource name of the Cloud KMS key to use for encrypting certificate data at rest. The key must be in the same region as the CA pool. |
| `--issuance-policy` | ISSUANCE_POLICY |  | A YAML file describing this CA Pool's issuance policy. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--publish-ca-cert` |  |  | If this is enabled, the following will happen: 1) The CA certificates will be written to a known location within the CA distribution point. 2) The AIA extension in all issued certificates will point to the CA cert URL in that distribition point. Note that the same bucket may be used for the CRLs if --publish-crl is set. Enabled by default, use --no-publish-ca-cert to disable. |
| `--publish-crl` |  |  | If this gets enabled, the following will happen: 1) CRLs will be written to a known location within the CA distribution point. 2) The CDP extension in all future issued certificates will point to the CRL URL in that distribution point. Note that the same bucket may be used for the CA cert if --publish-ca-cert is set. CRL publication is not supported for CAs in the DevOps tier. Enabled by default, use --no-publish-crl to disable. |
| `--publishing-encoding-format` | one of: der, pem | pem | The encoding format of the content published to storage buckets. PUBLISHING_ENCODING_FORMAT must be one of: der, pem. |
| `--tier` | one of: devops, enterprise | enterprise | The tier for the Certificate Authority. TIER must be one of: devops, enterprise. |


**Examples:**
```bash
To create a CA pool in the dev ops tier:

    $ gcloud privateca pools create my-pool --location=us-west1 \
      --tier=devops

To create a CA pool and restrict what it can issue:

    $ gcloud privateca pools create my-pool --location=us-west1 \
      --issuance-policy=policy.yaml

To create a CA pool that doesn't publicly publish CA certificates and CRLs:

    $ gcloud privateca pools create my-pool --location=us-west1 \
      --issuance-policy=policy.yaml --no-publish-ca-cert \
      --no-publish-crl
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/create)

---
### `gcloud privateca pools delete`

Delete a CA pool

Note that all certificate authorities must be removed from the CA Pool
before the CA pool can be deleted.

**Synopsis:**
```
gcloud privateca pools delete (CA_POOL : --location=LOCATION)
    [--ignore-dependent-resources] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA POOL resource - The ca pool to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument CA_POOL on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CA_POOL
     ID of the CA_POOL or fully qualified identifier for the CA_POOL.

     To set the pool attribute:
     + provide the argument CA_POOL on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA_POOL.

     To set the location attribute:
     + provide the argument CA_POOL on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ignore-dependent-resources` |  |  | This field skips the integrity check that would normally prevent breaking a CA Pool if it is used by another cloud resource and allows the CA Pool to be in a state where it is not able to issue certificates. Doing so may result in unintended and unrecoverable effects on any dependent resource(s) since the CA Pool would not be able to issue certificates. |


**Examples:**
```bash
To delete a CA pool:

    $ gcloud privateca pools delete my-pool --location=us-west1

To delete a CA pool while skipping the confirmation input:

    $ gcloud privateca pools delete my-pool --location=us-west1 --quiet
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/delete)

---
### `gcloud privateca pools describe`

Get metadata for a CA pool

Returns metadata for the given CA pool.

**Synopsis:**
```
gcloud privateca pools describe (POOL : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA Pool resource - The CA pool for which to obtain metadata. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument pool on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POOL
     ID of the CA Pool or fully qualified identifier for the CA Pool.

     To set the pool attribute:
     + provide the argument pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA Pool.

     To set the location attribute:
     + provide the argument pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Examples:**
```bash
To get metadata for the CA pool 'my-pool' in location 'us-west1':

    $ gcloud privateca pools describe my-pool --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/describe)

---
### `gcloud privateca pools get-ca-certs`

Get the root CA certs for all active CAs in the CA pool

**Synopsis:**
```
gcloud privateca pools get-ca-certs (CA_POOL : --location=LOCATION)
    --output-file=OUTPUT_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA POOL resource - The ca pool whose CA certificates should be fetched.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument CA_POOL on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CA_POOL
     ID of the CA_POOL or fully qualified identifier for the CA_POOL.

     To set the pool attribute:
     + provide the argument CA_POOL on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA_POOL.

     To set the location attribute:
     + provide the argument CA_POOL on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | The path where the concatenated PEM certificates will be written. This will include the root CA certificate for each active CA in the CA pool. |


**Examples:**
```bash
To get the root CA certs for all active CAs in the CA pool:

    $ gcloud privateca pools get-ca-certs my-pool \
        --output-file=ca-certificates.pem --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/get-ca-certs)

---
### `gcloud privateca pools get-iam-policy`

Get the IAM policy for a CA pool

Gets the IAM policy for the given CA pool.

    Returns an empty policy if the resource does not have a policy
    set.

**Synopsis:**
```
gcloud privateca pools get-iam-policy (POOL : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA Pool resource - The CA pool for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument pool on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POOL
     ID of the CA Pool or fully qualified identifier for the CA Pool.

     To set the pool attribute:
     + provide the argument pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA Pool.

     To set the location attribute:
     + provide the argument pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Examples:**
```bash
To get the IAM policy for the CA pool 'my-pool' with the location
'us-west1', run:

    $ gcloud privateca pools get-iam-policy my-pool --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/get-iam-policy)

---
### `gcloud privateca pools list`

List CA pools within a project

**Synopsis:**
```
gcloud privateca pools list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the CA pools. If this is not specified, CA pools across all locations will be listed. |


**Examples:**
```bash
To list the CA Pools within a project:

    $ gcloud privateca pools list

To list the CA Pools within a project and region 'us-west1':

    $ gcloud privateca pools list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/list)

---
### `gcloud privateca pools remove-iam-policy-binding`

Remove IAM policy binding for a CA pool

Removes a policy binding to the IAM policy of a CA pool. One binding
consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud privateca pools remove-iam-policy-binding
    (POOL : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA Pool resource - The CA pool for which to remove the IAM policy binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument pool on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POOL
     ID of the CA Pool or fully qualified identifier for the CA Pool.

     To set the pool attribute:
     + provide the argument pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA Pool.

     To set the location attribute:
     + provide the argument pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
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
'roles/privateca.certificateManager' for the user 'test-user@gmail.com' on
the CA pool 'my-pool' with the location 'us-west1', run:

    $ gcloud privateca pools remove-iam-policy-binding my-pool \
        --location=us-west1 --member='user:test-user@gmail.com' \
        --role='roles/privateca.certificateManager'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/remove-iam-policy-binding)

---
### `gcloud privateca pools set-iam-policy`

Set the IAM policy for a CA pool

Sets the IAM policy for the given CA pool as defined in a JSON or YAML
file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud privateca pools set-iam-policy (POOL : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA Pool resource - The CA pool for which to update the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument pool on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POOL
     ID of the CA Pool or fully qualified identifier for the CA Pool.

     To set the pool attribute:
     + provide the argument pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA Pool.

     To set the location attribute:
     + provide the argument pool on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for the CA pool 'my-pool' with the location
'us-west1':

    $ gcloud privateca pools set-iam-policy my-pool policy.json \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/set-iam-policy)

---
### `gcloud privateca pools update`

Update an existing CA Pool

**Synopsis:**
```
gcloud privateca pools update (CA_POOL : --location=LOCATION)
    [--encryption-key=ENCRYPTION_KEY] [--issuance-policy=ISSUANCE_POLICY]
    [--no-publish-ca-cert] [--no-publish-crl]
    [--publishing-encoding-format=PUBLISHING_ENCODING_FORMAT;
      default="pem"] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CA POOL resource - The ca pool to update. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument CA_POOL on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CA_POOL
     ID of the CA_POOL or fully qualified identifier for the CA_POOL.

     To set the pool attribute:
     + provide the argument CA_POOL on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CA_POOL.

     To set the location attribute:
     + provide the argument CA_POOL on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--encryption-key` | ENCRYPTION_KEY |  | The full resource name of the Cloud KMS key to use for encrypting certificate data at rest. The key must be in the same region as the CA pool. |
| `--issuance-policy` | ISSUANCE_POLICY |  | A YAML file describing this CA Pool's issuance policy. |
| `--publish-ca-cert` |  |  | If this is enabled, the following will happen: 1) The CA certificates will be written to a known location within the CA distribution point. 2) The AIA extension in all issued certificates will point to the CA cert URL in that distribution point. If this gets disabled, the AIA extension will not be written to any future certificates issued by this CA. However, an existing bucket will not be deleted, and the CA certificates will not be removed from that bucket. Note that the same bucket may be used for the CRLs if --publish-crl is set. Enabled by default, use --no-publish-ca-cert to disable. |
| `--publish-crl` |  |  | If this gets enabled, the following will happen: 1) CRLs will be written to a known location within the CA distribution point. 2) The CDP extension in all future issued certificates will point to the CRL URL in that distribution point. If this gets disabled, the CDP extension will not be written to any future certificates issued by CAs in this pool, and new CRLs will not be published to that bucket (which affects existing certs). However, an existing bucket will not be deleted, and any existing CRLs will not be removed from that bucket. Note that the same bucket may be used for the CA cert if --publish-ca-cert is set. CRL publication is not supported for CAs in the DevOps tier. Enabled by default, use --no-publish-crl to disable. |
| `--publishing-encoding-format` | one of: der, pem | pem | The encoding format of the content published to storage buckets. PUBLISHING_ENCODING_FORMAT must be one of: der, pem. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels on a CA pool:

    $ gcloud privateca pools update my-pool --location=us-west1 \
        --update-labels=foo=bar

To disable publishing CRLs on a CA pool:

    $ gcloud privateca pools update my-pool --location=us-west1 \
        --no-publish-crl
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/pools/update)

---
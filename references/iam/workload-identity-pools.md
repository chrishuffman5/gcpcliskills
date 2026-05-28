# gcloud iam workload-identity-pools

manage IAM workload identity pools

### `gcloud iam workload-identity-pools add-iam-policy-binding`

Add IAM policy binding for a workload identity pool

Adds a policy binding to the IAM policy of a workload identity pool, given
a workload identity pool ID and the binding. A binding consists of at least
one member, a role, and an optional condition.

**Synopsis:**
```
gcloud iam workload-identity-pools add-iam-policy-binding
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to add the
IAM policy binding for. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
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
To add an IAM policy binding for the role of
roles/iam.workloadIdentityPoolViewer for the user test-user@gmail.com on a
workload identity pool with identifier my-workload-identity-pool, run:

    $ gcloud iam workload-identity-pools add-iam-policy-binding \
        my-workload-identity-pool --location="global" \
        --member='user:test-user@gmail.com' \
        --role='roles/iam.workloadIdentityPoolViewer'

To add an IAM policy binding for the role of
roles/iam.workloadIdentityPoolViewer for all authenticated users on a
workload identity pool with identifier my-workload-identity-pool, run:

    $ gcloud iam workload-identity-pools add-iam-policy-binding \
        my-workload-identity-pool --location="global" \
        --member='allAuthenticatedUsers' \
        --role='roles/iam.workloadIdentityPoolViewer'

To add an IAM policy binding that expires at the end of the year 2024 for
the role of roles/iam.workloadIdentityPoolViewer and the user
test-user@gmail.com on a workload identity pool with identifier
my-workload-identity-pool, run:

    $ gcloud iam workload-identity-pools add-iam-policy-binding \
        my-workload-identity-pool --location="global" \
        --member='user:test-user@gmail.com' \
        --role='roles/iam.workloadIdentityPoolViewer' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2024,descrip\
    tion=Expires at midnight on 2024-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details on
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/add-iam-policy-binding)

---
### `gcloud iam workload-identity-pools create`

Create a new workload identity pool

Create a new workload identity pool.

**Synopsis:**
```
gcloud iam workload-identity-pools create
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION)
    [--description=DESCRIPTION] [--disabled] [--display-name=DISPLAY_NAME]
    [--inline-certificate-issuance-config-file=INLINE_CERTIFICATE_ISSUANCE_CONFIG_FILE]
    [--inline-trust-config-file=INLINE_TRUST_CONFIG_FILE] [--mode=MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description of the pool. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the pool is disabled. You cannot use a disabled pool to exchange tokens, or use existing tokens to access resources. If the pool is re-enabled, existing tokens grant access again. |
| `--display-name` | DISPLAY_NAME |  | A display name for the pool. Cannot exceed 32 characters. |
| `--inline-certificate-issuance-config-file` | INLINE_CERTIFICATE_ISSUANCE_CONFIG_FILE |  | YAML file with configuration for certificate issuance. Example file format: inlineCertificateIssuanceConfig: caPools: us-east1: projects/1234/locations/us-east1/caPools/capoolname us-west1: projects/1234/locations/us-west1/caPools/capoolname keyAlgorithm: ECDSA_P256 lifetime: 86400s rotationWindowPercentage: 50 |
| `--inline-trust-config-file` | INLINE_TRUST_CONFIG_FILE |  | YAML file with configuration for providing additional trust bundles. Example file format: inlineTrustConfig: additionalTrustBundles: example.com: trustAnchors: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" myorg.com: trustAnchors: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" |
| `--mode` | one of: federation-only, mode-unspecified, trust-domain |  | The mode of the pool. MODE must be one of: federation-only, mode-unspecified, trust-domain. |


**Examples:**
```bash
The following command creates a disabled workload identity pool in the
default project with the ID my-workload-identity-pool. Explicit values for
all required and optional parameters are provided.

    $ gcloud iam workload-identity-pools create \
        my-workload-identity-pool --location="global" \
        --display-name="My workload pool" \
        --description="My workload pool description" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/create)

---
### `gcloud iam workload-identity-pools create-cred-config`

Create a configuration file for generated credentials

This command creates a configuration file to allow access to authenticated
Google Cloud actions from a variety of external accounts.

**Synopsis:**
```
gcloud iam workload-identity-pools create-cred-config AUDIENCE
    --output-file=OUTPUT_FILE
    (--aws | --azure | --credential-cert-path=CREDENTIAL_CERT_PATH
      | --credential-source-file=CREDENTIAL_SOURCE_FILE
      | --credential-source-url=CREDENTIAL_SOURCE_URL
      | --executable-command=EXECUTABLE_COMMAND) [--app-id-uri=APP_ID_URI]
    [--credential-source-field-name=CREDENTIAL_SOURCE_FIELD_NAME]
    [--credential-source-headers=[key=value,...]]
    [--credential-source-type=CREDENTIAL_SOURCE_TYPE] [--enable-imdsv2]
    [--sts-location=STS_LOCATION] [--subject-token-type=SUBJECT_TOKEN_TYPE]
    [--credential-cert-private-key-path=CREDENTIAL_CERT_PRIVATE_KEY_PATH
      : --credential-cert-configuration-output-file=CREDENTIAL_CERT_CONFIGURATION_OUTPUT_FILE --credential-cert-trust-chain-path=CREDENTIAL_CERT_TRUST_CHAIN_PATH]
    [--executable-output-file=EXECUTABLE_OUTPUT_FILE
      --executable-timeout-millis=EXECUTABLE_TIMEOUT_MILLIS]
    [--service-account=SERVICE_ACCOUNT
      : --service-account-token-lifetime-seconds=SERVICE_ACCOUNT_TOKEN_LIFETIME_SECONDS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AUDIENCE
   The workload identity pool provider fully qualified identifier.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | Location to store the generated credential configuration file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--app-id-uri` | APP_ID_URI |  | The custom Application ID URI for the Azure access token. |
| `--credential-source-field-name` | CREDENTIAL_SOURCE_FIELD_NAME |  | Subject token field name (key) in a JSON credential source. |
| `--credential-source-headers` | [key=value,...] |  | Headers to use when querying the credential-source-url. |
| `--credential-source-type` | CREDENTIAL_SOURCE_TYPE |  | Format of the credential source (JSON or text). |
| `--enable-imdsv2` |  |  | Adds the AWS IMDSv2 session token Url to the credential source to enforce the AWS IMDSv2 flow. |
| `--sts-location` | STS_LOCATION |  | The location to use for the Security Token Service token endpoint. For example, specifying us-central1 will configure the client to use the regional endpoint sts.us-central1.rep.googleapis.com. If not specified, the global endpoint sts.googleapis.com is used. |
| `--subject-token-type` | SUBJECT_TOKEN_TYPE |  | The type of token being used for authorization. This defaults to urn:ietf:params:oauth:token-type:jwt. |


**Examples:**
```bash
To create a file-sourced credential configuration for your project, run:

    $ gcloud iam workload-identity-pools create-cred-config \
        projects/$PROJECT_NUMBER/locations/$REGION/\
    workloadIdentityPools/$WORKLOAD_POOL_ID/providers/$PROVIDER_ID \
        --service-account=$EMAIL \
        --credential-source-file=$PATH_TO_OIDC_ID_TOKEN \
        --output-file=credentials.json

To create a URL-sourced credential configuration for your project, run:

    $ gcloud iam workload-identity-pools create-cred-config \
        projects/$PROJECT_NUMBER/locations/$REGION/\
    workloadIdentityPools/$WORKLOAD_POOL_ID/providers/$PROVIDER_ID \
        --service-account=$EMAIL \
        --credential-source-url=$URL_FOR_OIDC_TOKEN \
        --credential-source-headers=Key=Value \
        --output-file=credentials.json

To create an executable-source credential configuration for your project,
run the following command:

    $ gcloud iam workload-identity-pools create-cred-config \
        locations/$REGION/workforcePools/$WORKFORCE_POOL_ID/providers/\
    $PROVIDER_ID --executable-command=$EXECUTABLE_COMMAND \
        --executable-timeout-millis=30000 \
        --executable-output-file=$CACHE_FILE \
        --output-file=credentials.json

To create an AWS-based credential configuration for your project, run:

    $ gcloud iam workload-identity-pools create-cred-config \
        projects/$PROJECT_NUMBER/locations/$REGION/\
    workloadIdentityPools/$WORKLOAD_POOL_ID/providers/$PROVIDER_ID \
        --service-account=$EMAIL --aws --enable-imdsv2 \
        --output-file=credentials.json

To create an Azure-based credential configuration for your project, run:

    $ gcloud iam workload-identity-pools create-cred-config \
        projects/$PROJECT_NUMBER/locations/$REGION/\
    workloadIdentityPools/$WORKLOAD_POOL_ID/providers/$PROVIDER_ID \
        --service-account=$EMAIL --azure \
        --app-id-uri=$URI_FOR_AZURE_APP_ID \
        --output-file=credentials.json

To create an X.509 certificate-based credential configuration for your
project, run:

    $ gcloud iam workload-identity-pools create-cred-config \
        projects/$PROJECT_NUMBER/locations/$REGION/\
    workloadIdentityPools/$WORKLOAD_POOL_ID/providers/$PROVIDER_ID \
        --service-account=$EMAIL \
        --credential-cert-path=$PATH_TO_CERTIFICATE_FILE \
        --credential-cert-private-key-path=$PATH_TO_PRIVATE_KEY_FILE \
        --output-file=credentials.json

To use the resulting file for any of these commands, set the
GOOGLE_APPLICATION_CREDENTIALS environment variable to point to the
generated file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/create-cred-config)

---
### `gcloud iam workload-identity-pools delete`

Delete a workload identity pool

Delete a workload identity pool.

**Synopsis:**
```
gcloud iam workload-identity-pools delete
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command deletes the workload identity pool with the ID
my-workload-identity-pool:

    $ gcloud iam workload-identity-pools delete \
        my-workload-identity-pool --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/delete)

---
### `gcloud iam workload-identity-pools describe`

Describe a workload identity pool

Describe a workload identity pool.

**Synopsis:**
```
gcloud iam workload-identity-pools describe
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command describes the workload identity pool with the ID
my-workload-identity-pool:

    $ gcloud iam workload-identity-pools describe \
        my-workload-identity-pool --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/describe)

---
### `gcloud iam workload-identity-pools get-iam-policy`

Get the IAM policy for a workload identity pool

Get the IAM policy for a workload identity pool.

**Synopsis:**
```
gcloud iam workload-identity-pools get-iam-policy
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool for which you
want to get IAM policy for. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command gets the IAM policy for the workload identity pool
with ID my-workload-identity-pool:

    $ gcloud iam workload-identity-pools get-iam-policy \
        my-workload-identity-pool --location="global"

The following command gets the IAM policy for the workload identity pool
with ID my-workload-identity-pool and outputs as a JSON which can be edited
and used as the policy file input for set-iam-policy command:

    $ gcloud iam workload-identity-pools get-iam-policy \
        my-workload-identity-pool --location="global" --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/get-iam-policy)

---
### `gcloud iam workload-identity-pools list`

List workload identity pools

List workload identity pools.

**Synopsis:**
```
gcloud iam workload-identity-pools list --location=LOCATION
    [--show-deleted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Whether to return soft-deleted pools. |


**Examples:**
```bash
The following command lists all workload identity pools in the default
project, including soft-deleted pools:

    $ gcloud iam workload-identity-pools list --location="global" \
        --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/list)

---
### `gcloud iam workload-identity-pools remove-iam-policy-binding`

Remove IAM policy binding from a workload identity pool

Removes a policy binding from the IAM policy of a workload identity pool. A
binding consists of at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud iam workload-identity-pools remove-iam-policy-binding
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to remove the
IAM policy binding from. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
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
To remove an IAM policy binding for the role of
roles/iam.workloadIdentityPoolViewer for the user test-user@gmail.com on a
workload identity pool with identifier my-workload-identity-pool, run:

    $ gcloud iam workload-identity-pools remove-iam-policy-binding \
        my-workload-identity-pool --location="global" \
        --member='user:test-user@gmail.com' \
        --role='roles/iam.workloadIdentityPoolViewer'

To remove an IAM policy binding for the role of
roles/iam.workloadIdentityPoolViewer from all authenticated users on
workload identity pool with identifier my-workload-identity-pool, run:

    $ gcloud iam workload-identity-pools remove-iam-policy-binding \
        my-workload-identity-pool --location="global" \
        --member='allAuthenticatedUsers' \
        --role='roles/iam.workloadIdentityPoolViewer'

To remove an IAM policy binding which expires at the end of the year 2024
for the role of roles/iam.workloadIdentityPoolViewer and the user
test-user@gmail.com on a workload identity pool with identifier
my-workload-identity-pool, run:

    $ gcloud iam workload-identity-pools remove-iam-policy-binding \
        my-workload-identity-pool --location="global" \
        --member='user:test-user@gmail.com' \
        --role='roles/iam.workloadIdentityPoolViewer' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2024,descrip\
    tion=Expires at midnight on 2024-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details on
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/remove-iam-policy-binding)

---
### `gcloud iam workload-identity-pools set-iam-policy`

Set the IAM policy for a workload identity pool

Replaces the existing IAM policy for a workload identity pool given a
workload identity pool ID and a file encoded in JSON or YAML that contains
the IAM policy.

**Synopsis:**
```
gcloud iam workload-identity-pools set-iam-policy
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool for which you
want to set IAM policy for. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for the workload identity pool with ID
my-workload-identity-pool:

    $ gcloud iam workload-identity-pools set-iam-policy \
        my-workload-identity-pool policy.json --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/set-iam-policy)

---
### `gcloud iam workload-identity-pools undelete`

Undelete a workload identity pool

Undelete a workload identity pool.

**Synopsis:**
```
gcloud iam workload-identity-pools undelete
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to undelete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command undeletes the workload identity pool with the ID
my-workload-identity-pool:

    $ gcloud iam workload-identity-pools undelete \
        my-workload-identity-pool --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/undelete)

---
### `gcloud iam workload-identity-pools update`

Update a workload identity pool

Update a workload identity pool.

**Synopsis:**
```
gcloud iam workload-identity-pools update
    (WORKLOAD_IDENTITY_POOL : --location=LOCATION)
    [--description=DESCRIPTION] [--disabled] [--display-name=DISPLAY_NAME]
    [--inline-trust-config-file=INLINE_TRUST_CONFIG_FILE]
    [--inline-certificate-issuance-config-file=INLINE_CERTIFICATE_ISSUANCE_CONFIG_FILE | --certificate-lifetime=CERTIFICATE_LIFETIME --key-algorithm=KEY_ALGORITHM --rotation-window-percentage=ROTATION_WINDOW_PERCENTAGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool resource - The workload identity pool to update.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument workload_identity_pool on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD_IDENTITY_POOL
     ID of the workload identity pool or fully qualified identifier for
     the workload identity pool.

     To set the workload_identity_pool attribute:
     + provide the argument workload_identity_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument workload_identity_pool on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description of the pool. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the pool is disabled. You cannot use a disabled pool to exchange tokens, or use existing tokens to access resources. If the pool is re-enabled, existing tokens grant access again. |
| `--display-name` | DISPLAY_NAME |  | A display name for the pool. Cannot exceed 32 characters. |
| `--inline-trust-config-file` | INLINE_TRUST_CONFIG_FILE |  | YAML file with configuration for providing additional trust bundles. Example file format: inlineTrustConfig: additionalTrustBundles: example.com: trustAnchors: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" myorg.com: trustAnchors: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" |


**Examples:**
```bash
The following command updates the workload identity pool with the ID
my-workload-identity-pool:

    $ gcloud iam workload-identity-pools update \
        my-workload-identity-pool --location="global" \
        --display-name="My workload pool" \
        --description="My workload pool description" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/update)

---

## `gcloud iam workload-identity-pools managed-identities` — manage IAM workload identity pool managed identities
### `gcloud iam workload-identity-pools managed-identities add-attestation-rule`

Add an attestation rule on a workload identity pool managed identity

Add an attestation rule on a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities add-attestation-rule
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --google-cloud-resource=GOOGLE_CLOUD_RESOURCE [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - The workload identity
pool managed identity to add attestation rule on. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--google-cloud-resource` | GOOGLE_CLOUD_RESOURCE |  | A single workload operating on Google Cloud. This will be set in the attestation rule to be added. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command adds an attestation rule with a Google Cloud resource
on a workload identity pool managed identity my-managed-identity.

    $ gcloud iam workload-identity-pools managed-identities \
        add-attestation-rule my-managed-identity \
        --namespace="my-namespace" \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" \
        --google-cloud-resource="//compute.googleapis.com/projects/123/t\
    ype/Instance/attached_service_account.uid/12345"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/add-attestation-rule)

---
### `gcloud iam workload-identity-pools managed-identities create`

Create a workload identity pool managed identity

Create a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities create
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [--description=DESCRIPTION] [--disabled] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - Workload identity pool
managed identity to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the managed identity. |
| `--disabled` |  |  | Whether the managed identity is disabled. If disabled, credentials may no longer be issued for this identity. Existing credentials may continue to be accepted until they expire. |


**Examples:**
```bash
The following command creates a workload identity pool managed identity
with the ID my-managed-identity:

    $ gcloud iam workload-identity-pools managed-identities create \
        my-managed-identity --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace" \
        --description="My managed identity description" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/create)

---
### `gcloud iam workload-identity-pools managed-identities delete`

Delete a workload identity pool managed identity

Delete a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities delete
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - Workload identity pool
managed identity to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workload identity pool managed identity in
the default project with the ID my-managed-identity.

    $ gcloud iam workload-identity-pools managed-identities delete \
        my-managed-identity --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/delete)

---
### `gcloud iam workload-identity-pools managed-identities describe`

Describe a workload identity pool managed identity

Describe a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities describe
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - Workload identity pool
managed identity to describe. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes a workload identity pool managed identity
in the default project with the ID my-managed-identity.

    $ gcloud iam workload-identity-pools managed-identities describe \
        my-managed-identity --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/describe)

---
### `gcloud iam workload-identity-pools managed-identities list`

List workload identity pool managed identities

List workload identity pool managed identities.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities list
    (--namespace=NAMESPACE : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--show-deleted]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--namespace` | NAMESPACE |  | _[This must be specified.]_ ID of the workload identity pool namespace or fully qualified identifier for the workload identity pool namespace. To set the namespace attribute: + provide the argument --namespace on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location name. To set the location attribute: + provide the argument --namespace on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--workload-identity-pool` | WORKLOAD_IDENTITY_POOL |  | _[This must be specified.]_ The ID to use for the pool, which becomes the final component of the resource name. This value should be 4-32 characters, and may contain the characters [a-z0-9-]. The prefix gcp- is reserved for use by Google, and may not be specified. To set the workload-identity-pool attribute: + provide the argument --namespace on the command line with a fully specified name; + provide the argument --workload-identity-pool on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Whether to return soft-deleted resources. |


**Examples:**
```bash
The following command lists all managed identities in the workload identity
pool namespace, including soft-deleted managed identities:

    $ gcloud iam workload-identity-pools managed-identities list \
        --namespace="my-namespace" \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/list)

---
### `gcloud iam workload-identity-pools managed-identities list-attestation-rules`

List the attestation rules on a workload identity pool managed identity

List the attestation rules on a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities
    list-attestation-rules
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--container-id-filter=CONTAINER_ID_FILTER] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - The managed identity to
list attestation rules. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--container-id-filter` | CONTAINER_ID_FILTER |  | Apply a filter on the container ids of the attestation rules being listed. Expects a comma-delimited string of project numbers in the format projects/<project-number>,.... |


**Examples:**
```bash
The following command lists the attestation rules on a workload identity
pool managed identity my-managed-identity with a container id filter.

    $ gcloud iam workload-identity-pools managed-identities \
        list-attestation-rules my-managed-identity \
        --namespace="my-namespace" \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" \
        --container-id-filter="projects/123,projects/456"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/list-attestation-rules)

---
### `gcloud iam workload-identity-pools managed-identities remove-attestation-rule`

Remove an attestation rule on a workload identity pool managed identity

Remove an attestation rule on a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities
    remove-attestation-rule
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --google-cloud-resource=GOOGLE_CLOUD_RESOURCE [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - The workload identity
pool managed identity to remove attestation rule on. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--google-cloud-resource` | GOOGLE_CLOUD_RESOURCE |  | A single workload operating on Google Cloud. This will be set in the attestation rule to be added. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command removes an attestation rule with a Google Cloud
resource on a workload identity pool managed identity my-managed-identity.

    $ gcloud iam workload-identity-pools managed-identities \
        remove-attestation-rule my-managed-identity \
        --namespace="my-namespace" \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" \
        --google-cloud-resource="//compute.googleapis.com/projects/123/t\
    ype/Instance/attached_service_account.uid/12345"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/remove-attestation-rule)

---
### `gcloud iam workload-identity-pools managed-identities set-attestation-rules`

Set attestation rules on a workload identity pool managed identity

Set attestation rules on a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities set-attestation-rules
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --policy-file=POLICY_FILE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - The workload identity
pool managed identity to set attestation rules on. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-file` | POLICY_FILE |  | Path to a local JSON-formatted or YAML-formatted file containing an attestation policy, structured as a list of attestation rules (https://cloud.google.com/iam/docs/reference/rest/v1/projects.locations.workloadIdentityPools.namespaces.managedIdentities/setAttestationRules#request-body). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command sets attestation rules on a workload identity pool
managed identity my-managed-identity using a policy file.

    $ gcloud iam workload-identity-pools managed-identities \
        set-attestation-rules my-managed-identity \
        --namespace="my-namespace" \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" --policy-file="policy.json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/set-attestation-rules)

---
### `gcloud iam workload-identity-pools managed-identities undelete`

Undelete a workload identity pool managed identity

Undelete a workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities undelete
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - Workload identity pool
managed identity to undelete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workload identity pool managed identity
in the default project with the ID my-managed-identity.

    $ gcloud iam workload-identity-pools managed-identities undelete \
        my-managed-identity --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/undelete)

---
### `gcloud iam workload-identity-pools managed-identities update`

Update workload identity pool managed identity

Update workload identity pool managed identity.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities update
    (MANAGED_IDENTITY : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [--description=DESCRIPTION] [--disabled] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity resource - Workload identity pool
managed identity to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument managed_identity on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGED_IDENTITY
     ID of the workload identity pool managed identity or fully qualified
     identifier for the workload identity pool managed identity.

     To set the managed_identity attribute:
     + provide the argument managed_identity on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument managed_identity on the command line with a
       fully specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the managed identity. |
| `--disabled` |  |  | Whether the managed identity is disabled. If disabled, credentials may no longer be issued for this identity. Existing credentials may continue to be accepted until they expire. |


**Examples:**
```bash
The following command updates the workload identity pool managed identity
with the ID my-managed-identity:

    $ gcloud iam workload-identity-pools managed-identities update \
        my-managed-identity --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace" \
        --description="My managed identity description" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/update)

---

## `gcloud iam workload-identity-pools managed-identities operations` — manage IAM workload identity pool managed identity long running operations
### `gcloud iam workload-identity-pools managed-identities operations describe`

Describe a workload identity pool managed identity operation

Describe a workload identity pool managed identity operation.

**Synopsis:**
```
gcloud iam workload-identity-pools managed-identities operations describe
    (OPERATION : --location=LOCATION --managed-identity=MANAGED_IDENTITY
      --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool managed identity operation resource - Workload
identity pool managed identity long-running operation to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the workload identity pool managed identity operation or fully
     qualified identifier for the workload identity pool managed identity
     operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --managed-identity=MANAGED_IDENTITY
     The ID to use for the managed identity. This value must be 2-63
     characters and may contain the characters [a-z0-9-]. The prefix gcp-
     is reserved for use by Google, and may not be specified.

     To set the managed-identity attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --managed-identity on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes the long-running workload identity pool
managed identity operation with the ID my-operation:

    $ gcloud iam workload-identity-pools managed-identities operations \
        describe my-operation \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace" \
        --managed-identity="my-managed-identity" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/managed-identities/operations/describe)

---

## `gcloud iam workload-identity-pools namespaces` — manage IAM workload identity pool namespaces
### `gcloud iam workload-identity-pools namespaces create`

Create a workload identity pool namespace

Create a workload identity pool namespace.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces create
    (NAMESPACE : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [--description=DESCRIPTION] [--disabled] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool namespace resource - The workload identity pool
namespace to create. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the workload identity pool namespace or fully qualified
     identifier for the workload identity pool namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the namespace. |
| `--disabled` |  |  | Whether the namespace is disabled. If disabled, credentials may no longer be issued for identities in this namespace. Existing credentials may continue to be accepted until they expire. |


**Examples:**
```bash
The following command creates a workload identity pool namespace with the
ID my-namespace:

    $ gcloud iam workload-identity-pools namespaces create \
        my-namespace --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --description="My namespace description" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/create)

---
### `gcloud iam workload-identity-pools namespaces delete`

Delete a workload identity pool namespace

Delete a workload identity pool namespace.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces delete
    (NAMESPACE : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool namespace resource - The workload identity pool
namespace to delete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the workload identity pool namespace or fully qualified
     identifier for the workload identity pool namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workload identity pool namespace in the
default project with the ID my-namespace.

    $ gcloud iam workload-identity-pools namespaces delete \
        my-namespace --location="global" \
        --workload-identity-pool="my-workload-identity-pool"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/delete)

---
### `gcloud iam workload-identity-pools namespaces describe`

Describe a workload identity pool namespace

Describe a workload identity pool namespace.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces describe
    (NAMESPACE : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool namespace resource - The workload identity pool
namespace to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the workload identity pool namespace or fully qualified
     identifier for the workload identity pool namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes a workload identity pool namespace in the
default project with the ID my-namespace.

    $ gcloud iam workload-identity-pools namespaces describe \
        my-namespace --location="global" \
        --workload-identity-pool="my-workload-identity-pool"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/describe)

---
### `gcloud iam workload-identity-pools namespaces list`

List workload identity pool namespaces

List workload identity pool namespaces.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces list
    (--workload-identity-pool=WORKLOAD_IDENTITY_POOL : --location=LOCATION)
    [--show-deleted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--workload-identity-pool` | WORKLOAD_IDENTITY_POOL |  | _[This must be specified.]_ ID of the workload identity pool or fully qualified identifier for the workload identity pool. To set the workload-identity-pool attribute: + provide the argument --workload-identity-pool on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location name. To set the location attribute: + provide the argument --workload-identity-pool on the command line with a fully specified name; + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Whether to return soft-deleted resources. |


**Examples:**
```bash
The following command lists all namespaces in the workload identity pool,
including soft-deleted namespaces:

    $ gcloud iam workload-identity-pools namespaces list \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/list)

---
### `gcloud iam workload-identity-pools namespaces undelete`

Undelete a workload identity pool namespace

Undelete a workload identity pool namespace.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces undelete
    (NAMESPACE : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool namespace resource - The workload identity pool
namespace to undelete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the workload identity pool namespace or fully qualified
     identifier for the workload identity pool namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workload identity pool namespace in the
default project with the ID my-namespace.

    $ gcloud iam workload-identity-pools namespaces undelete \
        my-namespace --location="global" \
        --workload-identity-pool="my-workload-identity-pool"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/undelete)

---
### `gcloud iam workload-identity-pools namespaces update`

Update workload identity pool namespace

Update workload identity pool namespace.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces update
    (NAMESPACE : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--async]
    [--description=DESCRIPTION] [--disabled] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool namespace resource - The workload identity pool
namespace to update. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument namespace on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAMESPACE
     ID of the workload identity pool namespace or fully qualified
     identifier for the workload identity pool namespace.

     To set the namespace attribute:
     + provide the argument namespace on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument namespace on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description of the namespace. |
| `--disabled` |  |  | Whether the namespace is disabled. If disabled, credentials may no longer be issued for identities in this namespace. Existing credentials may continue to be accepted until they expire. |


**Examples:**
```bash
The following command updates the workload identity pool namespace with the
ID my-namespace:

    $ gcloud iam workload-identity-pools namespaces update \
        my-namespace --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --description="My namespace description" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/update)

---

## `gcloud iam workload-identity-pools namespaces operations` — manage IAM workload identity pool namespace long running operations
### `gcloud iam workload-identity-pools namespaces operations describe`

Describe a workload identity pool namespace operation

Describe a workload identity pool namespace operation.

**Synopsis:**
```
gcloud iam workload-identity-pools namespaces operations describe
    (OPERATION : --location=LOCATION --namespace=NAMESPACE
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool namespace operation resource - The workload
identity pool namespace long-running operation to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the workload identity pool namespace operation or fully
     qualified identifier for the workload identity pool namespace
     operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --namespace=NAMESPACE
     The ID to use for the namespace. This value must be 2-63 characters,
     and may contain the characters [a-z0-9-]. The prefix gcp- is reserved
     for use by Google, and may not be specified.

     To set the namespace attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes the long-running workload identity pool
namespace operation with the ID my-operation:

    $ gcloud iam workload-identity-pools namespaces operations \
        describe my-operation \
        --workload-identity-pool="my-workload-identity-pool" \
        --namespace="my-namespace" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/namespaces/operations/describe)

---

## `gcloud iam workload-identity-pools operations` — manage IAM workload identity pool long running operations
### `gcloud iam workload-identity-pools operations describe`

Describe a workload identity pool operation

Describe a workload identity pool operation.

**Synopsis:**
```
gcloud iam workload-identity-pools operations describe
    (OPERATION : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool operation resource - The workload identity pool
long running operation to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the workload identity pool operation or fully qualified
     identifier for the workload identity pool operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes the long running workload identity
poolProvider operation with the ID my-operation:

    $ gcloud iam workload-identity-pools operations describe \
        my-operation \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/operations/describe)

---

## `gcloud iam workload-identity-pools providers` — manage IAM workload identity pool providers
### `gcloud iam workload-identity-pools providers create-aws`

Create a new AWS workload identity pool provider

Create a new AWS workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers create-aws
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --account-id=ACCOUNT_ID [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--account-id` | ACCOUNT_ID |  | The AWS account ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |


**Examples:**
```bash
The following command creates a disabled AWS workload identity pool
provider in the default project with the ID my-workload-identity-pool.
Explicit values for all required and optional parameters are provided.

    $ gcloud iam workload-identity-pools providers create-aws \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.arn" \
        --attribute-condition="true" --account-id=1234567890
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/create-aws)

---
### `gcloud iam workload-identity-pools providers create-oidc`

Create a new OIDC workload identity pool provider

Create a new OIDC workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers create-oidc
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --attribute-mapping=[KEY=VALUE,...] --issuer-uri=ISSUER_URI
    [--allowed-audiences=[ALLOWED_AUDIENCES,...]]
    [--attribute-condition=ATTRIBUTE_CONDITION] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME]
    [--jwk-json-path=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--issuer-uri` | ISSUER_URI |  | The OIDC issuer URL. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-audiences` | [ALLOWED_AUDIENCES,...] |  | Acceptable values for the aud field (audience) in the OIDC token. Token exchange requests are rejected if the token audience does not match one of the configured values. Each audience may be at most 256 characters. A maximum of 10 audiences may be configured. If this list is empty, the OIDC token audience must be equal to the full canonical resource name of the workload identity pool provider, with or without the HTTPS prefix. For example: //iam.googleapis.com/projects/<project-number>/locations/<location>/workloadIdentityPools/<pool-id>/providers/<provider-id> https://iam.googleapis.com/projects/<project-number>/locations/<location>/workloadIdentityPools/<pool-id>/providers/<provider-id> |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |
| `--jwk-json-path` | PATH_TO_FILE |  | Optional file containing jwk public keys. The file format must follow jwk specifications (https://www.rfc-editor.org/rfc/rfc7517#section-4). Example file format: { "keys": [ { "kty": "RSA/EC", "alg": "<algorithm>", "use": "sig", "kid": "<key-id>", "n": "", "e": "", "x": "", "y": "", "crv": "" } ] } . Use a full or relative path to a local file containing the value of jwk_json_path. |


**Examples:**
```bash
The following command creates a disabled OIDC workload identity pool
provider in the default project with the ID my-workload-identity-pool.
Explicit values for all required and optional parameters are provided.

    $ gcloud iam workload-identity-pools providers create-oidc \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --issuer-uri="https://test-idp.com" \
        --allowed-audiences=https://test-audience-1.com,https://\
    test-audience-2.com --jwk-json-path="path/to/jwk.json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/create-oidc)

---
### `gcloud iam workload-identity-pools providers create-saml`

Create a new SAML workload identity pool provider

Create a new SAML workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers create-saml
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --attribute-mapping=[KEY=VALUE,...] --idp-metadata-path=PATH_TO_FILE
    [--attribute-condition=ATTRIBUTE_CONDITION] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--idp-metadata-path` | PATH_TO_FILE |  | XML file with configuration metadata for the SAML identity provider. The metadata file must follow the SAML 2.0 metadata specification (https://www.oasis-open.org/committees/download.php/35391/sstc-saml-metadata-errata-2.0-wd-04-diff.pdf). Use a full or relative path to a local file containing the value of idp_metadata_path. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |


**Examples:**
```bash
The following command creates a disabled SAML workload identity pool
provider in the default project with the ID
my-workload-identity-pool-provider. Explicit values for all required and
optional parameters are provided.

    $ gcloud iam workload-identity-pools providers create-saml \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --idp-metadata-path="path/to/metadata/file.xml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/create-saml)

---
### `gcloud iam workload-identity-pools providers create-x509`

Create a new X.509 workload identity pool provider

Create a new X.509 workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers create-x509
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --trust-store-config-path=TRUST_STORE_CONFIG_PATH
    [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--trust-store-config-path` | TRUST_STORE_CONFIG_PATH |  | YAML file with configuration metadata for the X.509 identity provider. Example file format: trustStore: trustAnchors: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" intermediateCas: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |


**Examples:**
```bash
The following command creates a disabled X.509 workload identity pool
provider in the default project with the ID
my-workload-identity-pool-provider. Explicit values for all required and
optional parameters are provided.

    $ gcloud iam workload-identity-pools providers create-x509 \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --trust-store-config-path="path/to/config/file.yaml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/create-x509)

---
### `gcloud iam workload-identity-pools providers delete`

Delete a workload identity pool provider

Delete a workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers delete
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command deletes the workload identity pool provider with the
ID my-workload-identity-pool-provider:

    $ gcloud iam workload-identity-pools providers delete \
        my-workload-identity-pool-provider \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/delete)

---
### `gcloud iam workload-identity-pools providers describe`

Describe a workload identity pool provider

Describe a workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers describe
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes the workload identity pool provider with
the ID my-workload-identity-pool-provider:

    $ gcloud iam workload-identity-pools providers describe \
        my-workload-identity-pool-provider \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/describe)

---
### `gcloud iam workload-identity-pools providers list`

List workload identity pool providers

List workload identity pool providers.

**Synopsis:**
```
gcloud iam workload-identity-pools providers list
    (--workload-identity-pool=WORKLOAD_IDENTITY_POOL : --location=LOCATION)
    [--show-deleted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--workload-identity-pool` | WORKLOAD_IDENTITY_POOL |  | _[This must be specified.]_ ID of the workload identity pool or fully qualified identifier for the workload identity pool. To set the workload-identity-pool attribute: + provide the argument --workload-identity-pool on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location name. To set the location attribute: + provide the argument --workload-identity-pool on the command line with a fully specified name; + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Whether to return soft-deleted resources. |


**Examples:**
```bash
The following command lists all workload identity pool providers in the
workload identity pool, including soft-deleted providers:

    $ gcloud iam workload-identity-pools providers list \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global" --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/list)

---
### `gcloud iam workload-identity-pools providers undelete`

Undelete a workload identity pool provider

Undelete a workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers undelete
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to undelete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command undeletes the workload identity pool provider with
the ID my-workload-identity-pool-provider:

    $ gcloud iam workload-identity-pools providers undelete \
        my-workload-identity-pool-provider \
        --workload-identity-pool="my-workload-identity-pool" \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/undelete)

---
### `gcloud iam workload-identity-pools providers update-aws`

Update an AWS workload identity pool provider

Update an AWS workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers update-aws
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--account-id=ACCOUNT_ID] [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--account-id` | ACCOUNT_ID |  | The AWS account ID. |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |


**Examples:**
```bash
The following command updates an AWS workload identity pool provider with
the ID my-workload-identity-pool-provider. Explicit values for all required
and optional parameters are provided.

    $ gcloud iam workload-identity-pools providers update-aws \
        --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.arn" \
        --attribute-condition="true" --account-id=1234567890
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/update-aws)

---
### `gcloud iam workload-identity-pools providers update-oidc`

Update an OIDC workload identity pool provider

Update an OIDC workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers update-oidc
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--allowed-audiences=[ALLOWED_AUDIENCES,...]]
    [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME] [--issuer-uri=ISSUER_URI]
    [--jwk-json-path=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-audiences` | [ALLOWED_AUDIENCES,...] |  | Acceptable values for the aud field (audience) in the OIDC token. Token exchange requests are rejected if the token audience does not match one of the configured values. Each audience may be at most 256 characters. A maximum of 10 audiences may be configured. If this list is empty, the OIDC token audience must be equal to the full canonical resource name of the workload identity pool provider, with or without the HTTPS prefix. For example: //iam.googleapis.com/projects/<project-number>/locations/<location>/workloadIdentityPools/<pool-id>/providers/<provider-id> https://iam.googleapis.com/projects/<project-number>/locations/<location>/workloadIdentityPools/<pool-id>/providers/<provider-id> |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |
| `--issuer-uri` | ISSUER_URI |  | The OIDC issuer URL. |
| `--jwk-json-path` | PATH_TO_FILE |  | Optional file containing jwk public keys. The file format must follow jwk specifications (https://www.rfc-editor.org/rfc/rfc7517#section-4). Example file format: { "keys": [ { "kty": "RSA/EC", "alg": "<algorithm>", "use": "sig", "kid": "<key-id>", "n": "", "e": "", "x": "", "y": "", "crv": "" } ] } . Use a full or relative path to a local file containing the value of jwk_json_path. |


**Examples:**
```bash
The following command updates the OIDC workload identity pool provider with
the ID my-workload-identity-pool-provider. Explicit values for all required
and optional parameters are provided:

    $ gcloud iam workload-identity-pools providers update-oidc \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --issuer-uri="https://test-idp.com" \
        --allowed-audiences=https://test-audience-1.com,https://\
    test-audience-2.com --jwk-json-path="path/to/jwk.json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/update-oidc)

---
### `gcloud iam workload-identity-pools providers update-saml`

Update a SAML workload identity pool provider

Update a SAML workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers update-saml
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME]
    [--idp-metadata-path=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |
| `--idp-metadata-path` | PATH_TO_FILE |  | XML file with configuration metadata for the SAML identity provider. The metadata file must follow the SAML 2.0 metadata specification (https://www.oasis-open.org/committees/download.php/35391/sstc-saml-metadata-errata-2.0-wd-04-diff.pdf). Use a full or relative path to a local file containing the value of idp_metadata_path. |


**Examples:**
```bash
The following command updates the SAML workload identity pool provider with
the ID my-workload-identity-pool-provider. Explicit values for all required
and optional parameters are provided:

    $ gcloud iam workload-identity-pools providers update-saml \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --idp-metadata-path="path/to/metadata/file.xml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/update-saml)

---
### `gcloud iam workload-identity-pools providers update-x509`

Update an X.509 workload identity pool provider

Update an X.509 workload identity pool provider.

**Synopsis:**
```
gcloud iam workload-identity-pools providers update-x509
    (PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME]
    [--trust-store-config-path=TRUST_STORE_CONFIG_PATH]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider resource - The workload identity pool
provider to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the workload identity pool provider or fully qualified
     identifier for the workload identity pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict what otherwise valid authentication credentials issued by the provider should not be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential are accepted. The following example shows how to only allow credentials with a mapped google.groups value of admins: "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps attributes from authentication credentials issued by an external identity provider to Google Cloud attributes, such as subject and segment. Each key must be a string specifying the Google Cloud IAM attribute to map to. The following keys are supported: * google.subject: The principal IAM is authenticating. You can reference this value in IAM bindings. This is also the subject that appears in Cloud Logging logs. Cannot exceed 127 bytes. * google.groups: Groups the external identity belongs to. You can grant groups access to resources using an IAM principalSet binding; access applies to all members of the group. You can also provide custom attributes by specifying attribute.{custom_attribute}, where {custom_attribute} is the name of the custom attribute to be mapped. You can define a maximum of 50 custom attributes. The maximum length of a mapped attribute key is 100 characters, and the key may only contain the characters [a-z_0-9]. You can reference these attributes in IAM policies to define fine-grained access for a workload to Google Cloud resources. For example: * google.subject: principal://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/projects/{project}/locations/{location}/workloadIdentityPools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an identity provider credential to the normalized attribute specified by the corresponding map key. You can use the assertion keyword in the expression to access a JSON representation of the authentication credential issued by the provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. For AWS providers, the following rules apply: * If no attribute mapping is defined, the following default mapping applies: { "google.subject":"assertion.arn", "attribute.aws_role": "assertion.arn.contains('assumed-role')" " ? assertion.arn.extract('{account_arn}assumed-role/')" " + 'assumed-role/'" " + assertion.arn.extract('assumed-role/{role_name}/')" " : assertion.arn", } * If any custom attribute mappings are defined, they must include a mapping to the google.subject attribute. For OIDC providers, the following rules apply: * Custom attribute mappings must be defined, and must include a mapping to the google.subject attribute. For example, the following maps the sub claim of the incoming credential to the subject attribute on a Google token. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the provider. Cannot exceed 256 characters. |
| `--disabled` |  |  | Whether the provider is disabled. You cannot use a disabled provider to exchange tokens. However, existing tokens still grant access. |
| `--display-name` | DISPLAY_NAME |  | A display name for the provider. Cannot exceed 32 characters. |
| `--trust-store-config-path` | TRUST_STORE_CONFIG_PATH |  | YAML file with configuration metadata for the X.509 identity provider. Example file format: trustStore: trustAnchors: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" intermediateCas: - pemCertificate: "-----BEGIN CERTIFICATE----- <certificate> -----END CERTIFICATE-----" |


**Examples:**
```bash
The following command updates the X.509 workload identity pool provider
with the ID my-workload-identity-pool-provider. Explicit values for all
required and optional parameters are provided:

    $ gcloud iam workload-identity-pools providers update-x509 \
        my-workload-identity-pool-provider --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --display-name="My workload pool provider" \
        --description="My workload pool provider description" \
        --disabled --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --trust-store-config-path="path/to/config/file.yaml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/update-x509)

---

## `gcloud iam workload-identity-pools providers keys` — manage IAM workload identity pool provider keys
### `gcloud iam workload-identity-pools providers keys create`

Create a new workload identity pool provider key

Create a new workload identity pool provider key.

**Synopsis:**
```
gcloud iam workload-identity-pools providers keys create
    (KEY : --location=LOCATION
      --provider=PROVIDER --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    --spec=SPEC --use=USE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider key resource - The workload identity pool
provider key to create. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the workload identity pool provider key or fully qualified
     identifier for the workload identity pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID for the provider, which becomes the final component of the
     resource name. This value must be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spec` | one of: key-spec-unspecified, rsa-2048, rsa-3072, rsa-4096 |  | The specifications for the key. SPEC must be one of: key-spec-unspecified, rsa-2048, rsa-3072, rsa-4096. |
| `--use` | one of: encryption, key-use-unspecified |  | The purpose of the key. USE must be one of: encryption, key-use-unspecified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command creates a workload identity pool provider key in the
default project with the ID my-key. Explicit values for all required and
optional parameters are provided.

    $ gcloud iam workload-identity-pools providers keys create my-key \
        --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --provider="my-provider" --use="ENCRYPTION" --spec="RSA_4096"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/keys/create)

---
### `gcloud iam workload-identity-pools providers keys delete`

Delete a workload identity pool provider key

Delete a workload identity pool provider key.

**Synopsis:**
```
gcloud iam workload-identity-pools providers keys delete
    (KEY : --location=LOCATION
      --provider=PROVIDER --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider key resource - The workload identity pool
provider key to delete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the workload identity pool provider key or fully qualified
     identifier for the workload identity pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID for the provider, which becomes the final component of the
     resource name. This value must be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workload identity pool provider key in the
default project with the ID my-key.

    $ gcloud iam workload-identity-pools providers keys delete my-key \
        --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --provider="my-provider"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/keys/delete)

---
### `gcloud iam workload-identity-pools providers keys describe`

Describe a workload identity pool provider key

Describe a workload identity pool provider key.

**Synopsis:**
```
gcloud iam workload-identity-pools providers keys describe
    (KEY : --location=LOCATION
      --provider=PROVIDER --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider key resource - The workload identity pool
provider key to describe. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the workload identity pool provider key or fully qualified
     identifier for the workload identity pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID for the provider, which becomes the final component of the
     resource name. This value must be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes a workload identity pool provider key in
the default project with the ID my-key.

    $ gcloud iam workload-identity-pools providers keys describe \
        my-key --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --provider="my-provider"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/keys/describe)

---
### `gcloud iam workload-identity-pools providers keys list`

List workload identity pool provider keys

List workload identity pool provider keys.

**Synopsis:**
```
gcloud iam workload-identity-pools providers keys list
    (--provider=PROVIDER : --location=LOCATION
      --workload-identity-pool=WORKLOAD_IDENTITY_POOL) [--show-deleted]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--provider` | PROVIDER |  | _[This must be specified.]_ ID of the workload identity pool provider or fully qualified identifier for the workload identity pool provider. To set the provider attribute: + provide the argument --provider on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location name. To set the location attribute: + provide the argument --provider on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--workload-identity-pool` | WORKLOAD_IDENTITY_POOL |  | _[This must be specified.]_ The ID to use for the pool, which becomes the final component of the resource name. This value should be 4-32 characters, and may contain the characters [a-z0-9-]. The prefix gcp- is reserved for use by Google, and may not be specified. To set the workload-identity-pool attribute: + provide the argument --provider on the command line with a fully specified name; + provide the argument --workload-identity-pool on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Whether to return soft-deleted resources. |


**Examples:**
```bash
The following command lists all keys in the workload identity pool
provider, including soft-deleted keys:

    $ gcloud iam workload-identity-pools providers keys list \
        --workload-identity-pool="my-workload-identity-pool" \
        --provider="my-provider" --location="global" --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/keys/list)

---
### `gcloud iam workload-identity-pools providers keys undelete`

Undelete a workload identity pool provider key

Undelete a workload identity pool provider key.

**Synopsis:**
```
gcloud iam workload-identity-pools providers keys undelete
    (KEY : --location=LOCATION
      --provider=PROVIDER --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider key resource - The workload identity pool
provider key to undelete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the workload identity pool provider key or fully qualified
     identifier for the workload identity pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID for the provider, which becomes the final component of the
     resource name. This value must be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workload identity pool provider key in
the default project with the ID my-key.

    $ gcloud iam workload-identity-pools providers keys undelete \
        my-key --location="global" \
        --workload-identity-pool="my-workload-identity-pool" \
        --provider="my-provider"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/keys/undelete)

---

## `gcloud iam workload-identity-pools providers keys operations` — manage IAM workload identity pool provider key long running operations
### `gcloud iam workload-identity-pools providers keys operations describe`

Describe a workload identity pool provider key operation

Describe a workload identity pool provider key operation.

**Synopsis:**
```
gcloud iam workload-identity-pools providers keys operations describe
    (OPERATION : --key=KEY --location=LOCATION
      --provider=PROVIDER --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider key operation resource - The workload
identity pool provider key long-running operation to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the workload identity pool provider key operation or fully
     qualified identifier for the workload identity pool provider key
     operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --key=KEY
     The ID for the key, which becomes the final component of the resource
     name. This value must be 4-32 characters, and may contain the
     characters [a-z0-9-]. The prefix gcp- is reserved for use by Google,
     and may not be specified.

     To set the key attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --key on the command line.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID for the provider, which becomes the final component of the
     resource name. This value must be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
To describe the long-running workload identity pool provider key operation
with the ID my-operation, run:

    $ gcloud iam workload-identity-pools providers keys operations \
        describe my-operation --workload-identity-pool="my-pool" \
        --provider="my-provider" --key="my-key" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/keys/operations/describe)

---

## `gcloud iam workload-identity-pools providers operations` — manage IAM workload identity pool provider long running operations
### `gcloud iam workload-identity-pools providers operations describe`

Describe a workload identity pool provider operation

Describe a workload identity pool provider operation.

**Synopsis:**
```
gcloud iam workload-identity-pools providers operations describe
    (OPERATION : --location=LOCATION
      --provider=PROVIDER --workload-identity-pool=WORKLOAD_IDENTITY_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload identity pool provider operation resource - The workload identity
pool provider long running operation to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the workload identity pool provider operation or fully
     qualified identifier for the workload identity pool provider
     operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID for the provider, which becomes the final component of the
     resource name. This value must be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workload-identity-pool=WORKLOAD_IDENTITY_POOL
     The ID to use for the pool, which becomes the final component of the
     resource name. This value should be 4-32 characters, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the workload-identity-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workload-identity-pool on the command
       line.
```

**Examples:**
```bash
The following command describes the long running workload identity pool
provider operation with the ID my-operation:

    $ gcloud iam workload-identity-pools providers operations describe \
        my-operation \
        --workload-identity-pool="my-workload-identity-pool" \
        --provider="my-provider" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workload-identity-pools/providers/operations/describe)

---
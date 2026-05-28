# gcloud iam workforce-pools

create and manage workforce pools

### `gcloud iam workforce-pools create`

Create a new workforce pool under an organization

Creates a workforce pool under an organization given a valid organization
ID.

**Synopsis:**
```
gcloud iam workforce-pools create (WORKFORCE_POOL : --location=LOCATION)
    --organization=ORGANIZATION [--allowed-services=[domain=DOMAIN]]
    [--async] [--description=DESCRIPTION] [--disable-programmatic-signin]
    [--disabled] [--display-name=DISPLAY_NAME]
    [--session-duration=SESSION_DURATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool to create. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | The parent organization of the workforce pool to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-services` | [domain=DOMAIN] |  | Services allowed for web sign-in with the workforce pool. The flag accepts multiple values with the key as domain and value as the domain of the service allowed for web sign-in. If not set, by default all the services are allowed. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description for the workforce pool. Cannot exceed 256 characters in length. |
| `--disable-programmatic-signin` |  |  | Disable programmatic sign-in for workforce pool users. |
| `--disabled` |  |  | Whether or not the workforce pool is disabled. |
| `--display-name` | DISPLAY_NAME |  | A display name for the workforce pool. Cannot exceed 32 characters in length. |
| `--session-duration` | SESSION_DURATION |  | How long the Google Cloud access tokens, console sign-in sessions, and gcloud sign-in sessions from this workforce pool are valid. Must be greater than 15 minutes (900s) and less than 12 hours (43200s). If not configured, minted credentials will have a default duration of one hour (3600s). |


**Examples:**
```bash
The following command creates a workforce pool with ID my-workforce-pool in
the organization 12345:

    $ gcloud iam workforce-pools create my-workforce-pool \
        --organization=12345

The following command creates a workforce pool with ID my-workforce-pool
with explicit values for all required and optional parameters:

    $ gcloud iam workforce-pools create my-workforce-pool \
        --organization=12345 --location=global \
        --display-name="My Workforce Pool" \
        --description="My workforce pool
    description." --session-duration="7200s" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/create)

---
### `gcloud iam workforce-pools create-cred-config`

Create a configuration file for generated credentials

This command creates a configuration file to allow access to authenticated
Google Cloud actions from a variety of external user accounts.

**Synopsis:**
```
gcloud iam workforce-pools create-cred-config AUDIENCE
    --output-file=OUTPUT_FILE
    --workforce-pool-user-project=WORKFORCE_POOL_USER_PROJECT
    (--credential-source-file=CREDENTIAL_SOURCE_FILE
      | --credential-source-url=CREDENTIAL_SOURCE_URL
      | --executable-command=EXECUTABLE_COMMAND)
    [--credential-source-field-name=CREDENTIAL_SOURCE_FIELD_NAME]
    [--credential-source-headers=[key=value,...]]
    [--credential-source-type=CREDENTIAL_SOURCE_TYPE]
    [--subject-token-type=SUBJECT_TOKEN_TYPE]
    [--executable-interactive-timeout-millis=EXECUTABLE_INTERACTIVE_TIMEOUT_MILLIS --executable-output-file=EXECUTABLE_OUTPUT_FILE --executable-timeout-millis=EXECUTABLE_TIMEOUT_MILLIS]
    [--service-account=SERVICE_ACCOUNT
      : --service-account-token-lifetime-seconds=SERVICE_ACCOUNT_TOKEN_LIFETIME_SECONDS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AUDIENCE
   The workforce pool provider resource name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | Location to store the generated credential configuration file. |
| `--workforce-pool-user-project` | WORKFORCE_POOL_USER_PROJECT |  | The client project number used to identify the application (client project) to the server when calling Google APIs. The user principal must have serviceusage.services.use IAM permission to use the specified project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--credential-source-field-name` | CREDENTIAL_SOURCE_FIELD_NAME |  | Subject token field name (key) in a JSON credential source. |
| `--credential-source-headers` | [key=value,...] |  | Headers to use when querying the credential-source-url. |
| `--credential-source-type` | CREDENTIAL_SOURCE_TYPE |  | Format of the credential source (JSON or text). |
| `--subject-token-type` | SUBJECT_TOKEN_TYPE |  | The type of token being used for authorization. This defaults to urn:ietf:params:oauth:token-type:id_token. |


**Examples:**
```bash
To create a file-sourced credential configuration for your project, run:

    $ gcloud iam workforce-pools create-cred-config \
        locations/$REGION/workforcePools/$WORKFORCE_POOL_ID/providers/\
    $PROVIDER_ID --credential-source-file=$PATH_TO_OIDC_ID_TOKEN \
        --workforce-pool-user-project=$PROJECT_NUMBER \
        --output-file=credentials.json

To create a URL-sourced credential configuration for your project, run:

    $ gcloud iam workforce-pools create-cred-config \
        locations/$REGION/workforcePools/$WORKFORCE_POOL_ID/providers/\
    $PROVIDER_ID --credential-source-url=$URL_FOR_OIDC_TOKEN \
        --credential-source-headers=Key=Value \
        --workforce-pool-user-project=$PROJECT_NUMBER \
        --output-file=credentials.json

To create an executable-source credential configuration for your project,
run the following command:

    $ gcloud iam workforce-pools create-cred-config \
        locations/$REGION/workforcePools/$WORKFORCE_POOL_ID/providers/\
    $PROVIDER_ID --executable-command=$EXECUTABLE_COMMAND \
        --executable-timeout-millis=30000 \
        --executable-output-file=$CACHE_FILE \
        --workforce-pool-user-project=$PROJECT_NUMBER \
        --output-file=credentials.json

To use the resulting file for any of these commands, set the
GOOGLE_APPLICATION_CREDENTIALS environment variable to point to the
generated file.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/create-cred-config)

---
### `gcloud iam workforce-pools create-login-config`

Create a login configuration file to enable sign-in via a web-based authorization flow using Workforce Identity Federation

This command creates a configuration file to enable browser based
third-party sign in with Workforce Identity Federation through gcloud auth
login --login-config=/path/to/config.json.

**Synopsis:**
```
gcloud iam workforce-pools create-login-config AUDIENCE
    --output-file=OUTPUT_FILE [--activate] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AUDIENCE
   Workforce pool provider resource name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-file` | OUTPUT_FILE |  | Location to store the generated login configuration file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activate` |  |  | Sets the property auth/login_config_file to the created login configuration file. Calling gcloud auth login will automatically use this login configuration unless it is explicitly unset. |


**Examples:**
```bash
To create a login configuration for your project, run:

    $ gcloud iam workforce-pools create-login-config \
        locations/global/workforcePools/$WORKFORCE_POOL_ID/providers/\
    $PROVIDER_ID --output-file=login-config.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/create-login-config)

---
### `gcloud iam workforce-pools delete`

Delete a workforce pool

Delete a workforce pool.

**Synopsis:**
```
gcloud iam workforce-pools delete (WORKFORCE_POOL : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool to delete. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workforce pool with ID my-workforce-pool:

    $ gcloud iam workforce-pools delete my-workforce-pool \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/delete)

---
### `gcloud iam workforce-pools describe`

Describe a workforce pool

Describe a workforce pool.

**Synopsis:**
```
gcloud iam workforce-pools describe (WORKFORCE_POOL : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool to describe. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command describes a workforce pool with ID my-workforce-pool:

    $ gcloud iam workforce-pools describe my-workforce-pool \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/describe)

---
### `gcloud iam workforce-pools get-iam-policy`

Get the IAM policy for a workforce pool

Get the IAM policy for a workforce pool.

**Synopsis:**
```
gcloud iam workforce-pools get-iam-policy
    (WORKFORCE_POOL : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command gets the IAM policy for the workforce pool with ID
my-workforce-pool:

    $ gcloud iam workforce-pools get-iam-policy my-workforce-pool \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/get-iam-policy)

---
### `gcloud iam workforce-pools list`

List the workforce pools for an organization

Lists all of the workforce pools for an organization given a valid
organization ID.

This command can fail for the following reasons:
  o The organization specified does not exist.
  o The active account does not have permission to access the
    organization.

**Synopsis:**
```
gcloud iam workforce-pools list --location=LOCATION
    --organization=ORGANIZATION [--show-deleted] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location of the workforce pools to list. |
| `--organization` | ORGANIZATION |  | The parent organization of the workforce pools to list. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Show soft-deleted workforce pools by specifying this flag. |


**Examples:**
```bash
The following command lists the workforce pools for an organization with
the ID 12345, including soft-deleted pools:

    $ gcloud iam workforce-pools list --organization=12345 \
        --location=global --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/list)

---
### `gcloud iam workforce-pools set-iam-policy`

Set the IAM policy for a workforce pool

Set the IAM policy for a workforce pool.

**Synopsis:**
```
gcloud iam workforce-pools set-iam-policy
    (WORKFORCE_POOL : --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
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
The following command reads an IAM policy defined in a JSON file
policy.json and sets it for the workforce pool with ID my-workforce-pool:

    $ gcloud iam workforce-pools set-iam-policy my-workforce-pool \
        policy.json --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/set-iam-policy)

---
### `gcloud iam workforce-pools undelete`

Undelete a workforce pool

Undelete a workforce pool.

**Synopsis:**
```
gcloud iam workforce-pools undelete (WORKFORCE_POOL : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool to undelete. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workforce pool with ID my-workforce-pool:

    $ gcloud iam workforce-pools undelete my-workforce-pool \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/undelete)

---
### `gcloud iam workforce-pools update`

Update a workforce pool

Update a workforce pool.

**Synopsis:**
```
gcloud iam workforce-pools update (WORKFORCE_POOL : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--disable-programmatic-signin]
    [--disabled] [--display-name=DISPLAY_NAME]
    [--session-duration=SESSION_DURATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool resource - The workforce pool to update. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  WORKFORCE_POOL
     ID of the workforce pool or fully qualified identifier for the
     workforce pool.

     To set the workforce_pool attribute:
     + provide the argument workforce_pool on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument workforce_pool on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description for the workforce pool. Cannot exceed 256 characters in length. |
| `--disable-programmatic-signin` |  |  | Disables the programmatic sign-in for workforce pool users. Specify --no-disable-security-token-exchange to enable programmatic sign-in. For more information, refer to Obtain short-lived tokens for workforce identity federation at https://cloud.google.com/iam/docs/workforce-obtaining-short-lived-credentials |
| `--disabled` |  |  | Disables the workforce pool. You cannot use a disabled workforce pool to perform new token exchanges or sign-ins using any provider in the workforce pool. Specify --no-disabled to enable a disabled pool. |
| `--display-name` | DISPLAY_NAME |  | A display name for the workforce pool. Cannot exceed 32 characters in length. |
| `--session-duration` | SESSION_DURATION |  | How long the Google Cloud access tokens, console sign-in sessions, and gcloud sign-in sessions from this workforce pool are valid. Must be greater than 15 minutes (900s) and less than 12 hours (43200s). If not configured, minted credentials will have a default duration of one hour (3600s). |


**Examples:**
```bash
The following command updates a workforce pool with ID my-workforce-pool
with explicit values for all required and optional parameters:

    $ gcloud iam workforce-pools update my-workforce-pool \
        --location=global --display-name="My Workforce Pool" \
        --description="My workforce pool description." \
        --session-duration="7200s" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/update)

---

## `gcloud iam workforce-pools operations` — manage IAM workforce pool long-running operations
### `gcloud iam workforce-pools operations describe`

Describe a workforce pool operation

Describe a workforce pool operation.

**Synopsis:**
```
gcloud iam workforce-pools operations describe
    (OPERATION : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool operation resource - The workforce pool long-running
operation to describe. The arguments in this group can be used to specify
the attributes of this resource.

This must be specified.

  OPERATION
     ID of the workforce pool operation or fully qualified identifier for
     the workforce pool operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To describe the long-running workforce pool operation with the ID
my-operation, run:

    $ gcloud iam workforce-pools operations describe my-operation \
        --workforce-pool="my-workforce-pool" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/operations/describe)

---

## `gcloud iam workforce-pools providers` — create and manage workforce pool providers
### `gcloud iam workforce-pools providers create-oidc`

Create a new OIDC workforce pool provider

Create a new OIDC workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers create-oidc
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    --attribute-mapping=[KEY=VALUE,...] --client-id=CLIENT_ID
    --issuer-uri=ISSUER_URI
    (--web-sso-assertion-claims-behavior=WEB_SSO_ASSERTION_CLAIMS_BEHAVIOR
      --web-sso-response-type=WEB_SSO_RESPONSE_TYPE
      : --web-sso-additional-scopes=[WEB_SSO_ADDITIONAL_SCOPES,...])
    [--async] [--attribute-condition=ATTRIBUTE_CONDITION]
    [--client-secret-value=CLIENT_SECRET_VALUE] [--description=DESCRIPTION]
    [--detailed-audit-logging] [--disabled] [--display-name=DISPLAY_NAME]
    [--jwk-json-path=PATH_TO_FILE] [--scim-usage=SCIM_USAGE]
    [--extended-attributes-client-id=EXTENDED_ATTRIBUTES_CLIENT_ID
      --extended-attributes-client-secret-value=EXTENDED_ATTRIBUTES_CLIENT_SECRET_VALUE --extended-attributes-issuer-uri=EXTENDED_ATTRIBUTES_ISSUER_URI --extended-attributes-type=EXTENDED_ATTRIBUTES_TYPE : --extended-attributes-filter=EXTENDED_ATTRIBUTES_FILTER]
    [--extra-attributes-client-id=EXTRA_ATTRIBUTES_CLIENT_ID
      --extra-attributes-client-secret-value=EXTRA_ATTRIBUTES_CLIENT_SECRET_VALUE --extra-attributes-issuer-uri=EXTRA_ATTRIBUTES_ISSUER_URI --extra-attributes-type=EXTRA_ATTRIBUTES_TYPE : --extra-attributes-filter=EXTRA_ATTRIBUTES_FILTER]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to create.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps claims from the authentication credentials issued by the Identity Provider into Google Cloud IAM attributes, e.g. subject, segment. Each key must be a string specifying the Google Cloud IAM attribute to be produced. The following predefined keys are currently supported: * google.subject: required field that indicates the principal that is being authenticated to IAM, and will be logged in all API accesses for which Cloud Audit Logging is configured. * google.groups: optional field that indicates asserted groups that the user should be considered to belong to. You can create IAM bindings using the groups attribute and access to a resource will be granted if any of the groups asserted here match a group in the respective binding. * google.display_name: optional field that overrides the name of the user. If not set, google.subject will be displayed instead. This attribute cannot be used in IAM policies. The maximum length of this field is 100 characters. * google.profile_photo: optional fields that may be set to a valid URL specifying the user's thumbnail photo. When set, the image will be visible as the user's profile picture. If not set, a generic user icon will be displayed instead. This attribute cannot be used in IAM policies. Custom attributes can also be mapped by specifying attribute.{custom_attribute}, replacing {custom_attribute} with the name of the custom attribute to be mapped. A maximum of 50 custom attribute mappings can be defined. The maximum length of a mapped attribute key is 2048 characters and may only contain the characters [a-z0-9]. These attributes can then be referenced in IAM policies to define fine-grained access for the workforce pool to Google Cloud resources by specifying: * google.subject: principal://iam.googleapis.com/locations/global/workforcePools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an Identity Provider credential to the normalized attribute specified by the corresponding map key. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Identity Provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. Example: Map the sub claim of the incoming credential to the subject Google Cloud IAM attribute. {"google.subject": "assertion.sub"} |
| `--client-id` | CLIENT_ID |  | The OIDC client ID. This must match the audience claim of the JWT issued by the identity provider. |
| `--issuer-uri` | ISSUER_URI |  | The OIDC issuer URI. Must be a valid URI using the 'https' scheme. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict which otherwise valid authentication credentials issued by the provider should be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. google.profile_photo and google.display_name are not supported. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential will be accepted. Example: Only allow credentials with a mapped google.groups value of admins. "'admins' in google.groups" |
| `--client-secret-value` | CLIENT_SECRET_VALUE |  | The OIDC client secret. Required to enable Authorization Code flow for web sign-in. |
| `--description` | DESCRIPTION |  | A description for the workforce pool provider. Cannot exceed 256 characters in length. |
| `--detailed-audit-logging` |  |  | Enables detailed audit logging for this provider, which populates additional debug information in STS Cloud Audit Logs. Specify --no-detailed-audit-logging to disable it. |
| `--disabled` |  |  | Disables the workforce pool provider. You cannot use a disabled provider to perform new token exchanges or sign-ins. However, existing tokens still grant access. Specify --no-disabled to enable a disabled pool. |
| `--display-name` | DISPLAY_NAME |  | A display name for the workforce pool provider. Cannot exceed 32 characters in length. |
| `--jwk-json-path` | PATH_TO_FILE |  | Optional file containing JSON Web Key (JWK) public keys. The file format must follow JWK specifications (https://www.rfc-editor.org/rfc/rfc7517#section-4). Example file format: { "keys": [ { "kty": "RSA/EC", "alg": "<algorithm>", "use": "sig", "kid": "<key-id>", "n": "", "e": "", "x": "", "y": "", "crv": "" } ] } . Use a full or relative path to a local file containing the value of jwk_json_path. |
| `--scim-usage` | one of: enabled-for-groups, scim-usage-unspecified |  | Specifies whether the workforce identity pool provider uses SCIM-managed groups instead of the google.groups attribute mapping for authorization checks. The scim_usage and extended_attributes_oauth2_client fields are mutually exclusive. A request that enables both fields on the same workforce identity pool provider will produce an error. Use enabled-for-groups to enable SCIM-managed groups. Use scim-usage-unspecified to disable SCIM-managed groups. SCIM_USAGE must be one of: enabled-for-groups, scim-usage-unspecified. |
| `--extended-attributes-client-id` | EXTENDED_ATTRIBUTES_CLIENT_ID |  | The OAuth 2.0 client ID for retrieving extended attributes from the identity provider. Required to get extended group memberships for a subset of Google Cloud products. |
| `--extended-attributes-client-secret-value` | EXTENDED_ATTRIBUTES_CLIENT_SECRET_VALUE |  | The OAuth 2.0 client secret for retrieving extended attributes from the identity provider. Required to get extended group memberships for a subset of Google Cloud products. |
| `--extended-attributes-issuer-uri` | EXTENDED_ATTRIBUTES_ISSUER_URI |  | OIDC identity provider's issuer URI. Must be a valid URI using the https scheme. Required to get the OIDC discovery document. |
| `--extended-attributes-type` | EXTENDED_ATTRIBUTES_TYPE |  | Represents the identity provider and type of claims that should be fetched. EXTENDED_ATTRIBUTES_TYPE must be (only one value is supported): azure-ad-groups-id. |
| `--extended-attributes-filter` | EXTENDED_ATTRIBUTES_FILTER |  | The filter used to request specific records from the IdP. By default, all of the groups that are associated with a user are fetched. For Microsoft Entra ID, you can add $search query parameters using [Keyword Query Language] (https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference). To learn more about $search querying in Microsoft Entra ID, see [Use the $search query parameter] (https://learn.microsoft.com/en-us/graph/search-query-parameter). Additionally, Workforce Identity Federation automatically adds the following [$filter query parameters] (https://learn.microsoft.com/en-us/graph/filter-query-parameter), based on the value of attributes_type. Values passed to filter are converted to $search query parameters. Additional $filter query parameters cannot be added using this field. * AZURE_AD_GROUPS_ID: securityEnabled filter is applied. |
| `--extra-attributes-client-id` | EXTRA_ATTRIBUTES_CLIENT_ID |  | The OAuth 2.0 client ID for retrieving extra attributes from the identity provider. Required to get the access token using client credentials grant flow. |
| `--extra-attributes-client-secret-value` | EXTRA_ATTRIBUTES_CLIENT_SECRET_VALUE |  | The OAuth 2.0 client secret for retrieving extra attributes from the identity provider. Required to get the access token using client credentials grant flow. |
| `--extra-attributes-issuer-uri` | EXTRA_ATTRIBUTES_ISSUER_URI |  | OIDC identity provider's issuer URI. Must be a valid URI using the https scheme. Required to get the OIDC discovery document. |
| `--extra-attributes-type` | one of: azure-ad-groups-mail, azure-ad-groups-id |  | Represents the identity provider and type of claims that should be fetched. EXTRA_ATTRIBUTES_TYPE must be one of: azure-ad-groups-mail, azure-ad-groups-id. |
| `--extra-attributes-filter` | EXTRA_ATTRIBUTES_FILTER |  | The filter used to request specific records from the IdP. By default, all of the groups that are associated with a user are fetched. For Microsoft Entra ID, you can add $search query parameters using [Keyword Query Language] (https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference). To learn more about $search querying in Microsoft Entra ID, see [Use the $search query parameter] (https://learn.microsoft.com/en-us/graph/search-query-parameter). Additionally, Workforce Identity Federation automatically adds the following [$filter query parameters] (https://learn.microsoft.com/en-us/graph/filter-query-parameter), based on the value of attributes_type. Values passed to filter are converted to $search query parameters. Additional $filter query parameters cannot be added using this field. * AZURE_AD_GROUPS_MAIL: mailEnabled and securityEnabled filters are applied. * AZURE_AD_GROUPS_ID: securityEnabled filter is applied. |


**Examples:**
```bash
The following command creates a disabled OIDC workforce pool provider with
the ID my-workforce-pool-provider. Explicit values for all required and
optional parameters are provided.

    $ gcloud iam workforce-pools providers create-oidc \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global" \
        --display-name="My Workforce Pool Provider" \
        --description="My workforce pool provider description." \
        --disabled --detailed-audit-logging \
        --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" --client-id="client-id" \
        --client-secret-value="client-secret" \
        --issuer-uri="https://test-idp.com" \
        --web-sso-response-type="code" \
        --web-sso-assertion-claims-behavior="merge-user-info-over-id-tok\
    en-claims" --web-sso-additional-scopes="groups,photos" \
        --jwk-json-path="path/to/jwk.json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/create-oidc)

---
### `gcloud iam workforce-pools providers create-saml`

Create a new SAML workforce pool provider

Create a new SAML workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers create-saml
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    --attribute-mapping=[KEY=VALUE,...] --idp-metadata-path=PATH_TO_FILE
    [--async] [--attribute-condition=ATTRIBUTE_CONDITION]
    [--description=DESCRIPTION] [--detailed-audit-logging] [--disabled]
    [--display-name=DISPLAY_NAME] [--scim-usage=SCIM_USAGE]
    [--extended-attributes-client-id=EXTENDED_ATTRIBUTES_CLIENT_ID
      --extended-attributes-client-secret-value=EXTENDED_ATTRIBUTES_CLIENT_SECRET_VALUE --extended-attributes-issuer-uri=EXTENDED_ATTRIBUTES_ISSUER_URI --extended-attributes-type=EXTENDED_ATTRIBUTES_TYPE : --extended-attributes-filter=EXTENDED_ATTRIBUTES_FILTER]
    [--extra-attributes-client-id=EXTRA_ATTRIBUTES_CLIENT_ID
      --extra-attributes-client-secret-value=EXTRA_ATTRIBUTES_CLIENT_SECRET_VALUE --extra-attributes-issuer-uri=EXTRA_ATTRIBUTES_ISSUER_URI --extra-attributes-type=EXTRA_ATTRIBUTES_TYPE : --extra-attributes-filter=EXTRA_ATTRIBUTES_FILTER]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to create.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps claims from the authentication credentials issued by the Identity Provider into Google Cloud IAM attributes, e.g. subject, segment. Each key must be a string specifying the Google Cloud IAM attribute to be produced. The following predefined keys are currently supported: * google.subject: required field that indicates the principal that is being authenticated to IAM, and will be logged in all API accesses for which Cloud Audit Logging is configured. * google.groups: optional field that indicates asserted groups that the user should be considered to belong to. You can create IAM bindings using the groups attribute and access to a resource will be granted if any of the groups asserted here match a group in the respective binding. * google.display_name: optional field that overrides the name of the user. If not set, google.subject will be displayed instead. This attribute cannot be used in IAM policies. The maximum length of this field is 100 characters. * google.profile_photo: optional fields that may be set to a valid URL specifying the user's thumbnail photo. When set, the image will be visible as the user's profile picture. If not set, a generic user icon will be displayed instead. This attribute cannot be used in IAM policies. Custom attributes can also be mapped by specifying attribute.{custom_attribute}, replacing {custom_attribute} with the name of the custom attribute to be mapped. A maximum of 50 custom attribute mappings can be defined. The maximum length of a mapped attribute key is 2048 characters and may only contain the characters [a-z0-9]. These attributes can then be referenced in IAM policies to define fine-grained access for the workforce pool to Google Cloud resources by specifying: * google.subject: principal://iam.googleapis.com/locations/global/workforcePools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an Identity Provider credential to the normalized attribute specified by the corresponding map key. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Identity Provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. Example: Map the sub claim of the incoming credential to the subject Google Cloud IAM attribute. {"google.subject": "assertion.sub"} |
| `--idp-metadata-path` | PATH_TO_FILE |  | XML file with configuration metadata for the SAML identity provider. The metadata file must follow the SAML 2.0 metadata specification (https://www.oasis-open.org/committees/download.php/35391/sstc-saml-metadata-errata-2.0-wd-04-diff.pdf). Use a full or relative path to a local file containing the value of idp_metadata_path. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict which otherwise valid authentication credentials issued by the provider should be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. google.profile_photo and google.display_name are not supported. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential will be accepted. Example: Only allow credentials with a mapped google.groups value of admins. "'admins' in google.groups" |
| `--description` | DESCRIPTION |  | A description for the workforce pool provider. Cannot exceed 256 characters in length. |
| `--detailed-audit-logging` |  |  | Enables detailed audit logging for this provider, which populates additional debug information in STS Cloud Audit Logs. Specify --no-detailed-audit-logging to disable it. |
| `--disabled` |  |  | Disables the workforce pool provider. You cannot use a disabled provider to perform new token exchanges or sign-ins. However, existing tokens still grant access. Specify --no-disabled to enable a disabled pool. |
| `--display-name` | DISPLAY_NAME |  | A display name for the workforce pool provider. Cannot exceed 32 characters in length. |
| `--scim-usage` | one of: enabled-for-groups, scim-usage-unspecified |  | Specifies whether the workforce identity pool provider uses SCIM-managed groups instead of the google.groups attribute mapping for authorization checks. The scim_usage and extended_attributes_oauth2_client fields are mutually exclusive. A request that enables both fields on the same workforce identity pool provider will produce an error. Use enabled-for-groups to enable SCIM-managed groups. Use scim-usage-unspecified to disable SCIM-managed groups. SCIM_USAGE must be one of: enabled-for-groups, scim-usage-unspecified. |
| `--extended-attributes-client-id` | EXTENDED_ATTRIBUTES_CLIENT_ID |  | The OAuth 2.0 client ID for retrieving extended attributes from the identity provider. Required to get extended group memberships for a subset of Google Cloud products. |
| `--extended-attributes-client-secret-value` | EXTENDED_ATTRIBUTES_CLIENT_SECRET_VALUE |  | The OAuth 2.0 client secret for retrieving extended attributes from the identity provider. Required to get extended group memberships for a subset of Google Cloud products. |
| `--extended-attributes-issuer-uri` | EXTENDED_ATTRIBUTES_ISSUER_URI |  | OIDC identity provider's issuer URI. Must be a valid URI using the https scheme. Required to get the OIDC discovery document. |
| `--extended-attributes-type` | EXTENDED_ATTRIBUTES_TYPE |  | Represents the identity provider and type of claims that should be fetched. EXTENDED_ATTRIBUTES_TYPE must be (only one value is supported): azure-ad-groups-id. |
| `--extended-attributes-filter` | EXTENDED_ATTRIBUTES_FILTER |  | The filter used to request specific records from the IdP. By default, all of the groups that are associated with a user are fetched. For Microsoft Entra ID, you can add $search query parameters using [Keyword Query Language] (https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference). To learn more about $search querying in Microsoft Entra ID, see [Use the $search query parameter] (https://learn.microsoft.com/en-us/graph/search-query-parameter). Additionally, Workforce Identity Federation automatically adds the following [$filter query parameters] (https://learn.microsoft.com/en-us/graph/filter-query-parameter), based on the value of attributes_type. Values passed to filter are converted to $search query parameters. Additional $filter query parameters cannot be added using this field. * AZURE_AD_GROUPS_ID: securityEnabled filter is applied. |
| `--extra-attributes-client-id` | EXTRA_ATTRIBUTES_CLIENT_ID |  | The OAuth 2.0 client ID for retrieving extra attributes from the identity provider. Required to get the access token using client credentials grant flow. |
| `--extra-attributes-client-secret-value` | EXTRA_ATTRIBUTES_CLIENT_SECRET_VALUE |  | The OAuth 2.0 client secret for retrieving extra attributes from the identity provider. Required to get the access token using client credentials grant flow. |
| `--extra-attributes-issuer-uri` | EXTRA_ATTRIBUTES_ISSUER_URI |  | OIDC identity provider's issuer URI. Must be a valid URI using the https scheme. Required to get the OIDC discovery document. |
| `--extra-attributes-type` | one of: azure-ad-groups-mail, azure-ad-groups-id |  | Represents the identity provider and type of claims that should be fetched. EXTRA_ATTRIBUTES_TYPE must be one of: azure-ad-groups-mail, azure-ad-groups-id. |
| `--extra-attributes-filter` | EXTRA_ATTRIBUTES_FILTER |  | The filter used to request specific records from the IdP. By default, all of the groups that are associated with a user are fetched. For Microsoft Entra ID, you can add $search query parameters using [Keyword Query Language] (https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference). To learn more about $search querying in Microsoft Entra ID, see [Use the $search query parameter] (https://learn.microsoft.com/en-us/graph/search-query-parameter). Additionally, Workforce Identity Federation automatically adds the following [$filter query parameters] (https://learn.microsoft.com/en-us/graph/filter-query-parameter), based on the value of attributes_type. Values passed to filter are converted to $search query parameters. Additional $filter query parameters cannot be added using this field. * AZURE_AD_GROUPS_MAIL: mailEnabled and securityEnabled filters are applied. * AZURE_AD_GROUPS_ID: securityEnabled filter is applied. |


**Examples:**
```bash
The following command creates a disabled SAML workforce pool provider with
the ID my-workforce-pool-provider. Explicit values for all required and
optional parameters are provided.

    $ gcloud iam workforce-pools providers create-saml \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global" \
        --display-name="My Workforce Pool Provider" \
        --description="My workforce pool provider description." \
        --disabled --detailed-audit-logging \
        --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --idp-metadata-path="path/to/metdata/file.xml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/create-saml)

---
### `gcloud iam workforce-pools providers delete`

Delete a workforce pool provider

Delete a workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers delete
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to delete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workforce pool provider with the ID
my-workforce-pool-provider:

    $ gcloud iam workforce-pools providers delete \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/delete)

---
### `gcloud iam workforce-pools providers describe`

Describe a workforce pool provider

Describe a workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers describe
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to
describe. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
The following command describes a workforce pool provider with the ID
my-workforce-pool-provider:

    $ gcloud iam workforce-pools providers describe \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/describe)

---
### `gcloud iam workforce-pools providers list`

List workforce pool providers

List workforce pool providers.

**Synopsis:**
```
gcloud iam workforce-pools providers list
    (--workforce-pool=WORKFORCE_POOL : --location=LOCATION)
    [--show-deleted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--workforce-pool` | WORKFORCE_POOL |  | _[This must be specified.]_ ID of the workforce pool or fully qualified identifier for the workforce pool. To set the workforce-pool attribute: + provide the argument --workforce-pool on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location for the workforce pool. To set the location attribute: + provide the argument --workforce-pool on the command line with a fully specified name; + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Show soft-deleted workforce pool providers by specifying this flag. |


**Examples:**
```bash
The following command lists the workforce pool providers in the workforce
pool with ID my-workforce-pool, including soft-deleted pools:

    $ gcloud iam workforce-pools providers list \
        --workforce-pool="my-workforce-pool" --location="global" \
        --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/list)

---
### `gcloud iam workforce-pools providers undelete`

Undelete a workforce pool provider

Undelete a workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers undelete
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to
undelete. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workforce pool provider with the ID
my-workforce-pool-provider:

    $ gcloud iam workforce-pools providers undelete \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/undelete)

---
### `gcloud iam workforce-pools providers update-oidc`

Update an OIDC workforce pool provider

Update an OIDC workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers update-oidc
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--async] [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--client-id=CLIENT_ID]
    [--description=DESCRIPTION] [--detailed-audit-logging] [--disabled]
    [--display-name=DISPLAY_NAME] [--issuer-uri=ISSUER_URI]
    [--jwk-json-path=PATH_TO_FILE] [--scim-usage=SCIM_USAGE]
    [--web-sso-additional-scopes=[WEB_SSO_ADDITIONAL_SCOPES,...]]
    [--web-sso-assertion-claims-behavior=WEB_SSO_ASSERTION_CLAIMS_BEHAVIOR]
    [--web-sso-response-type=WEB_SSO_RESPONSE_TYPE]
    [--clear-client-secret | --client-secret-value=CLIENT_SECRET_VALUE]
    [--clear-extended-attributes-config
      | --extended-attributes-client-id=EXTENDED_ATTRIBUTES_CLIENT_ID
      --extended-attributes-client-secret-value=EXTENDED_ATTRIBUTES_CLIENT_SECRET_VALUE --extended-attributes-filter=EXTENDED_ATTRIBUTES_FILTER --extended-attributes-issuer-uri=EXTENDED_ATTRIBUTES_ISSUER_URI --extended-attributes-type=EXTENDED_ATTRIBUTES_TYPE]
    [--clear-extra-attributes-config
      | --extra-attributes-client-id=EXTRA_ATTRIBUTES_CLIENT_ID
      --extra-attributes-client-secret-value=EXTRA_ATTRIBUTES_CLIENT_SECRET_VALUE --extra-attributes-filter=EXTRA_ATTRIBUTES_FILTER --extra-attributes-issuer-uri=EXTRA_ATTRIBUTES_ISSUER_URI --extra-attributes-type=EXTRA_ATTRIBUTES_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to update.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict which otherwise valid authentication credentials issued by the provider should be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. google.profile_photo and google.display_name are not supported. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential will be accepted. Example: Only allow credentials with a mapped google.groups value of admins. "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps claims from the authentication credentials issued by the Identity Provider into Google Cloud IAM attributes, e.g. subject, segment. Each key must be a string specifying the Google Cloud IAM attribute to be produced. The following predefined keys are currently supported: * google.subject: required field that indicates the principal that is being authenticated to IAM, and will be logged in all API accesses for which Cloud Audit Logging is configured. * google.groups: optional field that indicates asserted groups that the user should be considered to belong to. You can create IAM bindings using the groups attribute and access to a resource will be granted if any of the groups asserted here match a group in the respective binding. * google.display_name: optional field that overrides the name of the user. If not set, google.subject will be displayed instead. This attribute cannot be used in IAM policies. The maximum length of this field is 100 characters. * google.profile_photo: optional fields that may be set to a valid URL specifying the user's thumbnail photo. When set, the image will be visible as the user's profile picture. If not set, a generic user icon will be displayed instead. This attribute cannot be used in IAM policies. Custom attributes can also be mapped by specifying attribute.{custom_attribute}, replacing {custom_attribute} with the name of the custom attribute to be mapped. A maximum of 50 custom attribute mappings can be defined. The maximum length of a mapped attribute key is 2048 characters and may only contain the characters [a-z0-9]. These attributes can then be referenced in IAM policies to define fine-grained access for the workforce pool to Google Cloud resources by specifying: * google.subject: principal://iam.googleapis.com/locations/global/workforcePools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an Identity Provider credential to the normalized attribute specified by the corresponding map key. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Identity Provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. Example: Map the sub claim of the incoming credential to the subject Google Cloud IAM attribute. {"google.subject": "assertion.sub"} |
| `--client-id` | CLIENT_ID |  | The OIDC client ID. This must match the audience claim of the JWT issued by the identity provider. |
| `--description` | DESCRIPTION |  | A description for the workforce pool provider. Cannot exceed 256 characters in length. |
| `--detailed-audit-logging` |  |  | Enables detailed audit logging for this provider, which populates additional debug information in STS Cloud Audit Logs. Specify --no-detailed-audit-logging to disable it. |
| `--disabled` |  |  | Disables the workforce pool provider. You cannot use a disabled provider to perform new token exchanges or sign-ins. However, existing tokens still grant access. Specify --no-disabled to enable a disabled pool. |
| `--display-name` | DISPLAY_NAME |  | A display name for the workforce pool provider. Cannot exceed 32 characters in length. |
| `--issuer-uri` | ISSUER_URI |  | The OIDC issuer URI. Must be a valid URI using the 'https' scheme. |
| `--jwk-json-path` | PATH_TO_FILE |  | Optional file containing JSON Web Key (JWK) public keys. The file format must follow JWK specifications (https://www.rfc-editor.org/rfc/rfc7517#section-4). Example file format: { "keys": [ { "kty": "RSA/EC", "alg": "<algorithm>", "use": "sig", "kid": "<key-id>", "n": "", "e": "", "x": "", "y": "", "crv": "" } ] } . Use a full or relative path to a local file containing the value of jwk_json_path. |
| `--scim-usage` | one of: enabled-for-groups, scim-usage-unspecified |  | Specifies whether the workforce identity pool provider uses SCIM-managed groups instead of the google.groups attribute mapping for authorization checks. The scim_usage and extended_attributes_oauth2_client fields are mutually exclusive. A request that enables both fields on the same workforce identity pool provider will produce an error. Use enabled-for-groups to enable SCIM-managed groups. Use scim-usage-unspecified to disable SCIM-managed groups. SCIM_USAGE must be one of: enabled-for-groups, scim-usage-unspecified. |
| `--web-sso-additional-scopes` | [WEB_SSO_ADDITIONAL_SCOPES,...] |  | Additional scopes to request for the OIDC authentication on top of scopes requested by default. By default, the openid, profile and email scopes that are supported by the identity provider are requested. Each additional scope may be at most 256 characters. A maximum of 10 additional scopes may be configured. |
| `--web-sso-assertion-claims-behavior` | one of: assertion-claims-behavior-unspecified, merge-user-info-over-id-token-claims, only-id-token-claims |  | The behavior for how OIDC Claims are included in the assertion object used for attribute mapping and attribute condition. Use merge-user-info-over-id-token-claims to merge the UserInfo Endpoint Claims with ID Token Claims, preferring UserInfo Claim Values for the same Claim Name. Currently this option is only available for Authorization Code flow. Use only-id-token-claims to include only ID token claims. WEB_SSO_ASSERTION_CLAIMS_BEHAVIOR must be one of: assertion-claims-behavior-unspecified, merge-user-info-over-id-token-claims, only-id-token-claims. |
| `--web-sso-response-type` | one of: code, id-token, response-type-unspecified |  | Response Type to request for in the OIDC Authorization Request for web sign-in. Use code to select the authorization code flow (https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth) Use id-token to select the implicit flow (https://openid.net/specs/openid-connect-core-1_0.html#ImplicitFlowAuth). WEB_SSO_RESPONSE_TYPE must be one of: code, id-token, response-type-unspecified. |


**Examples:**
```bash
The following command updates the OIDC workforce pool provider with the ID
my-workforce-pool-provider in the workforce pool my-workforce-pool.
Explicit values for all required and optional parameters are provided:

    $ gcloud iam workforce-pools providers update-oidc \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global" \
        --display-name="My Workforce Pool Provider" \
        --description="My workforce pool provider description." \
        --disabled --detailed-audit-logging \
        --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" --client-id="client-id" \
        --client-secret-value="client-secret" \
        --issuer-uri="https://test-idp.com" \
        --web-sso-response-type="code" \
        --web-sso-assertion-claims-behavior="merge-user-info-over-id-tok\
    en-claims" --web-sso-additional-scopes="groups,photos" \
        --jwk-json-path="path/to/jwk.json"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/update-oidc)

---
### `gcloud iam workforce-pools providers update-saml`

Update a new SAML workforce pool provider

Update a new SAML workforce pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers update-saml
    (PROVIDER : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--async] [--attribute-condition=ATTRIBUTE_CONDITION]
    [--attribute-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--detailed-audit-logging] [--disabled] [--display-name=DISPLAY_NAME]
    [--idp-metadata-path=PATH_TO_FILE] [--scim-usage=SCIM_USAGE]
    [--clear-extended-attributes-config
      | --extended-attributes-client-id=EXTENDED_ATTRIBUTES_CLIENT_ID
      --extended-attributes-client-secret-value=EXTENDED_ATTRIBUTES_CLIENT_SECRET_VALUE --extended-attributes-filter=EXTENDED_ATTRIBUTES_FILTER --extended-attributes-issuer-uri=EXTENDED_ATTRIBUTES_ISSUER_URI --extended-attributes-type=EXTENDED_ATTRIBUTES_TYPE]
    [--clear-extra-attributes-config
      | --extra-attributes-client-id=EXTRA_ATTRIBUTES_CLIENT_ID
      --extra-attributes-client-secret-value=EXTRA_ATTRIBUTES_CLIENT_SECRET_VALUE --extra-attributes-filter=EXTRA_ATTRIBUTES_FILTER --extra-attributes-issuer-uri=EXTRA_ATTRIBUTES_ISSUER_URI --extra-attributes-type=EXTRA_ATTRIBUTES_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider resource - The workforce pool provider to update.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PROVIDER
     ID of the workforce pool provider or fully qualified identifier for
     the workforce pool provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--attribute-condition` | ATTRIBUTE_CONDITION |  | A Common Expression Language (https://opensource.google/projects/cel) expression, in plain text, to restrict which otherwise valid authentication credentials issued by the provider should be accepted. The expression must output a boolean representing whether to allow the federation. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Provider. * google: The Google attributes mapped from the assertion in the attribute_mappings. google.profile_photo and google.display_name are not supported. * attribute: The custom attributes mapped from the assertion in the attribute_mappings. The maximum length of the attribute condition expression is 4096 characters. If unspecified, all valid authentication credential will be accepted. Example: Only allow credentials with a mapped google.groups value of admins. "'admins' in google.groups" |
| `--attribute-mapping` | [KEY=VALUE,...] |  | Maps claims from the authentication credentials issued by the Identity Provider into Google Cloud IAM attributes, e.g. subject, segment. Each key must be a string specifying the Google Cloud IAM attribute to be produced. The following predefined keys are currently supported: * google.subject: required field that indicates the principal that is being authenticated to IAM, and will be logged in all API accesses for which Cloud Audit Logging is configured. * google.groups: optional field that indicates asserted groups that the user should be considered to belong to. You can create IAM bindings using the groups attribute and access to a resource will be granted if any of the groups asserted here match a group in the respective binding. * google.display_name: optional field that overrides the name of the user. If not set, google.subject will be displayed instead. This attribute cannot be used in IAM policies. The maximum length of this field is 100 characters. * google.profile_photo: optional fields that may be set to a valid URL specifying the user's thumbnail photo. When set, the image will be visible as the user's profile picture. If not set, a generic user icon will be displayed instead. This attribute cannot be used in IAM policies. Custom attributes can also be mapped by specifying attribute.{custom_attribute}, replacing {custom_attribute} with the name of the custom attribute to be mapped. A maximum of 50 custom attribute mappings can be defined. The maximum length of a mapped attribute key is 2048 characters and may only contain the characters [a-z0-9]. These attributes can then be referenced in IAM policies to define fine-grained access for the workforce pool to Google Cloud resources by specifying: * google.subject: principal://iam.googleapis.com/locations/global/workforcePools/{pool}/subject/{value} * google.groups: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/group/{value} * attribute.{custom_attribute}: principalSet://iam.googleapis.com/locations/global/workforcePools/{pool}/attribute.{custom_attribute}/{value} Each value must be a Common Expression Language (https://opensource.google/projects/cel) function that maps an Identity Provider credential to the normalized attribute specified by the corresponding map key. The following keywords may be referenced in the expressions: * assertion: JSON representing the authentication credential issued by the Identity Provider. The maximum length of an attribute mapping expression is 2048 characters. When evaluated, the total size of all mapped attributes must not exceed 8KB. Example: Map the sub claim of the incoming credential to the subject Google Cloud IAM attribute. {"google.subject": "assertion.sub"} |
| `--description` | DESCRIPTION |  | A description for the workforce pool provider. Cannot exceed 256 characters in length. |
| `--detailed-audit-logging` |  |  | Enables detailed audit logging for this provider, which populates additional debug information in STS Cloud Audit Logs. Specify --no-detailed-audit-logging to disable it. |
| `--disabled` |  |  | Disables the workforce pool provider. You cannot use a disabled provider to perform new token exchanges or sign-ins. However, existing tokens still grant access. Specify --no-disabled to enable a disabled pool. |
| `--display-name` | DISPLAY_NAME |  | A display name for the workforce pool provider. Cannot exceed 32 characters in length. |
| `--idp-metadata-path` | PATH_TO_FILE |  | XML file with configuration metadata for the SAML identity provider. The metadata file must follow the SAML 2.0 metadata specification (https://www.oasis-open.org/committees/download.php/35391/sstc-saml-metadata-errata-2.0-wd-04-diff.pdf). Use a full or relative path to a local file containing the value of idp_metadata_path. |
| `--scim-usage` | one of: enabled-for-groups, scim-usage-unspecified |  | Specifies whether the workforce identity pool provider uses SCIM-managed groups instead of the google.groups attribute mapping for authorization checks. The scim_usage and extended_attributes_oauth2_client fields are mutually exclusive. A request that enables both fields on the same workforce identity pool provider will produce an error. Use enabled-for-groups to enable SCIM-managed groups. Use scim-usage-unspecified to disable SCIM-managed groups. SCIM_USAGE must be one of: enabled-for-groups, scim-usage-unspecified. |


**Examples:**
```bash
The following command updates the SAML workforce pool provider with the ID
my-workforce-pool-provider. Explicit values for all required and optional
parameters are provided.

    $ gcloud iam workforce-pools providers update-saml \
        my-workforce-pool-provider \
        --workforce-pool="my-workforce-pool" --location="global" \
        --display-name="My Workforce Pool Provider" \
        --description="My workforce pool provider description." \
        --disabled --detailed-audit-logging \
        --attribute-mapping="google.subject=assertion.sub" \
        --attribute-condition="true" \
        --idp-metadata-path="path/to/metdata/file.xml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/update-saml)

---

## `gcloud iam workforce-pools providers keys` — create and manage IAM workforce pool provider keys
### `gcloud iam workforce-pools providers keys create`

Create a new workforce pool provider key

Create a new workforce pool provider key.

**Synopsis:**
```
gcloud iam workforce-pools providers keys create
    (KEY : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL) --spec=SPEC
    --use=USE [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider key resource - The workforce pool provider key to
create. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  KEY
     ID of the workforce pool provider key or fully qualified identifier
     for the workforce pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spec` | one of: key-spec-unspecified, rsa-2048, rsa-3072, rsa-4096 |  | The specifications for the key. SPEC must be one of: key-spec-unspecified, rsa-2048, rsa-3072, rsa-4096. |
| `--use` | one of: encryption, key-use-unspecified, signing |  | The purpose of the key. USE must be one of: encryption, key-use-unspecified, signing. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command creates a workforce pool provider key with the ID
my-key. Explicit values for all required and optional parameters are
provided.

    $ gcloud iam workforce-pools providers keys create my-key \
        --location="global" --workforce-pool="my-workforce-pool" \
        --provider="my-provider" --use="ENCRYPTION" --spec="RSA_4096"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/keys/create)

---
### `gcloud iam workforce-pools providers keys delete`

Delete a workforce pool provider key

Delete a workforce pool provider key.

**Synopsis:**
```
gcloud iam workforce-pools providers keys delete
    (KEY : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider key resource - The workforce pool provider key to
delete. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  KEY
     ID of the workforce pool provider key or fully qualified identifier
     for the workforce pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workforce pool provider key with the ID
my-key.

    $ gcloud iam workforce-pools providers keys delete my-key \
        --location="global" --workforce-pool="my-workforce-pool" \
        --provider="my-provider"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/keys/delete)

---
### `gcloud iam workforce-pools providers keys describe`

Describe a workforce pool provider key

Describe a workforce pool provider key.

**Synopsis:**
```
gcloud iam workforce-pools providers keys describe
    (KEY : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider key resource - The workforce pool provider key to
describe. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  KEY
     ID of the workforce pool provider key or fully qualified identifier
     for the workforce pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
The following command describes a workforce pool provider key with the ID
my-key.

    $ gcloud iam workforce-pools providers keys describe my-key \
        --location="global" --workforce-pool="my-workforce-pool" \
        --provider="my-provider"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/keys/describe)

---
### `gcloud iam workforce-pools providers keys list`

List workforce pool provider keys

List workforce pool provider keys.

**Synopsis:**
```
gcloud iam workforce-pools providers keys list
    (--provider=PROVIDER
      : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--show-deleted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--provider` | PROVIDER |  | _[This must be specified.]_ ID of the workforce pool provider or fully qualified identifier for the workforce pool provider. To set the provider attribute: + provide the argument --provider on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location for the workforce pool. To set the location attribute: + provide the argument --provider on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--workforce-pool` | WORKFORCE_POOL |  | _[This must be specified.]_ The ID to use for the workforce pool, which becomes the final component of the resource name. This value must be a globally unique string of 6 to 63 lowercase letters, digits, or hyphens. It must start with a letter, and cannot have a trailing hyphen. The prefix gcp- is reserved for use by Google, and may not be specified. To set the workforce-pool attribute: + provide the argument --provider on the command line with a fully specified name; + provide the argument --workforce-pool on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Show soft-deleted keys by specifying this flag. |


**Examples:**
```bash
The following command lists the keys in the workforce pool provider with ID
my-provider, including soft-deleted keys:

    $ gcloud iam workforce-pools providers keys list \
        --workforce-pool="my-workforce-pool" --provider="my-provider" \
        --location="global" --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/keys/list)

---
### `gcloud iam workforce-pools providers keys undelete`

Undelete a workforce pool provider key

Undelete a workforce pool provider key.

**Synopsis:**
```
gcloud iam workforce-pools providers keys undelete
    (KEY : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider key resource - The workforce pool provider key to
undelete. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  KEY
     ID of the workforce pool provider key or fully qualified identifier
     for the workforce pool provider key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workforce pool provider key with the ID
my-key.

    $ gcloud iam workforce-pools providers keys undelete my-key \
        --location="global" --workforce-pool="my-workforce-pool" \
        --provider="my-provider"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/keys/undelete)

---

## `gcloud iam workforce-pools providers keys operations` — manage IAM workforce pool provider key long-running operations
### `gcloud iam workforce-pools providers keys operations describe`

Describe a workforce pool provider key operation

Describe a workforce pool provider key operation.

**Synopsis:**
```
gcloud iam workforce-pools providers keys operations describe
    (OPERATION : --key=KEY --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider key operation resource - The workforce pool
provider key long-running operation to describe. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  OPERATION
     ID of the workforce pool provider key operation or fully qualified
     identifier for the workforce pool provider key operation.

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
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To describe the long-running workforce pool provider key operation with the
ID my-operation, run:

    $ gcloud iam workforce-pools providers keys operations describe \
        my-operation --workforce-pool="my-workforce-pool" \
        --provider="my-provider" --key="my-key" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/keys/operations/describe)

---

## `gcloud iam workforce-pools providers operations` — manage IAM workforce pool provider long-running operations
### `gcloud iam workforce-pools providers operations describe`

Describe a workforce pool provider operation

Describe a workforce pool provider operation.

**Synopsis:**
```
gcloud iam workforce-pools providers operations describe
    (OPERATION : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider operation resource - The workforce pool provider
long-running operation to describe. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  OPERATION
     ID of the workforce pool provider operation or fully qualified
     identifier for the workforce pool provider operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To describe the long-running workforce pool provider operation with the ID
my-operation, run:

    $ gcloud iam workforce-pools providers operations describe \
        my-operation --workforce-pool="my-workforce-pool" \
        --provider="my-provider" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/operations/describe)

---

## `gcloud iam workforce-pools providers scim-tenants` — manage IAM workforce identity pool provider SCIM tenants
### `gcloud iam workforce-pools providers scim-tenants create`

Create an IAM workforce identity pool provider SCIM tenant

Create a new SCIM tenant associated with a specific workforce identity pool
provider.

Upon successful creation, the command returns the created SCIM tenant
resource.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants create
    (SCIM_TENANT : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    --claim-mapping=[KEY=VALUE,...] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim tenant resource - The ID of the SCIM tenant
to create. Must be 4-32 characters, alphanumeric ([a-z0-9-]), and cannot
start with gcp-. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  SCIM_TENANT
     ID of the workforce pool provider scim tenant or fully qualified
     identifier for the workforce pool provider scim tenant.

     To set the scim_tenant attribute:
     + provide the argument scim_tenant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--claim-mapping` | [KEY=VALUE,...] |  | A comma-separated list of KEY=VALUE pairs defining attribute mappings. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Optional, user-specified description for the SCIM tenant (max 256 characters). |
| `--display-name` | DISPLAY_NAME |  | Optional, user-specified display name for the SCIM tenant (max 32 characters). |


**Examples:**
```bash
To create a SCIM tenant with ID my-tenant under provider my-okta-provider
in pool my-pool located in global with claim mappings:

    $ gcloud iam workforce-pools providers scim-tenants create \
        my-tenant --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider \
        --claim-mapping="google.subject=user.externalId,google.group=gro\
    up.externalId"

To create a SCIM tenant sales-tenant under provider salesforce in pool
partner-pool located in europe-west1 with claim mappings:

    $ gcloud iam workforce-pools providers scim-tenants create \
        sales-tenant --location=europe-west1 \
        --workforce-pool=partner-pool --provider=salesforce \
        --claim-mapping="google.subject=user.externalId,google.group=gro\
    up.externalId"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/create)

---
### `gcloud iam workforce-pools providers scim-tenants delete`

Delete an IAM workforce identity pool provider SCIM tenant

Delete an existing SCIM tenant associated with a specific workforce
identity pool provider. This operation marks the tenant for deletion, and
it may be recoverable using the undelete command for a period.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants delete
    (SCIM_TENANT : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL) [--hard-delete]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim tenant resource - The SCIM tenant to delete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SCIM_TENANT
     ID of the workforce pool provider scim tenant or fully qualified
     identifier for the workforce pool provider scim tenant.

     To set the scim_tenant attribute:
     + provide the argument scim_tenant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hard-delete` |  |  | Deletes the SCIM tenant immediately. This operation cannot be undone. |


**Examples:**
```bash
To delete a SCIM tenant with ID my-tenant under provider my-okta-provider
in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants delete \
        my-tenant --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/delete)

---
### `gcloud iam workforce-pools providers scim-tenants describe`

Describe an IAM workforce identity pool provider SCIM tenant

Describe an existing SCIM tenant associated with a specific workforce
identity pool provider.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants describe
    (SCIM_TENANT : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim tenant resource - The SCIM tenant to
describe. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  SCIM_TENANT
     ID of the workforce pool provider scim tenant or fully qualified
     identifier for the workforce pool provider scim tenant.

     To set the scim_tenant attribute:
     + provide the argument scim_tenant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To describe a SCIM tenant with ID my-tenant under provider my-provider in
pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants describe \
        my-tenant --location=global --workforce-pool=my-pool \
        --provider=my-provider
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/describe)

---
### `gcloud iam workforce-pools providers scim-tenants list`

List IAM workforce identity pool provider SCIM tenants

List all SCIM tenants associated with a specific workforce identity pool
provider.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants list
    (--provider=PROVIDER
      : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--show-deleted] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--provider` | PROVIDER |  | _[This must be specified.]_ ID of the workforce pool provider or fully qualified identifier for the workforce pool provider. To set the provider attribute: + provide the argument --provider on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location for the workforce pool. To set the location attribute: + provide the argument --provider on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--workforce-pool` | WORKFORCE_POOL |  | _[This must be specified.]_ The ID to use for the workforce pool, which becomes the final component of the resource name. This value must be a globally unique string of 6 to 63 lowercase letters, digits, or hyphens. It must start with a letter, and cannot have a trailing hyphen. The prefix gcp- is reserved for use by Google, and may not be specified. To set the workforce-pool attribute: + provide the argument --provider on the command line with a fully specified name; + provide the argument --workforce-pool on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Include SCIM tenants that have been deleted. |


**Examples:**
```bash
To list all SCIM tenants under provider my-okta-provider in pool my-pool
located in global:

    $ gcloud iam workforce-pools providers scim-tenants list \
        --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider

To list deleted SCIM tenants as well:

    $ gcloud iam workforce-pools providers scim-tenants list \
        --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/list)

---
### `gcloud iam workforce-pools providers scim-tenants undelete`

Undelete an IAM workforce identity pool provider SCIM tenant

Undelete a previously deleted SCIM tenant associated with a specific
workforce identity pool provider, restoring it to an active state.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants undelete
    (SCIM_TENANT : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim tenant resource - The SCIM tenant to
undelete. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  SCIM_TENANT
     ID of the workforce pool provider scim tenant or fully qualified
     identifier for the workforce pool provider scim tenant.

     To set the scim_tenant attribute:
     + provide the argument scim_tenant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To undelete a SCIM tenant with ID my-tenant under provider my-okta-provider
in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants undelete \
        my-tenant --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/undelete)

---
### `gcloud iam workforce-pools providers scim-tenants update`

Update an IAM workforce identity pool provider SCIM tenant

Update the configuration of an existing SCIM tenant associated with a
specific workforce identity pool provider. Only fields specified in the
command will be modified.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants update
    (SCIM_TENANT : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL)
    [--claim-mapping=[KEY=VALUE,...]] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim tenant resource - The SCIM tenant to update.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SCIM_TENANT
     ID of the workforce pool provider scim tenant or fully qualified
     identifier for the workforce pool provider scim tenant.

     To set the scim_tenant attribute:
     + provide the argument scim_tenant on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument scim_tenant on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--claim-mapping` | [KEY=VALUE,...] |  | A comma-separated list of KEY=VALUE pairs defining attribute mappings. |
| `--description` | DESCRIPTION |  | Optional, user-specified description for the SCIM tenant (max 256 characters). |
| `--display-name` | DISPLAY_NAME |  | Optional, user-specified display name for the SCIM tenant (max 32 characters). |


**Examples:**
```bash
To update the display name and description of a SCIM tenant with ID
my-tenant under provider my-okta-provider in pool my-pool located in
global:

    $ gcloud iam workforce-pools providers scim-tenants update \
        my-tenant --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider \
        --display-name="Updated Tenant Name" \
        --description="New description"

To update the claim mapping for the same tenant:

    $ gcloud iam workforce-pools providers scim-tenants update \
        my-tenant --location=global --workforce-pool=my-pool \
        --provider=my-okta-provider \
        --claim-mapping="google.subject=new_external_id,google.groups=al\
    l_groups"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/update)

---

## `gcloud iam workforce-pools providers scim-tenants tokens` — manage IAM workforce identity pool provider SCIM tenant tokens
### `gcloud iam workforce-pools providers scim-tenants tokens create`

Create an IAM workforce identity pool provider SCIM tenant token

Create a new SCIM token associated with a specific workforce identity pool
provider SCIM tenant.

Upon successful creation, the command returns the created SCIM token
resource.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants tokens create
    (TOKEN : --location=LOCATION --provider=PROVIDER
      --scim-tenant=SCIM_TENANT --workforce-pool=WORKFORCE_POOL)
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim token resource - The ID of the SCIM token to
create. Must be 4-32 characters, alphanumeric ([a-z0-9-]), and cannot
start with gcp-. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  TOKEN
     ID of the workforce pool provider scim token or fully qualified
     identifier for the workforce pool provider scim token.

     To set the token attribute:
     + provide the argument token on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --scim-tenant=SCIM_TENANT
     The ID for the SCIM tenant, which becomes the final component of the
     resource name. This value must be 4-32 characters, alphanumeric
     ([a-z0-9-]), and cannot start with gcp-.

     To set the scim-tenant attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --scim-tenant on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Optional, user-specified display name for the SCIM token (max 32 characters). |


**Examples:**
```bash
To create a SCIM token with ID my-token under tenant my-tenant provider
my-provider in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants tokens create \
        my-token --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/tokens/create)

---
### `gcloud iam workforce-pools providers scim-tenants tokens delete`

Delete an IAM workforce identity pool provider SCIM tenant token

Delete a SCIM token associated with a specific workforce identity pool
provider SCIM tenant.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants tokens delete
    (TOKEN : --location=LOCATION --provider=PROVIDER
      --scim-tenant=SCIM_TENANT --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim token resource - The SCIM token to delete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  TOKEN
     ID of the workforce pool provider scim token or fully qualified
     identifier for the workforce pool provider scim token.

     To set the token attribute:
     + provide the argument token on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --scim-tenant=SCIM_TENANT
     The ID for the SCIM tenant, which becomes the final component of the
     resource name. This value must be 4-32 characters, alphanumeric
     ([a-z0-9-]), and cannot start with gcp-.

     To set the scim-tenant attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --scim-tenant on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To delete a SCIM token with ID my-token under tenant my-tenant provider
my-provider in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants tokens delete \
        my-token --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/tokens/delete)

---
### `gcloud iam workforce-pools providers scim-tenants tokens describe`

Describe an IAM workforce identity pool provider SCIM tenant token

Describe a SCIM token associated with a specific workforce identity pool
provider SCIM tenant.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants tokens describe
    (TOKEN : --location=LOCATION --provider=PROVIDER
      --scim-tenant=SCIM_TENANT --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim token resource - The SCIM token to describe.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  TOKEN
     ID of the workforce pool provider scim token or fully qualified
     identifier for the workforce pool provider scim token.

     To set the token attribute:
     + provide the argument token on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --scim-tenant=SCIM_TENANT
     The ID for the SCIM tenant, which becomes the final component of the
     resource name. This value must be 4-32 characters, alphanumeric
     ([a-z0-9-]), and cannot start with gcp-.

     To set the scim-tenant attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --scim-tenant on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To describe a SCIM token with ID my-token under tenant my-tenant provider
my-provider in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants tokens \
        describe my-token --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/tokens/describe)

---
### `gcloud iam workforce-pools providers scim-tenants tokens list`

List IAM workforce identity pool provider SCIM tenant tokens

List all SCIM tokens associated with a specific workforce identity pool
provider SCIM tenant.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants tokens list
    (--scim-tenant=SCIM_TENANT : --location=LOCATION
      --provider=PROVIDER --workforce-pool=WORKFORCE_POOL) [--show-deleted]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scim-tenant` | SCIM_TENANT |  | _[This must be specified.]_ ID of the workforce pool provider scim tenant or fully qualified identifier for the workforce pool provider scim tenant. To set the scim-tenant attribute: + provide the argument --scim-tenant on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location for the workforce pool. To set the location attribute: + provide the argument --scim-tenant on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--provider` | PROVIDER |  | _[This must be specified.]_ The ID to use for the workforce pool provider, which becomes the final component of the resource name. This value must be unique within the workforce pool, 4-32 characters in length, and may contain the characters [a-z0-9-]. The prefix gcp- is reserved for use by Google, and may not be specified. To set the provider attribute: + provide the argument --scim-tenant on the command line with a fully specified name; + provide the argument --provider on the command line. |
| `--workforce-pool` | WORKFORCE_POOL |  | _[This must be specified.]_ The ID to use for the workforce pool, which becomes the final component of the resource name. This value must be a globally unique string of 6 to 63 lowercase letters, digits, or hyphens. It must start with a letter, and cannot have a trailing hyphen. The prefix gcp- is reserved for use by Google, and may not be specified. To set the workforce-pool attribute: + provide the argument --scim-tenant on the command line with a fully specified name; + provide the argument --workforce-pool on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Include soft-deleted tokens in the results. |


**Examples:**
```bash
To list all SCIM tokens under tenant my-tenant provider my-provider in pool
my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants tokens list \
        --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant

To list deleted SCIM tokens as well:

    $ gcloud iam workforce-pools providers scim-tenants tokens list \
        --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/tokens/list)

---
### `gcloud iam workforce-pools providers scim-tenants tokens undelete`

Undelete an IAM workforce identity pool provider SCIM tenant token

Undelete a SCIM token associated with a specific workforce identity pool
provider SCIM tenant.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants tokens undelete
    (TOKEN : --location=LOCATION --provider=PROVIDER
      --scim-tenant=SCIM_TENANT --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim token resource - The SCIM token to undelete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  TOKEN
     ID of the workforce pool provider scim token or fully qualified
     identifier for the workforce pool provider scim token.

     To set the token attribute:
     + provide the argument token on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --scim-tenant=SCIM_TENANT
     The ID for the SCIM tenant, which becomes the final component of the
     resource name. This value must be 4-32 characters, alphanumeric
     ([a-z0-9-]), and cannot start with gcp-.

     To set the scim-tenant attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --scim-tenant on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To undelete a SCIM token with ID my-token under tenant my-tenant provider
my-provider in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants tokens \
        undelete my-token --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/tokens/undelete)

---
### `gcloud iam workforce-pools providers scim-tenants tokens update`

Update an IAM workforce identity pool provider SCIM tenant token

Update an existing SCIM token associated with a specific workforce identity
pool provider SCIM tenant.

**Synopsis:**
```
gcloud iam workforce-pools providers scim-tenants tokens update
    (TOKEN : --location=LOCATION --provider=PROVIDER
      --scim-tenant=SCIM_TENANT --workforce-pool=WORKFORCE_POOL)
    --display-name=DISPLAY_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool provider scim token resource - The SCIM token to update.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  TOKEN
     ID of the workforce pool provider scim token or fully qualified
     identifier for the workforce pool provider scim token.

     To set the token attribute:
     + provide the argument token on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --provider=PROVIDER
     The ID to use for the workforce pool provider, which becomes the
     final component of the resource name. This value must be unique
     within the workforce pool, 4-32 characters in length, and may contain
     the characters [a-z0-9-]. The prefix gcp- is reserved for use by
     Google, and may not be specified.

     To set the provider attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --provider on the command line.

  --scim-tenant=SCIM_TENANT
     The ID for the SCIM tenant, which becomes the final component of the
     resource name. This value must be 4-32 characters, alphanumeric
     ([a-z0-9-]), and cannot start with gcp-.

     To set the scim-tenant attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --scim-tenant on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument token on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Optional, user-specified display name for the SCIM token (max 32 characters). |


**Examples:**
```bash
To update the display name of a SCIM token with ID my-token under tenant
my-tenant provider my-provider in pool my-pool located in global:

    $ gcloud iam workforce-pools providers scim-tenants tokens update \
        my-token --location=global --workforce-pool=my-pool \
        --provider=my-provider --scim-tenant=my-tenant \
        --display-name="New display name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/providers/scim-tenants/tokens/update)

---

## `gcloud iam workforce-pools subjects` — create and manage workforce pool subjects
### `gcloud iam workforce-pools subjects delete`

Delete a workforce pool subject

Delete a workforce pool subject.

**Synopsis:**
```
gcloud iam workforce-pools subjects delete
    (SUBJECT : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool subject resource - The workforce pool subject to delete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SUBJECT
     ID of the workforce pool subject or fully qualified identifier for
     the workforce pool subject.

     To set the subject attribute:
     + provide the argument subject on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument subject on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument subject on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a workforce pool subject with the ID
my-workforce-pool-subject:

    $ gcloud iam workforce-pools subjects delete \
        my-workforce-pool-subject --workforce-pool="my-workforce-pool" \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/subjects/delete)

---
### `gcloud iam workforce-pools subjects undelete`

Undelete a workforce pool subject

Undelete a workforce pool subject.

**Synopsis:**
```
gcloud iam workforce-pools subjects undelete
    (SUBJECT : --location=LOCATION --workforce-pool=WORKFORCE_POOL)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool subject resource - The workforce pool subject to undelete.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SUBJECT
     ID of the workforce pool subject or fully qualified identifier for
     the workforce pool subject.

     To set the subject attribute:
     + provide the argument subject on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument subject on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument subject on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command undeletes a workforce pool subject with the ID
my-workforce-pool-subject:

    $ gcloud iam workforce-pools subjects undelete \
        my-workforce-pool-subject --workforce-pool="my-workforce-pool" \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/subjects/undelete)

---

## `gcloud iam workforce-pools subjects operations` — manage IAM workforce pool subject long-running operations
### `gcloud iam workforce-pools subjects operations describe`

Describe a workforce pool subject operation

Describe a workforce pool subject operation.

**Synopsis:**
```
gcloud iam workforce-pools subjects operations describe
    (OPERATION : --location=LOCATION
      --subject=SUBJECT --workforce-pool=WORKFORCE_POOL)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workforce pool subject operation resource - The workforce pool subject
long-running operation to describe. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  OPERATION
     ID of the workforce pool subject operation or fully qualified
     identifier for the workforce pool subject operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the workforce pool.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --subject=SUBJECT
     The ID to use for the workforce pool subject, which becomes the final
     component of the resource name.

     To set the subject attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --subject on the command line.

  --workforce-pool=WORKFORCE_POOL
     The ID to use for the workforce pool, which becomes the final
     component of the resource name. This value must be a globally unique
     string of 6 to 63 lowercase letters, digits, or hyphens. It must
     start with a letter, and cannot have a trailing hyphen. The prefix
     gcp- is reserved for use by Google, and may not be specified.

     To set the workforce-pool attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --workforce-pool on the command line.
```

**Examples:**
```bash
To describe the long-running workforce pool subject operation with the ID
my-operation, run:

    $ gcloud iam workforce-pools subjects operations describe \
        my-operation --workforce-pool="my-workforce-pool" \
        --subject="my-subject" --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/workforce-pools/subjects/operations/describe)

---
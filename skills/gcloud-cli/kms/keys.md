# gcloud kms keys

create and manage keys

### `gcloud kms keys add-iam-policy-binding`

Add IAM policy binding for a kms key

Adds a policy binding to the IAM policy of a kms key. A binding consists of
at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud kms keys add-iam-policy-binding
    (KEY : --keyring=KEYRING --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The key to add the IAM policy binding. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The containing keyring.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
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
'test-user@gmail.com' on the key frodo with the keyring fellowship and
location global, run:

    $ gcloud kms keys add-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' --role='roles/editor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/cloudkms.signer' and the user 'test-user@gmail.com' on a
the key frodo with the keyring fellowship and location global, run:

    $ gcloud kms keys add-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' \
        --role='roles/cloudkms.signer' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/add-iam-policy-binding)

---
### `gcloud kms keys create`

Create a new key

Creates a new key within the given keyring.

The flag --purpose is always required when creating a key. The flag
--default-algorithm is required when creating a symmetric signing key, an
asymmetric key, or an external key. Algorithm and purpose should be
compatible.

The optional flags --rotation-period and --next-rotation-time define a
rotation schedule for the key. A schedule can also be defined by the
--create-rotation-schedule command.

The flag --next-rotation-time must be in ISO 8601 or RFC3339 format, and
rotation-period must be in the form INTEGER[UNIT], where units can be one
of seconds (s), minutes (m), hours (h) or days (d).

The optional flag --protection-level specifies the physical environment
where crypto operations with the key happen. The default is software; use
hsm to create a hardware-backed key, external to create an externally
backed key, or external-vpc to create an external key over vpc.

The optional flag --labels defines a user specified key/value pair for the
given key.

The flag --skip-initial-version-creation creates a CryptoKey with no
versions. If you import into the CryptoKey, or create a new version in that
CryptoKey, there will be no primary version until one is set using the
--set-primary-version command. You must include
--skip-initial-version-creation when creating a CryptoKey with protection
level external or external-vpc.

The optional flag --import-only restricts the key to imported key versions
only. To do so, the flag --skip-initial-version-creation must also be set.

The optional flag --destroy-scheduled-duration defines the destroy schedule
for the key, and must be in the form INTEGER[UNIT], where units can be one
of seconds (s), minutes (m), hours (h) or days (d).

The flag --crypto-key-backend defines the resource name for the backend
where the key resides. Required for external-vpc keys.

The optional flag --allowed-access-reasons defines the Key Access
Justifications Policy for the key, and is specified as a comma separated
list of zero or more justification codes defined in
https://cloud.google.com/assured-workloads/key-access-justifications/docs/justification-codes.
The key must be enrolled in Key Access Justifications to use this flag.

**Synopsis:**
```
gcloud kms keys create (KEY : --keyring=KEYRING --location=LOCATION)
    --purpose=PURPOSE
    [--allowed-access-reasons=[ALLOWED_ACCESS_REASONS,...]]
    [--crypto-key-backend=CRYPTO_KEY_BACKEND]
    [--default-algorithm=DEFAULT_ALGORITHM]
    [--destroy-scheduled-duration=DESTROY_SCHEDULED_DURATION]
    [--import-only] [--labels=[KEY=VALUE,...]]
    [--next-rotation-time=NEXT_ROTATION_TIME]
    [--protection-level=PROTECTION_LEVEL; default="software"]
    [--rotation-period=ROTATION_PERIOD] [--skip-initial-version-creation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--purpose` | one of: asymmetric-encryption, asymmetric-signing, encryption, key-encapsulation, mac, raw-encryption |  | The "purpose" of the key. PURPOSE must be one of: asymmetric-encryption, asymmetric-signing, encryption, key-encapsulation, mac, raw-encryption. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-access-reasons` | one of: customer-authorized-workflow-servicing, customer-initiated-access, customer-initiated-support, google-initiated-review, google-initiated-service, google-initiated-system-operation, google-response-to-production-alert, modified-customer-initiated-access, modified-google-initiated-system-operation, reason-not-expected, reason-unspecified, third-party-data-request |  | The list of allowed Key Access Justifications access reasons on the key. The key must be enrolled in Key Access Justifications to configure this field. By default, this field is absent, and all justification codes are allowed. For more information about justification codes, see https://cloud.google.com/assured-workloads/key-access-justifications/docs/justification-codes. ALLOWED_ACCESS_REASONS must be one of: customer-authorized-workflow-servicing, customer-initiated-access, customer-initiated-support, google-initiated-review, google-initiated-service, google-initiated-system-operation, google-response-to-production-alert, modified-customer-initiated-access, modified-google-initiated-system-operation, reason-not-expected, reason-unspecified, third-party-data-request. |
| `--crypto-key-backend` | CRYPTO_KEY_BACKEND |  | The resource name of the backend environment where the key material for all CryptoKeyVersions associated with this CryptoKey reside and where all related cryptographic operations are performed. Currently only applicable for EXTERNAL_VPC and EkmConnection resource names. |
| `--default-algorithm` | one of: aes-128-cbc, aes-128-ctr, aes-128-gcm, aes-256-cbc, aes-256-ctr, aes-256-gcm, ec-sign-ed25519, ec-sign-p256-sha256, ec-sign-p384-sha384, ec-sign-secp256k1-sha256, external-symmetric-encryption, google-symmetric-encryption, hmac-sha1, hmac-sha224, hmac-sha256, hmac-sha384, hmac-sha512, kem-xwing, ml-kem-1024, ml-kem-768, pq-sign-hash-slh-dsa-sha2-128s-sha256, pq-sign-ml-dsa-65, pq-sign-slh-dsa-sha2-128s, rsa-decrypt-oaep-2048-sha1, rsa-decrypt-oaep-2048-sha256, rsa-decrypt-oaep-3072-sha1, rsa-decrypt-oaep-3072-sha256, rsa-decrypt-oaep-4096-sha1, rsa-decrypt-oaep-4096-sha256, rsa-decrypt-oaep-4096-sha512, rsa-sign-pkcs1-2048-sha256, rsa-sign-pkcs1-3072-sha256, rsa-sign-pkcs1-4096-sha256, rsa-sign-pkcs1-4096-sha512, rsa-sign-pss-2048-sha256, rsa-sign-pss-3072-sha256, rsa-sign-pss-4096-sha256, rsa-sign-pss-4096-sha512, rsa-sign-raw-pkcs1-2048, rsa-sign-raw-pkcs1-3072, rsa-sign-raw-pkcs1-4096 |  | The default algorithm for the crypto key. For more information about choosing an algorithm, see https://cloud.google.com/kms/docs/algorithms. DEFAULT_ALGORITHM must be one of: aes-128-cbc, aes-128-ctr, aes-128-gcm, aes-256-cbc, aes-256-ctr, aes-256-gcm, ec-sign-ed25519, ec-sign-p256-sha256, ec-sign-p384-sha384, ec-sign-secp256k1-sha256, external-symmetric-encryption, google-symmetric-encryption, hmac-sha1, hmac-sha224, hmac-sha256, hmac-sha384, hmac-sha512, kem-xwing, ml-kem-1024, ml-kem-768, pq-sign-hash-slh-dsa-sha2-128s-sha256, pq-sign-ml-dsa-65, pq-sign-slh-dsa-sha2-128s, rsa-decrypt-oaep-2048-sha1, rsa-decrypt-oaep-2048-sha256, rsa-decrypt-oaep-3072-sha1, rsa-decrypt-oaep-3072-sha256, rsa-decrypt-oaep-4096-sha1, rsa-decrypt-oaep-4096-sha256, rsa-decrypt-oaep-4096-sha512, rsa-sign-pkcs1-2048-sha256, rsa-sign-pkcs1-3072-sha256, rsa-sign-pkcs1-4096-sha256, rsa-sign-pkcs1-4096-sha512, rsa-sign-pss-2048-sha256, rsa-sign-pss-3072-sha256, rsa-sign-pss-4096-sha256, rsa-sign-pss-4096-sha512, rsa-sign-raw-pkcs1-2048, rsa-sign-raw-pkcs1-3072, rsa-sign-raw-pkcs1-4096. |
| `--destroy-scheduled-duration` | DESTROY_SCHEDULED_DURATION |  | The amount of time that versions of the key should spend in the DESTROY_SCHEDULED state before transitioning to DESTROYED. See $ gcloud topic datetimes for information on duration formats. |
| `--import-only` |  |  | Restrict this key to imported versions only. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--next-rotation-time` | NEXT_ROTATION_TIME |  | Next automatic rotation time of the key. See $ gcloud topic datetimes for information on time formats. |
| `--protection-level` | one of: software, hsm, hsm-single-tenant, external, external-vpc | software | Protection level of the key. PROTECTION_LEVEL must be one of: software, hsm, hsm-single-tenant, external, external-vpc. |
| `--rotation-period` | ROTATION_PERIOD |  | Automatic rotation period of the key. See $ gcloud topic datetimes for information on duration formats. |
| `--skip-initial-version-creation` |  |  | Skip creating the first version in a key and setting it as primary during creation. |


**Examples:**
```bash
The following command creates a key named frodo with protection level
software within the keyring fellowship and location us-east1:

    $ gcloud kms keys create frodo --location=us-east1 \
        --keyring=fellowship --purpose=encryption

The following command creates a key named strider with protection level
software within the keyring rangers and location global with a specified
rotation schedule:

    $ gcloud kms keys create strider --location=global \
        --keyring=rangers --purpose=encryption --rotation-period=30d \
        --next-rotation-time=2017-10-12T12:34:56.1234Z

The following command creates a raw encryption key named foo with
protection level software within the keyring fellowship and location
us-east1 with two specified labels:

    $ gcloud kms keys create foo --location=us-east1 \
        --keyring=fellowship --purpose=raw-encryption \
        --default-algorithm=aes-128-cbc --labels=env=prod,team=kms

The following command creates an asymmetric key named samwise with
protection level software and default algorithm ec-sign-p256-sha256 within
the keyring fellowship and location us-east1:

    $ gcloud kms keys create samwise --location=us-east1 \
        --keyring=fellowship --purpose=asymmetric-signing \
        --default-algorithm=ec-sign-p256-sha256

The following command creates a key named gimli with protection level hsm
and default algorithm google-symmetric-encryption within the keyring
fellowship and location us-east1:

    $ gcloud kms keys create gimli --location=us-east1 \
        --keyring=fellowship --purpose=encryption --protection-level=hsm

The following command creates a key named legolas with protection level
external and default algorithm external-symmetric-encryption within the
keyring fellowship and location us-central1:

    $ gcloud kms keys create legolas --location=us-central1 \
        --keyring=fellowship --purpose=encryption \
        --default-algorithm=external-symmetric-encryption \
        --protection-level=external --skip-initial-version-creation

The following command creates a key named bilbo with protection level
external-vpc and default algorithm external-symmetric-encryption and an
EkmConnection of eagles within the keyring fellowship and location
us-central1:

    $ gcloud kms keys create bilbo --location=us-central1 \
        --keyring=fellowship --purpose=encryption \
        --default-algorithm=external-symmetric-encryption \
        --protection-level=external-vpc \
        --skip-initial-version-creation \
        --crypto-key-backend="projects/$(gcloud config get project)/
        locations/us-central1/ekmConnections/eagles"

The following command creates a key named arwen with protection level
software within the keyring fellowship and location us-east1 with a Key
Access Justifications policy that allows access reasons
customer-initiated-access and google-initiated-system-operation:

    $ gcloud kms keys create arwen --location=us-east1 \
        --keyring=fellowship --purpose=encryption \
        --allowed-access-reasons=customer-initiated-access,\
    google-initiated-system-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/create)

---
### `gcloud kms keys describe`

Get metadata for a given key

Returns metadata for the given key.

**Synopsis:**
```
gcloud kms keys describe (KEY : --keyring=KEYRING --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command returns metadata for the key frodo within the keyring
fellowship in the location us-east1:

    $ gcloud kms keys describe frodo --keyring=fellowship \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/describe)

---
### `gcloud kms keys get-iam-policy`

Get the IAM policy for a key

Gets the IAM policy for the given key.

Returns an empty policy if the resource does not have a policy set.

**Synopsis:**
```
gcloud kms keys get-iam-policy
    (KEY : --keyring=KEYRING --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command gets the IAM policy for the key frodo within the
keyring fellowship and location global:

    $ gcloud kms keys get-iam-policy frodo --keyring=fellowship \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/get-iam-policy)

---
### `gcloud kms keys list`

List the keys within a keyring

Lists all keys within the given keyring.

**Synopsis:**
```
gcloud kms keys list (--keyring=KEYRING : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keyring` | KEYRING |  | _[This must be specified.]_ ID of the keyring or fully qualified identifier for the keyring. To set the keyring attribute: + provide the argument --keyring on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Google Cloud location for the keyring. To set the location attribute: + provide the argument --keyring on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
The following command lists all keys within the keyring fellowship and
location global:

    $ gcloud kms keys list --keyring=fellowship --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/list)

---
### `gcloud kms keys remove-iam-policy-binding`

Remove IAM policy binding for a kms key

Removes a policy binding from the IAM policy of a kms key. A binding
consists of at least one member, a role, and an optional condition.

**Synopsis:**
```
gcloud kms keys remove-iam-policy-binding
    (KEY : --keyring=KEYRING --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The key to remove the IAM policy binding. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The containing keyring.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The location of the resource.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
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
'test-user@gmail.com' on the key frodo with the keyring fellowship and
location global, run:

    $ gcloud kms keys remove-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding with a condition of
expression='request.time < timestamp("2019-01-01T00:00:00Z")',
title='expires_end_of_2018', and description='Expires at midnight on
2018-12-31' for the role of 'roles/cloudkms.signer' for the user
'test-user@gmail.com' on a the key frodo with the keyring fellowship and
location global, run:

    $ gcloud kms keys remove-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' \
        --role='roles/cloudkms.signer' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

To remove all IAM policy bindings regardless of the condition for the role
of 'roles/cloudkms.signer' and for the user 'test-user@gmail.com' on a the
key frodo with the keyring fellowship and location global, run:

    $ gcloud kms keys remove-iam-policy-binding frodo \
        --keyring='fellowship' --location='global' \
        --member='user:test-user@gmail.com' \
        --role='roles/cloudkms.signer' --all

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/remove-iam-policy-binding)

---
### `gcloud kms keys remove-rotation-schedule`

Remove the rotation schedule for a key

Removes the rotation schedule for the given key.

**Synopsis:**
```
gcloud kms keys remove-rotation-schedule
    (KEY : --keyring=KEYRING --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command removes the rotation schedule for the key named frodo
within the keyring fellowship and location global:

    $ gcloud kms keys remove-rotation-schedule frodo --location=global \
        --keyring=fellowship
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/remove-rotation-schedule)

---
### `gcloud kms keys set-iam-policy`

Set the IAM policy for a key

Sets the IAM policy for the given key as defined in a JSON or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud kms keys set-iam-policy
    (KEY : --keyring=KEYRING --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   JSON or YAML file with the IAM policy
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the key frodo with the keyring fellowship and
location global:

    $ gcloud kms keys set-iam-policy frodo policy.json \
        --keyring=fellowship --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/set-iam-policy)

---
### `gcloud kms keys set-primary-version`

Set the primary version of a key

Sets the specified version as the primary version of the given key. The
version is specified by its version number assigned on creation.

**Synopsis:**
```
gcloud kms keys set-primary-version
    (KEY : --keyring=KEYRING --location=LOCATION) --version=VERSION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | Version to make primary. |


**Examples:**
```bash
The following command sets version 9 as the primary version of the key
samwise within keyring fellowship and location global:

    $ gcloud kms keys set-primary-version samwise --version=9 \
        --keyring=fellowship --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/set-primary-version)

---
### `gcloud kms keys set-rotation-schedule`

Update the rotation schedule for a key

Updates the rotation schedule for the given key. The schedule automatically
creates a new primary version for the key according to the
--next-rotation-time and --rotation-period flags.

The flag --next-rotation-time must be in ISO or RFC3339 format, and
--rotation-period must be in the form INTEGER[UNIT], where units can be one
of seconds (s), minutes (m), hours (h) or days (d).

Key rotations performed manually via update-primary-version and the version
create do not affect the stored --next-rotation-time.

**Synopsis:**
```
gcloud kms keys set-rotation-schedule
    (KEY : --keyring=KEYRING --location=LOCATION)
    [--next-rotation-time=NEXT_ROTATION_TIME]
    [--rotation-period=ROTATION_PERIOD] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--next-rotation-time` | NEXT_ROTATION_TIME |  | Next automatic rotation time of the key. See $ gcloud topic datetimes for information on time formats. |
| `--rotation-period` | ROTATION_PERIOD |  | Automatic rotation period of the key. See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
The following command sets a 30 day rotation period for the key named frodo
within the keyring fellowship and location global starting at the specified
time:

    $ gcloud kms keys set-rotation-schedule frodo --location=global \
        --keyring=fellowship --rotation-period=30d \
        --next-rotation-time=2017-10-12T12:34:56.1234Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/set-rotation-schedule)

---
### `gcloud kms keys update`

Update a key

1. Update the rotation schedule for the given key.

Updates the rotation schedule for the given key. The schedule automatically
creates a new primary version for the key according to next-rotation-time
and rotation-period flags.

Flag next-rotation-time must be in ISO 8601 or RFC3339 format, and
rotation-period must be in the form INTEGER[UNIT], where units can be one
of seconds (s), minutes (m), hours (h) or days (d).

Key rotations performed manually via update-primary-version and the version
create do not affect the stored next-rotation-time.

2. Remove the rotation schedule for the given key with
remove-rotation-schedule flag.

3. Update/Remove the labels for the given key with update-labels and/or
remove-labels flags.

4. Update the primary version for the given key with primary-version flag.

5. Update the Key Access Justifications policy for the given key with
allowed-access-reasons flag to allow specified reasons. The key must be
enrolled in Key Access Justifications to use this flag.

6. Remove the Key Access Justifications policy for the given key with
remove-key-access-justifications-policy flag. The key must be enrolled in
Key Access Justifications to use this flag.

7. Update the Key Access Justifications policy for the given key with
allowed_access_reasons flag to allow zero access reasons. This effectively
disables the key, because a policy is configured to reject all access
reasons. The key must be enrolled in Key Access Justifications to use this
flag.

**Synopsis:**
```
gcloud kms keys update (KEY : --keyring=KEYRING --location=LOCATION)
    [--allowed-access-reasons=[ALLOWED_ACCESS_REASONS,...]]
    [--default-algorithm=DEFAULT_ALGORITHM]
    [--next-rotation-time=NEXT_ROTATION_TIME]
    [--primary-version=PRIMARY_VERSION]
    [--remove-key-access-justifications-policy]
    [--remove-rotation-schedule] [--rotation-period=ROTATION_PERIOD]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The KMS key resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --keyring=KEYRING
     The KMS keyring of the key.

     To set the keyring attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --keyring on the command line.

  --location=LOCATION
     The Google Cloud location for the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-access-reasons` | one of: customer-authorized-workflow-servicing, customer-initiated-access, customer-initiated-support, google-initiated-review, google-initiated-service, google-initiated-system-operation, google-response-to-production-alert, modified-customer-initiated-access, modified-google-initiated-system-operation, reason-not-expected, reason-unspecified, third-party-data-request |  | The list of allowed Key Access Justifications access reasons on the key. The key must be enrolled in Key Access Justifications to configure this field. By default, this field is absent, and all justification codes are allowed. For more information about justification codes, see https://cloud.google.com/assured-workloads/key-access-justifications/docs/justification-codes. ALLOWED_ACCESS_REASONS must be one of: customer-authorized-workflow-servicing, customer-initiated-access, customer-initiated-support, google-initiated-review, google-initiated-service, google-initiated-system-operation, google-response-to-production-alert, modified-customer-initiated-access, modified-google-initiated-system-operation, reason-not-expected, reason-unspecified, third-party-data-request. |
| `--default-algorithm` | one of: aes-128-cbc, aes-128-ctr, aes-128-gcm, aes-256-cbc, aes-256-ctr, aes-256-gcm, ec-sign-ed25519, ec-sign-p256-sha256, ec-sign-p384-sha384, ec-sign-secp256k1-sha256, external-symmetric-encryption, google-symmetric-encryption, hmac-sha1, hmac-sha224, hmac-sha256, hmac-sha384, hmac-sha512, kem-xwing, ml-kem-1024, ml-kem-768, pq-sign-hash-slh-dsa-sha2-128s-sha256, pq-sign-ml-dsa-65, pq-sign-slh-dsa-sha2-128s, rsa-decrypt-oaep-2048-sha1, rsa-decrypt-oaep-2048-sha256, rsa-decrypt-oaep-3072-sha1, rsa-decrypt-oaep-3072-sha256, rsa-decrypt-oaep-4096-sha1, rsa-decrypt-oaep-4096-sha256, rsa-decrypt-oaep-4096-sha512, rsa-sign-pkcs1-2048-sha256, rsa-sign-pkcs1-3072-sha256, rsa-sign-pkcs1-4096-sha256, rsa-sign-pkcs1-4096-sha512, rsa-sign-pss-2048-sha256, rsa-sign-pss-3072-sha256, rsa-sign-pss-4096-sha256, rsa-sign-pss-4096-sha512, rsa-sign-raw-pkcs1-2048, rsa-sign-raw-pkcs1-3072, rsa-sign-raw-pkcs1-4096 |  | The default algorithm for the crypto key. For more information about choosing an algorithm, see https://cloud.google.com/kms/docs/algorithms. DEFAULT_ALGORITHM must be one of: aes-128-cbc, aes-128-ctr, aes-128-gcm, aes-256-cbc, aes-256-ctr, aes-256-gcm, ec-sign-ed25519, ec-sign-p256-sha256, ec-sign-p384-sha384, ec-sign-secp256k1-sha256, external-symmetric-encryption, google-symmetric-encryption, hmac-sha1, hmac-sha224, hmac-sha256, hmac-sha384, hmac-sha512, kem-xwing, ml-kem-1024, ml-kem-768, pq-sign-hash-slh-dsa-sha2-128s-sha256, pq-sign-ml-dsa-65, pq-sign-slh-dsa-sha2-128s, rsa-decrypt-oaep-2048-sha1, rsa-decrypt-oaep-2048-sha256, rsa-decrypt-oaep-3072-sha1, rsa-decrypt-oaep-3072-sha256, rsa-decrypt-oaep-4096-sha1, rsa-decrypt-oaep-4096-sha256, rsa-decrypt-oaep-4096-sha512, rsa-sign-pkcs1-2048-sha256, rsa-sign-pkcs1-3072-sha256, rsa-sign-pkcs1-4096-sha256, rsa-sign-pkcs1-4096-sha512, rsa-sign-pss-2048-sha256, rsa-sign-pss-3072-sha256, rsa-sign-pss-4096-sha256, rsa-sign-pss-4096-sha512, rsa-sign-raw-pkcs1-2048, rsa-sign-raw-pkcs1-3072, rsa-sign-raw-pkcs1-4096. |
| `--next-rotation-time` | NEXT_ROTATION_TIME |  | Next automatic rotation time of the key. See $ gcloud topic datetimes for information on time formats. |
| `--primary-version` | PRIMARY_VERSION |  | Primary version to make primary. |
| `--remove-key-access-justifications-policy` |  |  | Removes the Key Access Justifications policy on the key, making all justification codes allowed. |
| `--remove-rotation-schedule` |  |  | Remove any existing rotation schedule on the key. |
| `--rotation-period` | ROTATION_PERIOD |  | Automatic rotation period of the key. See $ gcloud topic datetimes for information on duration formats. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command sets a 30 day rotation period for the key named frodo
within the keyring fellowship and location global starting at the specified
time:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --rotation-period=30d \
        --next-rotation-time=2017-10-12T12:34:56.1234Z

The following command removes the rotation schedule for the key named frodo
within the keyring fellowship and location global:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --remove-rotation-schedule

The following command updates the labels value for the key named frodo
within the keyring fellowship and location global. If the label key does
not exist at the time, it will be added:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --update-labels=k1=v1

The following command removes labels k1 and k2 from the key named frodo
within the keyring fellowship and location global:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --remove-labels=k1,k2

The following command updates the primary version for the key named frodo
within the keyring fellowship and location global:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --primary-version=1

The following command updates the default algorithm for the key named frodo
within the keyring fellowship and location global, assuming the key
originally has purpose 'asymmetric-encryption' and algorithm
'rsa-decrypt-oaep-2048-sha256':

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship \
        --default-algorithm=rsa-decrypt-oaep-4096-sha256

The following command updates the Key Access Justifications policy for the
key named frodo within the keyring fellowship and location global to allow
only customer-initiated-access and google-initiated-system-operation:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship \
        --allowed-access-reasons=customer-initiated-access,\
    google-initiated-system-operation

The following command removes the Key Access Justifications policy for the
key named frodo within the keyring fellowship and location global, which
results in all access reasons being allowed:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --remove-key-access-justifications-policy

The following command updates the Key Access Justifications policy for the
key named frodo within the keyring fellowship and location global to allow
only zero access reasons, effectively disabling the key:

    $ gcloud kms keys update frodo --location=global \
        --keyring=fellowship --allowed-access-reasons=
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/update)

---

## `gcloud kms keys versions` — create and manage versions
### `gcloud kms keys versions create`

Create a new version

Creates a new version within the given key.

**Synopsis:**
```
gcloud kms keys versions create
    [--ekm-connection-key-path=EKM_CONNECTION_KEY_PATH]
    [--external-key-uri=EXTERNAL_KEY_URI] [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--primary] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ekm-connection-key-path` | EKM_CONNECTION_KEY_PATH |  | The path to the external key material on the EKM for keys with protection level "external-vpc". |
| `--external-key-uri` | EXTERNAL_KEY_URI |  | The URI of the external key for keys with protection level "external". |
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--primary` |  |  | If specified, immediately makes the new version primary. This should only be used with the encryption purpose. |


**Examples:**
```bash
The following command creates a new version within the frodo key,
fellowship keyring, and global location and sets it as the primary version:

    $ gcloud kms keys versions create --location=global \
        --keyring=fellowship --key=frodo --primary

The following command creates a new version within the legolas key,
fellowship keyring, us-central1 location,
https://example.kms/v0/some/key/path as the address for its external key,
and sets it as the key's primary version:

    $ gcloud kms keys versions create --location=us-central1 \
        --keyring=fellowship --key=legolas \
        --external-key-uri=https://example.kms/v0/some/key/path \
        --primary

The following command creates a new version within the bilbo key,
fellowship keyring, us-central1 location, v0/some/key/path as the ekm
connection key path for its external key, and sets it as the key's primary
version:

    $ gcloud kms keys versions create --location=us-central1 \
        --keyring=fellowship --key=bilbo \
        --ekm-connection-key-path=v0/some/key/path --primary
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/create)

---
### `gcloud kms keys versions describe`

Get metadata for a given version

Returns metadata for the given version.

The optional flag attestation-file specifies file to write the attestation
object into. The attestation object enables the user to verify the
integrity and provenance of the key. See
https://cloud.google.com/kms/docs/attest-key for more information about
attestations.

**Synopsis:**
```
gcloud kms keys versions describe VERSION
    [--attestation-file=ATTESTATION_FILE] [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attestation-file` | ATTESTATION_FILE |  | Path to the output attestation file. |
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |


**Examples:**
```bash
The following command returns metadata for version 2 within key frodo
within the keyring fellowship in the location us-east1:

    $ gcloud kms keys versions describe 2 --key=frodo \
        --keyring=fellowship --location=us-east1

For key versions with protection level HSM, use the --attestation-file flag
to save the attestation to a local file.

    $ gcloud kms keys versions describe 2 --key=frodo \
        --keyring=fellowship --location=us-east1 \
        --attestation-file=path/to/attestation.dat
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/describe)

---
### `gcloud kms keys versions destroy`

Schedule a version to be destroyed

Schedules the given version for destruction in 24 hours.

After that time period passes it is automatically destroyed. Once
destroyed, the key material is removed but the version number can not be
reused.

Only versions which are Enabled or Disabled can be Scheduled for
destruction.

**Synopsis:**
```
gcloud kms keys versions destroy VERSION [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to destroy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |


**Examples:**
```bash
The following command schedules version 9 of key frodo within keyring
fellowship and location us-east1 for destruction:

    $ gcloud kms keys versions destroy 9 --location=us-east1 \
        --keyring=fellowship --key=frodo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/destroy)

---
### `gcloud kms keys versions disable`

Disable a given version

Disables the specified version within the given key.

Only a version which is Enabled can be Disabled.

**Synopsis:**
```
gcloud kms keys versions disable VERSION [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to disable.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |


**Examples:**
```bash
The following command disables version 3 of key frodo within keyring
fellowship and location us-east1:

    $ gcloud kms keys versions disable 3 --location=us-east1 \
        --keyring=fellowship --key=frodo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/disable)

---
### `gcloud kms keys versions enable`

Enable a given version

Enables the specified version within the given key.

Only a version which is Disabled can be Enabled.

**Synopsis:**
```
gcloud kms keys versions enable VERSION [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to enable.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |


**Examples:**
```bash
The following command enables version 3 of key frodo within keyring
fellowship and location us-east1:

    $ gcloud kms keys versions enable 3 --location=us-east1 \
        --keyring=fellowship --key=frodo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/enable)

---
### `gcloud kms keys versions get-certificate-chain`

Get a certificate chain for a given version

Returns the PEM-format certificate chain for the specified key version. The
optional flag output-file indicates the path to store the PEM. If not
specified, the PEM will be printed to stdout.

**Synopsis:**
```
gcloud kms keys versions get-certificate-chain VERSION
    [--certificate-chain-type=CERTIFICATE_CHAIN_TYPE; default="all"]
    [--key=KEY] [--keyring=KEYRING] [--location=LOCATION]
    [--output-file=OUTPUT_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version from which to get the certificate chain.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--certificate-chain-type` | one of: all, cavium, google-card, google-partition | all | Certificate chain to retrieve. CERTIFICATE_CHAIN_TYPE must be one of: all, cavium, google-card, google-partition. |
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--output-file` | OUTPUT_FILE |  | Path to the output file to store PEM. |


**Examples:**
```bash
The following command saves the Cavium certificate chain for CryptoKey
frodo Version 2 to /tmp/my/cavium.pem:

    $ gcloud kms keys versions get-certificate-chain 2 --key=frodo \
        --keyring=fellowship --location=us-east1 \
        --certificate-chain-type=cavium --output-file=/tmp/my/cavium.pem
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/get-certificate-chain)

---
### `gcloud kms keys versions get-public-key`

Get the public key for a given version

Returns the public key of the given asymmetric key version in the specified
format.

The optional flag output-file indicates the path to store the public key.
If not specified, the public key will be printed to stdout.

The optional flag public-key-format indicates the format in which the
public key will be returned. For the NIST PQC algorithms, this must be
specified and set to nist-pqc. For kem-xwing this must be specified and set
to xwing-raw-bytes. For all other algorithms, this flag is optional and can
be either pem or der; the default value is pem. See "Retrieve a public key"
in the Cloud KMS documentation
(https://cloud.google.com/kms/help/get-public-key) for more information
about the supported formats.

**Synopsis:**
```
gcloud kms keys versions get-public-key VERSION [--key=KEY]
    [--keyring=KEYRING] [--location=LOCATION] [--output-file=OUTPUT_FILE]
    [--public-key-format=PUBLIC_KEY_FORMAT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to get public key.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--output-file` | OUTPUT_FILE |  | Path to the output file to store public key. |
| `--public-key-format` | PUBLIC_KEY_FORMAT |  | The format in which the public key will be returned. |


**Examples:**
```bash
The following command saves the public key for CryptoKey frodo Version 2 to
'/tmp/my/public_key.file':

    $ gcloud kms keys versions get-public-key 2 --key=frodo \
        --keyring=fellowship --location=us-east1 \
        --public-key-format=pem --output-file=/tmp/my/public_key.file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/get-public-key)

---
### `gcloud kms keys versions import`

Import a version into an existing crypto key

Imports wrapped key material into a new version within an existing crypto
key following the import procedure documented at
https://cloud.google.com/kms/docs/importing-a-key.

**Synopsis:**
```
gcloud kms keys versions import --algorithm=ALGORITHM
    --import-job=IMPORT_JOB [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--public-key-file=PUBLIC_KEY_FILE]
    [--target-key-file=TARGET_KEY_FILE] [--version=VERSION]
    [--wrapped-key-file=WRAPPED_KEY_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--algorithm` | one of: aes-128-cbc, aes-128-ctr, aes-128-gcm, aes-256-cbc, aes-256-ctr, aes-256-gcm, ec-sign-ed25519, ec-sign-p256-sha256, ec-sign-p384-sha384, ec-sign-secp256k1-sha256, google-symmetric-encryption, hmac-sha1, hmac-sha224, hmac-sha256, hmac-sha384, hmac-sha512, kem-xwing, ml-kem-1024, ml-kem-768, pq-sign-hash-slh-dsa-sha2-128s-sha256, pq-sign-ml-dsa-65, pq-sign-slh-dsa-sha2-128s, rsa-decrypt-oaep-2048-sha1, rsa-decrypt-oaep-2048-sha256, rsa-decrypt-oaep-3072-sha1, rsa-decrypt-oaep-3072-sha256, rsa-decrypt-oaep-4096-sha1, rsa-decrypt-oaep-4096-sha256, rsa-decrypt-oaep-4096-sha512, rsa-sign-pkcs1-2048-sha256, rsa-sign-pkcs1-3072-sha256, rsa-sign-pkcs1-4096-sha256, rsa-sign-pkcs1-4096-sha512, rsa-sign-pss-2048-sha256, rsa-sign-pss-3072-sha256, rsa-sign-pss-4096-sha256, rsa-sign-pss-4096-sha512, rsa-sign-raw-pkcs1-2048, rsa-sign-raw-pkcs1-3072, rsa-sign-raw-pkcs1-4096 |  | The algorithm to assign to the new key version. For more information about supported algorithms, see https://cloud.google.com/kms/docs/algorithms. ALGORITHM must be one of: aes-128-cbc, aes-128-ctr, aes-128-gcm, aes-256-cbc, aes-256-ctr, aes-256-gcm, ec-sign-ed25519, ec-sign-p256-sha256, ec-sign-p384-sha384, ec-sign-secp256k1-sha256, google-symmetric-encryption, hmac-sha1, hmac-sha224, hmac-sha256, hmac-sha384, hmac-sha512, kem-xwing, ml-kem-1024, ml-kem-768, pq-sign-hash-slh-dsa-sha2-128s-sha256, pq-sign-ml-dsa-65, pq-sign-slh-dsa-sha2-128s, rsa-decrypt-oaep-2048-sha1, rsa-decrypt-oaep-2048-sha256, rsa-decrypt-oaep-3072-sha1, rsa-decrypt-oaep-3072-sha256, rsa-decrypt-oaep-4096-sha1, rsa-decrypt-oaep-4096-sha256, rsa-decrypt-oaep-4096-sha512, rsa-sign-pkcs1-2048-sha256, rsa-sign-pkcs1-3072-sha256, rsa-sign-pkcs1-4096-sha256, rsa-sign-pkcs1-4096-sha512, rsa-sign-pss-2048-sha256, rsa-sign-pss-3072-sha256, rsa-sign-pss-4096-sha256, rsa-sign-pss-4096-sha512, rsa-sign-raw-pkcs1-2048, rsa-sign-raw-pkcs1-3072, rsa-sign-raw-pkcs1-4096. |
| `--import-job` | IMPORT_JOB |  | Name of the import job to import from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key to import into. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--public-key-file` | PUBLIC_KEY_FILE |  | Path to the public key of the ImportJob, used to wrap the key for import. If missing, the public key will be fetched on your behalf. |
| `--target-key-file` | TARGET_KEY_FILE |  | Path to the unwrapped target key to import into a Cloud KMS key version. If specified, the key will be securely wrapped before transmission to Google. |
| `--version` | VERSION |  | Version to re-import into. Omit this field for first-time import. |
| `--wrapped-key-file` | WRAPPED_KEY_FILE |  | Path to the RSA/RSA+AES wrapped key file to import. |


**Examples:**
```bash
The following command will read the files 'path/to/ephemeral/key' and
'path/to/target/key' and use them to create a new version with algorithm
'google-symmetric-encryption' within the 'frodo' crypto key, 'fellowship'
keyring, and 'us-central1' location using import job 'strider' to unwrap
the provided key material.

    $ gcloud kms keys versions import --location=global \
        --keyring=fellowship --key=frodo --import-job=strider \
        --wrapped-key-file=path/to/target/key \
        --algorithm=google-symmetric-encryption
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/import)

---
### `gcloud kms keys versions list`

List the versions within a key

Lists all of the versions within the given key.

**Synopsis:**
```
gcloud kms keys versions list [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |


**Examples:**
```bash
The following command lists all versions within the key frodo, keyring
fellowship, and location global:

    $ gcloud kms keys versions list --location=global \
        --keyring=fellowship --key=frodo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/list)

---
### `gcloud kms keys versions restore`

Restore a version scheduled for destruction

Restores the given version that was scheduled to be destroyed.

This moves the version from Scheduled for destruction to Disabled. Only
versions which are Scheduled for destruction can be Restored.

**Synopsis:**
```
gcloud kms keys versions restore VERSION [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to restore.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |


**Examples:**
```bash
The following command restores version 9 of key frodo within keyring
fellowship and location us-east1 which was previously scheduled for
destruction:

    $ gcloud kms keys versions restore 9 --location=us-east1 \
        --keyring=fellowship --key=frodo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/restore)

---
### `gcloud kms keys versions update`

Update a key version

gcloud kms keys versions update can be used to update the key versions.
Updates can be made to the the key versions's state (enabling or disabling
it), to its external key URI (if the key version has protection level
EXTERNAL), or to its ekm connection key path (if the key version has
protection level EXTERNAL_VPC).

**Synopsis:**
```
gcloud kms keys versions update VERSION
    [--ekm-connection-key-path=EKM_CONNECTION_KEY_PATH]
    [--external-key-uri=EXTERNAL_KEY_URI] [--key=KEY] [--keyring=KEYRING]
    [--location=LOCATION] [--state=STATE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION
   Name of the version to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ekm-connection-key-path` | EKM_CONNECTION_KEY_PATH |  | The path to the external key material on the EKM for keys with protection level "external-vpc". |
| `--external-key-uri` | EXTERNAL_KEY_URI |  | The URI of the external key for keys with protection level "external". |
| `--key` | KEY |  | The containing key. |
| `--keyring` | KEYRING |  | Key ring of the key. |
| `--location` | LOCATION |  | Location of the keyring. |
| `--state` | STATE |  | State of the key version. |


**Examples:**
```bash
The following command enables the key version 8 of key frodo within keyring
fellowship and location us-east1:

    $ gcloud kms keys versions update 8 --location=us-east1 \
        --keyring=fellowship --key=frodo --state=enabled

The following command disables the key version 8 of key frodo within
keyring fellowship and location us-east1:

    $ gcloud kms keys versions update 8 --location=us-east1 \
        --keyring=fellowship --key=frodo --state=disabled

The following command updates the external key URI of version 8 of key
frodo within keyring fellowship and location us-east1:

    $ gcloud kms keys versions update 8 --location=us-east1 \
        --keyring=fellowship --key=frodo \
        --external-key-uri=https://example.kms/v0/some/key/path

The following command updates the ekm connection key path of version 8 of
key bilbo within keyring fellowship and location us-east1:

    $ gcloud kms keys versions update 8 --location=us-east1 \
        --keyring=fellowship --key=bilbo \
        --ekm-connection-key-path=v0/some/key/path
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/keys/versions/update)

---
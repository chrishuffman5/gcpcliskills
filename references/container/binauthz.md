# gcloud container binauthz

manage attestations for Binary Authorization on Google Cloud Platform

### `gcloud container binauthz create-signature-payload`

Create a JSON container image signature object

Given a container image URL specified by the manifest digest, this command
will produce a JSON object whose signature is expected by Cloud Binary
Authorization.

**Synopsis:**
```
gcloud container binauthz create-signature-payload
    --artifact-url=ARTIFACT_URL [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--artifact-url` | ARTIFACT_URL |  | Container URL. May be in the gcr.io/repository/image format, or may optionally contain the http or https scheme |


**Examples:**
```bash
To output serialized JSON to sign, run:

    $ gcloud container binauthz create-signature-payload \
      --artifact-url="gcr.io/example-project/example-image@sha256:abcd\
    "
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/create-signature-payload)

---

## `gcloud container binauthz attestations` — create and manage Google Binary Authorization attestations
### `gcloud container binauthz attestations create`

Create a Binary Authorization attestation

This command creates a Binary Authorization attestation for your project.
The attestation is created for the specified artifact (e.g. a gcr.io
container URL), associate with the specified attestor, and stored under the
specified project.

**Synopsis:**
```
gcloud container binauthz attestations create --artifact-url=ARTIFACT_URL
    --public-key-id=PUBLIC_KEY_ID --signature-file=SIGNATURE_FILE
    [--payload-file=PAYLOAD_FILE]
    [[--note=NOTE : --note-project=NOTE_PROJECT]
      | --validate [--attestor=ATTESTOR
      : --attestor-project=ATTESTOR_PROJECT]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--artifact-url` | ARTIFACT_URL |  | Container URL. May be in the gcr.io/repository/image format, or may optionally contain the http or https scheme |
| `--public-key-id` | PUBLIC_KEY_ID |  | The ID of the public key that will be used to verify the signature of the created Attestation. This ID must match the one found on the Attestor resource(s) which will verify this Attestation. For PGP keys, this must be the version 4, full 160-bit fingerprint, expressed as a 40 character hexadecimal string. See https://tools.ietf.org/html/rfc4880#section-12.2 for details. |
| `--signature-file` | SIGNATURE_FILE |  | Path to file containing the signature to store, or - to read signature from stdin. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--payload-file` | PAYLOAD_FILE |  | Path to file containing the payload over which the signature was calculated. This defaults to the output of the standard payload command: $ gcloud container binauthz create-signature-payload NOTE: If you sign a payload with e.g. different whitespace or formatting, you must explicitly provide the payload content via this flag. |


**Examples:**
```bash
To create an attestation in the project "my_proj" as the attestor with
resource path "projects/foo/attestors/bar", run:

    $ gcloud container binauthz attestations create --project=my_proj \
      --artifact-url='gcr.io/example-project/example-image@sha256:abcd\
    ' --attestor=projects/foo/attestors/bar \
        --signature-file=signed_artifact_attestation.pgp.sig \
        --public-key-id=AAAA0000000000000000FFFFFFFFFFFFFFFFFFFF

To create an attestation in the project "my_proj" in note
"projects/foo/notes/bar", run:

    $ gcloud container binauthz attestations create --project=my_proj \
      --artifact-url='gcr.io/example-project/example-image@sha256:abcd\
    ' --note=projects/foo/notes/bar \
        --signature-file=signed_artifact_attestation.pgp.sig \
        --public-key-id=AAAA0000000000000000FFFFFFFFFFFFFFFFFFFF
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestations/create)

---
### `gcloud container binauthz attestations list`

List Binary Authorization attestations

This command lists Binary Authorization attestations for your project.
Command line flags specify which attestor and artifact to list the
attestations for. If no attestor is specified, this lists all attestations
in the project, which requires the containeranalysis.occurrences.get
permission. If no artifact is specified, then this lists all URLs with
associated occurrences.

**Synopsis:**
```
gcloud container binauthz attestations list [--artifact-url=ARTIFACT_URL]
    [--attestor=ATTESTOR : --attestor-project=ATTESTOR_PROJECT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--artifact-url` | ARTIFACT_URL |  | Container URL. May be in the gcr.io/repository/image format, or may optionally contain the http or https scheme |


**Examples:**
```bash
List the Occurrence messages for all attestations bound to the passed
attestor:

    $ gcloud container binauthz attestations list \
      --attestor=projects/foo/attestor/bar

List the Occurrence messages for all attestations for the passed
artifact-url bound to the passed attestor:

    $ gcloud container binauthz attestations list \
      --attestor=projects/foo/attestors/bar \
      --artifact-url='gcr.io/foo/example-image@sha256:abcd'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestations/list)

---

## `gcloud container binauthz attestors` — create and manage Google Binary Authorization Attestors
### `gcloud container binauthz attestors add-iam-policy-binding`

Add IAM policy binding to a Binary Authorization attestor

Add an IAM policy binding to the IAM policy of a Binary Authorization
attestor. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud container binauthz attestors add-iam-policy-binding ATTESTOR
    --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The Binary Authorization attestor whose IAM policy to
add an IAM policy binding to. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument attestor on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the attestor attribute:
     + provide the argument attestor on the command line.
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
roles/binaryauthorization.attestorsEditor for the user test-user@gmail.com
on attestor my_attestor, run:

    $ gcloud container binauthz attestors add-iam-policy-binding \
        my_attestor --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestorsEditor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of roles/binaryauthorization.attestorsEditor and the user
test-user@gmail.com on attestor my_attestor, run:

    $ gcloud container binauthz attestors add-iam-policy-binding \
        my_attestor --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestorsEditor' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/add-iam-policy-binding)

---
### `gcloud container binauthz attestors create`

Create an Attestor

Create an Attestor.

**Synopsis:**
```
gcloud container binauthz attestors create ATTESTOR
    (--attestation-authority-note=ATTESTATION_AUTHORITY_NOTE
      : --attestation-authority-note-project=ATTESTATION_AUTHORITY_NOTE_PROJECT)
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The attestor to be created. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument ATTESTOR on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the name attribute:
     + provide the argument ATTESTOR on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attestation-authority-note` | ATTESTATION_AUTHORITY_NOTE |  | _[This must be specified.]_ ID of the note or fully qualified identifier for the note. To set the note attribute: + provide the argument --attestation-authority-note on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--attestation-authority-note-project` | ATTESTATION_AUTHORITY_NOTE_PROJECT |  | _[This must be specified.]_ The Container Analysis project for the note. To set the project attribute: + provide the argument --attestation-authority-note on the command line with a fully specified name; + provide the argument --attestation-authority-note-project on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description for the attestor |


**Examples:**
```bash
To create an Attestor with an existing Note projects/my_proj/notes/my_note:

    $ gcloud container binauthz attestors create my_new_attestor \
        --attestation-authority-note=my_note \
        --attestation-authority-note-project=my_proj
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/create)

---
### `gcloud container binauthz attestors delete`

Delete an Attestor

**Synopsis:**
```
gcloud container binauthz attestors delete ATTESTOR [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The attestor to be deleted. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument ATTESTOR on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the name attribute:
     + provide the argument ATTESTOR on the command line.
```

**Examples:**
```bash
To delete an existing Attestor my_attestor:

    $ gcloud container binauthz attestors delete my_attestor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/delete)

---
### `gcloud container binauthz attestors describe`

Describe an Attestor

**Synopsis:**
```
gcloud container binauthz attestors describe ATTESTOR
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The attestor to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument ATTESTOR on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the name attribute:
     + provide the argument ATTESTOR on the command line.
```

**Examples:**
```bash
To describe an existing Attestor my_attestor:

    $ gcloud container binauthz attestors describe my_attestor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/describe)

---
### `gcloud container binauthz attestors get-iam-policy`

Get the IAM policy for an attestor

Returns an empty policy if the resource does not have an existing IAM
policy set.

**Synopsis:**
```
gcloud container binauthz attestors get-iam-policy ATTESTOR
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The attestor whose IAM policy will be fetched. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument ATTESTOR on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the name attribute:
     + provide the argument ATTESTOR on the command line.
```

**Examples:**
```bash
The following command gets the IAM policy for the attestor my_attestor:

    $ gcloud container binauthz attestors get-iam-policy my_attestor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/get-iam-policy)

---
### `gcloud container binauthz attestors list`

List Attestors associated with the current project

**Synopsis:**
```
gcloud container binauthz attestors list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list attestors:

    $ gcloud container binauthz attestors list

To list attestors in a verbose format (including information about public
keys associated with each attestor:

    $ gcloud container binauthz attestors list --format=yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/list)

---
### `gcloud container binauthz attestors remove-iam-policy-binding`

Remove IAM policy binding of a Binary Authorization attestor

Remove an IAM policy binding from the IAM policy of a Binary Authorization
attestor. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud container binauthz attestors remove-iam-policy-binding ATTESTOR
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The Binary Authorization attestor whose IAM policy to
remove an IAM policy binding from. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument attestor on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the attestor attribute:
     + provide the argument attestor on the command line.
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
roles/binaryauthorization.attestorsEditor for the user test-user@gmail.com
on attestor my_attestor, run:

    $ gcloud container binauthz attestors remove-iam-policy-binding \
        my_attestor --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestorsEditor'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of roles/binaryauthorization.attestorsEditor and the user
test-user@gmail.com on attestor my_attestor, run:

    $ gcloud container binauthz attestors remove-iam-policy-binding \
        my_attestor --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestorsEditor' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/remove-iam-policy-binding)

---
### `gcloud container binauthz attestors set-iam-policy`

Set the IAM policy for an attestor

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud container binauthz attestors set-iam-policy ATTESTOR_NAME
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ATTESTOR_NAME
   The name of the attestor whose IAM policy will be updated.

POLICY_FILE
   The JSON or YAML file containing the IAM policy.
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'iam_policy.json' and set it for the attestor my_attestor:

    $ gcloud container binauthz attestors set-iam-policy my_attestor \
        iam_policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/set-iam-policy)

---
### `gcloud container binauthz attestors update`

Update an existing Attestor

**Synopsis:**
```
gcloud container binauthz attestors update ATTESTOR
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Attestor resource - The attestor to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument ATTESTOR on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ATTESTOR
     ID of the attestor or fully qualified identifier for the attestor.

     To set the name attribute:
     + provide the argument ATTESTOR on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The new description for the attestor |


**Examples:**
```bash
To update an existing Attestor my_attestor:

    $ gcloud container binauthz attestors update my_attestor \
        --description="my new attestor description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/update)

---

## `gcloud container binauthz attestors public-keys` — create and manage public keys associated with Attestation Authorities
### `gcloud container binauthz attestors public-keys add`

Add a public key to an Attestor

**Synopsis:**
```
gcloud container binauthz attestors public-keys add --attestor=ATTESTOR
    (--pgp-public-key-file=PATH_TO_FILE | (--keyversion=KEYVERSION
      : --keyversion-key=KEYVERSION_KEY
      --keyversion-keyring=KEYVERSION_KEYRING
      --keyversion-location=KEYVERSION_LOCATION
      --keyversion-project=KEYVERSION_PROJECT)
      | --pkix-public-key-algorithm=PKIX_PUBLIC_KEY_ALGORITHM
      --pkix-public-key-file=PATH_TO_FILE) [--comment=COMMENT]
    [--public-key-id-override=PUBLIC_KEY_ID_OVERRIDE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attestor` | ATTESTOR |  | _[This must be specified.]_ ID of the attestor or fully qualified identifier for the attestor. To set the name attribute: + provide the argument --attestor on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--comment` | COMMENT |  | The comment describing the public key. |
| `--public-key-id-override` | PUBLIC_KEY_ID_OVERRIDE |  | If provided, the ID to replace the default API-generated one. All IDs must be valid URIs as defined by RFC 3986 (https://tools.ietf.org/html/rfc3986). When creating Attestations to be verified by this key, one must always provide this custom ID as the public key ID. |


**Examples:**
```bash
To add a new KMS public key to an existing Attestor my_attestor:

    $ gcloud container binauthz attestors public-keys add \
        --attestor=my_attestor --keyversion-project=foo \
        --keyversion-location=us-west1 --keyversion-keyring=aring \
        --keyversion-key=akey --keyversion=1

To add a new PGP public key to an existing Attestor my_attestor:

    $ gcloud container binauthz attestors public-keys add \
        --attestor=my_attestor --pgp-public-key-file=my_key.pub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/public-keys/add)

---
### `gcloud container binauthz attestors public-keys remove`

Remove a public key from an Attestor

**Synopsis:**
```
gcloud container binauthz attestors public-keys remove PUBLIC_KEY_ID
    --attestor=ATTESTOR [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PUBLIC_KEY_ID
   The ID of the public key to remove.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attestor` | ATTESTOR |  | _[This must be specified.]_ ID of the attestor or fully qualified identifier for the attestor. To set the name attribute: + provide the argument --attestor on the command line. |


**Examples:**
```bash
To remove a public key from the Attestor my_attestor:

    $ gcloud container binauthz attestors public-keys remove \
        0638AADD940361EA2D7F14C58C124F0E663DA097 --attestor=my_attestor
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/public-keys/remove)

---
### `gcloud container binauthz attestors public-keys update`

Update a public key on an Attestor

**Synopsis:**
```
gcloud container binauthz attestors public-keys update PUBLIC_KEY_ID
    --attestor=ATTESTOR [--comment=COMMENT]
    [--pgp-public-key-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PUBLIC_KEY_ID
   The ID of the public key to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attestor` | ATTESTOR |  | _[This must be specified.]_ ID of the attestor or fully qualified identifier for the attestor. To set the name attribute: + provide the argument --attestor on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--comment` | COMMENT |  | The comment describing the public key. |
| `--pgp-public-key-file` | PATH_TO_FILE |  | The path to a file containing the updated ASCII-armored PGP public key. Use a full or relative path to a local file containing the value of pgp_public_key_file. |


**Examples:**
```bash
To update a PGP public key on an existing Attestor my_attestor:

    $ gcloud container binauthz attestors public-keys update \
        0638AADD940361EA2D7F14C58C124F0E663DA097 \
        --attestor=my_attestor --pgp-public-key-file=my_key.pub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/attestors/public-keys/update)

---

## `gcloud container binauthz policy` — create and manage Google Binary Authorization policies
### `gcloud container binauthz policy add-iam-policy-binding`

Add IAM policy binding to a Binary Authorization policy

Add an IAM policy binding to the IAM policy of a Binary Authorization
policy. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud container binauthz policy add-iam-policy-binding --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
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


**Examples:**
```bash
To add an IAM policy binding for the role of
'roles/binaryauthorization.attestationAuthoritiesEditor' for the user
'test-user@gmail.com' on the current project's Binary Authorization policy,
run:

    $ gcloud container binauthz policy add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestationAuthoritiesEditor'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/binaryauthorization.attestationAuthoritiesEditor' and
the user 'test-user@gmail.com' on the current project's Binary
Authorization policy, run:

    $ gcloud container binauthz policy add-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestationAuthoritiesEditor' \
    --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/policy/add-iam-policy-binding)

---
### `gcloud container binauthz policy export`

Export the Binary Authorization policy for the current project

This function's default output is a valid policy YAML file. If dumped to a
file and edited, the new policy can be provided to the $ gcloud container
binauthz policy import command to cause these edits to be reflected in the
project policy.

**Synopsis:**
```
gcloud container binauthz policy export [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To export the current project's policy:

    $ gcloud container binauthz policy export > my_policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/policy/export)

---
### `gcloud container binauthz policy get-iam-policy`

Get the IAM policy for a Binary Authorization policy

Returns an empty policy if the resource does not have an existing IAM
policy set.

**Synopsis:**
```
gcloud container binauthz policy get-iam-policy [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command gets the IAM policy for the current project's Binary
Authorization policy:

    $ gcloud container binauthz policy get-iam-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/policy/get-iam-policy)

---
### `gcloud container binauthz policy import`

Import a Binary Authorization policy to the current project

This command accepts a description of the desired policy in the form of a
YAML-formatted file. A representation of the current policy can be
retrieved using the $ gcloud container binauthz policy export command. One
method of modifying the policy is to run $ gcloud container binauthz policy
export, dump the contents to a file, modify the policy file to reflect the
desired new policy, and provide this modified file to $ gcloud container
binauthz policy import.

**Synopsis:**
```
gcloud container binauthz policy import POLICY_FILE [--strict-validation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   The file containing the YAML-formatted policy description.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--strict-validation` |  |  | Whether to perform additional checks on the validity of policy contents. |


**Examples:**
```bash
To update the current project's policy:

    $ gcloud container binauthz policy export > my_policy.yaml

    $ edit my_policy.yaml

    $ gcloud container binauthz policy import my_policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/policy/import)

---
### `gcloud container binauthz policy remove-iam-policy-binding`

Remove IAM policy binding of a Binary Authorization policy

Remove an IAM policy binding from the IAM policy of a Binary Authorization
policy. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud container binauthz policy remove-iam-policy-binding
    --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
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
'roles/binaryauthorization.attestationAuthoritiesEditor' for the user
'test-user@gmail.com' on the current project's Binary Authorization policy,
run:

    $ gcloud container binauthz policy remove-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestationAuthoritiesEditor'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/binaryauthorization.attestationAuthoritiesEditor'
and the user 'test-user@gmail.com' on the current project's Binary
Authorization policy, run:

    $ gcloud container binauthz policy remove-iam-policy-binding \
        --member='user:test-user@gmail.com' \
        --role='roles/binaryauthorization.attestationAuthoritiesEditor' \
    --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/policy/remove-iam-policy-binding)

---
### `gcloud container binauthz policy set-iam-policy`

Set the IAM policy for a Binary Authorization policy

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud container binauthz policy set-iam-policy POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   The JSON or YAML file containing the IAM policy.
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'iam_policy.json' and set it for the current project's Binary Authorization
policy:

    $ gcloud container binauthz policy set-iam-policy iam_policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/binauthz/policy/set-iam-policy)

---
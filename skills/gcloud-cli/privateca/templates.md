# gcloud privateca templates

manage certificate templates

### `gcloud privateca templates add-iam-policy-binding`

Add IAM policy binding for a certificate template

Adds a policy binding to the IAM policy of a certificate template. One
binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud privateca templates add-iam-policy-binding
    (CERTIFICATE_TEMPLATE : --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate Template resource - The certificate template for which to add
the IAM policy binding. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the Certificate Template or fully qualified identifier for the
     Certificate Template.

     To set the certificate_template attribute:
     + provide the argument certificate_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Certificate Template.

     To set the location attribute:
     + provide the argument certificate_template on the command line
       with a fully specified name;
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
To add an IAM policy binding for the role of 'roles/privateca.templateUser'
for the user 'test-user@gmail.com' on the certificate template
'mtls-template' with the location 'us-west1', run:

    $ gcloud privateca templates add-iam-policy-binding mtls-template \
        --location='us-west1' --member='user:test-user@gmail.com' \
        --role='roles/privateca.templateUser'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/add-iam-policy-binding)

---
### `gcloud privateca templates create`

Create a new certificate template

Create a certificate template that enforces policy restrictions on
certificate requestors. Using a certificate template, you can define
restrictions on the kinds of Subjects/SANs and x509 extensions allowed from
certificate requestors as well as a default set of x509 extensions that
should be applied to all certificates using that template. These templates
can be binded to IAM identities such that certain groups of requestors must
use particular templates, allowing for fine-grained policy enforcements
based on identity.

For more information and examples, see
https://cloud.google.com/certificate-authority-service/docs/creating-certificate-template.

**Synopsis:**
```
gcloud privateca templates create
    (CERTIFICATE_TEMPLATE : --location=LOCATION) --copy-sans --copy-subject
    [--description=DESCRIPTION]
    [--identity-cel-expression=IDENTITY_CEL_EXPRESSION]
    [--labels=[KEY=VALUE,...]] [--maximum-lifetime=MAXIMUM_LIFETIME]
    [--predefined-values-file=PREDEFINED_VALUES_FILE]
    [--copy-all-requested-extensions
      | --copy-extensions-by-oid=[OBJECT_ID,...]
      --copy-known-extensions=[KNOWN_EXTENSIONS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE TEMPLATE resource - The template to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_TEMPLATE on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the CERTIFICATE_TEMPLATE or fully qualified identifier for the
     CERTIFICATE_TEMPLATE.

     To set the certificate template attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_TEMPLATE.

     To set the location attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--copy-sans` |  |  | If this is specified, the Subject Alternative Name extension from the certificate request will be copied into the signed certificate. Specify --no-copy-sans to drop any caller-specified SANs in the certificate request. |
| `--copy-subject` |  |  | If this is specified, the Subject from the certificate request will be copied into the signed certificate. Specify --no-copy-subject to drop any caller-specified subjects from the certificate request. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A text description for the Certificate Template. |
| `--identity-cel-expression` | IDENTITY_CEL_EXPRESSION |  | A CEL expression that will be evaluated against the identity in the certificate before it is issued, and returns a boolean signifying whether the request should be allowed. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--maximum-lifetime` | MAXIMUM_LIFETIME |  | If this is set, then issued certificate's lifetime will be truncated to the value provided. If the issuing CaPool's IssuancePolicy specifies a maximum lifetime the minimum of the two durations will be the maximum lifetime for the issued certificate. Note that if the issuing CertificateAuthority expires before a Certificate's requested maximum_lifetime, the effective lifetime will be explicitly truncated to match it. |
| `--predefined-values-file` | PREDEFINED_VALUES_FILE |  | A YAML file describing any predefined X.509 values set by this template. The provided extensions will be copied over to any certificate requests that use this template, taking precedent over any allowed extensions in the certificate request. The format of this file should be a YAML representation of the X509Parameters message, which is defined here: https://cloud.google.com/certificate-authority-service/docs/reference/rest/v1/X509Parameters. Some examples can be found here: https://cloud.google.com/certificate-authority-service/docs/creating-certificate-template |


**Examples:**
```bash
To create a template that prohibits any x509 extension from a requester,
but permits custom subjects/SANs and defines the default x509 extensions,
run:

    $ gcloud privateca templates create restricted-template \
        --location=us-west1 --copy-subject --copy-sans \
        --predefined-values-file=x509_parameters.yaml

To create a template that allows requesters to specify only DNS names from
requesters, use a custom CEL expression with a SAN only restriction:

    $ gcloud privateca templates create dns-only-template \
        --location=us-west1 \
        --description="Restricts certificates to DNS SANs." \
        --no-copy-subject --copy-sans \
        --identity-cel-expression="subject_alt_names.all(san, san.type \
    == DNS)"

To create a template that permits a requestor to specify extensions by
OIDs, and subjects (but not SANs), with default x509 exensions:

    $ gcloud privateca templates create mtls-only-extensions \
        --location=us-west1 --copy-subject --no-copy-sans \
        --predefined-values-file=mtls_cert_exts.yaml \
        --copy-extensions-by-oid=1.3.6.1.5.5.7.3.2,1.3.6.1.5.5.7.3.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/create)

---
### `gcloud privateca templates delete`

Delete a certificate template

**Synopsis:**
```
gcloud privateca templates delete
    (CERTIFICATE_TEMPLATE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE TEMPLATE resource - The template to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_TEMPLATE on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the CERTIFICATE_TEMPLATE or fully qualified identifier for the
     CERTIFICATE_TEMPLATE.

     To set the certificate template attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_TEMPLATE.

     To set the location attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Examples:**
```bash
To delete a certificate template:

    $ gcloud privateca templates delete my-template --location=us-west1

To delete a certificate template while skipping the confirmation input:

    $ gcloud privateca templates delete my-template \
        --location=us-west1 --quiet
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/delete)

---
### `gcloud privateca templates describe`

Show details about a certificate template

Show details about a certificate template.

**Synopsis:**
```
gcloud privateca templates describe
    (CERTIFICATE_TEMPLATE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate Template resource - The certificate template you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the Certificate Template or fully qualified identifier for the
     Certificate Template.

     To set the certificate_template attribute:
     + provide the argument certificate_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Certificate Template.

     To set the location attribute:
     + provide the argument certificate_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Examples:**
```bash
To show details about a certificate template, run:

    $ gcloud privateca templates describe my-template \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/describe)

---
### `gcloud privateca templates get-iam-policy`

Get the IAM policy for a certificate template

Gets the IAM policy for the given certificate template.

    Returns an empty policy if the resource does not have a policy
    set.

**Synopsis:**
```
gcloud privateca templates get-iam-policy
    (CERTIFICATE_TEMPLATE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate Template resource - The certificate template for which to
display the IAM policy. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the Certificate Template or fully qualified identifier for the
     Certificate Template.

     To set the certificate_template attribute:
     + provide the argument certificate_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Certificate Template.

     To set the location attribute:
     + provide the argument certificate_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Examples:**
```bash
To get the IAM policy for the certificate template 'mtls-template' with the
location 'us-west1', run:

    $ gcloud privateca templates get-iam-policy mtls-template \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/get-iam-policy)

---
### `gcloud privateca templates list`

List certificate templates within a project

List certificate templates.

**Synopsis:**
```
gcloud privateca templates list [--location=LOCATION; default="-"]
    [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]; default="name"] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | - | The location you want to list the certificate templates for. Set this to "-" to list certificate templates across all locations. |


**Examples:**
```bash
To list all certificate templates in a project across all locations, run:

    $ gcloud privateca templates list

To list all certificate templates in a project and location 'us-central1',
run:

    $ gcloud privateca templates list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/list)

---
### `gcloud privateca templates remove-iam-policy-binding`

Remove IAM policy binding for a certificate template

Removes a policy binding to the IAM policy of a certificate template. One
binding consists of a member and a role.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud privateca templates remove-iam-policy-binding
    (CERTIFICATE_TEMPLATE : --location=LOCATION) --member=PRINCIPAL
    --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate Template resource - The certificate template for which to
remove the IAM policy binding. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the Certificate Template or fully qualified identifier for the
     Certificate Template.

     To set the certificate_template attribute:
     + provide the argument certificate_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Certificate Template.

     To set the location attribute:
     + provide the argument certificate_template on the command line
       with a fully specified name;
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
'roles/privateca.templateUser' for the user 'test-user@gmail.com' on the
certificate template 'my-template' with the location 'us-west1', run:

    $ gcloud privateca templates remove-iam-policy-binding my-template \
        --location=us-west1 --member='user:test-user@gmail.com' \
        --role='roles/privateca.templateUser'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/remove-iam-policy-binding)

---
### `gcloud privateca templates replicate`

Replicate a certificate template to multiple locations

Replicate a certificate template to multiple locations.

**Synopsis:**
```
gcloud privateca templates replicate
    (CERTIFICATE_TEMPLATE : --location=LOCATION)
    (--all-locations | --target-locations=[LOCATION,...])
    [--continue-on-error] [--overwrite] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE TEMPLATE resource - The template to replicate. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_TEMPLATE on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the CERTIFICATE_TEMPLATE or fully qualified identifier for the
     CERTIFICATE_TEMPLATE.

     To set the certificate template attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_TEMPLATE.

     To set the location attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-locations` |  |  | _[Exactly one of these must be specified:]_ Replicate this template to all supported locations. |
| `--target-locations` | [LOCATION,...] |  | _[Exactly one of these must be specified:]_ Replicate this template to the given locations. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--continue-on-error` |  |  | Continue replicating the template to other locations even if an error is encountered. If this is set, an error in one location will be logged but will not prevent replication to other locations. |
| `--overwrite` |  |  | Overwrite any existing templates with the same name, if they exist. |


**Examples:**
```bash
To replicate a certificate templates to all supported locations, run:

    $ gcloud privateca templates replicate my-template \
        --location=us-west1 --all-locations

To replicate a certificate template to 'us-west2' and 'us-east1', run:

    $ gcloud privateca templates replicate my-template \
        --location=us-west1 --target-locations=us-west2,us-east1

To overwrite existing templates with the same resource ID in the target
locations, use the --overwrite flag:

    $ gcloud privateca templates replicate my-template \
        --location=us-west1 --target-locations=us-west2,us-east1 \
        --overwrite

To continue replicating templates in other locations in the event of a
failure in one or more locations, use the --continue-on-error flag:

    $ gcloud privateca templates replicate my-template \
        --location=us-west1 --all-locations --continue-on-error
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/replicate)

---
### `gcloud privateca templates set-iam-policy`

Set the IAM policy for a certificate template

Sets the IAM policy for the given certificate template as defined in a JSON
or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud privateca templates set-iam-policy
    (CERTIFICATE_TEMPLATE : --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate Template resource - The certificate template for which to
update the IAM policy. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument certificate_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the Certificate Template or fully qualified identifier for the
     Certificate Template.

     To set the certificate_template attribute:
     + provide the argument certificate_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Certificate Template.

     To set the location attribute:
     + provide the argument certificate_template on the command line
       with a fully specified name;
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
'policy.json' and set it for the certificate template 'my-template' with
the location 'us-west1':

    $ gcloud privateca templates set-iam-policy my-template \
        --location=us-west1 policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/set-iam-policy)

---
### `gcloud privateca templates update`

Update a certificate template

Update a certificate template.

**Synopsis:**
```
gcloud privateca templates update
    (CERTIFICATE_TEMPLATE : --location=LOCATION) [--copy-sans]
    [--copy-subject] [--description=DESCRIPTION]
    [--identity-cel-expression=IDENTITY_CEL_EXPRESSION]
    [--predefined-values-file=PREDEFINED_VALUES_FILE]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--copy-all-requested-extensions
      | --copy-extensions-by-oid=[OBJECT_ID,...] | --drop-oid-extensions
      --copy-known-extensions=[KNOWN_EXTENSIONS,...]
      | --drop-known-extensions] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CERTIFICATE TEMPLATE resource - The template to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument CERTIFICATE_TEMPLATE on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CERTIFICATE_TEMPLATE
     ID of the CERTIFICATE_TEMPLATE or fully qualified identifier for the
     CERTIFICATE_TEMPLATE.

     To set the certificate template attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the CERTIFICATE_TEMPLATE.

     To set the location attribute:
     + provide the argument CERTIFICATE_TEMPLATE on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property privateca/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--copy-sans` |  |  | If this is specified, the Subject Alternative Name extension from the certificate request will be copied into the signed certificate. Specify --no-copy-sans to drop any caller-specified SANs in the certificate request. |
| `--copy-subject` |  |  | If this is specified, the Subject from the certificate request will be copied into the signed certificate. Specify --no-copy-subject to drop any caller-specified subjects from the certificate request. |
| `--description` | DESCRIPTION |  | A text description for the Certificate Template. |
| `--identity-cel-expression` | IDENTITY_CEL_EXPRESSION |  | A CEL expression that will be evaluated against the identity in the certificate before it is issued, and returns a boolean signifying whether the request should be allowed. |
| `--predefined-values-file` | PREDEFINED_VALUES_FILE |  | A YAML file describing any predefined X.509 values set by this template. The provided extensions will be copied over to any certificate requests that use this template, taking precedent over any allowed extensions in the certificate request. The format of this file should be a YAML representation of the X509Parameters message, which is defined here: https://cloud.google.com/certificate-authority-service/docs/reference/rest/v1/X509Parameters. Some examples can be found here: https://cloud.google.com/certificate-authority-service/docs/creating-certificate-template |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a template named "dns-restricted" with new default x509
extensions:

    $ gcloud privateca templates update dns-restricted \
        --location=us-west1 \
        --predefined-values-file=x509_parameters.yaml

To update a template named "dns-restricted" to allow requestors to specify
subject:

    $ gcloud privateca templates update dns-restricted \
        --location=us-west1 --copy-subject

To update a template named "dns-restricted" with allowed extension
'base-key-usage' to allow requestors to specify additional x509 extension
'extended-key-usage':

    $ gcloud privateca templates update dns-restricted \
        --location=us-west1 \
        --copy-known-extensions=base-key-usage,extended-key-usage

To update a template named "mtls-restricted" with allowed OID '1.1' to
allow requestors to specify alternative OIDS '2.2,3.3':

    $ gcloud privateca templates update mtls-restricted \
        --location=us-west1 --copy-extensions-by-oid=2.2,3.3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/privateca/templates/update)

---
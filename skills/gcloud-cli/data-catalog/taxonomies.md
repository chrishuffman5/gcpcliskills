# gcloud data-catalog taxonomies

manage taxonomies in Data Catalog

### `gcloud data-catalog taxonomies add-iam-policy-binding`

Add an IAM policy binding to a Policy Tag Taxonomy

Add an IAM policy binding to a Policy Tag Taxonomy.

**Synopsis:**
```
gcloud data-catalog taxonomies add-iam-policy-binding
    (TAXONOMY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Taxonomy resource - Policy tag taxonomy for which to add an IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument taxonomy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAXONOMY
     ID of the taxonomy or fully qualified identifier for the taxonomy.

     To set the taxonomy attribute:
     + provide the argument taxonomy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the taxonomy.

     To set the location attribute:
     + provide the argument taxonomy on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with taxonomy 'TAXONOMY' in location 'LOCATION', run:

    $ gcloud data-catalog taxonomies add-iam-policy-binding TAXONOMY \
        --location='LOCATION' --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/add-iam-policy-binding)

---
### `gcloud data-catalog taxonomies describe`

Describe a Policy Tag Taxonomy

Describe a Policy Tag Taxonomy.

**Synopsis:**
```
gcloud data-catalog taxonomies describe (TAXONOMY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Taxonomy resource - Policy tag taxonomy to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument taxonomy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAXONOMY
     ID of the taxonomy or fully qualified identifier for the taxonomy.

     To set the taxonomy attribute:
     + provide the argument taxonomy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the taxonomy.

     To set the location attribute:
     + provide the argument taxonomy on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the Taxonomy 'TAXONOMY' in the location 'LOCATION', run:

    $ gcloud data-catalog taxonomies describe TAXONOMY \
        --location='LOCATION'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/describe)

---
### `gcloud data-catalog taxonomies export`

Export a list of taxonomies from a certain project

Export a list of taxonomies from a certain project.

**Synopsis:**
```
gcloud data-catalog taxonomies export TAXONOMIES --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TAXONOMIES
   List of taxonomies to bring.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To export 'TAXONOMY1' and 'TAXONOMY2' from your project within location
LOCATION and render the export on the command line:

    $ gcloud data-catalog taxonomies export "TAXONOMY1,TAXONOMY2" \
        --location=LOCATION

To export 'TAXONOMY1' and 'TAXONOMY2' from your project within location
LOCATION and store the export into a file "/path/file.yaml":

    $ gcloud data-catalog taxonomies export "TAXONOMY1,TAXONOMY2" \
        --location=LOCATION > /path/file.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/export)

---
### `gcloud data-catalog taxonomies get-iam-policy`

Get the IAM policy for a Policy Tag Taxonomy

gcloud data-catalog taxonomies get-iam-policy displays the IAM policy
associated with a Policy Tag Taxonomy. If formatted as JSON, the output can
be edited and used as a policy file for set-iam-policy. The output includes
an "etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ gcloud data-catalog taxonomies
set-iam-policy for additional details.

**Synopsis:**
```
gcloud data-catalog taxonomies get-iam-policy
    (TAXONOMY : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Taxonomy resource - Policy tag taxonomy for which to display the IAM
policy. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument taxonomy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAXONOMY
     ID of the taxonomy or fully qualified identifier for the taxonomy.

     To set the taxonomy attribute:
     + provide the argument taxonomy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the taxonomy.

     To set the location attribute:
     + provide the argument taxonomy on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for 'TAXONOMY' in 'LOCATION', run:

    $ gcloud data-catalog taxonomies get-iam-policy TAXONOMY \
        --location='LOCATION'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/get-iam-policy)

---
### `gcloud data-catalog taxonomies import`

Export a file with serialized taxonomies to a certain project

Export a file with serialized taxonomies to a certain project.

**Synopsis:**
```
gcloud data-catalog taxonomies import TAXONOMIES --location=LOCATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TAXONOMIES
   File containing serialized taxonomy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To parse and import the taxonomies contained in '/tmp/taxonomies.json' to
your project within location LOCATION:

    $ gcloud data-catalog taxonomies import "/tmp/taxonomies.json" \
        --location="LOCATION"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/import)

---
### `gcloud data-catalog taxonomies list`

List Cloud Policy Tag Taxonomies

List Cloud Policy Tag Taxonomies.

**Synopsis:**
```
gcloud data-catalog taxonomies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
List the policy tag taxonomies for a location 'LOCATION':

    $ gcloud data-catalog taxonomies list --location='LOCATION'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/list)

---
### `gcloud data-catalog taxonomies remove-iam-policy-binding`

Remove an IAM policy binding from a policy tag taxonomy

Remove an IAM policy binding from a policy tag taxonomy.

**Synopsis:**
```
gcloud data-catalog taxonomies remove-iam-policy-binding
    (TAXONOMY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Taxonomy resource - Policy tag taxonomy from which to remove the IAM
policy binding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument taxonomy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAXONOMY
     ID of the taxonomy or fully qualified identifier for the taxonomy.

     To set the taxonomy attribute:
     + provide the argument taxonomy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the taxonomy.

     To set the location attribute:
     + provide the argument taxonomy on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on taxonomy 'TAXONOMY' in location 'LOCATION', run:

    $ gcloud data-catalog taxonomies remove-iam-policy-binding \
        TAXONOMY --location='LOCATION' \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on taxonomy 'TAXONOMY' in location 'LOCATION', run:

    $ gcloud data-catalog taxonomies remove-iam-policy-binding \
        TAXONOMY --location='LOCATION' \
        --member='allAuthenticatedUsers' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/remove-iam-policy-binding)

---
### `gcloud data-catalog taxonomies set-iam-policy`

Set the IAM policy for a Policy Tag taxonomy

Set the IAM policy for the given Policy Tag taxonomy as defined in a JSON
or YAML file.

**Synopsis:**
```
gcloud data-catalog taxonomies set-iam-policy
    (TAXONOMY : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Taxonomy resource - Policy tag taxonomy for which to set the IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument taxonomy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAXONOMY
     ID of the taxonomy or fully qualified identifier for the taxonomy.

     To set the taxonomy attribute:
     + provide the argument taxonomy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the taxonomy.

     To set the location attribute:
     + provide the argument taxonomy on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the taxonomy 'TAXONOMY' in location
'LOCATION':

    $ gcloud data-catalog taxonomies set-iam-policy TAXONOMY \
        --location='LOCATION' policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/set-iam-policy)

---

## `gcloud data-catalog taxonomies policy-tags` — manage policy tags in Data Catalog
### `gcloud data-catalog taxonomies policy-tags add-iam-policy-binding`

Add an IAM policy binding to a Data Catalog policy tag

Add an IAM policy binding to a Data Catalog policy tag.

**Synopsis:**
```
gcloud data-catalog taxonomies policy-tags add-iam-policy-binding
    (POLICY_TAG : --location=LOCATION --taxonomy=TAXONOMY)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy tag resource - Policy tag for which to add an IAM policy binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_tag on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_TAG
     ID of the policy tag or fully qualified identifier for the policy
     tag.

     To set the policy_tag attribute:
     + provide the argument policy_tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the policy tag.

     To set the location attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --taxonomy=TAXONOMY
     Taxonomy of the policy tag.

     To set the taxonomy attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --taxonomy on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with policy tag 'POLICY_TAG' in location 'LOCATION'
and taxonomy 'TAXONOMY', run:

    $ gcloud data-catalog taxonomies policy-tags \
        add-iam-policy-binding POLICY_TAG --location='LOCATION' \
        --taxonomy='TAXONOMY' --member='user:test-user@gmail.com' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/policy-tags/add-iam-policy-binding)

---
### `gcloud data-catalog taxonomies policy-tags describe`

Describe a Policy Tag Manager Policy tag

Describe a Policy Tag Manager Policy tag.

**Synopsis:**
```
gcloud data-catalog taxonomies policy-tags describe
    (POLICY_TAG : --location=LOCATION --taxonomy=TAXONOMY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy tag resource - Policy tag to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument policy_tag on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_TAG
     ID of the policy tag or fully qualified identifier for the policy
     tag.

     To set the policy_tag attribute:
     + provide the argument policy_tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the policy tag.

     To set the location attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --taxonomy=TAXONOMY
     Taxonomy of the policy tag.

     To set the taxonomy attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --taxonomy on the command line.
```

**Examples:**
```bash
To describe the Policy Tag 'POLICY_TAG' in the taxonomy 'TAXONOMY', run:

    $ gcloud data-catalog taxonomies policy-tags describe POLICY_TAG \
        --taxonomy='TAXONOMY' --location='LOCATION'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/policy-tags/describe)

---
### `gcloud data-catalog taxonomies policy-tags get-iam-policy`

Get the IAM policy for a Data Catalog Policy Tag

gcloud data-catalog taxonomies policy-tags get-iam-policy displays the IAM
policy associated with a Data Catalog Policy Tag. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates; see $ gcloud data-catalog
taxonomies policy-tags set-iam-policy for additional details.

**Synopsis:**
```
gcloud data-catalog taxonomies policy-tags get-iam-policy
    (POLICY_TAG : --location=LOCATION --taxonomy=TAXONOMY)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy tag resource - Policy tag for which to display the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_tag on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_TAG
     ID of the policy tag or fully qualified identifier for the policy
     tag.

     To set the policy_tag attribute:
     + provide the argument policy_tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the policy tag.

     To set the location attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --taxonomy=TAXONOMY
     Taxonomy of the policy tag.

     To set the taxonomy attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --taxonomy on the command line.
```

**Examples:**
```bash
To print the IAM policy for 'POLICY_TAG' in 'LOCATION' and 'TAXONOMY', run:

    $ gcloud data-catalog taxonomies policy-tags get-iam-policy \
        POLICY_TAG --taxonomy='TAXONOMY' --location='LOCATION'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/policy-tags/get-iam-policy)

---
### `gcloud data-catalog taxonomies policy-tags list`

List Cloud Policy Tag Manager policy tags

List Cloud Policy Tag Manager policy tags.

**Synopsis:**
```
gcloud data-catalog taxonomies policy-tags list
    (--taxonomy=TAXONOMY : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--taxonomy` | TAXONOMY |  | _[This must be specified.]_ ID of the taxonomy or fully qualified identifier for the taxonomy. To set the taxonomy attribute: + provide the argument --taxonomy on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the taxonomy. To set the location attribute: + provide the argument --taxonomy on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
List the policy tags for a Cloud Policy Tag Manager taxonomy 'TAXONOMY':

    $ gcloud data-catalog taxonomies policy-tags list \
        --taxonomy='TAXONOMY' --location='LOCATION'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/policy-tags/list)

---
### `gcloud data-catalog taxonomies policy-tags remove-iam-policy-binding`

Remove an IAM policy binding from a Data Catalog policy tag

Remove an IAM policy binding from a Data Catalog policy tag.

**Synopsis:**
```
gcloud data-catalog taxonomies policy-tags remove-iam-policy-binding
    (POLICY_TAG : --location=LOCATION --taxonomy=TAXONOMY)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy tag resource - Policy tag from which to remove the IAM policy
binding. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument policy_tag on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_TAG
     ID of the policy tag or fully qualified identifier for the policy
     tag.

     To set the policy_tag attribute:
     + provide the argument policy_tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the policy tag.

     To set the location attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --taxonomy=TAXONOMY
     Taxonomy of the policy tag.

     To set the taxonomy attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --taxonomy on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' on policy tag 'POLICY_TAG' in location 'LOCATION' and
taxonomy 'TAXONOMY', run:

    $ gcloud data-catalog taxonomies policy-tags \
        remove-iam-policy-binding POLICY_TAG --location='LOCATION' \
        --taxonomy='TAXONOMY' --member='user:test-user@gmail.com' \
        --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on policy tag 'POLICY_TAG' in location 'LOCATION' and
taxonomy 'TAXONOMY', run:

    $ gcloud data-catalog taxonomies policy-tags \
        remove-iam-policy-binding POLICY_TAG --location='LOCATION' \
        --taxonomy='TAXONOMY' --member='allAuthenticatedUsers' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/policy-tags/remove-iam-policy-binding)

---
### `gcloud data-catalog taxonomies policy-tags set-iam-policy`

Set the IAM policy for a Data Catalog Policy Tag

Set the IAM policy for the given Data Catalog Policy Tag as defined in a
JSON or YAML file.

**Synopsis:**
```
gcloud data-catalog taxonomies policy-tags set-iam-policy
    (POLICY_TAG : --location=LOCATION --taxonomy=TAXONOMY) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy tag resource - Policy tag for which to set the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_tag on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY_TAG
     ID of the policy tag or fully qualified identifier for the policy
     tag.

     To set the policy_tag attribute:
     + provide the argument policy_tag on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the policy tag.

     To set the location attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --taxonomy=TAXONOMY
     Taxonomy of the policy tag.

     To set the taxonomy attribute:
     + provide the argument policy_tag on the command line with a fully
       specified name;
     + provide the argument --taxonomy on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the Policy Tag 'POLICY_TAG' with location
'LOCATION' in the taxonomy 'TAXONOMY':

    $ gcloud data-catalog taxonomies policy-tags set-iam-policy \
        POLICY_TAG --location=LOCATION --taxonomy=TAXONOMY policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/taxonomies/policy-tags/set-iam-policy)

---
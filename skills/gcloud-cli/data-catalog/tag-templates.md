# gcloud data-catalog tag-templates

manage tag templates in Data Catalog

### `gcloud data-catalog tag-templates add-iam-policy-binding`

Add IAM policy binding to a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Add IAM policy binding to a Data Catalog tag template.

**Synopsis:**
```
gcloud data-catalog tag-templates add-iam-policy-binding
    (TAG_TEMPLATE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template for which to add IAM policy binding
to. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
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
'test-user@gmail.com' with tag template 'my-tag-template' and location
'us-central1', run:

    $ gcloud data-catalog tag-templates add-iam-policy-binding \
        my-tag-template --location='us-central1' \
        --member='user:test-user@gmail.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/add-iam-policy-binding)

---
### `gcloud data-catalog tag-templates create`

Create a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Create a Data Catalog tag template.

**Synopsis:**
```
gcloud data-catalog tag-templates create
    (TAG_TEMPLATE : --location=LOCATION)
    --field=[id=ID,
      type=TYPE,display-name=DISPLAY_NAME,required=REQUIRED,...]
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--field` | [id=ID,type=TYPE,display-name=DISPLAY_NAME,required=REQUIRED,...] |  | Specification for a tag template field. This flag can be repeated to specify multiple fields. The following keys are allowed: *id*::: (Required) ID of the tag template field. *type*::: (Required) Type of the tag template field. Choices are double, string, bool, timestamp, and enum. To specify a string field: `type=string` To specify an enum field with values 'A' and 'B': `type=enum(A\|B)` *display-name*::: Display name of the tag template field. *required*::: Indicates if the tag template field is required. Defaults to FALSE. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Human-readable name for the tag template. |


**Examples:**
```bash
Create a string tag template with a required string field:

    $ gcloud data-catalog tag-templates create TEMPLATE \
        --field=id=ID,display-name=DISPLAY,type=string,required=TRUE

Create an enum tag template with an optional enum field with values 'A' and
'B':

    $ gcloud data-catalog tag-templates create TEMPLATE \
        --field=id=ID,display-name=DISPLAY,type='enum(A|B)'

Create a tag template with a optional string field and a required enum
field with values 'A' and 'B':

    $ gcloud data-catalog tag-templates create TEMPLATE \
        --field=id=ID1,display-name=DISPLAY1,type=string \
        --field=id=ID2,display-name=DISPLAY2,type='enum(A|B)',\
    required=TRUE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/create)

---
### `gcloud data-catalog tag-templates delete`

Delete a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Delete a Data Catalog tag template.

**Synopsis:**
```
gcloud data-catalog tag-templates delete
    (TAG_TEMPLATE : --location=LOCATION) [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If True, any tags with this tag template will be deleted. |


**Examples:**
```bash
Delete a tag template:

    $ gcloud data-catalog tag-templates delete TEMPLATE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/delete)

---
### `gcloud data-catalog tag-templates describe`

Describe a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Describe a Data Catalog tag template.

**Synopsis:**
```
gcloud data-catalog tag-templates describe
    (TAG_TEMPLATE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Describe a tag template:

    $ gcloud data-catalog tag-templates describe TEMPLATE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/describe)

---
### `gcloud data-catalog tag-templates get-iam-policy`

Get the IAM policy for a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

gcloud data-catalog tag-templates get-iam-policy displays the IAM policy
associated with a Data Catalog. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy. The output includes an
"etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ gcloud data-catalog tag-templates
set-iam-policy for additional details.

**Synopsis:**
```
gcloud data-catalog tag-templates get-iam-policy
    (TAG_TEMPLATE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template for which to display the IAM policy.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given tag template, run:

    $ gcloud data-catalog tag-templates get-iam-policy \
        --location=my-location my-tag-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/get-iam-policy)

---
### `gcloud data-catalog tag-templates remove-iam-policy-binding`

Remove IAM policy binding from a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Removes a policy binding from the IAM policy of a Data Catalog tag
template, given a project ID and the binding.

**Synopsis:**
```
gcloud data-catalog tag-templates remove-iam-policy-binding
    (TAG_TEMPLATE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template to remove the IAM policy binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
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
'test-user@gmail.com' on tag template 'my-tag-template' with location
'my-location', run:

    $ gcloud data-catalog tag-templates remove-iam-policy-binding \
        --location=my-location my-tag-template \
        --member='user:test-user@gmail.com' --role='roles/editor'

To remove an IAM policy binding for the role of 'roles/editor' from all
authenticated users on tag template 'my-tag-template' with location
'my-location', run:

    $ gcloud data-catalog tag-templates remove-iam-policy-binding \
        --location=my-location my-tag-template \
        --member='allAuthenticatedUsers' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/remove-iam-policy-binding)

---
### `gcloud data-catalog tag-templates set-iam-policy`

Set the IAM policy for a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Sets the IAM policy for the given Data Catalog tag template as defined in a
JSON or YAML file.

**Synopsis:**
```
gcloud data-catalog tag-templates set-iam-policy
    (TAG_TEMPLATE : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template to set the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
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
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the tag template 'my-tag-template' with
location 'my-location':

    $ gcloud data-catalog tag-templates set-iam-policy my-tag-template \
        --location=my-location policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/set-iam-policy)

---
### `gcloud data-catalog tag-templates update`

Update a Data Catalog tag template

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Update a Data Catalog tag template.

**Synopsis:**
```
gcloud data-catalog tag-templates update
    (TAG_TEMPLATE : --location=LOCATION) [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template resource - Tag template to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument tag_template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TAG_TEMPLATE
     ID of the tag template or fully qualified identifier for the tag
     template.

     To set the tag_template attribute:
     + provide the argument tag_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template.

     To set the location attribute:
     + provide the argument tag_template on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | New human-readable name for the tag template. |


**Examples:**
```bash
Update the display name of a tag template:

    $ gcloud data-catalog tag-templates update TEMPLATE \
        --display-name=DISPLAY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/update)

---

## `gcloud data-catalog tag-templates fields` — manage tag template fields in Data Catalog
### `gcloud data-catalog tag-templates fields create`

Create a Data Catalog tag template field

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Create a Data Catalog tag template field.

**Synopsis:**
```
gcloud data-catalog tag-templates fields create
    (FIELD : --location=LOCATION --tag-template=TAG_TEMPLATE) --type=TYPE
    [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template field resource - Tag template field to create. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument field on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIELD
     ID of the tag template field or fully qualified identifier for the
     tag template field.

     To set the field attribute:
     + provide the argument field on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template field.

     To set the location attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --tag-template=TAG_TEMPLATE
     Tag template of the tag template field.

     To set the tag-template attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --tag-template on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | TYPE |  | Type of the tag template field. Choices are double, string, bool, timestamp, and enum. To specify a string field: `type=string` To specify an enum field with values 'A' and 'B': `type="enum(A\|B)"` |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the tag template field. |


**Examples:**
```bash
Create a string tag template field:

    $ gcloud data-catalog tag-templates fields create create FIELD \
        --display-name=DISPLAY --type=string

Create an enum tag template field with values 'A' and 'B':

    $ gcloud data-catalog tag-templates fields create FIELD \
        --display-name=DISPLAY --type="enum(A|B)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/fields/create)

---
### `gcloud data-catalog tag-templates fields delete`

Delete a Data Catalog tag template field

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Delete a Data Catalog tag template field.

**Synopsis:**
```
gcloud data-catalog tag-templates fields delete
    (FIELD : --location=LOCATION --tag-template=TAG_TEMPLATE) [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template field resource - Tag template field to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument field on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIELD
     ID of the tag template field or fully qualified identifier for the
     tag template field.

     To set the field attribute:
     + provide the argument field on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template field.

     To set the location attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --tag-template=TAG_TEMPLATE
     Tag template of the tag template field.

     To set the tag-template attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --tag-template on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If True, this tag template field will be deleted from any existing tags. |


**Examples:**
```bash
Delete a tag template field:

    $ gcloud data-catalog tag-templates fields delete FIELD
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/fields/delete)

---
### `gcloud data-catalog tag-templates fields rename`

Rename a Data Catalog tag template field

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Rename a Data Catalog tag template field.

**Synopsis:**
```
gcloud data-catalog tag-templates fields rename
    (FIELD : --location=LOCATION --tag-template=TAG_TEMPLATE)
    --new-id=NEW_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template field resource - Tag template field to rename. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument field on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIELD
     ID of the tag template field or fully qualified identifier for the
     tag template field.

     To set the field attribute:
     + provide the argument field on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template field.

     To set the location attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --tag-template=TAG_TEMPLATE
     Tag template of the tag template field.

     To set the tag-template attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --tag-template on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-id` | NEW_ID |  | New ID of the tag template field. |


**Examples:**
```bash
Update the ID of a tag template field:

    $ gcloud data-catalog tag-templates fields rename FIELD \
        --new-id="new-id"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/fields/rename)

---
### `gcloud data-catalog tag-templates fields update`

Update a Data Catalog tag template field

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Update a Data Catalog tag template field.

**Synopsis:**
```
gcloud data-catalog tag-templates fields update
    (FIELD : --location=LOCATION --tag-template=TAG_TEMPLATE)
    [--display-name=DISPLAY_NAME] [--enum-values=[ENUM_VALUES,...]]
    [--required] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tag template field resource - Tag template field to update. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument field on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIELD
     ID of the tag template field or fully qualified identifier for the
     tag template field.

     To set the field attribute:
     + provide the argument field on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the tag template field.

     To set the location attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --tag-template=TAG_TEMPLATE
     Tag template of the tag template field.

     To set the tag-template attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --tag-template on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the tag template field. |
| `--enum-values` | [ENUM_VALUES,...] |  | Comma-separated list of enum values. The list of enum values passed with this flag replaces the existing one in tag template enum field. That means: * the enum values passed to the flag and not present in tag template enum field get created * the enum values present in tag template enum field and missing in the list get removed * the order of the items on the list is preserved Enum values can only be removed from optional enum fields for now. |
| `--required` |  |  | Indicates if the tag template field is required. Updating from FALSE (optional) to TRUE (required) is NOT allowed. |


**Examples:**
```bash
Update the display name of a tag template field:

    $ gcloud data-catalog tag-templates fields update FIELD \
        --display-name=NAME

Set tag template enum field values to be 'A' and 'B':

    $ gcloud data-catalog tag-templates fields update FIELD \
        --enum-values=A,B

Set a tag template field to be optional:

    $ gcloud data-catalog tag-templates fields update FIELD --no-required
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/fields/update)

---

## `gcloud data-catalog tag-templates fields enum-values` — manage tag template enum values in Data Catalog
### `gcloud data-catalog tag-templates fields enum-values rename`

Rename an enum value in Data Catalog tag template enum field

(DEPRECATED) This command is deprecated. Please use gcloud dataplex
aspect-types instead.

Rename an enum value in Data Catalog tag template enum field.

**Synopsis:**
```
gcloud data-catalog tag-templates fields enum-values rename
    (ENUM_VALUE
      : --field=FIELD --location=LOCATION --tag-template=TAG_TEMPLATE)
    --new-id=NEW_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Enum value resource - Enum value to rename. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument enum_value on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENUM_VALUE
     ID of the enum value or fully qualified identifier for the enum
     value.

     To set the enum_value attribute:
     + provide the argument enum_value on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --field=FIELD
     Tag template field that contains enum value.

     To set the field attribute:
     + provide the argument enum_value on the command line with a fully
       specified name;
     + provide the argument --field on the command line.

  --location=LOCATION
     Location of the enum value.

     To set the location attribute:
     + provide the argument enum_value on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --tag-template=TAG_TEMPLATE
     Tag template that contains enum value.

     To set the tag-template attribute:
     + provide the argument enum_value on the command line with a fully
       specified name;
     + provide the argument --tag-template on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-id` | NEW_ID |  | New display name of the enum value. |


**Examples:**
```bash
Rename an enum value in tag template enum field:

    $ gcloud data-catalog tag-templates fields enum-values rename \
        ENUM_VALUE --new-id="new-id"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/tag-templates/fields/enum-values/rename)

---
# gcloud dataplex glossaries

manage Dataplex glossaries

### `gcloud dataplex glossaries add-iam-policy-binding`

Add IAM policy binding to a Dataplex Glossary

Add IAM policy binding to a Dataplex Glossary.

**Synopsis:**
```
gcloud dataplex glossaries add-iam-policy-binding
    (GLOSSARY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
you want to add IAM policy binding to. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/dataplex.viewer for the
user test-user@gmail.com to Glossary test-glossary in location us-central,
run:        $ gcloud dataplex glossaries add-iam-policy-binding test-glossary \
        --project=test-project --location=us-central1 \
        --role=roles/dataplex.viewer --member=user:test-user@gmail.com \
        See https://cloud.google.com/dataplex/docs/iam-roles for \
        details of policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/add-iam-policy-binding)

---
### `gcloud dataplex glossaries create`

Create a Dataplex Glossary resource

A Glossary represents a collection of Categories and Terms.

**Synopsis:**
```
gcloud dataplex glossaries create (GLOSSARY : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
you want to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the Glossary. |
| `--display-name` | DISPLAY_NAME |  | Display Name of the Glossary. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Glossary test-glossary in project test-dataplex at location
us-central1, with description test description and displayName displayName
, run:

    $ gcloud dataplex glossaries create test-glossary \
        --location=us-central1 --project=test-dataplex \
        --description='test description' --display-name='displayName'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/create)

---
### `gcloud dataplex glossaries delete`

Delete a Dataplex Glossary

Delete a Dataplex Glossary.

**Synopsis:**
```
gcloud dataplex glossaries delete (GLOSSARY : --location=LOCATION)
    [--async] [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
you want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | etag value for particular Glossary. |


**Examples:**
```bash
To Delete Glossary test-glossary in project test-dataplex at location
us-central1, run:        $ gcloud dataplex glossaries delete test-glossary \
      --location=us-central1 --project=test-dataplex
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/delete)

---
### `gcloud dataplex glossaries describe`

Describe a Glossary

Describe a Glossary. Displays all details of a Glossary given a valid
Glossary ID.

**Synopsis:**
```
gcloud dataplex glossaries describe (GLOSSARY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Glossary you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex Glossary test-glossary within location us-central1
and in project test-project

    $ gcloud dataplex glossaries describe test-glossary \
       --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/describe)

---
### `gcloud dataplex glossaries get-iam-policy`

Retrieve a Dataplex Glossary IAM policy

Displays the IAM policy associated with a Dataplex Glossary resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex glossaries get-iam-policy (GLOSSARY : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
IAM policy you want to retrieve. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To get the IAM policy of a Dataplex Glossary test-glossary in project
test-project under location us-central1        $ gcloud dataplex glossaries get-iam-policy test-glossary \
        --project=test-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/get-iam-policy)

---
### `gcloud dataplex glossaries list`

List Glossaries

List Glossaries.

**Synopsis:**
```
gcloud dataplex glossaries list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To List Glossaries in project test-dataplex at location us-central1

    $ gcloud dataplex glossaries list --location=us-central1 \
      --project=test-dataplex
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/list)

---
### `gcloud dataplex glossaries remove-iam-policy-binding`

Removes IAM policy binding from a Dataplex Glossary

Removes IAM policy binding from a Dataplex Glossary.

**Synopsis:**
```
gcloud dataplex glossaries remove-iam-policy-binding
    (GLOSSARY : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
you want to remove IAM policy binding from The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role roles/dataplex.viewer for the
user test-user@gmail.com from a glossary test-glossary within projet
test-project in location us-central1, run:        $ gcloud dataplex glossaries remove-iam-policy-binding \
        test-glossary --project=test-project --location=us-central1 \
        --role=roles/dataplex.viewer --member=user:test-user@gmail.com \
        See https://cloud.google.com/dataplex/docs/iam-roles for \
        details of policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/remove-iam-policy-binding)

---
### `gcloud dataplex glossaries set-iam-policy`

Set an IAM policy binding for a Dataplex Glossary as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex glossaries set-iam-policy (GLOSSARY : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
you want to set IAM policy to. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
policy.json and set it for the Dataplex Glossary test-glossary within
project test-project in location us-central1:        $ gcloud dataplex glossaries set-iam-policy test-glossary \
        --project=test-project --location=us-central1 policy.json \
        where policy.json is the relative path to the json file.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/set-iam-policy)

---
### `gcloud dataplex glossaries update`

Updates a Dataplex Glossary

Updates a Dataplex Glossary.

**Synopsis:**
```
gcloud dataplex glossaries update (GLOSSARY : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME] [--etag=ETAG]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary resource - Arguments and flags that define the Dataplex Glossary
you want to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY
     ID of the glossary or fully qualified identifier for the glossary.

     To set the glossary attribute:
     + provide the argument glossary on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the Glossary. |
| `--display-name` | DISPLAY_NAME |  | Display Name of the Glossary. |
| `--etag` | ETAG |  | etag value for particular Glossary. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update Glossary test-glossary in project test-dataplex at location
us-central1, with description updated description and displayName
displayName        $ gcloud dataplex glossaries update test-glossary \
        --location=us-central1 --project test-dataplex \
        --description='updated description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/update)

---

## `gcloud dataplex glossaries categories` — manage Dataplex glossary categories
### `gcloud dataplex glossaries categories create`

Creates a glossary category

A glossary category represents a collection of glossary categories and
glossary terms within a glossary that are related to each other.

**Synopsis:**
```
gcloud dataplex glossaries categories create
    (GLOSSARY_CATEGORY : --glossary=GLOSSARY --location=LOCATION)
    --parent=PARENT [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary category resource - Arguments and flags that define the Dataplex
Glossary Category you want to create. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_category on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_CATEGORY
     ID of the glossary category or fully qualified identifier for the
     glossary category.

     To set the glossary_category attribute:
     + provide the argument glossary_category on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     The name of glossary category to use.

     To set the glossary attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Immediate parent of the created glossary category. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the glossary category. |
| `--display-name` | DISPLAY_NAME |  | Display name of the glossary category. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a glossary category test-category in glossary test-glossary in
project test-project in location us-central1, with description test
description, displayName displayName and parent
projects/test-project/locations/us-central1/glossaries/test-glossary , run:

    $ gcloud dataplex glossaries categories create test-category \
        --glossary=test-glossary --location=us-central1 \
        --project=test-project \
        --parent='projects/test-project/locations/us-central1/glossaries\
    /test-glossary' --description='test description' \
        --display-name='displayName'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/categories/create)

---
### `gcloud dataplex glossaries categories delete`

Deletes a glossary category

Deletes a glossary category.

**Synopsis:**
```
gcloud dataplex glossaries categories delete
    (GLOSSARY_CATEGORY : --glossary=GLOSSARY --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary category resource - Arguments and flags that define the glossary
category you want to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_category on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_CATEGORY
     ID of the glossary category or fully qualified identifier for the
     glossary category.

     To set the glossary_category attribute:
     + provide the argument glossary_category on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     Identifier of the Dataplex Glossary resource.

     To set the glossary attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To delete glossary category test-category in glossary test-glossary in
project test-project in location us-central1, run:        $ gcloud dataplex glossaries categories delete test-category \
      --glossary=test-glossary --location=us-central1 \
      --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/categories/delete)

---
### `gcloud dataplex glossaries categories describe`

Describes a glossary category

Describes a glossary category.

**Synopsis:**
```
gcloud dataplex glossaries categories describe
    (GLOSSARY_CATEGORY : --glossary=GLOSSARY --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary category resource - Arguments and flags that define the glossary
category you want to describe. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_category on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_CATEGORY
     ID of the glossary category or fully qualified identifier for the
     glossary category.

     To set the glossary_category attribute:
     + provide the argument glossary_category on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     Identifier of the Dataplex Glossary resource.

     To set the glossary attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a glossary category test-category in glossary test-glossary in
project test-project in loaction us-central1, run:        $ gcloud dataplex glossaries categories describe test-category \
        --glossary=test-glossary --location=us-central1 \
        --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/categories/describe)

---
### `gcloud dataplex glossaries categories list`

List glossary categories

List glossary categories.

**Synopsis:**
```
gcloud dataplex glossaries categories list
    (--glossary=GLOSSARY : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--glossary` | GLOSSARY |  | _[This must be specified.]_ ID of the glossary or fully qualified identifier for the glossary. To set the glossary attribute: + provide the argument --glossary on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --glossary on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list glossary categories in glossary test-glossary in location
us-central1 in project test-project, run :

    $ gcloud dataplex glossaries categories list \
         --glossary=test-glossary --location=us-central1 \
         --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/categories/list)

---
### `gcloud dataplex glossaries categories update`

Updates a glossary category

Updates a glossary category.

**Synopsis:**
```
gcloud dataplex glossaries categories update
    (GLOSSARY_CATEGORY : --glossary=GLOSSARY --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--parent=PARENT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary category resource - Arguments and flags that define the Dataplex
Glossary Category you want to update. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_category on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_CATEGORY
     ID of the glossary category or fully qualified identifier for the
     glossary category.

     To set the glossary_category attribute:
     + provide the argument glossary_category on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     The name of glossary category to use.

     To set the glossary attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_category on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the glossary category. |
| `--display-name` | DISPLAY_NAME |  | Display Name of the glossary category. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--parent` | PARENT |  | Immediate parent of the created glossary category. |


**Examples:**
```bash
To update display name, desciption and labels of glossary category
test-category in glossary test-glossary in project test-project in location
us-central1, run:

    $ gcloud dataplex glossaries categories update test-category \
        --location=us-central1 --project=test-project \
        --glossary=test-glossary --description='updated description' \
        --display-name='updated displayName' \
        --labels=key1=value1,key2=value2

To update parent of glossary category test-category in glossary
test-glossary in project test-project in location us-central1, run:

    $ gcloud dataplex glossaries categories update test-category \
        --location=us-central1 --project=test-project \
        --glossary=test-glossary \
        --parent='projects/test-project/locations/us-central1/glossaries\
    /updated-glossary'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/categories/update)

---

## `gcloud dataplex glossaries terms` — manage Dataplex glossary terms
### `gcloud dataplex glossaries terms create`

Creates a glossary term

A glossary term holds a rich text description that can be attached to
entries or specific columns to enrich them.

**Synopsis:**
```
gcloud dataplex glossaries terms create
    (GLOSSARY_TERM : --glossary=GLOSSARY --location=LOCATION)
    --parent=PARENT [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary term resource - Arguments and flags that define the Dataplex
Glossary Term you want to create. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_term on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_TERM
     ID of the glossary term or fully qualified identifier for the
     glossary term.

     To set the glossary_term attribute:
     + provide the argument glossary_term on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     The name of glossary term to use.

     To set the glossary attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--parent` | PARENT |  | Immediate parent of the created glossary term. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the glossary term. |
| `--display-name` | DISPLAY_NAME |  | Display name of the glossary term. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a glossary term test-term in glossary test-glossary in project
test-project in location us-central1, with description test description,
displayName displayName and parent
projects/test-project/locations/us-central1/glossaries/test-glossary/categories/test-category
, run:

    $ gcloud dataplex glossaries terms create test-term \
        --glossary=test-glossary --location=us-central1 \
        --project=test-project \
        --parent='projects/test-project/locations/us-central1/glossaries\
    /test-glossary/categories/test-category' \
        --description='test description' --display-name='displayName'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/terms/create)

---
### `gcloud dataplex glossaries terms delete`

Deletes a glossary term

Deletes a glossary term.

**Synopsis:**
```
gcloud dataplex glossaries terms delete
    (GLOSSARY_TERM : --glossary=GLOSSARY --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary term resource - Arguments and flags that define the glossary term
you want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_term on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_TERM
     ID of the glossary term or fully qualified identifier for the
     glossary term.

     To set the glossary_term attribute:
     + provide the argument glossary_term on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     Identifier of the Dataplex Glossary resource.

     To set the glossary attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To delete the glossary term test-term in glossary test-glossary in project
test-project in location us-central1, run:

    $ gcloud dataplex glossaries terms delete test-term \
      --glossary=test-glossary --location=us-central1 \
      --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/terms/delete)

---
### `gcloud dataplex glossaries terms describe`

Describes a glossary term

Describes a glossary term.

**Synopsis:**
```
gcloud dataplex glossaries terms describe
    (GLOSSARY_TERM : --glossary=GLOSSARY --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary term resource - Arguments and flags that define the glossary term
you want to describe. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_term on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_TERM
     ID of the glossary term or fully qualified identifier for the
     glossary term.

     To set the glossary_term attribute:
     + provide the argument glossary_term on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     Identifier of the Dataplex Glossary resource.

     To set the glossary attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe the glossary term test-term in glossary test-glossary in
project test-project in loaction us-central1, run:

    $ gcloud dataplex glossaries terms describe test-term \
        --glossary=test-glossary --location=us-central1 \
        --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/terms/describe)

---
### `gcloud dataplex glossaries terms list`

List glossary terms

List glossary terms.

**Synopsis:**
```
gcloud dataplex glossaries terms list
    (--glossary=GLOSSARY : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--glossary` | GLOSSARY |  | _[This must be specified.]_ ID of the glossary or fully qualified identifier for the glossary. To set the glossary attribute: + provide the argument --glossary on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --glossary on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list glossary terms in glossary test-glossary in project test-project in
location us-central1, run :

    $ gcloud dataplex glossaries terms list --glossary=test-glossary \
         --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/terms/list)

---
### `gcloud dataplex glossaries terms update`

Updates a glossary term

Updates a glossary term.

**Synopsis:**
```
gcloud dataplex glossaries terms update
    (GLOSSARY_TERM : --glossary=GLOSSARY --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--parent=PARENT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Glossary term resource - Arguments and flags that define the Dataplex
Glossary Term you want to update. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument glossary_term on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GLOSSARY_TERM
     ID of the glossary term or fully qualified identifier for the
     glossary term.

     To set the glossary_term attribute:
     + provide the argument glossary_term on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --glossary=GLOSSARY
     The name of glossary term to use.

     To set the glossary attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --glossary on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument glossary_term on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the glossary term. |
| `--display-name` | DISPLAY_NAME |  | Display name of the glossary term. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--parent` | PARENT |  | Immediate parent of the created glossary term. |


**Examples:**
```bash
To update display name, desciption and labels of glossary term test-term in
glossary test-glossary in project test-project in location us-central1,
run:

    $ gcloud dataplex glossaries terms update test-term \
        --location=us-central1 --project=test-project \
        --glossary=test-glossary --description='updated description' \
        --display-name='updated displayName' \
        --labels=key1=value1,key2=value2

To update parent of glossary term test-term in glossary test-glossary in
project test-project in location us-central1, run:

    $ gcloud dataplex glossaries terms update test-term \
        --location=us-central1 --project=test-project \
        --glossary=test-glossary \
        --parent='projects/test-project/locations/us-central1/glossaries\
    /updated-glossary'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/glossaries/terms/update)

---
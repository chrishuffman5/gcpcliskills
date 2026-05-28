# gcloud dataplex aspect-types

manage Dataplex Aspect Types

### `gcloud dataplex aspect-types add-iam-policy-binding`

Add IAM policy binding to a Dataplex Aspect Type

Add IAM policy binding to a Dataplex Aspect Type.

**Synopsis:**
```
gcloud dataplex aspect-types add-iam-policy-binding
    (ASPECT_TYPE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex aspect
type you want to add IAM policy binding to. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
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
user test-user@gmail.com to Aspect Type test-aspect-type in project
test-project and in location us-central1, run:

    $ gcloud dataplex aspect-types add-iam-policy-binding \
        test-aspect-type --project=test-project --location=us-central1 \
        --role=roles/dataplex.viewer --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/add-iam-policy-binding)

---
### `gcloud dataplex aspect-types create`

Create a Dataplex Aspect Type

Aspect Type is a template for creating Aspects.

**Synopsis:**
```
gcloud dataplex aspect-types create (ASPECT_TYPE : --location=LOCATION)
    --metadata-template-file-name=METADATA_TEMPLATE_FILE_NAME
    [--data-classification=DATA_CLASSIFICATION] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--async | --validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex aspect
type you want to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--metadata-template-file-name` | METADATA_TEMPLATE_FILE_NAME |  | The name of the JSON or YAML file to define Metadata Template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-classification` | DATA_CLASSIFICATION |  | Data classification of the Aspect Type. DATA_CLASSIFICATION must be (only one value is supported): METADATA_AND_DATA. |
| `--description` | DESCRIPTION |  | Description of the Aspect Type. |
| `--display-name` | DISPLAY_NAME |  | Display name of the Aspect Type. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create Aspect Type test-aspect-type in project test-dataplex at location
us-central1, with description test description, displayName test display
name and metadataTemplateFileName file.json, run:

    $ gcloud dataplex aspect-types create test-aspect-type \
        --location=us-central1 --project=test-project \
        --description='test description' \
        --display-name='test display name' \
        --metadata-template-file-name='file.json'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/create)

---
### `gcloud dataplex aspect-types delete`

Delete a Dataplex Aspect Type

Delete a Dataplex Aspect Type.

**Synopsis:**
```
gcloud dataplex aspect-types delete (ASPECT_TYPE : --location=LOCATION)
    [--async] [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex Aspect
Type you want to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | etag for the Aspect Type you want to delete. |


**Examples:**
```bash
To delete Aspect Type test-aspect-type in project test-project and in
location us-central1, run:

    $ gcloud dataplex aspect-types delete test-aspect-type \
      --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/delete)

---
### `gcloud dataplex aspect-types describe`

Describe a Dataplex Aspect Type

Displays all details of an Aspect Type given a valid Aspect Type ID.

**Synopsis:**
```
gcloud dataplex aspect-types describe (ASPECT_TYPE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex Aspect
Type you want to retrieve. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex Aspect Type test-aspect-type in location us-central1
and in project test-project, run:

    $ gcloud dataplex aspect-types describe test-aspect-type \
       --location=us-central1 --project=test-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/describe)

---
### `gcloud dataplex aspect-types get-iam-policy`

Retrieve a Dataplex Aspect Type IAM policy

Displays the IAM policy associated with a Dataplex Aspect Type resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex aspect-types get-iam-policy
    (ASPECT_TYPE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex Aspect
Type IAM policy you want to retrieve. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To get the IAM policy of a Dataplex Aspect Type test-aspect-type in project
test-project under location us-central1, run:

    $ gcloud dataplex aspect-types get-iam-policy test-aspect-type \
        --project=test-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/get-iam-policy)

---
### `gcloud dataplex aspect-types list`

List Dataplex Aspect Types

List Dataplex Aspect Types based on project and location.

gcloud dataplex aspect-types list --project={project_id}
--location={location}

**Synopsis:**
```
gcloud dataplex aspect-types list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list Aspect Types in project test-dataplex at location us-central1

    $ gcloud dataplex aspect-types list --location=us-central1 \
      --project=test-dataplex
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/list)

---
### `gcloud dataplex aspect-types remove-iam-policy-binding`

Remove IAM policy binding from a Dataplex Aspect Type

Remove IAM policy binding from a Dataplex Aspect Type.

**Synopsis:**
```
gcloud dataplex aspect-types remove-iam-policy-binding
    (ASPECT_TYPE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex aspect
type you want to remove IAM policy binding from The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
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
user testuser@gmail.com from an aspect type test-aspect-type in project
test-project and in location us-central1, run:

    $ gcloud dataplex aspect-types remove-iam-policy-binding \
        test-aspect-type --project=test-project --location=us-central1 \
        --role=roles/dataplex.viewer --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/remove-iam-policy-binding)

---
### `gcloud dataplex aspect-types set-iam-policy`

Set an IAM policy binding for a Dataplex Aspect Type as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex aspect-types set-iam-policy
    (ASPECT_TYPE : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex aspect
type you want to set IAM policy to. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
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
policy.json and set it for the Dataplex Aspect Type test-aspect-type in
project test-project and in location us-central1:

    $ gcloud dataplex aspect-types set-iam-policy test-aspect-type \
        --project=test-project --location=us-central1 policy.json

    where policy.json is the relative path to the JSON file.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/set-iam-policy)

---
### `gcloud dataplex aspect-types update`

Update a Dataplex Aspect Type

Update a Dataplex Aspect Type.

**Synopsis:**
```
gcloud dataplex aspect-types update (ASPECT_TYPE : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME] [--etag=ETAG]
    [--labels=[KEY=VALUE,...]]
    [--metadata-template-file-name=METADATA_TEMPLATE_FILE_NAME]
    [--async | --validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Aspect type resource - Arguments and flags that define the Dataplex aspect
type you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument aspect_type on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ASPECT_TYPE
     ID of the aspect type or fully qualified identifier for the aspect
     type.

     To set the aspect_type attribute:
     + provide the argument aspect_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument aspect_type on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the Aspect Type. |
| `--display-name` | DISPLAY_NAME |  | Display name of the Aspect Type. |
| `--etag` | ETAG |  | etag value for particular Aspect Type. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--metadata-template-file-name` | METADATA_TEMPLATE_FILE_NAME |  | The name of the JSON or YAML file to define Metadata Template. |


**Examples:**
```bash
To update Aspect Type test-aspect-type in project test-project at location
us-central1, with description updated description and display name updated
display name, run:

    $ gcloud dataplex aspect-types update test-aspect-type \
        --location=us-central1 --project=test-project \
        --description='updated description' \
        --display-name='updated display name'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/aspect-types/update)

---
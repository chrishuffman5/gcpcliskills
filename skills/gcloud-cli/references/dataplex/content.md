# gcloud dataplex content

manage Dataplex Content

### `gcloud dataplex content add-iam-policy-binding`

Adds IAM policy binding to a Dataplex Content

Adds IAM policy binding to a Dataplex Content.

**Synopsis:**
```
gcloud dataplex content add-iam-policy-binding
    (CONTENT : --lake=LAKE --location=LOCATION) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - The Content to add IAM policy binding to. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
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
user 'testuser@gmail.com' to content test-content within lake test-lake in
location us-central, run:

    $ gcloud dataplex content add-iam-policy-binding test-content \
        --project=test-project --location=us-central1 --lake=test-lake \
        --role=roles/dataplex.viewer --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/add-iam-policy-binding)

---
### `gcloud dataplex content create`

Creating a content

Creating a content.

**Synopsis:**
```
gcloud dataplex content create --data-text=DATA_TEXT --path=PATH
    (--kernel-type=KERNEL_TYPE | --query-engine=QUERY_ENGINE)
    (--lake=LAKE : --location=LOCATION) [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-text` | DATA_TEXT |  | Content data in string format |
| `--path` | PATH |  | The path for the Content file, represented as directory structure |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the Content |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | Validate the create action, but don't actually perform it. |


**Examples:**
```bash
To create a Dataplex content test-content of type notebook within lake
test-lake in location us-central1.

    $ gcloud dataplex content create --project=test-project \
         --location=us-central1 --lake=test-lake --kernel-type=PYTHON3 \
         --data-text='' --path='test-content'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/create)

---
### `gcloud dataplex content delete`

Delete a Dataplex Content Resource

Delete a Dataplex Content resource based on project, location, lake, and
content.

**Synopsis:**
```
gcloud dataplex content delete (CONTENT : --lake=LAKE --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Arguments and flags that define the Dataplex Content
you want to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To delete a content test-content in lake test-lake under location
us-central1 inside project test-project, run :

    $ gcloud dataplex content delete --project=test-project \
         --location=us-central1 --lake=test-lake test-content
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/delete)

---
### `gcloud dataplex content describe`

Retrieve a Dataplex Content Resource

Get a Dataplex Content resource based on project, location, lake, and
content.

**Synopsis:**
```
gcloud dataplex content describe
    (CONTENT : --lake=LAKE --location=LOCATION)
    [--view=VIEW; default="basic"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Arguments and flags that define the Dataplex Content
you want to retrieve. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: basic Does not include the Content data in response | basic | There are two possible views, 'basic' and 'full'. The default view is 'basic'. VIEW must be one of: basic Does not include the Content data in response. full Includes the content data in response. |


**Examples:**
```bash
To describe a Dataplex Content test-content in project test-project under
loaction us-central1 inside project test-project, run:

    $ gcloud dataplex content describe test-content \
        --project=test-project --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/describe)

---
### `gcloud dataplex content get-iam-policy`

Retrieve the IAM policy for a Dataplex Content

Get a Dataplex Content Iam Policy based on project_id, location, lake_id,
and contents_id.

**Synopsis:**
```
gcloud dataplex content get-iam-policy
    (CONTENT : --lake=LAKE --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - Arguments and flags that define the Dataplex contents
IAM policy you want to retrieve. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To get the IAM policy of a Dataplex Content test-content in project
test-project under loaction us-central1 inside lake test-lake, run:

    $ gcloud dataplex content get-iam-policy test-content \
        --project=test-project --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/get-iam-policy)

---
### `gcloud dataplex content list`

List Dataplex Content Resources

List Dataplex Content resource based on project, location, and lake.
Currently list does not support project/{project_id}/.../ notation.

**Synopsis:**
```
gcloud dataplex content list (--lake=LAKE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lake` | LAKE |  | _[This must be specified.]_ ID of the lake or fully qualified identifier for the lake. To set the lake attribute: + provide the argument --lake on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --lake on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all Dataplex Content resource in lake test-lake under location
us-central1 inside project test-project, run :

    $ gcloud dataplex content list --project=test-project \
         --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/list)

---
### `gcloud dataplex content remove-iam-policy-binding`

Removes IAM policy binding from a Dataplex Content

Removes IAM policy binding from a Dataplex Content.

**Synopsis:**
```
gcloud dataplex content remove-iam-policy-binding
    (CONTENT : --lake=LAKE --location=LOCATION) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - The Content to remove IAM policy binding from The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
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
user testuser@gmail.com from a content test-content within lake test-lake
in location us-central1, run:

    $ gcloud dataplex content remove-iam-policy-binding test-content \
        --project=test-project --location=us-central1 --lake=test-lake \
        --role=roles/dataplex.viewer --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/remove-iam-policy-binding)

---
### `gcloud dataplex content set-iam-policy`

Set the IAM policy to a Dataplex Content as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex content set-iam-policy
    (CONTENT : --lake=LAKE --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - The Content to set IAM policy to. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
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
policy.json and set it for the Dataplex content test-content within lake
test-lake in location us-central1 and :

    $ gcloud dataplex content set-iam-policy test-content \
        --project=test-project --location=us-central1 --lake=test-lake \
        policy.json

    where policy.json is the relative path to the json file.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/set-iam-policy)

---
### `gcloud dataplex content update`

Update a Dataplex Content Resource with the given configurations

Update a Dataplex Content Resource with the given configurations.

**Synopsis:**
```
gcloud dataplex content update (CONTENT : --lake=LAKE --location=LOCATION)
    [--data-text=DATA_TEXT] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [--path=PATH] [--validate-only]
    [--kernel-type=KERNEL_TYPE | --query-engine=QUERY_ENGINE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Content resource - The Content to Update a Content to. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument content on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONTENT
     ID of the content or fully qualified identifier for the content.

     To set the content attribute:
     + provide the argument content on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument content on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data-text` | DATA_TEXT |  | Content data in string format |
| `--description` | DESCRIPTION |  | Description of the Content |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--path` | PATH |  | The path for the Content file, represented as directory structure |
| `--validate-only` |  |  | Validate the update action, but don't actually perform it. |


**Examples:**
```bash
To update a Dataplex content test-content in project test-project within
lake test-lake in location us-central1 and change the description to
Updated Description, run:

    $ gcloud dataplex content update test-content \
        --project=test-project --location=us-central1 --lake=test-lake \
        --description='Updated Description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/content/update)

---
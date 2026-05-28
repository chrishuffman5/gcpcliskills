# gcloud dataplex lakes

manage Dataplex Lake resources

### `gcloud dataplex lakes add-iam-policy-binding`

Add IAM policy binding to a Dataplex lake resource

Add IAM policy binding to a Dataplex lake resource.

**Synopsis:**
```
gcloud dataplex lakes add-iam-policy-binding (LAKE : --location=LOCATION)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lakes resource - Arguments and flags that define the Dataplex lake you
want to add IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lakes or fully qualified identifier for the lakes.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
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
user test-user@gmail.com to lake test-lake in location us-central, run:

    $ gcloud dataplex lakes add-iam-policy-binding test-lake \
        --location=us-central1 --role=roles/dataplex.viewer \
        --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/add-iam-policy-binding)

---
### `gcloud dataplex lakes authorize`

Authorize a service agent to manage resources

The service agent for the primary project will be granted an IAM role on a
secondary project, a Cloud Storage bucket, or a BigQuery dataset.

**Synopsis:**
```
gcloud dataplex lakes authorize
    (--project-resource=PROJECT_RESOURCE
      | --storage-bucket-resource=STORAGE_BUCKET_RESOURCE
      | --bigquery-dataset-resource=BIGQUERY_DATASET_RESOURCE
      --secondary-project=SECONDARY_PROJECT) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--project-resource` | PROJECT_RESOURCE |  | _[Exactly one of these must be specified:]_ The identifier of the project whose resources the service agent will manage. |
| `--storage-bucket-resource` | STORAGE_BUCKET_RESOURCE |  | _[Exactly one of these must be specified:]_ The identifier of the Cloud Storage bucket that the service agent will manage. |


**Examples:**
```bash
To authorize the service agent in project test-project to manage resources
in the project test-project2, run:

    $ gcloud dataplex lakes authorize --project=test-project \
        --project-resource=test-project2

To authorize the service agent in project test-project to manage the Cloud
Storage bucket dataplex-storage-bucket, run:

    $ gcloud dataplex lakes authorize --project=test-project \
        --storage-bucket-resource=dataplex-storage-bucket

To authorize the service agent in project test-project to manage the
BigQuery dataset test-dataset in project test-project2, run:

    $ gcloud dataplex lakes authorize --project=test-project \
        --bigquery-dataset-resource=test-dataset \
        --secondary-project=test-project2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/authorize)

---
### `gcloud dataplex lakes create`

Create a Dataplex lake resource

A lake is a centralized repository for managing data across the
organization, where enterprise data is distributed across many cloud
projects, and stored in a variety of storage services, such as Google Cloud
Storage and BigQuery. A lake provides data admins with tools to organize,
secure and manage their data at scale, and provides data scientists and
data engineers an integrated experience to easily search, discover, analyze
and transform data and associated metadata.

The Lake ID will be used to generate names such as database and dataset
names when publishing metadata to Hive Metastore and BigQuery. The Lake id
must follow these rules:
  o Must contain only lowercase letters, numbers, and hyphens.
  o Must start with a letter.
  o Must end with a number or a letter.
  o Must be between 1-63 characters.
  o Must be unique within the customer project / location.

**Synopsis:**
```
gcloud dataplex lakes create (LAKE : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--metastore-service=METASTORE_SERVICE]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lakes resource - Arguments and flags that define the Dataplex lake you
want to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lakes or fully qualified identifier for the lakes.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the lake. |
| `--display-name` | DISPLAY_NAME |  | Display name of the lake. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | _[where the location matches the location of the lake.]_ Validate the create action, but don't actually perform it. |


**Examples:**
```bash
To create a Dataplex lake with name my-dataplex-lake in location
us-central1, run:

    $ gcloud dataplex lakes create my-dataplex-lake --location=us-central

To create a Dataplex lake with name my-dataplex-lake in location
us-central1 with metastore service service-123abc attached, run:

    $ gcloud dataplex lakes create my-dataplex-lake \
        --location=us-central \
        --metastore-service=projects/my-project/services/service-123abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/create)

---
### `gcloud dataplex lakes deauthorize`

Deauthorize a service agent from managing resources

The service agent for the primary project will have its IAM role revoked
from a secondary project, a Cloud Storage bucket, or a BigQuery dataset.

**Synopsis:**
```
gcloud dataplex lakes deauthorize
    (--project-resource=PROJECT_RESOURCE
      | --storage-bucket-resource=STORAGE_BUCKET_RESOURCE
      | --bigquery-dataset-resource=BIGQUERY_DATASET_RESOURCE
      --secondary-project=SECONDARY_PROJECT) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--project-resource` | PROJECT_RESOURCE |  | _[Exactly one of these must be specified:]_ The identifier of the project whose resources the service agent will no longer manage. |
| `--storage-bucket-resource` | STORAGE_BUCKET_RESOURCE |  | _[Exactly one of these must be specified:]_ The identifier of the Cloud Storage bucket that the service agent will no longer manage. |


**Examples:**
```bash
To deauthorize the service agent in project test-project from managing
resources in the project test-project2, run:

    $ gcloud dataplex lakes deauthorize --project=test-project \
        --project-resource=test-project2

To deauthorize the service agent in project test-project from managing the
Cloud Storage bucket dataplex-storage-bucket, run:

    $ gcloud dataplex lakes deauthorize --project=test-project \
        --storage-bucket-resource=dataplex-storage-bucket

To deauthorize the service agent in project test-project from managing the
BigQuery dataset test-dataset in project test-project2, run:

    $ gcloud dataplex lakes deauthorize --project=test-project \
        --bigquery-dataset-resource=test-dataset \
        --secondary-project=test-project2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/deauthorize)

---
### `gcloud dataplex lakes delete`

Delete a Dataplex lake resource

Delete a Dataplex lake resource.

**Synopsis:**
```
gcloud dataplex lakes delete (LAKE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lake resource - Arguments and flags that define the Dataplex lake you want
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lake or fully qualified identifier for the lake.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Dataplex lake test-lake in location us-central1, run:

    $ gcloud dataplex lakes delete test-lake --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/delete)

---
### `gcloud dataplex lakes describe`

Describe a Dataplex lake resource

Displays all details of a Dataplex lake resource given a valid lake ID.

**Synopsis:**
```
gcloud dataplex lakes describe (LAKE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lake resource - Arguments and flags that define the Dataplex lake you want
to retrieve. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lake or fully qualified identifier for the lake.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex lake test-lake in location us-central1, run:

    $ gcloud dataplex lakes describe test-lake --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/describe)

---
### `gcloud dataplex lakes get-iam-policy`

Get the IAM policy for a Dataplex lake resource

Displays the IAM policy associated with a Dataplex lake resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex lakes get-iam-policy (LAKE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lake resource - Arguments and flags that define the Dataplex lake IAM
policy you want to retrieve. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lake or fully qualified identifier for the lake.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To print the IAM policy for Dataplex lake test-lake in location
us-central1, run:

    $ gcloud dataplex lakes get-iam-policy test-lake \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/get-iam-policy)

---
### `gcloud dataplex lakes list`

List Dataplex lake resources under a project

List all Dataplex lake resource under a specific project and location.

**Synopsis:**
```
gcloud dataplex lakes list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all Dataplex lake resources in location us-central, run:

    $ gcloud dataplex lakes list --project=test-project \
      --location=us-central1

To list all Dataplex lakes in all locations, run:

    $ gcloud dataplex lakes list --project=test-project --location=-
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/list)

---
### `gcloud dataplex lakes remove-iam-policy-binding`

Remove IAM policy binding from a Dataplex lake resource

Remove IAM policy binding from a Dataplex lake resource.

**Synopsis:**
```
gcloud dataplex lakes remove-iam-policy-binding
    (LAKE : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lakes resource - Arguments and flags that define the Dataplex lake you
want to remove IAM policy binding from. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lakes or fully qualified identifier for the lakes.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
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
user test-user@gmail.com from lake test-lake in location 'us-central', run:

    $ gcloud dataplex lakes remove-iam-policy-binding test-lake \
        --location=us-central1 --role=roles/dataplex.viewer \
        --member=user:foo@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/remove-iam-policy-binding)

---
### `gcloud dataplex lakes set-iam-policy`

Set the IAM policy to a Dataplex lake as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex lakes set-iam-policy (LAKE : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lakes resource - Arguments and flags that define the Dataplex lake you
want to set IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lakes or fully qualified identifier for the lakes.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
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
policy.son and set it for the Dataplex lake test-lake defined in location
us-central1:

    $ gcloud dataplex lakes set-iam-policy --location=us-central1 \
        test-lake policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/set-iam-policy)

---
### `gcloud dataplex lakes update`

Update a Dataplex lake resource

Update a Dataplex lake resource.

**Synopsis:**
```
gcloud dataplex lakes update (LAKE : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--metastore-service=METASTORE_SERVICE]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lakes resource - Arguments and flags that define the Dataplex lake you
want to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lake on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LAKE
     ID of the lakes or fully qualified identifier for the lakes.

     To set the lake attribute:
     + provide the argument lake on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument lake on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the lake |
| `--display-name` | DISPLAY_NAME |  | Display Name |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | _[where the location matches the location of the lake.]_ Validate the update action, but don't actually perform it. |


**Examples:**
```bash
To update a Dataplex Lake test-lake in location us-central1 to have the
display name first-dataplex-lake and metastore service
projects/test-lake/locations/us-central1/service/test-service, run:

    $ gcloud dataplex lakes update test-lake --location=us-central1 \
        --display-name="first-dataplex-lake" \
        --metastore-service="projects/test-lake/locations/us-central1/se\
    rvice/test-service"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/update)

---

## `gcloud dataplex lakes actions` — manage Dataplex lake resource actions
### `gcloud dataplex lakes actions list`

List Dataplex lake actions

List all Dataplex Actions under a specific lake.

**Synopsis:**
```
gcloud dataplex lakes actions list (--lake=LAKE : --location=LOCATION)
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
To list all actions of a Dataplex Lake test-lake defined in location
us-central1 run:

    $ gcloud dataplex lakes actions list --location=us-central1 \
        --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/lakes/actions/list)

---
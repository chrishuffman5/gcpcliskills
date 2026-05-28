# gcloud dataplex environments

manage Dataplex Environments

### `gcloud dataplex environments add-iam-policy-binding`

Adds IAM policy binding to a Dataplex Environment

Adds IAM policy binding to a Dataplex Environment.

**Synopsis:**
```
gcloud dataplex environments add-iam-policy-binding
    (ENVIRONMENT : --lake=LAKE --location=LOCATION) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environments resource - The Environment to add IAM policy binding to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environments or fully qualified identifier for the
     environments.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
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
user 'testuser@gmail.com' to environment test-environment within lake
test-lake in location us-central, run:

    $ gcloud dataplex environments add-iam-policy-binding \
        test-environment --project=test-project --location=us-central1 \
        --lake=test-lake --role=roles/dataplex.viewer \
        --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/add-iam-policy-binding)

---
### `gcloud dataplex environments create`

Create a Dataplex Environment

Create a Dataplex Environment.

**Synopsis:**
```
gcloud dataplex environments create
    (ENVIRONMENT : --lake=LAKE --location=LOCATION)
    ((--os-image-version=OS_IMAGE_VERSION
      : --os-image-java-libraries=[OS_IMAGE_JAVA_LIBRARIES,...]
      --os-image-properties=[OS_IMAGE_PROPERTIES,...]
      --os-image-python-packages=[OS_IMAGE_PYTHON_PACKAGES,...])
      : --compute-disk-size-gb=COMPUTE_DISK_SIZE_GB; default=100
      --compute-max-node-count=COMPUTE_MAX_NODE_COUNT
      --compute-node-count=COMPUTE_NODE_COUNT) [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--labels=[KEY=VALUE,...]]
    [--async | --validate-only]
    [--session-enable-fast-startup
      --session-max-idle-duration=SESSION_MAX_IDLE_DURATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environments resource - The Environment to create a Environment to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environments or fully qualified identifier for the
     environments.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--os-image-version` | OS_IMAGE_VERSION |  | _[This must be specified.]_ Dataplex Image version. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--os-image-java-libraries` | [OS_IMAGE_JAVA_LIBRARIES,...] |  | _[This must be specified.]_ List of Java jars to be included in the runtime environment. Valid input includes Cloud Storage URIs to Jar binaries. For example, gs://bucket-name/my/path/to/file.jar |
| `--os-image-properties` | [OS_IMAGE_PROPERTIES,...] |  | _[This must be specified.]_ Override to common configuration of open source components installed on the Dataproc cluster. The properties to set on daemon config files. Property keys are specified in prefix:property format. |
| `--os-image-python-packages` | [OS_IMAGE_PYTHON_PACKAGES,...] |  | _[This must be specified.]_ A list of python packages to be installed. Valid formats include Cloud Storage URI to a PIP installable library. For example, gs://bucket-name/my/path/to/lib.tar.gz |
| `--compute-disk-size-gb` | COMPUTE_DISK_SIZE_GB | 100 | _[Compute resources associated with the analyze interactive workloads.]_ Size in GB of the disk. Default is 100 GB. |
| `--compute-max-node-count` | COMPUTE_MAX_NODE_COUNT |  | _[Compute resources associated with the analyze interactive workloads.]_ Maximum number of configurable nodes. |
| `--compute-node-count` | COMPUTE_NODE_COUNT |  | _[Compute resources associated with the analyze interactive workloads.]_ Total number of worker nodes in the cluster. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the Environment |
| `--display-name` | DISPLAY_NAME |  | Display Name of the Environment |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Dataplex Environment test-environment within lake test-lake in
location us-central1 inside project test-project , run:

    $ gcloud dataplex environments create test-environment \
        --project=test-project --location=us-central1 --lake=test-lake \
        --os-image-version=1.0

To know about the other required arguments to create an environment run:

    $ gcloud dataplex environment create --help
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/create)

---
### `gcloud dataplex environments delete`

Delete a Dataplex Environment

Delete a Dataplex Environment based on project, location, lake,
environment.

**Synopsis:**
```
gcloud dataplex environments delete
    (ENVIRONMENT : --lake=LAKE --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - Arguments and flags that define the Dataplex
Environment you want to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
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
To delete a Dataplex Environment test-environment in project test-project
under location us-central1 within lake test-lake, run:

    $ gcloud dataplex environments delete test-environment \
         --project=test-project --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/delete)

---
### `gcloud dataplex environments describe`

Retrieve a Dataplex Environment

Get a Dataplex Environment resource based on project, location, lake, and
environment.

**Synopsis:**
```
gcloud dataplex environments describe
    (ENVIRONMENT : --lake=LAKE --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - Arguments and flags that define the Dataplex
Environment you want to retrieve. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex Environment test-environment in project test-project
under location us-central1 within lake test-lake, run:

    $ gcloud dataplex environments describe test-environment \
        --project=test-project --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/describe)

---
### `gcloud dataplex environments get-iam-policy`

Retrieve a Dataplex Environment IAM policy

Get a Dataplex Environment Iam Policy based on project_id, location,
lake_id, and environment_id.

**Synopsis:**
```
gcloud dataplex environments get-iam-policy
    (ENVIRONMENT : --lake=LAKE --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environment resource - Arguments and flags that define the Dataplex
Environment IAM policy you want to retrieve. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environment or fully qualified identifier for the
     environment.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To get the IAM policy of a Dataplex Environment test-environment in project
test-project under location us-central1 within lake test-lake, run:

    $ gcloud dataplex environments get-iam-policy test-environment \
        --project=test-project --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/get-iam-policy)

---
### `gcloud dataplex environments list`

List Dataplex Environments

List Dataplex Environments based on project, location and lake.

**Synopsis:**
```
gcloud dataplex environments list (--lake=LAKE : --location=LOCATION)
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
To list all Dataplex Environments in lake test-lake under location
us-central1, run :-

    $ gcloud dataplex environments list --project=test-project \
       --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/list)

---
### `gcloud dataplex environments remove-iam-policy-binding`

Removes IAM policy binding from a Dataplex Environment

Removes IAM policy binding from a Dataplex Environment.

**Synopsis:**
```
gcloud dataplex environments remove-iam-policy-binding
    (ENVIRONMENT : --lake=LAKE --location=LOCATION) --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environments resource - The Environment to remove IAM policy binding from
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environments or fully qualified identifier for the
     environments.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
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
user testuser@gmail.com from an environment test-environment within lake
test-lake in location us-central1, run:

    $ gcloud dataplex environments remove-iam-policy-binding \
        test-environment --project=test-project --location=us-central1 \
        --lake=test-lake --role=roles/dataplex.viewer \
        --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/remove-iam-policy-binding)

---
### `gcloud dataplex environments set-iam-policy`

Set an IAM policy binding for a Dataplex Environment as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex environments set-iam-policy
    (ENVIRONMENT : --lake=LAKE --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environments resource - The Environment to set IAM policy to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environments or fully qualified identifier for the
     environments.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
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
policy.json and set it for the Dataplex environment test-environment within
lake test-lake in location us-central1:

    $ gcloud dataplex environments set-iam-policy test-environment \
        --project=test-project --location=us-central1 --lake=test-lake \
        policy.json

    where policy.json is the relative path to the json file.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/set-iam-policy)

---
### `gcloud dataplex environments update`

Update a Dataplex Environment with the given configurations

Update a Dataplex Environment with the given configurations.

**Synopsis:**
```
gcloud dataplex environments update
    (ENVIRONMENT : --lake=LAKE --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [--async | --validate-only]
    [--compute-disk-size-gb=COMPUTE_DISK_SIZE_GB
      --compute-max-node-count=COMPUTE_MAX_NODE_COUNT
      --compute-node-count=COMPUTE_NODE_COUNT
      --os-image-java-libraries=[OS_IMAGE_JAVA_LIBRARIES,...]
      --os-image-properties=[OS_IMAGE_PROPERTIES,...]
      --os-image-python-packages=[OS_IMAGE_PYTHON_PACKAGES,...]
      --os-image-version=OS_IMAGE_VERSION]
    [--session-enable-fast-startup
      --session-max-idle-duration=SESSION_MAX_IDLE_DURATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Environments resource - The Environment to update a Environment to. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument environment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENVIRONMENT
     ID of the environments or fully qualified identifier for the
     environments.

     To set the environment attribute:
     + provide the argument environment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument environment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of the Environment |
| `--display-name` | DISPLAY_NAME |  | Display Name of the Environment |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Dataplex environment test-environment within lake test-lake in
location us-central1 and change the description to Updated Description,
run:

    $ gcloud dataplex environments update test-environment \
        --project=test-project --location=us-central1 --lake=test-lake \
        --description='Updated Description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/update)

---

## `gcloud dataplex environments sessions` — manage Dataplex Sessions services
### `gcloud dataplex environments sessions list`

List Sessions associated with a Environment

List Sessions associated with a Environment based on project, location,
lake and environment.

**Synopsis:**
```
gcloud dataplex environments sessions list
    (--environment=ENVIRONMENT : --lake=LAKE --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--environment` | ENVIRONMENT |  | _[This must be specified.]_ ID of the environment or fully qualified identifier for the environment. To set the environment attribute: + provide the argument --environment on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--lake` | LAKE |  | _[This must be specified.]_ Identifier of the Dataplex lake resource. To set the lake attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --lake on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --environment on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list sessions associated with a Dataplex Environment test-environment in
project test-project and lake test-lake under location us-central1, run:

    $ gcloud dataplex environments sessions list test-environment \
        --project=test-project --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/environments/sessions/list)

---
# gcloud dataplex tasks

manage Dataplex Task services

### `gcloud dataplex tasks add-iam-policy-binding`

Add IAM policy binding to a Dataplex task resource

Add IAM policy binding to a Dataplex task resource.

**Synopsis:**
```
gcloud dataplex tasks add-iam-policy-binding
    (TASK : --lake=LAKE --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tasks resource - Arguments and flags that define the Dataplex task you
want to add IAM policy binding to. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the tasks or fully qualified identifier for the tasks.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
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
user 'testuser@gmail.com' to task test-task within lake test-lake in
location us-central, run:

    $ gcloud dataplex tasks add-iam-policy-binding test-task \
        --location=us-central1 --lake=test-lake \
        --role=roles/dataplex.viewer --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/add-iam-policy-binding)

---
### `gcloud dataplex tasks create`

Create a Dataplex task resource

Create a Dataplex task resource.

A task represents a user visible job that you want Dataplex to perform on a
schedule. It encapsulates your code, your parameters and the schedule.

This task ID must follow these rules: o Must contain only lowercase
letters, numbers, and hyphens. o Must start with a letter. o Must end with
a number or a letter. o Must be between 1-63 characters. o Must be unique
within the customer project / location.

**Synopsis:**
```
gcloud dataplex tasks create (TASK : --lake=LAKE --location=LOCATION)
    (--execution-service-account=EXECUTION_SERVICE_ACCOUNT
      : --execution-args=[KEY=VALUE,...]
      --execution-project=EXECUTION_PROJECT --kms-key=KMS_KEY
      --max-job-execution-lifetime=MAX_JOB_EXECUTION_LIFETIME)
    ([--notebook=NOTEBOOK
      : --notebook-archive-uris=[NOTEBOOK_ARCHIVE_URIS,...]
      --notebook-file-uris=[NOTEBOOK_FILE_URIS,...]
      --notebook-batch-executors-count=NOTEBOOK_BATCH_EXECUTORS_COUNT
      --notebook-batch-max-executors-count=NOTEBOOK_BATCH_MAX_EXECUTORS_COUNT --notebook-container-image=NOTEBOOK_CONTAINER_IMAGE --notebook-container-image-java-jars=[NOTEBOOK_CONTAINER_IMAGE_JAVA_JARS,
      ...] --notebook-container-image-properties=[KEY=VALUE,...]
      --notebook-vpc-network-tags=[NOTEBOOK_VPC_NETWORK_TAGS,...]
      --notebook-vpc-network-name=NOTEBOOK_VPC_NETWORK_NAME
      | --notebook-vpc-sub-network-name=NOTEBOOK_VPC_SUB_NETWORK_NAME]
      | [(--spark-main-class=SPARK_MAIN_CLASS
      | --spark-main-jar-file-uri=SPARK_MAIN_JAR_FILE_URI
      | --spark-python-script-file=SPARK_PYTHON_SCRIPT_FILE
      | --spark-sql-script=SPARK_SQL_SCRIPT
      | --spark-sql-script-file=SPARK_SQL_SCRIPT_FILE)
      : --spark-archive-uris=[SPARK_ARCHIVE_URIS,...]
      --spark-file-uris=[SPARK_FILE_URIS,...]
      --batch-executors-count=BATCH_EXECUTORS_COUNT
      --batch-max-executors-count=BATCH_MAX_EXECUTORS_COUNT
      --container-image=CONTAINER_IMAGE
      --container-image-java-jars=[CONTAINER_IMAGE_JAVA_JARS,...]
      --container-image-properties=[KEY=VALUE,...]
      --container-image-python-packages=[CONTAINER_IMAGE_PYTHON_PACKAGES,
      ...] --vpc-network-tags=[VPC_NETWORK_TAGS,...]
      --vpc-network-name=VPC_NETWORK_NAME
      | --vpc-sub-network-name=VPC_SUB_NETWORK_NAME])
    (--trigger-type=TRIGGER_TYPE : --trigger-disabled
      --trigger-max-retires=TRIGGER_MAX_RETIRES
      --trigger-schedule=TRIGGER_SCHEDULE
      --trigger-start-time=TRIGGER_START_TIME) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - Arguments and flags that specify the Dataplex Task you
want to create. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the task or fully qualified identifier for the task.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--execution-service-account` | EXECUTION_SERVICE_ACCOUNT |  | _[This must be specified.]_ Service account to use to execute a task. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--execution-args` | [KEY=VALUE,...] |  | _[This must be specified.]_ The arguments to pass to the task. The args can use placeholders of the format ${placeholder} as part of key/value string. These will be interpolated before passing the args to the driver. Currently supported placeholders: + ${task_id} + ${job_time} To pass positional args, set the key as TASK_ARGS. The value should be a comma-separated string of all the positional arguments. See https://cloud.google.com/sdk/gcloud/reference/topic/escaping for details on using a delimiter other than a comma. In case of other keys being present in the args, then TASK_ARGS will be passed as the last argument. |
| `--execution-project` | EXECUTION_PROJECT |  | _[This must be specified.]_ The project in which jobs are run. By default, the project containing the Lake is used. If a project is provided, the --execution-service-account must belong to this same project. |
| `--kms-key` | KMS_KEY |  | _[This must be specified.]_ The Cloud KMS key to use for encryption, of the form: projects/{project_number}/locations/{location_id}/keyRings/{key-ring-name}/cryptoKeys/{key-name} |
| `--max-job-execution-lifetime` | MAX_JOB_EXECUTION_LIFETIME |  | _[This must be specified.]_ The maximum duration before the job execution expires. |
| `--trigger-type` | one of: on-demand The ON_DEMAND trigger type runs the Dataplex task one time shortly after task creation |  | _[This must be specified.]_ Trigger type of the user-specified Dataplex Task. TRIGGER_TYPE must be one of: on-demand The ON_DEMAND trigger type runs the Dataplex task one time shortly after task creation. recurring The RECURRING trigger type makes the task scheduled to run periodically. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--trigger-disabled` |  |  | _[This must be specified.]_ Prevent the task from executing. This does not cancel already running tasks. It is intended to temporarily disable RECURRING tasks. |
| `--trigger-max-retires` | TRIGGER_MAX_RETIRES |  | _[This must be specified.]_ Number of retry attempts before aborting. Set to zero to never attempt to retry a failed task. |
| `--trigger-schedule` | TRIGGER_SCHEDULE |  | _[This must be specified.]_ Cron schedule (https://en.wikipedia.org/wiki/Cron) for running tasks periodically. |
| `--trigger-start-time` | TRIGGER_START_TIME |  | _[This must be specified.]_ The first run of the task begins after this time. If not specified, an ON_DEMAND task runs when it is submitted and a RECURRING task runs based on the trigger schedule. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the Dataplex task. |
| `--display-name` | DISPLAY_NAME |  | Display name of the Dataplex task. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Dataplex task test-task with ON_DEMAND trigger type,
dataplex-demo-test@test-project.iam.gserviceaccount.com as execution
service account and gs://test-bucket/test-file.py as spark python script
file within lake test-lake in location us-central1.

    $ gcloud dataplex tasks create test-task --location=us-central1 \
      --lake=test-lake \
      --execution-service-account=dataplex-demo-test@test-project.iam.\
    gserviceaccount.com \
        --spark-python-script-file=gs://test-bucket/test-file.py \
        --trigger-type=ON_DEMAND

To create a Dataplex task test-task with RECURRING trigger type starting
every hour at minute 0,
dataplex-demo-test@test-project.iam.gserviceaccount.com as execution
service account and gs://test-bucket/test-file.py as spark python script
file within lake test-lake in location us-central1.

    $ gcloud dataplex tasks create test-task --location=us-central1 \
        --lake=test-lake \
        --execution-service-account=dataplex-demo-test@test-project.iam.\
    gserviceaccount.com \
        --spark-python-script-file=gs://test-bucket/test-file.py \
        --trigger-type=RECURRING --trigger-schedule="0 * * * *"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/create)

---
### `gcloud dataplex tasks delete`

Delete a Dataplex task resource

Delete a Dataplex task resource.

**Synopsis:**
```
gcloud dataplex tasks delete (TASK : --lake=LAKE --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - Arguments and flags that define the Dataplex Task you want
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the task or fully qualified identifier for the task.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
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
To delete a Dataplex task test-task within lake test-lake in location
us-central1, run:

    $ gcloud dataplex tasks delete test-task --location=us-central1 \
      --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/delete)

---
### `gcloud dataplex tasks describe`

Describe a Dataplex task resource

Describe a Dataplex task resource.

Displays all details of a Dataplex task resource given a valid task ID.

**Synopsis:**
```
gcloud dataplex tasks describe (TASK : --lake=LAKE --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - Arguments and flags that define the Dataplex Tasks you
want to retrieve. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the task or fully qualified identifier for the task.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To describe a Dataplex task test-task within lake test-lake in location
us-central1, run:

    $ gcloud dataplex tasks describe test-task --location=us-central1 \
      --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/describe)

---
### `gcloud dataplex tasks get-iam-policy`

Get the IAM policy for a Dataplex task resource

Displays the IAM policy associated with a Dataplex task resource. If
formatted as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates.

**Synopsis:**
```
gcloud dataplex tasks get-iam-policy
    (TASK : --lake=LAKE --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - Arguments and flags that define the Dataplex Task IAM
policy you want to retrieve. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the task or fully qualified identifier for the task.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Examples:**
```bash
To print the IAM policy for Dataplex lake test-task within lake test-lake
in location us-central1, run:

    $ gcloud dataplex tasks get-iam-policy test-task \
        --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/get-iam-policy)

---
### `gcloud dataplex tasks list`

List Dataplex task resources under a lake

List Dataplex Task resources under a specific project, location, and lake.

**Synopsis:**
```
gcloud dataplex tasks list (--lake=LAKE : --location=LOCATION)
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
To list all Dataplex Task resources under the lake test-lake within project
test-project in location us-central1, run:

    $ gcloud dataplex tasks list --project=test-project \
      --location=us-central1 --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/list)

---
### `gcloud dataplex tasks remove-iam-policy-binding`

Remove IAM policy binding from a Dataplex task resource

Remove IAM policy binding from a Dataplex task resource.

**Synopsis:**
```
gcloud dataplex tasks remove-iam-policy-binding
    (TASK : --lake=LAKE --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tasks resource - Arguments and flags that define the Dataplex task you
want to remove IAM policy binding from. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the tasks or fully qualified identifier for the tasks.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
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
user testuser@gmail.com from a task test-task within lake test-lake in
location us-central1, run:

    $ gcloud dataplex tasks remove-iam-policy-binding test-task \
        --location=us-central1 --lake=test-lake \
        --role=roles/dataplex.viewer --member=user:testuser@gmail.com

See https://cloud.google.com/dataplex/docs/iam-roles for details of policy
role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/remove-iam-policy-binding)

---
### `gcloud dataplex tasks run`

Trigger one-time run of a Dataplex task

Trigger one-time run of a Dataplex task.

**Synopsis:**
```
gcloud dataplex tasks run (TASK : --lake=LAKE --location=LOCATION)
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
    [-- execution-spec-args ...]
```

**Positional arguments:**
```
Tasks resource - Arguments and flags that define the Dataplex task you
want to run. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the tasks or fully qualified identifier for the tasks.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

[-- execution-spec-args ...]
   Execution spec arguments to pass to the driver. Follows the format
   argKey=argValue.

   The '--' argument must be specified between gcloud specific args on the
   left and execution-spec-args on the right.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To trigger a one-time run of a Dataplex task test-task within lake
test-lake in location us-central1, run:

    $ gcloud dataplex tasks run test-task --location=us-central1 \
         --lake=test-lake
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/run)

---
### `gcloud dataplex tasks set-iam-policy`

Set the IAM policy to a Dataplex task as defined in a JSON or YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud dataplex tasks set-iam-policy
    (TASK : --lake=LAKE --location=LOCATION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Tasks resource - Arguments and flags that define the Dataplex task you
want to set IAM policy to. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the tasks or fully qualified identifier for the tasks.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     The identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     The location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
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
policy.json and set it for the Dataplex task test-task within lake
test-lake in location us-central1:

    $ gcloud dataplex tasks set-iam-policy --lake=test-lake \
        --location=us-central1 test-task policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/set-iam-policy)

---
### `gcloud dataplex tasks update`

Update a Dataplex task resource

Update a Dataplex task resource with the given configurations.

**Synopsis:**
```
gcloud dataplex tasks update (TASK : --lake=LAKE --location=LOCATION)
    [--async] [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--execution-args=[KEY=VALUE,...] --execution-project=EXECUTION_PROJECT
      --execution-service-account=EXECUTION_SERVICE_ACCOUNT
      --kms-key=KMS_KEY
      --max-job-execution-lifetime=MAX_JOB_EXECUTION_LIFETIME]
    [--notebook=NOTEBOOK
      --notebook-archive-uris=[NOTEBOOK_ARCHIVE_URIS,...]
      --notebook-file-uris=[NOTEBOOK_FILE_URIS,...]
      --notebook-batch-executors-count=NOTEBOOK_BATCH_EXECUTORS_COUNT
      --notebook-batch-max-executors-count=NOTEBOOK_BATCH_MAX_EXECUTORS_COUNT --notebook-container-image=NOTEBOOK_CONTAINER_IMAGE --notebook-container-image-java-jars=[NOTEBOOK_CONTAINER_IMAGE_JAVA_JARS,
      ...] --notebook-container-image-properties=[KEY=VALUE,...]
      --notebook-vpc-network-tags=[NOTEBOOK_VPC_NETWORK_TAGS,...]
      --notebook-vpc-network-name=NOTEBOOK_VPC_NETWORK_NAME
      | --notebook-vpc-sub-network-name=NOTEBOOK_VPC_SUB_NETWORK_NAME
      | --spark-archive-uris=[SPARK_ARCHIVE_URIS,...]
      --spark-file-uris=[SPARK_FILE_URIS,...]
      --batch-executors-count=BATCH_EXECUTORS_COUNT
      --batch-max-executors-count=BATCH_MAX_EXECUTORS_COUNT
      --container-image=CONTAINER_IMAGE
      --container-image-java-jars=[CONTAINER_IMAGE_JAVA_JARS,...]
      --container-image-properties=[KEY=VALUE,...]
      --container-image-python-packages=[CONTAINER_IMAGE_PYTHON_PACKAGES,
      ...] --vpc-network-tags=[VPC_NETWORK_TAGS,...]
      --vpc-network-name=VPC_NETWORK_NAME
      --vpc-sub-network-name=VPC_SUB_NETWORK_NAME
      --spark-main-class=SPARK_MAIN_CLASS
      | --spark-main-jar-file-uri=SPARK_MAIN_JAR_FILE_URI
      | --spark-python-script-file=SPARK_PYTHON_SCRIPT_FILE
      | --spark-sql-script=SPARK_SQL_SCRIPT
      | --spark-sql-script-file=SPARK_SQL_SCRIPT_FILE]
    [--trigger-disabled --trigger-max-retires=TRIGGER_MAX_RETIRES
      --trigger-schedule=TRIGGER_SCHEDULE
      --trigger-start-time=TRIGGER_START_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - Arguments and flags that specify the Dataplex Task you
want to update. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument task on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the task or fully qualified identifier for the task.

     To set the task attribute:
     + provide the argument task on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument task on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the task. |
| `--display-name` | DISPLAY_NAME |  | Display name of the task. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Dataplex task test-task within lake test-lake in location
us-central1 and change the description to Updated Description, run:

    $ gcloud dataplex tasks update \
        projects/test-project/locations/us-central1/lakes/test-lake/\
    tasks/test-task --description='Updated Description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/update)

---

## `gcloud dataplex tasks jobs` — manage Dataplex Jobs services
### `gcloud dataplex tasks jobs cancel`

Cancel a Dataplex Job running a particular task

Cancel the operation that the given Dataplex Job is running task under a
specific project, location, lake and task.

**Synopsis:**
```
gcloud dataplex tasks jobs cancel
    (JOB : --lake=LAKE --location=LOCATION --task=TASK)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Arguments and flags that define the Dataplex Job running a
particular Task you want to cancel. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --task=TASK
     Identifier of the Dataplex task resource.

     To set the task attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --task on the command line.
```

**Examples:**
```bash
To cancel an job test-job running task test-task within lake test-lake in
location us-central1, run:

    $ gcloud dataplex tasks jobs cancel test-job \
        --location=us-central1 --lake=test-lake --task=test-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/jobs/cancel)

---
### `gcloud dataplex tasks jobs describe`

Describe a Dataplex job running a particular task

Describe a Dataplex job running a particular task.

Displays all details of a Dataplex job given a valid job ID.

**Synopsis:**
```
gcloud dataplex tasks jobs describe
    (JOB : --lake=LAKE --location=LOCATION --task=TASK)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Arguments and flags that define the Dataplex Job running a
particular Task you want to retrieve. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --lake=LAKE
     Identifier of the Dataplex lake resource.

     To set the lake attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --lake on the command line.

  --location=LOCATION
     Location of the Dataplex resource.

     To set the location attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property dataplex/location.

  --task=TASK
     Identifier of the Dataplex task resource.

     To set the task attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --task on the command line.
```

**Examples:**
```bash
To describe a Dataplex job test-job running a task test-task within lake
test-lake in location us-central1, run:

    $ gcloud dataplex tasks jobs describe test-job \
        --location=us-central1 --lake=test-lake --task=test-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/jobs/describe)

---
### `gcloud dataplex tasks jobs list`

List job runs of a Dataplex task resource

List Jobs runs of a Task under a specific project, location, lake and task.

**Synopsis:**
```
gcloud dataplex tasks jobs list
    (--task=TASK : --lake=LAKE --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--task` | TASK |  | _[This must be specified.]_ ID of the task or fully qualified identifier for the task. To set the task attribute: + provide the argument --task on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--lake` | LAKE |  | _[This must be specified.]_ Identifier of the Dataplex lake resource. To set the lake attribute: + provide the argument --task on the command line with a fully specified name; + provide the argument --lake on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the Dataplex resource. To set the location attribute: + provide the argument --task on the command line with a fully specified name; + provide the argument --location on the command line; + set the property dataplex/location. |


**Examples:**
```bash
To list all the Dataplex job runs for a task test-task within lake
test-lake in location us-central1, run:

    gcloud dataplex tasks jobs list --location=us-central1 --lake=test-lake --task=test-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataplex/tasks/jobs/list)

---
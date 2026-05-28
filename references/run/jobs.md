# gcloud run jobs

view and manage your Cloud Run jobs

### `gcloud run jobs add-iam-policy-binding`

Add IAM policy binding to a Cloud Run job

Add an IAM policy binding to the IAM policy of a Cloud Run job. One binding
consists of a member, and a role.

**Synopsis:**
```
gcloud run jobs add-iam-policy-binding JOB --member=PRINCIPAL --role=ROLE
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job for which to add IAM policy binding to. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/run.invoker' for the
user 'test-user@gmail.com' with job 'my-job' and region 'us-central1', run:

    $ gcloud run jobs add-iam-policy-binding my-job \
        --region='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/run.invoker'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/add-iam-policy-binding)

---
### `gcloud run jobs create`

Create a Cloud Run job

Creates a new Cloud Run job.

**Synopsis:**
```
gcloud run jobs create [JOB] [--binary-authorization=POLICY]
    [--breakglass=JUSTIFICATION] [--container=CONTAINER]
    [--gpu-type=GPU_TYPE] [--[no-]gpu-zonal-redundancy] [--key=KEY]
    [--labels=[KEY=VALUE,...]] [--max-retries=MAX_RETRIES]
    [--parallelism=PARALLELISM] [--region=REGION]
    [--service-account=SERVICE_ACCOUNT]
    [--set-cloudsql-instances=[CLOUDSQL-INSTANCES,...]]
    [--task-timeout=TASK_TIMEOUT] [--tasks=TASKS; default=1]
    [--vpc-connector=VPC_CONNECTOR] [--vpc-egress=VPC_EGRESS]
    [--add-volume=[KEY=VALUE,...]
      --clear-volumes --remove-volume=[VOLUME,...]]
    [--add-volume-mount=[volume=NAME,mount-path=MOUNT_PATH,...]
      --args=[ARG,...] --clear-volume-mounts --command=[COMMAND,...]
      --cpu=CPU --depends-on=[CONTAINER,...] --gpu=GPU --image=IMAGE
      --memory=MEMORY --remove-volume-mount=[MOUNT_PATH,...]
      --startup-probe=[KEY=VALUE,...] --clear-env-vars
      | --env-vars-file=FILE_PATH | --set-env-vars=[KEY=VALUE,...]
      | --remove-env-vars=[KEY,...]
      --update-env-vars=[KEY=VALUE,...] --clear-secrets
      | --set-secrets=[KEY=VALUE,...]
      | --remove-secrets=[KEY,...] --update-secrets=[KEY=VALUE,...]]
    [--async | --execute-now --wait]
    [--network=NETWORK --network-tags=[TAG,...] --subnet=SUBNET]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to create. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * specify the job name from an interactive prompt with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [JOB]
     ID of the Job or fully qualified identifier for the Job.

     To set the jobs attribute:
     + provide the argument JOB on the command line;
     + specify the job name from an interactive prompt.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--binary-authorization` | POLICY |  | Binary Authorization policy to check against. This must be set to "default". |
| `--breakglass` | JUSTIFICATION |  | Justification to bypass Binary Authorization policy constraints and allow the operation. See https://cloud.google.com/binary-authorization/docs/using-breakglass for more information. Next update or deploy command will automatically clear existing breakglass justification. |
| `--container` | CONTAINER |  | Specifies a container by name. Flags following --container will apply to the specified container. Flags that are not container-specific must be specified before --container. |
| `--gpu-type` | GPU_TYPE |  | The GPU type to use. |
| `--[no-]gpu-zonal-redundancy` |  |  | Set GPU zonal redundancy. Use --gpu-zonal-redundancy to enable and --no-gpu-zonal-redundancy to disable. |
| `--key` | KEY |  | CMEK key reference to encrypt the container with. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--max-retries` | MAX_RETRIES |  | Number of times a task is allowed to restart in case of failure before being failed permanently. This applies per-task, not per-job. If set to 0, tasks will only run once and never be retried on failure. |
| `--parallelism` | PARALLELISM |  | Number of tasks that may run concurrently. Must be less than or equal to the number of tasks. Set to 0 to unset. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--service-account` | SERVICE_ACCOUNT |  | the email address of an IAM service account associated with the revision of the service. The service account represents the identity of the running revision, and determines what permissions the revision has. |
| `--set-cloudsql-instances` | [CLOUDSQL-INSTANCES,...] |  | You can specify a name of a Cloud SQL instance if it's in the same project and region as your Cloud Run resource; otherwise specify <project>:<region>:<instance> for the instance. |
| `--task-timeout` | TASK_TIMEOUT |  | Set the maximum time (deadline) a job task attempt can run for. In the case of retries, this deadline applies to each attempt of a task. If the task attempt does not complete within this time, it will be killed. It is specified as a duration; for example, "10m5s" is ten minutes, and five seconds. If you don't specify a unit, seconds is assumed. For example, "10" is 10 seconds. |
| `--tasks` | TASKS | 1 | Number of tasks that must run to completion for the execution to be considered done. |
| `--vpc-connector` | VPC_CONNECTOR |  | Set a VPC connector for this resource. |
| `--vpc-egress` | one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector |  | Specify which of the outbound traffic to send through Direct VPC egress or the VPC connector for this resource. This resource must have Direct VPC egress enabled or a VPC connector to set this flag. VPC_EGRESS must be one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector. Provides the same functionality as 'all-traffic'. Prefer to use 'all-traffic' instead. all-traffic Sends all outbound traffic through Direct VPC egress or the VPC connector. private-ranges-only Default option. Sends outbound traffic to private IP addresses (RFC 1918 and Private Google Access IPs) through Direct VPC egress or the VPC connector. Traffic to other Cloud Run services might require additional configuration. See https://cloud.google.com/run/docs/securing/private-networking#send_requests_to_other_services_and_services for more information. |
| `--add-volume` | [KEY=VALUE,...] |  | Adds a volume to the Cloud Run resource. To add more than one volume, specify this flag multiple times. Volumes must have a name and type key. Only certain values are supported for type. Depending on the provided type, other keys will be required. The following types are supported with the specified additional keys: cloud-storage: A volume representing a Cloud Storage bucket. This volume type is mounted using Cloud Storage FUSE. See https://cloud.google.com/storage/docs/gcs-fuse for the details and limitations of this filesystem. Additional keys: * bucket: (required) the name of the bucket to use as the source of this volume * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. * mount-options: (optional) A list of flags to pass to GCSFuse. Flags should be specified without leading dashes and separated by semicolons. in-memory: An ephemeral volume that stores data in the instance's memory. With this type of volume, data is not shared between instances and all data will be lost when the instance it is on is terminated. Additional keys: * size-limit: (optional) A quantity representing the maximum amount of memory allocated to this volume, such as "512Mi" or "3G". Data stored in an in-memory volume consumes the memory allocation of the container that wrote the data. If size-limit is not specified, the maximum size will be half the total memory limit of all containers. nfs: Represents a volume backed by an NFS server. Additional keys: * location: (required) The location of the NFS Server, in the form SERVER:/PATH * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. |
| `--clear-volumes` |  |  | Remove all existing volumes from the Cloud Run resource, including volumes mounted as secrets |
| `--remove-volume` | [VOLUME,...] |  | Removes volumes from the Cloud Run resource. |


**Examples:**
```bash
To deploy a new job my-data-transformation on Cloud Run:

    $ gcloud run jobs create my-data-transformation \
      --image=us-docker.pkg.dev/project/image

You may also omit the job name. Then a prompt will be displayed with a
suggested default value:

    $ gcloud run jobs create --image=us-docker.pkg.dev/project/image
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/create)

---
### `gcloud run jobs delete`

Delete a job

Delete a job.

**Synopsis:**
```
gcloud run jobs delete JOB [--[no-]async] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to delete. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the Job or fully qualified identifier for the Job.

     To set the jobs attribute:
     + provide the argument JOB on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]async` |  |  | Return immediately, without waiting for the operation in progress to complete. Defaults to --no-async. Use --async to enable and --no-async to disable. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To delete a job:

    $ gcloud run jobs delete job-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/delete)

---
### `gcloud run jobs deploy`

Create or update a Cloud Run job

Creates or updates a Cloud Run job.

**Synopsis:**
```
gcloud run jobs deploy [JOB] [--binary-authorization=POLICY]
    [--breakglass=JUSTIFICATION] [--container=CONTAINER]
    [--gpu-type=GPU_TYPE] [--[no-]gpu-zonal-redundancy] [--key=KEY]
    [--labels=[KEY=VALUE,...]] [--max-retries=MAX_RETRIES]
    [--parallelism=PARALLELISM] [--region=REGION]
    [--remove-containers=[CONTAINER,...]]
    [--service-account=SERVICE_ACCOUNT]
    [--set-cloudsql-instances=[CLOUDSQL-INSTANCES,...]]
    [--task-timeout=TASK_TIMEOUT] [--tasks=TASKS; default=1]
    [--vpc-connector=VPC_CONNECTOR] [--vpc-egress=VPC_EGRESS]
    [--add-volume=[KEY=VALUE,...]
      --clear-volumes --remove-volume=[VOLUME,...]]
    [--add-volume-mount=[volume=NAME,mount-path=MOUNT_PATH,...]
      --args=[ARG,...] --clear-volume-mounts --command=[COMMAND,...]
      --cpu=CPU --depends-on=[CONTAINER,...] --gpu=GPU --memory=MEMORY
      --remove-volume-mount=[MOUNT_PATH,...]
      --startup-probe=[KEY=VALUE,...] --clear-env-vars
      | --env-vars-file=FILE_PATH | --set-env-vars=[KEY=VALUE,...]
      | --remove-env-vars=[KEY,...]
      --update-env-vars=[KEY=VALUE,...] --clear-secrets
      | --set-secrets=[KEY=VALUE,...] | --remove-secrets=[KEY,...]
      --update-secrets=[KEY=VALUE,...] --image=IMAGE | --source=SOURCE]
    [--async | --execute-now --wait]
    [--clear-network
      | --network=NETWORK --subnet=SUBNET --clear-network-tags
      | --network-tags=[TAG,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to deploy. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * specify the job name from an interactive prompt with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [JOB]
     ID of the Job or fully qualified identifier for the Job.

     To set the jobs attribute:
     + provide the argument JOB on the command line;
     + specify the job name from an interactive prompt.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--binary-authorization` | POLICY |  | Binary Authorization policy to check against. This must be set to "default". |
| `--breakglass` | JUSTIFICATION |  | Justification to bypass Binary Authorization policy constraints and allow the operation. See https://cloud.google.com/binary-authorization/docs/using-breakglass for more information. Next update or deploy command will automatically clear existing breakglass justification. |
| `--container` | CONTAINER |  | Specifies a container by name. Flags following --container will apply to the specified container. Flags that are not container-specific must be specified before --container. |
| `--gpu-type` | GPU_TYPE |  | The GPU type to use. |
| `--[no-]gpu-zonal-redundancy` |  |  | Set GPU zonal redundancy. Use --gpu-zonal-redundancy to enable and --no-gpu-zonal-redundancy to disable. |
| `--key` | KEY |  | CMEK key reference to encrypt the container with. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--max-retries` | MAX_RETRIES |  | Number of times a task is allowed to restart in case of failure before being failed permanently. This applies per-task, not per-job. If set to 0, tasks will only run once and never be retried on failure. |
| `--parallelism` | PARALLELISM |  | Number of tasks that may run concurrently. Must be less than or equal to the number of tasks. Set to 0 to unset. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--remove-containers` | [CONTAINER,...] |  | List of containers to remove. |
| `--service-account` | SERVICE_ACCOUNT |  | the email address of an IAM service account associated with the revision of the service. The service account represents the identity of the running revision, and determines what permissions the revision has. |
| `--set-cloudsql-instances` | [CLOUDSQL-INSTANCES,...] |  | You can specify a name of a Cloud SQL instance if it's in the same project and region as your Cloud Run resource; otherwise specify <project>:<region>:<instance> for the instance. |
| `--task-timeout` | TASK_TIMEOUT |  | Set the maximum time (deadline) a job task attempt can run for. In the case of retries, this deadline applies to each attempt of a task. If the task attempt does not complete within this time, it will be killed. It is specified as a duration; for example, "10m5s" is ten minutes, and five seconds. If you don't specify a unit, seconds is assumed. For example, "10" is 10 seconds. |
| `--tasks` | TASKS | 1 | Number of tasks that must run to completion for the execution to be considered done. |
| `--vpc-connector` | VPC_CONNECTOR |  | Set a VPC connector for this resource. |
| `--vpc-egress` | one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector |  | Specify which of the outbound traffic to send through Direct VPC egress or the VPC connector for this resource. This resource must have Direct VPC egress enabled or a VPC connector to set this flag. VPC_EGRESS must be one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector. Provides the same functionality as 'all-traffic'. Prefer to use 'all-traffic' instead. all-traffic Sends all outbound traffic through Direct VPC egress or the VPC connector. private-ranges-only Default option. Sends outbound traffic to private IP addresses (RFC 1918 and Private Google Access IPs) through Direct VPC egress or the VPC connector. Traffic to other Cloud Run services might require additional configuration. See https://cloud.google.com/run/docs/securing/private-networking#send_requests_to_other_services_and_services for more information. |
| `--add-volume` | [KEY=VALUE,...] |  | Adds a volume to the Cloud Run resource. To add more than one volume, specify this flag multiple times. Volumes must have a name and type key. Only certain values are supported for type. Depending on the provided type, other keys will be required. The following types are supported with the specified additional keys: cloud-storage: A volume representing a Cloud Storage bucket. This volume type is mounted using Cloud Storage FUSE. See https://cloud.google.com/storage/docs/gcs-fuse for the details and limitations of this filesystem. Additional keys: * bucket: (required) the name of the bucket to use as the source of this volume * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. * mount-options: (optional) A list of flags to pass to GCSFuse. Flags should be specified without leading dashes and separated by semicolons. in-memory: An ephemeral volume that stores data in the instance's memory. With this type of volume, data is not shared between instances and all data will be lost when the instance it is on is terminated. Additional keys: * size-limit: (optional) A quantity representing the maximum amount of memory allocated to this volume, such as "512Mi" or "3G". Data stored in an in-memory volume consumes the memory allocation of the container that wrote the data. If size-limit is not specified, the maximum size will be half the total memory limit of all containers. nfs: Represents a volume backed by an NFS server. Additional keys: * location: (required) The location of the NFS Server, in the form SERVER:/PATH * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. |
| `--clear-volumes` |  |  | Remove all existing volumes from the Cloud Run resource, including volumes mounted as secrets |
| `--remove-volume` | [VOLUME,...] |  | Removes volumes from the Cloud Run resource. |


**Examples:**
```bash
To deploy a new job my-data-transformation to Cloud Run:

    $ gcloud run jobs deploy my-data-transformation \
      --image=us-docker.pkg.dev/project/image

You may also omit the job name. Then a prompt will be displayed with a
suggested default value:

    $ gcloud run jobs deploy --image=us-docker.pkg.dev/project/image
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/deploy)

---
### `gcloud run jobs describe`

Obtain details about jobs

Obtain details about jobs.

**Synopsis:**
```
gcloud run jobs describe JOB [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to describe. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the Job or fully qualified identifier for the Job.

     To set the jobs attribute:
     + provide the argument JOB on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To describe a job:

    $ gcloud run jobs describe my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/describe)

---
### `gcloud run jobs execute`

Execute a job

Execute a job.

**Synopsis:**
```
gcloud run jobs execute [JOB] [--container=CONTAINER] [--region=REGION]
    [--task-timeout=TASK_TIMEOUT] [--tasks=TASKS]
    [--args=[ARG,...] --update-env-vars=[KEY=VALUE,...]] [--async | --wait]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to execute. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * specify the job name from an interactive prompt with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [JOB]
     ID of the Job or fully qualified identifier for the Job.

     To set the jobs attribute:
     + provide the argument JOB on the command line;
     + specify the job name from an interactive prompt.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--container` | CONTAINER |  | Specifies a container by name. Flags following --container will apply to the specified container. Flags that are not container-specific must be specified before --container. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--task-timeout` | TASK_TIMEOUT |  | The existing maximum time (deadline) a job task attempt can run for. If provided, an execution will be created with this value. Otherwise existing maximum time of the job is used. In the case of retries, this deadline applies to each attempt of a task. If the task attempt does not complete within this time, it will be killed. It is specified as a duration; for example, "10m5s" is ten minutes, and five seconds. If you don't specify a unit, seconds is assumed. For example, "10" is 10 seconds. |
| `--tasks` | TASKS |  | Number of tasks that must run to completion for the execution to be considered done. If provided, an execution will be created with this value. Otherwise the existing task count of the job is used. |


**Examples:**
```bash
To execute a job:

    $ gcloud run jobs execute my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/execute)

---
### `gcloud run jobs get-iam-policy`

Get the IAM policy for a Cloud Run job

This command gets the IAM policy for a job. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates; see $ gcloud alpha run
registries set-iam-policy for additional details.

**Synopsis:**
```
gcloud run jobs get-iam-policy JOB [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job for which to display the IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To print the IAM policy for a given job, run:

    $ gcloud run jobs get-iam-policy --region=us-central1 my-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/get-iam-policy)

---
### `gcloud run jobs list`

List jobs

List jobs.

**Synopsis:**
```
gcloud run jobs list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To list all jobs in all regions:

    $ gcloud run jobs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/list)

---
### `gcloud run jobs remove-iam-policy-binding`

Remove IAM policy binding of a Cloud Run job

Remove an IAM policy binding from the IAM policy of a job. One binding
consists of a member, and a role.

**Synopsis:**
```
gcloud run jobs remove-iam-policy-binding JOB --member=PRINCIPAL
    --role=ROLE [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job for which to remove the IAM policy binding. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/run.invoker' for the
user 'test-user@gmail.com' with servcie 'my-job' and region 'us-central1',
run:

    $ gcloud run jobs remove-iam-policy-binding my-job \
        --region='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/run.invoker'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/remove-iam-policy-binding)

---
### `gcloud run jobs replace`

Create or replace a job from a YAML job specification

Creates or replaces a job from a YAML job specification.

**Synopsis:**
```
gcloud run jobs replace FILE [--async] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FILE
   The absolute path to the YAML file with a Cloud Run job definition for
   the job to update or create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To replace the specification for a job defined in myjob.yaml

    $ gcloud run jobs replace myjob.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/replace)

---
### `gcloud run jobs set-iam-policy`

Set the IAM policy for a job

This command replaces the existing IAM policy for a job, given a job and a
file encoded in JSON or YAML that contains the IAM policy. If the given
policy file specifies an "etag" value, then the replacement will succeed
only if the policy already in place matches that etag. (An etag obtain via
get-iam-policy will prevent the replacement if the policy for the job has
been subsequently updated.) A policy file that does not contain an etag
value will replace any existing policy for the job.

**Synopsis:**
```
gcloud run jobs set-iam-policy JOB POLICY_FILE [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The job for which to set the IAM policy. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument job on the command line with a fully specified
   name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument job on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for a job with identifier 'my-job'

    $ gcloud run jobs set-iam-policy --region=us-central1 my-job \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/set-iam-policy)

---
### `gcloud run jobs update`

Update a Cloud Run Job

Updates a Cloud Run job.

**Synopsis:**
```
gcloud run jobs update [JOB] [--breakglass=JUSTIFICATION]
    [--clear-vpc-connector] [--container=CONTAINER] [--gpu-type=GPU_TYPE]
    [--[no-]gpu-zonal-redundancy] [--key=KEY] [--max-retries=MAX_RETRIES]
    [--parallelism=PARALLELISM] [--region=REGION]
    [--remove-containers=[CONTAINER,...]]
    [--service-account=SERVICE_ACCOUNT] [--task-timeout=TASK_TIMEOUT]
    [--tasks=TASKS; default=1] [--vpc-connector=VPC_CONNECTOR]
    [--vpc-egress=VPC_EGRESS]
    [--add-cloudsql-instances=[CLOUDSQL-INSTANCES,...]
      | --clear-cloudsql-instances
      | --remove-cloudsql-instances=[CLOUDSQL-INSTANCES,...]
      | --set-cloudsql-instances=[CLOUDSQL-INSTANCES,...]]
    [--add-volume=[KEY=VALUE,...]
      --clear-volumes --remove-volume=[VOLUME,...]]
    [--add-volume-mount=[volume=NAME,mount-path=MOUNT_PATH,...]
      --args=[ARG,...] --clear-volume-mounts --command=[COMMAND,...]
      --cpu=CPU --depends-on=[CONTAINER,...] --gpu=GPU --image=IMAGE
      --memory=MEMORY --remove-volume-mount=[MOUNT_PATH,...]
      --startup-probe=[KEY=VALUE,...] --clear-env-vars
      | --env-vars-file=FILE_PATH | --set-env-vars=[KEY=VALUE,...]
      | --remove-env-vars=[KEY,...]
      --update-env-vars=[KEY=VALUE,...] --clear-secrets
      | --set-secrets=[KEY=VALUE,...]
      | --remove-secrets=[KEY,...] --update-secrets=[KEY=VALUE,...]]
    [--async | --execute-now --wait]
    [--binary-authorization=POLICY | --clear-binary-authorization]
    [--clear-labels | --remove-labels=[KEY,...] --labels=[KEY=VALUE,...]
      | --update-labels=[KEY=VALUE,...]]
    [--clear-network
      | --network=NETWORK --subnet=SUBNET --clear-network-tags
      | --network-tags=[TAG,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - Job to update. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * specify the job name from an interactive prompt with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [JOB]
     ID of the Job or fully qualified identifier for the Job.

     To set the jobs attribute:
     + provide the argument JOB on the command line;
     + specify the job name from an interactive prompt.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--breakglass` | JUSTIFICATION |  | Justification to bypass Binary Authorization policy constraints and allow the operation. See https://cloud.google.com/binary-authorization/docs/using-breakglass for more information. Next update or deploy command will automatically clear existing breakglass justification. |
| `--clear-vpc-connector` |  |  | Remove the VPC connector for this resource. |
| `--container` | CONTAINER |  | Specifies a container by name. Flags following --container will apply to the specified container. Flags that are not container-specific must be specified before --container. |
| `--gpu-type` | GPU_TYPE |  | The GPU type to use. |
| `--[no-]gpu-zonal-redundancy` |  |  | Set GPU zonal redundancy. Use --gpu-zonal-redundancy to enable and --no-gpu-zonal-redundancy to disable. |
| `--key` | KEY |  | CMEK key reference to encrypt the container with. |
| `--max-retries` | MAX_RETRIES |  | Number of times a task is allowed to restart in case of failure before being failed permanently. This applies per-task, not per-job. If set to 0, tasks will only run once and never be retried on failure. |
| `--parallelism` | PARALLELISM |  | Number of tasks that may run concurrently. Must be less than or equal to the number of tasks. Set to 0 to unset. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--remove-containers` | [CONTAINER,...] |  | List of containers to remove. |
| `--service-account` | SERVICE_ACCOUNT |  | the email address of an IAM service account associated with the revision of the service. The service account represents the identity of the running revision, and determines what permissions the revision has. |
| `--task-timeout` | TASK_TIMEOUT |  | Set the maximum time (deadline) a job task attempt can run for. In the case of retries, this deadline applies to each attempt of a task. If the task attempt does not complete within this time, it will be killed. It is specified as a duration; for example, "10m5s" is ten minutes, and five seconds. If you don't specify a unit, seconds is assumed. For example, "10" is 10 seconds. |
| `--tasks` | TASKS | 1 | Number of tasks that must run to completion for the execution to be considered done. |
| `--vpc-connector` | VPC_CONNECTOR |  | Set a VPC connector for this resource. |
| `--vpc-egress` | one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector |  | Specify which of the outbound traffic to send through Direct VPC egress or the VPC connector for this resource. This resource must have Direct VPC egress enabled or a VPC connector to set this flag. VPC_EGRESS must be one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector. Provides the same functionality as 'all-traffic'. Prefer to use 'all-traffic' instead. all-traffic Sends all outbound traffic through Direct VPC egress or the VPC connector. private-ranges-only Default option. Sends outbound traffic to private IP addresses (RFC 1918 and Private Google Access IPs) through Direct VPC egress or the VPC connector. Traffic to other Cloud Run services might require additional configuration. See https://cloud.google.com/run/docs/securing/private-networking#send_requests_to_other_services_and_services for more information. |
| `--add-volume` | [KEY=VALUE,...] |  | _[values.]_ Adds a volume to the Cloud Run resource. To add more than one volume, specify this flag multiple times. Volumes must have a name and type key. Only certain values are supported for type. Depending on the provided type, other keys will be required. The following types are supported with the specified additional keys: cloud-storage: A volume representing a Cloud Storage bucket. This volume type is mounted using Cloud Storage FUSE. See https://cloud.google.com/storage/docs/gcs-fuse for the details and limitations of this filesystem. Additional keys: * bucket: (required) the name of the bucket to use as the source of this volume * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. * mount-options: (optional) A list of flags to pass to GCSFuse. Flags should be specified without leading dashes and separated by semicolons. in-memory: An ephemeral volume that stores data in the instance's memory. With this type of volume, data is not shared between instances and all data will be lost when the instance it is on is terminated. Additional keys: * size-limit: (optional) A quantity representing the maximum amount of memory allocated to this volume, such as "512Mi" or "3G". Data stored in an in-memory volume consumes the memory allocation of the container that wrote the data. If size-limit is not specified, the maximum size will be half the total memory limit of all containers. nfs: Represents a volume backed by an NFS server. Additional keys: * location: (required) The location of the NFS Server, in the form SERVER:/PATH * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. |
| `--clear-volumes` |  |  | _[values.]_ Remove all existing volumes from the Cloud Run resource, including volumes mounted as secrets |
| `--remove-volume` | [VOLUME,...] |  | _[values.]_ Removes volumes from the Cloud Run resource. |


**Examples:**
```bash
To update the container image of Cloud Run job my-job:

    $ gcloud run jobs update my-job \
      --image=us-docker.pkg.dev/project/image
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/update)

---

## `gcloud run jobs executions` — view and manage your Cloud Run jobs executions
### `gcloud run jobs executions cancel`

Cancel an execution

Cancel an execution.

**Synopsis:**
```
gcloud run jobs executions cancel EXECUTION [--[no-]async]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Execution resource - Execution to cancel. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument EXECUTION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the Execution or fully qualified identifier for the Execution.

     To set the executions attribute:
     + provide the argument EXECUTION on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]async` |  |  | Return immediately, without waiting for the operation in progress to complete. Defaults to --no-async. Use --async to enable and --no-async to disable. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To cancel an execution:

    $ gcloud run jobs executions cancel my-execution
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/executions/cancel)

---
### `gcloud run jobs executions delete`

Delete an execution

Delete an execution.

**Synopsis:**
```
gcloud run jobs executions delete EXECUTION [--[no-]async]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Execution resource - Execution to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument EXECUTION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the Execution or fully qualified identifier for the Execution.

     To set the executions attribute:
     + provide the argument EXECUTION on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]async` |  |  | Return immediately, without waiting for the operation in progress to complete. Defaults to --no-async. Use --async to enable and --no-async to disable. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To delete an execution:

    $ gcloud run jobs executions delete my-execution
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/executions/delete)

---
### `gcloud run jobs executions describe`

Obtain details about executions

Obtain details about executions.

**Synopsis:**
```
gcloud run jobs executions describe EXECUTION [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Execution resource - Execution to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument EXECUTION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the Execution or fully qualified identifier for the Execution.

     To set the executions attribute:
     + provide the argument EXECUTION on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To describe an execution:

    $ gcloud run jobs executions describe my-execution
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/executions/describe)

---
### `gcloud run jobs executions list`

List executions

List executions.

**Synopsis:**
```
gcloud run jobs executions list [--job=JOB] [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job` | JOB |  | Limit matched resources to the given job. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To list all executions in all regions:

    $ gcloud run jobs executions list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/executions/list)

---

## `gcloud run jobs executions tasks` — view and manage your Cloud Run jobs tasks
### `gcloud run jobs executions tasks describe`

Obtain details about tasks

Obtain details about tasks.

**Synopsis:**
```
gcloud run jobs executions tasks describe TASK [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - Task to describe. This represents a Cloud resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument TASK on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the Task or fully qualified identifier for the Task.

     To set the tasks attribute:
     + provide the argument TASK on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To describe a task:

    $ gcloud run jobs executions tasks describe my-task
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/executions/tasks/describe)

---
### `gcloud run jobs executions tasks list`

List tasks

List tasks.

**Synopsis:**
```
gcloud run jobs executions tasks list --execution=EXECUTION
    [--region=REGION] [--succeeded] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--execution` | EXECUTION |  | _[This must be specified.]_ ID of the Execution or fully qualified identifier for the Execution. To set the executions attribute: + provide the argument --execution on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--succeeded` |  |  | Include succeeded tasks. |


**Examples:**
```bash
To list all tasks for an execution:

    $ gcloud run jobs executions tasks list --execution=my-execution
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/executions/tasks/list)

---

## `gcloud run jobs logs` — read logs for Cloud Run jobs
### `gcloud run jobs logs read`

Read logs for Cloud Run jobs

gcloud run jobs logs read reads log entries. Log entries matching
--log-filter are returned according to the specified --order. If the log
entries come from multiple logs, then entries from different logs might be
intermingled in the results.

**Synopsis:**
```
gcloud run jobs logs read JOB [--freshness=FRESHNESS; default="1d"]
    [--log-filter=LOG_FILTER] [--order=ORDER; default="desc"]
    [--region=REGION] [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
JOB
   Name for a Cloud Run job.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--freshness` | FRESHNESS | 1d | Return entries that are not older than this value. Works only with DESC ordering and filters without a timestamp. See $ gcloud topic datetimes for information on duration formats. |
| `--log-filter` | LOG_FILTER |  | Filter expression that specifies the log entries to return. Detailed information about filters can be found at: https://cloud.google.com/logging/docs/view/logging-query-language |
| `--order` | one of: desc, asc | desc | Ordering of returned log entries based on timestamp field. ORDER must be one of: desc, asc. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To read log entries from for a Cloud Run job, run:

    $ gcloud run jobs logs read my-job

To read log entries with severity ERROR or higher, run:

    $ gcloud run jobs logs read my-job --log-filter="severity>=ERROR"

To read log entries written in a specific time window, run:

    $ gcloud run jobs logs read my-job \
        --log-filter='timestamp<="2015-05-31T23:59:59Z" AND
     timestamp>="2015-05-31T00:00:00Z"'

To read up to 10 log entries in your job payloads that include the word
SearchText and format the output in JSON format, run:

    $ gcloud run jobs logs read my-job \
        --log-filter="textPayload:SearchText" --limit=10 --format=json

Detailed information about filters can be found at:
https://cloud.google.com/logging/docs/view/advanced_filters
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/jobs/logs/read)

---
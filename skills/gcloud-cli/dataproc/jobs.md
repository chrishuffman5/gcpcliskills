# gcloud dataproc jobs

submit and manage Dataproc jobs

### `gcloud dataproc jobs delete`

Delete the record of an inactive job

Delete the record of an inactive job.

**Synopsis:**
```
gcloud dataproc jobs delete (JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To delete the record of a job, run:

    $ gcloud dataproc jobs delete job_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/delete)

---
### `gcloud dataproc jobs describe`

View the details of a job

View the details of a job.

**Synopsis:**
```
gcloud dataproc jobs describe (JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To view the details of a job, run:

    $ gcloud dataproc jobs describe job_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/describe)

---
### `gcloud dataproc jobs get-iam-policy`

Get IAM policy for a job

Gets the IAM policy for a job, given a job ID.

**Synopsis:**
```
gcloud dataproc jobs get-iam-policy (JOB : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to retrieve the policy for. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command prints the IAM policy for a job with the ID
example-job:

    $ gcloud dataproc jobs get-iam-policy example-job
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/get-iam-policy)

---
### `gcloud dataproc jobs kill`

Kill an active job

Kill an active job.

**Synopsis:**
```
gcloud dataproc jobs kill (JOB : --region=REGION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to kill. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately without waiting for the operation in progress to complete. |


**Examples:**
```bash
To cancel a job, run:

    $ gcloud dataproc jobs kill job_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/kill)

---
### `gcloud dataproc jobs list`

List jobs in a project

List jobs in a project. An optional filter can be used to constrain the
jobs returned. Filters are case-sensitive and have the following syntax:

    [field = value] AND [field [= value]] ...

where field is status.state or labels.[KEY], and [KEY] is a label key.
value can be * to match all values. status.state can be either ACTIVE or
INACTIVE. Only the logical AND operator is supported; space-separated items
are treated as having an implicit AND operator.

**Synopsis:**
```
gcloud dataproc jobs list [--cluster=CLUSTER] [--region=REGION]
    [--state-filter=STATE_FILTER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | Restrict to the jobs of this Dataproc cluster. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |
| `--state-filter` | one of: active, inactive |  | Filter by job state. STATE_FILTER must be one of: active, inactive. |


**Examples:**
```bash
To see the list of all jobs in Dataproc's 'us-central1' region, run:

    $ gcloud dataproc jobs list --region=us-central1

To see a list of all active jobs in cluster 'mycluster' with a label
env=staging located in 'us-central1', run:

    $ gcloud dataproc jobs list --region=us-central1 \
        --filter='status.state = ACTIVE AND
        placement.clusterName = 'mycluster' AND labels.env = staging'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/list)

---
### `gcloud dataproc jobs set-iam-policy`

Set IAM policy for a job

Sets the IAM policy for a job, given a job ID and the policy.

**Synopsis:**
```
gcloud dataproc jobs set-iam-policy (JOB : --region=REGION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to set the policy on. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy from 'policy.json' and set it
for a job with 'example-job' as the identifier:

    $ gcloud dataproc jobs set-iam-policy example-job policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/set-iam-policy)

---
### `gcloud dataproc jobs update`

Update the labels for a job

Update the labels for a job.

**Synopsis:**
```
gcloud dataproc jobs update (JOB : --region=REGION)
    (--update-labels=[KEY=VALUE,...] --clear-labels
      | --remove-labels=[KEY,...]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | _[At least one of these must be specified:]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To add the label 'customer=acme' to a job , run:

    $ gcloud dataproc jobs update job_id --update-labels=customer=acme

To update the label 'customer=ackme' to 'customer=acme', run:

    $ gcloud dataproc jobs update job_id --update-labels=customer=acme

To remove the label whose key is 'customer', run:

    $ gcloud dataproc jobs update job_id --remove-labels=customer
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/update)

---
### `gcloud dataproc jobs wait`

View the output of a job as it runs or after it completes

View the output of a job as it runs or after it completes.

**Synopsis:**
```
gcloud dataproc jobs wait (JOB : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The ID of the job to wait for. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

  --region=REGION
     Dataproc region for the job. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To see a list of all jobs, run:

    $ gcloud dataproc jobs list

To display these jobs with their respective IDs and underlying REST calls,
run:

    $ gcloud dataproc jobs list --format "table(reference.jobId)" \
        --limit 1 --log-http

To view the output of a job as it runs, run:

    $ gcloud dataproc jobs wait job_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/wait)

---

## `gcloud dataproc jobs submit` — submit Dataproc jobs to execute on a cluster
### `gcloud dataproc jobs submit flink`

Submit a Flink job to a cluster

Submit a Flink job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit flink (--class=MAIN_CLASS | --jar=MAIN_JAR)
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...]) [--async]
    [--bucket=BUCKET] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--jars=[JAR,...]]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [--savepoint=SAVEPOINT] [GCLOUD_WIDE_FLAG ...]
    [-- JOB_ARGS ...]
```

**Positional arguments:**
```
[-- JOB_ARGS ...]
   The job arguments to pass.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARGS on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--class` | MAIN_CLASS |  | _[Exactly one of these must be specified:]_ The class containing the main method of the driver. Must be in a provided jar or jar that is already on the classpath |
| `--jar` | MAIN_JAR |  | _[Exactly one of these must be specified:]_ The HCFS URI of jar file containing the driver jar. |
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO. |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--jars` | [JAR,...] |  | Comma-separated list of jar files to provide to the task manager classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key=value pairs to configure Flink. For a list of available properties, see: https://nightlies.apache.org/flink/flink-docs-master/docs/deployment/config/. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |
| `--savepoint` | SAVEPOINT |  | HCFS URI of the savepoint that is used to refer to the state of the previously stopped job. The new job will resume previous state from there. |


**Examples:**
```bash
To submit a Flink job that runs the main class of a jar, run:

    $ gcloud dataproc jobs submit flink --cluster=my-cluster \
        --region=us-central1 --jar=my_jar.jar -- arg1 arg2

To submit a Flink job that runs a specific class as an entrypoint:

    $ gcloud dataproc jobs submit flink --cluster=my-cluster \
        --region=us-central1 --class=org.my.main.Class \
        --jars=my_jar.jar -- arg1 arg2

To submit a Flink job that runs a jar that is on the cluster, run:

    $ gcloud dataproc jobs submit flink --cluster=my-cluster \
        --region=us-central1 \
        --jar=/usr/lib/flink/examples/streaming/TopSpeedWindowing.jar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/flink)

---
### `gcloud dataproc jobs submit hadoop`

Submit a Hadoop job to a cluster

Submit a Hadoop job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit hadoop (--class=MAIN_CLASS | --jar=MAIN_JAR)
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    [--archives=[ARCHIVE,...]] [--async] [--bucket=BUCKET]
    [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--files=[FILE,...]]
    [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...] [-- JOB_ARGS ...]
```

**Positional arguments:**
```
[-- JOB_ARGS ...]
   The arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARGS on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--class` | MAIN_CLASS |  | _[Exactly one of these must be specified:]_ The class containing the main method of the driver. Must be in a provided jar or jar that is already on the classpath |
| `--jar` | MAIN_JAR |  | _[Exactly one of these must be specified:]_ The HCFS URI of jar file containing the driver jar. |
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be provided to the job. must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--files` | [FILE,...] |  | Comma separated list of file paths to be provided to the job. A file path can either be a path to a local file or a path to a file already in a Cloud Storage bucket. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the MR and driver classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Hadoop. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Hadoop job that runs the main class of a jar, run:

    $ gcloud dataproc jobs submit hadoop --cluster=my-cluster \
        --jar=my_jar.jar -- arg1 arg2

To submit a Hadoop job that runs a specific class of a jar, run:

    $ gcloud dataproc jobs submit hadoop --cluster=my-cluster \
        --class=org.my.main.Class --jars=my_jar1.jar,my_jar2.jar \
        -- arg1 arg2

To submit a Hadoop job that runs a jar that is already on the cluster, run:

    $ gcloud dataproc jobs submit hadoop --cluster=my-cluster \
        --jar=file:///usr/lib/hadoop-op/hadoop-op-examples.jar \
        -- wordcount gs://my_bucket/my_file.txt gs://my_bucket/output
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/hadoop)

---
### `gcloud dataproc jobs submit hive`

Submit a Hive job to a cluster

Submit a Hive job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit hive
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE) [--async]
    [--bucket=BUCKET] [--continue-on-failure]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--jars=[JAR,...]]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL] [--params=[PARAM=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |
| `--execute` | QUERY, -e QUERY |  | _[Exactly one of these must be specified:]_ A Hive query to execute as part of the job. |
| `--file` | FILE, -f FILE |  | _[Exactly one of these must be specified:]_ HCFS URI of file containing Hive script to execute as the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--continue-on-failure` |  |  | Whether to continue if a single query fails. |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the Hive and MR. May contain UDFs. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--params` | [PARAM=VALUE,...] |  | A list of key value pairs to set variables in the Hive queries. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Hive. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Hive job with a local script, run:

    $ gcloud dataproc jobs submit hive --cluster=my-cluster \
        --file=my_queries.q

To submit a Hive job with inline queries, run:

    $ gcloud dataproc jobs submit hive --cluster=my-cluster \
        -e="CREATE EXTERNAL TABLE foo(bar int) LOCATION \
    'gs://my_bucket/'" -e="SELECT * FROM foo WHERE bar > 2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/hive)

---
### `gcloud dataproc jobs submit pig`

Submit a Pig job to a cluster

Submit a Pig job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit pig
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE) [--async]
    [--bucket=BUCKET] [--continue-on-failure]
    [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--jars=[JAR,...]]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL] [--params=[PARAM=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |
| `--execute` | QUERY, -e QUERY |  | _[Exactly one of these must be specified:]_ A Pig query to execute as part of the job. |
| `--file` | FILE, -f FILE |  | _[Exactly one of these must be specified:]_ HCFS URI of file containing Pig script to execute as the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--continue-on-failure` |  |  | Whether to continue if a single query fails. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to Pig and MR. May contain UDFs. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--params` | [PARAM=VALUE,...] |  | A list of key value pairs to set variables in the Pig queries. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Pig. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Pig job with a local script, run:

    $ gcloud dataproc jobs submit pig --cluster=my-cluster \
        --file=my_queries.pig

To submit a Pig job with inline queries, run:

    $ gcloud dataproc jobs submit pig --cluster=my-cluster \
        -e="LNS = LOAD 'gs://my_bucket/my_file.txt' AS (line)" \
        -e="WORDS = FOREACH LNS GENERATE FLATTEN(TOKENIZE(line)) AS \
    word" -e="GROUPS = GROUP WORDS BY word" \
        -e="WORD_COUNTS = FOREACH GROUPS GENERATE group, COUNT(WORDS)" \
        -e="DUMP WORD_COUNTS"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/pig)

---
### `gcloud dataproc jobs submit presto`

Submit a Presto job to a cluster

**Synopsis:**
```
gcloud dataproc jobs submit presto
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE) [--async]
    [--bucket=BUCKET] [--client-tags=[CLIENT_TAG,...]]
    [--continue-on-failure] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PARAM=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--query-output-format=QUERY_OUTPUT_FORMAT] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |
| `--execute` | QUERY, -e QUERY |  | _[Exactly one of these must be specified:]_ A Presto query to execute. |
| `--file` | FILE, -f FILE |  | _[Exactly one of these must be specified:]_ HCFS URI of file containing the Presto script to execute. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--client-tags` | [CLIENT_TAG,...] |  | A list of Presto client tags to attach to this query. |
| `--continue-on-failure` |  |  | Whether to continue if a query fails. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package-to-log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PARAM=VALUE,...] |  | A list of key value pairs to set Presto session properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--query-output-format` | QUERY_OUTPUT_FORMAT |  | The query output display format. See the Presto documentation for supported output formats. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Presto job with a local script, run:

    $ gcloud dataproc jobs submit presto --cluster=my-cluster \
        --file=my_script.R

To submit a Presto job with inline queries, run:

    $ gcloud dataproc jobs submit presto --cluster=my-cluster \
        -e="SELECT * FROM foo WHERE bar > 2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/presto)

---
### `gcloud dataproc jobs submit pyspark`

Submit a PySpark job to a cluster

Submit a PySpark job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit pyspark PY_FILE
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    [--archives=[ARCHIVE,...]] [--async] [--bucket=BUCKET]
    [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--files=[FILE,...]]
    [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--py-files=[PY_FILE,...]] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
    [-- JOB_ARGS ...]
```

**Positional arguments:**
```
PY_FILE
   Main .py file to run as the driver.

[-- JOB_ARGS ...]
   Arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARGS on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be extracted into the working directory of each executor. Must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of key value pairs to configure driver logging, where key is a package and value is the log4j log level. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--files` | [FILE,...] |  | Comma separated list of files to be placed in the working directory of both the app driver and executors. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the executor and driver classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key value pairs to configure PySpark. For a list of available properties, see: https://spark.apache.org/docs/latest/configuration.html#available-properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--py-files` | [PY_FILE,...] |  | Comma separated list of Python files to be provided to the job. Must be one of the following file formats ".py, .zip, or .egg". |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a PySpark job with a local script and custom flags, run:

    $ gcloud dataproc jobs submit pyspark --cluster=my-cluster \
        my_script.py -- --custom-flag

To submit a Spark job that runs a script that is already on the cluster,
run:

    $ gcloud dataproc jobs submit pyspark --cluster=my-cluster \
        file:///usr/lib/spark/examples/src/main/python/pi.py -- 100
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/pyspark)

---
### `gcloud dataproc jobs submit spark`

Submit a Spark job to a cluster

Submit a Spark job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit spark (--class=MAIN_CLASS | --jar=MAIN_JAR)
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    [--archives=[ARCHIVE,...]] [--async] [--bucket=BUCKET]
    [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--files=[FILE,...]]
    [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...] [-- JOB_ARGS ...]
```

**Positional arguments:**
```
[-- JOB_ARGS ...]
   Arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARGS on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--class` | MAIN_CLASS |  | _[Exactly one of these must be specified:]_ The class containing the main method of the driver. Must be in a provided jar or jar that is already on the classpath |
| `--jar` | MAIN_JAR |  | _[Exactly one of these must be specified:]_ The HCFS URI of jar file containing the driver jar. |
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be extracted into the working directory of each executor. Must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--files` | [FILE,...] |  | Comma separated list of files to be placed in the working directory of both the app driver and executors. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the executor and driver classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key value pairs to configure Spark. For a list of available properties, see: https://spark.apache.org/docs/latest/configuration.html#available-properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Spark job that runs the main class of a jar, run:

    $ gcloud dataproc jobs submit spark --cluster=my-cluster \
        --region=us-central1 --jar=my_jar.jar -- arg1 arg2

To submit a Spark job that runs a specific class of a jar, run:

    $ gcloud dataproc jobs submit spark --cluster=my-cluster \
        --region=us-central1 --class=org.my.main.Class \
        --jars=my_jar1.jar,my_jar2.jar -- arg1 arg2

To submit a Spark job that runs a jar that is already on the cluster, run:

    $ gcloud dataproc jobs submit spark --cluster=my-cluster \
        --region=us-central1 --class=org.apache.spark.examples.SparkPi \
        --jars=file:///usr/lib/spark/examples/jars/spark-examples.jar \
        -- 1000
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/spark)

---
### `gcloud dataproc jobs submit spark-r`

Submit a SparkR job to a cluster

Submit a SparkR job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit spark-r R_FILE
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    [--archives=[ARCHIVE,...]] [--async] [--bucket=BUCKET]
    [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--files=[FILE,...]]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...] [-- JOB_ARGS ...]
```

**Positional arguments:**
```
R_FILE
   Main .R file to run as the driver.

[-- JOB_ARGS ...]
   Arguments to pass to the driver.

   The '--' argument must be specified between gcloud specific args on the
   left and JOB_ARGS on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be extracted into the working directory of each executor. Must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of key value pairs to configure driver logging, where key is a package and value is the log4j log level. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--files` | [FILE,...] |  | Comma separated list of files to be placed in the working directory of both the app driver and executors. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key value pairs to configure SparkR. For a list of available properties, see: https://spark.apache.org/docs/latest/configuration.html#available-properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a SparkR job with a local script, run:

    $ gcloud dataproc jobs submit spark-r --cluster=my-cluster \
        my_script.R

To submit a Spark job that runs a script already on the cluster, run:

    $ gcloud dataproc jobs submit spark-r --cluster=my-cluster \
        file:///.../my_script.R -- gs://my_bucket/data.csv
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/spark-r)

---
### `gcloud dataproc jobs submit spark-sql`

Submit a Spark SQL job to a cluster

Submit a Spark SQL job to a cluster.

**Synopsis:**
```
gcloud dataproc jobs submit spark-sql
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE) [--async]
    [--bucket=BUCKET] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES] [--jars=[JAR,...]]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL] [--params=[PARAM=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |
| `--execute` | QUERY, -e QUERY |  | _[Exactly one of these must be specified:]_ A Spark SQL query to execute as part of the job. |
| `--file` | FILE, -f FILE |  | _[Exactly one of these must be specified:]_ HCFS URI of file containing Spark SQL script to execute as the job. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the executor and driver classpaths. May contain UDFs. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--params` | [PARAM=VALUE,...] |  | A list of key value pairs to set variables in the Hive queries. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Hive. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Spark SQL job with a local script, run:

    $ gcloud dataproc jobs submit spark-sql --cluster=my-cluster \
        --file=my_queries.ql

To submit a Spark SQL job with inline queries, run:

    $ gcloud dataproc jobs submit spark-sql --cluster=my-cluster \
        -e="CREATE EXTERNAL TABLE foo(bar int) LOCATION \
    'gs://my_bucket/'" -e="SELECT * FROM foo WHERE bar > 2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/spark-sql)

---
### `gcloud dataproc jobs submit trino`

Submit a Trino job to a cluster

**Synopsis:**
```
gcloud dataproc jobs submit trino
    (--cluster=CLUSTER | --cluster-labels=[KEY=VALUE,...])
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE) [--async]
    [--bucket=BUCKET] [--client-tags=[CLIENT_TAG,...]]
    [--continue-on-failure] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--driver-required-memory-mb=DRIVER_REQUIRED_MEMORY_MB]
    [--driver-required-vcores=DRIVER_REQUIRED_VCORES]
    [--labels=[KEY=VALUE,...]]
    [--max-failures-per-hour=MAX_FAILURES_PER_HOUR]
    [--max-failures-total=MAX_FAILURES_TOTAL]
    [--properties=[PARAM=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--query-output-format=QUERY_OUTPUT_FORMAT] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | _[Exactly one of these must be specified:]_ The Dataproc cluster to submit the job to. |
| `--cluster-labels` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Labels of Dataproc cluster on which to place the job. |
| `--execute` | QUERY, -e QUERY |  | _[Exactly one of these must be specified:]_ A Trino query to execute. |
| `--file` | FILE, -f FILE |  | _[Exactly one of these must be specified:]_ HCFS URI of file containing the Trino script to execute. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bucket` | BUCKET |  | The Cloud Storage bucket to stage files in. Defaults to the cluster's configured bucket. |
| `--client-tags` | [CLIENT_TAG,...] |  | A list of Trino client tags to attach to this query. |
| `--continue-on-failure` |  |  | Whether to continue if a query fails. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package-to-log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--driver-required-memory-mb` | DRIVER_REQUIRED_MEMORY_MB |  | The memory allocation requested by the job driver in megabytes (MB) for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--driver-required-vcores` | DRIVER_REQUIRED_VCORES |  | The vCPU allocation requested by the job driver for execution on the driver node group (it is used only by clusters with a driver node group). |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-failures-per-hour` | MAX_FAILURES_PER_HOUR |  | Specifies the maximum number of times a job can be restarted per hour in event of failure. Default is 0 (no retries after job failure). |
| `--max-failures-total` | MAX_FAILURES_TOTAL |  | Specifies the maximum total number of times a job can be restarted after the job fails. Default is 0 (no retries after job failure). |
| `--properties` | [PARAM=VALUE,...] |  | A list of key value pairs to set Trino session properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--query-output-format` | QUERY_OUTPUT_FORMAT |  | The query output display format. See the Trino documentation for supported output formats. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To submit a Trino job with a local script, run:

    $ gcloud dataproc jobs submit trino --cluster=my-cluster \
        --file=my_script.R

To submit a Trino job with inline queries, run:

    $ gcloud dataproc jobs submit trino --cluster=my-cluster \
        -e="SELECT * FROM foo WHERE bar > 2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/trino)

---
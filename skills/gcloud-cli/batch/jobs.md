# gcloud batch jobs

manage Batch job resources

### `gcloud batch jobs cancel`

Cancel a job

This command can fail for the following reasons:
  o The job specified does not exist.
  o The active account does not have permission to cancel the given job.

**Synopsis:**
```
gcloud batch jobs cancel (JOB : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The Batch job resource. If --location not specified,the
current batch/location is used. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument JOB on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the job.

     To set the location attribute:
     + provide the argument JOB on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property batch/location.
```

**Examples:**
```bash
To cancel the job with name projects/foo/locations/us-central1/jobs/bar,
run:

    $ gcloud batch jobs cancel \
        projects/foo/locations/us-central1/jobs/bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/jobs/cancel)

---
### `gcloud batch jobs delete`

Delete a job

This command can fail for the following reasons:
  o The job specified does not exist.
  o The active account does not have permission to delete the given job.

**Synopsis:**
```
gcloud batch jobs delete (JOB : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The Batch job resource. If --location not specified,the
current batch/location is used. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument JOB on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the job.

     To set the location attribute:
     + provide the argument JOB on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property batch/location.
```

**Examples:**
```bash
To delete the job with name projects/foo/locations/us-central1/jobs/bar,
run:

    $ gcloud batch jobs delete \
        projects/foo/locations/us-central1/jobs/bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/jobs/delete)

---
### `gcloud batch jobs describe`

Show details of a job

This command can fail for the following reasons:
  o The job specified does not exist.
  o The active account does not have permission to access the given job.

**Synopsis:**
```
gcloud batch jobs describe (JOB : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The Batch job resource. If --location not specified,the
current batch/location is used. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  JOB
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument JOB on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud location for the job.

     To set the location attribute:
     + provide the argument JOB on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property batch/location.
```

**Examples:**
```bash
To print details of the job with name
projects/foo/locations/us-central1/jobs/bar, run:

    $ gcloud batch jobs describe \
        projects/foo/locations/us-central1/jobs/bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/jobs/describe)

---
### `gcloud batch jobs list`

List jobs for a specified Batch project/location

This command can fail for the following reasons:
  o The project/location specified do not exist.
  o The active account does not have permission to access the given
    project/location.

**Synopsis:**
```
gcloud batch jobs list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property batch/location. |


**Examples:**
```bash
To print all the jobs under all available locations for the default
project, run:

    $ gcloud batch jobs list

To print all the jobs under projects/location
projects/foo/locations/us-central1, run:

    $ gcloud batch jobs list --project=foo --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/jobs/list)

---
### `gcloud batch jobs submit`

Submit a Batch job

This command creates and submits a Batch job. After you create and submit
the job, Batch automatically queues, schedules, and executes it.

**Synopsis:**
```
gcloud batch jobs submit [[JOB] --location=LOCATION]
    (--config=PATH_TO_FILE
      --container-commands-file=CONTAINER_COMMANDS_FILE
      --container-entrypoint=CONTAINER_ENTRYPOINT
      --container-image-uri=CONTAINER_IMAGE_URI
      | --script-file-path=SCRIPT_FILE_PATH | --script-text=SCRIPT_TEXT)
    [--job-prefix=JOB_PREFIX] [--machine-type=MACHINE_TYPE]
    [--priority=PRIORITY] [--provisioning-model=PROVISIONING_MODEL]
    [--network=NETWORK --subnetwork=SUBNETWORK : --no-external-ip-address]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Job resource - The Batch job resource. If --location not specified,the
current batch/location is used. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument JOB on the command line with a fully specified
   name;
 * job ID is optional and will be generated if not specified with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [JOB]
     ID of the job or fully qualified identifier for the job.

     To set the job attribute:
     + provide the argument JOB on the command line;
     + job ID is optional and will be generated if not specified.

  --location=LOCATION
     Google Cloud location for the job.

     To set the location attribute:
     + provide the argument JOB on the command line with a fully
       specified name;
     + job ID is optional and will be generated if not specified with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property batch/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | PATH_TO_FILE |  | _[At least one of these must be specified:]_ The file path of the job config file in either JSON or YAML format. It also supports direct input from stdin with '-' or HereDoc (in shells with HereDoc support like Bash) with '- <<DELIMITER'. Use a full or relative path to a local file containing the value of config. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job-prefix` | JOB_PREFIX |  | Specify the job prefix. A job ID in the format of job prefix + %Y%m%d-%H%M%S will be generated. Note that job prefix cannot be specified while JOB ID positional argument is specified. |
| `--machine-type` | MACHINE_TYPE |  | Specify the Compute Engine machine type, for example, e2-standard-4. Currently only one machine type is supported. |
| `--priority` | PRIORITY |  | Job priority [0-99] 0 is the lowest priority. |
| `--provisioning-model` | one of: SPOT The SPOT VM provisioning model |  | Specify the allowed provisioning model for the compute instances. PROVISIONING_MODEL must be one of: SPOT The SPOT VM provisioning model. Ideal for fault-tolerant workloads that can withstand preemption. STANDARD The STANDARD VM provisioning model |
| `--network` | NETWORK |  | The URL for the network resource. Must specify subnetwork as well if network is specified |
| `--subnetwork` | SUBNETWORK |  | The URL for the subnetwork resource. Must specify network as well if subnetwork is specified |
| `--no-external-ip-address` |  |  | Required if no external public IP address is attached to the VM. If no external public IP address, additional configuration is required to allow the VM to access Google Services. |


**Examples:**
```bash
To submit a job with a sample JSON configuration file (config.json) and
name projects/foo/locations/us-central1/jobs/bar, run:

    $ gcloud batch jobs submit \
        projects/foo/locations/us-central1/jobs/bar --config=config.json

To submit a job with a sample YAML configuration file (config.yaml) and
name projects/foo/locations/us-central1/jobs/bar, run:

    $ gcloud batch jobs submit \
        projects/foo/locations/us-central1/jobs/bar --config=config.yaml

To submit a job through stdin with a sample job configuration and name
projects/foo/locations/us-central1/jobs/bar, run:

    $ gcloud batch jobs submit \
        projects/foo/locations/us-central1/jobs/bar --config=-

    then input json job config via stdin
    {
      job config
    }

To submit a job through HereDoc with a sample job configuration and name
projects/foo/locations/us-central1/jobs/bar, run:

    $ gcloud batch jobs submit \
        projects/foo/locations/us-central1/jobs/bar --config=- << EOF

    {
      job config
    }
    EOF

For details about how to define a job's configuration using JSON, see the
projects.locations.jobs resource in the Batch API Reference. If you want to
define a job's configuration using YAML, convert the JSON syntax to YAML.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/jobs/submit)

---
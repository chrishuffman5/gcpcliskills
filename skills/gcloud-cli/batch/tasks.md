# gcloud batch tasks

manage Batch task resources

### `gcloud batch tasks describe`

Show details of a task

This command can fail for the following reasons:
  o The task specified does not exist.
  o The active account does not have permission to access the given task.

**Synopsis:**
```
gcloud batch tasks describe
    (TASK : --job=JOB --location=LOCATION --task_group=TASK_GROUP)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Task resource - The Batch task resource. If not specified,the current
batch/location is used. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument TASK on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TASK
     ID of the task or fully qualified identifier for the task.

     To set the task attribute:
     + provide the argument TASK on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --job=JOB
     The job ID for the task.

     To set the job attribute:
     + provide the argument TASK on the command line with a fully
       specified name;
     + provide the argument --job on the command line.

  --location=LOCATION
     Google Cloud location for the task.

     To set the location attribute:
     + provide the argument TASK on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property batch/location.

  --task_group=TASK_GROUP
     The task_group ID for the task.

     To set the task_group attribute:
     + provide the argument TASK on the command line with a fully
       specified name;
     + provide the argument --task_group on the command line.
```

**Examples:**
```bash
To print details of the task with name
projects/foo/locations/us-central1/jobs/bar/taskGroups/group0/tasks/0, run:

    $ gcloud batch tasks describe \
        projects/foo/locations/us-central1/jobs/bar/taskGroups/group0/\
    tasks/0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/tasks/describe)

---
### `gcloud batch tasks list`

List tasks for a specified Batch job

Currently, since Batch only supports one taskGroup, group0, the command
takes --job as the required argument and will list all tasks in group0 of
the job.

This command can fail for the following reasons:
  o The job specified does not exist.
  o The active account does not have permission to access the given job

**Synopsis:**
```
gcloud batch tasks list (--job=JOB : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--job` | JOB |  | _[This must be specified.]_ ID of the job or fully qualified identifier for the job. To set the job attribute: + provide the argument --job on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ Google Cloud location for the job. To set the location attribute: + provide the argument --job on the command line with a fully specified name; + provide the argument --location on the command line; + set the property batch/location. |


**Examples:**
```bash
To print all tasks in the job with name
projects/foo/locations/us-central1/jobs/bar, run:

    $ gcloud batch tasks list \
        --job projects/foo/locations/us-central1/jobs/bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/batch/tasks/list)

---
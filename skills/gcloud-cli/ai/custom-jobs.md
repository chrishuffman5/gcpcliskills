# gcloud ai custom-jobs

manage Vertex AI custom jobs

### `gcloud ai custom-jobs cancel`

Cancel a running custom job

If the job is already finished, the command will not perform any operation.

**Synopsis:**
```
gcloud ai custom-jobs cancel (CUSTOM_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Custom job resource - The custom job to cancel. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument custom_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CUSTOM_JOB
     ID of the custom job or fully qualified identifier for the custom
     job.

     To set the name attribute:
     + provide the argument custom_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the custom job.

     To set the region attribute:
     + provide the argument custom_job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To cancel a job 123 under project example in region us-central1, run:

    $ gcloud ai custom-jobs cancel 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/custom-jobs/cancel)

---
### `gcloud ai custom-jobs create`

Create a new custom job

This command will attempt to run the custom job immediately upon creation.

**Synopsis:**
```
gcloud ai custom-jobs create --display-name=DISPLAY_NAME
    (--config=CONFIG --worker-pool-spec=[WORKER_POOL_SPEC,...])
    [--args=[ARG,...]] [--command=[COMMAND,...]]
    [--enable-dashboard-access] [--enable-web-access]
    [--labels=[KEY=VALUE,...]] [--network=NETWORK]
    [--persistent-resource-id=PERSISTENT_RESOURCE_ID]
    [--python-package-uris=[PYTHON_PACKAGE_URIS,...]] [--region=REGION]
    [--service-account=SERVICE_ACCOUNT]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Display name of the custom job to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--args` | [ARG,...] |  | Comma-separated arguments passed to containers or python tasks. |
| `--command` | [COMMAND,...] |  | Command to be invoked when containers are started. It overrides the entrypoint instruction in Dockerfile when provided. |
| `--enable-dashboard-access` |  |  | Whether you want Vertex AI to enable dashboard built on the training containers. If set to true, you can access the dashboard at the URIs given by CustomJob.web_access_uris or Trial.web_access_uris (within HyperparameterTuningJob.trials). |
| `--enable-web-access` |  |  | Whether you want Vertex AI to enable interactive shell access (https://cloud.google.com/vertex-ai/docs/training/monitor-debug-interactive-shell) to training containers. If set to true, you can access interactive shells at the URIs given by CustomJob.web_access_uris or Trial.web_access_uris (within HyperparameterTuningJob.trials). |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--network` | NETWORK |  | Full name of the Google Compute Engine network to which the Job is peered with. Private services access must already have been configured. If unspecified, the Job is not peered with any network. |
| `--persistent-resource-id` | PERSISTENT_RESOURCE_ID |  | The name of the persistent resource from the same project and region on which to run this custom job. If this is specified, the job will be run on existing machines held by the PersistentResource instead of on-demand short-lived machines. The network and CMEK configs on the job should be consistent with those on the PersistentResource, otherwise, the job will be rejected. |
| `--python-package-uris` | [PYTHON_PACKAGE_URIS,...] |  | The common Python package URIs to be used for training with a pre-built container image. e.g. --python-package-uri=path1,path2 If you are using multiple worker pools and want to specify a different Python packag fo reach pool, use --config instead. |
| `--service-account` | SERVICE_ACCOUNT |  | _[+ choose one from the prompted list of available regions.]_ The email address of a service account to use when running the training appplication. You must have the iam.serviceAccounts.actAs permission for the specified service account. |


**Examples:**
```bash
To create a job under project example in region us-central1, run:

    $ gcloud ai custom-jobs create --region=us-central1 \
        --project=example \
        --worker-pool-spec=replica-count=1,machine-type='n1-highmem-2',\
    container-image-uri='gcr.io/ucaip-test/ucaip-training-test' \
        --display-name=test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/custom-jobs/create)

---
### `gcloud ai custom-jobs describe`

Get detailed information about the custom job by given id

**Synopsis:**
```
gcloud ai custom-jobs describe (CUSTOM_JOB : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Custom job resource - The custom job to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument custom_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CUSTOM_JOB
     ID of the custom job or fully qualified identifier for the custom
     job.

     To set the name attribute:
     + provide the argument custom_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the custom job.

     To set the region attribute:
     + provide the argument custom_job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Examples:**
```bash
To get a job 123 under project example in region us-central1, run:

    $ gcloud ai custom-jobs describe 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/custom-jobs/describe)

---
### `gcloud ai custom-jobs list`

Lists the existing custom jobs

**Synopsis:**
```
gcloud ai custom-jobs list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property ai/region; + choose one from the prompted list of available regions. |


**Examples:**
```bash
To list the jobs of project example in region us-central1, run:

    $ gcloud ai custom-jobs list --project=example --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/custom-jobs/list)

---
### `gcloud ai custom-jobs local-run`

Run a custom training locally

Packages your training code into a Docker image and executes it locally.

You should execute this command in the top folder which includes all the
code and resources you want to pack and run, or specify the 'work-dir' flag
to point to it. Any other path you specified via flags should be a relative
path to the work-dir and under it; otherwise it will be unaccessible.

Supposing your directories are like the following structures:

    /root
      - my_project
          - my_training
              - task.py
              - util.py
              - setup.py
          - other_modules
              - some_module.py
          - dataset
              - small.dat
              - large.dat
          - config
          - dep
              - foo.tar.gz
          - bar.whl
          - requirements.txt
      - another_project
          - something

If you set 'my_project' as the package, then you should execute the task.py
by specifying "--script=my_training/task.py" or
"--python-module=my_training.task", the 'requirements.txt' will be
processed. And you will also be able to install extra packages by, e.g.
specifying "--extra-packages=dep/foo.tar.gz,bar.whl" or include extra
directories, e.g. specifying "--extra-dirs=dataset,config".

If you set 'my_training' as the package, then you should execute the
task.py by specifying "--script=task.py" or "--python-module=task", the
'setup.py' will be processed. However, you won't be able to access any
other files or directories that are not in 'my_training' folder.

See more details in the HELP info of the corresponding flags.

**Synopsis:**
```
gcloud ai custom-jobs local-run --executor-image-uri=IMAGE_URI
    [--extra-dirs=[EXTRA_DIR,...]] [--extra-packages=[PACKAGE,...]] [--gpu]
    [--local-package-path=LOCAL_PATH] [--output-image-uri=OUTPUT_IMAGE]
    [--requirements=[REQUIREMENTS,...]]
    [--service-account-key-file=ACCOUNT_KEY_FILE]
    [--python-module=PYTHON_MODULE | --script=SCRIPT]
    [GCLOUD_WIDE_FLAG ...] [-- ARGS ...]
```

**Positional arguments:**
```
[-- ARGS ...]
   Additional user arguments to be forwarded to your application.

   The '--' argument must be specified between gcloud specific args on the
   left and ARGS on the right. Example:

       $ gcloud ai custom-jobs local-run --script=my_run.sh \
           --base-image=gcr.io/my/image -- --my-arg bar --enable_foo
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--executor-image-uri` | IMAGE_URI |  | URI or ID of the container image in either the Container Registry or local that will run the application. See https://cloud.google.com/vertex-ai/docs/training/pre-built-containers for available pre-built container images provided by Vertex AI for training. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--extra-dirs` | [EXTRA_DIR,...] |  | Extra directories under the working directory to include, besides the one that contains the main executable. By default, only the parent directory of the main script or python module is copied to the container. For example, if the module is "training.task" or the script is "training/task.py", the whole "training" directory, including its sub-directories, will always be copied to the container. You may specify this flag to also copy other directories if necessary. Note: if no parent is specified in 'python_module' or 'scirpt', the whole working directory is copied, then you don't need to specify this flag. |
| `--extra-packages` | [PACKAGE,...] |  | Local paths to Python archives used as training dependencies in the image container. These can be absolute or relative paths. However, they have to be under the work_dir; Otherwise, this tool will not be able to access it. Example: 'dep1.tar.gz, ./downloads/dep2.whl' |
| `--gpu` |  |  | Enable to use GPU. |
| `--local-package-path` | LOCAL_PATH |  | local path of the directory where the python-module or script exists. If not specified, it use the directory where you run the this command. Only the contents of this directory will be accessible to the built container image. |
| `--output-image-uri` | OUTPUT_IMAGE |  | Uri of the custom container image to be built with the your application packed in. |
| `--requirements` | [REQUIREMENTS,...] |  | Python dependencies from PyPI to be used when running the application. If this is not specified, and there is no "setup.py" or "requirements.txt" in the working directory, your application will only have access to what exists in the base image with on other dependencies. Example: 'tensorflow-cpu, pandas==1.2.0, matplotlib>=3.0.2' |
| `--service-account-key-file` | ACCOUNT_KEY_FILE |  | The JSON file of a Google Cloud service account private key. When specified, the corresponding service account will be used to authenticate the local container to access Google Cloud services. Note that the key file won't be copied to the container, it will be mounted during running time. |


**Examples:**
```bash
To execute an python module with required dependencies, run:

    $ gcloud ai custom-jobs local-run --python-module=my_training.task \
        --executor-image-uri=gcr.io/my/image \
        --requirements=pandas,scipy>=1.3.0

To execute a python script using local GPU, run:

    $ gcloud ai custom-jobs local-run --script=my_training/task.py \
        --executor-image-uri=gcr.io/my/image --gpu

To execute an arbitrary script with custom arguments, run:

    $ gcloud ai custom-jobs local-run --script=my_run.sh \
        --executor-image-uri=gcr.io/my/image -- --my-arg bar \
        --enable_foo

To run an existing container training without building new image, run:

    $ gcloud ai custom-jobs local-run \
        --executor-image-uri=gcr.io/my/custom-training-image
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/custom-jobs/local-run)

---
### `gcloud ai custom-jobs stream-logs`

Show stream logs from a running custom job

**Synopsis:**
```
gcloud ai custom-jobs stream-logs (CUSTOM_JOB : --region=REGION)
    [--allow-multiline-logs]
    [--polling-interval=POLLING_INTERVAL; default=60]
    [--task-name=TASK_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Custom job resource - The custom job to fetch stream log. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument custom_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CUSTOM_JOB
     ID of the custom job or fully qualified identifier for the custom
     job.

     To set the name attribute:
     + provide the argument custom_job on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the custom job.

     To set the region attribute:
     + provide the argument custom_job on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property ai/region;
     + choose one from the prompted list of available regions.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-multiline-logs` |  |  | Output multiline log messages as single records. |
| `--polling-interval` | POLLING_INTERVAL | 60 | Number of seconds to wait between efforts to fetch the latest log messages. |
| `--task-name` | TASK_NAME |  | If set, display only the logs for this particular task. |


**Examples:**
```bash
To stream logs of custom job 123 under project example in region
us-central1, run:

    $ gcloud ai custom-jobs stream-logs 123 --project=example \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai/custom-jobs/stream-logs)

---
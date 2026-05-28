# gcloud ai-platform local

AI Platform Local commands

### `gcloud ai-platform local predict`

Run prediction locally

gcloud ai-platform local predict performs prediction locally with the given
instances. It requires the TensorFlow SDK
(https://www.tensorflow.org/install) be installed locally. The output
format mirrors gcloud ai-platform predict (online prediction).

You cannot use this command with custom prediction routines.

**Synopsis:**
```
gcloud ai-platform local predict --model-dir=MODEL_DIR
    (--json-instances=JSON_INSTANCES | --json-request=JSON_REQUEST
      | --text-instances=TEXT_INSTANCES) [--framework=FRAMEWORK]
    [--signature-name=SIGNATURE_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--model-dir` | MODEL_DIR |  | Path to the model. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--framework` | one of: scikit-learn, tensorflow, xgboost |  | ML framework used to train this version of the model. If not specified, defaults to 'tensorflow'. FRAMEWORK must be one of: scikit-learn, tensorflow, xgboost. |
| `--signature-name` | SIGNATURE_NAME |  | Name of the signature defined in the SavedModel to use for this job. Defaults to DEFAULT_SERVING_SIGNATURE_DEF_KEY in https://www.tensorflow.org/api_docs/python/tf/compat/v1/saved_model/signature_constants, which is "serving_default". Only applies to TensorFlow models. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/local/predict)

---
### `gcloud ai-platform local train`

Run an AI Platform training job locally

This command runs the specified module in an environment similar to that of
a live AI Platform Training Job.

This is especially useful in the case of testing distributed models, as it
allows you to validate that you are properly interacting with the AI
Platform cluster configuration. If your model expects a specific number of
parameter servers or workers (i.e. you expect to use the CUSTOM machine
type), use the --parameter-server-count and --worker-count flags to further
specify the desired cluster configuration, just as you would in your cloud
training job configuration:

    $ gcloud ai-platform local train --module-name trainer.task \
            --package-path /path/to/my/code/trainer \
            --distributed \
            --parameter-server-count 4 \
            --worker-count 8

Unlike submitting a training job, the --package-path parameter can be
omitted, and will use your current working directory.

AI Platform Training sets a TF_CONFIG environment variable on each VM in
your training job. You can use TF_CONFIG to access the cluster description
and the task description for each VM.

Learn more about TF_CONFIG:
https://cloud.google.com/ai-platform/training/docs/distributed-training-details.

**Synopsis:**
```
gcloud ai-platform local train --module-name=MODULE_NAME [--distributed]
    [--evaluator-count=EVALUATOR_COUNT] [--job-dir=JOB_DIR]
    [--package-path=PACKAGE_PATH]
    [--parameter-server-count=PARAMETER_SERVER_COUNT]
    [--start-port=START_PORT; default=27182] [--worker-count=WORKER_COUNT]
    [GCLOUD_WIDE_FLAG ...] [-- USER_ARGS ...]
```

**Positional arguments:**
```
[-- USER_ARGS ...]
   Additional user arguments to be forwarded to user code. Any relative
   paths will be relative to the parent directory of --package-path.

   The '--' argument must be specified between gcloud specific args on the
   left and USER_ARGS on the right.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--module-name` | MODULE_NAME |  | Name of the module to run. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--distributed` |  |  | Runs the provided code in distributed mode by providing cluster configurations as environment variables to subprocesses |
| `--evaluator-count` | EVALUATOR_COUNT |  | Number of evaluators with which to run. Ignored if --distributed is not specified. Default: 0 |
| `--job-dir` | JOB_DIR |  | Cloud Storage path or local_directory in which to store training outputs and other data needed for training. This path will be passed to your TensorFlow program as the --job-dir command-line arg. The benefit of specifying this field is that AI Platform will validate the path for use in training. However, note that your training program will need to parse the provided --job-dir argument. |
| `--package-path` | PACKAGE_PATH |  | Path to a Python package to build. This should point to a local directory containing the Python source for the job. It will be built using setuptools (which must be installed) using its parent directory as context. If the parent directory contains a setup.py file, the build will use that; otherwise, it will use a simple built-in one. |
| `--parameter-server-count` | PARAMETER_SERVER_COUNT |  | Number of parameter servers with which to run. Ignored if --distributed is not specified. Default: 2 |
| `--start-port` | START_PORT | 27182 | Start of the range of ports reserved by the local cluster. This command will use a contiguous block of ports equal to parameter-server-count + worker-count + 1. If --distributed is not specified, this flag is ignored. |
| `--worker-count` | WORKER_COUNT |  | Number of workers with which to run. Ignored if --distributed is not specified. Default: 2 |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/ai-platform/local/train)

---
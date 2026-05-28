# gcloud workflows (top-level commands)

### `gcloud workflows delete`

Delete a workflow

Delete a workflow and all of its executions.

**Synopsis:**
```
gcloud workflows delete (WORKFLOW : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - The name of the workflow to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the workflow. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the workflow 'my-workflow', run:

    $ gcloud workflows delete my-workflow

You may also skip waiting for the operation to finish:

    $ gcloud workflows delete my-workflow --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/delete)

---
### `gcloud workflows deploy`

Create or update a workflow

Create or update a workflow.

**Synopsis:**
```
gcloud workflows deploy (WORKFLOW : --location=LOCATION) [--async]
    [--call-log-level=CALL_LOG_LEVEL; default="none"]
    [--description=DESCRIPTION]
    [--execution-history-level=EXECUTION_HISTORY_LEVEL; default="none"]
    [--labels=[KEY=VALUE,...]] [--service-account=SERVICE_ACCOUNT]
    [--source=SOURCE] [--tags=[KEY=VALUE,...]]
    [--clear-env-vars | --env-vars-file=FILE_PATH
      | --remove-env-vars=[KEY,...] | --set-env-vars=[KEY=VALUE,...]
      | --update-env-vars=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - Name of the workflow to deploy. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for the workflow. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--call-log-level` | one of: log-all-calls Log all calls to subworkflows or library functions and their results | none | Level of call logging to apply by default for the workflow. CALL_LOG_LEVEL must be one of: log-all-calls Log all calls to subworkflows or library functions and their results. log-errors-only Log when a call is stopped due to an exception. log-none Perform no call logging. none No logging level specified. |
| `--description` | DESCRIPTION |  | The description of the workflow to deploy. |
| `--execution-history-level` | one of: execution-history-basic Enable basic execution history | none | Level of execution history to apply for the workflow. EXECUTION_HISTORY_LEVEL must be one of: execution-history-basic Enable basic execution history. execution-history-detailed Enable detailed execution history, including expected iterations and in-scope variable values. none No execution history level specified. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--service-account` | SERVICE_ACCOUNT |  | The service account that should be used as the workflow identity. "projects/PROJECT_ID/serviceAccounts/" prefix may be skipped from the full resource name, in that case "projects/-/serviceAccounts/" is prepended to the service account ID. |
| `--source` | SOURCE |  | Location of a workflow source code to deploy. Required on first deployment. Location needs to be defined as a path to a local file with the source code. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as "<tag-key-namespaced-name>=<tag-value-short-name>". Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To deploy a workflow with source code myWorkflow.yaml on Workflows:

    $ gcloud workflows deploy my-workflow --source=myWorkflow.yaml

You may also skip waiting for the operation to finish:

    $ gcloud workflows deploy my-workflow --source=myWorkflow.yaml \
        --async

To specify a service account as the workflow identity:

    $ gcloud workflows deploy my-workflow --source=myWorkflow.yaml \
        --service-account=my-account@my-project.iam.gserviceaccount.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/deploy)

---
### `gcloud workflows describe`

Show metadata for a workflow

Display all metadata associated with a workflow of given name and
revisionID. If revisionID is not provided, the metadata for the latest
revision is retrieved.

**Synopsis:**
```
gcloud workflows describe (WORKFLOW : --location=LOCATION)
    [--revision-id=REVISION_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - The name of the workflow to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the workflow. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--revision-id` | REVISION_ID |  | The revision ID of the workflow to describe. |


**Examples:**
```bash
To describe the workflow 'my-workflow' at revision '000001-dc1', run:

    $ gcloud workflows describe my-workflow `--revision-id=000001-dc1`
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/describe)

---
### `gcloud workflows execute`

Execute a workflow

Execute a workflow.

**Synopsis:**
```
gcloud workflows execute (WORKFLOW : --location=LOCATION)
    [--call-log-level=CALL_LOG_LEVEL; default="none"] [--data=DATA]
    [--disable-concurrency-quota-overflow-buffering]
    [--execution-history-level=EXECUTION_HISTORY_LEVEL; default="none"]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - Name of the workflow to execute. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the workflow. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--call-log-level` | one of: log-all-calls Log all calls to subworkflows or library functions and their results | none | Level of call logging to apply during execution. CALL_LOG_LEVEL must be one of: log-all-calls Log all calls to subworkflows or library functions and their results. log-errors-only Log when a call is stopped due to an exception. log-none Perform no call logging. none No call logging level specified. |
| `--data` | DATA |  | JSON string with data that will be passed to the workflow as an argument. |
| `--disable-concurrency-quota-overflow-buffering` |  |  | If set, the execution will not be backlogged when the concurrency quota is exhausted. Backlogged executions start when the concurrency quota becomes available. |
| `--execution-history-level` | one of: execution-history-basic Enable basic execution history | none | Level of execution history to apply during execution. EXECUTION_HISTORY_LEVEL must be one of: execution-history-basic Enable basic execution history. execution-history-detailed Enable detailed execution history, including expected iterations and in-scope variable values. none No execution history level specified. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens, underscores, lowercase characters, and numbers. Values must contain only hyphens, underscores, lowercase characters, and numbers. |


**Examples:**
```bash
To execute a workflow named 'my-workflow' with the data that will be passed
to the workflow, run:

    $ gcloud workflows execute my-workflow --data=my-data
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/execute)

---
### `gcloud workflows list`

List workflows

List workflows under a project and location.

**Synopsis:**
```
gcloud workflows list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property workflows/location. |


**Examples:**
```bash
To list workflows, run:

    $ gcloud workflows list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/list)

---
### `gcloud workflows run`

Execute a workflow and wait for the execution to complete

Execute a workflow and wait for the execution to complete.

**Synopsis:**
```
gcloud workflows run (WORKFLOW : --location=LOCATION)
    [--call-log-level=CALL_LOG_LEVEL; default="none"] [--data=DATA]
    [--disable-concurrency-quota-overflow-buffering]
    [--execution-history-level=EXECUTION_HISTORY_LEVEL; default="none"]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - Name of the workflow to execute. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument workflow on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKFLOW
     ID of the workflow or fully qualified identifier for the workflow.

     To set the workflow attribute:
     + provide the argument workflow on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for the workflow. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument workflow on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--call-log-level` | one of: log-all-calls Log all calls to subworkflows or library functions and their results | none | Level of call logging to apply during execution. CALL_LOG_LEVEL must be one of: log-all-calls Log all calls to subworkflows or library functions and their results. log-errors-only Log when a call is stopped due to an exception. log-none Perform no call logging. none No logging level specified. |
| `--data` | DATA |  | JSON string with data that will be passed to the workflow as an argument. |
| `--disable-concurrency-quota-overflow-buffering` |  |  | If set, the execution will not be backlogged when the concurrency quota is exhausted. Backlogged executions start when the concurrency quota becomes available. |
| `--execution-history-level` | one of: execution-history-basic Enable execution history basic feature | none | Level of execution history to apply during execution. EXECUTION_HISTORY_LEVEL must be one of: execution-history-basic Enable execution history basic feature. execution-history-detailed Enable execution history detailed feature. none No execution history level specified. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To execute a workflow named my-workflow with the data that will be passed
to the workflow, run:

    $ gcloud workflows run my-workflow `--data=my-data`

To add two labels {foo: bar, baz: qux} to the execution, run:

    $ gcloud workflows run my-workflow `--data=my-data` \
        `--labels=foo=bar,baz=qux`
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/run)

---
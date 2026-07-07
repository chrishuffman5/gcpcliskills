# gcloud workflows executions

manage your Cloud Workflow execution resources

### `gcloud workflows executions cancel`

Cancel a workflow execution

Cancel a workflow execution.

**Synopsis:**
```
gcloud workflows executions cancel
    (EXECUTION : --location=LOCATION --workflow=WORKFLOW)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Execution resource - The name of the workflow execution to cancel. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument execution on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the execution or fully qualified identifier for the execution.

     To set the execution attribute:
     + provide the argument execution on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the execution. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.

  --workflow=WORKFLOW
     The Cloud Workflow for the execution.

     To set the workflow attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --workflow on the command line.
```

**Examples:**
```bash
To cancel an execution with ID 'my-workflow-execution-ID' from a workflow
named 'my-workflow', run:

    $ gcloud workflows executions cancel my-workflow-execution-ID \
      --workflow=my-workflow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions/cancel)

---
### `gcloud workflows executions describe`

Show metadata for a workflow execution

Display all metadata associated with a workflow execution of given ID.

**Synopsis:**
```
gcloud workflows executions describe
    (EXECUTION : --location=LOCATION --workflow=WORKFLOW)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Execution resource - The name of the workflow execution to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument execution on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the execution or fully qualified identifier for the execution.

     To set the execution attribute:
     + provide the argument execution on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the execution. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.

  --workflow=WORKFLOW
     The Cloud Workflow for the execution.

     To set the workflow attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --workflow on the command line.
```

**Examples:**
```bash
To describe an execution with ID 'my-workflow-execution-ID' from a workflow
named 'my-workflow', run:

    $ gcloud workflows executions describe my-workflow-execution-ID \
      --workflow=my-workflow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions/describe)

---
### `gcloud workflows executions describe-last`

Show metadata for the last cached workflow execution

Show metadata for the last cached workflow execution.

**Synopsis:**
```
gcloud workflows executions describe-last [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To show metadata for the last cached workflow execution, run:

    $ gcloud workflows executions describe-last
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions/describe-last)

---
### `gcloud workflows executions list`

List workflow executions

List workflow executions for a given workflow.

**Synopsis:**
```
gcloud workflows executions list (WORKFLOW : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workflow resource - The workflow name. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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

**Examples:**
```bash
To list executions of a workflow named 'my-workflow', run:

    $ gcloud workflows executions list my-workflow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions/list)

---
### `gcloud workflows executions wait`

Wait for an execution to complete

Wait for an execution to complete.

**Synopsis:**
```
gcloud workflows executions wait
    (EXECUTION : --location=LOCATION --workflow=WORKFLOW)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Execution resource - Name of the execution to wait on. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument execution on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  EXECUTION
     ID of the execution or fully qualified identifier for the execution.

     To set the execution attribute:
     + provide the argument execution on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Cloud location for the execution. Alternatively, set the property
     [workflows/location].

     To set the location attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property workflows/location.

  --workflow=WORKFLOW
     Workflow for the execution.

     To set the workflow attribute:
     + provide the argument execution on the command line with a fully
       specified name;
     + provide the argument --workflow on the command line.
```

**Examples:**
```bash
To wait for an execution with ID 'my-workflow-execution-ID' from a workflow
named 'my-workflow' to finish, run:

    $ gcloud workflows executions wait my-workflow-execution-ID \
        --workflow=my-workflow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions/wait)

---
### `gcloud workflows executions wait-last`

Wait for the last cached workflow execution to complete

Wait for the last cached workflow execution to complete.

**Synopsis:**
```
gcloud workflows executions wait-last [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To wait for the last cached workflow execution to complete, run:

    $ gcloud workflows executions wait-last
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/workflows/executions/wait-last)

---
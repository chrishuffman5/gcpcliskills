# gcloud dataproc workflow-templates

create and manage Dataproc workflow templates

### `gcloud dataproc workflow-templates create`

Create a workflow template

Create a workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates create (TEMPLATE : --region=REGION)
    [--dag-timeout=DAG_TIMEOUT] [--kms-key=KMS_KEY]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dag-timeout` | DAG_TIMEOUT |  | The duration for which a DAG of jobs can run before being auto-cancelled, such as "10m" or "16h". See $ gcloud topic datetimes for information on duration formats. |
| `--kms-key` | KMS_KEY |  | The KMS key used to encrypt sensitive data in the workflow template. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a workflow template named my-workflow-template in region
us-central1 with label params 'key1'='value1' and 'key2'='value2', run:

    $ gcloud dataproc workflow-templates create my-workflow-template \
        --region=us-central1 --labels="key1=value1,key2=value2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/create)

---
### `gcloud dataproc workflow-templates delete`

Delete a workflow template

Delete a workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates delete (TEMPLATE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To delete a workflow template 'my-workflow-template', run:

    $ gcloud dataproc workflow-templates delete my-workflow-template \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/delete)

---
### `gcloud dataproc workflow-templates describe`

Describe a workflow template

Describe a workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates describe (TEMPLATE : --region=REGION)
    [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--version` | VERSION |  | The version of the workflow template. |


**Examples:**
```bash
To describe a workflow template 'my-template' in region 'us-central1', run:

    $ gcloud dataproc workflow-templates describe workflow-template \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/describe)

---
### `gcloud dataproc workflow-templates export`

Export a workflow template

Exports a workflow template's configuration to a file. This configuration
can be imported at a later time.

**Synopsis:**
```
gcloud dataproc workflow-templates export (TEMPLATE : --region=REGION)
    [--destination=DESTINATION] [--version=VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |
| `--version` | VERSION |  | The version of the workflow template. |


**Examples:**
```bash
To export version 1.0 of workflow template for 'my-workflow-template' in
region 'us-central1' to template.yaml, run:

    $ gcloud dataproc workflow-templates export my-workflow-template \
        --region=us-central1 --destination=path/to/template.yaml \
        --version=1.0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/export)

---
### `gcloud dataproc workflow-templates get-iam-policy`

Get IAM policy for a workflow template

Gets the IAM policy for a workflow template, given a template ID.

**Synopsis:**
```
gcloud dataproc workflow-templates get-iam-policy
    (TEMPLATE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to retrieve the
policy for. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command prints the IAM policy for a workflow template with
the ID example-workflow:

    $ gcloud dataproc workflow-templates get-iam-policy example-workflow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/get-iam-policy)

---
### `gcloud dataproc workflow-templates import`

Import a workflow template

If the specified template resource already exists, it will be overwritten.
Otherwise, a new template will be created. To edit an existing template,
you can export the template to a file, edit its configuration, and then
import the new configuration.

**Synopsis:**
```
gcloud dataproc workflow-templates import (TEMPLATE : --region=REGION)
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/import)

---
### `gcloud dataproc workflow-templates instantiate`

Instantiate a workflow template

Instantiate a workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates instantiate (TEMPLATE : --region=REGION)
    [--async] [--parameters=[PARAM=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to run. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--parameters` | [PARAM=VALUE,...] |  | A map from parameter names to values that should be used for those parameters. A value must be provided for every configured parameter. Parameters can be configured when creating or updating a workflow template. |


**Examples:**
```bash
To instantiate a workflow template 'my-template' in region 'us-central1'
with parameter set 'param1'='value1' and 'param2'='value2', run:

    $ gcloud dataproc workflow-templates instantiate my-template \
        --region=us-central1 --parameters="param1=value1,param2=value2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/instantiate)

---
### `gcloud dataproc workflow-templates instantiate-from-file`

Instantiate a workflow template from a file

Instantiate a workflow template from a file.

**Synopsis:**
```
gcloud dataproc workflow-templates instantiate-from-file --file=FILE
    [--async] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | The YAML file containing the workflow template to run |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To instantiate a workflow template from a yaml file 'template.yaml' in
region 'us-central1', run:

    $ gcloud dataproc workflow-templates instantiate-from-file \
        --file=template.yaml --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/instantiate-from-file)

---
### `gcloud dataproc workflow-templates list`

List workflow templates

List workflow templates.

**Synopsis:**
```
gcloud dataproc workflow-templates list [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
To list all workflow-templates from region 'us-central1' run:

    $ gcloud dataproc workflow-templates list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/list)

---
### `gcloud dataproc workflow-templates remove-dag-timeout`

Remove DAG timeout from a workflow template

Remove DAG timeout from a workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates remove-dag-timeout
    (TEMPLATE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to remove the DAG
timeout from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To remove a DAG timeout from a workflow template named my-workflow-template
in region us-central1, run:

    $ gcloud dataproc workflow-templates remove-dag-timeout \
        my-workflow-template --region=us-central1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/remove-dag-timeout)

---
### `gcloud dataproc workflow-templates remove-job`

Remove a job from workflow template

Remove a job from workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates remove-job (TEMPLATE : --region=REGION)
    [--step-id=STEP_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to remove job. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template to remove. |


**Examples:**
```bash
To remove a job with step ID 'step-id' from a workflow template
'workflow-template' in region 'us-central1', run:

    $ gcloud dataproc workflow-templates remove-job workflow-template \
        --region=us-central1 --step-id=step-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/remove-job)

---
### `gcloud dataproc workflow-templates set-cluster-selector`

Set cluster selector for the workflow template

Set cluster selector for the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates set-cluster-selector
    (TEMPLATE : --region=REGION)
    [--cluster-labels=KEY=VALUE,[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to set cluster
selector. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster-labels` | KEY=VALUE,[KEY=VALUE,...] |  | A list of label KEY=VALUE pairs to add. |


**Examples:**
```bash
To set placement cluster selector labels on a workflow template, run:

    $ gcloud dataproc workflow-templates set-cluster-selector \
        my_template --region=us-central1 \
        --cluster-labels=environment=production
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/set-cluster-selector)

---
### `gcloud dataproc workflow-templates set-dag-timeout`

Set DAG timeout on a workflow template

Set DAG timeout on a workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates set-dag-timeout
    (TEMPLATE : --region=REGION) --dag-timeout=DAG_TIMEOUT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to set the DAG
timeout on. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dag-timeout` | DAG_TIMEOUT |  | The duration for which a DAG of jobs can run before being auto-cancelled, such as "10m" or "16h". See $ gcloud topic datetimes for information on duration formats. |


**Examples:**
```bash
To add a DAG timeout of 2h (or update an existing one to 2h) on a workflow
template named my-workflow-template in region us-central1, run:

    $ gcloud dataproc workflow-templates set-dag-timeout \
        my-workflow-template --region=us-central1 --dag-timeout=2h"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/set-dag-timeout)

---
### `gcloud dataproc workflow-templates set-iam-policy`

Set IAM policy for a template

Sets the IAM policy for a workflow template, given a template ID and the
policy.

**Synopsis:**
```
gcloud dataproc workflow-templates set-iam-policy
    (TEMPLATE : --region=REGION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to set the policy
on. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
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
for a template with 'example-template' as the identifier:

    $ gcloud dataproc workflow-templates set-iam-policy \
        example-template policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/set-iam-policy)

---
### `gcloud dataproc workflow-templates set-managed-cluster`

Set a managed cluster for the workflow template

Set a managed cluster for the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates set-managed-cluster
    (TEMPLATE : --region=REGION) [--autoscaling-policy=AUTOSCALING_POLICY]
    [--bucket=BUCKET] [--cluster-name=CLUSTER_NAME] [--cluster-type=TYPE]
    [--confidential-compute] [--dataproc-metastore=DATAPROC_METASTORE]
    [--enable-component-gateway]
    [--initialization-action-timeout=TIMEOUT; default="10m"]
    [--initialization-actions=CLOUD_STORAGE_URI,[...]]
    [--labels=[KEY=VALUE,...]]
    [--master-accelerator=[type=TYPE,[count=COUNT],...]]
    [--master-boot-disk-provisioned-iops=MASTER_BOOT_DISK_PROVISIONED_IOPS]
    [--master-boot-disk-provisioned-throughput=MASTER_BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--master-boot-disk-size=MASTER_BOOT_DISK_SIZE]
    [--master-boot-disk-type=MASTER_BOOT_DISK_TYPE]
    [--master-local-ssd-interface=MASTER_LOCAL_SSD_INTERFACE]
    [--master-machine-type=MASTER_MACHINE_TYPE]
    [--master-min-cpu-platform=PLATFORM]
    [--min-secondary-worker-fraction=MIN_SECONDARY_WORKER_FRACTION]
    [--node-group=NODE_GROUP]
    [--num-master-local-ssds=NUM_MASTER_LOCAL_SSDS]
    [--num-masters=NUM_MASTERS]
    [--num-secondary-worker-local-ssds=NUM_SECONDARY_WORKER_LOCAL_SSDS]
    [--num-worker-local-ssds=NUM_WORKER_LOCAL_SSDS]
    [--optional-components=[COMPONENT,...]]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--properties=[PREFIX:PROPERTY=VALUE,...]]
    [--secondary-worker-accelerator=[type=TYPE,[count=COUNT],...]]
    [--secondary-worker-boot-disk-size=SECONDARY_WORKER_BOOT_DISK_SIZE]
    [--secondary-worker-boot-disk-type=SECONDARY_WORKER_BOOT_DISK_TYPE]
    [--secondary-worker-local-ssd-interface=SECONDARY_WORKER_LOCAL_SSD_INTERFACE]
    [--secondary-worker-machine-types=type=MACHINE_TYPE[,
      type=MACHINE_TYPE...][,rank=RANK]]
    [--secondary-worker-standard-capacity-base=SECONDARY_WORKER_STANDARD_CAPACITY_BASE]
    [--secondary-worker-standard-capacity-percent-above-base=SECONDARY_WORKER_STANDARD_CAPACITY_PERCENT_ABOVE_BASE]
    [--shielded-integrity-monitoring] [--shielded-secure-boot]
    [--shielded-vtpm] [--temp-bucket=TEMP_BUCKET] [--tier=TIER]
    [--worker-accelerator=[type=TYPE,[count=COUNT],...]]
    [--worker-boot-disk-provisioned-iops=WORKER_BOOT_DISK_PROVISIONED_IOPS]
    [--worker-boot-disk-provisioned-throughput=WORKER_BOOT_DISK_PROVISIONED_THROUGHPUT]
    [--worker-boot-disk-size=WORKER_BOOT_DISK_SIZE]
    [--worker-boot-disk-type=WORKER_BOOT_DISK_TYPE]
    [--worker-local-ssd-interface=WORKER_LOCAL_SSD_INTERFACE]
    [--worker-min-cpu-platform=PLATFORM] [--zone=ZONE]
    [--identity-config-file=IDENTITY_CONFIG_FILE
      | --secure-multi-tenancy-user-mapping=SECURE_MULTI_TENANCY_USER_MAPPING]
    [--image=IMAGE | --image-version=VERSION]
    [--kerberos-config-file=KERBEROS_CONFIG_FILE | --enable-kerberos
      --kerberos-root-principal-password-uri=KERBEROS_ROOT_PRINCIPAL_PASSWORD_URI [--kerberos-kms-key=KERBEROS_KMS_KEY : --kerberos-kms-key-keyring=KERBEROS_KMS_KEY_KEYRING --kerberos-kms-key-location=KERBEROS_KMS_KEY_LOCATION --kerberos-kms-key-project=KERBEROS_KMS_KEY_PROJECT]]
    [--kms-key=KMS_KEY : --kms-keyring=KMS_KEYRING
      --kms-location=KMS_LOCATION --kms-project=KMS_PROJECT]
    [--metadata=KEY=VALUE,[KEY=VALUE,...]
      --resource-manager-tags=KEY=VALUE,[KEY=VALUE,...]
      --scopes=SCOPE,[SCOPE,...] --service-account=SERVICE_ACCOUNT
      --tags=TAG,[TAG,...] --network=NETWORK | --subnet=SUBNET
      --reservation=RESERVATION
      --reservation-affinity=RESERVATION_AFFINITY; default="any"]
    [[--metric-sources=[METRIC_SOURCE,...]
      : --metric-overrides=[METRIC_SOURCE:INSTANCE:GROUP:METRIC,...]
      | --metric-overrides-file=METRIC_OVERRIDES_FILE]]
    [--no-address | --public-ip-address]
    [--single-node | --min-num-workers=MIN_NUM_WORKERS
      --num-secondary-workers=NUM_SECONDARY_WORKERS
      --num-workers=NUM_WORKERS
      --secondary-worker-type=TYPE; default="preemptible"]
    [--worker-machine-type=WORKER_MACHINE_TYPE
      | --worker-machine-types=type=MACHINE_TYPE[,
      type=MACHINE_TYPE...][,rank=RANK]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The name of the workflow template to set managed
cluster. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the template. Each Dataproc region constitutes an
     independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--autoscaling-policy` | AUTOSCALING_POLICY |  | ID of the autoscaling policy or fully qualified identifier for the autoscaling policy. To set the autoscaling_policy attribute: * provide the argument --autoscaling-policy on the command line. |
| `--bucket` | BUCKET |  | The Google Cloud Storage bucket to use by default to stage job dependencies, miscellaneous config files, and job driver console output when using this cluster. |
| `--cluster-name` | CLUSTER_NAME |  | The name of the managed dataproc cluster. If unspecified, the workflow template ID will be used. |
| `--cluster-type` | one of: standard, single-node, zero-scale |  | The type of cluster. TYPE must be one of: standard, single-node, zero-scale. |
| `--confidential-compute` |  |  | Enables Confidential VM. See https://cloud.google.com/compute/confidential-vm/docs for more information. Note that Confidential VM can only be enabled when the machine types are N2D (https://cloud.google.com/compute/docs/machine-types#n2d_machine_types) and the image is SEV Compatible. |
| `--dataproc-metastore` | DATAPROC_METASTORE |  | Specify the name of a Dataproc Metastore service to be used as an external metastore in the format: "projects/{project-id}/locations/{region}/services/{service-name}". |
| `--enable-component-gateway` |  |  | Enable access to the web UIs of selected components on the cluster through the component gateway. |
| `--initialization-action-timeout` | TIMEOUT | 10m | The maximum duration of each initialization action. See $ gcloud topic datetimes for information on duration formats. |
| `--initialization-actions` | CLOUD_STORAGE_URI,[...] |  | A list of Google Cloud Storage URIs of executables to run on each node in the cluster. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--master-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the master instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--master-boot-disk-provisioned-iops` | MASTER_BOOT_DISK_PROVISIONED_IOPS |  | Indicates the IOPS (https://cloud.google.com/compute/docs/disks/hyperdisks#iops) to provision for the disk. This sets the limit for disk I/O operations per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--master-boot-disk-provisioned-throughput` | MASTER_BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates the throughput (https://cloud.google.com/compute/docs/disks/hyperdisks#throughput) to provision for the disk. This sets the limit for throughput in MiB per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--master-boot-disk-size` | MASTER_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum boot disk size is 10 GB. Boot disk size must be a multiple of 1 GB. |
| `--master-boot-disk-type` | MASTER_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--master-local-ssd-interface` | MASTER_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to master node(s) in a cluster. |
| `--master-machine-type` | MASTER_MACHINE_TYPE |  | The type of machine to use for the master. Defaults to server-specified. |
| `--master-min-cpu-platform` | PLATFORM |  | When specified, the VM is scheduled on the host with a specified CPU architecture or a more recent CPU platform that's available in that zone. To list available CPU platforms in a zone, run: $ gcloud compute zones describe ZONE CPU platform selection may not be available in a zone. Zones that support CPU platform selection provide an availableCpuPlatforms field, which contains the list of available CPU platforms in the zone (see Availability of CPU platforms for more information). |
| `--min-secondary-worker-fraction` | MIN_SECONDARY_WORKER_FRACTION |  | Minimum fraction of secondary worker nodes required to create the cluster. If it is not met, cluster creation will fail. Must be a decimal value between 0 and 1. The number of required secondary workers is calculated by ceil(min-secondary-worker-fraction * num_secondary_workers). Defaults to 0.0001. |
| `--node-group` | NODE_GROUP |  | The name of the sole-tenant node group to create the cluster on. Can be a short name ("node-group-name") or in the format "projects/{project-id}/zones/{zone}/nodeGroups/{node-group-name}". |
| `--num-master-local-ssds` | NUM_MASTER_LOCAL_SSDS |  | The number of local SSDs to attach to the master in a cluster. |
| `--num-masters` | NUM_MASTERS |  | The number of master nodes in the cluster. Number of Masters Cluster Mode 1 Standard 3 High Availability |
| `--num-secondary-worker-local-ssds` | NUM_SECONDARY_WORKER_LOCAL_SSDS |  | The number of local SSDs to attach to each preemptible worker in a cluster. |
| `--num-worker-local-ssds` | NUM_WORKER_LOCAL_SSDS |  | The number of local SSDs to attach to each worker in a cluster. |
| `--optional-components` | [COMPONENT,...] |  | List of optional components to be installed on cluster machines. The following page documents the optional components that can be installed: https://cloud.google.com/dataproc/docs/concepts/configuring-clusters/optional-components. |
| `--private-ipv6-google-access-type` | one of: inherit-subnetwork, outbound, bidirectional |  | The private IPv6 Google access type for the cluster. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: inherit-subnetwork, outbound, bidirectional. |
| `--properties` | [PREFIX:PROPERTY=VALUE,...] |  | Specifies configuration properties for installed packages, such as Hadoop and Spark. Properties are mapped to configuration files by specifying a prefix, such as "core:io.serializations". The following are supported prefixes and their mappings: Prefix File Purpose of file capacity-scheduler capacity-scheduler.xml Hadoop YARN Capacity Scheduler configuration core core-site.xml Hadoop general configuration distcp distcp-default.xml Hadoop Distributed Copy configuration hadoop-env hadoop-env.sh Hadoop specific environment variables hdfs hdfs-site.xml Hadoop HDFS configuration hive hive-site.xml Hive configuration mapred mapred-site.xml Hadoop MapReduce configuration mapred-env mapred-env.sh Hadoop MapReduce specific environment variables pig pig.properties Pig configuration spark spark-defaults.conf Spark configuration spark-env spark-env.sh Spark specific environment variables yarn yarn-site.xml Hadoop YARN configuration yarn-env yarn-env.sh Hadoop YARN specific environment variables See https://cloud.google.com/dataproc/docs/concepts/configuring-clusters/cluster-properties for more information. |
| `--secondary-worker-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the secondary-worker instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--secondary-worker-boot-disk-size` | SECONDARY_WORKER_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum boot disk size is 10 GB. Boot disk size must be a multiple of 1 GB. |
| `--secondary-worker-boot-disk-type` | SECONDARY_WORKER_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--secondary-worker-local-ssd-interface` | SECONDARY_WORKER_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to each secondary worker in a cluster. |
| `--secondary-worker-machine-types` | type=MACHINE_TYPE[,type=MACHINE_TYPE...][,rank=RANK] |  | Types of machines with optional rank for secondary workers to use. Defaults to server-specified.eg. --secondary-worker-machine-types="type=e2-standard-8,type=t2d-standard-8,rank=0" |
| `--secondary-worker-standard-capacity-base` | SECONDARY_WORKER_STANDARD_CAPACITY_BASE |  | This flag sets the base number of Standard VMs to use for secondary workers (https://cloud.google.com/dataproc/docs/concepts/compute/secondary-vms#preemptible_and_non-preemptible_secondary_workers). Dataproc will create only standard VMs until it reaches this number, then it will mix Spot and Standard VMs according to SECONDARY_WORKER_STANDARD_CAPACITY_PERCENT_ABOVE_BASE. |
| `--secondary-worker-standard-capacity-percent-above-base` | SECONDARY_WORKER_STANDARD_CAPACITY_PERCENT_ABOVE_BASE |  | When combining Standard and Spot VMs for secondary-workers (https://cloud.google.com/dataproc/docs/concepts/compute/secondary-vms#preemptible_and_non-preemptible_secondary_workers) once the number of Standard VMs specified by SECONDARY_WORKER_STANDARD_CAPACITY_BASE has been used, this flag specifies the percentage of the total number of additional Standard VMs secondary workers will use. Spot VMs will be used for the remaining percentage. |
| `--shielded-integrity-monitoring` |  |  | Enables monitoring and attestation of the boot integrity of the cluster's VMs. vTPM (virtual Trusted Platform Module) must also be enabled. A TPM is a hardware module that can be used for different security operations, such as remote attestation, encryption, and sealing of keys. |
| `--shielded-secure-boot` |  |  | The cluster's VMs will boot with secure boot enabled. |
| `--shielded-vtpm` |  |  | The cluster's VMs will boot with the TPM (Trusted Platform Module) enabled. A TPM is a hardware module that can be used for different security operations, such as remote attestation, encryption, and sealing of keys. |
| `--temp-bucket` | TEMP_BUCKET |  | The Google Cloud Storage bucket to use by default to store ephemeral cluster and jobs data, such as Spark and MapReduce history files. |
| `--tier` | one of: premium, standard |  | Cluster tier. TIER must be one of: premium, standard. |
| `--worker-accelerator` | [type=TYPE,[count=COUNT],...] |  | Attaches accelerators, such as GPUs, to the worker instance(s). type The specific type of accelerator to attach to the instances, such as nvidia-tesla-t4 for NVIDIA T4. Use gcloud compute accelerator-types list to display available accelerator types. count The number of accelerators to attach to each instance. The default value is 1. |
| `--worker-boot-disk-provisioned-iops` | WORKER_BOOT_DISK_PROVISIONED_IOPS |  | Indicates the IOPS (https://cloud.google.com/compute/docs/disks/hyperdisks#iops) to provision for the disk. This sets the limit for disk I/O operations per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--worker-boot-disk-provisioned-throughput` | WORKER_BOOT_DISK_PROVISIONED_THROUGHPUT |  | Indicates the throughput (https://cloud.google.com/compute/docs/disks/hyperdisks#throughput) to provision for the disk. This sets the limit for throughput in MiB per second. This is only supported if the bootdisk type is hyperdisk-balanced (https://cloud.google.com/compute/docs/disks/hyperdisks). |
| `--worker-boot-disk-size` | WORKER_BOOT_DISK_SIZE |  | The size of the boot disk. The value must be a whole number followed by a size unit of KB for kilobyte, MB for megabyte, GB for gigabyte, or TB for terabyte. For example, 10GB will produce a 10 gigabyte disk. The minimum boot disk size is 10 GB. Boot disk size must be a multiple of 1 GB. |
| `--worker-boot-disk-type` | WORKER_BOOT_DISK_TYPE |  | The type of the boot disk. The value must be pd-balanced, pd-ssd, or pd-standard. |
| `--worker-local-ssd-interface` | WORKER_LOCAL_SSD_INTERFACE |  | Interface to use to attach local SSDs to each worker in a cluster. |
| `--worker-min-cpu-platform` | PLATFORM |  | When specified, the VM is scheduled on the host with a specified CPU architecture or a more recent CPU platform that's available in that zone. To list available CPU platforms in a zone, run: $ gcloud compute zones describe ZONE CPU platform selection may not be available in a zone. Zones that support CPU platform selection provide an availableCpuPlatforms field, which contains the list of available CPU platforms in the zone (see Availability of CPU platforms for more information). |
| `--zone` | ZONE |  | The compute zone (e.g. us-central1-a) for the cluster. If empty and --region is set to a value other than global, the server will pick a zone in the region. Overrides the default compute/zone property value for this command invocation. |
| `--metric-sources` | one of: FLINK, HDFS, HIVEMETASTORE, HIVESERVER2, MONITORING_AGENT_DEFAULTS, SPARK, SPARK_HISTORY_SERVER, YARN |  | _[be one of: any, none, specific.]_ Specifies a list of cluster Metric Sources (https://cloud.google.com/dataproc/docs/guides/monitoring#available_oss_metrics) to collect custom metrics. METRIC_SOURCE must be one of: FLINK, HDFS, HIVEMETASTORE, HIVESERVER2, MONITORING_AGENT_DEFAULTS, SPARK, SPARK_HISTORY_SERVER, YARN. |


**Examples:**
```bash
To update managed cluster in a workflow template, run:

    $ gcloud dataproc workflow-templates set-managed-cluster \
        my_template --region=us-central1 --no-address --num-workers=10 \
        --worker-machine-type=custom-6-23040
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/set-managed-cluster)

---

## `gcloud dataproc workflow-templates add-job` — add Dataproc jobs to workflow template
### `gcloud dataproc workflow-templates add-job hadoop`

Add a hadoop job to the workflow template

Add a hadoop job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job hadoop --step-id=STEP_ID
    (--class=MAIN_CLASS | --jar=MAIN_JAR)
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--archives=[ARCHIVE,...]] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--files=[FILE,...]] [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
    [-- JOB_ARGS ...]
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
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be provided to the job. must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--files` | [FILE,...] |  | Comma separated list of file paths to be provided to the job. A file path can either be a path to a local file or a path to a file already in a Cloud Storage bucket. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the MR and driver classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Hadoop. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a Hadoop job executing 'my-jar' jar driver with 'my-class'
containing the main method to a the workflow template
'my-workflow-template' in region 'us-central1' with step-id 'my-step-id' ,
run:

    $ gcloud dataproc workflow-templates add-job hadoop \
        --step-id=my-step_id --class=my-class --jar=my-jar.jar \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/hadoop)

---
### `gcloud dataproc workflow-templates add-job hive`

Add a Hive job to the workflow template

Add a Hive job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job hive --step-id=STEP_ID
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE)
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--continue-on-failure] [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--params=[PARAM=VALUE,...]] [--properties=[PROPERTY=VALUE,...]]
    [--properties-file=PROPERTIES_FILE]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--continue-on-failure` |  |  | Whether to continue if a single query fails. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the Hive and MR. May contain UDFs. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--params` | [PARAM=VALUE,...] |  | A list of key value pairs to set variables in the Hive queries. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Hive. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a Hive job executing query 'QUERY' to a the workflow template
'my-workflow-template' in region 'us-central1' with step-id 'my-step-id' ,
run:

    $ gcloud dataproc workflow-templates add-job hive \
        --step-id=my-step_id -e=QUERY \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/hive)

---
### `gcloud dataproc workflow-templates add-job pig`

Add a Pig job to the workflow template

Add a Pig job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job pig --step-id=STEP_ID
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE)
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--continue-on-failure] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--params=[PARAM=VALUE,...]] [--properties=[PROPERTY=VALUE,...]]
    [--properties-file=PROPERTIES_FILE]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--continue-on-failure` |  |  | Whether to continue if a single query fails. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to Pig and MR. May contain UDFs. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--params` | [PARAM=VALUE,...] |  | A list of key value pairs to set variables in the Pig queries. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Pig. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a Pig job executing query 'QUERY' to a the workflow template
'my-workflow-template' in region 'us-central1' with step-id 'my-step-id' ,
run:

    $ gcloud dataproc workflow-templates add-job pig \
        --step-id=my-step_id -e=QUERY \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/pig)

---
### `gcloud dataproc workflow-templates add-job presto`

Add a Presto job to the workflow template

Add a Presto job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job presto --step-id=STEP_ID
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE)
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--client-tags=[CLIENT_TAG,...]] [--continue-on-failure]
    [--driver-log-levels=[PACKAGE=LEVEL,...]] [--labels=[KEY=VALUE,...]]
    [--properties=[PARAM=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--query-output-format=QUERY_OUTPUT_FORMAT]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--client-tags` | [CLIENT_TAG,...] |  | A list of Presto client tags to attach to this query. |
| `--continue-on-failure` |  |  | Whether to continue if a query fails. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package-to-log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--properties` | [PARAM=VALUE,...] |  | A list of key value pairs to set Presto session properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--query-output-format` | QUERY_OUTPUT_FORMAT |  | The query output display format. See the Presto documentation for supported output formats. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a Presto job that executes query 'QUERY' to a the workflow template
'my-workflow-template' in region 'us-central1' with step-id 'my-step-id',

run:

    $ gcloud dataproc workflow-templates add-job presto \
        --step-id=my-step_id -e=QUERY \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/presto)

---
### `gcloud dataproc workflow-templates add-job pyspark`

Add a PySpark job to the workflow template

Add a PySpark job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job pyspark PY_FILE
    --step-id=STEP_ID
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--archives=[ARCHIVE,...]] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--files=[FILE,...]] [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--py-files=[PY_FILE,...]] [--start-after=STEP_ID,[STEP_ID,...]]
    [GCLOUD_WIDE_FLAG ...] [-- JOB_ARGS ...]
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
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be extracted into the working directory of each executor. Must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of key value pairs to configure driver logging, where key is a package and value is the log4j log level. For example: root=FATAL,com.example=INFO |
| `--files` | [FILE,...] |  | Comma separated list of files to be placed in the working directory of both the app driver and executors. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the executor and driver classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key value pairs to configure PySpark. For a list of available properties, see: https://spark.apache.org/docs/latest/configuration.html#available-properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--py-files` | [PY_FILE,...] |  | Comma separated list of Python files to be provided to the job. Must be one of the following file formats ".py, .zip, or .egg". |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a PySpark job with archives 'archive1.tgz' and 'archive2.zip' to a
the workflow template 'my-workflow-template' in region 'us-central1' with
step-id 'my-step-id', run:

    $ gcloud dataproc workflow-templates add-job pyspark \
        --step-id=my-step_id --archives="archive1.tgz,archive2.zip" \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/pyspark)

---
### `gcloud dataproc workflow-templates add-job spark`

Add a Spark job to the workflow template

Add a Spark job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job spark --step-id=STEP_ID
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--archives=[ARCHIVE,...]] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--files=[FILE,...]] [--jars=[JAR,...]] [--labels=[KEY=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--start-after=STEP_ID,[STEP_ID,...]]
    [--class=MAIN_CLASS --jar=MAIN_JAR] [GCLOUD_WIDE_FLAG ...]
    [-- JOB_ARGS ...]
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
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be extracted into the working directory of each executor. Must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--files` | [FILE,...] |  | Comma separated list of files to be placed in the working directory of both the app driver and executors. |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the executor and driver classpaths. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key value pairs to configure Spark. For a list of available properties, see: https://spark.apache.org/docs/latest/configuration.html#available-properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |
| `--class` | MAIN_CLASS |  | The class containing the main method of the driver. Must be in a provided jar or jar that is already on the classpath |
| `--jar` | MAIN_JAR |  | The HCFS URI of jar file containing the driver jar. |


**Examples:**
```bash
To add a Spark job with files 'file1' and 'file2' to a the workflow
template 'my-workflow-template' in region 'us-central1' with step-id
'my-step-id' , run:

    $ gcloud dataproc workflow-templates add-job spark \
        --step-id=my-step_id --files="file1,file2" \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/spark)

---
### `gcloud dataproc workflow-templates add-job spark-r`

Add a SparkR job to the workflow template

Add a SparkR job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job spark-r R_FILE --step-id=STEP_ID
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--archives=[ARCHIVE,...]] [--driver-log-levels=[PACKAGE=LEVEL,...]]
    [--files=[FILE,...]] [--labels=[KEY=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
    [-- JOB_ARGS ...]
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
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--archives` | [ARCHIVE,...] |  | Comma separated list of archives to be extracted into the working directory of each executor. Must be one of the following file formats: .zip, .tar, .tar.gz, or .tgz. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | List of key value pairs to configure driver logging, where key is a package and value is the log4j log level. For example: root=FATAL,com.example=INFO |
| `--files` | [FILE,...] |  | Comma separated list of files to be placed in the working directory of both the app driver and executors. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--properties` | [PROPERTY=VALUE,...] |  | List of key value pairs to configure SparkR. For a list of available properties, see: https://spark.apache.org/docs/latest/configuration.html#available-properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a SparkR job executing file 'test.r' to a the workflow template
'my-workflow-template' in region 'us-central1' with step-id 'my-step-id' ,
run:

    $ gcloud dataproc workflow-templates add-job spark-r test.r \
        --step-id=my-step_id --workflow-template=my-workflow-template \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/spark-r)

---
### `gcloud dataproc workflow-templates add-job spark-sql`

Add a SparkSql job to the workflow template

Add a SparkSql job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job spark-sql --step-id=STEP_ID
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE)
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--driver-log-levels=[PACKAGE=LEVEL,...]] [--jars=[JAR,...]]
    [--labels=[KEY=VALUE,...]] [--params=[PARAM=VALUE,...]]
    [--properties=[PROPERTY=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package to log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--jars` | [JAR,...] |  | Comma separated list of jar files to be provided to the executor and driver classpaths. May contain UDFs. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--params` | [PARAM=VALUE,...] |  | A list of key value pairs to set variables in the Hive queries. |
| `--properties` | [PROPERTY=VALUE,...] |  | A list of key value pairs to configure Hive. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a SparkSql job executing query 'QUERY' to a the workflow template
'my-workflow-template' in region 'us-central1' with step-id 'my-step-id' ,
run:

    $ gcloud dataproc workflow-templates add-job spark-sql \
        --step-id=my-step_id -e=QUERY \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/spark-sql)

---
### `gcloud dataproc workflow-templates add-job trino`

Add a Trino job to the workflow template

Add a Trino job to the workflow template.

**Synopsis:**
```
gcloud dataproc workflow-templates add-job trino --step-id=STEP_ID
    (--execute=QUERY, -e QUERY | --file=FILE, -f FILE)
    (--workflow-template=WORKFLOW_TEMPLATE : --region=REGION)
    [--client-tags=[CLIENT_TAG,...]] [--continue-on-failure]
    [--driver-log-levels=[PACKAGE=LEVEL,...]] [--labels=[KEY=VALUE,...]]
    [--properties=[PARAM=VALUE,...]] [--properties-file=PROPERTIES_FILE]
    [--query-output-format=QUERY_OUTPUT_FORMAT]
    [--start-after=STEP_ID,[STEP_ID,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--step-id` | STEP_ID |  | The step ID of the job in the workflow template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--client-tags` | [CLIENT_TAG,...] |  | A list of Trino client tags to attach to this query. |
| `--continue-on-failure` |  |  | Whether to continue if a query fails. |
| `--driver-log-levels` | [PACKAGE=LEVEL,...] |  | A list of package-to-log4j log level pairs to configure driver logging. For example: root=FATAL,com.example=INFO |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--properties` | [PARAM=VALUE,...] |  | A list of key value pairs to set Trino session properties. |
| `--properties-file` | PROPERTIES_FILE |  | Path to a local file or a file in a Cloud Storage bucket containing configuration properties for the job. The client machine running this command must have read permission to the file. Specify properties in the form of property=value in the text file. For example: # Properties to set for the job: key1=value1 key2=value2 # Comment out properties not used. # key3=value3 If a property is set in both --properties and --properties-file, the value defined in --properties takes precedence. |
| `--query-output-format` | QUERY_OUTPUT_FORMAT |  | The query output display format. See the Trino documentation for supported output formats. |
| `--start-after` | STEP_ID,[STEP_ID,...] |  | (Optional) List of step IDs to start this job after. |


**Examples:**
```bash
To add a Trino job that executes 'QUERY' to the workflow template
'my-workflow-template' in the 'us-central1' region with 'my-step-id',

run:

    $ gcloud dataproc workflow-templates add-job trino \
        --step-id=my-step_id -e=QUERY \
        --workflow-template=my-workflow-template --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/workflow-templates/add-job/trino)

---
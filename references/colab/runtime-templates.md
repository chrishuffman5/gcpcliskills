# gcloud colab runtime-templates

manage Colab Enterprise runtime templates

### `gcloud colab runtime-templates add-iam-policy-binding`

Add an IAM policy binding to a Colab Enterprise runtime template

Add an IAM policy binding to a Colab Enterprise runtime template.

**Synopsis:**
```
gcloud colab runtime-templates add-iam-policy-binding
    (RUNTIME_TEMPLATE : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime template resource - Unique name of the runtime template to add IAM
policy binding to. This was optionally provided by setting
--runtime-template-id in the create runtime-template command, or was
system-generated if unspecified. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_TEMPLATE
     ID of the runtime template or fully qualified identifier for the
     runtime template.

     To set the name attribute:
     + provide the argument runtime_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime template.

     To set the region attribute:
     + provide the argument runtime_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To set someone@example.com to have the roles/aiplatform.notebookRuntimeUser
role for a runtime template with id my-runtime-template in region
us-central1, run:

    $ gcloud colab runtime-templates add-iam-policy-binding \
        my-runtime-template --region=us-central1 \
        --member=user:someone@example.com \
        --role=roles/aiplatform.notebookRuntimeUser
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/add-iam-policy-binding)

---
### `gcloud colab runtime-templates create`

Create a runtime template

Create a Colab Enterprise runtime template, a VM configuration for your
notebook runtimes.

**Synopsis:**
```
gcloud colab runtime-templates create --display-name=DISPLAY_NAME [--async]
    [--region=REGION] [--runtime-template-id=RUNTIME_TEMPLATE_ID]
    [--description=DESCRIPTION --no-enable-euc --enable-secure-boot
      --idle-shutdown-timeout=IDLE_SHUTDOWN_TIMEOUT; default="3h"
      --labels=[KEY=VALUE,...] --network-tags=[TAGS,...]
      --accelerator-count=ACCELERATOR_COUNT
      --accelerator-type=ACCELERATOR_TYPE --machine-type=MACHINE_TYPE;
      default="e2-standard-4" --disk-size-gb=DISK_SIZE_GB; default=100
      --disk-type=DISK_TYPE; default="PD_STANDARD" [--kms-key=KMS_KEY
      : --kms-keyring=KMS_KEYRING --kms-location=KMS_LOCATION
      --kms-project=KMS_PROJECT] --no-enable-internet-access
      --network=NETWORK [--subnetwork=SUBNETWORK
      : --subnetwork-region=SUBNETWORK_REGION]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name of the runtime template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--runtime-template-id` | RUNTIME_TEMPLATE_ID |  | _[+ set the property colab/region.]_ The id of the runtime template. If not specified, a random id will be generated. |


**Examples:**
```bash
To create a runtime template in region 'us-central1' with the display name
'my-runtime-template', run:

    $ gcloud colab runtime-templates create --region=us-central1 \
        --display-name=my-runtime-template

To create a runtime template for a VM with machine type n1-standard-2 and
one NVIDIA_TESLA_V100 accelerator, run:

    $ gcloud colab runtime-templates create \
        --machine-type=n1-standard-2 \
        --accelerator-type=NVIDIA_TESLA_V100 --accelerator-count=1 \
        --region=us-central1 --display-name=my-runtime-template

To create a runtime template that disables end user credential access, run:

    $ gcloud colab runtime-templates create --no-enable-euc \
        --region=us-central1 --display-name=my-runtime-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/create)

---
### `gcloud colab runtime-templates delete`

Delete a runtime template

Delete a Colab Enterprise notebook runtime template.

**Synopsis:**
```
gcloud colab runtime-templates delete (RUNTIME_TEMPLATE : --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime template resource - Unique name of the runtime template to delete.
This was optionally provided by setting --runtime-template-id in the
create runtime-template command, or was system-generated if unspecified.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument runtime_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_TEMPLATE
     ID of the runtime template or fully qualified identifier for the
     runtime template.

     To set the name attribute:
     + provide the argument runtime_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime template.

     To set the region attribute:
     + provide the argument runtime_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a runtime template with id 'my-runtime-template' in region
'us-central1', run:

    $ gcloud colab runtime-templates delete my-runtime-template \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/delete)

---
### `gcloud colab runtime-templates describe`

Describe a runtime template

Describe a Colab Enterprise notebook runtime template.

**Synopsis:**
```
gcloud colab runtime-templates describe
    (RUNTIME_TEMPLATE : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime template resource - Unique name of the runtime template to
describe. This was optionally provided by setting --runtime-template-id in
the create runtime-template command, or was system-generated if
unspecified. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_TEMPLATE
     ID of the runtime template or fully qualified identifier for the
     runtime template.

     To set the name attribute:
     + provide the argument runtime_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime template.

     To set the region attribute:
     + provide the argument runtime_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Examples:**
```bash
To describe a runtime template with id 'my-runtime-template' in region
'us-central1', run:

    $ gcloud colab runtime-templates describe my-runtime-template \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/describe)

---
### `gcloud colab runtime-templates get-iam-policy`

Get IAM policy for a Colab Enterprise runtime template

Get the IAM policy for a Colab Enterprise runtime template.

**Synopsis:**
```
gcloud colab runtime-templates get-iam-policy
    (RUNTIME_TEMPLATE : --region=REGION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime template resource - Unique name of the runtime template to get IAM
policy for. This was optionally provided by setting --runtime-template-id
in the create runtime-template command, or was system-generated if
unspecified. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_TEMPLATE
     ID of the runtime template or fully qualified identifier for the
     runtime template.

     To set the name attribute:
     + provide the argument runtime_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime template.

     To set the region attribute:
     + provide the argument runtime_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Examples:**
```bash
To get the IAM policy for a runtime template with id my-runtime-template in
region us-central1, run:

    $ gcloud colab runtime-templates get-iam-policy \
        my-runtime-template --location=us-central1 \
        --member=user:someone@example.com \
        --role=roles/aiplatform.notebookRuntimeUser
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/get-iam-policy)

---
### `gcloud colab runtime-templates list`

List your runtime templates

List your project's Colab Enterprise notebook runtime templates in a given
region.

**Synopsis:**
```
gcloud colab runtime-templates list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line; + set the property colab/region. |


**Examples:**
```bash
To list your runtime templates in region 'us-central1', run:

    $ gcloud colab runtime-templates list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/list)

---
### `gcloud colab runtime-templates remove-iam-policy-binding`

Remove an IAM policy binding from a Colab Enterprise runtime template

Remove an IAM policy binding from a Colab Enterprise runtime template.

**Synopsis:**
```
gcloud colab runtime-templates remove-iam-policy-binding
    (RUNTIME_TEMPLATE : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime template resource - Unique name of the runtime template to remove
IAM policy from. This was optionally provided by setting
--runtime-template-id in the create runtime-template command, or was
system-generated if unspecified. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_TEMPLATE
     ID of the runtime template or fully qualified identifier for the
     runtime template.

     To set the name attribute:
     + provide the argument runtime_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime template.

     To set the region attribute:
     + provide the argument runtime_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding of roles/aiplatform.notebookRuntimeUser for
someone@example.com, from the runtime template with id my-runtime-template
in region us-central1, run:

    $ gcloud colab runtime-templates remove-iam-policy-binding \
        my-runtime-template --region=us-central1 \
        --member=user:someone@example.com \
        --role=roles/aiplatform.notebookRuntimeUser
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/remove-iam-policy-binding)

---
### `gcloud colab runtime-templates set-iam-policy`

Set IAM policy for a Colab Enterprise runtime template as defined in a JSON or YAML file

Set the IAM policy for a Colab Enterprise runtime template as defined in a
JSON or YAML file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud colab runtime-templates set-iam-policy
    (RUNTIME_TEMPLATE : --region=REGION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Runtime template resource - Unique name of the runtime template to set IAM
policy for. This was optionally provided by setting --runtime-template-id
in the create runtime-template command, or was system-generated if
unspecified. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument runtime_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RUNTIME_TEMPLATE
     ID of the runtime template or fully qualified identifier for the
     runtime template.

     To set the name attribute:
     + provide the argument runtime_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Cloud region for the runtime template.

     To set the region attribute:
     + provide the argument runtime_template on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property colab/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the IAM policy for a runtime template with id my-runtime-template in
region us-central1 to the policy defined in policy.json, run:

    $ gcloud colab runtime-templates set-iam-policy \
        my-runtime-template policy.json --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/colab/runtime-templates/set-iam-policy)

---
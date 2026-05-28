# gcloud compute os-config

manage OS Config tasks for Compute Engine VM instances

### `gcloud compute os-config troubleshoot`

Troubleshoot issues with the setup of VM Manager on a specified VM instance

gcloud compute os-config troubleshoot troubleshoots issues with the setup
of VM Manager on a specified VM instance

The troubleshoot command investigates the following settings or
configurations for your VM Manager setup:

  o Checks if the OS Config API is enabled in the project.
  o Checks if the required metadata is set up correctly in the VM
    instance.
  o Checks if the latest version of the OS Config agent is running on the
    VM instance.
  o Checks if a service account is attached to the VM instance.
  o Checks if the VM Manager service agent is enabled.
  o Checks if the VM instance has a public IP or Private Google Access.

**Synopsis:**
```
gcloud compute os-config troubleshoot INSTANCE_NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To troubleshoot an instance named my-instance in zone us-west1-a, run

    $ gcloud compute os-config troubleshoot my-instance --zone=us-west1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/troubleshoot)

---

## `gcloud compute os-config inventories` — display inventory of a Compute Engine VM
### `gcloud compute os-config inventories describe`

Describe the inventory data for a Compute Engine VM instance

Describe the inventory data for a Compute Engine VM instance.

**Synopsis:**
```
gcloud compute os-config inventories describe INSTANCE
    [--location=LOCATION] [--view=VIEW] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   ID or name of the Compute Engine VM instance to describe. For details
   on valid instance IDs, refer to the criteria documented under the field
   id at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Compute Engine VM instance to describe. If not specified, the property compute/zone is used. For details on setting properties, see: https://cloud.google.com/sdk/docs/properties |
| `--view` | one of: basic Output is limited to operating system details |  | Specifies what information should be included in the output. If unspecified, the default view is basic. VIEW must be one of: basic Output is limited to operating system details. full Output includes operating system details and package information. |


**Examples:**
```bash
To describe the inventory of an instance my-instance that has the instance
ID 5678 in the current project and location 'us-central1-a', run:

    $ gcloud compute os-config inventories describe my-instance \
        --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/inventories/describe)

---
### `gcloud compute os-config inventories list`

List inventory data for all Compute Engine VM instances in a specified location

List inventory data for all Compute Engine VM instances in a specified
location.

The default page size is 25. To modify this, use the --page-size flag.

**Synopsis:**
```
gcloud compute os-config inventories list [--location=LOCATION]
    [--view=VIEW] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Compute Engine VM instances to list. If not specified, the property compute/zone is used. For details on setting properties, see: https://cloud.google.com/sdk/docs/properties |
| `--view` | one of: basic Output is limited to operating system details |  | Specifies what information should be included in the output. If unspecified, the default view is basic. VIEW must be one of: basic Output is limited to operating system details. full Output includes operating system details and package information. |


**Examples:**
```bash
To list the inventory of VMs in my-project and location us-central1-a, run:

    $ gcloud compute os-config inventories list --project=my-project \
        --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/inventories/list)

---

## `gcloud compute os-config os-policy-assignment-reports` — manage OS policy asssignment reports
### `gcloud compute os-config os-policy-assignment-reports describe`

Describe an OS policy assignment report

**Synopsis:**
```
gcloud compute os-config os-policy-assignment-reports describe
    (INSTANCE_OS_POLICY_ASSIGNMENT
      : --instance=INSTANCE --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment resource - OS policy assignment report. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument instance_os_policy_assignment on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INSTANCE_OS_POLICY_ASSIGNMENT
     ID of the OS policy assignment or fully qualified identifier for the
     OS policy assignment.

     To set the instance_os_policy_assignment attribute:
     + provide the argument instance_os_policy_assignment on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Compute Engine VM instance.

     To set the instance attribute:
     + provide the argument instance_os_policy_assignment on the command
       line with a fully specified name;
     + provide the argument --instance on the command line.

  --location=LOCATION
     Location of the OS policy assignment.

     To set the location attribute:
     + provide the argument instance_os_policy_assignment on the command
       line with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe the report of an OS policy assignment my-assignment for an
instance my-instance in location us-central1-a:

    $ gcloud compute os-config os-policy-assignment-reports describe \
        my-assignment --instance=my-instance --location=us-central1-a

Or use the relative names or URI of the resource, assuming the project ID
is my-project:

    $ gcloud compute os-config os-policy-assignment-reports describe \
        projects/my-project/locations/us-central1-a/instances/\
    my-instance/osPolicyAssignments/my-assignment/report

    $ gcloud compute os-config os-policy-assignment-reports describe \
        https://osconfig.googleapis.com/v1alpha/projects/my-project/\
    locations/us-central1-a/instances/instance-name/\
    osPolicyAssignments/assignment-id/report
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignment-reports/describe)

---
### `gcloud compute os-config os-policy-assignment-reports list`

List OS policy assignment reports

List OS policy assignment reports.

**Synopsis:**
```
gcloud compute os-config os-policy-assignment-reports list
    [--location=LOCATION]
    [--assignment-id=ASSIGNMENT_ID | --instance=INSTANCE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the OS policy assignment reports to list, will default to the user's compute/zone property if not specified. |


**Examples:**
```bash
To list reports OS policy assignment in location us-central1-a:

    $ gcloud compute os-config os-policy-assignment-reports list \
        --location=us-central1-a

To list reports of an instance my-instance in location us-central1-a:

    $ gcloud compute os-config os-policy-assignment-reports list \
        --location=us-central1-a --instance=my-instance

To list reports of an OS policy assignment my-assignment in location
us-central1-a:

    $ gcloud compute os-config os-policy-assignment-reports list \
        --location=us-central1-a --assignment-id=my-assignment
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignment-reports/list)

---

## `gcloud compute os-config os-policy-assignments` — manage OS policy assignments
### `gcloud compute os-config os-policy-assignments create`

Create an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments create
    (OS_POLICY_ASSIGNMENT : --location=LOCATION) --file=FILE [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment resource - Location to create the OS policy
assignment in. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument os_policy_assignment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OS_POLICY_ASSIGNMENT
     ID of the OS policy assignment or fully qualified identifier for the
     OS policy assignment.

     To set the os_policy_assignment attribute:
     + provide the argument os_policy_assignment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment.

     To set the location attribute:
     + provide the argument os_policy_assignment on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | Absolute path to the OS policy assignment file on your local client. File must be in either JSON or YAML format. This file defines the OS policies that you want to apply to your VMs, the target VMs that you want to apply the policies to, and the rollout rate at which to apply the OS policies. For more information about this resource and sample OS policy assignment files, see https://cloud.google.com/compute/docs/os-configuration-management/working-with-os-policies#os-policy-assignment. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create an OS policy assignment my-assignment in my-project and location
us-central1-a with config file /path/to/file/config.yaml, run:

    $ gcloud compute os-config os-policy-assignments create \
        my-assignment --project=my-project --location=us-central1-a \
        --file=/path/to/file/config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/create)

---
### `gcloud compute os-config os-policy-assignments delete`

Delete an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments delete
    (OS_POLICY_ASSIGNMENT : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment resource - OS policy assignment to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument os_policy_assignment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OS_POLICY_ASSIGNMENT
     ID of the OS policy assignment or fully qualified identifier for the
     OS policy assignment.

     To set the os_policy_assignment attribute:
     + provide the argument os_policy_assignment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment.

     To set the location attribute:
     + provide the argument os_policy_assignment on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an OS policy my-assignment in location us-central1-a:

    $ gcloud compute os-config os-policy-assignments delete \
        my-assignment --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/delete)

---
### `gcloud compute os-config os-policy-assignments describe`

Describe an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments describe
    (OS_POLICY_ASSIGNMENT : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment resource - OS policy assignment to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument os_policy_assignment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OS_POLICY_ASSIGNMENT
     ID of the OS policy assignment or fully qualified identifier for the
     OS policy assignment.

     To set the os_policy_assignment attribute:
     + provide the argument os_policy_assignment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment.

     To set the location attribute:
     + provide the argument os_policy_assignment on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe an OS policy my-assignment in location us-central1-a:

    $ gcloud compute os-config os-policy-assignments describe \
        my-assignment --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/describe)

---
### `gcloud compute os-config os-policy-assignments list`

List OS policy assignments for a specified location

List OS policy assignments.

**Synopsis:**
```
gcloud compute os-config os-policy-assignments list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/zone. |


**Examples:**
```bash
To list the OS policy assignments in my-project and location us-central1-a,
run:

    $ gcloud compute os-config os-policy-assignments list \
        --project=my-project --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/list)

---
### `gcloud compute os-config os-policy-assignments list-revisions`

List the revisions of an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments list-revisions
    (OS_POLICY_ASSIGNMENT : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment resource - OS policies assignment data to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument os_policy_assignment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OS_POLICY_ASSIGNMENT
     ID of the OS policy assignment or fully qualified identifier for the
     OS policy assignment.

     To set the os_policy_assignment attribute:
     + provide the argument os_policy_assignment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment.

     To set the location attribute:
     + provide the argument os_policy_assignment on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To list the revisions of an OS policy my-assignment in location
us-central1-a:

    $ gcloud compute os-config os-policy-assignments list-revisions \
        my-assignment --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/list-revisions)

---
### `gcloud compute os-config os-policy-assignments update`

Update an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments update
    (OS_POLICY_ASSIGNMENT : --location=LOCATION) --file=FILE
    [--allow-missing] [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment resource - OS policy assignment to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument os_policy_assignment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OS_POLICY_ASSIGNMENT
     ID of the OS policy assignment or fully qualified identifier for the
     OS policy assignment.

     To set the os_policy_assignment attribute:
     + provide the argument os_policy_assignment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment.

     To set the location attribute:
     + provide the argument os_policy_assignment on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | Absolute path to the OS policy assignment file on your local client. File must be in either JSON or YAML format. This file defines the OS policies that you want to apply to your VMs, the target VMs that you want to apply the policies to, and the rollout rate at which to apply the OS policies. For more information about this resource and sample OS policy assignment files, see https://cloud.google.com/compute/docs/os-configuration-management/working-with-os-policies#os-policy-assignment. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-missing` |  |  | If set to true, and the OS policy assignment is not found, the new policy assignment resource will be created. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update an OS policy assignment my-assignment in location us-central1-a
with config file /path/to/file/config.yaml, run:

    $ gcloud compute os-config os-policy-assignments update \
        my-assignment --location=us-central1-a \
        --file=/path/to/file/config.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/update)

---

## `gcloud compute os-config os-policy-assignments operations` — manage long-running operations generated from creating or editing OS policy assignments
### `gcloud compute os-config os-policy-assignments operations cancel`

Cancel an OS policy assignment operation

Cancel an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments operations cancel
    (OPERATION
      : --location=LOCATION --os-policy-assignment=OS_POLICY_ASSIGNMENT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment operation resource - OS policy assignment data to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the OS policy assignment operation or fully qualified
     identifier for the OS policy assignment operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --os-policy-assignment=OS_POLICY_ASSIGNMENT
     OS policy assignment.

     To set the os-policy-assignment attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --os-policy-assignment on the command line.
```

**Examples:**
```bash
To cancel a long-running operation operation-id for OS policy assignment
my-assignment in location us-central1-a:

    $ gcloud compute os-config os-policy-assignments operations cancel \
        operation-id --location=us-central1-a \
        --os-policy-assignment=my-assignment

Or pass the full operation name:

    $ gcloud compute os-config os-policy-assignments operations cancel \
        projects/my-project/locations/us-central1-a/\
    osPolicyAssignments/my-assignment/operations/operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/operations/cancel)

---
### `gcloud compute os-config os-policy-assignments operations describe`

Describe an OS policy assignment operation

Describe an OS policy assignment

**Synopsis:**
```
gcloud compute os-config os-policy-assignments operations describe
    (OPERATION
      : --location=LOCATION --os-policy-assignment=OS_POLICY_ASSIGNMENT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OS policy assignment operation resource - OS policy assignment data to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the OS policy assignment operation or fully qualified
     identifier for the OS policy assignment operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the OS policy assignment operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property compute/zone.

  --os-policy-assignment=OS_POLICY_ASSIGNMENT
     OS policy assignment.

     To set the os-policy-assignment attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --os-policy-assignment on the command line.
```

**Examples:**
```bash
To describe an operation with`operation-id for an OS policy assignment
my-assignment in location us-central1-a, run:

    $ gcloud compute os-config os-policy-assignments operations \
        describe operation-id --location=us-central1-a \
        --os-policy-assignment=my-assignment

You can also describe an operation by passing the full operation name:

    $ gcloud compute os-config os-policy-assignments operations \
        describe \
        projects/my-project/locations/us-central1-a/\
    osPolicyAssignments/my-assignment/operations/operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/os-policy-assignments/operations/describe)

---

## `gcloud compute os-config patch-deployments` — manage guest OS patch deployments for Compute Engine VM instances
### `gcloud compute os-config patch-deployments create`

Create a patch deployment for a project

gcloud compute os-config patch-deployments create creates a patch
deployment in a project from a specified file. A patch deployment triggers
a patch job to run at specific time(s) according to a schedule, and applies
instance filters and other patch configurations to the patch job at run
time. Alternatively, to run a patch job on-demand, see $ gcloud compute
os-config patch-jobs execute.

**Synopsis:**
```
gcloud compute os-config patch-deployments create PATCH_DEPLOYMENT_ID
    --file=FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PATCH_DEPLOYMENT_ID
   Name of the patch deployment to create.

   This name must contain only lowercase letters, numbers, and hyphens,
   start with a letter, end with a number or a letter, be between 1-63
   characters, and unique within the project.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | The JSON or YAML file with the patch deployment to create. For information about the patch deployment format, see https://cloud.google.com/compute/docs/osconfig/rest/v1/projects.patchDeployments. |


**Examples:**
```bash
To create a patch deployment patch-deployment-1 in the current project,
run:

    $ gcloud compute os-config patch-deployments create \
      patch-deployment-1 --file=path_to_config_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/create)

---
### `gcloud compute os-config patch-deployments delete`

Delete the specified patch deployment

Delete the specified patch deployment.

**Synopsis:**
```
gcloud compute os-config patch-deployments delete PATCH_DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch deployment resource - Patch deployment to delete. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument patch_deployment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_DEPLOYMENT
     ID of the patch_deployment or fully qualified identifier for the
     patch_deployment.

     To set the patch_deployment attribute:
     + provide the argument patch_deployment on the command line.
```

**Examples:**
```bash
To delete the patch deployment patch-deployment-1 in the current project,
run:

    $ gcloud compute os-config patch-deployments delete \
      patch-deployment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/delete)

---
### `gcloud compute os-config patch-deployments describe`

Describe the specified patch deployment

Describe the specified patch deployment.

**Synopsis:**
```
gcloud compute os-config patch-deployments describe PATCH_DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch deployment resource - Patch deployment to describe. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument patch_deployment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_DEPLOYMENT
     ID of the patch_deployment or fully qualified identifier for the
     patch_deployment.

     To set the patch_deployment attribute:
     + provide the argument patch_deployment on the command line.
```

**Examples:**
```bash
To check the status of the patch deployment patch-deployment-1 in the
current project, run:

    $ gcloud compute os-config patch-deployments describe \
      patch-deployment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/describe)

---
### `gcloud compute os-config patch-deployments list`

List patch deployments in a project

List patch deployments in a project.

**Synopsis:**
```
gcloud compute os-config patch-deployments list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all patch deployments in the current project, run:

    $ gcloud compute os-config patch-deployments list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/list)

---
### `gcloud compute os-config patch-deployments pause`

Pause patch deployment in a project

Pause patch deployment in a project.

**Synopsis:**
```
gcloud compute os-config patch-deployments pause PATCH_DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch deployment resource - Patch deployment to pause. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument patch_deployment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_DEPLOYMENT
     ID of the patch_deployment or fully qualified identifier for the
     patch_deployment.

     To set the patch_deployment attribute:
     + provide the argument patch_deployment on the command line.
```

**Examples:**
```bash
To pause the patch deployment patch-deployment-1 in the current project,
run:

    $ gcloud compute os-config patch-deployments pause patch-deployment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/pause)

---
### `gcloud compute os-config patch-deployments resume`

Resume patch deployment in a project

Resume patch deployment in a project.

**Synopsis:**
```
gcloud compute os-config patch-deployments resume PATCH_DEPLOYMENT
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch deployment resource - Patch deployment to resume. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument patch_deployment on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_DEPLOYMENT
     ID of the patch_deployment or fully qualified identifier for the
     patch_deployment.

     To set the patch_deployment attribute:
     + provide the argument patch_deployment on the command line.
```

**Examples:**
```bash
To resume the patch deployment patch-deployment-1 in the current project,
run:

    $ gcloud compute os-config patch-deployments resume \
      patch-deployment-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/resume)

---
### `gcloud compute os-config patch-deployments update`

Update patch deployment in a project

Updates a patch deployment in a project. To update the patch deployment,
you must specify a configuration file.

**Synopsis:**
```
gcloud compute os-config patch-deployments update PATCH_DEPLOYMENT_ID
    --file=FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PATCH_DEPLOYMENT_ID
   Name of the patch deployment to update.

   To get a list of patch deployments that are available for update, run
   the gcloud compute os-config patch-deployments list command.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file` | FILE |  | The JSON or YAML file with the patch deployment to update. For information about the patch deployment format, see https://cloud.google.com/compute/docs/osconfig/rest/v1/projects.patchDeployments. |


**Examples:**
```bash
To update a patch deployment patch-deployment-1 in the current project,
run:

    $ gcloud compute os-config patch-deployments update \
      patch-deployment-1 --file=path_to_config_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-deployments/update)

---

## `gcloud compute os-config patch-jobs` — manage OS patches for Compute Engine VMs
### `gcloud compute os-config patch-jobs cancel`

Cancel a specific OS patch job which must currently be active

**Synopsis:**
```
gcloud compute os-config patch-jobs cancel PATCH_JOB [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch job resource - Patch job to cancel. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument patch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_JOB
     ID of the patch_job or fully qualified identifier for the patch_job.

     To set the patch_job attribute:
     + provide the argument patch_job on the command line.
```

**Examples:**
```bash
To cancel the patch job job1, run:

    $ gcloud compute os-config patch-jobs cancel job1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-jobs/cancel)

---
### `gcloud compute os-config patch-jobs describe`

Describe a specified OS patch job

**Synopsis:**
```
gcloud compute os-config patch-jobs describe PATCH_JOB
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch job resource - Patch job to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument patch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_JOB
     ID of the patch_job or fully qualified identifier for the patch_job.

     To set the patch_job attribute:
     + provide the argument patch_job on the command line.
```

**Examples:**
```bash
To check the status of the patch job job1, run:

    $ gcloud compute os-config patch-jobs describe job1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-jobs/describe)

---
### `gcloud compute os-config patch-jobs execute`

Execute an OS patch on the specified VM instances

Execute an OS patch on the specified VM instances.

**Synopsis:**
```
gcloud compute os-config patch-jobs execute
    (--instance-filter-all | --instance-filter-group-labels=[KEY=VALUE,...]
      --instance-filter-name-prefixes=[INSTANCE_FILTER_NAME_PREFIXES,...]
      --instance-filter-names=[INSTANCE_FILTER_NAMES,...]
      --instance-filter-zones=[INSTANCE_FILTER_ZONES,...]) [--async]
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME] [--dry-run]
    [--duration=DURATION] [--mig-instances-allowed]
    [--reboot-config=REBOOT_CONFIG] [--skip-unpatchable-vms]
    [--apt-dist --apt-excludes=[APT_EXCLUDES,...]
      | --apt-exclusive-packages=[APT_EXCLUSIVE_PACKAGES,...]]
    [--post-patch-linux-executable=POST_PATCH_LINUX_EXECUTABLE
      --post-patch-linux-success-codes=[POST_PATCH_LINUX_SUCCESS_CODES,
      ...]]
    [--post-patch-windows-executable=POST_PATCH_WINDOWS_EXECUTABLE
      --post-patch-windows-success-codes=[POST_PATCH_WINDOWS_SUCCESS_CODES,
      ...]]
    [--pre-patch-linux-executable=PRE_PATCH_LINUX_EXECUTABLE
      --pre-patch-linux-success-codes=[PRE_PATCH_LINUX_SUCCESS_CODES,...]]
    [--pre-patch-windows-executable=PRE_PATCH_WINDOWS_EXECUTABLE
      --pre-patch-windows-success-codes=[PRE_PATCH_WINDOWS_SUCCESS_CODES,
      ...]]
    [--rollout-mode=ROLLOUT_MODE
      --rollout-disruption-budget=ROLLOUT_DISRUPTION_BUDGET
      | --rollout-disruption-budget-percent=ROLLOUT_DISRUPTION_BUDGET_PERCENT]
    [--windows-exclusive-patches=[WINDOWS_EXCLUSIVE_PATCHES,...]
      | --windows-classifications=[WINDOWS_CLASSIFICATIONS,...]
      --windows-excludes=[WINDOWS_EXCLUDES,...]]
    [--yum-exclusive-packages=[YUM_EXCLUSIVE_PACKAGES,...]
      | --yum-excludes=[YUM_EXCLUDES,...] --yum-minimal --yum-security]
    [--zypper-exclusive-patches=[ZYPPER_EXCLUSIVE_PATCHES,...]
      | --zypper-categories=[ZYPPER_CATEGORIES,...]
      --zypper-excludes=[ZYPPER_EXCLUDES,...]
      --zypper-severities=[ZYPPER_SEVERITIES,...]
      --zypper-with-optional --zypper-with-update] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-filter-all` |  |  | _[Exactly one of these must be specified:]_ A filter that targets all instances in the project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Textual description of the patch job. |
| `--display-name` | DISPLAY_NAME |  | Display name for this patch job. This does not have to be unique. |
| `--dry-run` |  |  | Whether to execute this patch job as a dry run. If this patch job is a dry run, instances are contacted, but the patch is not run. |
| `--duration` | DURATION |  | Total duration in which the patch job must complete. If the patch does not complete in this time, the process times out. While some instances might still be running the patch, they will not continue to work after completing the current step. See $ gcloud topic datetimes for information on specifying absolute time durations. If unspecified, the job stays active until all instances complete the patch. |
| `--mig-instances-allowed` |  |  | If set, patching of VMs that are part of a managed instance group (MIG) is allowed. |
| `--reboot-config` | one of: always Always reboot the machine after the update completes |  | Post-patch reboot settings. REBOOT_CONFIG must be one of: always Always reboot the machine after the update completes. default The agent decides if a reboot is necessary by checking signals such as registry keys or '/var/run/reboot-required'. never Never reboot the machine after the update completes. |
| `--skip-unpatchable-vms` |  |  | If set, enables enhanced reporting for the patch job: 1. Allows the patch job to skip unpatchable instances, reporting them as SKIPPED. An instance can be unpatchable for two reasons: a. The instance runs Container-Optimized OS (COS), which cannot be patched. b. The instance is part of a managed instance group (MIG), and patching MIG instances is disabled in the patch job's configuration (`--mig-instances-allowed` flag is not set). 2. Reports the patch job as SUCCEEDED if it completes without errors, even if some instances were SKIPPED. 3. Reports the patch job as COMPLETED_WITH_INACTIVE_VMS if it completes without errors, but some instances were INACTIVE and were not patched. |


**Examples:**
```bash
To start a patch job named my patch job that patches all instances in the
current project, run:

    $ gcloud compute os-config patch-jobs execute \
    --display-name="my patch job" --instance-filter-all

To patch an instance named instance-1 in the us-east1-b zone, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-names="zones/us-east1-b/instances/instance-1"

To patch all instances in the us-central1-b and europe-west1-d zones, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-zones="us-central1-b,europe-west1-d"

To patch all instances where the env label is test and app label is web,
run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-group-labels="env=test,app=web"

To patch all instances where the env label is test and app label is web or
where the env label is staging and app label is web, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-group-labels="env=test,app=web" \
    --instance-filter-group-labels="env=staging,app=web"

To apply security and critical patches to Windows instances with the prefix
windows- in the instance name, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-name-prefixes="windows-" \
    --windows-classifications=SECURITY,CRITICAL

To update only KB4339284 on Windows instances with the prefix windows- in
the instance name, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-name-prefixes="windows-" \
    --windows-exclusive-patches=4339284

To patch all instances in the current project and specify scripts to run
pre-patch and post-patch, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-all \
    --pre-patch-linux-executable="/bin/script" \
    --pre-patch-linux-success-codes=0,200 \
    --pre-patch-windows-executable="C:\Users\user\script.ps1" \
    --post-patch-linux-executable="gs://my-bucket/linux-script#123" \
    --post-patch-windows-executable="gs://my-bucket/windows-script#678"

To patch all instances zone-by-zone with no more than 50 percent of the
instances in the same zone disrupted at a given time, run:

    $ gcloud compute os-config patch-jobs execute \
    --instance-filter-all --rollout-mode=zone-by-zone \
    --rollout-disruption-budget-percent=50
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-jobs/execute)

---
### `gcloud compute os-config patch-jobs list`

List ongoing and completed patch jobs

**Synopsis:**
```
gcloud compute os-config patch-jobs list [--filter=EXPRESSION]
    [--limit=LIMIT; default=10] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list patch jobs in the current project, run:

    $ gcloud compute os-config patch-jobs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-jobs/list)

---
### `gcloud compute os-config patch-jobs list-instance-details`

List the instance details for an OS patch job

**Synopsis:**
```
gcloud compute os-config patch-jobs list-instance-details PATCH_JOB
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Patch job resource - Patch job to list instance details. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument patch_job on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PATCH_JOB
     ID of the patch_job or fully qualified identifier for the patch_job.

     To set the patch_job attribute:
     + provide the argument patch_job on the command line.
```

**Examples:**
```bash
To list the instance details for each instance in the patch job job1, run:

    $ gcloud compute os-config patch-jobs list-instance-details job1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/patch-jobs/list-instance-details)

---

## `gcloud compute os-config policy-orchestrators` — manage VM Manager policy orchestrators
### `gcloud compute os-config policy-orchestrators create`

Create a policy orchestrator

Create a policy orchestrator.

**Synopsis:**
```
gcloud compute os-config policy-orchestrators create
    (POLICY_ORCHESTRATOR : --folder=FOLDER --organization=ORGANIZATION)
    --policy-type=POLICY_TYPE [--action=ACTION; default="upsert"] [--async]
    [--include-folders=INCLUDE_FOLDERS]
    [--include-locations=INCLUDE_LOCATIONS]
    [--include-projects=INCLUDE_PROJECTS] [--policy-file=POLICY_FILE]
    [--policy-id=POLICY_ID] [--state=STATE; default="ACTIVE"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy orchestrator resource - Policy orchestrator to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_orchestrator on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [policy_orchestrator_project,
   policy_orchestrator_folder, policy_orchestrator_organization].

This must be specified.

  POLICY_ORCHESTRATOR
     ID of the policy_orchestrator or fully qualified identifier for the
     policy_orchestrator.

     To set the policy_orchestrator attribute:
     + provide the argument policy_orchestrator on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     Folder of the policy_orchestrator.

     To set the folder attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type [policy_orchestrator_folder].

  --organization=ORGANIZATION
     Organization of the policy_orchestrator.

     To set the organization attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type [policy_orchestrator_organization].
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-type` | POLICY_TYPE |  | Policy type to use. POLICY_TYPE must be (only one value is supported): os_policy_assignment_v1 OS policy assignment v1. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: delete Delete a policy with a given name | upsert | Action to be taken on policy. ACTION must be one of: delete Delete a policy with a given name. policy-id must be specified. upsert Create or update a policy. policy-file must be specified. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--include-folders` | INCLUDE_FOLDERS |  | Applies policy to selected folders. Comma-separated list of folder numbers. Can beused together with --include-projects. |
| `--include-locations` | INCLUDE_LOCATIONS |  | Applies policy to selected locations, e.g. us-central1-a. |
| `--include-projects` | INCLUDE_PROJECTS |  | Applies policy to selected projects. Comma-separated list of project numbers. Can be used together with --include-folders. |
| `--policy-file` | POLICY_FILE |  | Absolute path to the OS policy assignment file on your local client. File must be in either JSON or YAML format. This file defines the OS policies that you want to apply to your VMs, the target VMs that you want to apply the policies to, and the rollout rate at which to apply the OS policies on a zonal level. For more information about this resource and sample OS policy assignment files, see https://cloud.google.com/compute/docs/os-configuration-management/working-with-os-policies#os-policy-assignment. |
| `--policy-id` | POLICY_ID |  | Policy id. Must be specified for DELETE action. |
| `--state` | one of: active Creates a policy orchestrator in ACTIVE state | ACTIVE | State of the policy orchestrator. STATE must be one of: active Creates a policy orchestrator in ACTIVE state. stopped Creates a policy orchestrator in STOPPED state. |


**Examples:**
```bash
To create a policy orchestrator my-orchestrator in folder 123456 for OS
policy assignment with config file /path/to/file/config.yaml, run:

    $ gcloud compute os-config policy-orchestrators create \
        my-orchestrator --folder=123456 \
        --policy-type os_policy_assignment_v1 \
        --policy-file=/path/to/file/config.yaml

To create a policy orchestrator my-orchestrator in folder 123456 that
deletes OS Policy assignments with id my-policy, run:

    $ gcloud compute os-config policy-orchestrators create \
        my-orchestrator --folder=123456 \
        --policy-type os_policy_assignment_v1 --action delete \
        --policy-id my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/policy-orchestrators/create)

---
### `gcloud compute os-config policy-orchestrators delete`

Delete a policy orchestrator

Delete a policy orchestrator and cancel ongoing rollouts (best-effort).

**Synopsis:**
```
gcloud compute os-config policy-orchestrators delete
    (POLICY_ORCHESTRATOR : --folder=FOLDER --organization=ORGANIZATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy orchestrator resource - policy orchestrator to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_orchestrator on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [policy_orchestrator_project,
   policy_orchestrator_folder, policy_orchestrator_organization].

This must be specified.

  POLICY_ORCHESTRATOR
     ID of the policy_orchestrator or fully qualified identifier for the
     policy_orchestrator.

     To set the policy_orchestrator attribute:
     + provide the argument policy_orchestrator on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     Folder of the policy_orchestrator.

     To set the folder attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type [policy_orchestrator_folder].

  --organization=ORGANIZATION
     Organization of the policy_orchestrator.

     To set the organization attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type [policy_orchestrator_organization].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a policy orchestrator my-orchestrator in the folder 123456:

    $ gcloud compute os-config policy-orchestrators delete \
        my-orchestrator --folder=123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/policy-orchestrators/delete)

---
### `gcloud compute os-config policy-orchestrators describe`

Describe a policy orchestrator

Get the details of a policy orchestrator.

**Synopsis:**
```
gcloud compute os-config policy-orchestrators describe
    (POLICY_ORCHESTRATOR : --folder=FOLDER --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy orchestrator resource - The policy orchestrator to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_orchestrator on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [policy_orchestrator_project,
   policy_orchestrator_folder, policy_orchestrator_organization].

This must be specified.

  POLICY_ORCHESTRATOR
     ID of the policy_orchestrator or fully qualified identifier for the
     policy_orchestrator.

     To set the policy_orchestrator attribute:
     + provide the argument policy_orchestrator on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     Folder of the policy_orchestrator.

     To set the folder attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type [policy_orchestrator_folder].

  --organization=ORGANIZATION
     Organization of the policy_orchestrator.

     To set the organization attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type [policy_orchestrator_organization].
```

**Examples:**
```bash
To describe a policy orchestrator my-orchestrator:

    $ gcloud compute os-config policy-orchestrators describe \
        my-orchestrator
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/policy-orchestrators/describe)

---
### `gcloud compute os-config policy-orchestrators list`

List policy orchestrators

List policy orchestrators.

**Synopsis:**
```
gcloud compute os-config policy-orchestrators list
    [--folder=FOLDER --organization=ORGANIZATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[following types: [project_a, folder_a, organization_a].]_ ID of the project_folder_organization or fully qualified identifier for the project_folder_organization. To set the folder attribute: + provide the argument --folder on the command line. Must be specified for resource of type [folder_a]. |
| `--organization` | ORGANIZATION |  | _[following types: [project_a, folder_a, organization_a].]_ ID of the project_folder_organization or fully qualified identifier for the project_folder_organization. To set the organization attribute: + provide the argument --organization on the command line. Must be specified for resource of type [organization_a]. |


**Examples:**
```bash
To list the policy orchestrators in folder 123456, run:

    $ gcloud compute os-config policy-orchestrators list --folder 123456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/policy-orchestrators/list)

---
### `gcloud compute os-config policy-orchestrators update`

Update a policy orchestrator

Update a policy orchestrator.

**Synopsis:**
```
gcloud compute os-config policy-orchestrators update
    (POLICY_ORCHESTRATOR : --folder=FOLDER --organization=ORGANIZATION)
    [--action=ACTION] [--async] [--policy-file=POLICY_FILE]
    [--policy-id=POLICY_ID] [--state=STATE]
    [--clear-folders | --include-folders=INCLUDE_FOLDERS]
    [--clear-locations | --include-locations=INCLUDE_LOCATIONS]
    [--clear-projects | --include-projects=INCLUDE_PROJECTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy orchestrator resource - Policy orchestrator to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy_orchestrator on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project. This resource can be one of the
   following types: [policy_orchestrator_project,
   policy_orchestrator_folder, policy_orchestrator_organization].

This must be specified.

  POLICY_ORCHESTRATOR
     ID of the policy_orchestrator or fully qualified identifier for the
     policy_orchestrator.

     To set the policy_orchestrator attribute:
     + provide the argument policy_orchestrator on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --folder=FOLDER
     Folder of the policy_orchestrator.

     To set the folder attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --folder on the command line. Must be
       specified for resource of type [policy_orchestrator_folder].

  --organization=ORGANIZATION
     Organization of the policy_orchestrator.

     To set the organization attribute:
     + provide the argument policy_orchestrator on the command line with
       a fully specified name;
     + provide the argument --organization on the command line. Must be
       specified for resource of type [policy_orchestrator_organization].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: delete Delete a policy with a given name |  | Action to be taken on policy. ACTION must be one of: delete Delete a policy with a given name. policy-id must be specified. upsert Create or update a policy. policy-file must be specified. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--policy-file` | POLICY_FILE |  | Absolute path to the OS policy assignment file on your local client. File must be in either JSON or YAML format. This file defines the OS policies that you want to apply to your VMs, the target VMs that you want to apply the policies to, and the rollout rate at which to apply the OS policies on a zonal level. For more information about this resource and sample OS policy assignment files, see https://cloud.google.com/compute/docs/os-configuration-management/working-with-os-policies#os-policy-assignment. |
| `--policy-id` | POLICY_ID |  | Policy id. Must be specified for DELETE action. |
| `--state` | one of: active Updates the policy orchestrator to ACTIVE state |  | State of the policy orchestrator. STATE must be one of: active Updates the policy orchestrator to ACTIVE state. stopped Updates the policy orchestrator to STOPPED state. |


**Examples:**
```bash
To update an policy orchestrator my-orchestrator in folder 123456 with
config file /path/to/file/config.yaml, run:

    $ gcloud compute os-config policy-orchestrators update \
        my-orchestrator --folder=123456 \
        --policy-file=/path/to/file/config.yaml

To update an policy orchestrator my-orchestrator in folder 123456 with
state STOPPED, run:

    $ gcloud compute os-config policy-orchestrators update \
        my-orchestrator --folder=123456 --state=stopped
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/policy-orchestrators/update)

---

## `gcloud compute os-config project-feature-settings` — manage VM Manager project feature settings
### `gcloud compute os-config project-feature-settings describe`

Get all VM Manager project feature settings

Get all VM Manager project feature settings.

**Synopsis:**
```
gcloud compute os-config project-feature-settings describe
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To get project feature settings for project my-project:

    $ gcloud compute os-config project-feature-settings describe \
       --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/project-feature-settings/describe)

---
### `gcloud compute os-config project-feature-settings update`

Update VM Manager project feature settings

Update VM Manager project feature settings.

**Synopsis:**
```
gcloud compute os-config project-feature-settings update
    --patch-and-config-feature-set=PATCH_AND_CONFIG_FEATURE_SET
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--patch-and-config-feature-set` | one of: full Full set of VM Manager functionality (alias for osconfig-c) |  | Specifies the feature set for VM Manager. PATCH_AND_CONFIG_FEATURE_SET must be one of: full Full set of VM Manager functionality (alias for osconfig-c). limited Limited feature set. Enables only the basic set of features (alias for osconfig-b). osconfig-b Limited feature set. Enables only the basic set of features. osconfig-c Full set of VM Manager functionality. |


**Examples:**
```bash
To update project feature settings for project my-project:

    $ gcloud compute os-config project-feature-settings update \
       --project=my-project --patch-and-config-feature-set=full
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/project-feature-settings/update)

---

## `gcloud compute os-config vulnerability-reports` — display vulnerability reports for a Compute Engine VM
### `gcloud compute os-config vulnerability-reports describe`

Describe the vulnerability report data for a Compute Engine VM instance

Describe the vulnerability report data for a Compute Engine VM instance.

**Synopsis:**
```
gcloud compute os-config vulnerability-reports describe INSTANCE
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE
   ID or name of the Compute Engine VM instance to describe. For details
   on valid instance IDs, refer to the criteria documented under the field
   id at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Compute Engine VM instance to describe. If not specified, the property compute/zone is used. For details on setting properties, see: https://cloud.google.com/sdk/docs/properties |


**Examples:**
```bash
To describe the vulnerability report of an instance my-instance that has
the instance ID 5678 in the current project and location 'us-central1-a',
run:

    $ gcloud compute os-config vulnerability-reports describe \
        my-instance --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/vulnerability-reports/describe)

---
### `gcloud compute os-config vulnerability-reports list`

List vulnerability report data for all Compute Engine VM instances in a specified location

List vulnerability report data for all Compute Engine VM instances in a
specified location.

The default page size is 25. To modify this, use the --page-size flag.

**Synopsis:**
```
gcloud compute os-config vulnerability-reports list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Location of the Compute Engine VM instances to list. If not specified, the property compute/zone is used. For details on setting properties, see: https://cloud.google.com/sdk/docs/properties |


**Examples:**
```bash
To list the vulnerability report of Compute Engine VM instances in
my-project and location us-central1-a, run:

    $ gcloud compute os-config vulnerability-reports list \
        --project=my-project --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/os-config/vulnerability-reports/list)

---
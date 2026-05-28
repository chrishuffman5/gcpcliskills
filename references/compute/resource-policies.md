# gcloud compute resource-policies

manage Compute Engine Resource Policies

### `gcloud compute resource-policies delete`

Delete a Compute Engine resource policy

Delete a Compute Engine resource policy.

**Synopsis:**
```
gcloud compute resource-policies delete NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
The following command deletes a Compute Engine resource policy.

    $ gcloud compute resource-policies delete my-resource-policy \
        --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/delete)

---
### `gcloud compute resource-policies describe`

Describe a Compute Engine resource policy

Describe a Compute Engine resource policy.

**Synopsis:**
```
gcloud compute resource-policies describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
The following command shows the details of a Compute Engine resource
policy.

    $ gcloud compute resource-policies describe my-resource-policy \
        --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/describe)

---
### `gcloud compute resource-policies get-iam-policy`

Get the IAM policy for a Compute Engine resource policy

gcloud compute resource-policies get-iam-policy displays the IAM policy
associated with a Compute Engine resource policy in a project. If formatted
as JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute resource-policies get-iam-policy
    (RESOURCE_POLICY : --region=REGION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Resource policy resource - The resource policy to display the IAM policy
for. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument resource_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESOURCE_POLICY
     ID of the resource policy or fully qualified identifier for the
     resource policy.

     To set the resource_policy attribute:
     + provide the argument resource_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument resource_policy on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To print the IAM policy for a given resource policy, run:

    $ gcloud compute resource-policies get-iam-policy my-policy \
        --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/get-iam-policy)

---
### `gcloud compute resource-policies list`

List Google Compute Engine resource policies

gcloud compute resource-policies list displays all Google Compute Engine
resource policies in a project.

By default, resource policies from all regions are listed. The results can
be narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute resource-policies list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all resource policies in a project in table form, run:

    $ gcloud compute resource-policies list

To list the URIs of all resource policies in a project, run:

    $ gcloud compute resource-policies list --uri

To list all resource policies in the us-central1 and europe-west1 regions,
run:

    $ gcloud compute resource-policies list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/list)

---
### `gcloud compute resource-policies set-iam-policy`

Set the IAM policy for a Compute Engine resource policy

Set the IAM policy for the given resource policy as defined in a JSON or
YAML file.

**Synopsis:**
```
gcloud compute resource-policies set-iam-policy
    (RESOURCE_POLICY : --region=REGION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Resource policy resource - The resource policy to set the IAM policy for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument resource_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESOURCE_POLICY
     ID of the resource policy or fully qualified identifier for the
     resource policy.

     To set the resource_policy attribute:
     + provide the argument resource_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument resource_policy on the command line with a
       fully specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the resource policy my-policy:

    $ gcloud compute resource-policies set-iam-policy my-policy \
        --region=REGION policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/set-iam-policy)

---

## `gcloud compute resource-policies create` — create Compute Engine Resource Policies
### `gcloud compute resource-policies create disk-consistency-group`

Create a Compute Engine Disk Consistency Group resource policy

Create a Compute Engine disk consistency group resource policy.

**Synopsis:**
```
gcloud compute resource-policies create disk-consistency-group NAME
    [--description=DESCRIPTION] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
Create a disk consistency group policy:

    $ gcloud compute resource-policies create disk-consistency-group \
        my-resource-policy --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/create/disk-consistency-group)

---
### `gcloud compute resource-policies create group-placement`

Create a Compute Engine group placement resource policy

Create a Compute Engine Group Placement Resource Policy.

**Synopsis:**
```
gcloud compute resource-policies create group-placement NAME
    [--availability-domain-count=AVAILABILITY_DOMAIN_COUNT]
    [--collocation=COLLOCATION] [--description=DESCRIPTION]
    [--gpu-topology=GPU_TOPOLOGY] [--region=REGION] [--vm-count=VM_COUNT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--availability-domain-count` | AVAILABILITY_DOMAIN_COUNT |  | Number of availability domain in the group placement policy. |
| `--collocation` | one of: collocated Low network latency between more VMs placed on the same availability domain |  | Collocation specifies whether to place VMs inside the sameavailability domain on the same low-latency network. COLLOCATION must be one of: collocated Low network latency between more VMs placed on the same availability domain. unspecified-collocation Unspecified network latency between VMs placed on the same availability domain. This is the default behavior. |
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--gpu-topology` | GPU_TOPOLOGY |  | Specifies the shape of the GPU slice, in slice based GPU families eg. A4X. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--vm-count` | VM_COUNT |  | Number of instances targeted by the group placement policy. Google does not recommend that you use this flag unless you use a compact policy and you want your policy to work only if it contains this exact number of VMs. |


**Examples:**
```bash
To create a Compute Engine group placement policy with two availability
domains, run:        $ gcloud compute resource-policies create group-placement \
        my-resource-policy --region=REGION --availability-domain-count=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/create/group-placement)

---
### `gcloud compute resource-policies create instance-schedule`

Create a Compute Engine instance schedule resource policy

Create a Compute Engine instance schedule resource policy.

**Synopsis:**
```
gcloud compute resource-policies create instance-schedule NAME
    [--description=DESCRIPTION] [--end-date=END_DATE]
    [--initiation-date=INITIATION_DATE] [--region=REGION]
    [--timezone=TIMEZONE] [--vm-start-schedule=VM_START_SCHEDULE]
    [--vm-stop-schedule=VM_STOP_SCHEDULE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--end-date` | END_DATE |  | The expiration time of the schedule policy. The timestamp must be an RFC3339 valid string. |
| `--initiation-date` | INITIATION_DATE |  | The start time of the schedule policy. The timestamp must be an RFC3339 valid string. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--timezone` | TIMEZONE |  | Timezone used in interpreting schedule. The value of this field must be a time zone name from the tz database http://en.wikipedia.org/wiki/Tz_database |
| `--vm-start-schedule` | VM_START_SCHEDULE |  | Schedule for starting the instance, specified using standard CRON format. |
| `--vm-stop-schedule` | VM_STOP_SCHEDULE |  | Schedule for stopping the instance, specified using standard CRON format. |


**Examples:**
```bash
To create an instance schedule resource policy that has a daily start
operation at 8 AM and a daily stop operation at 5 PM for the UTC timezone,
run:

    $ gcloud compute resource-policies create instance-schedule \
        my-resource-policy --description="daily policy" \
        --vm-start-schedule="0 8 * * *" \
        --vm-stop-schedule="0 17 * * *" --timezone="UTC" --region=REGION

Use the initiation date and end date to limit when the policy is active. To
create an instance schedule resource policy with initiation and end dates,
run:

    $ gcloud compute resource-policies create instance-schedule \
        my-resource-policy --description="limited daily policy" \
        --vm-start-schedule="0 8 * * *" \
        --vm-stop-schedule="0 17 * * *" --timezone="UTC" \
        --region=REGION --initiation-date="2021-01-01T00:00:00.000Z" \
        --end-date="2021-02-01T00:00:00.000Z"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/create/instance-schedule)

---
### `gcloud compute resource-policies create snapshot-schedule`

Create a Compute Engine Snapshot Schedule Resource Policy

Create a Compute Engine Snapshot Schedule Resource Policy.

**Synopsis:**
```
gcloud compute resource-policies create snapshot-schedule NAME
    --max-retention-days=MAX_RETENTION_DAYS
    (--weekly-schedule-from-file=PATH_TO_FILE
      | --start-time=START_TIME (--daily-schedule | --hourly-schedule=HOURS
      | --weekly-schedule=WEEKLY_CYCLE)) [--description=DESCRIPTION]
    [--on-source-disk-delete=ON_SOURCE_DISK_DELETE] [--region=REGION]
    [--guest-flush
      --snapshot-labels=[KEY=VALUE,...] --storage-location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-retention-days` | MAX_RETENTION_DAYS |  | Maximum number of days snapshot can be retained. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--on-source-disk-delete` | one of: apply-retention-policy Continue to apply the retention window to automatically-created snapshots when the source disk is deleted |  | Retention behavior of automatic snapshots in the event of source disk deletion. ON_SOURCE_DISK_DELETE must be one of: apply-retention-policy Continue to apply the retention window to automatically-created snapshots when the source disk is deleted. keep-auto-snapshots Keep automatically-created snapshots when the source disk is deleted. This is the default behavior. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
The following command creates a Compute Engine Snapshot Schedule Resource
Policy with a daily snapshot taken at 13:00Z and a one day snapshot
retention policy.

    $ gcloud compute resource-policies create snapshot-schedule \
        my-resource-policy --region=REGION --start-time=13:00 \
        --daily-schedule --max-retention-days=1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/create/snapshot-schedule)

---
### `gcloud compute resource-policies create workload-policy`

Create a Compute Engine workload resource policy

Create a Compute Engine workload resource policy.

**Synopsis:**
```
gcloud compute resource-policies create workload-policy NAME --type=TYPE
    [--description=DESCRIPTION] [--region=REGION]
    [--accelerator-topology=ACCELERATOR_TOPOLOGY
      | --max-topology-distance=MAX_TOPOLOGY_DISTANCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: HIGH_AVAILABILITY For workloads that aim to be highly available |  | Type of the workload policy defining the high-level intent of the cluster. TYPE must be one of: HIGH_AVAILABILITY For workloads that aim to be highly available. Common examples are web / ML serving, or distributed database clusters. Compute Engine spreads VMs at best-effort to improve reliability of the distributed infrastructure. HIGH_THROUGHPUT For high throughput distributed workloads eg. HPC or ML training. Compute Engine collocates VMs at best-effort to reduce network latency between VMs. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To create a workload policy:

    $ gcloud compute resource-policies create workload-policy NAME \
        --type=TYPE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/create/workload-policy)

---

## `gcloud compute resource-policies update` — update Compute Engine Resource Policies
### `gcloud compute resource-policies update instance-schedule`

Update a Compute Engine Instance Schedule Resource Policy

Update a Compute Engine Instance Schedule Resource Policy.

**Synopsis:**
```
gcloud compute resource-policies update instance-schedule NAME
    [--description=DESCRIPTION] [--end-date=END_DATE]
    [--initiation-date=INITIATION_DATE] [--region=REGION]
    [--timezone=TIMEZONE] [--vm-start-schedule=VM_START_SCHEDULE]
    [--vm-stop-schedule=VM_STOP_SCHEDULE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--end-date` | END_DATE |  | The expiration time of the schedule policy. The timestamp must be an RFC3339 valid string. |
| `--initiation-date` | INITIATION_DATE |  | The start time of the schedule policy. The timestamp must be an RFC3339 valid string. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--timezone` | TIMEZONE |  | Timezone used in interpreting schedule. The value of this field must be a time zone name from the tz database http://en.wikipedia.org/wiki/Tz_database |
| `--vm-start-schedule` | VM_START_SCHEDULE |  | Schedule for starting the instance, specified using standard CRON format. |
| `--vm-stop-schedule` | VM_STOP_SCHEDULE |  | Schedule for stopping the instance, specified using standard CRON format. |


**Examples:**
```bash
To update an instance schedule resource policy with specified parameters:

    $ gcloud compute resource-policies update instance-schedule NAME \
        --region=REGION --timezone=UTC --vm-start-schedule="0 7 * * *" \
        --vm-stop-schedule="0 17 * * *"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/update/instance-schedule)

---
### `gcloud compute resource-policies update snapshot-schedule`

Update a Compute Engine Snapshot Schedule Resource Policy

Update a Compute Engine Snapshot Schedule Resource Policy.

**Synopsis:**
```
gcloud compute resource-policies update snapshot-schedule NAME
    [--description=DESCRIPTION] [--max-retention-days=MAX_RETENTION_DAYS]
    [--on-source-disk-delete=ON_SOURCE_DISK_DELETE] [--region=REGION]
    [--snapshot-labels=[KEY=VALUE,...]]
    [--weekly-schedule-from-file=PATH_TO_FILE
      | --start-time=START_TIME (--daily-schedule | --hourly-schedule=HOURS
      | --weekly-schedule=WEEKLY_CYCLE)] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the resource policy to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the backend. |
| `--max-retention-days` | MAX_RETENTION_DAYS |  | Maximum number of days snapshot can be retained. |
| `--on-source-disk-delete` | one of: apply-retention-policy Continue to apply the retention window to automatically-created snapshots when the source disk is deleted |  | Retention behavior of automatic snapshots in the event of source disk deletion. ON_SOURCE_DISK_DELETE must be one of: apply-retention-policy Continue to apply the retention window to automatically-created snapshots when the source disk is deleted. keep-auto-snapshots Keep automatically-created snapshots when the source disk is deleted. This is the default behavior. |
| `--region` | REGION |  | Region of the resource policy to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--snapshot-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. The label is added to each snapshot created by the schedule. |


**Examples:**
```bash
The following command updates a Compute Engine Snapshot Schedule Resource
Policy to take a daily snapshot at 13:00 UTC

    $ gcloud compute resource-policies update snapshot-schedule \
        my-resource-policy --region=REGION --start-time=13:00 \
        --daily-schedule
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/resource-policies/update/snapshot-schedule)

---
# gcloud compute reservations

manage Compute Engine reservations

### `gcloud compute reservations add-iam-policy-binding`

Add IAM policy binding to a Compute Engine reservation

Add an IAM policy binding to the IAM policy of a Compute Engine
reservation. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud compute reservations add-iam-policy-binding
    (RESERVATION : --zone=ZONE) --member=PRINCIPAL --role=ROLE
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - The reservation for which to add IAM policy binding
to. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ A condition to include in the binding. When the condition is explicitly specified as None (--condition=None), a binding without a condition is added. When the condition is specified and is not None, --role cannot be a basic role. Basic roles are roles/editor, roles/owner, and roles/viewer. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/compute.securityAdmin'
for the user 'test-user@gmail.com' with reservation 'my-reservation' and
zone 'ZONE', run:

    $ gcloud compute reservations add-iam-policy-binding \
        my-reservation --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To add an IAM policy binding which expires at the end of the year 2018 for
the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with reservation 'my-reservation' and zone 'ZONE',
run:

    $ gcloud compute reservations add-iam-policy-binding \
        my-reservation --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/add-iam-policy-binding)

---
### `gcloud compute reservations create`

Create a Compute Engine reservation

Create a Compute Engine reservation.

**Synopsis:**
```
gcloud compute reservations create RESERVATION
    (--vm-count=VM_COUNT
      (--source-instance-template=SOURCE_INSTANCE_TEMPLATE
      | [--machine-type=MACHINE_TYPE
      : --accelerator=[count=COUNT],[type=TYPE]
      --local-ssd=[count=COUNT],[interface=INTERFACE],[size=SIZE]
      --min-cpu-platform=MIN_CPU_PLATFORM])
      : --require-specific-reservation --resource-policies=[KEY=VALUE,...])
    [--description=DESCRIPTION]
    [--reservation-sharing-policy=RESERVATION_SHARING_POLICY] [--zone=ZONE]
    [--share-setting=SHARE_SETTING
      --share-with=SHARE_WITH,[SHARE_WITH,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vm-count` | VM_COUNT |  | _[This must be specified.]_ The number of VM instances that are allocated to this reservation. The value of this field must be an int in the range [1, 1000]. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--require-specific-reservation` |  |  | _[This must be specified.]_ Indicates whether the reservation can be consumed by VMs with "any reservation" defined. If enabled, then only VMs that target this reservation by name using --reservation-affinity=specific can consume from this reservation. |
| `--resource-policies` | [KEY=VALUE,...] |  | _[This must be specified.]_ The resource policies to include in this reservation. If you omit this flag, no resource policies are added. You can specify any string as the key, and specify the name of a resource policy as the value. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional description of the reservation to create. |
| `--reservation-sharing-policy` | one of: ALLOW_ALL The reservation can be shared with Google Cloud services |  | The reservation sharing policy to use for this reservation. RESERVATION_SHARING_POLICY must be one of: ALLOW_ALL The reservation can be shared with Google Cloud services. DISALLOW_ALL The reservation won't be shared with Google Cloud services. If you omit this flag during creation, the default value is DISALLOW_ALL. |
| `--zone` | ZONE |  | Zone of the reservation to create. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To create a Compute Engine reservation by specifying VM properties using an
instance template, run:

    $ gcloud compute reservations create my-reservation --vm-count=1 \
      --source-instance-template=example-instance-template \
      --zone=fake-zone

To create a Compute Engine reservation by directly specifying VM
properties, run:

    $ gcloud compute reservations create my-reservation --vm-count=1 \
      --machine-type=custom-8-10240 \
      --min-cpu-platform="Intel Haswell" \
      --accelerator=count=2,type=nvidia-tesla-v100 \
      --local-ssd=size=375,interface=scsi --zone=fake-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/create)

---
### `gcloud compute reservations delete`

Delete a Compute Engine reservation

Delete a Compute Engine reservation.

**Synopsis:**
```
gcloud compute reservations delete (RESERVATION : --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - The name of the reservation to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a given Compute Engine reservation, run:

    $ gcloud compute reservations delete my-reservation --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/delete)

---
### `gcloud compute reservations describe`

Show details about a Compute Engine reservation

Show details about a Compute Engine reservation.

**Synopsis:**
```
gcloud compute reservations describe (RESERVATION : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - The name of the reservation to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe a given Compute Engine reservation, run:

    $ gcloud compute reservations describe my-reservation --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/describe)

---
### `gcloud compute reservations get-iam-policy`

Get the IAM policy for a Compute Engine reservation

gcloud compute reservations get-iam-policy displays the IAM policy
associated with a Compute Engine reservation in a project. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute reservations get-iam-policy (RESERVATION : --zone=ZONE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - The reservation to display the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To print the IAM policy for a given reservation, run:

    $ gcloud compute reservations get-iam-policy my-reservation \
        --zone=my-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/get-iam-policy)

---
### `gcloud compute reservations list`

List Compute Engine reservations

List Compute Engine reservations.

**Synopsis:**
```
gcloud compute reservations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Compute Engine reservations, run:

    $ gcloud compute reservations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/list)

---
### `gcloud compute reservations perform-maintenance`

Perform maintenance on a reservation, only applicable to reservations with reservation blocks

Perform maintenance on a reservation, only applicable to reservations with
reservation blocks.

**Synopsis:**
```
gcloud compute reservations perform-maintenance RESERVATION [--scope=SCOPE]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to perform-maintenance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | one of: all Perform maintenance on all hosts in the reservation |  | The maintenance scope to set for the reservation. SCOPE must be one of: all Perform maintenance on all hosts in the reservation. running Perform maintenance only on the hosts in the reservation that have running VMs. unused Perform maintenance only on the hosts in the reservation that don't have running VMs. |
| `--zone` | ZONE |  | Zone of the reservation to perform-maintenance. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To perform maintenance on reservation my-reservation in my-zone with scope
all, run:

    $ gcloud compute reservations perform-maintenance my-reservation \
        --zone=my-zone --scope=all
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/perform-maintenance)

---
### `gcloud compute reservations remove-iam-policy-binding`

Remove IAM policy binding from a Compute Engine reservation

Remove an IAM policy binding from the IAM policy of a Compute Engine
reservation. One binding consists of a member, a role, and an optional
condition.

**Synopsis:**
```
gcloud compute reservations remove-iam-policy-binding
    (RESERVATION : --zone=ZONE) --member=PRINCIPAL --role=ROLE
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - The reservation for which to remove IAM policy
binding from. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | _[At most one of these can be specified:]_ Remove all bindings with this role and principal, irrespective of any conditions. |
| `--condition` | [KEY=VALUE,...] |  | _[At most one of these can be specified:]_ The condition of the binding that you want to remove. When the condition is explicitly specified as None (--condition=None), a binding without a condition is removed. Otherwise, only a binding with a condition that exactly matches the specified condition (including the optional description) is removed. For more on conditions, refer to the conditions overview guide: https://cloud.google.com/iam/docs/conditions-overview When using the --condition flag, include the following key-value pairs: expression (Required) Condition expression that evaluates to True or False. This uses a subset of Common Expression Language syntax. If the condition expression includes a comma, use a different delimiter to separate the key-value pairs. Specify the delimiter before listing the key-value pairs. For example, to specify a colon (:) as the delimiter, do the following: --condition=^:^title=TITLE:expression=EXPRESSION. For more information, see https://cloud.google.com/sdk/gcloud/reference/topic/escaping. title (Required) A short string describing the purpose of the expression. description (Optional) Additional description for the expression. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ Path to a local JSON or YAML file that defines the condition. To see available fields, see the help for --condition. Use a full or relative path to a local file containing the value of condition. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/compute.securityAdmin' for the user 'test-user@gmail.com' with
reservation 'my-reservation' and zone 'ZONE', run:

    $ gcloud compute reservations remove-iam-policy-binding \
        my-reservation --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

To remove an IAM policy binding which expires at the end of the year 2018
for the role of 'roles/compute.securityAdmin' and the user
'test-user@gmail.com' with reservation 'my-reservation' and zone 'ZONE',
run:

    $ gcloud compute reservations remove-iam-policy-binding \
        my-reservation --zone=ZONE --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin' \
        --condition='expression=request.time <
     timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2018,descrip\
    tion=Expires at midnight on 2018-12-31'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/remove-iam-policy-binding)

---
### `gcloud compute reservations set-iam-policy`

Set the IAM policy for a Compute Engine reservation

Set the IAM policy for the given reservation as defined in a JSON or YAML
file.

**Synopsis:**
```
gcloud compute reservations set-iam-policy (RESERVATION : --zone=ZONE)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - The reservation to set the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the reservation my-reservation:

    $ gcloud compute reservations set-iam-policy my-reservation \
        --zone=ZONE policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/set-iam-policy)

---
### `gcloud compute reservations update`

Update Compute Engine reservations

Update Compute Engine reservations.

**Synopsis:**
```
gcloud compute reservations update RESERVATION
    [--add-share-with=PROJECT,[PROJECT,...]]
    [--[no-]enable-emergent-maintenance]
    [--remove-share-with=PROJECT,[PROJECT,...]]
    [--reservation-sharing-policy=RESERVATION_SHARING_POLICY]
    [--scheduling-type=SCHEDULING_TYPE] [--vm-count=VM_COUNT] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-share-with` | PROJECT,[PROJECT,...] |  | If this reservation is shared (--share-setting is projects), then specify a comma-separated list of projects to share the reservation with. You must list the projects using project IDs or project numbers. |
| `--[no-]enable-emergent-maintenance` |  |  | Enables the reservation to receive notifications when urgent maintenance for a GPU VM starts after the VM encounters a host error. Use --enable-emergent-maintenance to enable and --no-enable-emergent-maintenance to disable. |
| `--remove-share-with` | PROJECT,[PROJECT,...] |  | A list of specific projects to remove from the list of projects that this reservation is shared with. List must contain project IDs or project numbers. |
| `--reservation-sharing-policy` | one of: ALLOW_ALL The reservation can be shared with Google Cloud services |  | The reservation sharing policy to use for this reservation. RESERVATION_SHARING_POLICY must be one of: ALLOW_ALL The reservation can be shared with Google Cloud services. DISALLOW_ALL The reservation won't be shared with Google Cloud services. If you omit this flag during creation, the default value is DISALLOW_ALL. |
| `--scheduling-type` | one of: GROUPED In GROUPED mode, maintenance is synchronized across all your VMs |  | How Compute Engine schedules maintenance events for your reserved hosts. SCHEDULING_TYPE must be one of: GROUPED In GROUPED mode, maintenance is synchronized across all your VMs. INDEPENDENT In INDEPENDENT mode, your VMs have different, unsynchronized maintenance schedules. |
| `--vm-count` | VM_COUNT |  | The number of VM instances that are allocated to this reservation. The value of this field must be an int in the range [1, 1000]. |
| `--zone` | ZONE |  | Zone of the reservation to update. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add project-1,project-2,project-3 to the list of projects that are
shared with a Compute Engine reservation, my-reservation in zone:
us-central1-a, run:

    $ gcloud compute reservations update my-reservation \
      --add-share-with=project-1,project-2,project-3 \
      --zone=us-central1-a

To remove project-1,project-2,project-3 from the list of projects that are
shared with a Compute Engine reservation, my-reservation in zone:
us-central1-a, run:

    $ gcloud compute reservations update my-reservation \
      --remove-share-with=project-1,project-2,project-3 \
      --zone=us-central1-a

To update the number of reserved VM instances to 500 for a Compute Engine
reservation, my-reservation in zone: us-central1-a, run:

    $ gcloud compute reservations update my-reservation \
      --zone=us-central1-a --vm-count=500
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/update)

---

## `gcloud compute reservations blocks` — manage Compute Engine reservation blocks
### `gcloud compute reservations blocks describe`

Describe a Compute Engine reservation block

Describe a Compute Engine reservation block.

**Synopsis:**
```
gcloud compute reservations blocks describe RESERVATION
    --block-name=BLOCK_NAME
    [--full-view=FULL_VIEW; default="BLOCK_VIEW_UNSPECIFIED"] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--block-name` | BLOCK_NAME |  | The name of the reservation block. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full-view` | one of: BLOCK_VIEW_BASIC Basic default view of the reservation block | BLOCK_VIEW_UNSPECIFIED | The view type for the reservation block. FULL_VIEW must be one of: BLOCK_VIEW_BASIC Basic default view of the reservation block. BLOCK_VIEW_FULL Full detailed view of the reservation block. |
| `--zone` | ZONE |  | Zone of the reservation to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe a reservation block in reservation my-reservation in my-zone
with block name my-reservation-block-0001, run:

    $ gcloud compute reservations blocks describe my-reservation \
        --zone=my-zone --block-name=my-reservation-block-0001
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/blocks/describe)

---
### `gcloud compute reservations blocks list`

List Compute Engine reservation blocks

gcloud compute reservations blocks list displays all Compute Engine
reservation blocks in a densely deployed reservation.

**Synopsis:**
```
gcloud compute reservations blocks list RESERVATION [--zone=ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the reservation to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To list all reservation blocks in a densely deployed reservation in table
form, run:

    $ gcloud compute reservations blocks list my-reservation \
        --zone=us-central1-a --project=my-project

To list the URIs of all reservation blocks in a densely deployed
reservation, run:

    $ gcloud compute reservations blocks list my-reservation \
        --zone=us-central1-a --project=my-project --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/blocks/list)

---
### `gcloud compute reservations blocks perform-maintenance`

Perform maintenance on a reservation block within a reservation

Perform maintenance on a reservation block within a reservation.

**Synopsis:**
```
gcloud compute reservations blocks perform-maintenance RESERVATION
    --block-name=BLOCK_NAME [--scope=SCOPE] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to perform-maintenance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--block-name` | BLOCK_NAME |  | The name of the reservation block. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | one of: all Perform maintenance on all hosts in the reservation block |  | The maintenance scope to set for the reservation block. SCOPE must be one of: all Perform maintenance on all hosts in the reservation block. running Perform maintenance only on the hosts in the reservation block that have running VMs. unused Perform maintenance only on the hosts in the reservation block that don't have running VMs. |
| `--zone` | ZONE |  | Zone of the reservation to perform-maintenance. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To perform maintenance on a reservation block in reservation my-reservation
in my-zone with block name my-reservation-block-0001 with scope all, run:

    $ gcloud compute reservations blocks perform-maintenance \
        my-reservation --zone=my-zone \
        --block-name=my-reservation-block-0001 --scope=all
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/blocks/perform-maintenance)

---

## `gcloud compute reservations sub-blocks` — manage Compute Engine reservation sub blocks
### `gcloud compute reservations sub-blocks describe`

Describe a Compute Engine reservation sub-block

Describe a Compute Engine reservation sub-block.

**Synopsis:**
```
gcloud compute reservations sub-blocks describe RESERVATION
    --block-name=BLOCK_NAME --sub-block-name=SUB_BLOCK_NAME
    [--full-view=FULL_VIEW; default="SUB_BLOCK_VIEW_UNSPECIFIED"]
    [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--block-name` | BLOCK_NAME |  | The name of the reservation block. |
| `--sub-block-name` | SUB_BLOCK_NAME |  | The name of the reservation sub block. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--full-view` | one of: SUB_BLOCK_VIEW_BASIC Basic default view of the reservation sub-block | SUB_BLOCK_VIEW_UNSPECIFIED | The view type for the reservation sub-block. FULL_VIEW must be one of: SUB_BLOCK_VIEW_BASIC Basic default view of the reservation sub-block. SUB_BLOCK_VIEW_FULL Full detailed view of the reservation sub-block. |
| `--zone` | ZONE |  | Zone of the reservation to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe a reservation sub-block in reservation exr1 in my-zone with
block name my-block and sub-block name my-sub-block, run:

    $ gcloud compute reservations sub-blocks describe exr1 \
        --zone=my-zone --block-name=my-block \
        --sub-block-name=my-sub-block
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/sub-blocks/describe)

---
### `gcloud compute reservations sub-blocks list`

List Compute Engine reservation sub-blocks

gcloud compute reservations sub-blocks list displays all Compute Engine
reservation sub-blocks in an extended reservation's block.

**Synopsis:**
```
gcloud compute reservations sub-blocks list RESERVATION
    --block-name=BLOCK_NAME [--zone=ZONE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to list.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--block-name` | BLOCK_NAME |  | The name of the reservation block. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the reservation to list. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To list all reservation sub-blocks in an extended reservation's block
my-block in table form, run:

    $ gcloud compute reservations sub-blocks list extended-reservation \
        --block-name=my-block --zone=us-central1-a --project=my-project

To list the URIs of all reservation blocks in an extended reservation, run:

    $ gcloud compute reservations sub-blocks list extended-reservation \
        --block-name=my-block --zone=us-central1-a \
        --project=my-project --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/sub-blocks/list)

---
### `gcloud compute reservations sub-blocks perform-maintenance`

Perform maintenance on a reservation sub-block

Perform maintenance on a reservation sub-block.

**Synopsis:**
```
gcloud compute reservations sub-blocks perform-maintenance RESERVATION
    --block-name=BLOCK_NAME --sub-block-name=SUB_BLOCK_NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Name of the reservation to perform-maintenance.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--block-name` | BLOCK_NAME |  | The name of the reservation block. |
| `--sub-block-name` | SUB_BLOCK_NAME |  | The name of the reservation sub block. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the reservation to perform-maintenance. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To perform maintenance on a reservation sub-block in reservation exr-1 in
ZONE with block name block-1 and sub-block name sub-block-1, run:

    $ gcloud compute reservations sub-blocks perform-maintenance exr-1 \
        --zone=ZONE --block-name=block-1 --sub-block-name=sub-block-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/sub-blocks/perform-maintenance)

---
### `gcloud compute reservations sub-blocks report-subblock-as-faulty`

Report a sub-block within a reservation as faulty

Report a sub-block within a reservation as faulty.

**Synopsis:**
```
gcloud compute reservations sub-blocks report-subblock-as-faulty
    RESERVATION --block-name=BLOCK_NAME
    --disruption-schedule=DISRUPTION_SCHEDULE
    --failure-component=FAILURE_COMPONENT
    --fault-reasons=[behavior=BEHAVIOR],[description=DESCRIPTION]
    --sub-block-name=SUB_BLOCK_NAME [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   The name of the reservation containing the sub-block to report as
   faulty
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--block-name` | BLOCK_NAME |  | The name of the reservation block. |
| `--disruption-schedule` | DISRUPTION_SCHEDULE |  | The disruption schedule for the sub-block. DISRUPTION_SCHEDULE must be (only one value is supported): IMMEDIATE All VMs are immediately disrupted. |
| `--failure-component` | one of: MULTIPLE_FAULTY_HOSTS Multiple hosts experienced the fault |  | The component that experienced the fault. FAILURE_COMPONENT must be one of: MULTIPLE_FAULTY_HOSTS Multiple hosts experienced the fault. NVLINK_SWITCH The NVLink switch experienced the fault. |
| `--fault-reasons` | [behavior=BEHAVIOR],[description=DESCRIPTION] |  | The reasons for reporting the sub-block as faulty. You can repeat this flag. Each flag must specify a "behavior" attribute and can optionally include a "description" attribute. The possible values for "behavior" are: PERFORMANCE, SWITCH_FAILURE, GPU_ERROR. |
| `--sub-block-name` | SUB_BLOCK_NAME |  | The name of the reservation sub block. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the reservation to report-subblock-as-faulty. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To report reservation exr-1 in ZONE with block name block-1 and sub block
name sub-block-1 as faulty, run:

    $ gcloud compute reservations sub-blocks report-subblock-as-faulty \
        exr-1 --zone=ZONE --block-name=block-1 \
        --sub-block-name=sub-block-1 --disruption-schedule=IMMEDIATE \
        --fault-reasons=behavior=PERFORMANCE,description="performance \
    issues" --failure-component=NVLINK_SWITCH
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/reservations/sub-blocks/report-subblock-as-faulty)

---
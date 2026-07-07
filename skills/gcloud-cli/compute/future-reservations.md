# gcloud compute future-reservations

manage Compute Engine future reservations

### `gcloud compute future-reservations cancel`

Cancel a Compute Engine future reservation

Cancel a Compute Engine future reservation.

**Synopsis:**
```
gcloud compute future-reservations cancel
    (FUTURE_RESERVATION : --zone=ZONE) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Future reservation resource - The name of the future reservation to
cancel. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument future_reservation on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FUTURE_RESERVATION
     ID of the future reservation or fully qualified identifier for the
     future reservation.

     To set the future_reservation attribute:
     + provide the argument future_reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument future_reservation on the command line with
       a fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To cancel a given Compute Engine future reservation, run:

    $ gcloud compute future-reservations cancel my-reservation \
        --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/future-reservations/cancel)

---
### `gcloud compute future-reservations create`

Create a Compute Engine reservation

Create a Compute Engine reservation.

**Synopsis:**
```
gcloud compute future-reservations create FUTURE_RESERVATION
    --[no-]auto-delete-auto-created-reservations
    (--source-instance-template=SOURCE_INSTANCE_TEMPLATE
      | [--machine-type=MACHINE_TYPE
      : --accelerator=[count=COUNT],[type=TYPE]
      --local-ssd=[count=COUNT],[interface=INTERFACE],[size=SIZE]
      --min-cpu-platform=MIN_CPU_PLATFORM] | [--tpu-version=TPU_VERSION
      : --chip-count=CHIP_COUNT --workload-type=WORKLOAD_TYPE])
    (--start-time=START_TIME (--duration=DURATION | --end-time=END_TIME))
    [--deployment-type=DEPLOYMENT_TYPE] [--description=DESCRIPTION]
    [--name-prefix=NAME_PREFIX] [--planning-status=PLANNING_STATUS]
    [--[no-]require-specific-reservation]
    [--reservation-mode=RESERVATION_MODE]
    [--reservation-name=RESERVATION_NAME]
    [--scheduling-type=SCHEDULING_TYPE] [--total-count=TOTAL_COUNT]
    [--zone=ZONE]
    [--auto-created-reservations-delete-time=AUTO_CREATED_RESERVATIONS_DELETE_TIME | --auto-created-reservations-duration=AUTO_CREATED_RESERVATIONS_DURATION]
    [--commitment-name=COMMITMENT_NAME --commitment-plan=COMMITMENT_PLAN
      --previous-commitment-terms=PREVIOUS_COMMITMENT_TERMS]
    [--share-setting=SHARE_SETTING --share-with=PROJECT,[PROJECT,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FUTURE_RESERVATION
   Name of the future reservation to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]auto-delete-auto-created-reservations` |  |  | If specified, the auto-created reservations for a future reservation are deleted at the end time (default) or at a specified delete time. Use --auto-delete-auto-created-reservations to enable and --no-auto-delete-auto-created-reservations to disable. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment-type` | one of: DENSE DENSE mode is for densely deployed reservation blocks |  | The deployment type for the reserved capacity. DEPLOYMENT_TYPE must be one of: DENSE DENSE mode is for densely deployed reservation blocks. FLEXIBLE FLEXIBLE mode is for highly flexible, logical reservation blocks. |
| `--description` | DESCRIPTION |  | An optional description of the future reservation to create. |
| `--name-prefix` | NAME_PREFIX |  | A name prefix for the auto-created reservations when capacity is delivered at the start time. Each auto-created reservation name starts with the name prefix. |
| `--planning-status` | one of: DRAFT Default planning status value |  | The planning status of the future reservation. The default value is DRAFT. While in DRAFT, any changes to the future reservation's properties will be allowed. If set to SUBMITTED, the future reservation will submit and its procurementStatus will change to PENDING_APPROVAL. Once the future reservation is pending approval, changes to the future reservation's properties will not be allowed. PLANNING_STATUS must be one of: DRAFT Default planning status value. SUBMITTED Planning status value to immediately submit the future reservation. |
| `--[no-]require-specific-reservation` |  |  | Indicate whether the auto-created reservations can be consumed by VMs with "any reservation" defined. If enabled, then only VMs that target the auto-created reservation by name using --reservation-affinity=specific can consume from this reservation. Auto-created reservations delivered with this flag enabled will inherit the name of the future reservation. Use --require-specific-reservation to enable and --no-require-specific-reservation to disable. |
| `--reservation-mode` | one of: CALENDAR This indicates to create a future reservation in calendar mode, which is ideal for reserving GPU VMs |  | The mode of the reservation. RESERVATION_MODE must be one of: CALENDAR This indicates to create a future reservation in calendar mode, which is ideal for reserving GPU VMs. The auto-created reservations for the future reservation are automatically deleted at the end of the reservation period. DEFAULT This indicates to create a standard future reservation. If you want to automatically delete the auto-created reservations, then you must use the --auto-delete-auto-created-reservations flag. |
| `--reservation-name` | RESERVATION_NAME |  | Name of reservations where the capacity is provisioned at the time of delivery of future reservations. If the reservation with the given name does not exist already, it is created automatically at the time of Approval with INACTIVE state till specified start-time. Either provide the reservation_name or a name_prefix. |
| `--scheduling-type` | one of: GROUPED In GROUPED mode, maintenance on all reserved instances is synchronized |  | Maintenance for the reserved capacity. SCHEDULING_TYPE must be one of: GROUPED In GROUPED mode, maintenance on all reserved instances is synchronized. INDEPENDENT In INDEPENDENT mode, maintenance is not synchronized for this reservation, and each instance has its own maintenance window. |
| `--total-count` | TOTAL_COUNT |  | The total number of instances for which capacity assurance is requested at a future time period. |
| `--zone` | ZONE |  | Zone of the future reservation to create. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/future-reservations/create)

---
### `gcloud compute future-reservations delete`

Delete a Compute Engine future reservation

Delete a Compute Engine future reservation.

**Synopsis:**
```
gcloud compute future-reservations delete
    (FUTURE_RESERVATION : --zone=ZONE) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Future reservation resource - The name of the future reservation to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument future_reservation on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FUTURE_RESERVATION
     ID of the future reservation or fully qualified identifier for the
     future reservation.

     To set the future_reservation attribute:
     + provide the argument future_reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument future_reservation on the command line with
       a fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a given Compute Engine future reservation, run:

    $ gcloud compute future-reservations delete my-reservation \
        --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/future-reservations/delete)

---
### `gcloud compute future-reservations describe`

Show details about a Compute Engine future reservation

Show details about a Compute Engine future reservation.

**Synopsis:**
```
gcloud compute future-reservations describe
    (FUTURE_RESERVATION : --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Future reservation resource - The name of the future reservation to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument future_reservation on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FUTURE_RESERVATION
     ID of the future reservation or fully qualified identifier for the
     future reservation.

     To set the future_reservation attribute:
     + provide the argument future_reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument future_reservation on the command line with
       a fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To describe a given Compute Engine future reservation, run:

    $ gcloud compute future-reservations describe my-reservation \
        --zone=ZONE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/future-reservations/describe)

---
### `gcloud compute future-reservations list`

List Compute Engine future reservations

List Compute Engine future reservations.

**Synopsis:**
```
gcloud compute future-reservations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Compute Engine future reservations, run:

    $ gcloud compute future-reservations list my-future-reservation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/future-reservations/list)

---
### `gcloud compute future-reservations update`

Update Compute Engine future reservations

Update Compute Engine future reservations.

**Synopsis:**
```
gcloud compute future-reservations update FUTURE_RESERVATION
    [--[no-]auto-delete-auto-created-reservations]
    [--deployment-type=DEPLOYMENT_TYPE] [--description=DESCRIPTION]
    [--[no-]enable-emergent-maintenance]
    [--planning-status=PLANNING_STATUS]
    [--[no-]require-specific-reservation]
    [--reservation-name=RESERVATION_NAME]
    [--scheduling-type=SCHEDULING_TYPE] [--total-count=TOTAL_COUNT]
    [--zone=ZONE]
    [--auto-created-reservations-delete-time=AUTO_CREATED_RESERVATIONS_DELETE_TIME | --auto-created-reservations-duration=AUTO_CREATED_RESERVATIONS_DURATION]
    [--clear-name-prefix | --name-prefix=NAME_PREFIX]
    [--clear-share-settings
      | --share-setting=SHARE_SETTING --share-with=PROJECT,[PROJECT,...]]
    [--commitment-name=COMMITMENT_NAME --commitment-plan=COMMITMENT_PLAN
      --previous-commitment-terms=PREVIOUS_COMMITMENT_TERMS]
    [--machine-type=MACHINE_TYPE --min-cpu-platform=MIN_CPU_PLATFORM
      --accelerator=[count=COUNT],[type=TYPE]
      | --clear-accelerator --clear-local-ssd
      | --local-ssd=[count=COUNT],[interface=INTERFACE],[size=SIZE]]
    [--start-time=START_TIME --duration=DURATION | --end-time=END_TIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FUTURE_RESERVATION
   Name of the future reservation to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]auto-delete-auto-created-reservations` |  |  | If specified, the auto-created reservations for a future reservation are deleted at the end time (default) or at a specified delete time. Use --auto-delete-auto-created-reservations to enable and --no-auto-delete-auto-created-reservations to disable. |
| `--deployment-type` | one of: DENSE DENSE mode is for densely deployed reservation blocks |  | The deployment type for the reserved capacity. DEPLOYMENT_TYPE must be one of: DENSE DENSE mode is for densely deployed reservation blocks. FLEXIBLE FLEXIBLE mode is for highly flexible, logical reservation blocks. |
| `--description` | DESCRIPTION |  | An optional description of the future reservation to create. |
| `--[no-]enable-emergent-maintenance` |  |  | Emergent maintenance flag for the reservation, which enrolls all the underlying vms, hosts and SB infrastructure to receive emergent maintenance notifications in advance. Use --enable-emergent-maintenance to enable and --no-enable-emergent-maintenance to disable. |
| `--planning-status` | one of: DRAFT Default planning status value |  | The planning status of the future reservation. The default value is DRAFT. While in DRAFT, any changes to the future reservation's properties will be allowed. If set to SUBMITTED, the future reservation will submit and its procurementStatus will change to PENDING_APPROVAL. Once the future reservation is pending approval, changes to the future reservation's properties will not be allowed. PLANNING_STATUS must be one of: DRAFT Default planning status value. SUBMITTED Planning status value to immediately submit the future reservation. |
| `--[no-]require-specific-reservation` |  |  | Indicate whether the auto-created reservations can be consumed by VMs with "any reservation" defined. If enabled, then only VMs that target the auto-created reservation by name using --reservation-affinity=specific can consume from this reservation. Auto-created reservations delivered with this flag enabled will inherit the name of the future reservation. Use --require-specific-reservation to enable and --no-require-specific-reservation to disable. |
| `--reservation-name` | RESERVATION_NAME |  | Name of reservations where the capacity is provisioned at the time of delivery of future reservations. If the reservation with the given name does not exist already, it is created automatically at the time of Approval with INACTIVE state till specified start-time. Either provide the reservation_name or a name_prefix. |
| `--scheduling-type` | one of: GROUPED In GROUPED mode, maintenance on all reserved instances is synchronized |  | Maintenance for the reserved capacity. SCHEDULING_TYPE must be one of: GROUPED In GROUPED mode, maintenance on all reserved instances is synchronized. INDEPENDENT In INDEPENDENT mode, maintenance is not synchronized for this reservation, and each instance has its own maintenance window. |
| `--total-count` | TOTAL_COUNT |  | The total number of instances for which capacity assurance is requested at a future time period. |
| `--zone` | ZONE |  | Zone of the future reservation to update. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To update total count, start and end time of a Compute Engine future
reservation in us-central1-a, run:

    $ gcloud compute future-reservations update my-future-reservation \
      --total-count=1000 --start-time=2021-11-10T07:00:00Z \
      --end-time=2021-12-10T07:00:00Z --zone=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/future-reservations/update)

---
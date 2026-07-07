# gcloud bms volumes

manage bare metal volumes in Bare Metal Solution

### `gcloud bms volumes describe`

Describe a Bare Metal Solution volume

Describe a Bare Metal Solution volume.

**Synopsis:**
```
gcloud bms volumes describe (VOLUME : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - volume. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To get a description of an volume called my-volume in project my-project
and region us-central1, run:

    $ gcloud bms volumes describe my-volume --project=my-project \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/describe)

---
### `gcloud bms volumes list`

List Bare Metal Solution volumes in a project

List Bare Metal Solution volumes in a project.

**Synopsis:**
```
gcloud bms volumes list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list volumes within the project in the region us-central1, run:

    $ gcloud bms volumes list --region=us-central1

Or:

To list all volumes in the project, run:

    $ gcloud bms volumes list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/list)

---
### `gcloud bms volumes rename`

Rename a Bare Metal Solution volume

Rename a Bare Metal Solution volume.

**Synopsis:**
```
gcloud bms volumes rename (VOLUME : --region=REGION) --new-name=NEW_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - volume. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-name` | NEW_NAME |  | New volume name for renaming an already existing volume. |


**Examples:**
```bash
To rename a volume my-volume to my-new-volume-name in region us-central1,
run:

    $ gcloud bms volumes rename my-volume \
        --new-name=my-new-volume-name --region=us-central1 \
        --project=bms-example-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/rename)

---
### `gcloud bms volumes restore`

Restore a Bare Metal Solution boot volume from an existing snapshot

Restore a Bare Metal Solution boot volume from an existing snapshot.

**Synopsis:**
```
gcloud bms volumes restore (VOLUME : --region=REGION) --snapshot=SNAPSHOT
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - volume. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshot` | SNAPSHOT |  | Name of the snapshot to restore. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To restore a boot volume named my-boot-volume in region us-central1 from
snapshot named my-snapshot, run:

    $ gcloud bms volumes restore my-boot-volume --region=us-central1 \
        --snapshot=my-snapshot
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/restore)

---
### `gcloud bms volumes snapshot`

Create a snapshot of a Bare Metal Solution boot volume

Create a snapshot of a Bare Metal Solution boot volume.

**Synopsis:**
```
gcloud bms volumes snapshot (VOLUME : --region=REGION)
    --description=DESCRIPTION --snapshot-name=SNAPSHOT_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - volume. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Textual description of the created snapshot. |
| `--snapshot-name` | SNAPSHOT_NAME |  | Name to assign to the created snapshot. |


**Examples:**
```bash
To create a snapshot of a boot volume named my-boot-volume in region
us-central1 with the name my-snapshot and description my-description, run:

    $ gcloud bms volumes snapshot my-boot-volume --region=us-central1 \
        --snapshot-name=my-snapshot --description=my-description
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/snapshot)

---
### `gcloud bms volumes update`

Update a Bare Metal Solution volume

Update a Bare Metal Solution volume.

This call returns immediately, but the update operation may take several
minutes to complete. To check if the operation is complete, use the
describe command for the volume.

**Synopsis:**
```
gcloud bms volumes update (VOLUME : --region=REGION) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Volume resource - volume. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument volume on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VOLUME
     ID of the volume or fully qualified identifier for the volume.

     To set the volume attribute:
     + provide the argument volume on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument volume on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To add the label 'key1=value1' to a policy, run:

    $ gcloud bms volumes update my-volume --update-labels=key1=value1

To clear all labels, run:

    $ gcloud bms volumes update my-volume --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/update)

---

## `gcloud bms volumes luns` — manage bare metal logical unit numbers (LUNs) in Bare Metal Solution
### `gcloud bms volumes luns describe`

Describe a Bare Metal Solution LUN

Describe a Bare Metal Solution logical unit number (LUN).

**Synopsis:**
```
gcloud bms volumes luns describe (LUN : --region=REGION --volume=VOLUME)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Lun resource - lun. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument lun on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  LUN
     ID of the lun or fully qualified identifier for the lun.

     To set the lun attribute:
     + provide the argument lun on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument lun on the command line with a fully
       specified name;
     + provide the argument --region on the command line.

  --volume=VOLUME
     Bare Metal Solution volume.

     To set the volume attribute:
     + provide the argument lun on the command line with a fully
       specified name;
     + provide the argument --volume on the command line.
```

**Examples:**
```bash
To get details about a LUN called my-lun on volume my-volume in region
us-central1, run:

    $ gcloud bms volumes luns describe my-lun --region=us-central1 \
        --volume=my-volume
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/luns/describe)

---
### `gcloud bms volumes luns list`

List Bare Metal Solution LUNs in a project

List Bare Metal Solution logical unit numbers (LUNs) for a volume.

**Synopsis:**
```
gcloud bms volumes luns list (--volume=VOLUME : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--volume` | VOLUME |  | _[This must be specified.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ Region of the resource. To set the region attribute: + provide the argument --volume on the command line with a fully specified name; + provide the argument --region on the command line. |


**Examples:**
```bash
To list all LUNs on volume my-volume in region us-central1, run:

    $ gcloud bms volumes luns list --region=us-central1 \
        --volume=my-volume
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/luns/list)

---

## `gcloud bms volumes snapshots` — manage snapshots for Bare Metal Solution volumes
### `gcloud bms volumes snapshots delete`

Delete a Bare Metal Solution boot volume snapshot

Delete a Bare Metal Solution boot volume snapshot.

**Synopsis:**
```
gcloud bms volumes snapshots delete
    (SNAPSHOT : --region=REGION --volume=VOLUME) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - snapshot. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNAPSHOT
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot attribute:
     + provide the argument snapshot on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --region on the command line.

  --volume=VOLUME
     Bare Metal Solution volume.

     To set the volume attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --volume on the command line.
```

**Examples:**
```bash
To delete a snapshot called my-snapshot on boot volume my-boot-volume in
region us-central1, run:

    $ gcloud bms volumes snapshots delete my-snapshot \
        --region=us-central1 --volume=my-boot-volume
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/snapshots/delete)

---
### `gcloud bms volumes snapshots describe`

Describe a Bare Metal Solution boot volume snapshot

Describe a Bare Metal Solution boot volume snapshot.

**Synopsis:**
```
gcloud bms volumes snapshots describe
    (SNAPSHOT : --region=REGION --volume=VOLUME) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snapshot resource - snapshot. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument snapshot on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNAPSHOT
     ID of the snapshot or fully qualified identifier for the snapshot.

     To set the snapshot attribute:
     + provide the argument snapshot on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --region on the command line.

  --volume=VOLUME
     Bare Metal Solution volume.

     To set the volume attribute:
     + provide the argument snapshot on the command line with a fully
       specified name;
     + provide the argument --volume on the command line.
```

**Examples:**
```bash
To get a description of a snapshot called my-snapshot on boot volume
my-boot-volume in region us-central1, run:

    $ gcloud bms volumes snapshots describe my-snapshot \
        --region=us-central1 --volume=my-boot-volume
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/snapshots/describe)

---
### `gcloud bms volumes snapshots list`

List snapshots for a Bare Metal Solution boot volume

List snapshots for a Bare Metal Solution boot volume.

**Synopsis:**
```
gcloud bms volumes snapshots list (--volume=VOLUME : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--volume` | VOLUME |  | _[This must be specified.]_ ID of the volume or fully qualified identifier for the volume. To set the volume attribute: + provide the argument --volume on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ Region of the resource. To set the region attribute: + provide the argument --volume on the command line with a fully specified name; + provide the argument --region on the command line. |


**Examples:**
```bash
To list snapshots on boot volume my-boot-volume in region us-central1, run:

    $ gcloud bms volumes snapshots list --region=us-central1 \
        --volume=my-boot-volume
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/volumes/snapshots/list)

---
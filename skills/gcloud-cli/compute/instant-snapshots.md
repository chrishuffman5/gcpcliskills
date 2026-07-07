# gcloud compute instant-snapshots

create, list and delete Compute Engine instant snapshots

### `gcloud compute instant-snapshots add-labels`

Add labels to Google Compute Engine instant-snapshotss

gcloud compute instant-snapshots add-labels adds labels to a Google Compute
Engine instant-snapshots.

**Synopsis:**
```
gcloud compute instant-snapshots add-labels INSTANT_SNAPSHOT_NAME
    --labels=[KEY=VALUE,...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANT_SNAPSHOT_NAME
   Name of the instant snapshot to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | A list of labels to add. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instant snapshot to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instant snapshot to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To add key-value pairs k0=v0 and k1=v1 to 'example-instant-snapshots'

    $ gcloud compute instant-snapshots add-labels \
        example-instant-snapshots --labels=k0=v0,k1=v1

Labels can be used to identify the instant-snapshots and to filter them. To
find a instant-snapshots labeled with key-value pair k1, v2

    $ gcloud compute instant-snapshots list --filter='labels.k1:v2'

To list only the labels when describing a resource, use --format

    $ gcloud compute instant-snapshots describe \
        example-instant-snapshots --format='default(labels)'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instant-snapshots/add-labels)

---
### `gcloud compute instant-snapshots create`

Create a Compute Engine instant snapshot

gcloud compute instant-snapshots create creates an instant snapshot of a
disk. Instant snapshots are useful for backing up the disk data.

**Synopsis:**
```
gcloud compute instant-snapshots create INSTANT_SNAPSHOT_NAME
    --source-disk=SOURCE_DISK [--labels=[KEY=VALUE,...]]
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANT_SNAPSHOT_NAME
   Name of the instant snapshot to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-disk` | SOURCE_DISK |  | _[This must be specified.]_ Source disk used to create the instant snapshot. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create an instant snapshot 'my-instant-snap' from a disk 'my-disk' in
zone 'us-east1-a', run:

    $ gcloud compute instant-snapshots create my-instant-snap \
      --source-disk=my-disk --zone=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instant-snapshots/create)

---
### `gcloud compute instant-snapshots delete`

Delete a Compute Engine instant snapshot

gcloud compute instant-snapshots delete deletes a Compute Engine instant
snapshot. A disk can be deleted only if it is not attached to any virtual
machine instances.

**Synopsis:**
```
gcloud compute instant-snapshots delete INSTANT_SNAPSHOT_NAME
    [INSTANT_SNAPSHOT_NAME ...] [--region=REGION | --zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANT_SNAPSHOT_NAME [INSTANT_SNAPSHOT_NAME ...]
   Names of the instant snapshots to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instant snapshots to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instant snapshots to delete. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To delete Compute Engine instant snapshots with the names
'instant-snapshot-1' and 'instant-snapshot-2', run:

    $ gcloud compute instant-snapshots delete instant-snapshot-1 \
        instant-snapshot-2

To list all instant snapshots that were created before a specific date, use
the --filter flag with the gcloud compute instant-snapshots list command.

    $ gcloud compute instant-snapshots list \
        --filter="creationTimestamp<'2017-01-01'"

For more information on how to use --filter with the list command, run $
gcloud topic filters.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instant-snapshots/delete)

---
### `gcloud compute instant-snapshots describe`

Describe a Compute Engine instant snapshot

gcloud compute instant-snapshots describe displays all data associated with
a Compute Engine instant snapshot in a project.

**Synopsis:**
```
gcloud compute instant-snapshots describe INSTANT_SNAPSHOT_NAME
    [--region=REGION | --zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANT_SNAPSHOT_NAME
   Name of the instant snapshot to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the instant snapshot to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--zone` | ZONE |  | _[At most one of these can be specified:]_ Zone of the instant snapshot to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To describe the instant snapshot 'instant-snapshot-1' in zone 'us-east1-a',
run:

    $ gcloud compute instant-snapshots describe instant-snapshot-1 \
      --zone=us-east1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instant-snapshots/describe)

---
### `gcloud compute instant-snapshots list`

List Google Compute Engine instant snapshots

gcloud compute instant-snapshots list displays all Google Compute Engine
instant snapshots in a project.

By default, instant snapshots from all regions and instant snapshots from
all zones are listed. The results can be narrowed down by providing the
--regions or --zones flag.

**Synopsis:**
```
gcloud compute instant-snapshots list [NAME ...]
    [--regexp=REGEXP, -r REGEXP]
    [--regions=[REGION,...] | --zones=[ZONE,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all instant snapshots in a project in table form, run:

    $ gcloud compute instant-snapshots list

To list the URIs of all instant snapshots in a project, run:

    $ gcloud compute instant-snapshots list --uri

To list all instant snapshots in the us-central1 and europe-west1 regions,
given they are regional resources, run:

    $ gcloud compute instant-snapshots list \
        --filter="region:( europe-west1 us-central1 )"

To list all instant snapshots in zones us-central1-b and europe-west1-d,
given they are zonal resources, run:

    $ gcloud compute instant-snapshots list \
        --filter="zone:( europe-west1-d us-central1-b )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/instant-snapshots/list)

---
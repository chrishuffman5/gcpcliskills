# gcloud network-services multicast-group-range-activations

manage Network Services MulticastGroupRangeActivations

### `gcloud network-services multicast-group-range-activations create`

Create a multicast group range activation

Create a multicast group range activation in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-group-range-activations create
    (MULTICAST_GROUP_RANGE_ACTIVATION : --location=LOCATION)
    --multicast-domain-activation=MULTICAST_DOMAIN_ACTIVATION
    --multicast-group-range=MULTICAST_GROUP_RANGE [--async]
    [--description=DESCRIPTION] [--[no-]enable-logging]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range activation resource - Name of the multicast group
range activation to be created. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range_activation on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE_ACTIVATION
     ID of the multicast group range activation or fully qualified
     identifier for the multicast group range activation.

     To set the multicast_group_range_activation attribute:
     + provide the argument multicast_group_range_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicast-domain-activation` | MULTICAST_DOMAIN_ACTIVATION |  | The multicast domain activation to be used. |
| `--multicast-group-range` | MULTICAST_GROUP_RANGE |  | The multicast group range to be used. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group. |
| `--[no-]enable-logging` |  |  | Whether to enable logging for this multicast group range activation. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Create a multicast group range activation with the name
'my-mg-range-activation', multicast-group-range 'path-to-mgr',
multicast-domain-activation 'path-to-mda', and location 'zone'.

    $ gcloud network-services multicast-group-range-activations create \
        my-mg-range-activation --multicast-group-range=path-to-mgr \
        --multicast-domain-activation=path-to-mda --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-range-activations/create)

---
### `gcloud network-services multicast-group-range-activations delete`

Delete a multicast group range activation

Delete a multicast group range activation in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-group-range-activations delete
    (MULTICAST_GROUP_RANGE_ACTIVATION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range activation resource - The multicast group range
activation to delete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range_activation on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE_ACTIVATION
     ID of the multicast group range activation or fully qualified
     identifier for the multicast group range activation.

     To set the multicast_group_range_activation attribute:
     + provide the argument multicast_group_range_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast group range activation in the current project, run:

    $ gcloud network-services multicast-group-range-activations delete \
        my-mg-range-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-range-activations/delete)

---
### `gcloud network-services multicast-group-range-activations describe`

Describe a multicast group range activations

Show details of a multicast group range activation in the specified
location of the current project.

**Synopsis:**
```
gcloud network-services multicast-group-range-activations describe
    (MULTICAST_GROUP_RANGE_ACTIVATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range activation resource - The multicast group range
activation to display. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range_activation on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE_ACTIVATION
     ID of the multicast group range activation or fully qualified
     identifier for the multicast group range activation.

     To set the multicast_group_range_activation attribute:
     + provide the argument multicast_group_range_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe details of a multicast group range activation in the current
project and location, run:

    $ gcloud network-services multicast-group-range-activations \
        describe my-mg-range-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-range-activations/describe)

---
### `gcloud network-services multicast-group-range-activations list`

List multicast group range activations

List all multicast group range activations in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-group-range-activations list
    --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list multicast group range activations in the current project and
location, run:

    $ gcloud network-services multicast-group-range-activations list \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-range-activations/list)

---
### `gcloud network-services multicast-group-range-activations update`

Update a multicast group range activation

Update a multicast group range activation in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-group-range-activations update
    (MULTICAST_GROUP_RANGE_ACTIVATION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--[no-]enable-logging]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range activation resource - Name of the multicast group
range to be updated. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range_activation on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE_ACTIVATION
     ID of the multicast group range activation or fully qualified
     identifier for the multicast group range activation.

     To set the multicast_group_range_activation attribute:
     + provide the argument multicast_group_range_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group range activation. |
| `--[no-]enable-logging` |  |  | Whether to enable logging for this multicast group range activation. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast group range activation with the name
'my-multicast-group-range-activation' and location 'zone'.

    $ gcloud network-services multicast-group-range-activations update \
        my-multicast-group-range-activation --enable-logging \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-range-activations/update)

---
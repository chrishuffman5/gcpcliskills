# gcloud network-services multicast-group-producer-activations

manage Network Services MulticastGroupProducerActivations

### `gcloud network-services multicast-group-producer-activations create`

Create a multicast group producer activation

Create a multicast group producer activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-producer-activations create
    (MULTICAST_GROUP_PRODUCER_ACTIVATION : --location=LOCATION)
    --multicast-producer-association=MULTICAST_PRODUCER_ASSOCIATION
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--multicast-group-range-activation=MULTICAST_GROUP_RANGE_ACTIVATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group producer activation resource - Name of the multicast group
producer activation to be created. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_producer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_PRODUCER_ACTIVATION
     ID of the multicast group producer activation or fully qualified
     identifier for the multicast group producer activation.

     To set the multicast_group_producer_activation attribute:
     + provide the argument multicast_group_producer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_producer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicast-producer-association` | MULTICAST_PRODUCER_ASSOCIATION |  | The multicast producer association to be used. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group producer activation. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--multicast-group-range-activation` | MULTICAST_GROUP_RANGE_ACTIVATION |  | The multicast group range activation to be used. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-producer-activations/create)

---
### `gcloud network-services multicast-group-producer-activations delete`

Delete a multicast group producer activation

Delete a multicast group producer activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-producer-activations delete
    (MULTICAST_GROUP_PRODUCER_ACTIVATION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group producer activation resource - The multicast group
producer activation to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_producer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_PRODUCER_ACTIVATION
     ID of the multicast group producer activation or fully qualified
     identifier for the multicast group producer activation.

     To set the multicast_group_producer_activation attribute:
     + provide the argument multicast_group_producer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_producer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast group producer activation in the current project,
run:

    $ gcloud network-services multicast-group-producer-activations \
        delete my-multicast-group-producer-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-producer-activations/delete)

---
### `gcloud network-services multicast-group-producer-activations describe`

Describe a multicast group producer activation

Show details of a multicastgroup producer activation in the specified
location of the current project.

**Synopsis:**
```
gcloud network-services multicast-group-producer-activations describe
    (MULTICAST_GROUP_PRODUCER_ACTIVATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group producer activation resource - The multicast group
producer activation to display. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_producer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_PRODUCER_ACTIVATION
     ID of the multicast group producer activation or fully qualified
     identifier for the multicast group producer activation.

     To set the multicast_group_producer_activation attribute:
     + provide the argument multicast_group_producer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_producer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe details of a multicast group producer activation in the current
project and location, run:

    $ gcloud network-services multicast-group-producer-activations \
        describe my-multicast-group-producer-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-producer-activations/describe)

---
### `gcloud network-services multicast-group-producer-activations list`

List multicast group producer activations

List all multicast group producer activations in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-producer-activations list
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
To list multicast group producer activations in the current project and
location, run:

    $ gcloud network-services multicast-group-producer-activations \
        list --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-producer-activations/list)

---
### `gcloud network-services multicast-group-producer-activations update`

Update a multicast group producer activation

Update a multicast group producer activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-producer-activations update
    (MULTICAST_GROUP_PRODUCER_ACTIVATION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group producer activation resource - Name of the multicast group
producer activation to be updated. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_producer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_PRODUCER_ACTIVATION
     ID of the multicast group producer activation or fully qualified
     identifier for the multicast group producer activation.

     To set the multicast_group_producer_activation attribute:
     + provide the argument multicast_group_producer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_producer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group producer activation. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast group producer activation with the name my-mgpa and
location zone.

    $ gcloud network-services multicast-group-producer-activations \
        update my-mgpa --description="new description" --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-producer-activations/update)

---
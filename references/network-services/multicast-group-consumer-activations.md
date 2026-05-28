# gcloud network-services multicast-group-consumer-activations

manage Network Services MulticastGroupConsumerActivations

### `gcloud network-services multicast-group-consumer-activations create`

Create a multicast group consumer activation

Create a multicast group consumer activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-consumer-activations create
    (MULTICAST_GROUP_CONSUMER_ACTIVATION : --location=LOCATION)
    --multicast-consumer-association=MULTICAST_CONSUMER_ASSOCIATION
    [--async] [--description=DESCRIPTION] [--[no-]enable-logging]
    [--labels=[KEY=VALUE,...]]
    [--multicast-group-range-activation=MULTICAST_GROUP_RANGE_ACTIVATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group consumer activation resource - Name of the multicast group
consumer activation to be created. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_consumer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_CONSUMER_ACTIVATION
     ID of the multicast group consumer activation or fully qualified
     identifier for the multicast group consumer activation.

     To set the multicast_group_consumer_activation attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicast-consumer-association` | MULTICAST_CONSUMER_ASSOCIATION |  | The multicast consumer association to be used. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group consumer activation. |
| `--[no-]enable-logging` |  |  | Whether to enable logging for this multicast group consumer activation. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--multicast-group-range-activation` | MULTICAST_GROUP_RANGE_ACTIVATION |  | The multicast group range activation to be used. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-consumer-activations/create)

---
### `gcloud network-services multicast-group-consumer-activations delete`

Delete a multicast group consumer activation

Delete a multicast group consumer activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-consumer-activations delete
    (MULTICAST_GROUP_CONSUMER_ACTIVATION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group consumer activation resource - The multicast group
consumer activation to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_consumer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_CONSUMER_ACTIVATION
     ID of the multicast group consumer activation or fully qualified
     identifier for the multicast group consumer activation.

     To set the multicast_group_consumer_activation attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast group consumer activation in the current project,
run:

    $ gcloud network-services multicast-group-consumer-activations \
        delete my-multicast-group-consumer-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-consumer-activations/delete)

---
### `gcloud network-services multicast-group-consumer-activations describe`

Describe a multicast group consumer activation

Show details of a multicast group consumer activation in the specified
location of the current project.

**Synopsis:**
```
gcloud network-services multicast-group-consumer-activations describe
    (MULTICAST_GROUP_CONSUMER_ACTIVATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group consumer activation resource - The multicast group
consumer activation to display. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_consumer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_CONSUMER_ACTIVATION
     ID of the multicast group consumer activation or fully qualified
     identifier for the multicast group consumer activation.

     To set the multicast_group_consumer_activation attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe details of a multicast group consumer activation in the current
project and location, run:

    $ gcloud network-services multicast-group-consumer-activations \
        describe my-multicast-group-consumer-activation --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-consumer-activations/describe)

---
### `gcloud network-services multicast-group-consumer-activations list`

List multicast group consumer activations

List all multicast group consumer activations in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-consumer-activations list
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
To list multicast group consumer activations in the current project and
location, run:

    $ gcloud network-services multicast-group-consumer-activations \
        list --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-consumer-activations/list)

---
### `gcloud network-services multicast-group-consumer-activations update`

Update a multicast group consumer activation

Update a multicast group consumer activation in the specified location of
the current project.

**Synopsis:**
```
gcloud network-services multicast-group-consumer-activations update
    (MULTICAST_GROUP_CONSUMER_ACTIVATION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--[no-]enable-logging]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group consumer activation resource - Name of the multicast group
consumer activation to be updated. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_consumer_activation on the
   command line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_CONSUMER_ACTIVATION
     ID of the multicast group consumer activation or fully qualified
     identifier for the multicast group consumer activation.

     To set the multicast_group_consumer_activation attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_consumer_activation on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group consumer activation. |
| `--[no-]enable-logging` |  |  | Whether to enable logging for this multicast group consumer activation. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast group consumer activation with the name
'my-multicast-group-consumer-activation' and location 'zone'.

    $ gcloud network-services multicast-group-consumer-activations \
        update my-multicast-group-consumer-activation --enable-logging \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-consumer-activations/update)

---
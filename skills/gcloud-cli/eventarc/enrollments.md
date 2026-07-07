# gcloud eventarc enrollments

manage Eventarc enrollments

### `gcloud eventarc enrollments create`

Create an Eventarc enrollment

Create an Eventarc enrollment.

**Synopsis:**
```
gcloud eventarc enrollments create (ENROLLMENT : --location=LOCATION)
    --cel-match=CEL_MATCH --destination-pipeline=DESTINATION_PIPELINE
    (--message-bus=MESSAGE_BUS : --message-bus-project=MESSAGE_BUS_PROJECT)
    [--async] [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Enrollment resource - The enrollment to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument enrollment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENROLLMENT
     ID of the enrollment or fully qualified identifier for the
     enrollment.

     To set the enrollment attribute:
     + provide the argument enrollment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc enrollment, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument enrollment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cel-match` | CEL_MATCH |  | The cel match expression for the enrollment. |
| `--destination-pipeline` | DESTINATION_PIPELINE |  | ID of the destination pipeline or fully qualified identifier for the destination pipeline. To set the pipeline attribute: * provide the argument --destination-pipeline on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a new enrollment my-enrollment in location us-central1 for
message-bus my-message-bus with cel matching expression message.type ==
"google.cloud.pubsub.topic.v1.messagePublished" and destination pipeline
my-pipeline, run:

    $ gcloud eventarc enrollments create my-enrollment \
         --location=us-central1 --message-bus=my-message-bus \
         --cel-match="message.type == \
     'google.cloud.pubsub.topic.v1.messagePublished'" \
         --destination-pipeline=my-pipeline
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/enrollments/create)

---
### `gcloud eventarc enrollments delete`

Delete an Eventarc enrollment

Delete an Eventarc enrollment.

**Synopsis:**
```
gcloud eventarc enrollments delete (ENROLLMENT : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Enrollment resource - Enrollment to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument enrollment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENROLLMENT
     ID of the enrollment or fully qualified identifier for the
     enrollment.

     To set the enrollment attribute:
     + provide the argument enrollment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc enrollment, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument enrollment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the enrollment my-enrollment in location us-central1, run:

    $ gcloud eventarc enrollments delete my-enrollment \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/enrollments/delete)

---
### `gcloud eventarc enrollments describe`

Describe an Eventarc enrollment

Describe an Eventarc enrollment.

**Synopsis:**
```
gcloud eventarc enrollments describe (ENROLLMENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Enrollment resource - Enrollment to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument enrollment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENROLLMENT
     ID of the enrollment or fully qualified identifier for the
     enrollment.

     To set the enrollment attribute:
     + provide the argument enrollment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc enrollment, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument enrollment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the enrollment my-enrollment in location us-central1, run:

    $ gcloud eventarc enrollments describe my-enrollment \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/enrollments/describe)

---
### `gcloud eventarc enrollments list`

List Eventarc enrollments

List Eventarc enrollments.

**Synopsis:**
```
gcloud eventarc enrollments list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |


**Examples:**
```bash
To list all enrollments in location us-central1, run:

    $ gcloud eventarc enrollments list --location=us-central1

To list all enrollments in all locations, run:

    $ gcloud eventarc enrollments list --location=-

or

    $ gcloud eventarc enrollments list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/enrollments/list)

---
### `gcloud eventarc enrollments update`

Update an Eventarc enrollment

Update an Eventarc enrollment.

**Synopsis:**
```
gcloud eventarc enrollments update (ENROLLMENT : --location=LOCATION)
    [--async] [--cel-match=CEL_MATCH]
    [--destination-pipeline=DESTINATION_PIPELINE]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Enrollment resource - The enrollment to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument enrollment on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENROLLMENT
     ID of the enrollment or fully qualified identifier for the
     enrollment.

     To set the enrollment attribute:
     + provide the argument enrollment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc enrollment, which should be one of the
     supported regions. Alternatively, set the [eventarc/location]
     property.

     To set the location attribute:
     + provide the argument enrollment on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--cel-match` | CEL_MATCH |  | The cel match expression for the enrollment. |
| `--destination-pipeline` | DESTINATION_PIPELINE |  | ID of the pipeline or fully qualified identifier for the pipeline. To set the pipeline attribute: * provide the argument --destination-pipeline on the command line. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the enrollment my-enrollment with a new CEL expression
message.type == 'google.cloud.pubsub.topic.v1.messagePublished', run:

    $ gcloud eventarc enrollments update my-enrollment \
         --location=us-central1 \
         --cel-match="message.type == \
     'google.cloud.pubsub.topic.v1.messagePublished'"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/enrollments/update)

---
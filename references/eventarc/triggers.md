# gcloud eventarc triggers

manage Eventarc triggers

### `gcloud eventarc triggers create`

Create an Eventarc trigger

Create an Eventarc trigger.

**Synopsis:**
```
gcloud eventarc triggers create (TRIGGER : --location=LOCATION)
    --event-filters=[ATTRIBUTE=VALUE,...]
    ([--destination-gke-cluster=DESTINATION_GKE_CLUSTER
      --destination-gke-service=DESTINATION_GKE_SERVICE
      : --destination-gke-location=DESTINATION_GKE_LOCATION
      --destination-gke-namespace=DESTINATION_GKE_NAMESPACE
      --destination-gke-path=DESTINATION_GKE_PATH]
      | [--destination-http-endpoint-uri=DESTINATION_HTTP_ENDPOINT_URI
      : --network-attachment=NETWORK_ATTACHMENT]
      | [--destination-run-service=DESTINATION_RUN_SERVICE
      : --destination-run-path=DESTINATION_RUN_PATH
      --destination-run-region=DESTINATION_RUN_REGION]
      | [--destination-workflow=DESTINATION_WORKFLOW
      : --destination-workflow-location=DESTINATION_WORKFLOW_LOCATION])
    [--async] [--channel=CHANNEL]
    [--event-data-content-type=EVENT_DATA_CONTENT_TYPE]
    [--event-filters-path-pattern=[ATTRIBUTE=PATH_PATTERN,...]]
    [--labels=[KEY=VALUE,...]] [--max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--service-account=SERVICE_ACCOUNT] [--transport-topic=TRANSPORT_TOPIC]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - The trigger to create. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument trigger on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument trigger on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc trigger, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument trigger on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--event-filters` | [ATTRIBUTE=VALUE,...] |  | The trigger's list of filters that apply to CloudEvents attributes. This flag can be repeated to add more filters to the list. Only events that match all these filters will be sent to the destination. The filters must include the type attribute, as well as any other attributes that are expected for the chosen type. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--event-data-content-type` | EVENT_DATA_CONTENT_TYPE |  | _[+ provide the argument --channel on the command line.]_ Depending on the event provider, you can specify the encoding of the event data payload that will be delivered to your destination, to either be encoded in application/json or application/protobuf. The default encoding is application/json. Note that for custom sources or third-party providers, or for direct events from Cloud Pub/Sub, this formatting option is not supported. |
| `--event-filters-path-pattern` | [ATTRIBUTE=PATH_PATTERN,...] |  | _[+ provide the argument --channel on the command line.]_ The trigger's list of filters in path pattern format that apply to CloudEvent attributes. This flag can be repeated to add more filters to the list. Only events that match all these filters will be sent to the destination. Currently, path pattern format is only available for the resourceName attribute for Cloud Audit Log events. |
| `--labels` | [KEY=VALUE,...] |  | _[+ provide the argument --channel on the command line.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--service-account` | SERVICE_ACCOUNT |  | _[The maximum number of delivery attempts. The only valid value is 1.]_ The IAM service account email associated with the trigger. |


**Examples:**
```bash
To create a new trigger my-trigger for events of type
google.cloud.pubsub.topic.v1.messagePublished with destination Cloud Run
service my-service, run:

    $ gcloud eventarc triggers create my-trigger \
         --event-filters="type=google.cloud.pubsub.topic.v1.messagePublis\
     hed" --destination-run-service=my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/triggers/create)

---
### `gcloud eventarc triggers delete`

Delete an Eventarc trigger

Delete an Eventarc trigger.

**Synopsis:**
```
gcloud eventarc triggers delete (TRIGGER : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - The trigger to delete. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument trigger on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument trigger on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc trigger, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument trigger on the command line with a fully
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
To delete the trigger my-trigger, run:

    $ gcloud eventarc triggers delete my-trigger
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/triggers/delete)

---
### `gcloud eventarc triggers describe`

Describe an Eventarc trigger

Describe an Eventarc trigger.

**Synopsis:**
```
gcloud eventarc triggers describe (TRIGGER : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - The trigger to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument trigger on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument trigger on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc trigger, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument trigger on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the trigger my-trigger, run:

    $ gcloud eventarc triggers describe my-trigger
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/triggers/describe)

---
### `gcloud eventarc triggers list`

List Eventarc triggers

List Eventarc triggers.

**Synopsis:**
```
gcloud eventarc triggers list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |


**Examples:**
```bash
To list all triggers in location us-central1, run:

    $ gcloud eventarc triggers list --location=us-central1

To list all triggers in all locations, run:

    $ gcloud eventarc triggers list --location=-

or

    $ gcloud eventarc triggers list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/triggers/list)

---
### `gcloud eventarc triggers update`

Update an Eventarc trigger

Update an Eventarc trigger.

**Synopsis:**
```
gcloud eventarc triggers update (TRIGGER : --location=LOCATION) [--async]
    [--event-data-content-type=EVENT_DATA_CONTENT_TYPE]
    [--event-filters=[ATTRIBUTE=VALUE,...]]
    [--event-filters-path-pattern=[ATTRIBUTE=PATH_PATTERN,...]]
    [--max-retry-attempts=MAX_RETRY_ATTEMPTS]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-service-account | --service-account=SERVICE_ACCOUNT]
    [--destination-gke-namespace=DESTINATION_GKE_NAMESPACE
      --destination-gke-service=DESTINATION_GKE_SERVICE
      --clear-destination-gke-path
      | --destination-gke-path=DESTINATION_GKE_PATH
      | --destination-run-region=DESTINATION_RUN_REGION
      --destination-run-service=DESTINATION_RUN_SERVICE
      --clear-destination-run-path
      | --destination-run-path=DESTINATION_RUN_PATH
      | --destination-workflow=DESTINATION_WORKFLOW
      --destination-workflow-location=DESTINATION_WORKFLOW_LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Trigger resource - The trigger to update. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument trigger on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TRIGGER
     ID of the trigger or fully qualified identifier for the trigger.

     To set the trigger attribute:
     + provide the argument trigger on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc trigger, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument trigger on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--event-data-content-type` | EVENT_DATA_CONTENT_TYPE |  | Depending on the event provider, you can specify the encoding of the event data payload that will be delivered to your destination, to either be encoded in application/json or application/protobuf. The default encoding is application/json. Note that for custom sources or third-party providers, or for direct events from Cloud Pub/Sub, this formatting option is not supported. |
| `--event-filters` | [ATTRIBUTE=VALUE,...] |  | The trigger's list of filters that apply to CloudEvents attributes. This flag can be repeated to add more filters to the list. Only events that match all these filters will be sent to the destination. The filters must include the type attribute, as well as any other attributes that are expected for the chosen type. |
| `--event-filters-path-pattern` | [ATTRIBUTE=PATH_PATTERN,...] |  | The trigger's list of filters in path pattern format that apply to CloudEvent attributes. This flag can be repeated to add more filters to the list. Only events that match all these filters will be sent to the destination. Currently, path pattern format is only available for the resourceName attribute for Cloud Audit Log events. |
| `--update-labels` | [KEY=VALUE,...] |  | _[The maximum number of delivery attempts. The only valid value is 1.]_ List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the trigger my-trigger by setting its destination Cloud Run
service to my-service, run:

    $ gcloud eventarc triggers update my-trigger \
         --destination-run-service=my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/triggers/update)

---
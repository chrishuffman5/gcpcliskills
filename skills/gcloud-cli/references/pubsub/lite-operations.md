# gcloud pubsub lite-operations

manage Pub/Sub Lite operations

### `gcloud pubsub lite-operations describe`

Describe a Pub/Sub Lite operation

Describe a Pub/Sub Lite operation.

**Synopsis:**
```
gcloud pubsub lite-operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The Pub/Sub Lite operation to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a Pub/Sub Lite operation, run:

    $ gcloud pubsub lite-operations describe operation-id \
      --location=us-central1-a

Alternatively, specify the full operation name:

    $ gcloud pubsub lite-operations describe \
      projects/my-project/locations/us-central1-a/operations/\
    operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-operations/describe)

---
### `gcloud pubsub lite-operations list`

List Pub/Sub Lite operations

List Pub/Sub Lite operations.

The optional --subscription flag can be used to filter operations for a
Pub/Sub Lite subscription. The optional --done flag can be used to filter
by operation completion status. These flags are ignored if --filter is set.

To describe a listed operation, run:

    $ gcloud pubsub lite-operations list operation-id \
      --location=us-central1-a

**Synopsis:**
```
gcloud pubsub lite-operations list --location=LOCATION [--done=DONE]
    [--subscription=SUBSCRIPTION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--done` | one of: false, true |  | Filter operations by completion status. This flag is ignored if --filter is set. DONE must be one of: false, true. |
| `--subscription` | SUBSCRIPTION |  | Filter operations by target subscription. This flag is ignored if --filter is set. |


**Examples:**
```bash
To list Pub/Sub Lite operations, run:

    $ gcloud pubsub lite-operations list --location=us-central1-a \
      --limit=50

To list incomplete Pub/Sub Lite operations, run:

    $ gcloud pubsub lite-operations list --location=us-central1-a \
      --done=false

To list Pub/Sub Lite operations for a subscription, run:

    $ gcloud pubsub lite-operations list --location=us-central1-a \
      --subscription=my-subscription --limit=50

To list incomplete Pub/Sub Lite operations for a subscription, run:

    $ gcloud pubsub lite-operations list --location=us-central1-a \
      --subscription=my-subscription --done=false
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-operations/list)

---
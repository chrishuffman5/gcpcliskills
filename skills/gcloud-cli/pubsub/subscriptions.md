# gcloud pubsub subscriptions

manage Cloud Pub/Sub subscriptions

### `gcloud pubsub subscriptions ack`

Acknowledges one or more messages on the specified subscription

Acknowledges one or more messages as having been successfully received. If
a delivered message is not acknowledged within the Subscription's ack
deadline, Cloud Pub/Sub will attempt to deliver it again.

To automatically acknowledge messages when pulling from a Subscription, you
can use the --auto-ack flag on gcloud pubsub subscriptions pull.

**Synopsis:**
```
gcloud pubsub subscriptions ack SUBSCRIPTION --ack-ids=[ACK_ID,...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to ACK messages on. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ack-ids` | [ACK_ID,...] |  | One or more ACK_IDs to acknowledge. An ACK_ID is a string that is returned to subscribers (https://cloud.google.com/pubsub/docs/reference/rpc/google.pubsub.v1#google.pubsub.v1.ReceivedMessage). along with the message. The ACK_ID is different from the message ID (https://cloud.google.com/pubsub/docs/reference/rpc/google.pubsub.v1#google.pubsub.v1.PubsubMessage). |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/ack)

---
### `gcloud pubsub subscriptions add-iam-policy-binding`

Add IAM policy binding to a subscription

Add an IAM policy binding to a Cloud Pub/Sub Subscription.

**Synopsis:**
```
gcloud pubsub subscriptions add-iam-policy-binding SUBSCRIPTION
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - The subscription to add the IAM policy binding.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding with the role of 'roles/editor' for the user
'test-user@example.com' on the subscription 'my-subscription', run:

    $ gcloud pubsub subscriptions add-iam-policy-binding \
        my-subscription --member='user:test-user@example.com' \
        --role='roles/editor'

To add an IAM policy binding with the role of 'roles/editor' for the
service account 'my-iam-account@my-project.iam.gserviceaccount.com' on the
subscription 'my-subscription', run:

    $ gcloud pubsub subscriptions add-iam-policy-binding \
        my-subscription \
        --member='serviceAccount:my-iam-account@my-project.iam.gservicea\
    ccount.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/add-iam-policy-binding)

---
### `gcloud pubsub subscriptions create`

Creates one or more Cloud Pub/Sub subscriptions

Creates one or more Cloud Pub/Sub subscriptions for a given topic. The new
subscription defaults to a PULL subscription unless a push endpoint is
specified.

**Synopsis:**
```
gcloud pubsub subscriptions create SUBSCRIPTION [SUBSCRIPTION ...]
    (--topic=TOPIC : --topic-project=TOPIC_PROJECT)
    [--ack-deadline=ACK_DEADLINE] [--enable-exactly-once-delivery]
    [--enable-message-ordering] [--expiration-period=EXPIRATION_PERIOD]
    [--labels=[KEY=VALUE,...]] [--message-filter=MESSAGE_FILTER]
    [--message-retention-duration=MESSAGE_RETENTION_DURATION]
    [--message-transforms-file=MESSAGE_TRANSFORMS_FILE]
    [--retain-acked-messages] [--tags=[KEY=VALUE,...]]
    [[--bigquery-table=BIGQUERY_TABLE
      : --bigquery-service-account-email=BIGQUERY_SERVICE_ACCOUNT_EMAIL
      --drop-unknown-fields --write-metadata --use-table-schema
      | --use-topic-schema] | [--cloud-storage-bucket=CLOUD_STORAGE_BUCKET
      : --cloud-storage-file-datetime-format=CLOUD_STORAGE_FILE_DATETIME_FORMAT --cloud-storage-file-prefix=CLOUD_STORAGE_FILE_PREFIX --cloud-storage-file-suffix=CLOUD_STORAGE_FILE_SUFFIX --cloud-storage-max-bytes=CLOUD_STORAGE_MAX_BYTES --cloud-storage-max-duration=CLOUD_STORAGE_MAX_DURATION --cloud-storage-max-messages=CLOUD_STORAGE_MAX_MESSAGES --cloud-storage-output-format=OUTPUT_FORMAT; default="text" --cloud-storage-service-account-email=CLOUD_STORAGE_SERVICE_ACCOUNT_EMAIL --cloud-storage-use-topic-schema --cloud-storage-write-metadata]]
    [--max-delivery-attempts=MAX_DELIVERY_ATTEMPTS
      [--dead-letter-topic=DEAD_LETTER_TOPIC
      : --dead-letter-topic-project=DEAD_LETTER_TOPIC_PROJECT]]
    [--max-retry-delay=MAX_RETRY_DELAY --min-retry-delay=MIN_RETRY_DELAY]
    [--push-auth-service-account=SERVICE_ACCOUNT_EMAIL
      --push-auth-token-audience=OPTIONAL_AUDIENCE_OVERRIDE
      --push-endpoint=PUSH_ENDPOINT [--push-no-wrapper
      : --push-no-wrapper-write-metadata]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - One or more subscriptions to create. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION [SUBSCRIPTION ...]
     IDs of the subscriptions or fully qualified identifiers for the
     subscriptions.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--topic` | TOPIC |  | _[This must be specified.]_ ID of the topic or fully qualified identifier for the topic. To set the topic attribute: + provide the argument --topic on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--topic-project` | TOPIC_PROJECT |  | _[This must be specified.]_ Project ID of the Google Cloud project for the topic. To set the project attribute: + provide the argument --topic on the command line with a fully specified name; + provide the argument --topic-project on the command line; + provide the argument --project on the command line; + set the property core/project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ack-deadline` | ACK_DEADLINE |  | The number of seconds the system will wait for a subscriber to acknowledge receiving a message before re-attempting delivery. |
| `--enable-exactly-once-delivery` |  |  | Whether or not to enable exactly-once delivery on the subscription. If true, Pub/Sub provides the following guarantees for the delivery of a message with a given value of message_id on this subscription: The message sent to a subscriber is guaranteed not to be resent before the message's acknowledgment deadline expires. An acknowledged message will not be resent to a subscriber. Use --no-enable-exactly-once-delivery to disable this flag. |
| `--enable-message-ordering` |  |  | Whether to receive messages with the same ordering key in order. If set, messages with the same ordering key are sent to subscribers in the order that Pub/Sub receives them. Use --no-enable-message-ordering to disable this flag. |
| `--expiration-period` | EXPIRATION_PERIOD |  | The subscription will expire if it is inactive for the given period. Valid values are strings of the form INTEGER[UNIT], where UNIT is one of "s", "m", "h", and "d" for seconds, minutes, hours, and days, respectively. If the unit is omitted, seconds is assumed. This flag additionally accepts the special value "never" to indicate that the subscription will never expire. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--message-filter` | MESSAGE_FILTER |  | Expression to filter messages. If set, Pub/Sub only delivers the messages that match the filter. The expression must be a non-empty string in the Pub/Sub filtering language (https://cloud.google.com/pubsub/docs/filtering). |
| `--message-retention-duration` | MESSAGE_RETENTION_DURATION |  | How long to retain unacknowledged messages in the subscription's backlog, from the moment a message is published. If --retain-acked-messages is true, this also configures the retention of acknowledged messages. The default value is 7 days, the minimum is 10 minutes, and the maximum is 31 days. Valid values are strings of the form INTEGER[UNIT], where UNIT is one of "s", "m", "h", and "d" for seconds, minutes, hours, and days, respectively. If the unit is omitted, seconds is assumed. |
| `--message-transforms-file` | MESSAGE_TRANSFORMS_FILE |  | Path to YAML or JSON file containing message transforms. |
| `--retain-acked-messages` |  |  | Whether or not to retain acknowledged messages. If true, messages are not expunged from the subscription's backlog until they fall out of the --message-retention-duration window. Acknowledged messages are not retained by default. Use --no-retain-acked-messages to disable this flag. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/create)

---
### `gcloud pubsub subscriptions delete`

Deletes one or more Cloud Pub/Sub subscriptions

Deletes one or more Cloud Pub/Sub subscriptions.

**Synopsis:**
```
gcloud pubsub subscriptions delete SUBSCRIPTION [SUBSCRIPTION ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - One or more subscriptions to delete. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION [SUBSCRIPTION ...]
     IDs of the subscriptions or fully qualified identifiers for the
     subscriptions.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/delete)

---
### `gcloud pubsub subscriptions describe`

Describes a Cloud Pub/Sub subscription

Describes a Cloud Pub/Sub subscription.

**Synopsis:**
```
gcloud pubsub subscriptions describe SUBSCRIPTION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/describe)

---
### `gcloud pubsub subscriptions get-iam-policy`

Get the IAM policy for a Cloud Pub/Sub Subscription

Get the IAM policy for a Cloud Pub/Sub Subscription.

**Synopsis:**
```
gcloud pubsub subscriptions get-iam-policy SUBSCRIPTION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to get the IAM policy of.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given subscription, run:

    $ gcloud pubsub subscriptions get-iam-policy my-subscription
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/get-iam-policy)

---
### `gcloud pubsub subscriptions list`

Lists Cloud Pub/Sub subscriptions

Lists all of the Cloud Pub/Sub subscriptions that exist in a given project.

**Synopsis:**
```
gcloud pubsub subscriptions list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/list)

---
### `gcloud pubsub subscriptions modify-message-ack-deadline`

Modifies the ACK deadline for a specific Cloud Pub/Sub message

This method is useful to indicate that more time is needed to process a
message by the subscriber, or to make the message available for redelivery
if the processing was interrupted.

**Synopsis:**
```
gcloud pubsub subscriptions modify-message-ack-deadline SUBSCRIPTION
    --ack-deadline=ACK_DEADLINE --ack-ids=[ACK_ID,...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription messages belong to. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ack-deadline` | ACK_DEADLINE |  | The number of seconds the system will wait for a subscriber to acknowledge receiving a message before re-attempting delivery. |
| `--ack-ids` | [ACK_ID,...] |  | One or more ACK_IDs to modify the deadline for. An ACK_ID is a string that is returned to subscribers (https://cloud.google.com/pubsub/docs/reference/rpc/google.pubsub.v1#google.pubsub.v1.ReceivedMessage). along with the message. The ACK_ID is different from the message ID (https://cloud.google.com/pubsub/docs/reference/rpc/google.pubsub.v1#google.pubsub.v1.PubsubMessage). |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/modify-message-ack-deadline)

---
### `gcloud pubsub subscriptions modify-push-config`

Modifies the push configuration of a Cloud Pub/Sub subscription

Modifies the push configuration of a Cloud Pub/Sub subscription.

**Synopsis:**
```
gcloud pubsub subscriptions modify-push-config SUBSCRIPTION
    --push-endpoint=PUSH_ENDPOINT
    [--push-auth-service-account=SERVICE_ACCOUNT_EMAIL]
    [--push-auth-token-audience=OPTIONAL_AUDIENCE_OVERRIDE]
    [--push-no-wrapper : --push-no-wrapper-write-metadata]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to modify. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--push-endpoint` | PUSH_ENDPOINT |  | A URL to use as the endpoint for this subscription. This will also automatically set the subscription type to PUSH. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--push-auth-service-account` | SERVICE_ACCOUNT_EMAIL |  | Service account email used as the identity for the generated Open ID Connect token for authenticated push. |
| `--push-auth-token-audience` | OPTIONAL_AUDIENCE_OVERRIDE |  | Audience used in the generated Open ID Connect token for authenticated push. If not specified, it will be set to the push-endpoint. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/modify-push-config)

---
### `gcloud pubsub subscriptions pull`

Pulls one or more Cloud Pub/Sub messages from a subscription

Returns one or more messages from the specified Cloud Pub/Sub subscription,
if there are any messages enqueued.

By default, this command returns only one message from the subscription.
Use the --limit flag to specify the max messages to return.

Please note that this command is not guaranteed to return all the messages
in your backlog or the maximum specified in the --limit argument. Receiving
fewer messages than available occasionally is normal.

**Synopsis:**
```
gcloud pubsub subscriptions pull SUBSCRIPTION [--auto-ack]
    [--filter=EXPRESSION] [--limit=LIMIT; default=1]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to pull messages from.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--auto-ack` |  |  | Automatically ACK every message pulled from this subscription. Use --no-auto-ack to disable this flag. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/pull)

---
### `gcloud pubsub subscriptions remove-iam-policy-binding`

Remove IAM policy binding of a subscription

Remove an IAM policy binding of a Cloud Pub/Sub Subscription.

**Synopsis:**
```
gcloud pubsub subscriptions remove-iam-policy-binding SUBSCRIPTION
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - The subscription to remove the IAM policy binding
from. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To Remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with subscription 'my-subscription', run:

    $ gcloud pubsub subscriptions remove-iam-policy-binding \
        my-subscription --member='user:test-user@gmail.com' \
        --role='roles/editor'

The following command will remove an IAM policy binding for the role of
'roles/editor' from all authenticated users on subscription
'my-subscription':

    $ gcloud pubsub subscriptions remove-iam-policy-binding \
        my-subscription --member='allAuthenticatedUsers' \
        --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/remove-iam-policy-binding)

---
### `gcloud pubsub subscriptions seek`

Resets a subscription's backlog to a point in time or to a given snapshot

Resets a subscription's backlog to a point in time or to a given snapshot.

**Synopsis:**
```
gcloud pubsub subscriptions seek SUBSCRIPTION
    (--snapshot=SNAPSHOT | --time=TIME)
    [--snapshot-project=SNAPSHOT_PROJECT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to affect. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshot` | SNAPSHOT |  | _[Exactly one of these must be specified:]_ The name of the snapshot. The snapshot's topic must be the same as that of the subscription. |
| `--time` | TIME |  | _[Exactly one of these must be specified:]_ The time to seek to. Messages in the subscription that were published before this time are marked as acknowledged, and messages retained in the subscription that were published after this time are marked as unacknowledged. See $ gcloud topic datetimes for information on time formats. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snapshot-project` | SNAPSHOT_PROJECT |  | The name of the project the snapshot belongs to (if seeking to a snapshot). If not set, it defaults to the currently selected cloud project. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/seek)

---
### `gcloud pubsub subscriptions set-iam-policy`

Set IAM policy for a subscription

Set the IAM policy for a Cloud Pub/Sub Subscription.

**Synopsis:**
```
gcloud pubsub subscriptions set-iam-policy SUBSCRIPTION POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to set an IAM policy on.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.

POLICY_FILE
   JSON or YAML file with the IAM policy
```

**Examples:**
```bash
The following command will read an IAM policy from 'policy.json' and set it
for a subscription with 'my-subscription' as the identifier:

    $ gcloud pubsub subscriptions set-iam-policy my-subscription \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/set-iam-policy)

---
### `gcloud pubsub subscriptions update`

Updates an existing Cloud Pub/Sub subscription

Updates an existing Cloud Pub/Sub subscription.

**Synopsis:**
```
gcloud pubsub subscriptions update SUBSCRIPTION
    [--ack-deadline=ACK_DEADLINE] [--enable-exactly-once-delivery]
    [--expiration-period=EXPIRATION_PERIOD]
    [--message-retention-duration=MESSAGE_RETENTION_DURATION]
    [--retain-acked-messages] [--update-labels=[KEY=VALUE,...]]
    [--clear-bigquery-config | [--bigquery-table=BIGQUERY_TABLE
      : --bigquery-service-account-email=BIGQUERY_SERVICE_ACCOUNT_EMAIL
      --drop-unknown-fields --write-metadata --use-table-schema
      | --use-topic-schema] | --clear-cloud-storage-config
      | [--cloud-storage-bucket=CLOUD_STORAGE_BUCKET
      : --cloud-storage-file-datetime-format=CLOUD_STORAGE_FILE_DATETIME_FORMAT --cloud-storage-file-prefix=CLOUD_STORAGE_FILE_PREFIX --cloud-storage-file-suffix=CLOUD_STORAGE_FILE_SUFFIX --cloud-storage-max-bytes=CLOUD_STORAGE_MAX_BYTES --cloud-storage-max-duration=CLOUD_STORAGE_MAX_DURATION --cloud-storage-max-messages=CLOUD_STORAGE_MAX_MESSAGES --cloud-storage-output-format=OUTPUT_FORMAT; default="text" --cloud-storage-service-account-email=CLOUD_STORAGE_SERVICE_ACCOUNT_EMAIL --cloud-storage-use-topic-schema --cloud-storage-write-metadata]]
    [--clear-dead-letter-policy
      | --max-delivery-attempts=MAX_DELIVERY_ATTEMPTS
      [--dead-letter-topic=DEAD_LETTER_TOPIC
      : --dead-letter-topic-project=DEAD_LETTER_TOPIC_PROJECT]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-message-transforms
      | --message-transforms-file=MESSAGE_TRANSFORMS_FILE]
    [--clear-retry-policy | --max-retry-delay=MAX_RETRY_DELAY
      --min-retry-delay=MIN_RETRY_DELAY]
    [--push-auth-service-account=SERVICE_ACCOUNT_EMAIL
      --push-auth-token-audience=OPTIONAL_AUDIENCE_OVERRIDE
      --push-endpoint=PUSH_ENDPOINT --clear-push-no-wrapper-config
      | [--push-no-wrapper : --push-no-wrapper-write-metadata]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - Name of the subscription to update. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument subscription on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBSCRIPTION
     ID of the subscription or fully qualified identifier for the
     subscription.

     To set the subscription attribute:
     + provide the argument subscription on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ack-deadline` | ACK_DEADLINE |  | The number of seconds the system will wait for a subscriber to acknowledge receiving a message before re-attempting delivery. |
| `--enable-exactly-once-delivery` |  |  | Whether or not to enable exactly-once delivery on the subscription. If true, Pub/Sub provides the following guarantees for the delivery of a message with a given value of message_id on this subscription: The message sent to a subscriber is guaranteed not to be resent before the message's acknowledgment deadline expires. An acknowledged message will not be resent to a subscriber. Use --no-enable-exactly-once-delivery to disable this flag. |
| `--expiration-period` | EXPIRATION_PERIOD |  | The subscription will expire if it is inactive for the given period. Valid values are strings of the form INTEGER[UNIT], where UNIT is one of "s", "m", "h", and "d" for seconds, minutes, hours, and days, respectively. If the unit is omitted, seconds is assumed. This flag additionally accepts the special value "never" to indicate that the subscription will never expire. |
| `--message-retention-duration` | MESSAGE_RETENTION_DURATION |  | How long to retain unacknowledged messages in the subscription's backlog, from the moment a message is published. If --retain-acked-messages is true, this also configures the retention of acknowledged messages. Specify "default" to use the default value of 7 days. The minimum is 10 minutes, and the maximum is 31 days. Valid values are strings of the form INTEGER[UNIT], where UNIT is one of "s", "m", "h", and "d" for seconds, minutes, hours, and days, respectively. If the unit is omitted, seconds is assumed. |
| `--retain-acked-messages` |  |  | Whether or not to retain acknowledged messages. If true, messages are not expunged from the subscription's backlog until they fall out of the --message-retention-duration window. Acknowledged messages are not retained by default. Use --no-retain-acked-messages to disable this flag. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/subscriptions/update)

---
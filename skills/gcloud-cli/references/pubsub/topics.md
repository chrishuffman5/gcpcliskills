# gcloud pubsub topics

manage Cloud Pub/Sub topics

### `gcloud pubsub topics add-iam-policy-binding`

Add IAM policy binding to a topic

Add an IAM policy binding to a Cloud Pub/Sub Topic.

**Synopsis:**
```
gcloud pubsub topics add-iam-policy-binding TOPIC --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - The topic to add the IAM policy binding. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding with the role of 'roles/editor' for the user
'test-user@example.com' on the topic 'my-topic', run:

    $ gcloud pubsub topics add-iam-policy-binding my-topic \
        --member='user:test-user@example.com' --role='roles/editor'

To add an IAM policy binding with the role of 'roles/editor' for the
service account 'my-iam-account@my-project.iam.gserviceaccount.com' on the
topic 'my-topic', run:

    $ gcloud pubsub topics add-iam-policy-binding my-topic \
        --member='serviceAccount:my-iam-account@my-project.iam.gservicea\
    ccount.com' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/add-iam-policy-binding)

---
### `gcloud pubsub topics create`

Creates one or more Cloud Pub/Sub topics

Creates one or more Cloud Pub/Sub topics.

**Synopsis:**
```
gcloud pubsub topics create TOPIC [TOPIC ...] [--labels=[KEY=VALUE,...]]
    [--message-retention-duration=MESSAGE_RETENTION_DURATION]
    [--message-transforms-file=MESSAGE_TRANSFORMS_FILE]
    [--tags=[KEY=VALUE,...]]
    [--ingestion-log-severity=INGESTION_LOG_SEVERITY
      --aws-msk-ingestion-aws-role-arn=AWS_MSK_INGESTION_AWS_ROLE_ARN
      --aws-msk-ingestion-cluster-arn=AWS_MSK_INGESTION_CLUSTER_ARN
      --aws-msk-ingestion-service-account=AWS_MSK_INGESTION_SERVICE_ACCOUNT
      --aws-msk-ingestion-topic=AWS_MSK_INGESTION_TOPIC
      | --azure-event-hubs-ingestion-client-id=AZURE_EVENT_HUBS_INGESTION_CLIENT_ID --azure-event-hubs-ingestion-event-hub=AZURE_EVENT_HUBS_INGESTION_EVENT_HUB --azure-event-hubs-ingestion-namespace=AZURE_EVENT_HUBS_INGESTION_NAMESPACE --azure-event-hubs-ingestion-resource-group=AZURE_EVENT_HUBS_INGESTION_RESOURCE_GROUP --azure-event-hubs-ingestion-service-account=AZURE_EVENT_HUBS_INGESTION_SERVICE_ACCOUNT --azure-event-hubs-ingestion-subscription-id=AZURE_EVENT_HUBS_INGESTION_SUBSCRIPTION_ID --azure-event-hubs-ingestion-tenant-id=AZURE_EVENT_HUBS_INGESTION_TENANT_ID | [--cloud-storage-ingestion-bucket=CLOUD_STORAGE_INGESTION_BUCKET --cloud-storage-ingestion-input-format=INPUT_FORMAT : --cloud-storage-ingestion-text-delimiter=CLOUD_STORAGE_INGESTION_TEXT_DELIMITER --cloud-storage-ingestion-minimum-object-create-time=CLOUD_STORAGE_INGESTION_MINIMUM_OBJECT_CREATE_TIME --cloud-storage-ingestion-match-glob=CLOUD_STORAGE_INGESTION_MATCH_GLOB] | --confluent-cloud-ingestion-bootstrap-server=CONFLUENT_CLOUD_INGESTION_BOOTSTRAP_SERVER --confluent-cloud-ingestion-cluster-id=CONFLUENT_CLOUD_INGESTION_CLUSTER_ID --confluent-cloud-ingestion-identity-pool-id=CONFLUENT_CLOUD_INGESTION_IDENTITY_POOL_ID --confluent-cloud-ingestion-service-account=CONFLUENT_CLOUD_INGESTION_SERVICE_ACCOUNT --confluent-cloud-ingestion-topic=CONFLUENT_CLOUD_INGESTION_TOPIC | --kinesis-ingestion-consumer-arn=KINESIS_INGESTION_CONSUMER_ARN --kinesis-ingestion-role-arn=KINESIS_INGESTION_ROLE_ARN --kinesis-ingestion-service-account=KINESIS_INGESTION_SERVICE_ACCOUNT --kinesis-ingestion-stream-arn=KINESIS_INGESTION_STREAM_ARN]
    [--message-encoding=ENCODING (--schema=SCHEMA
      : --schema-project=SCHEMA_PROJECT)
      : --first-revision-id=FIRST_REVISION_ID
      --last-revision-id=LAST_REVISION_ID]
    [--message-storage-policy-allowed-regions=[REGION,...]
      : --message-storage-policy-enforce-in-transit]
    [--topic-encryption-key=TOPIC_ENCRYPTION_KEY
      : --topic-encryption-key-keyring=TOPIC_ENCRYPTION_KEY_KEYRING
      --topic-encryption-key-location=TOPIC_ENCRYPTION_KEY_LOCATION
      --topic-encryption-key-project=TOPIC_ENCRYPTION_KEY_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - One or more topics to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC [TOPIC ...]
     IDs of the topics or fully qualified identifiers for the topics.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--message-retention-duration` | MESSAGE_RETENTION_DURATION |  | Indicates the minimum duration to retain a message after it is published to the topic. If this field is set, messages published to the topic in the last MESSAGE_RETENTION_DURATION are always available to subscribers. For instance, it allows any attached subscription to seek to a timestamp that is up to MESSAGE_RETENTION_DURATION in the past. If this field is not set, message retention is controlled by settings on individual subscriptions. The minimum is 10 minutes and the maximum is 31 days. Valid values are strings of the form INTEGER[UNIT], where UNIT is one of "s", "m", "h", and "d" for seconds, minutes, hours, and days, respectively. If the unit is omitted, seconds is assumed. |
| `--message-transforms-file` | MESSAGE_TRANSFORMS_FILE |  | Path to YAML or JSON file containing message transforms. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


**Examples:**
```bash
To create a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics create mytopic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/create)

---
### `gcloud pubsub topics delete`

Deletes one or more Cloud Pub/Sub topics

Deletes one or more Cloud Pub/Sub topics.

**Synopsis:**
```
gcloud pubsub topics delete TOPIC [TOPIC ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - One or more topics to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC [TOPIC ...]
     IDs of the topics or fully qualified identifiers for the topics.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Examples:**
```bash
To delete a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics delete mytopic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/delete)

---
### `gcloud pubsub topics describe`

Describes a Cloud Pub/Sub topic

Describes a Cloud Pub/Sub topic.

**Synopsis:**
```
gcloud pubsub topics describe TOPIC [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Name of the topic to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/describe)

---
### `gcloud pubsub topics detach-subscription`

Detaches one or more Cloud Pub/Sub subscriptions

Detaches one or more Cloud Pub/Sub subscriptions.

**Synopsis:**
```
gcloud pubsub topics detach-subscription SUBSCRIPTION [SUBSCRIPTION ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subscription resource - One or more subscriptions to detach. This
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

**Examples:**
```bash
To detach a Cloud Pub/Sub subscription, run:

    $ gcloud pubsub topics detach-subscription mysubscription
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/detach-subscription)

---
### `gcloud pubsub topics get-iam-policy`

Get the IAM policy for a Cloud Pub/Sub Topic

Get the IAM policy for a Cloud Pub/Sub Topic.

**Synopsis:**
```
gcloud pubsub topics get-iam-policy TOPIC [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Name of the topic to get the IAM policy of. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given topic, run:

    $ gcloud pubsub topics get-iam-policy my-topic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/get-iam-policy)

---
### `gcloud pubsub topics list`

Lists Cloud Pub/Sub topics within a project

Lists all of the Cloud Pub/Sub topics that exist in a given project that
match the given topic name filter.

**Synopsis:**
```
gcloud pubsub topics list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To filter results by topic name (ie. only show topic 'my-topic'), run:

    $ gcloud pubsub topics list --filter="name.scope(topic):'my-topic'"

To combine multiple filters (with AND or OR), run:

    $ gcloud pubsub topics list \
        --filter="name.scope(topic):'my-topic' OR \
    name.scope(topic):'my-other-topic'"

To filter topics that match an expression:

    $ gcloud pubsub topics list --filter="name.scope(topic):'my-topic_*'"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/list)

---
### `gcloud pubsub topics list-subscriptions`

Lists Cloud Pub/Sub subscriptions from a given topic

Lists all of the Cloud Pub/Sub subscriptions attached to the given topic
and that match the given filter.

**Synopsis:**
```
gcloud pubsub topics list-subscriptions TOPIC [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Name of the topic to list subscriptions for. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Examples:**
```bash
To filter results by subscription name (ie. only show subscription
'mysubs'), run:

    $ gcloud pubsub topics list-subscriptions mytopic --filter=mysubs

To combine multiple filters (with AND or OR), run:

    $ gcloud pubsub topics list-subscriptions mytopic \
        --filter="mysubs1 OR mysubs2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/list-subscriptions)

---
### `gcloud pubsub topics publish`

Publishes a message to the specified topic

Publishes a message to the specified topic name for testing and
troubleshooting. Use with caution: all associated subscribers must be able
to consume and acknowledge any message you publish, otherwise the system
will continuously re-attempt delivery of the bad message for 7 days.

**Synopsis:**
```
gcloud pubsub topics publish TOPIC [--attribute=[ATTRIBUTE,...]]
    [--message=MESSAGE] [--ordering-key=ORDERING_KEY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Name of the topic to publish messages to. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute` | [ATTRIBUTE,...] |  | Comma-separated list of attributes. Each ATTRIBUTE has the form name="value". You can specify up to 100 attributes. |
| `--message` | MESSAGE |  | The body of the message to publish to the given topic name. Information on message formatting and size limits can be found at: https://cloud.google.com/pubsub/docs/publisher#publish |
| `--ordering-key` | ORDERING_KEY |  | The key for ordering delivery to subscribers. All messages with the same ordering key are sent to subscribers in the order that Pub/Sub receives them. |


**Examples:**
```bash
To publish messages in a batch to a specific Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics publish mytopic --message="Hello World!" \
        --attribute=KEY1=VAL1,KEY2=VAL2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/publish)

---
### `gcloud pubsub topics remove-iam-policy-binding`

Remove IAM policy binding of a topic

Remove an IAM policy binding of a Cloud Pub/Sub Topic.

**Synopsis:**
```
gcloud pubsub topics remove-iam-policy-binding TOPIC --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - The topic to remove the IAM policy binding from. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To Remove an IAM policy binding for the role of 'roles/editor' for the user
'test-user@gmail.com' with topic 'my-topic', run:

    $ gcloud pubsub topics remove-iam-policy-binding my-topic \
        --member='user:test-user@gmail.com' --role='roles/editor'

The following command will remove an IAM policy binding for the role of
'roles/editor' from all authenticated users on topic 'my-topic':

    $ gcloud pubsub topics remove-iam-policy-binding my-topic \
        --member='allAuthenticatedUsers' --role='roles/editor'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/remove-iam-policy-binding)

---
### `gcloud pubsub topics set-iam-policy`

Set IAM policy for a topic

Set the IAM policy for a Cloud Pub/Sub Topic.

**Synopsis:**
```
gcloud pubsub topics set-iam-policy TOPIC POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Name of the topic to set an IAM policy on. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.

POLICY_FILE
   JSON or YAML file with the IAM policy
```

**Examples:**
```bash
The following command will read an IAM policy from 'policy.json' and set it
for a topic with 'my-topic' as the identifier:

    $ gcloud pubsub topics set-iam-policy my-topic policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/set-iam-policy)

---
### `gcloud pubsub topics update`

Updates an existing Cloud Pub/Sub topic

Updates an existing Cloud Pub/Sub topic.

**Synopsis:**
```
gcloud pubsub topics update TOPIC [--update-labels=[KEY=VALUE,...]]
    [--clear-ingestion-data-source-settings
      | --ingestion-log-severity=INGESTION_LOG_SEVERITY
      --aws-msk-ingestion-aws-role-arn=AWS_MSK_INGESTION_AWS_ROLE_ARN
      --aws-msk-ingestion-cluster-arn=AWS_MSK_INGESTION_CLUSTER_ARN
      --aws-msk-ingestion-service-account=AWS_MSK_INGESTION_SERVICE_ACCOUNT
      --aws-msk-ingestion-topic=AWS_MSK_INGESTION_TOPIC
      | --azure-event-hubs-ingestion-client-id=AZURE_EVENT_HUBS_INGESTION_CLIENT_ID --azure-event-hubs-ingestion-event-hub=AZURE_EVENT_HUBS_INGESTION_EVENT_HUB --azure-event-hubs-ingestion-namespace=AZURE_EVENT_HUBS_INGESTION_NAMESPACE --azure-event-hubs-ingestion-resource-group=AZURE_EVENT_HUBS_INGESTION_RESOURCE_GROUP --azure-event-hubs-ingestion-service-account=AZURE_EVENT_HUBS_INGESTION_SERVICE_ACCOUNT --azure-event-hubs-ingestion-subscription-id=AZURE_EVENT_HUBS_INGESTION_SUBSCRIPTION_ID --azure-event-hubs-ingestion-tenant-id=AZURE_EVENT_HUBS_INGESTION_TENANT_ID | [--cloud-storage-ingestion-bucket=CLOUD_STORAGE_INGESTION_BUCKET --cloud-storage-ingestion-input-format=INPUT_FORMAT : --cloud-storage-ingestion-text-delimiter=CLOUD_STORAGE_INGESTION_TEXT_DELIMITER --cloud-storage-ingestion-minimum-object-create-time=CLOUD_STORAGE_INGESTION_MINIMUM_OBJECT_CREATE_TIME --cloud-storage-ingestion-match-glob=CLOUD_STORAGE_INGESTION_MATCH_GLOB] | --confluent-cloud-ingestion-bootstrap-server=CONFLUENT_CLOUD_INGESTION_BOOTSTRAP_SERVER --confluent-cloud-ingestion-cluster-id=CONFLUENT_CLOUD_INGESTION_CLUSTER_ID --confluent-cloud-ingestion-identity-pool-id=CONFLUENT_CLOUD_INGESTION_IDENTITY_POOL_ID --confluent-cloud-ingestion-service-account=CONFLUENT_CLOUD_INGESTION_SERVICE_ACCOUNT --confluent-cloud-ingestion-topic=CONFLUENT_CLOUD_INGESTION_TOPIC | --kinesis-ingestion-consumer-arn=KINESIS_INGESTION_CONSUMER_ARN --kinesis-ingestion-role-arn=KINESIS_INGESTION_ROLE_ARN --kinesis-ingestion-service-account=KINESIS_INGESTION_SERVICE_ACCOUNT --kinesis-ingestion-stream-arn=KINESIS_INGESTION_STREAM_ARN]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-message-retention-duration
      | --message-retention-duration=MESSAGE_RETENTION_DURATION]
    [--clear-message-transforms
      | --message-transforms-file=MESSAGE_TRANSFORMS_FILE]
    [--clear-schema-settings
      | [--message-encoding=ENCODING (--schema=SCHEMA
      : --schema-project=SCHEMA_PROJECT)
      : --first-revision-id=FIRST_REVISION_ID
      --last-revision-id=LAST_REVISION_ID]]
    [--recompute-message-storage-policy
      | [--message-storage-policy-allowed-regions=[REGION,...]
      : --message-storage-policy-enforce-in-transit]]
    [--topic-encryption-key=TOPIC_ENCRYPTION_KEY
      : --topic-encryption-key-keyring=TOPIC_ENCRYPTION_KEY_KEYRING
      --topic-encryption-key-location=TOPIC_ENCRYPTION_KEY_LOCATION
      --topic-encryption-key-project=TOPIC_ENCRYPTION_KEY_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Topic resource - Name of the topic to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument topic on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TOPIC
     ID of the topic or fully qualified identifier for the topic.

     To set the topic attribute:
     + provide the argument topic on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update existing labels on a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics update mytopic \
      --update-labels=KEY1=VAL1,KEY2=VAL2

To clear all labels on a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics update mytopic --clear-labels

To remove an existing label on a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics update mytopic --remove-labels=KEY1,KEY2

To enable customer-managed encryption for a Cloud Pub/Sub topic by
protecting message data with a Cloud KMS CryptoKey, run:

    $ gcloud pubsub topics update mytopic \
      --topic-encryption-key=projects/PROJECT_ID/locations/\
    KMS_LOCATION/keyRings/KEYRING/cryptoKeys/KEY

To enable or update retention on a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics update mytopic \
      --message-retention-duration=MESSAGE_RETENTION_DURATION

To disable retention on a Cloud Pub/Sub topic, run:

    $ gcloud pubsub topics update mytopic \
      --clear-message-retention-duration

To update a Cloud Pub/Sub topic's message storage policy, run:

    $ gcloud pubsub topics update mytopic \
      --message-storage-policy-allowed-regions=some-cloud-region1,\
    some-cloud-region2

To recompute a Cloud Pub/Sub topic's message storage policy based on your
organization's "Resource Location Restriction" policy, run:

    $ gcloud pubsub topics update mytopic \
      --recompute-message-storage-policy

To enforce both at-rest and in-transit guarantees for messages published to
the topic, run:

    $ gcloud pubsub topics update mytopic \
      --message-storage-policy-allowed-regions=some-cloud-region1,\
    some-cloud-region2 --message-storage-policy-enforce-in-transit
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/topics/update)

---
# gcloud pubsub message-transforms

manage Cloud Pub/Sub message transforms

### `gcloud pubsub message-transforms test`

Tests message transforms against a given message

Tests message transforms against a given message.

**Synopsis:**
```
gcloud pubsub message-transforms test
    (--attribute=[ATTRIBUTE,...] --message=MESSAGE)
    (--message-transforms-file=MESSAGE_TRANSFORMS_FILE
      | --subscription=SUBSCRIPTION
      | [--topic=TOPIC : --topic-project=TOPIC_PROJECT])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attribute` | [ATTRIBUTE,...] |  | _[At least one of these must be specified:]_ Comma-separated list of attributes to attach to the message. Each ATTRIBUTE has the form name="value". You can specify up to 100 attributes. |
| `--message` | MESSAGE |  | _[At least one of these must be specified:]_ Message body to test the message transforms against. |
| `--message-transforms-file` | MESSAGE_TRANSFORMS_FILE |  | _[Exactly one of these must be specified:]_ Path to YAML or JSON file containing message transforms. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/message-transforms/test)

---
### `gcloud pubsub message-transforms validate`

Validates a message transform

Validates a message transform.

**Synopsis:**
```
gcloud pubsub message-transforms validate
    --message-transform-file=MESSAGE_TRANSFORM_FILE [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--message-transform-file` | MESSAGE_TRANSFORM_FILE |  | Path to YAML or JSON file containing a message transform. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/message-transforms/validate)

---
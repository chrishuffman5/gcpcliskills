# gcloud pubsub snapshots

manage Cloud Pub/Sub snapshots

### `gcloud pubsub snapshots create`

Creates one or more Cloud Pub/Sub snapshots

Creates one or more Cloud Pub/Sub snapshots.

**Synopsis:**
```
gcloud pubsub snapshots create SNAPSHOT [SNAPSHOT ...]
    --subscription=SUBSCRIPTION [--labels=[KEY=VALUE,...]]
    [--subscription-project=SUBSCRIPTION_PROJECT] [--tags=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT [SNAPSHOT ...]
   One or more snapshot names to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--subscription` | SUBSCRIPTION |  | The subscription whose backlog the snapshot retains. Specifically, the created snapshot is guaranteed to retain a) The existing backlog on the subscription, i.e., the set of messages in the subscription that are unacknowledged upon the successful completion of the create snapshot request, b) Any messages published to the subscription's topic following the successful creation of the snapshot. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--subscription-project` | SUBSCRIPTION_PROJECT |  | The name of the project the provided subscription belongs to. If not set, it defaults to the currently selected cloud project. |
| `--tags` | [KEY=VALUE,...] |  | List of tags KEY=VALUE pairs to bind. Each item must be expressed as <tag-key-namespaced-name>=<tag-value-short-name>. Example: 123/environment=production,123/costCenter=marketing |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/snapshots/create)

---
### `gcloud pubsub snapshots delete`

Deletes one or more Cloud Pub/Sub snapshots

Deletes one or more Cloud Pub/Sub snapshots.

**Synopsis:**
```
gcloud pubsub snapshots delete SNAPSHOT [SNAPSHOT ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT [SNAPSHOT ...]
   One or more snapshot names to delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/snapshots/delete)

---
### `gcloud pubsub snapshots describe`

Describes a Cloud Pub/Sub snapshot

Describes a Cloud Pub/Sub snapshot.

**Synopsis:**
```
gcloud pubsub snapshots describe SNAPSHOT [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SNAPSHOT
   snapshot to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/snapshots/describe)

---
### `gcloud pubsub snapshots list`

Lists all the snapshots in a given project

Lists all the snapshots in a given project.

**Synopsis:**
```
gcloud pubsub snapshots list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/snapshots/list)

---
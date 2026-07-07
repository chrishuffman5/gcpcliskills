# gcloud asset feeds

manage Cloud Asset Inventory feeds

### `gcloud asset feeds create`

Create a Cloud Asset Inventory Feed

Create a new Cloud Asset Inventory Feed for updates on assets.

**Synopsis:**
```
gcloud asset feeds create FEED_ID --pubsub-topic=PUBSUB_TOPIC
    (--asset-names=[ASSET_NAMES,...] --asset-types=[ASSET_TYPES,...]
      --relationship-types=[RELATIONSHIP_TYPES,...])
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID)
    [--condition-description=CONDITION_DESCRIPTION]
    [--condition-expression=CONDITION_EXPRESSION]
    [--condition-title=CONDITION_TITLE] [--content-type=CONTENT_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FEED_ID
   Asset feed identifier being created, it must be unique under the
   specified parent resource project/folder/organization.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pubsub-topic` | PUBSUB_TOPIC |  | Name of the Cloud Pub/Sub topic to publish to, of the form projects/PROJECT_ID/topics/TOPIC_ID. You can list existing topics with gcloud pubsub topics list --format="text(name)" |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition-description` | CONDITION_DESCRIPTION |  | Description of the feed condition. For reference only. |
| `--condition-expression` | CONDITION_EXPRESSION |  | Feed condition expression. If not specified, no condition will be applied to feed. For more information, see: https://cloud.google.com/asset-inventory/docs/monitoring-asset-changes#feed_with_condition |
| `--condition-title` | CONDITION_TITLE |  | Title of the feed condition. For reference only. |
| `--content-type` | one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship |  | Asset content type. If not specified, no content but the asset name and type will be returned in the feed. For more information, see https://cloud.google.com/resource-manager/docs/cloud-asset-inventory/overview#asset_content_type. CONTENT_TYPE must be one of: resource, iam-policy, org-policy, access-policy, os-inventory, relationship. |


**Examples:**
```bash
To create a new feed 'feed1' in project 'p1' which alerts on compute disks
and network resources types, run:

    $ gcloud asset feeds create feed1 --project=p1 \
        --asset-types=compute.googleapis.com/Network,\
    compute.googleapis.com/Disk --content-type=resource \
        --pubsub-topic=projects/project1/topics/feed-topic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/feeds/create)

---
### `gcloud asset feeds delete`

Delete a Cloud Asset Inventory Feed

Delete a Cloud Asset Inventory Feed.

**Synopsis:**
```
gcloud asset feeds delete FEED_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FEED_ID
   Asset feed identifier to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the feed. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the feed. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ project of the feed. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To delete a feed 'feed1' in project 'p1', run:

    $ gcloud asset feeds delete feed1 --project=p1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/feeds/delete)

---
### `gcloud asset feeds describe`

Describe a Cloud Asset Inventory Feed

Describe a Cloud Asset Inventory Feed.

**Synopsis:**
```
gcloud asset feeds describe FEED_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FEED_ID
   Asset feed identifier to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the feed. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the feed. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ project of the feed. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To describe a feed 'feed1' in project 'p1', run:

    $ gcloud asset feeds describe feed1 --project=p1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/feeds/describe)

---
### `gcloud asset feeds list`

List Cloud Asset Inventory Feeds

List Cloud Asset Inventory Feeds under a parent resource.

**Synopsis:**
```
gcloud asset feeds list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the feed. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the feed. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ project of the feed. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Examples:**
```bash
To list feeds in organization 'org1', run:

    $ gcloud asset feeds list --organization=org1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/feeds/list)

---
### `gcloud asset feeds update`

Update an existing Cloud Asset Inventory Feed

Update an existing Cloud Asset Inventory Feed.

**Synopsis:**
```
gcloud asset feeds update FEED_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--pubsub-topic=PUBSUB_TOPIC]
    [--add-asset-names=[ASSET-NAMES,...] | --clear-asset-names
      | --remove-asset-names=[ASSET-NAMES,...]]
    [--add-asset-types=[ASSET-TYPES,...] | --clear-asset-types
      | --remove-asset-types=[ASSET-TYPES,...]]
    [--add-relationship-types=[RELATIONSHIP-TYPES,...]
      | --clear-relationship-types
      | --remove-relationship-types=[RELATIONSHIP-TYPES,...]]
    [--clear-condition-description
      | --condition-description=CONDITION_DESCRIPTION]
    [--clear-condition-expression
      | --condition-expression=CONDITION_EXPRESSION]
    [--clear-condition-title | --condition-title=CONDITION_TITLE]
    [--clear-content-type | --content-type=CONTENT_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FEED_ID
   Identifier of the asset feed to update, which must be unique in its
   parent resource. Parent resource can be a project, folder, or an
   organization.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder of the feed. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization of the feed. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ project of the feed. The Google Cloud project ID to use for this invocation. If omitted, then the current project is assumed; the current project can be listed using gcloud config list --format='text(core.project)' and can be set using gcloud config set project PROJECTID. --project and its fallback core/project property play two roles in the invocation. It specifies the project of the resource to operate on. It also specifies the project for API enablement check, quota, and billing. To specify a different project for quota and billing, use --billing-project or billing/quota_project property. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pubsub-topic` | PUBSUB_TOPIC |  | Name of the Cloud Pub/Sub topic to publish to, of the form projects/PROJECT_ID/topics/TOPIC_ID. You can list existing topics with gcloud pubsub topics list --format="text(name)" |


**Examples:**
```bash
To add an asset-type to an existing feed, run:

    $ gcloud asset feeds update feed1 --project=p1 \
        --add-asset-types=pubsub.googleapis.com/Topic
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/asset/feeds/update)

---
# gcloud scc notifications

manage Cloud SCC (Security Command Center) notifications

### `gcloud scc notifications create`

Create a Security Command Center notification config

Create a Security Command Center notification config.

Notification configs that are created with Security Command Center API V2
and later include a location attribute. If a location is not specified, the
default global location is used. For example, the following Notification
config name has location=global attribute:
organizations/123/locations/global/notificationConfigs/my-config.

**Synopsis:**
```
gcloud scc notifications create NOTIFICATION_CONFIG_ID
    --pubsub-topic=PUBSUB_TOPIC [--description=DESCRIPTION]
    [--filter=FILTER] [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NOTIFICATION_CONFIG_ID
   The ID of the notification config. Formatted as
   "organizations/123/notificationConfigs/456" or just "456".
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--pubsub-topic` | PUBSUB_TOPIC |  | The Pub/Sub topic which will receive notifications. Its format is "projects/[project_id]/topics/[topic]". |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The text that will be used to describe a notification configuration. |
| `--filter` | FILTER |  | Filter to be used for notification config. |
| `--location` | LOCATION | global | If data residency is enabled, specify the Security Command Center location in which to create the notification. The resulting notificationConfig resource is stored only in this location. Only findings that are issued in this location are sent to Pub/Sub. If data residency is not enabled, specifying the --location flag creates the notification by using Security Command Center API v2, and the only valid value for the flag is global. |


**Examples:**
```bash
Create a notification config test-config under organization 123 for
findings for pubsub-topic projects/test-project/topics/notification-test
with a filter on resource name:

    $ gcloud scc notifications create test-config --organization=123 \
        --pubsub-topic=projects/test-project/topics/notification-test \
        --filter="resource_name: \"a\""

Create a notification config test-config under folder 456 for findings for
pubsub-topic projects/test-project/topics/notification-test with a filter
on resource name:

    $ gcloud scc notifications create test-config --folder=456 \
        --pubsub-topic=projects/test-project/topics/notification-test \
        --filter="resource_name: \"a\""

Create a notification config test-config under project 789 for findings for
pubsub-topic projects/test-project/topics/notification-test with a filter
on resource name:

    $ gcloud scc notifications create test-config --project=789 \
        --pubsub-topic=projects/test-project/topics/notification-test \
        --filter="resource_name: \"a\""

Create a notification config test-config under organization 123 for
findings for pubsub-topic projects/test-project/topics/notification-test
with a filter on resource name and location=eu

    $ gcloud scc notifications create test-config --project=789 \
        --pubsub-topic=projects/test-project/topics/notification-test \
        --filter="resource_name: \"a\"" --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/notifications/create)

---
### `gcloud scc notifications delete`

Delete a Security Command Center notification config

Delete a Security Command Center notification config.

Notification configs that are created with Security Command Center API V2
and later include a location attribute. If the location attribute is
included in the resource name of a Notification configs, you must specify
it when referencing the Notification config. For example, the following
Notification configs name has location=eu:
organizations/123/locations/eu/notificationConfigs/test-config.

**Synopsis:**
```
gcloud scc notifications delete NOTIFICATION_CONFIG_ID
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NOTIFICATION_CONFIG_ID
   The ID of the notification config. Formatted as
   "organizations/123/notificationConfigs/456" or just "456".
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | Required if either data residency is enabled or the notificationConfig was created by using the API v2. If data residency is enabled, specify the Security Command Center location in which the notification is stored. If data residency is not enabled, include /locations/``LOCATION'' in the full name or specify the --location flag only if the notificationConfig was created by using the Security Command Center API v2, in which case, the only valid location is global. |


**Examples:**
```bash
Delete notification config 'test-config' from organization 123

    $ gcloud scc notifications delete test-config --organization=123

Delete notification config 'test-config' from folder 456

    $ gcloud scc notifications delete test-config --folder=456

Delete notification config 'test-config' from project 789

    $ gcloud scc notifications delete test-config --project=789

Delete notification config 'test-config' with location global from
organization 123

    $ gcloud scc notifications delete test-config --organization=123 \
        --location=global

Delete notification config 'test-config' with location=eu from organization
123

    $ gcloud scc notifications delete test-config --organization=123 \
        --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/notifications/delete)

---
### `gcloud scc notifications describe`

Describe a Security Command Center notification config

Describe a Security Command Center notification config.

Notification configs that are created with Security Command Center API V2
and later include a location attribute. If the location attribute is
included in the resource name of a Notification configs, you must specify
it when referencing the Notification config. For example, the following
Notification configs name has location=eu:
organizations/123/locations/eu/notificationConfigs/test-config.

**Synopsis:**
```
gcloud scc notifications describe NOTIFICATION_CONFIG_ID
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NOTIFICATION_CONFIG_ID
   The ID of the notification config. Formatted as
   "organizations/123/notificationConfigs/456" or just "456".
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | Required if either data residency is enabled or the notificationConfig resources were created by using the API v2. If data residency is enabled, specify the Security Command Center location in which the notifications are stored. If data residency is not enabled, include /locations/``LOCATION'' only if the notificationConfig resource was created by using the Security Command Center API v2, in which case, the only valid location is global. |


**Examples:**
```bash
Describe notification config 'test-config' from organization 123

    $ gcloud scc notifications describe test-config --organization=123

Describe notification config 'test-config' from folder 456

    $ gcloud scc notifications describe test-config --folder=456

Describe notification config 'test-config' from project 789

    $ gcloud scc notifications describe test-config --project=789

Describe notification config 'test-config' from organization 123 and
location=global

    $ gcloud scc notifications describe test-config --organization=123 \
      --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/notifications/describe)

---
### `gcloud scc notifications list`

List Security Command Center notification configs

List Security Command Center notification configs.

    Notification Configs that are created with Security Command Center API V2
    and later include a `location` attribute. Include the `--location` flag to
    list Notification Configs with `location` attribute other than `global`.

**Synopsis:**
```
gcloud scc notifications list [PARENT]
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Parent resource - parent organization, folder, or project in the Google
Cloud resource hierarchy to be used for the gcloud scc command. Specify
the argument as either [RESOURCE_TYPE/RESOURCE_ID] or [RESOURCE_ID], as
shown in the preceding examples. This represents a Cloud resource.

  [PARENT]
     ID of the parent or fully qualified identifier for the parent.

     To set the parent attribute:
     + provide the argument parent on the command line;
     + Set the parent property in configuration using gcloud config set
       scc/parent if it is not specified in command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | Required if either data residency is enabled or the notificationConfig resources were created by using the API v2. If data residency is enabled, specify the Security Command Center location in which the notifications are stored. If data residency is not enabled, including /locations/``LOCATION'' in the name or the --location flag in the command lists only the notificationConfig resources that were created by using the Security Command Center API v2 and the only valid location is global. |


**Examples:**
```bash
List notification configs from organization 123

    $ gcloud scc notifications list 123
    $ gcloud scc notifications list organizations/123

List notification configs from folder 456

    $ gcloud scc notifications list folders/456

List notification configs from project 789

    $ gcloud scc notifications list projects/789

List notification configs from organization 123 and location=eu

    $ gcloud scc notifications list 123 --location=eu
    $ gcloud scc notifications list organizations/123 \
        --location=locations/eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/notifications/list)

---
### `gcloud scc notifications update`

Update a Security Command Center notification config

Update a Security Command Center notification config.

Notification configs that are created with Security Command Center API V2
and later include a location attribute. If the location attribute is
included in the resource name of a Notification configs, you must specify
it when referencing the Notification config. For example, the following
Notification configs name has location=eu:
organizations/123/locations/eu/notificationConfigs/test-config.

**Synopsis:**
```
gcloud scc notifications update NOTIFICATION_CONFIG_ID
    [--description=DESCRIPTION] [--filter=FILTER]
    [--location=LOCATION; default="global"] [--pubsub-topic=PUBSUB_TOPIC]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NOTIFICATION_CONFIG_ID
   The ID of the notification config. Formatted as
   "organizations/123/notificationConfigs/456" or just "456".
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The text that will be used to describe a notification configuration. |
| `--filter` | FILTER |  | The filter string which will applied to events of findings of a notification configuration. |
| `--location` | LOCATION | global | Required if either data residency is enabled or the notificationConfig was created by using the API v2. If data residency is enabled, specify the Security Command Center location in which the notification is stored. If data residency is not enabled, include /locations/``LOCATION'' in the full name or specify the --location flag only if the notificationConfig resource was created by using the Security Command Center API v2, in which case, the only valid location is global. |
| `--pubsub-topic` | PUBSUB_TOPIC |  | The Pub/Sub topic which will receive notifications. Its format is "projects/[project_id]/topics/[topic]". |


**Examples:**
```bash
Update all mutable fields under an organization parent test-config
(description + pubsub topic + filter):

    $ gcloud scc notifications update scc notifications update \
        test-config --organization=123 --description="New description" \
        --pubsub-topic="projects/22222/topics/newtopic"

Update all mutable fields under a folder parent test-config (description +
pubsub topic + filter):

    $ gcloud scc notifications update scc notifications update \
        test-config --folder=456 --description="New description" \
        --pubsub-topic="projects/22222/topics/newtopic"

Update all mutable fields under a project parent test-config (description +
pubsub topic + filter):

    $ gcloud scc notifications update scc notifications update \
        test-config --project=789 --description="New description" \
        --pubsub-topic="projects/22222/topics/newtopic"

Update test-config's description

    $ gcloud scc notifications update test-config --organization=123 \
        --description="New description"

Update test-config's pubsub-topic

    $ gcloud scc notifications update test-config --organization=123 \
        --pubsub-topic="projects/22222/topics/newtopic"

Update test-config's filter

    $ gcloud scc notifications update test-config --organization=123 \
        --filter='state = \"ACTIVE\"'

Update all mutable fields for test-config with location=global under an
organization parent (description + pubsub topic + filter):

    $ gcloud scc notifications update scc notifications update \
        test-config --organization=123 --description="New description" \
        --pubsub-topic="projects/22222/topics/newtopic" \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/notifications/update)

---
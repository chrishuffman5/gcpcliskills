# gcloud spanner instance-configs

manage Cloud Spanner instance configs

### `gcloud spanner instance-configs create`

Create a Cloud Spanner instance configuration

Create a Cloud Spanner instance configuration.

**Synopsis:**
```
gcloud spanner instance-configs create INSTANCE_CONFIG
    (--base-config=BASE_CONFIG --replicas=location=LOCATION,type=TYPE:[...]
      | [--clone-config=INSTANCE_CONFIG
      : --add-replicas=location=LOCATION,type=TYPE:[...]
      --skip-replicas=location=LOCATION,type=TYPE:[...]]) [--async]
    [--display-name=DISPLAY_NAME] [--etag=ETAG] [--labels=[KEY=VALUE,...]]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_CONFIG
   Cloud Spanner instance configuration. The 'custom-' prefix is required
   to avoid name conflicts with Google-managed configurations.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--base-config` | BASE_CONFIG |  | _[Command-line flags to setup a custom instance configuration replicas:]_ The name of the Google-managed instance configuration, based on which your custom configuration is created. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--replicas` | location=LOCATION,type=TYPE:[...] |  | _[Command-line flags to setup a custom instance configuration replicas:]_ The geographic placement of nodes in this instance configuration and their replication types. location The location of the serving resources, e.g. "us-central1". type The type of replica. Items in the list are separated by ":". The allowed values and formats are as follows. |
| `--clone-config` | INSTANCE_CONFIG |  | _[options:]_ The ID of the instance config, based on which this configuration is created. The clone is an independent copy of this config. Available configurations can be found by running "gcloud spanner instance-configs list" This flag argument must be specified if any of the other arguments in this group are specified. |
| `--add-replicas` | location=LOCATION,type=TYPE:[...] |  | _[options:]_ Add new replicas while cloning from the source config. |
| `--skip-replicas` | location=LOCATION,type=TYPE:[...] |  | _[options:]_ Skip replicas from the source config while cloning. Each replica in the list must exist in the source config replicas list. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | The name of this instance configuration as it appears in UIs. Must specify this option if creating an instance-config with --replicas. |
| `--etag` | ETAG |  | Used for optimistic concurrency control. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | If specified, validate that the creation will succeed without creating the instance configuration. |


**Examples:**
```bash
To create a custom Cloud Spanner instance configuration based on an
existing Google-managed configuration (nam3) by adding a READ_ONLY type
replica in location us-east4, run:

    $ gcloud spanner instance-configs create custom-instance-config \
        --clone-config=nam3 \
        --add-replicas=location=us-east4,type=READ_ONLY

To create a custom Cloud Spanner instance configuration based on another
custom configuration (custom-instance-config) by adding a READ_ONLY type
replica in location us-east1 and removing a READ_ONLY type replica in
location us-east4, run:

    $ gcloud spanner instance-configs create custom-instance-config1 \
        --clone-config=custom-instance-config \
        --add-replicas=location=us-east1,type=READ_ONLY \
        --skip-replicas=location=us-east4,type=READ_ONLY
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-configs/create)

---
### `gcloud spanner instance-configs delete`

Delete a Cloud Spanner instance configuration

Delete a Cloud Spanner instance configuration.

**Synopsis:**
```
gcloud spanner instance-configs delete INSTANCE_CONFIG [--etag=ETAG]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_CONFIG
   Cloud Spanner instance config.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Used for optimistic concurrency control as a way to help prevent simultaneous deletes of an instance config from overwriting each other. |
| `--validate-only` |  |  | If specified, validate that the deletion will succeed without deleting the instance config. |


**Examples:**
```bash
To delete a custom Cloud Spanner instance configuration, run:

    $ gcloud spanner instance-configs delete custom-instance-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-configs/delete)

---
### `gcloud spanner instance-configs describe`

Describe a Cloud Spanner instance configuration

Describe a Cloud Spanner instance configuration.

**Synopsis:**
```
gcloud spanner instance-configs describe INSTANCE_CONFIG
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_CONFIG
   Cloud Spanner instance config.
```

**Examples:**
```bash
To describe an instance config named regional-us-central1, run:

    $ gcloud spanner instance-configs describe regional-us-central1

To describe an instance config named nam-eur-asia1, run:

    $ gcloud spanner instance-configs describe nam-eur-asia1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-configs/describe)

---
### `gcloud spanner instance-configs list`

List the available Cloud Spanner instance configurations

List the available Cloud Spanner instance configurations.

**Synopsis:**
```
gcloud spanner instance-configs list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the Cloud Spanner instance configs that are availble for this
project, run:

    $ gcloud spanner instance-configs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-configs/list)

---
### `gcloud spanner instance-configs update`

Update a Cloud Spanner instance configuration

Update a Cloud Spanner instance configuration.

**Synopsis:**
```
gcloud spanner instance-configs update INSTANCE_CONFIG [--async]
    [--display-name=DISPLAY_NAME] [--etag=ETAG]
    [--update-labels=[KEY=VALUE,...]] [--validate-only]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_CONFIG
   Cloud Spanner instance config. The 'custom-' prefix is required to
   avoid name conflicts with Google-managed configurations.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | The name of this instance configuration as it appears in UIs. |
| `--etag` | ETAG |  | Used for optimistic concurrency control. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | Use this flag to validate that the request will succeed before executing it. |


**Examples:**
```bash
To update display name of a custom Cloud Spanner instance configuration
'custom-instance-config', run:

    $ gcloud spanner instance-configs update custom-instance-config \
        --display-name=nam3-RO-us-central1

To modify the instance config 'custom-instance-config' by adding label
'k0', with value 'value1' and label 'k1' with value 'value2' and removing
labels with key 'k3', run:

    $ gcloud spanner instance-configs update custom-instance-config \
         --update-labels=k0=value1,k1=value2 --remove-labels=k3

To clear all labels of a custom Cloud Spanner instance configuration
'custom-instance-config', run:

    $ gcloud spanner instance-configs update custom-instance-config \
        --clear-labels

To remove an existing label of a custom Cloud Spanner instance
configuration 'custom-instance-config', run:

    $ gcloud spanner instance-configs update custom-instance-config \
        --remove-labels=KEY1,KEY2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/instance-configs/update)

---
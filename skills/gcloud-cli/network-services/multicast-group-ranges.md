# gcloud network-services multicast-group-ranges

manage Network Services MulticastGroupRanges

### `gcloud network-services multicast-group-ranges create`

Create a multicast group range

Create a multicast group range in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-group-ranges create
    (MULTICAST_GROUP_RANGE : --location=LOCATION)
    --multicast-domain=MULTICAST_DOMAIN
    --reserved-internal-range=RESERVED_INTERNAL_RANGE [--async]
    [--consumer-accept-list=[CONSUMER_ACCEPT_LIST,...]]
    [--description=DESCRIPTION] [--distribution-scope=DISTRIBUTION_SCOPE]
    [--[no-]enable-logging] [--labels=[KEY=VALUE,...]]
    [--require-explicit-accept] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range resource - Name of the multicast group range to be
created. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE
     ID of the multicast group range or fully qualified identifier for the
     multicast group range.

     To set the multicast_group_range attribute:
     + provide the argument multicast_group_range on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicast-domain` | MULTICAST_DOMAIN |  | The multicast domain to be used. |
| `--reserved-internal-range` | RESERVED_INTERNAL_RANGE |  | The reserved internal range to be used. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--consumer-accept-list` | [CONSUMER_ACCEPT_LIST,...] |  | An optional list of consumer projects that can use this multicast group range. |
| `--description` | DESCRIPTION |  | The description for the multicast group range. |
| `--distribution-scope` | one of: distribution-scope-unspecified, intra-region, intra-zone |  | Distribution scope of this multicast group range. DISTRIBUTION_SCOPE must be one of: distribution-scope-unspecified, intra-region, intra-zone. |
| `--[no-]enable-logging` |  |  | Whether to enable logging for this multicast group range. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--require-explicit-accept` |  |  | Whether an empty consumer accept list will reject all consumer projects. |


**Examples:**
```bash
Create a multicast group range with the name 'my-multicast-group-range',
reserved-internal-range 'path-to-ir', multicast-domain 'path-to-md', and
location 'global'.

    $ gcloud network-services multicast-group-ranges create \
        my-multicast-group-range --reserved-internal-range=path-to-ir \
        --multicast-domain=path-to-md --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-ranges/create)

---
### `gcloud network-services multicast-group-ranges delete`

Delete a multicast group range

Delete a multicast group range in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-group-ranges delete
    (MULTICAST_GROUP_RANGE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range resource - The multicast group range to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE
     ID of the multicast group range or fully qualified identifier for the
     multicast group range.

     To set the multicast_group_range attribute:
     + provide the argument multicast_group_range on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast group range in the current project, run:

    $ gcloud network-services multicast-group-ranges delete \
        my-multicast-group-range --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-ranges/delete)

---
### `gcloud network-services multicast-group-ranges describe`

Describe a multicast group range

Show details of a multicast group range in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-group-ranges describe
    (MULTICAST_GROUP_RANGE : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range resource - The multicast group range to display. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE
     ID of the multicast group range or fully qualified identifier for the
     multicast group range.

     To set the multicast_group_range attribute:
     + provide the argument multicast_group_range on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a multicast group range in the current project, run:

    $ gcloud network-services multicast-group-ranges describe \
        my-multicast-group-range --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-ranges/describe)

---
### `gcloud network-services multicast-group-ranges list`

List multicast group ranges

List all multicast group ranges in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-group-ranges list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list multicast group ranges in the current project, run:

    $ gcloud network-services multicast-group-ranges list \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-ranges/list)

---
### `gcloud network-services multicast-group-ranges update`

Update a multicast group range

Update a multicast group range in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-group-ranges update
    (MULTICAST_GROUP_RANGE : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--[no-]enable-logging]
    [--[no-]require-explicit-accept] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--consumer-accept-list=[CONSUMER_ACCEPT_LIST,...]
      | --add-consumer-accept-list=[ADD_CONSUMER_ACCEPT_LIST,...]
      --clear-consumer-accept-list
      | --remove-consumer-accept-list=[REMOVE_CONSUMER_ACCEPT_LIST,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast group range resource - Name of the multicast group range to be
updated. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_group_range on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_GROUP_RANGE
     ID of the multicast group range or fully qualified identifier for the
     multicast group range.

     To set the multicast_group_range attribute:
     + provide the argument multicast_group_range on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_group_range on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast group range. |
| `--[no-]enable-logging` |  |  | Whether to enable logging for this multicast group range. Use --enable-logging to enable and --no-enable-logging to disable. |
| `--[no-]require-explicit-accept` |  |  | Whether an empty consumer accept list will reject all consumer projects. Use --require-explicit-accept to enable and --no-require-explicit-accept to disable. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast group range with the name 'my-multicast-group-range' and
location 'global'.

    $ gcloud network-services multicast-group-ranges update \
        my-multicast-group-range --require-explicit-accept \
        --enable-logging --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-group-ranges/update)

---
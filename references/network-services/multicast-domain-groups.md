# gcloud network-services multicast-domain-groups

manage Network Services MulticastDomainGroups

### `gcloud network-services multicast-domain-groups create`

Create a multicast domain group

Create a multicast domain group in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-domain-groups create
    (MULTICAST_DOMAIN_GROUP : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain group resource - Name of the multicast domain group to be
created. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_group on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_GROUP
     ID of the multicast domain group or fully qualified identifier for
     the multicast domain group.

     To set the multicast_domain_group attribute:
     + provide the argument multicast_domain_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_group on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast domain group. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Create a multicast domain group with the name 'my-multicast-domain-group',
and location global.

    $ gcloud network-services multicast-domain-groups create \
        my-multicast-domain-group --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-groups/create)

---
### `gcloud network-services multicast-domain-groups delete`

Delete a multicast domain group

Delete a multicast domain group in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-domain-groups delete
    (MULTICAST_DOMAIN_GROUP : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain group resource - The multicast domain group to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_group on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_GROUP
     ID of the multicast domain group or fully qualified identifier for
     the multicast domain group.

     To set the multicast_domain_group attribute:
     + provide the argument multicast_domain_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_group on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast domain group in the current project, run:

    $ gcloud network-services multicast-domain-groups delete \
        my-multicast-domain-group --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-groups/delete)

---
### `gcloud network-services multicast-domain-groups describe`

Describe a multicast domain group

Show details of a multicast domain group in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-domain-groups describe
    (MULTICAST_DOMAIN_GROUP : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain group resource - The multicast domain group to display.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_group on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_GROUP
     ID of the multicast domain group or fully qualified identifier for
     the multicast domain group.

     To set the multicast_domain_group attribute:
     + provide the argument multicast_domain_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_group on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a multicast domain group in the current project, run:

    $ gcloud network-services multicast-domain-groups describe \
        my-multicast-domain-group --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-groups/describe)

---
### `gcloud network-services multicast-domain-groups list`

List multicast domain groups

List all multicast domain groups in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-domain-groups list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list multicast domain groups in the current project, run:

    $ gcloud network-services multicast-domain-groups list \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-groups/list)

---
### `gcloud network-services multicast-domain-groups update`

Update a multicast domain group

Update a multicast domain group in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-domain-groups update
    (MULTICAST_DOMAIN_GROUP : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain group resource - Name of the multicast domain group to be
updated. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain_group on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN_GROUP
     ID of the multicast domain group or fully qualified identifier for
     the multicast domain group.

     To set the multicast_domain_group attribute:
     + provide the argument multicast_domain_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain_group on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast domain group. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast domain group with the name my-multicast-domain-group and
location zone.

    $ gcloud network-services multicast-domain-groups update \
        my-multicast-domain-group --description="new description" \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domain-groups/update)

---
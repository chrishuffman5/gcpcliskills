# gcloud network-services multicast-producer-associations

manage Network Services MulticastProducerAssociations

### `gcloud network-services multicast-producer-associations create`

Create a multicast producer association

Create a multicast producer association in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-producer-associations create
    (MULTICAST_PRODUCER_ASSOCIATION : --location=LOCATION)
    --multicast-domain-activation=MULTICAST_DOMAIN_ACTIVATION
    --network=NETWORK [--async] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast producer association resource - Name of the multicast producer
association to be created. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_producer_association on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_PRODUCER_ASSOCIATION
     ID of the multicast producer association or fully qualified
     identifier for the multicast producer association.

     To set the multicast_producer_association attribute:
     + provide the argument multicast_producer_association on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_producer_association on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--multicast-domain-activation` | MULTICAST_DOMAIN_ACTIVATION |  | The multicast domain activation to be used. |
| `--network` | NETWORK |  | The path of the multicast producer VPC network. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast producer association. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Create a multicast producer association with the name
'my-multicast-producer-association', multicast-domain-activation
'path-to-mda', network 'path-to-network', and location 'zone'.

    $ gcloud network-services multicast-producer-associations create \
        my-multicast-producer-association \
        --multicast-domain-activation=path-to-mda \
        --network=path-to-network --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-producer-associations/create)

---
### `gcloud network-services multicast-producer-associations delete`

Delete a multicast producer association

Delete a multicast producer association in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-producer-associations delete
    (MULTICAST_PRODUCER_ASSOCIATION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast producer association resource - The multicast producer
association to delete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_producer_association on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_PRODUCER_ASSOCIATION
     ID of the multicast producer association or fully qualified
     identifier for the multicast producer association.

     To set the multicast_producer_association attribute:
     + provide the argument multicast_producer_association on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_producer_association on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast producer association in the current project, run:

    $ gcloud network-services multicast-producer-associations delete \
        my-multicast-producer-association --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-producer-associations/delete)

---
### `gcloud network-services multicast-producer-associations describe`

Describe a multicast producer associations

Show details of a multicast producer association in the specified location
of the current project.

**Synopsis:**
```
gcloud network-services multicast-producer-associations describe
    (MULTICAST_PRODUCER_ASSOCIATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast producer association resource - The multicast producer
association to display. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_producer_association on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_PRODUCER_ASSOCIATION
     ID of the multicast producer association or fully qualified
     identifier for the multicast producer association.

     To set the multicast_producer_association attribute:
     + provide the argument multicast_producer_association on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_producer_association on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe details of a multicast producer association in the current
project and location, run:

    $ gcloud network-services multicast-producer-associations describe \
        my-multicast-producer-association --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-producer-associations/describe)

---
### `gcloud network-services multicast-producer-associations list`

List multicast producer associations

List all multicast producer associations in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-producer-associations list
    --location=LOCATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list multicast producer associations in the current project and
location, run:

    $ gcloud network-services multicast-producer-associations list \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-producer-associations/list)

---
### `gcloud network-services multicast-producer-associations update`

Update a multicast producer association

Update a multicast producer association in the specified location of the
current project.

**Synopsis:**
```
gcloud network-services multicast-producer-associations update
    (MULTICAST_PRODUCER_ASSOCIATION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast producer association resource - Name of the multicast producer
association to be updated. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument multicast_producer_association on the command
   line with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_PRODUCER_ASSOCIATION
     ID of the multicast producer association or fully qualified
     identifier for the multicast producer association.

     To set the multicast_producer_association attribute:
     + provide the argument multicast_producer_association on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_producer_association on the
       command line with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast producer association. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast producer association with the name
my-multicast-producer-association and location zone.

    $ gcloud network-services multicast-producer-associations update \
        my-multicast-producer-association \
        --description="new description" --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-producer-associations/update)

---
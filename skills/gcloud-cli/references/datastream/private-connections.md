# gcloud datastream private-connections

manage Datastream private connections

### `gcloud datastream private-connections create`

Create a Datastream private connection

**Synopsis:**
```
gcloud datastream private-connections create
    (PRIVATE_CONNECTION : --location=LOCATION) --display-name=DISPLAY_NAME
    (--network-attachment=NETWORK_ATTACHMENT | --subnet=SUBNET --vpc=VPC)
    [--labels=[KEY=VALUE,...]] [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private connection resource - The private connection to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the private_connection or fully qualified identifier for the
     private_connection.

     To set the private_connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the private_connection.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | Friendly name for the private connection. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--validate-only` |  |  | If set, the request will retrieve the project id to allow in the network attachment Datastream will connect to. |


**Examples:**
```bash
To create a privateConnection with VPC Peering called
'my-privateConnection', run:

    $ gcloud datastream private-connections create \
      my-privateConnection --location=us-central1 \
      --display-name=my-privateConnection --vpc=vpc-example \
      --subnet=10.0.0.0/29

To create a privateConnection with PSC Interface called
'my-privateConnection', run:

    $ gcloud datastream private-connections create \
      my-privateConnection --location=us-central1 \
      --display-name=my-privateConnection \
      --network-attachment=network-attachment-example
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/private-connections/create)

---
### `gcloud datastream private-connections delete`

Delete a Datastream private connection

Deletes a private connection. You must set the --force parameter to ensure
that the private connectivity configuration is deleted properly.

**Synopsis:**
```
gcloud datastream private-connections delete
    (PRIVATE_CONNECTION : --location=LOCATION) [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private connection resource - Private connection resource - Private
connection to delete. The arguments in this group can be used to specify
the attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the private_connection or fully qualified identifier for the
     private_connection.

     To set the private_connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | You must set the force to ensure that the private connectivity configuration is deleted properly. |


**Examples:**
```bash
To delete a private connection:

    $ gcloud datastream private-connections delete PRIVATE_CONNECTION \
      --location=us-central1 --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/private-connections/delete)

---
### `gcloud datastream private-connections describe`

Show details about a Datastream private connection

Show details about a private connection.

**Synopsis:**
```
gcloud datastream private-connections describe
    (PRIVATE_CONNECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private connection resource - The private connection you want to get the
details of. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the private_connection or fully qualified identifier for the
     private_connection.

     To set the private_connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the resources.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about a private connection, run:

    $ gcloud datastream private-connections describe \
        my-private-connection --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/private-connections/describe)

---
### `gcloud datastream private-connections list`

List private connections

List private connections.

**Synopsis:**
```
gcloud datastream private-connections list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all private connections in a project and location 'us-central1',
run:

    $ gcloud datastream private-connections list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastream/private-connections/list)

---
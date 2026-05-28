# gcloud database-migration private-connections

manage Database Migration Service private connections

### `gcloud database-migration private-connections create`

Create a Database Migration private connection

**Synopsis:**
```
gcloud database-migration private-connections create
    (PRIVATE_CONNECTION : --region=REGION) --display-name=DISPLAY_NAME
    (--network-attachment=NETWORK_ATTACHMENT | --subnet=SUBNET --vpc=VPC)
    [--no-async] [--labels=[KEY=VALUE,...]] [--skip-validation]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
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

  --region=REGION
     The Cloud region for the private_connection.

     To set the region attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | A user-friendly name for the private connection. The display name can include letters, numbers, spaces, and hyphens, and must start with a letter. The maximum length allowed is 60 characters. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--skip-validation` |  |  | Creates the private connection without running prior verifications. |
| `--validate-only` |  |  | If set, the request will retrieve the project id to allow in the network attachment Datastream will connect to. |


**Examples:**
```bash
To create a private connection with VPC Peering called
'my-private-connection', run:

    $ gcloud database-migration private-connections create \
      my-private-connection --region=us-central1 \
      --display-name=my-private-connection --vpc=vpc-example \
      --subnet=10.0.0.0/29

    To create a private connection with PSC Interface called 'my-privateConnection', run:

    $ gcloud database-migration private-connections create \
      my-private-connection --location=us-central1 \
      --display-name=my-private-connection \
      --network-attachment=network-attachment-example

    To use a private connection, all migrations and connection profiles that use this configuration must be in the same region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/private-connections/create)

---
### `gcloud database-migration private-connections delete`

Delete a Database Migration private connection

**Synopsis:**
```
gcloud database-migration private-connections delete
    (PRIVATE_CONNECTION : --region=REGION) [--no-async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private connection resource - The private connection to delete. The
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

  --region=REGION
     The Cloud region for the private_connection.

     To set the region attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-async` |  |  | Waits for the operation in progress to complete before returning. |


**Examples:**
```bash
To delete a private connection called 'my-private-connection', run:

    $ gcloud database-migration private-connections delete \
      my-private-connection --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/private-connections/delete)

---
### `gcloud database-migration private-connections describe`

Show details about a database migration private connection

Show details about a private connection.

**Synopsis:**
```
gcloud database-migration private-connections describe
    (PRIVATE_CONNECTION : --region=REGION) [GCLOUD_WIDE_FLAG ...]
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

  --region=REGION
     The name of the region.

     To set the region attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To show details about a private connection called 'my-private-connection',
run:

    $ gcloud database-migration private-connections describe \
        my-private-connection --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/private-connections/describe)

---
### `gcloud database-migration private-connections list`

List private connections

List private connections.

**Synopsis:**
```
gcloud database-migration private-connections list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list all private connections in the current project and location
'us-central1', run:

    $ gcloud database-migration private-connections list \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/database-migration/private-connections/list)

---
# gcloud backup-dr management-servers

manage Backup and DR management server

### `gcloud backup-dr management-servers create`

Create a new management server in the project

Create a new management server in the project. A management server is
required to access the management console. It can only be created in
locations where Backup and DR is available. Resources in other locations
can be backed up.

**Synopsis:**
```
gcloud backup-dr management-servers create
    (MANAGEMENT_SERVER : --location=LOCATION) [--async] [--network=NETWORK]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management Server resource - Name of the management server to be created.
Once the management server is deployed, this name can't be changed. The
name must be unique for a project and location. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument management_server on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_SERVER
     ID of the Management Server or fully qualified identifier for the
     Management Server.

     To set the name attribute:
     + provide the argument management_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Management Server.

     To set the location attribute:
     + provide the argument management_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--network` | NETWORK |  | (DEPRECATED) Name of an existing VPC network with private service access configured in the format - projects/<project>/global/networks/<network>. This VPC network allows the management console to communicate with all backup/recovery appliances and requires a minimum IP range of /23. This value cannot be changed after you deploy the management server. If you don't have private service access, configure one. [Learn more] (https://cloud.google.com/vpc/docs/configure-private-services-access) Flag --network is deprecated. |


**Examples:**
```bash
To create a new management server sample-ms in project sample-project and
location us-central1, run:

    $ gcloud backup-dr management-servers create sample-ms \
        --project=sample-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/management-servers/create)

---
### `gcloud backup-dr management-servers delete`

Delete the specified Management Server

Delete the specified Management Server.

**Synopsis:**
```
gcloud backup-dr management-servers delete
    (MANAGEMENT_SERVER : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management Server resource - Name of the management server to delete.
Before you delete, take a look at the prerequisites here
(https://cloud.google.com/backup-disaster-recovery/docs/configuration/decommission).
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_server on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_SERVER
     ID of the Management Server or fully qualified identifier for the
     Management Server.

     To set the name attribute:
     + provide the argument management_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the Management Server.

     To set the location attribute:
     + provide the argument management_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a management server sample-ms in project sample-project and
location us-central1 , run:

    $ gcloud backup-dr management-servers delete sample-ms \
        --project=sample-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/management-servers/delete)

---
### `gcloud backup-dr management-servers describe`

Show details of the management server

Show all configuration data associated with the specified management
server.

**Synopsis:**
```
gcloud backup-dr management-servers describe
    (MANAGEMENT_SERVER : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Management server resource - Name of the management server to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument management_server on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MANAGEMENT_SERVER
     ID of the management_server or fully qualified identifier for the
     management_server.

     To set the management_server attribute:
     + provide the argument management_server on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument management_server on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To view details for management server 'MANAGEMENT_SERVER', run:

    $ gcloud backup-dr management-servers describe MANAGEMENT_SERVER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/management-servers/describe)

---
### `gcloud backup-dr management-servers list`

List management servers in the project

List management servers in the project. Currently, a project can have only
one management server.

**Synopsis:**
```
gcloud backup-dr management-servers list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + default is all locations . |


**Examples:**
```bash
To list management servers for all locations, run:

    $ gcloud backup-dr management-servers list

To list management servers in a location my-location, run:

    $ gcloud backup-dr management-servers list --location=my-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/management-servers/list)

---
# gcloud oracle-database odb-networks

manage Odb Network resources

### `gcloud oracle-database odb-networks create`

Create a new OdbNetwork

Create a new OdbNetwork.

**Synopsis:**
```
gcloud oracle-database odb-networks create
    (ODB_NETWORK : --location=LOCATION) --network=NETWORK [--async]
    [--gcp-oracle-zone=GCP_ORACLE_ZONE] [--labels=[LABELS,...]]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OdbNetwork resource - Identifier. The name of the OdbNetwork resource in
the following format:
projects/{project}/locations/{region}/odbNetworks/{odb_network} The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument odb_network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ODB_NETWORK
     ID of the odbNetwork or fully qualified identifier for the
     odbNetwork.

     To set the odb_network attribute:
     + provide the argument odb_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the odbNetwork resource.

     To set the location attribute:
     + provide the argument odb_network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | _[This must be specified.]_ ID of the network or fully qualified identifier for the network. To set the network attribute: + provide the argument --network on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--gcp-oracle-zone` | GCP_ORACLE_ZONE |  | The GCP Oracle zone where OdbNetwork is hosted. Example: us-east4-b-r2. If not specified, the system will pick a zone based on availability. |
| `--labels` | [LABELS,...] |  | Labels or tags associated with the resource. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create OdbNetwork with id my-odbnetwork with network
projects/my-project/locations/global/networks/default in the location
us-east4. run:

    $ gcloud oracle-database odb-networks create my-odbnetwork \
        --location=us-east4 \
        --network=projects/my-project/locations/global/networks/default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/create)

---
### `gcloud oracle-database odb-networks delete`

Delete an OdbNetwork

Delete an OdbNetwork.

**Synopsis:**
```
gcloud oracle-database odb-networks delete
    (ODB_NETWORK : --location=LOCATION) [--async] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OdbNetwork resource - The name of the resource in the following format:
projects/{project}/locations/{location}/odbNetworks/{odb_network}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument odb_network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ODB_NETWORK
     ID of the odbNetwork or fully qualified identifier for the
     odbNetwork.

     To set the odb_network attribute:
     + provide the argument odb_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the odbNetwork resource.

     To set the location attribute:
     + provide the argument odb_network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete an OdbNetwork with id my-odbnetwork in the location us-east4,
run:

    $ gcloud oracle-database odb-networks delete my-odbnetwork \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/delete)

---
### `gcloud oracle-database odb-networks describe`

Get details of an OdbNetwork

Get details of an OdbNetwork.

**Synopsis:**
```
gcloud oracle-database odb-networks describe
    (ODB_NETWORK : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OdbNetwork resource - The name of the OdbNetwork in the following format:
projects/{project}/locations/{location}/odbNetworks/{odb_network}. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument odb_network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ODB_NETWORK
     ID of the odbNetwork or fully qualified identifier for the
     odbNetwork.

     To set the odb_network attribute:
     + provide the argument odb_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the odbNetwork resource.

     To set the location attribute:
     + provide the argument odb_network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get an OdbNetwork with id my-odbnetwork in the location us-east4, run:

    $ gcloud oracle-database odb-networks describe my-odbnetwork \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/describe)

---
### `gcloud oracle-database odb-networks list`

List all OdbNetworks

List all OdbNetworks.

**Synopsis:**
```
gcloud oracle-database odb-networks list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all OdbNetworks in the location us-east4, run:

    $ gcloud oracle-database odb-networks list --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/list)

---

## `gcloud oracle-database odb-networks odb-subnets` — manage Odb Subnet resources
### `gcloud oracle-database odb-networks odb-subnets create`

Create a new OdbSubnet

Create a new OdbSubnet.

**Synopsis:**
```
gcloud oracle-database odb-networks odb-subnets create
    (ODB_SUBNET : --location=LOCATION --odb-network=ODB_NETWORK)
    --cidr-range=CIDR_RANGE --purpose=PURPOSE [--async]
    [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OdbSubnet resource - Identifier. The name of the OdbSubnet resource in the
following format:
projects/{project}/locations/{location}/odbNetworks/{odb_network}/odbSubnets/{odb_subnet}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument odb_subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ODB_SUBNET
     ID of the odbSubnet or fully qualified identifier for the odbSubnet.

     To set the odb_subnet attribute:
     + provide the argument odb_subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the odbSubnet resource.

     To set the location attribute:
     + provide the argument odb_subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --odb-network=ODB_NETWORK
     The odbNetwork id of the odbSubnet resource.

     To set the odb-network attribute:
     + provide the argument odb_subnet on the command line with a fully
       specified name;
     + provide the argument --odb-network on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cidr-range` | CIDR_RANGE |  | The CIDR range of the subnet. |
| `--purpose` | one of: backup-subnet Subnet to be used for backup |  | Purpose of the subnet. PURPOSE must be one of: backup-subnet Subnet to be used for backup. client-subnet Subnet to be used for client connections. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [LABELS,...] |  | Labels or tags associated with the resource. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To create OdbSubnet with id my-odbsubnet with cidr-range 10.0.10.0/24 and
the purpose of subnet is for client connections CLIENT_SUBNET in the
location us-east4 for a given OdbNetwork with id my-odbnetwork. run:

    $ gcloud oracle-database odb-networks odb-subnets create \
        my-odbsubnet --odb-network=my-odbnetwork \
        --cidr-range=10.0.10.0/24 --purpose=CLIENT_SUBNET \
        --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/odb-subnets/create)

---
### `gcloud oracle-database odb-networks odb-subnets delete`

Delete an OdbSubnet

Delete an OdbSubnet.

**Synopsis:**
```
gcloud oracle-database odb-networks odb-subnets delete
    (ODB_SUBNET : --location=LOCATION --odb-network=ODB_NETWORK) [--async]
    [--request-id=REQUEST_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OdbSubnet resource - The name of the resource in the following format:
projects/{project}/locations/{region}/odbNetworks/{odb_network}/odbSubnets/{odb_subnet}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument odb_subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ODB_SUBNET
     ID of the odbSubnet or fully qualified identifier for the odbSubnet.

     To set the odb_subnet attribute:
     + provide the argument odb_subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the odbSubnet resource.

     To set the location attribute:
     + provide the argument odb_subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --odb-network=ODB_NETWORK
     The odbNetwork id of the odbSubnet resource.

     To set the odb-network attribute:
     + provide the argument odb_subnet on the command line with a fully
       specified name;
     + provide the argument --odb-network on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--request-id` | REQUEST_ID |  | An optional ID to identify the request. This value is used to identify duplicate requests. If you make a request with the same request ID and the original request is still in progress or completed, the server ignores the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |


**Examples:**
```bash
To delete an OdbSubnet with id my-odbsubnet in the location us-east4 for a
given OdbNetwork with id my-odbnetwork, run:

    $ gcloud oracle-database odb-networks odb-subnets delete \
        my-odbsubnet --odb-network=my-odbnetwork --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/odb-subnets/delete)

---
### `gcloud oracle-database odb-networks odb-subnets describe`

Get details of an OdbSubnet

Get details of an OdbSubnet.

**Synopsis:**
```
gcloud oracle-database odb-networks odb-subnets describe
    (ODB_SUBNET : --location=LOCATION --odb-network=ODB_NETWORK)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OdbSubnet resource - The name of the OdbSubnet in the following format:
projects/{project}/locations/{location}/odbNetworks/{odb_network}/odbSubnets/{odb_subnet}.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument odb_subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ODB_SUBNET
     ID of the odbSubnet or fully qualified identifier for the odbSubnet.

     To set the odb_subnet attribute:
     + provide the argument odb_subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the odbSubnet resource.

     To set the location attribute:
     + provide the argument odb_subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --odb-network=ODB_NETWORK
     The odbNetwork id of the odbSubnet resource.

     To set the odb-network attribute:
     + provide the argument odb_subnet on the command line with a fully
       specified name;
     + provide the argument --odb-network on the command line.
```

**Examples:**
```bash
To get an OdbSubnet with id my-odbsubnet in the location us-east4 for a
given OdbNetwork with id my-odbnetwork, run:

    $ gcloud oracle-database odb-networks odb-subnets describe \
        my-odbsubnet --odb-network=my-odbnetwork --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/odb-subnets/describe)

---
### `gcloud oracle-database odb-networks odb-subnets list`

List all OdbSubnets

List all OdbSubnets.

**Synopsis:**
```
gcloud oracle-database odb-networks odb-subnets list
    (--odb-network=ODB_NETWORK : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--odb-network` | ODB_NETWORK |  | _[This must be specified.]_ ID of the odbNetwork or fully qualified identifier for the odbNetwork. To set the odb-network attribute: + provide the argument --odb-network on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the odbNetwork resource. To set the location attribute: + provide the argument --odb-network on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all OdbSubnets in the location us-east4 for a given OdbNetwork with
id my-odbnetwork, run:

    $ gcloud oracle-database odb-networks odb-subnets list \
        --odb-network=my-odbnetwork --location=us-east4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/oracle-database/odb-networks/odb-subnets/list)

---
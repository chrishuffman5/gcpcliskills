# gcloud vmware private-connections

manage Private Connections in Google Cloud VMware Engine

### `gcloud vmware private-connections create`

Create a Google Cloud Private Connection

Creates a new private connection to connect VMware Engine Network to the
specified VPC network. This establishes private IP connectivity between the
VPC network and all the VMware Private Clouds attached to the VMware Engine
Network. Private connection creation is considered finished when the
connection is in ACTIVE state. Check the progress of the private connection
using gcloud vmware private-connections list.

**Synopsis:**
```
gcloud vmware private-connections create
    (PRIVATE_CONNECTION : --location=LOCATION)
    --service-project=SERVICE_PROJECT --type=TYPE
    --vmware-engine-network=VMWARE_ENGINE_NETWORK [--async]
    [--description=DESCRIPTION] [--routing-mode=ROUTING_MODE]
    [--service-network=SERVICE_NETWORK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private Connection resource - private_connection. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the Private Connection or fully qualified identifier for the
     Private Connection.

     To set the private-connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-project` | SERVICE_PROJECT |  | Project ID or project number of the service network. |
| `--type` | one of: DELL_POWERSCALE Peering connection used for connecting to Dell PowerScale |  | Type of private connection. TYPE must be one of: DELL_POWERSCALE Peering connection used for connecting to Dell PowerScale. NETAPP_CLOUD_VOLUMES Peering connection used for connecting to NetApp Cloud Volumes. PRIVATE_SERVICE_ACCESS Peering connection used for establishing private services access (https://cloud.google.com/vpc/docs/private-services-access). THIRD_PARTY_SERVICE Peering connection used for connecting to third-party services. Most third-party services require manual setup of reverse peering on the VPC network associated with the third-party service. |
| `--vmware-engine-network` | VMWARE_ENGINE_NETWORK |  | Resource ID of the legacy VMware Engine network. Provide the {vmware_engine_network_id}, which will be in the form of {location}-default. The {location} is the same as the location specified in the private connection resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the private connection. |
| `--routing-mode` | one of: GLOBAL, REGIONAL |  | Type of the routing mode. Default value is set to GLOBAL. For type=PRIVATE_SERVICE_ACCESS, this field can be set to GLOBAL or REGIONAL, for other types only GLOBAL is supported. ROUTING_MODE must be one of: GLOBAL, REGIONAL. |
| `--service-network` | SERVICE_NETWORK |  | Resource ID of the service network to connect with the VMware Engine network to create a private connection. * For type=PRIVATE_SERVICE_ACCESS, this field represents service networking VPC. In this case the field value will be automatically set to servicenetworking and cannot be changed. * For type=NETAPP_CLOUD_VOLUME, this field represents NetApp service VPC. In this case the field value will be automatically set to netapp-tenant-vpc and cannot be changed. * For type=DELL_POWERSCALE, this field represents Dell service VPC. In this case the field value will be automatically set to dell-tenant-vpc and cannot be changed. * For type=THIRD_PARTY_SERVICE, this field could represent a consumer VPC or any other producer VPC to which the VMware Engine Network needs to be connected. service-network field is required for this type. |


**Examples:**
```bash
To create a Private Connection of type PRIVATE_SERVICE_ACCESS, first obtain
the service-project by listing vpc-peerings, run:

    $ gcloud compute networks peerings list --network=my-vpc \
        --project=my-project

where my-vpc is the VPC on which a private service access connection is
created and project is the one in which the private connection will be
created.

The response will be of this format:

NAME NETWORK PEER_PROJECT

servicenetworking-googleapis-com my-vpc td096d594ece09650-tp

The PEER_PROJECT field in the output of the command will provide the value
for the service-project required for creating the private connection.

To create a Private Connection called my-private-connection of type
PRIVATE_SERVICE_ACCESS in project my-project and region us-west1 with
routing_mode REGIONAL to connect service networking VPC from project
td096d594ece09650-tp to legacy VMware Engine Network us-west1-default, run:

    $ gcloud vmware private-connections create my-private-connection \
        --location=us-west1 --project=my-project \
        --vmware-engine-network=us-west1-default \
        --description="A short description for the new private \
    connection" --routing-mode=REGIONAL \
        --service-project=td096d594ece09650-tp \
        --type=PRIVATE_SERVICE_ACCESS

Or:

    $ gcloud vmware private-connections create my-private-connection \
        --vmware-engine-network=us-west1-default \
        --description="A short description for the new private \
    connection" --routing-mode=REGIONAL \
        --service-project=td096d594ece09650-tp \
        --type=PRIVATE_SERVICE_ACCESS

    In the second example, the project and location are taken from gcloud properties core/project and compute/region, respectively.

To create a Private Connection called my-private-connection of type
THIRD_PARTY_SERVICE in project my-project and region us-west1 to connect
VPC my-service-network from project td096d594ece09650-tp to legacy VMware
Engine Network us-west1-default, run:

    $ gcloud vmware private-connections create my-private-connection \
        --location=us-west1 --project=my-project \
        --vmware-engine-network=us-west1-default \
        --description="A short description for the new private \
    connection" --service-network=my-service-network \
        --service-project=td096d594ece09650-tp \
        --type=THIRD_PARTY_SERVICE

Or:

    $ gcloud vmware private-connections create my-private-connection \
        --vmware-engine-network=us-west1-default \
        --description="A short description for the new private \
    connection" --service-network=my-service-network \
        --service-project=td096d594ece09650-tp \
        --type=THIRD_PARTY_SERVICE

    In the above example, the project and location are taken from gcloud properties core/project and compute/region, respectively.

If you try to create a private connection of type=THIRD_PARTY_SERVICE, and
do not provide the service-network field, an error will be thrown with the
message:

Missing required argument [--service-network]: For private connection of
type THIRD_PARTY_SERVICE, service-network field is required
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-connections/create)

---
### `gcloud vmware private-connections delete`

Delete a Google Cloud Private Connection

Delete a Private Connection. When a private connection is deleted for a
VMware Engine network, the connected network becomes inaccessible to that
VMware Engine network.

**Synopsis:**
```
gcloud vmware private-connections delete
    (PRIVATE_CONNECTION : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private Connection resource - private_connection. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the Private Connection or fully qualified identifier for the
     Private Connection.

     To set the private-connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a Private Connection resource called my-private-connection in
project my-project and region us-west1, run:

    $ gcloud vmware private-connections delete my-private-connection \
        --location=us-west1 --project=my-project

Or:

    $ gcloud vmware private-connections delete my-private-connection

In the second example, the project and the location is taken from gcloud
properties core/project and compute/region, respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-connections/delete)

---
### `gcloud vmware private-connections describe`

Describe a Google Cloud Private Connection

Describe a Private Connection by its resource name. It contains details of
the private connection, such as service_network, vmware_engine_network,
routing_mode and state.

**Synopsis:**
```
gcloud vmware private-connections describe
    (PRIVATE_CONNECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private Connection resource - private_connection. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the Private Connection or fully qualified identifier for the
     Private Connection.

     To set the private-connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To get the information about a private connection resource called
my-private-connection in project my-project and region us-west1, run:

    $ gcloud vmware private-connections describe my-private-connection \
        --location=us-west1 --project=my-project

Or:

    $ gcloud vmware private-connections describe my-private-connection

In the second example, the project and location are taken from gcloud
properties core/project and compute/region, respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-connections/describe)

---
### `gcloud vmware private-connections list`

List Google Cloud Private Connections

Lists VMware Engine private connections.

**Synopsis:**
```
gcloud vmware private-connections list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the regional location or fully qualified identifier for the regional location. To set the location attribute: + provide the argument --location on the command line; + set the property compute/region. |


**Examples:**
```bash
To list private connections in project my-project and region us-west1
sorted from oldest to newest, run:

    $ gcloud vmware private-connections list --location=us-west1 \
        --project=my-project --sort-by=~create_time

Or:

    $ gcloud vmware private-connections list --sort-by=~create_time

In the second example, the project and the location are taken from gcloud
properties core/project and compute/region, respectively.

To list private connections in project my-project from all regions, run:

    $ gcloud vmware private-connections list --location=- \
        --project=my-project

Or:

    $ gcloud vmware private-connections list --location=-

In the last example, the project is taken from gcloud properties
core/project.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-connections/list)

---
### `gcloud vmware private-connections update`

Update a Google Cloud Private Connection

Updates a VMware Engine private connection. Only description and
routing-mode can be updated.

**Synopsis:**
```
gcloud vmware private-connections update
    (PRIVATE_CONNECTION : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--routing-mode=ROUTING_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Private Connection resource - private_connection. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument private_connection on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PRIVATE_CONNECTION
     ID of the Private Connection or fully qualified identifier for the
     Private Connection.

     To set the private-connection attribute:
     + provide the argument private_connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument private_connection on the command line with
       a fully specified name;
     + provide the argument --location on the command line;
     + set the property compute/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Updated description for this Private Connection. |
| `--routing-mode` | one of: GLOBAL, REGIONAL |  | Updated routing mode for this Private Connection. ROUTING_MODE must be one of: GLOBAL, REGIONAL. |


**Examples:**
```bash
To update a private connection named my-private-connection in project
my-project and region us-west1 by changing its description to Updated
description for the private connection and routing-mode to GLOBAL, run:

    $ gcloud vmware private-connections update my-private-connection \
        --location=us-west1 --project=my-project \
        --description="Updated description for the private connection" \
        --routing-mode=GLOBAL

Or:

    $ gcloud vmware private-connections update my-private-connection \
        --description="Updated description for the private connection" \
        --routing-mode=GLOBAL

In the second example, the project and location are taken from gcloud
properties core/project and compute/regions, respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-connections/update)

---

## `gcloud vmware private-connections routes` — manage private connection peering routes in Google Cloud VMware Engine
### `gcloud vmware private-connections routes list`

List Google Cloud private connection peering routes

Lists the private connection routes exchanged over a peering connection.

**Synopsis:**
```
gcloud vmware private-connections routes list
    (--private-connection=PRIVATE_CONNECTION : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--private-connection` | PRIVATE_CONNECTION |  | _[This must be specified.]_ ID of the Private Connection or fully qualified identifier for the Private Connection. To set the private-connection attribute: + provide the argument --private-connection on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The resource name of the location. To set the location attribute: + provide the argument --private-connection on the command line with a fully specified name; + provide the argument --location on the command line; + set the property compute/region. |


**Examples:**
```bash
To list all the peering routes of private connection called
my-private-connection in project my-project and region us-west1, run:

    $ gcloud vmware private-connections routes list \
        --private-connection=my-private-connection --location=us-west1 \
        --project=my-project

Or:

    $ gcloud vmware private-connections routes list \
        --private-connection=my-private-connection

In the last example, the project and the location are taken from gcloud
properties core/project and compute/region, respectively.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/private-connections/routes/list)

---
# gcloud vmware network-peerings

manage VMware Engine VPC peering using Google Cloud VMware Engine

### `gcloud vmware network-peerings create`

Create a VMware Engine VPC network peering

Create a VMware Engine VPC network peering. VPC network peering creation is
considered finished when the network peering is in ACTIVE state. Check the
progress of a VPC network peering using gcloud vmware network-peerings
list.

**Synopsis:**
```
gcloud vmware network-peerings create
    (NETWORK_PEERING : --location=LOCATION) --peer-network=PEER_NETWORK
    --peer-network-type=PEER_NETWORK_TYPE
    --vmware-engine-network=VMWARE_ENGINE_NETWORK [--async]
    [--description=DESCRIPTION] [--no-exchange-subnet-routes]
    [--no-export-custom-routes] [--no-export-custom-routes-with-public-ip]
    [--no-import-custom-routes] [--no-import-custom-routes-with-public-ip]
    [--peer-mtu=PEER_MTU] [--peer-project=PEER_PROJECT]
    [--vmware-engine-network-project=VMWARE_ENGINE_NETWORK_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine VPC network peering resource - network_peering. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument network_peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_PEERING
     ID of the VMware Engine VPC network peering or fully qualified
     identifier for the VMware Engine VPC network peering.

     To set the network-peering attribute:
     + provide the argument network_peering on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_peering on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default).
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-network` | PEER_NETWORK |  | ID of the network to peer with the VMware Engine network. The peer network can be a consumer VPC network or another VMware Engine network. |
| `--peer-network-type` | one of: PEER_NETWORK_TYPE_UNSPECIFIED, STANDARD, VMWARE_ENGINE_NETWORK, PRIVATE_SERVICES_ACCESS, NETAPP_CLOUD_VOLUMES, THIRD_PARTY_SERVICE, DELL_POWERSCALE, GOOGLE_CLOUD_NETAPP_VOLUMES |  | Type of the VPC network to peer with the VMware Engine network. PEER_NETWORK_TYPE must be one of the following: * STANDARD: Peering connection used for connecting to another VPC network established by the same user. For example, a peering connection to another VPC network in the same project or to an on-premises network. * VMWARE_ENGINE_NETWORK: Peering connection used for connecting to another VMware Engine network. * PRIVATE_SERVICES_ACCESS: Peering connection used for establishing private services access. * NETAPP_CLOUD_VOLUMES: Peering connection used for connecting to NetApp Cloud Volumes. * THIRD_PARTY_SERVICE: Peering connection used for connecting to third-party services. Most third-party services require manual setup of reverse peering on the VPC network associated with the third-party service. * DELL_POWERSCALE: Peering connection used for connecting to Dell PowerScale Filers. * GOOGLE_CLOUD_NETAPP_VOLUMES: Peering connection used for connecting to Google Cloud NetApp Volumes. PEER_NETWORK_TYPE must be one of: PEER_NETWORK_TYPE_UNSPECIFIED, STANDARD, VMWARE_ENGINE_NETWORK, PRIVATE_SERVICES_ACCESS, NETAPP_CLOUD_VOLUMES, THIRD_PARTY_SERVICE, DELL_POWERSCALE, GOOGLE_CLOUD_NETAPP_VOLUMES. |
| `--vmware-engine-network` | VMWARE_ENGINE_NETWORK |  | ID of the VMware Engine network to attach the new peering to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | User-provided description of the VPC network peering. |
| `--exchange-subnet-routes` |  |  | True if full-mesh connectivity is created and managed automatically between peered VPC networks; false otherwise. This field is always true because Google Compute Engine automatically creates and manages subnetwork routes between two VPC networks when the peering state is ACTIVE. Enabled by default, use --no-exchange-subnet-routes to disable. |
| `--export-custom-routes` |  |  | True if custom routes are exported to the peered VPC network; false otherwise. The default value is true. Enabled by default, use --no-export-custom-routes to disable. |
| `--export-custom-routes-with-public-ip` |  |  | True if all subnet routes with public IP address range are exported; false otherwise. The default value is true. Enabled by default, use --no-export-custom-routes-with-public-ip to disable. |
| `--import-custom-routes` |  |  | True if custom routes are imported to the peered VPC network; false otherwise. The default value is true. Enabled by default, use --no-import-custom-routes to disable. |
| `--import-custom-routes-with-public-ip` |  |  | True if all subnet routes with public IP address range are imported; false otherwise. The default value is true. Enabled by default, use --no-import-custom-routes-with-public-ip to disable. |
| `--peer-mtu` | PEER_MTU |  | Maximum transmission unit (MTU) in bytes. |
| `--peer-project` | PEER_PROJECT |  | Project ID or project number of the peer network. Use this flag when the peer network is in another project. |
| `--vmware-engine-network-project` | VMWARE_ENGINE_NETWORK_PROJECT |  | Project of the VMware Engine network to attach the new peering to. Use this flag when the VMware Engine network is in another project. |


**Examples:**
```bash
To create a VPC network peering called new-peering that connects the VMware
Engine network my-vmware-engine-network with another VMware Engine network
another-vmware-engine-network from project another-project, run:

    $ gcloud vmware network-peerings create new-peering \
        --vmware-engine-network=my-vmware-engine-network \
        --peer-network=another-vmware-engine-network \
        --peer-network-type=VMWARE_ENGINE_NETWORK \
        --peer-project=another-project

In this example, the project is taken from gcloud properties core/project
and location is taken as global.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-peerings/create)

---
### `gcloud vmware network-peerings delete`

Delete a Google Cloud VMware Engine VPC network peering

Delete a VPC network peering. After you delete a VPC network peering, you
won't be able to access the corresponding VMware Engine network through the
peer network.

**Synopsis:**
```
gcloud vmware network-peerings delete
    (NETWORK_PEERING : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine VPC network peering resource - network_peering. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument network_peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_PEERING
     ID of the VMware Engine VPC network peering or fully qualified
     identifier for the VMware Engine VPC network peering.

     To set the network-peering attribute:
     + provide the argument network_peering on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_peering on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a VPC network peering with name my-peering, run:

    $ gcloud vmware network-peerings delete my-peering

In this example, the project is taken from gcloud properties core/project
and location is taken as global.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-peerings/delete)

---
### `gcloud vmware network-peerings describe`

Describe a Google Cloud VMware Engine VPC network peering

Get information about a VPC network peering.

**Synopsis:**
```
gcloud vmware network-peerings describe
    (NETWORK_PEERING : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine VPC network peering resource - network_peering. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument network_peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_PEERING
     ID of the VMware Engine VPC network peering or fully qualified
     identifier for the VMware Engine VPC network peering.

     To set the network-peering attribute:
     + provide the argument network_peering on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_peering on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default).
```

**Examples:**
```bash
To get information about a VPC network peering called new-peering, run:

    $ gcloud vmware network-peerings describe new-peering

In this example, the project is taken from gcloud properties core/project
and location is taken as global.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-peerings/describe)

---
### `gcloud vmware network-peerings list`

List Google Cloud VMware Engine VPC network peerings

List VPC network peerings across all locations in your project.

**Synopsis:**
```
gcloud vmware network-peerings list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set location as 'global' (default). |


**Examples:**
```bash
To list all the VPC network peerings created on or after April 12, 2021,
sorted from oldest to newest, run:

    $ gcloud vmware network-peerings list \
        --filter="createTime > 2021-04-12T00:00:00.00Z" \
        --sort-by=createTime

In this example, the location is taken as global.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-peerings/list)

---
### `gcloud vmware network-peerings update`

Update a Google Cloud VMware Engine VPC network peering

Update a VMware Engine VPC network peering description.

**Synopsis:**
```
gcloud vmware network-peerings update
    (NETWORK_PEERING : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine VPC network peering resource - network_peering. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument network_peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_PEERING
     ID of the VMware Engine VPC network peering or fully qualified
     identifier for the VMware Engine VPC network peering.

     To set the network-peering attribute:
     + provide the argument network_peering on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument network_peering on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Updated description for this VPC network peering. |


**Examples:**
```bash
To update only the description of a VPC network peering named my-peering to
Example description, run:

    $ gcloud vmware network-peerings update my-peering \
        --description="Example description"

In this example, the project is taken from gcloud properties core/project
and location is taken as global.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-peerings/update)

---

## `gcloud vmware network-peerings routes` — manage VMware Engine VPC peering routes using Google Cloud VMware Engine
### `gcloud vmware network-peerings routes list`

List Google Cloud VMware Engine VPC network peering routes

List VPC network peering routes across all locations in your project.

**Synopsis:**
```
gcloud vmware network-peerings routes list
    (--network-peering=NETWORK_PEERING : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network-peering` | NETWORK_PEERING |  | _[This must be specified.]_ ID of the VMware Engine VPC network peering or fully qualified identifier for the VMware Engine VPC network peering. To set the network-peering attribute: + provide the argument --network-peering on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The resource name of the location. To set the location attribute: + provide the argument --network-peering on the command line with a fully specified name; + provide the argument --location on the command line; + set location as 'global' (default). |


**Examples:**
```bash
To list peering routes imported from peer network via my-peering:

    $ gcloud vmware network-peerings routes list \
        --network-peering=my-peering --filter="direction=INCOMING"

To list peering routes exported to peer network via my-peering:

    $ gcloud vmware network-peerings routes list \
        --network-peering=my-peering --filter="direction=OUTGOING"

In above examples, the location is taken as global.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/network-peerings/routes/list)

---
# gcloud edge-cloud networking

manage Distributed Cloud Edge Network resources


## `gcloud edge-cloud networking interconnects` — manage Distributed Cloud Edge Network interconnects
### `gcloud edge-cloud networking interconnects describe`

Show details about the Distributed Cloud Edge Network interconnect

Show details about the Distributed Cloud Edge Network interconnect.

**Synopsis:**
```
gcloud edge-cloud networking interconnects describe
    (INTERCONNECT : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Interconnect resource - The interconnect you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument interconnect on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCONNECT
     ID of the interconnect or fully qualified identifier for the
     interconnect.

     To set the interconnect attribute:
     + provide the argument interconnect on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument interconnect on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument interconnect on the command line with a
       fully specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To show details about an interconnect called 'my-interconnect1' in edge
zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking interconnects describe \
        my-interconnect1 --location=us-central1 \
        --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/describe)

---
### `gcloud edge-cloud networking interconnects get-diagnostics`

Get the diagnostics of a specified Distributed Cloud Edge Network interconnect

Get the diagnostics of a specified Distributed Cloud Edge Network
interconnect.

**Synopsis:**
```
gcloud edge-cloud networking interconnects get-diagnostics
    (INTERCONNECT : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Interconnect resource - The interconnect to get diagnostics. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument interconnect on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCONNECT
     ID of the interconnect or fully qualified identifier for the
     interconnect.

     To set the interconnect attribute:
     + provide the argument interconnect on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the interconnect.

     To set the location attribute:
     + provide the argument interconnect on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the interconnect.

     To set the zone attribute:
     + provide the argument interconnect on the command line with a
       fully specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To get the diagnostics of the Distributed Cloud Edge Network interconnect
'my-interconnect' in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking interconnects get-diagnostics \
      my-interconnect --location=us-central1 \
      --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/get-diagnostics)

---
### `gcloud edge-cloud networking interconnects list`

List Distributed Cloud Edge Network interconnects

List Distributed Cloud Edge Network interconnects.

**Synopsis:**
```
gcloud edge-cloud networking interconnects list
    (--zone=ZONE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The global location name. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list the Distributed Cloud Edge Network interconnects in edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking interconnects list \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/list)

---

## `gcloud edge-cloud networking interconnects attachments` — manage Distributed Cloud Edge Network interconnect attachments
### `gcloud edge-cloud networking interconnects attachments delete`

Delete a Distributed Cloud Edge Network interconnect attachment

Delete a Distributed Cloud Edge Network interconnect attachment.

**Synopsis:**
```
gcloud edge-cloud networking interconnects attachments delete
    (INTERCONNECT_ATTACHMENT : --location=LOCATION --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Interconnect attachment resource - Distributed Cloud Edge Network
interconnectAttachment to delete. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument interconnect_attachment on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCONNECT_ATTACHMENT
     ID of the interconnect attachment or fully qualified identifier for
     the interconnect attachment.

     To set the interconnect_attachment attribute:
     + provide the argument interconnect_attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument interconnect_attachment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument interconnect_attachment on the command line
       with a fully specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an interconnect attachment called 'my-attachment' in edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking interconnects attachments delete \
        my-attachment --location=us-central1 \
        --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/attachments/delete)

---
### `gcloud edge-cloud networking interconnects attachments describe`

Show details about a Distributed Cloud Edge Network interconnect attachment

Show details about a Distributed Cloud Edge Network interconnect
attachment.

**Synopsis:**
```
gcloud edge-cloud networking interconnects attachments describe
    (INTERCONNECT_ATTACHMENT : --location=LOCATION --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Interconnect attachment resource - The interconnect attachment you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument interconnect_attachment on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCONNECT_ATTACHMENT
     ID of the interconnect attachment or fully qualified identifier for
     the interconnect attachment.

     To set the interconnect_attachment attribute:
     + provide the argument interconnect_attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument interconnect_attachment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument interconnect_attachment on the command line
       with a fully specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To show details about an interconnect attachment called 'my-attachment' in
edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking interconnects attachments describe \
        my-attachment --location=us-central1 \
        --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/attachments/describe)

---
### `gcloud edge-cloud networking interconnects attachments list`

List Distributed Cloud Edge Network interconnect attachments

List Distributed Cloud Edge Network interconnect attachments.

**Synopsis:**
```
gcloud edge-cloud networking interconnects attachments list
    (--zone=ZONE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The global location name. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list the interconnect attachments in edge zone 'us-central1-edge-den1',
run:

    $ gcloud edge-cloud networking interconnects attachments list \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/attachments/list)

---

## `gcloud edge-cloud networking interconnects attachments dedicated` — manage Distributed Cloud Edge Network dedicated interconnect attachments
### `gcloud edge-cloud networking interconnects attachments dedicated create`

Create a Distributed Cloud Edge Network interconnect attachment

Create a new dedicated Distributed Cloud Edge Network interconnect
attachment.

**Synopsis:**
```
gcloud edge-cloud networking interconnects attachments dedicated create
    (INTERCONNECT_ATTACHMENT : --location=LOCATION --zone=ZONE)
    --interconnect=INTERCONNECT [--async] [--description=DESCRIPTION]
    [--labels=[KEY=VALUE,...]] [--mtu=MTU; default=1500]
    [--network=NETWORK] [--vlan-id=VLAN_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Interconnect attachment resource - Distributed Cloud Edge Network
interconnectAttachment to create. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument interconnect_attachment on the command line with
   a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  INTERCONNECT_ATTACHMENT
     ID of the interconnect attachment or fully qualified identifier for
     the interconnect attachment.

     To set the interconnect_attachment attribute:
     + provide the argument interconnect_attachment on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument interconnect_attachment on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument interconnect_attachment on the command line
       with a fully specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interconnect` | INTERCONNECT |  | The underlying interconnect object that this attachment's traffic will traverse through. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect attachment. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--mtu` | MTU | 1500 | Maximum transmission unit (MTU) is the size of the largest IP packet that can be transmitted on this attachment. Default value is 1500 bytes, and the valid values are 1500 and 9000. |
| `--network` | NETWORK |  | The network to use for dynamic routing. |
| `--vlan-id` | VLAN_ID |  | The ID of the vlan to tag the subnetwork. Default value is 0. |


**Examples:**
```bash
To create a dedicated interconnect attachment called 'my-attachment' in
edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking interconnects attachments dedicated \
        create my-attachment --location=us-central1 \
        --zone=us-central1-edge-den1 --interconnect=INTERCONNECT-LINK1 \
        --network=my-edge-network --vlan-id=200 --mtu=1500
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/interconnects/attachments/dedicated/create)

---

## `gcloud edge-cloud networking networks` — manage Distributed Cloud Edge Network networks
### `gcloud edge-cloud networking networks create`

Create a Distributed Cloud Edge Network network

Create a new Distributed Cloud Edge Network network resource.

**Synopsis:**
```
gcloud edge-cloud networking networks create
    (NETWORK : --location=LOCATION --zone=ZONE) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]] [--mtu=MTU]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - Distributed Cloud Edge Network network to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | An optional, textual description for the network. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet that can be transmitted on this network. Default value is 1500 bytes, and the valid values are 1500 and 9000. |


**Examples:**
```bash
To create a network called 'my-network' with MTU value of 9000 bytes in
edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking networks create my-network \
        --location=us-central1 --zone=us-central1-edge-den1 --mtu=9000
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/networks/create)

---
### `gcloud edge-cloud networking networks delete`

Delete a Distributed Cloud Edge Network network

Delete a Distributed Cloud Edge Network network.

**Synopsis:**
```
gcloud edge-cloud networking networks delete
    (NETWORK : --location=LOCATION --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - Distributed Cloud Edge Network network to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Distributed Cloud Edge Network network called 'my-network' in
edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking networks delete my-network \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/networks/delete)

---
### `gcloud edge-cloud networking networks describe`

Show details about the Distributed Cloud Edge Network network

Show details about the Distributed Cloud Edge Network network.

**Synopsis:**
```
gcloud edge-cloud networking networks describe
    (NETWORK : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - The Distributed Cloud Edge Network network you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To show details about a network called 'my-network' in edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking networks describe my-network \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/networks/describe)

---
### `gcloud edge-cloud networking networks get-status`

Get the status of a specified Distributed Cloud Edge Network network

Get the status of a specified Distributed Cloud Edge Network network.

**Synopsis:**
```
gcloud edge-cloud networking networks get-status
    (NETWORK : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - The network to get status. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the network.

     To set the location attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the network.

     To set the zone attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To get the status of the Distributed Cloud Edge Network network
'my-network' in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking networks get-status my-network \
      --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/networks/get-status)

---
### `gcloud edge-cloud networking networks list`

List Distributed Cloud Edge Network networks

List Distributed Cloud Edge Network networks.

**Synopsis:**
```
gcloud edge-cloud networking networks list
    (--zone=ZONE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The global location name. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list the Distributed Cloud Edge Network networks in edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking networks list \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/networks/list)

---

## `gcloud edge-cloud networking operations` — command group for working with Distributed Cloud Edge Network operations
### `gcloud edge-cloud networking operations describe`

Get description of a long-running edge network operation

Get information about a long-running edge network operation.

**Synopsis:**
```
gcloud edge-cloud networking operations describe
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get information about a long-running operation with name
'projects/my-project/locations/us-east1/operations/123', run the following
command:

    $ gcloud edge-cloud networking operations describe \
        projects/my-project/locations/us-east1/operations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/operations/describe)

---
### `gcloud edge-cloud networking operations wait`

Poll long-running edge network operation until it completes

Poll a long-running edge network operation until it completes. When the
operation is complete, this command will display the results of the
analysis.

**Synopsis:**
```
gcloud edge-cloud networking operations wait
    (OPERATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - ID for the operation to poll until complete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To poll a long-running edge network operation named
'projects/my-project/locations/us-east1/operations/123' until it completes,
run the following:

    $ gcloud edge-cloud networking operations wait \
        projects/my-project/locations/us-east1/operations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/operations/wait)

---

## `gcloud edge-cloud networking routers` — manage Distributed Cloud Edge Network routers
### `gcloud edge-cloud networking routers add-bgp-peer`

Add a BGP peer to a Distributed Cloud Edge Network router

Create a BGP peer to a Distributed Cloud Edge Network router

**Synopsis:**
```
gcloud edge-cloud networking routers add-bgp-peer
    (ROUTER : --location=LOCATION --zone=ZONE) --interface=INTERFACE
    --peer-asn=PEER_ASN --peer-ipv4-range=PEER_IPV4_RANGE
    --peer-name=PEER_NAME [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - The router to which we add a bgp peer. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the router.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the router.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface` | INTERFACE |  | The name of the interface for this BGP peer. |
| `--peer-asn` | PEER_ASN |  | The BGP autonomous system number (ASN) for this BGP peer. Must be a 16-bit or 32-bit private ASN as defined in https://tools.ietf.org/html/rfc6996, for example --asn=64512. |
| `--peer-ipv4-range` | PEER_IPV4_RANGE |  | The IPv4 link-local address range of the peer router. |
| `--peer-name` | PEER_NAME |  | The name of the new BGP peer being added. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create and add a BGP peer for the Distributed Cloud Edge Network router
'my-router' in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking routers add-bgp-peer my-router \
      --interface=my-int-r1 --peer-asn=33333 --peer-name=peer1 \
      --peer-ipv4-range=208.117.254.232/31 --location=us-central1 \
      --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/add-bgp-peer)

---
### `gcloud edge-cloud networking routers add-interface`

Add an interface to a Distributed Cloud Edge Network router

Create an interface to a Distributed Cloud Edge Network router.

**Synopsis:**
```
gcloud edge-cloud networking routers add-interface
    (ROUTER : --location=LOCATION --zone=ZONE)
    --interface-name=INTERFACE_NAME
    (--loopback-ip-addresses=[LOOPBACK_IP_ADDRESSES,...]
      | --subnetwork=SUBNETWORK
      | --interconnect-attachment=INTERCONNECT_ATTACHMENT
      --ip-address=IP_ADDRESS --ip-mask-length=IP_MASK_LENGTH) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - The router to which we add an interface. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the router.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the router.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface-name` | INTERFACE_NAME |  | The name of the interface being added. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create and add a northbound interface for Distributed Cloud Edge Network
router 'my-router' in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking routers add-interface my-router \
      --interface-name=my-int-r1 \
      --interconnect-attachment=my-link-attachment \
      --ip-address=208.117.254.233 --ip-mask-length=31 \
      --location=us-central1 --zone=us-central1-edge-den1

To create and add a southbound interface for Distributed Cloud Edge Network
router 'my-router' in edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking routers add-interface my-router \
     --interface-name=my-int-r2 --subnetwork=my-subnet \
     --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/add-interface)

---
### `gcloud edge-cloud networking routers create`

Create a Distributed Cloud Edge Network router

Create a new Distributed Cloud Edge Network router.

**Synopsis:**
```
gcloud edge-cloud networking routers create
    (ROUTER : --location=LOCATION --zone=ZONE) --asn=ASN --network=NETWORK
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - Distributed Cloud Edge Network router to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asn` | ASN |  | The locally assigned BGP ASN. |
| `--network` | NETWORK |  | The network that this subnetwork belongs to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | An optional, textual description for the router. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a router called 'my-router' with asn 65555 in edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking routers create my-router \
        --network=my-network --location=us-central1 \
        --zone=us-central1-edge-den1 --asn=65555
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/create)

---
### `gcloud edge-cloud networking routers delete`

Delete a Distributed Cloud Edge Network router

Delete a Distributed Cloud Edge Network router.

**Synopsis:**
```
gcloud edge-cloud networking routers delete
    (ROUTER : --location=LOCATION --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - Distributed Cloud Edge Network router to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a router called 'my-router' in edge zone 'us-central1-edge-den1',
run:

    $ gcloud edge-cloud networking routers delete my-router \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/delete)

---
### `gcloud edge-cloud networking routers describe`

Show details about the Distributed Cloud Edge Network router

Show details about the Distributed Cloud Edge Network router.

**Synopsis:**
```
gcloud edge-cloud networking routers describe
    (ROUTER : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - The router you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To show details about a router named 'my-router' in edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking routers describe my-router \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/describe)

---
### `gcloud edge-cloud networking routers get-status`

Get the status of a specified Distributed Cloud Edge Network router

Get the status of a specified Distributed Cloud Edge Network router.

**Synopsis:**
```
gcloud edge-cloud networking routers get-status
    (ROUTER : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - The router to get status. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the router.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the router.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To get the status of the Distributed Cloud Edge Network router 'my-router'
in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking routers get-status my-router \
      --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/get-status)

---
### `gcloud edge-cloud networking routers list`

List Distributed Cloud Edge Network routers

List Distributed Cloud Edge Network routers.

**Synopsis:**
```
gcloud edge-cloud networking routers list
    (--zone=ZONE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The global location name. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list the routers in edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking routers list --location=us-central1 \
        --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/list)

---
### `gcloud edge-cloud networking routers remove-bgp-peer`

Remove a BGP peer from a Distributed Cloud Edge Network router

Delete a list of BGP peer from a Distributed Cloud Edge Network router

**Synopsis:**
```
gcloud edge-cloud networking routers remove-bgp-peer
    (ROUTER : --location=LOCATION --zone=ZONE)
    (--peer-name=PEER_NAME | --peer-names=[PEER_NAME,...]) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - The router from which we delete a BGP peer. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the router.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the router.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-name` | PEER_NAME |  | _[Exactly one of these must be specified:]_ The name of the BGP peer being removed. |
| `--peer-names` | [PEER_NAME,...] |  | _[Exactly one of these must be specified:]_ The list of names for peers being removed. Only single value allowed currently. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a BGP peer 'peer1' from the Distributed Cloud Edge Network router
'my-router' in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking routers remove-bgp-peer my-router \
      --peer-name=peer1 --location=us-central1 \
      --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/remove-bgp-peer)

---
### `gcloud edge-cloud networking routers remove-interface`

Remove an interface on a Distributed Cloud Edge Network router

Remove an interface on a Distributed Cloud Edge Network router.

**Synopsis:**
```
gcloud edge-cloud networking routers remove-interface
    (ROUTER : --location=LOCATION --zone=ZONE)
    (--interface-name=INTERFACE_NAME
      | --interface-names=[INTERFACE_NAME,...]) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Router resource - The router from which we remove an interface. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument router on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTER
     ID of the router or fully qualified identifier for the router.

     To set the router attribute:
     + provide the argument router on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the router.

     To set the location attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The zone of the router.

     To set the zone attribute:
     + provide the argument router on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface-name` | INTERFACE_NAME |  | _[Exactly one of these must be specified:]_ The name of the interface being removed. |
| `--interface-names` | [INTERFACE_NAME,...] |  | _[Exactly one of these must be specified:]_ The list of names for interfaces being removed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To remove the interface 'my-int-r1' on Distributed Cloud Edge Network
router 'my-router' in edge zone 'us-central1-edge-den1' , run:

    $ gcloud edge-cloud networking routers remove-interface my-router \
      --interface-name=my-int-r1 --location=us-central1 \
      --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/routers/remove-interface)

---

## `gcloud edge-cloud networking subnets` — manage Distributed Cloud Edge Network subnets
### `gcloud edge-cloud networking subnets create`

Create a Distributed Cloud Edge Network subnet

Create a new Distributed Cloud Edge Network subnet.

**Synopsis:**
```
gcloud edge-cloud networking subnets create
    (SUBNET : --location=LOCATION --zone=ZONE) --network=NETWORK [--async]
    [--description=DESCRIPTION] [--ipv4-range=[IPV4_RANGE,...]]
    [--ipv6-range=[IPV6_RANGE,...]] [--labels=[KEY=VALUE,...]]
    [--vlan-id=VLAN_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnet resource - Distributed Cloud Edge Network subnet to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNET
     ID of the subnet or fully qualified identifier for the subnet.

     To set the subnet attribute:
     + provide the argument subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network that this subnetwork belongs to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | An optional, textual description for the subnet. |
| `--ipv4-range` | [IPV4_RANGE,...] |  | The ranges of ipv4 addresses that are owned by this subnetwork in CIDR format. |
| `--ipv6-range` | [IPV6_RANGE,...] |  | The ranges of ipv6 addresses that are owned by this subnetwork in CIDR format. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--vlan-id` | VLAN_ID |  | The ID of the VLAN to tag the subnetwork. If not specified we assign one automatically. |


**Examples:**
```bash
To create a Distributed Cloud Edge Network subnet called my-subnet with
VLAN ID and owned ip ranges specified in the edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking subnets create my-subnet \
        --network=my-network --location=us-central1 \
        --zone=us-central1-edge-den1 \
        --ipv4-range=192.168.1.1/24,172.10.10.1/24 \
        --ipv6-range=2001:db8::1/64,4001:230::1/64 --vlan-id=100 \
        --bonding-type=bonded
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/subnets/create)

---
### `gcloud edge-cloud networking subnets delete`

Delete a Distributed Cloud Edge Network subnet

Delete a Distributed Cloud Edge Network subnet.

**Synopsis:**
```
gcloud edge-cloud networking subnets delete
    (SUBNET : --location=LOCATION --zone=ZONE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnet resource - Distributed Cloud Edge Network subnet to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNET
     ID of the subnet or fully qualified identifier for the subnet.

     To set the subnet attribute:
     + provide the argument subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a subnet called 'my-subnet' in the edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking subnets delete my-subnet \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/subnets/delete)

---
### `gcloud edge-cloud networking subnets describe`

Show details about the Distributed Cloud Edge Network subnet

Show details about the Distributed Cloud Edge Network subnet.

**Synopsis:**
```
gcloud edge-cloud networking subnets describe
    (SUBNET : --location=LOCATION --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnet resource - The subnet you want to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument subnet on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNET
     ID of the subnet or fully qualified identifier for the subnet.

     To set the subnet attribute:
     + provide the argument subnet on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The global location name.

     To set the location attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --zone=ZONE
     The name of the Google Distributed Cloud Edge zone.

     To set the zone attribute:
     + provide the argument subnet on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To show details about a subnet named 'my-subnet' in the edge zone
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking subnets describe my-subnet \
        --location=us-central1 --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/subnets/describe)

---
### `gcloud edge-cloud networking subnets list`

List Distributed Cloud Edge Network subnets

List Distributed Cloud Edge Network subnets.

**Synopsis:**
```
gcloud edge-cloud networking subnets list
    (--zone=ZONE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | _[This must be specified.]_ ID of the zone or fully qualified identifier for the zone. To set the zone attribute: + provide the argument --zone on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The global location name. To set the location attribute: + provide the argument --zone on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list the subnets in the edge zone 'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking subnets list --location=us-central1 \
        --zone=us-central1-edge-den1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/subnets/list)

---

## `gcloud edge-cloud networking zones` — manage Distributed Cloud Edge Network zones
### `gcloud edge-cloud networking zones init`

Initialize a specified Distributed Cloud Edge Network zone

Initialize a specified Distributed Cloud Edge Network zone.

**Synopsis:**
```
gcloud edge-cloud networking zones init (ZONE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Zone resource - The zone to initialize. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument zone on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ZONE
     ID of the zone or fully qualified identifier for the zone.

     To set the zone attribute:
     + provide the argument zone on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the zone.

     To set the location attribute:
     + provide the argument zone on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To initialize a Distributed Cloud Edge Network zone called
'us-central1-edge-den1', run:

    $ gcloud edge-cloud networking zones init us-central1-edge-den1 \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/networking/zones/init)

---
# gcloud network-connectivity spokes

manage Network Connectivity Center spokes

### `gcloud network-connectivity spokes delete`

Delete a spoke

Delete the specified spoke.

**Synopsis:**
```
gcloud network-connectivity spokes delete SPOKE [--async]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --global on the command line;
 * provide the argument --region on the command line.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a spoke named myspoke in the us-central1 region, run:

    $ gcloud network-connectivity spokes delete myspoke \
         --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/delete)

---
### `gcloud network-connectivity spokes describe`

Describe a spoke

Retrieve and display details about a spoke.

**Synopsis:**
```
gcloud network-connectivity spokes describe SPOKE
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --global on the command line;
 * provide the argument --region on the command line.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ Indicates that the spoke is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ A Google Cloud region. To see the names of regions, see Viewing a list of available regions (https://cloud.google.com/compute/docs/regions-zones/viewing-regions-zones#viewing_a_list_of_available_regions). |


**Examples:**
```bash
To display details about a spoke named myspoke in the us-central1 region,
run:

    $ gcloud network-connectivity spokes describe myspoke \
         --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/describe)

---
### `gcloud network-connectivity spokes list`

List spokes

Retrieve and display a list of all spokes in the specified project.

**Synopsis:**
```
gcloud network-connectivity spokes list [--global | --region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ Indicates that the spoke is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ A Google Cloud region. To see the names of regions, see Viewing a list of available regions (https://cloud.google.com/compute/docs/regions-zones/viewing-regions-zones#viewing_a_list_of_available_regions). Use ``-`` to specify all regions. |


**Examples:**
```bash
To list all spokes in the us-central1 region, run:

    $ gcloud network-connectivity spokes list --region=us-central1

To list all spokes in all regions, run:

    $ gcloud network-connectivity spokes list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/list)

---

## `gcloud network-connectivity spokes linked-interconnect-attachments` — manage VLAN attachment spokes
### `gcloud network-connectivity spokes linked-interconnect-attachments create`

Create a new VLAN attachment spoke

Create a new VLAN attachment spoke
(https://cloud.google.com/network-connectivity/docs/network-connectivity-center/how-to/working-with-hubs-spokes#create-vlan-spoke).

**Synopsis:**
```
gcloud network-connectivity spokes linked-interconnect-attachments create
    (SPOKE : --region=REGION) --hub=HUB
    --interconnect-attachments=[INTERCONNECT_ATTACHMENTS,...] [--async]
    [--description=DESCRIPTION] [--group=GROUP]
    [--include-import-ranges=[INCLUDE_IMPORT_RANGES,...]]
    [--labels=[KEY=VALUE,...]] [--site-to-site-data-transfer]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to be created. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument spoke on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | Hub that the spoke will attach to. The hub must already exist. |
| `--interconnect-attachments` | [INTERCONNECT_ATTACHMENTS,...] |  | VLAN attachments that the spoke provides connectivity to. The resources must already exist. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the spoke to create. |
| `--group` | GROUP |  | The group that the spoke will be added to. The group must already exist. If unset, the spoke will be added to the ``default`` group. |
| `--include-import-ranges` | [INCLUDE_IMPORT_RANGES,...] |  | IP address range(s) allowed to be imported from hub subnets. Only ``ALL_IPV4_RANGES`` can be added to the list. If it's empty, the spoke does not import any subnets from the hub. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--site-to-site-data-transfer` |  |  | Whether to enable site-to-site data transfer for this spoke. Data transfer is available only in supported locations (https://cloud.google.com/network-connectivity/docs/network-connectivity-center/concepts/locations). |


**Examples:**
```bash
To create a spoke in region us-central1 that uses data transfer and has two
VLAN attachments, run:

    $ gcloud network-connectivity spokes \
        linked-interconnect-attachments create my-spoke \
        --hub="https://www.googleapis.com/networkconnectivity/v1/project\
    s/my-project/locations/global/hubs/my-hub" --region=us-central1 \
        --interconnect-attachments=https://www.googleapis.com/compute/\
    v1/projects/my-project/regions/us-central1/interconnectAttachments/\
    ic1,https://www.googleapis.com/compute/v1/projects/my-project/\
    regions/us-central1/interconnectAttachments/ic2 \
        --site-to-site-data-transfer
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-interconnect-attachments/create)

---
### `gcloud network-connectivity spokes linked-interconnect-attachments update`

Update a VLAN attachment spoke

Update the details of a VLAN attachment spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-interconnect-attachments update
    (SPOKE : --region=REGION) [--async] [--description=DESCRIPTION]
    [--include-import-ranges=[INCLUDE_IMPORT_RANGES,...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument spoke on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the spoke. |
| `--include-import-ranges` | [INCLUDE_IMPORT_RANGES,...] |  | IP address range(s) allowed to be imported from hub subnets. Only ``ALL_IPV4_RANGES`` can be added to the list. If it's empty, the spoke does not import any subnets from the hub. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a VLAN attachment spoke named my-spoke, run:

    $ gcloud network-connectivity spokes \
        linked-interconnect-attachments update my-spoke \
        --region=us-central1 --description="new spoke description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-interconnect-attachments/update)

---

## `gcloud network-connectivity spokes linked-producer-vpc-network` — manage Producer VPC spokes
### `gcloud network-connectivity spokes linked-producer-vpc-network create`

Create a new Producer VPC spoke

Create a new Producer VPC spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-producer-vpc-network create SPOKE
    --hub=HUB --network=NETWORK --peering=PEERING [--async]
    [--description=DESCRIPTION] [--exclude-export-ranges=[CIDR_RANGE,...]]
    [--global] [--include-export-ranges=[CIDR_RANGE,...]]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --global on the command line.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | Hub that the spoke will attach to. The hub must already exist. |
| `--network` | NETWORK |  | Your VPC network that contains the peering to the Producer VPC, which this spoke connects to the Hub. The peering must already exist and be in the ACTIVE state. |
| `--peering` | PEERING |  | Peering between your network and the Producer VPC, which this spoke connects to the Hub. The peering must already exist and be in the ACTIVATE state. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the spoke to create. |
| `--exclude-export-ranges` | [CIDR_RANGE,...] |  | Subnet IP address range(s) to hide from other VPC networks that are connected through Network Connectivity Center. |
| `--global` |  |  | Indicates that the spoke is global. |
| `--include-export-ranges` | [CIDR_RANGE,...] |  | Subnet IP address range(s) to export to other VPC networks that are connected through Network Connectivity Center. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Producer VPC spoke named myspoke, run:

    $ gcloud network-connectivity spokes linked-producer-vpc-network \
         create myspoke \
         --hub=https://www.googleapis.com/networkconnectivity/v1/\
     projects/my-project/locations/global/hubs/my-hub --global \
         --network=https://www.googleapis.com/compute/v1/projects/\
     my-project/global/networks/my-vpc --peering=my-peering-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-producer-vpc-network/create)

---
### `gcloud network-connectivity spokes linked-producer-vpc-network update`

Update a Producer VPC spoke

Update the details of a Producer VPC spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-producer-vpc-network update SPOKE
    [--async] [--description=DESCRIPTION]
    [--exclude-export-ranges=[CIDR_RANGE,...]] [--global]
    [--include-export-ranges=[CIDR_RANGE,...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --global on the command line.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the spoke. |
| `--exclude-export-ranges` | [CIDR_RANGE,...] |  | New exclude export ranges of the spoke. |
| `--global` |  |  | Indicates that the spoke is global. |
| `--include-export-ranges` | [CIDR_RANGE,...] |  | New include export ranges of the spoke. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a Producer VPC spoke named my-spoke, run:

    $ gcloud network-connectivity spokes linked-producer-vpc-network \
         update myspoke --global --description="new spoke description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-producer-vpc-network/update)

---

## `gcloud network-connectivity spokes linked-router-appliances` — manage Router appliance spokes
### `gcloud network-connectivity spokes linked-router-appliances create`

Create a new Router appliance spoke

Create a new Router appliance spoke
(https://cloud.google.com/network-connectivity/docs/network-connectivity-center/how-to/working-with-hubs-spokes#create-ra-spoke).

**Synopsis:**
```
gcloud network-connectivity spokes linked-router-appliances create
    (SPOKE : --region=REGION) --hub=HUB
    --router-appliance=[instance=INSTANCE],[ip=IP] [--async]
    [--description=DESCRIPTION] [--group=GROUP]
    [--include-import-ranges=[INCLUDE_IMPORT_RANGES,...]]
    [--labels=[KEY=VALUE,...]] [--site-to-site-data-transfer]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to be created. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument spoke on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | Hub that the spoke will attach to. The hub must already exist. |
| `--router-appliance` | [instance=INSTANCE],[ip=IP] |  | Router appliance instance(s) that the spoke provides connectivity to. The resources must already exist. For example, use --router-appliance=instance=ins_uri_1,ip=10.10.0.1 to add a single router appliance instance, or --router-appliance=instance=ins_uri_1,ip=10.10.0.1 --router-appliance=instance=ins_uri_2,ip=10.10.0.2 ... to add multiple instances. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the spoke to create. |
| `--group` | GROUP |  | The group that the spoke will be added to. The group must already exist. If unset, the spoke will be added to the ``default`` group. |
| `--include-import-ranges` | [INCLUDE_IMPORT_RANGES,...] |  | IP address range(s) allowed to be imported from hub subnets. Only ``ALL_IPV4_RANGES`` can be added to the list. If it's empty, the spoke does not import any subnets from the hub. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--site-to-site-data-transfer` |  |  | Whether to enable site-to-site data transfer for this spoke. Data transfer is available only in supported locations (https://cloud.google.com/network-connectivity/docs/network-connectivity-center/concepts/locations). |


**Examples:**
```bash
To create a spoke in region us-central1 that uses data transfer and has two
router appliance instances, run:

    $ gcloud network-connectivity spokes linked-router-appliances \
        create my-spoke \
        --hub="https://www.googleapis.com/networkconnectivity/v1/project\
    s/my-project/locations/global/hubs/my-hub" --region=us-central1 \
        --router-appliance=instance=https://www.googleapis.com/compute/\
    v1/projects/my-project/zones/us-central1-a/instances/vm1,\
    ip=10.10.0.1 \
        --router-appliance=instance=https://www.googleapis.com/compute/\
    v1/projects/my-project/zones/us-central1-a/instances/vm2,\
    ip=10.10.0.2 --site-to-site-data-transfer
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-router-appliances/create)

---
### `gcloud network-connectivity spokes linked-router-appliances update`

Update a Router appliance spoke

Update the details of a Router appliance spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-router-appliances update
    (SPOKE : --region=REGION) [--async] [--description=DESCRIPTION]
    [--include-import-ranges=[INCLUDE_IMPORT_RANGES,...]]
    [--router-appliance=[instance=INSTANCE],[ip=IP]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument spoke on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the spoke. |
| `--include-import-ranges` | [INCLUDE_IMPORT_RANGES,...] |  | IP address range(s) allowed to be imported from hub subnets. Only ``ALL_IPV4_RANGES`` can be added to the list. If it's empty, the spoke does not import any subnets from the hub. |
| `--router-appliance` | [instance=INSTANCE],[ip=IP] |  | Router appliance instance(s) with which to replace the set of instances already linked to this spoke. Pass this flag multiple times to replace with multiple instances. For example, use --router-appliance=instance=new_ins_uri,ip=10.10.0.1 for a single router appliance instance, or --router-appliance=instance=new_ins_uri_1,ip=10.10.0.1 --router-appliance=instance=new_ins_uri_2,ip=10.10.0.2 ... for multiple instances. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a Router appliance spoke named my-spoke, run:

    $ gcloud network-connectivity spokes linked-router-appliances \
        update my-spoke --region=us-central1 \
        --description="new spoke description"

To replace the router appliance instances linked to a spoke with two new
instances, run:

    $ gcloud network-connectivity spokes linked-router-appliances \
        update my-spoke --region=us-central1 \
        --router-appliance=instance=https://www.googleapis.com/compute/\
    v1/projects/my-project/zones/us-central1-a/instances/vm1,\
    ip=10.10.0.1 \
        --router-appliance=instance=https://www.googleapis.com/compute/\
    v1/projects/my-project/zones/us-central1-a/instances/vm2,\
    ip=10.10.0.2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-router-appliances/update)

---

## `gcloud network-connectivity spokes linked-vpc-network` — manage VPC spokes
### `gcloud network-connectivity spokes linked-vpc-network create`

Create a new VPC spoke

Create a new VPC spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-vpc-network create SPOKE
    --hub=HUB --vpc-network=VPC_NETWORK [--async]
    [--description=DESCRIPTION] [--exclude-export-ranges=[CIDR_RANGE,...]]
    [--global] [--include-export-ranges=[CIDR_RANGE,...]]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to create. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --global on the command line.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | Hub that the spoke will attach to. The hub must already exist. |
| `--vpc-network` | VPC_NETWORK |  | VPC network that the spoke provides connectivity to. The resource must already exist. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the spoke to create. |
| `--exclude-export-ranges` | [CIDR_RANGE,...] |  | Subnet IP address range(s) to hide from other VPC networks that are connected through Network Connectivity Center. |
| `--global` |  |  | Indicates that the spoke is global. |
| `--include-export-ranges` | [CIDR_RANGE,...] |  | Subnet IP address range(s) to export to other VPC networks that are connected through Network Connectivity Center. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a VPC spoke named myspoke, run:

    $ gcloud network-connectivity spokes linked-vpc-network create \
         myspoke \
         --hub=https://www.googleapis.com/networkconnectivity/v1/\
     projects/my-project/locations/global/hubs/my-hub --global \
         --vpc-network=https://www.googleapis.com/compute/v1/projects/\
     my-project/global/networks/my-vpc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-vpc-network/create)

---
### `gcloud network-connectivity spokes linked-vpc-network update`

Update a VPC spoke

Update the details of a VPC spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-vpc-network update SPOKE
    [--async] [--description=DESCRIPTION]
    [--exclude-export-ranges=[CIDR_RANGE,...]] [--global]
    [--include-export-ranges=[CIDR_RANGE,...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --global on the command line.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the spoke. |
| `--exclude-export-ranges` | [CIDR_RANGE,...] |  | New exclude export ranges of the spoke. |
| `--global` |  |  | Indicates that the spoke is global. |
| `--include-export-ranges` | [CIDR_RANGE,...] |  | New include export ranges of the spoke. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a global VPC spoke named my-spoke, run:

    $ gcloud network-connectivity spokes linked-vpc-network update \
         myspoke --global --description="new spoke description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-vpc-network/update)

---

## `gcloud network-connectivity spokes linked-vpn-tunnels` — manage VPN spokes
### `gcloud network-connectivity spokes linked-vpn-tunnels create`

Create a new VPN spoke

Create a new VPN spoke
(https://cloud.google.com/network-connectivity/docs/network-connectivity-center/how-to/working-with-hubs-spokes#create-vpn-spoke).

**Synopsis:**
```
gcloud network-connectivity spokes linked-vpn-tunnels create
    (SPOKE : --region=REGION) --hub=HUB --vpn-tunnels=[VPN_TUNNELS,...]
    [--async] [--description=DESCRIPTION] [--group=GROUP]
    [--include-import-ranges=[INCLUDE_IMPORT_RANGES,...]]
    [--labels=[KEY=VALUE,...]] [--site-to-site-data-transfer]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to be created. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument spoke on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | Hub that the spoke will attach to. The hub must already exist. |
| `--vpn-tunnels` | [VPN_TUNNELS,...] |  | HA VPN tunnels that the spoke provides connectivity to. The resources must already exist. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the spoke to create. |
| `--group` | GROUP |  | The group that the spoke will be added to. The group must already exist. If unset, the spoke will be added to the ``default`` group. |
| `--include-import-ranges` | [INCLUDE_IMPORT_RANGES,...] |  | IP address range(s) allowed to be imported from hub subnets. Only ``ALL_IPV4_RANGES`` can be added to the list. If it's empty, the spoke does not import any subnets from the hub. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--site-to-site-data-transfer` |  |  | Whether to enable site-to-site data transfer for this spoke. Data transfer is available only in supported locations (https://cloud.google.com/network-connectivity/docs/network-connectivity-center/concepts/locations). |


**Examples:**
```bash
To create a VPN spoke in region us-central1 that uses data transfer and has
two tunnels, run:

    $ gcloud network-connectivity spokes linked-vpn-tunnels create \
        my-spoke \
        --hub="https://www.googleapis.com/networkconnectivity/v1/project\
    s/my-project/locations/global/hubs/my-hub" --region=us-central1 \
        --vpn-tunnels=https://www.googleapis.com/compute/v1/projects/\
    my-project/regions/us-central1/vpnTunnels/vpn-tunnel1,https://\
    www.googleapis.com/compute/v1/projects/my-project/regions/\
    us-central1/vpnTunnels/vpn-tunnel2 --site-to-site-data-transfer
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-vpn-tunnels/create)

---
### `gcloud network-connectivity spokes linked-vpn-tunnels update`

Update a VPN spoke

Update the details of a VPN spoke.

**Synopsis:**
```
gcloud network-connectivity spokes linked-vpn-tunnels update
    (SPOKE : --region=REGION) [--async] [--description=DESCRIPTION]
    [--include-import-ranges=[INCLUDE_IMPORT_RANGES,...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Spoke resource - Name of the spoke to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument spoke on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPOKE
     ID of the spoke or fully qualified identifier for the spoke.

     To set the spoke attribute:
     + provide the argument spoke on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The location Id.

     To set the region attribute:
     + provide the argument spoke on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the spoke. |
| `--include-import-ranges` | [INCLUDE_IMPORT_RANGES,...] |  | IP address range(s) allowed to be imported from hub subnets. Only ``ALL_IPV4_RANGES`` can be added to the list. If it's empty, the spoke does not import any subnets from the hub. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a VPN spoke named my-spoke, run:

    $ gcloud network-connectivity spokes linked-vpn-tunnels update \
        my-spoke --region=us-central1 \
        --description="new spoke description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/spokes/linked-vpn-tunnels/update)

---
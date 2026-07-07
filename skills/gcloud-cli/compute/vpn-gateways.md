# gcloud compute vpn-gateways

read and manipulate Highly Available VPN Gateways

### `gcloud compute vpn-gateways create`

Create a new Compute Engine Highly Available VPN gateway

gcloud compute vpn-gateways create creates a new Highly Available VPN
gateway.

Highly Available VPN Gateway provides a means to create a VPN solution with
a higher availability SLA compared to Classic Target VPN Gateway. Highly
Available VPN gateways are simply referred to as VPN gateways in the API
documentation and gcloud commands. A VPN Gateway can reference one or more
VPN tunnels that connect it to external VPN gateways or Cloud VPN Gateways.

**Synopsis:**
```
gcloud compute vpn-gateways create NAME --network=NETWORK
    [--description=DESCRIPTION] [--gateway-ip-version=GATEWAY_IP_VERSION]
    [--interconnect-attachments=[INTERCONNECT_ATTACHMENTS,...]]
    [--region=REGION] [--stack-type=STACK_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the VPN Gateway to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | A reference to a network to which the VPN gateway is attached. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the VPN gateway. |
| `--gateway-ip-version` | one of: IPV4 Every HA-VPN gateway interface is configured with an IPv4 address |  | IP version of the HA VPN gateway. You must specify either IPv4 or IPv6. If you do not specify this field, every HA VPN gateway interface will be configured with an IPv4 address. GATEWAY_IP_VERSION must be one of: IPV4 Every HA-VPN gateway interface is configured with an IPv4 address. IPV6 Every HA-VPN gateway interface is configured with an IPv6 address. |
| `--interconnect-attachments` | [INTERCONNECT_ATTACHMENTS,...] |  | Names of interconnect attachments (VLAN attachments) associated with the VPN gateway interfaces. You must specify this field when using a VPN gateway for HA VPN over Cloud Interconnect. Otherwise, this field is optional. For example, --interconnect-attachments attachment-a-zone1,attachment-a-zone2 associates VPN gateway with attachment from zone1 on interface 0 and with attachment from zone2 on interface 1. |
| `--region` | REGION |  | Region of the VPN Gateway to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--stack-type` | one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this VPN gateway |  | The stack type of the protocol(s) enabled on this VPN gateway. If not provided, IPV4_ONLY will be used. STACK_TYPE must be one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this VPN gateway. IPV4_ONLY Only IPv4 protocol is enabled on this VPN gateway. IPV6_ONLY Only IPv6 protocol is enabled on this VPN gateway. |


**Examples:**
```bash
To create a VPN gateway, run:

    $ gcloud compute vpn-gateways create my-vpn-gateway \
      --region=us-central1 --network=default
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-gateways/create)

---
### `gcloud compute vpn-gateways delete`

Delete Compute Engine Highly Available VPN Gateways

gcloud compute vpn-gateways delete is used to delete one or more Compute
Engine Highly Available VPN Gateways. VPN Gateways can only be deleted when
no VPN tunnels refer to them.

Highly Available VPN Gateway provides a means to create a VPN solution with
a higher availability SLA compared to Classic Target VPN Gateway. Highly
Available VPN gateways are simply referred to as VPN gateways in the API
documentation and gcloud commands. A VPN Gateway can reference one or more
VPN tunnels that connect it to external VPN gateways or Cloud VPN Gateways.

**Synopsis:**
```
gcloud compute vpn-gateways delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the VPN Gateways to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the VPN Gateways to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete a VPN gateway, run:

    $ gcloud compute vpn-gateways delete my-gateway --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-gateways/delete)

---
### `gcloud compute vpn-gateways describe`

Describe a Compute Engine Highly Available VPN Gateway

gcloud compute vpn-gateways describe is used to display all data associated
with a Compute Engine Highly Available VPN Gateway in a project.

Highly Available VPN Gateway provides a means to create a VPN solution with
a higher availability SLA compared to Classic Target VPN Gateway. Highly
Available VPN gateways are simply referred to as VPN gateways in the API
documentation and gcloud commands. A VPN Gateway can reference one or more
VPN tunnels that connect it to external VPN gateways or Cloud VPN Gateways.

**Synopsis:**
```
gcloud compute vpn-gateways describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the VPN Gateway to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the VPN Gateway to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe a VPN gateway, run:

    $ gcloud compute vpn-gateways describe my-gateway \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-gateways/describe)

---
### `gcloud compute vpn-gateways get-status`

Get status of a Compute Engine Highly Available VPN Gateway

gcloud compute vpn-gateways get-status is used to display high availability
configuration status for the Cloud VPN gateway, the command will show you
the high availability configuration status for VPN tunnels associated with
each peer gateway to which the Cloud VPN gateway is connected; the peer
gateway could be either a Cloud VPN gateway or an external VPN gateway.

**Synopsis:**
```
gcloud compute vpn-gateways get-status NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the VPN Gateway to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the VPN Gateway to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To get status of a VPN gateway, run:

    $ gcloud compute vpn-gateways get-status my-gateway \
      --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-gateways/get-status)

---
### `gcloud compute vpn-gateways list`

List Google Compute Engine Highly Available VPN Gateways

gcloud compute vpn-gateways list displays all Google Compute Engine Highly
Available VPN Gateways in a project.

By default, Highly Available VPN Gateways from all regions are listed. The
results can be narrowed down using a filter: --filter="region:( REGION ...
)".

**Synopsis:**
```
gcloud compute vpn-gateways list [NAME ...] [--regexp=REGEXP, -r REGEXP]
    [--regions=REGION,[REGION,...]] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--regions` | REGION,[REGION,...] |  | If provided, only resources from the given regions are queried. |


**Examples:**
```bash
To list all Highly Available VPN Gateways in a project in table form, run:

    $ gcloud compute vpn-gateways list

To list the URIs of all Highly Available VPN Gateways in a project, run:

    $ gcloud compute vpn-gateways list --uri

To list all Highly Available VPN Gateways in the us-central1 and
europe-west1 regions, run:

    $ gcloud compute vpn-gateways list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-gateways/list)

---
### `gcloud compute vpn-gateways update`

Update a Compute Engine Highly Available VPN gateway

gcloud compute vpn-gateways update updates labels for a Compute Engine
Highly Available VPN gateway.

For example:

    $ gcloud compute vpn-gateways update example-gateway \
        --region us-central1 \
      --update-labels=k0=value1,k1=value2 --remove-labels=k3

will add/update labels k0 and k1 and remove labels with key k3.

Labels can be used to identify the VPN gateway and to filter them as in

    $ gcloud compute vpn-gateways list --filter='labels.k1:value2'

To list existing labels

    $ gcloud compute vpn-gateways describe example-gateway \
        --format="default(labels)"

**Synopsis:**
```
gcloud compute vpn-gateways update NAME [--region=REGION]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the VPN Gateway to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the VPN Gateway to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels for a VPN gateway, run:

    $ gcloud compute vpn-gateways update my-gateway \
      --region=us-central1 --update-labels=k0=value1,k1=value2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-gateways/update)

---
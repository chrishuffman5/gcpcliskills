# gcloud compute packet-mirrorings

manage Compute Engine packet mirroring resources

### `gcloud compute packet-mirrorings create`

Create a Compute Engine packet mirroring policy

Create a Compute Engine packet mirroring policy.

**Synopsis:**
```
gcloud compute packet-mirrorings create NAME --collector-ilb=COLLECTOR_ILB
    --network=NETWORK [--async] [--description=DESCRIPTION] [--no-enable]
    [--filter-cidr-ranges=[CIDR_RANGE,...]] [--filter-direction=DIRECTION]
    [--filter-protocols=[PROTOCOL,...]]
    [--mirrored-instances=[INSTANCE,...]] [--mirrored-subnets=[SUBNET,...]]
    [--mirrored-tags=[TAG,...]] [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the packet mirroring to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collector-ilb` | COLLECTOR_ILB |  | Forwarding rule configured as collector. This must be a regional forwarding rule (in the same region) with load balancing scheme INTERNAL and isMirroringCollector set to true. You can provide this as the full URL to the forwarding rule, partial URL, or name. For example, the following are valid values: * https://compute.googleapis.com/compute/v1/projects/myproject/ regions/us-central1/forwardingRules/fr-1 * projects/myproject/regions/us-central1/forwardingRules/fr-1 * fr-1 |
| `--network` | NETWORK |  | Network for this packet mirroring. Only the packets in this network will be mirrored. It is mandatory that all mirrored VMs have a network interface controller (NIC) in the given network. All mirrored subnetworks should belong to the given network. You can provide this as the full URL to the network, partial URL, or name. For example, the following are valid values: * https://compute.googleapis.com/compute/v1/projects/myproject/ global/networks/network-1 * projects/myproject/global/networks/network-1 * network-1 |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Optional, textual description for the packet mirroring. |
| `--enable` |  |  | Enable or disable the packet-mirroring. Enabled by default, use --no-enable to disable. |
| `--filter-cidr-ranges` | [CIDR_RANGE,...] |  | One or more IPv4 or IPv6 CIDR ranges that apply as filters on the source (ingress) or destination (egress) IP in the IP header. If no ranges are specified, all IPv4 traffic that matches the specified IPProtocols is mirrored. If neither cidrRanges nor IPProtocols is specified, all IPv4 traffic is mirrored. To mirror all IPv4 and IPv6 traffic, use 0.0.0.0/0,::/0 |
| `--filter-direction` | one of: both, egress, ingress |  | * For ingress, only ingress traffic is mirrored. * For egress, only egress traffic is mirrored. * For both (default), both directions are mirrored. DIRECTION must be one of: both, egress, ingress. |
| `--filter-protocols` | [PROTOCOL,...] |  | List of IP protocols that apply as filters for packet mirroring traffic. If unspecified, the packet mirroring applies to all traffic. PROTOCOL can be one of tcp, udp, icmp, esp, ah, ipip, sctp, or an IANA protocol number. |
| `--mirrored-instances` | [INSTANCE,...] |  | List of instances to be mirrored. You can provide this as the full or valid partial URL to the instance. For example, the following are valid values: * https://compute.googleapis.com/compute/v1/projects/myproject/ zones/us-central1-a/instances/instance- * projects/myproject/zones/us-central1-a/instances/instance-1 |
| `--mirrored-subnets` | [SUBNET,...] |  | List of subnets to be mirrored. You can provide this as the full URL to the subnet, partial URL, or name. For example, the following are valid values: * https://compute.googleapis.com/compute/v1/projects/myproject/ regions/us-central1/subnetworks/subnet-1 * projects/myproject/regions/us-central1/subnetworks/subnet-1 * subnet-1 |
| `--mirrored-tags` | [TAG,...] |  | List of virtual machine instance tags to be mirrored. To read more about configuring network tags, read this guide: https://cloud.google.com/vpc/docs/add-remove-network-tags The virtual machines with the provided tags must live in zones contained in the same region as this packet mirroring. |
| `--region` | REGION |  | Region of the packet mirroring to create. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
Mirror all tcp traffic to/from all instances in subnet my-subnet in
us-central1, and send the mirrored traffic to the collector-fr Forwarding
Rule.

    $ gcloud compute packet-mirrorings create my-pm \
        --network my-network --region us-central1 \
        --mirrored-subnets my-subnet --collector-ilb collector-fr \
        --filter-protocols tcp

Mirror all traffic between instances with tag t1 and external server with
IP 11.22.33.44 in us-central1, and send the mirrored traffic to the
collector-fr Forwarding Rule.

    $ gcloud compute packet-mirrorings create my-pm \
        --network my-network --region us-central1 --mirrored-tags t1 \
        --collector-ilb collector-fr --filter-cidr-ranges 11.22.33.44/32
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/packet-mirrorings/create)

---
### `gcloud compute packet-mirrorings delete`

Delete a Compute Engine packet mirroring policy

Delete a Compute Engine Packet Mirroring policy.

**Synopsis:**
```
gcloud compute packet-mirrorings delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the packet mirrorings to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the packet mirrorings to delete. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
Delete the Packet Mirroring policy pm-1 in region us-central1.

    $ gcloud compute packet-mirrorings delete pm-1 --region us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/packet-mirrorings/delete)

---
### `gcloud compute packet-mirrorings describe`

Describe a Compute Engine packet mirroring policy

Describe a Compute Engine Packet Mirroring policy.

**Synopsis:**
```
gcloud compute packet-mirrorings describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the packet mirroring to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the packet mirroring to describe. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
Describe the Packet Mirroring policy pm-1 in region us-central1.

    $ gcloud compute packet-mirrorings describe pm-1 --region us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/packet-mirrorings/describe)

---
### `gcloud compute packet-mirrorings list`

List Google Compute Engine packet mirroring policies

gcloud compute packet-mirrorings list displays all Google Compute Engine
packet mirroring policies in a project.

By default, packet mirroring policies from all regions are listed. The
results can be narrowed down using a filter: --filter="region:( REGION ...
)".

**Synopsis:**
```
gcloud compute packet-mirrorings list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--regions=REGION,[REGION,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
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
To list all packet mirroring policies in a project in table form, run:

    $ gcloud compute packet-mirrorings list

To list the URIs of all packet mirroring policies in a project, run:

    $ gcloud compute packet-mirrorings list --uri

To list all packet mirroring policies in the us-central1 and europe-west1
regions, run:

    $ gcloud compute packet-mirrorings list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/packet-mirrorings/list)

---
### `gcloud compute packet-mirrorings update`

Update a Compute Engine packet mirroring policy

Update a Compute Engine packet mirroring policy.

**Synopsis:**
```
gcloud compute packet-mirrorings update NAME [--async]
    [--collector-ilb=COLLECTOR_ILB] [--description=DESCRIPTION] [--enable]
    [--filter-direction=DIRECTION] [--region=REGION]
    [--add-filter-cidr-ranges=[CIDR_RANGE,...] | --clear-filter-cidr-ranges
      | --remove-filter-cidr-ranges=[CIDR_RANGE,...]
      | --set-filter-cidr-ranges=[CIDR_RANGE,...]]
    [--add-filter-protocols=[PROTOCOL,...] | --clear-filter-protocols
      | --remove-filter-protocols=[PROTOCOL,...]
      | --set-filter-protocols=[PROTOCOL,...]]
    [--add-mirrored-instances=[INSTANCE,...] | --clear-mirrored-instances
      | --remove-mirrored-instances=[INSTANCE,...]
      | --set-mirrored-instances=[INSTANCE,...]]
    [--add-mirrored-subnets=[SUBNET,...] | --clear-mirrored-subnets
      | --remove-mirrored-subnets=[SUBNET,...]
      | --set-mirrored-subnets=[SUBNET,...]]
    [--add-mirrored-tags=[TAG,...] | --clear-mirrored-tags
      | --remove-mirrored-tags=[TAG,...] | --set-mirrored-tags=[TAG,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the packet mirroring to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--collector-ilb` | COLLECTOR_ILB |  | Forwarding rule configured as collector. This must be a regional forwarding rule (in the same region) with load balancing scheme INTERNAL and isMirroringCollector set to true. You can provide this as the full URL to the forwarding rule, partial URL, or name. For example, the following are valid values: * https://compute.googleapis.com/compute/v1/projects/myproject/ regions/us-central1/forwardingRules/fr-1 * projects/myproject/regions/us-central1/forwardingRules/fr-1 * fr-1 |
| `--description` | DESCRIPTION |  | Optional, textual description for the packet mirroring. |
| `--enable` |  |  | Enable or disable the packet-mirroring. |
| `--filter-direction` | one of: both, egress, ingress |  | * For ingress, only ingress traffic is mirrored. * For egress, only egress traffic is mirrored. * For both (default), both directions are mirrored. DIRECTION must be one of: both, egress, ingress. |
| `--region` | REGION |  | Region of the packet mirroring to update. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
Stop mirroring by tags, add subnet-1 as a mirrored subnet.

    $ gcloud compute packet-mirrorings update my-pm \
        --region us-central1 --clear-mirrored-tags \
        --add-mirrored-subnets subnet-1

Change the load-balancer to send mirrored traffic to.

    $ gcloud compute packet-mirrorings update my-pm \
        --region us-central1 --collector-ilb new-forwarding-rule

Disable a Packet Mirroring policy.

    $ gcloud compute packet-mirrorings update my-pm \
        --region us-central1 --no-enable

Re-enable a disabled Packet Mirroring policy.

    $ gcloud compute packet-mirrorings update my-pm \
        --region us-central1 --enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/packet-mirrorings/update)

---
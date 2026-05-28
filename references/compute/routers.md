# gcloud compute routers

list, create, and delete Compute Engine routers

### `gcloud compute routers add-bgp-peer`

Add a BGP peer to a Compute Engine router

Add a BGP peer to a Compute Engine router.

**Synopsis:**
```
gcloud compute routers add-bgp-peer NAME --interface=INTERFACE
    --peer-asn=PEER_ASN --peer-name=PEER_NAME
    [--advertised-route-priority=ADVERTISED_ROUTE_PRIORITY]
    [--advertisement-mode=MODE] [--async]
    [--custom-learned-route-priority=PRIORITY] [--[no-]enable-ipv4]
    [--[no-]enable-ipv6] [--[no-]enabled]
    [--export-policies=[EXPORT_POLICY,...]]
    [--import-policies=[IMPORT_POLICY,...]] [--instance=INSTANCE]
    [--instance-zone=INSTANCE_ZONE]
    [--ipv4-nexthop-address=IPV4_NEXTHOP_ADDRESS]
    [--ipv6-nexthop-address=IPV6_NEXTHOP_ADDRESS]
    [--md5-authentication-key=MD5_AUTHENTICATION_KEY]
    [--peer-ip-address=PEER_IP_ADDRESS]
    [--peer-ipv4-nexthop-address=PEER_IPV4_NEXTHOP_ADDRESS]
    [--peer-ipv6-nexthop-address=PEER_IPV6_NEXTHOP_ADDRESS]
    [--region=REGION] [--set-advertisement-groups=[GROUP,...]]
    [--set-advertisement-ranges=[CIDR_RANGE=DESC,...]]
    [--set-custom-learned-route-ranges=[CIDR_RANGE,...]]
    [--bfd-min-receive-interval=BFD_MIN_RECEIVE_INTERVAL
      --bfd-min-transmit-interval=BFD_MIN_TRANSMIT_INTERVAL
      --bfd-multiplier=BFD_MULTIPLIER
      --bfd-session-initialization-mode=BFD_SESSION_INITIALIZATION_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface` | INTERFACE |  | The name of the interface for this BGP peer. |
| `--peer-asn` | PEER_ASN |  | The BGP autonomous system number (ASN) for this BGP peer. Must be a 16-bit or 32-bit private ASN as defined in https://tools.ietf.org/html/rfc6996, for example --asn=64512. |
| `--peer-name` | PEER_NAME |  | The name of the new BGP peer being added. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--advertised-route-priority` | ADVERTISED_ROUTE_PRIORITY |  | The priority of routes advertised to this BGP peer. In the case where there is more than one matching route of maximum length, the routes with lowest priority value win. 0 <= priority <= 65535. If not specified, will use Google-managed priorities. |
| `--advertisement-mode` | one of: CUSTOM Custom (user-configured) BGP advertisements |  | The new advertisement mode for this peer. MODE must be one of: CUSTOM Custom (user-configured) BGP advertisements. DEFAULT Default (Google-managed) BGP advertisements. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--custom-learned-route-priority` | PRIORITY |  | An integral value 0 <= priority <= 65535, to be applied to all custom learned route IP address ranges for this peer. If not specified, a Google-managed priority value of 100 is used. The routes with the lowest priority value win. |
| `--[no-]enable-ipv4` |  |  | If IPv4 is enabled, the peer connection can be established with IPv4 route exchange. If disabled, no IPv4 route exchange is allowed on any active session. By default enabled for IPv4-based BGP sessions. Use --enable-ipv4 to enable and --no-enable-ipv4 to disable. |
| `--[no-]enable-ipv6` |  |  | If IPv6 is enabled, the peer connection can be established with IPv6 route exchange. If disabled, no IPv6 route exchange is allowed on any active session. Disabled by default. Use --enable-ipv6 to enable and --no-enable-ipv6 to disable. |
| `--[no-]enabled` |  |  | If enabled, the peer connection can be established with routing information. If disabled, any active session with the peer is terminated and all associated routing information is removed. Enabled by default. Use --enabled to enable and --no-enabled to disable. |
| `--export-policies` | [EXPORT_POLICY,...] |  | Comma-separated list of export policies. Passing an empty string removes all export policies. |
| `--import-policies` | [IMPORT_POLICY,...] |  | Comma-separated list of import policies. Passing an empty string removes all import policies. |
| `--instance` | INSTANCE |  | Router appliance instance of the BGP peer being added. |
| `--instance-zone` | INSTANCE_ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--ipv4-nexthop-address` | IPV4_NEXTHOP_ADDRESS |  | If IPv4 route exchange is enabled for IPv6-based BGP, the IPv4 next hop address of the Cloud Router interface for this BGP peer. Ignored otherwise. Must be a Google owned link-local IPv4 address in the range 169.254.0.0/16 and must belong to the same subnet as the interface address of the peer router. |
| `--ipv6-nexthop-address` | IPV6_NEXTHOP_ADDRESS |  | If IPv6 route exchange is enabled for IPv4-based BGP, the IPv6 next hop address of the Cloud Router interface for this BGP peer. Ignored otherwise. Must be a Google owned global unicast IPv6 address belonging to the range 2600:2d00:0:2:0:0:0:0/64 or 2600:2d00:0:3:0:0:0:0/64 and must belong to same subnet as the interface address of the peer router. |
| `--md5-authentication-key` | MD5_AUTHENTICATION_KEY |  | The MD5 authentication key for this BGP peer. Maximum length is 80 characters. Can contain only printable ASCII characters. |
| `--peer-ip-address` | PEER_IP_ADDRESS |  | The address of the peer router. Must be a link-local IPv4 address in the range 169.254.0.0/16 or an ULA IPv6 address in the range fdff:1::/64. |
| `--peer-ipv4-nexthop-address` | PEER_IPV4_NEXTHOP_ADDRESS |  | If IPv4 route exchange is enabled for IPv6-based BGP, the IPv4 next hop address of the peer router. Ignored otherwise. Must be a Google owned link-local IPv4 address in the range 169.254.0.0/16. |
| `--peer-ipv6-nexthop-address` | PEER_IPV6_NEXTHOP_ADDRESS |  | If IPv6 route exchange is enabled for IPv4-based BGP, the IPv6 next hop address of the peer router. Ignored otherwise. Must be a Google owned global unicast IPv6 address belonging to the range 2600:2d00:0:2:0:0:0:0/64 or 2600:2d00:0:3:0:0:0:0/64. |
| `--region` | REGION |  | Region of the router to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--set-advertisement-groups` | [GROUP,...] |  | The list of pre-defined groups of IP ranges to dynamically advertise on this peer. This list can only be specified in custom advertisement mode. GROUP must be (only one value is supported): ALL_SUBNETS Automatically advertise all available subnets. This excludes any routes learned for subnets that use VPC Network Peering. |
| `--set-advertisement-ranges` | [CIDR_RANGE=DESC,...] |  | The list of individual IP ranges, in CIDR format, to dynamically advertise on this peer. Each IP range can (optionally) be given a text description DESC. For example, to advertise a specific range, use --set-advertisement-ranges=192.168.10.0/24. To store a description with the range, use --set-advertisement-ranges=192.168.10.0/24=my-networks. This list can only be specified in custom advertisement mode. |
| `--set-custom-learned-route-ranges` | [CIDR_RANGE,...] |  | The list of user-defined custom learned route IP address ranges for this peer. This list is a comma separated IP address ranges such as 1.2.3.4,6.7.0.0/16,2001:db8:abcd:12::/64 where each IP address range must be a valid CIDR-formatted prefix. If an IP address is provided without a subnet mask, it is interpreted as a /32 singular IP address range for IPv4, and /128 for IPv6. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/add-bgp-peer)

---
### `gcloud compute routers add-interface`

Add an interface to a Compute Engine router

gcloud compute routers add-interface is used to add an interface to a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers add-interface NAME --interface-name=INTERFACE_NAME
    (--interconnect-attachment=INTERCONNECT_ATTACHMENT
      --interconnect-attachment-region=INTERCONNECT_ATTACHMENT_REGION
      | --subnetwork=SUBNETWORK --subnetwork-region=SUBNETWORK_REGION
      | --vpn-tunnel=VPN_TUNNEL --vpn-tunnel-region=VPN_TUNNEL_REGION)
    [--ip-address=IP_ADDRESS] [--ip-version=IP_VERSION]
    [--mask-length=MASK_LENGTH] [--redundant-interface=REDUNDANT_INTERFACE]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface-name` | INTERFACE_NAME |  | The name of the interface being added. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ip-address` | IP_ADDRESS |  | The link local (IPv4) or ULA (IPv6) address of the router for this interface. |
| `--ip-version` | one of: IPV4 Interface with IPv4-based BGP |  | IP version of the interface. Possible values are IPV4 and IPV6. Defaults to IPV4. IP_VERSION must be one of: IPV4 Interface with IPv4-based BGP. IPV6 Interface with IPv6-based BGP. |
| `--mask-length` | MASK_LENGTH |  | The subnet mask for the IP range of the interface. The interface IP address and BGP peer IP address must be selected from the subnet defined by this range. |
| `--redundant-interface` | REDUNDANT_INTERFACE |  | The interface that is redundant to the current interface. |
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/add-interface)

---
### `gcloud compute routers add-route-policy`

Add an empty route policy to a Compute Engine router

gcloud compute routers add-route-policy adds an empty route policy to a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers add-route-policy NAME --policy-name=POLICY_NAME
    --policy-type=POLICY_TYPE [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-name` | POLICY_NAME |  | Name of the route policy to add. |
| `--policy-type` | one of: EXPORT The route policy is an export policy |  | Type of the route policy to add. POLICY_TYPE must be one of: EXPORT The route policy is an export policy. IMPORT The route policy is an import policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To add an import route policy my-policy to a router my-router in region
us-central1, run:

    $ gcloud compute routers add-route-policy my-router \
      --region=us-central1 --policy-name=my-policy \
      --policy-type=IMPORT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/add-route-policy)

---
### `gcloud compute routers add-route-policy-term`

Adds a new term to an existing route policy of a Comute Engine router

gcloud compute routers add-route-policy-term adds a term to a route policy.

**Synopsis:**
```
gcloud compute routers add-route-policy-term NAME --actions=[ACTION;...]
    --match=MATCH --policy-name=POLICY_NAME --priority=PRIORITY
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--actions` | [ACTION;...] |  | Semicolon separated CEL expressions for the actions to take when the rule matches. |
| `--match` | MATCH |  | CEL expression for matching a route. |
| `--policy-name` | POLICY_NAME |  | Name of the route policy to which to add the term. |
| `--priority` | PRIORITY |  | Order of the term within the policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To add a term with priority 0 with match destination == '192.168.0.0/16'
and actions drop() to a route policy my-policy of a router my-router in
region us-central1, run:

    $ gcloud compute routers add-route-policy-term my-router \
      --region=us-central1 --policy-name=my-policy --priority=0 \
      --match="destination == '192.168.0.0/16'" --actions="drop()"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/add-route-policy-term)

---
### `gcloud compute routers create`

Create a Compute Engine router

gcloud compute routers create is used to create a router to provide dynamic
routing to VPN tunnels and interconnects.

**Synopsis:**
```
gcloud compute routers create NAME --network=NETWORK
    [--advertisement-mode=MODE] [--asn=ASN] [--async]
    [--bgp-identifier-range=BGP_IDENTIFIER_RANGE]
    [--description=DESCRIPTION] [--encrypted-interconnect-router]
    [--keepalive-interval=KEEPALIVE_INTERVAL] [--region=REGION]
    [--resource-manager-tags=[KEY=VALUE,...]]
    [--set-advertisement-groups=[GROUP,...]]
    [--set-advertisement-ranges=[CIDR_RANGE=DESC,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network for this router |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--advertisement-mode` | one of: CUSTOM Custom (user-configured) BGP advertisements |  | The new advertisement mode for this router. MODE must be one of: CUSTOM Custom (user-configured) BGP advertisements. DEFAULT Default (Google-managed) BGP advertisements. |
| `--asn` | ASN |  | The optional BGP autonomous system number (ASN) for this router. Must be a 16-bit or 32-bit private ASN as defined in https://tools.ietf.org/html/rfc6996, for example --asn=64512. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bgp-identifier-range` | BGP_IDENTIFIER_RANGE |  | The range of valid BGP Identifiers for this Router. Must be a link-local IPv4 range from 169.254.0.0/16, of size at least /30, even if the BGP sessions are over IPv6. It must not overlap with any IPv4 BGP session ranges. This is commonly called "router ID" by other vendors. |
| `--description` | DESCRIPTION |  | An optional description of this router. |
| `--encrypted-interconnect-router` |  |  | Indicates if a router is dedicated for use with encrypted interconnect attachments (VLAN attachments). |
| `--keepalive-interval` | KEEPALIVE_INTERVAL |  | The interval between BGP keepalive messages that are sent to the peer. If set, this value must be between 20 and 60 seconds. The default is 20 seconds. See $ gcloud topic datetimes for information on duration formats. BGP systems exchange keepalive messages to determine whether a link or host has failed or is no longer available. Hold time is the length of time in seconds that the BGP session is considered operational without any activity. After the hold time expires, the session is dropped. Hold time is three times the interval at which keepalive messages are sent, and the hold time is the maximum number of seconds allowed to elapse between successive keepalive messages that BGP receives from a peer. BGP will use the smaller of either the local hold time value or the peer's hold time value as the hold time for the BGP connection between the two peers. |
| `--region` | REGION |  | Region of the router to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | Comma-separated list of Resource Manager tags to attach to the router. Key-value pairs must be provided in the form tagKeys/{TagKey_Numeric_ID}=tagValues/{TagValue_Numeric_ID}. See Listing tag keys (https://cloud.google.com/resource-manager/docs/tags/tags-creating-and-managing#listing_keys). |
| `--set-advertisement-groups` | [GROUP,...] |  | The list of pre-defined groups of IP ranges to dynamically advertise on this router. This list can only be specified in custom advertisement mode. GROUP must be (only one value is supported): ALL_SUBNETS Automatically advertise all available subnets. This excludes any routes learned for subnets that use VPC Network Peering. |
| `--set-advertisement-ranges` | [CIDR_RANGE=DESC,...] |  | The list of individual IP ranges, in CIDR format, to dynamically advertise on this router. Each IP range can (optionally) be given a text description DESC. For example, to advertise a specific range, use --set-advertisement-ranges=192.168.10.0/24. To store a description with the range, use --set-advertisement-ranges=192.168.10.0/24=my-networks. This list can only be specified in custom advertisement mode. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/create)

---
### `gcloud compute routers delete`

Delete Compute Engine routers

gcloud compute routers delete deletes one or more Compute Engine routers.
Routers can only be deleted when no other resources (e.g., virtual machine
instances) refer to them.

**Synopsis:**
```
gcloud compute routers delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the routers to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the routers to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/delete)

---
### `gcloud compute routers describe`

Describe a Compute Engine router

gcloud compute routers describe displays all data associated with a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/describe)

---
### `gcloud compute routers download-route-policy`

Download a route policy from a Compute Engine router

gcloud compute routers download-route-policy downloads a route policy from
a Compute Engine router.

**Synopsis:**
```
gcloud compute routers download-route-policy NAME --file-name=FILE_NAME
    --policy-name=POLICY_NAME [--file-format=FILE_FORMAT] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to export.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-name` | FILE_NAME |  | The name of the file to download the route policy config to. |
| `--policy-name` | POLICY_NAME |  | Name of the route policy to download. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-format` | one of: json, yaml |  | Format of the file passed to --file-name. FILE_FORMAT must be one of: json, yaml. |
| `--region` | REGION |  | Region of the router to export. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To download a route policy my-export-policy to a file my-export-policy.yaml
from a router my-router in region us-central1, run:

    $ gcloud compute routers download-route-policy my-router \
        --region=us-central1 --policy-name=my-export-policy \
        --file-name=my-export-policy.yaml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/download-route-policy)

---
### `gcloud compute routers get-nat-ip-info`

Display NAT IP information in a router

    $ gcloud compute routers get-nat-ip-info

shows a mapping of IP:[usage, mode] allocated to each NAT via the specified
router.

**Synopsis:**
```
gcloud compute routers get-nat-ip-info NAME [--nat-name=NAT_NAME]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to get NAT IP info.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat-name` | NAT_NAME |  | The NAT name to filter out NAT IP information |
| `--region` | REGION |  | Region of the router to get NAT IP info. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To show NAT IP information from all NATs in router 'r1' in region
'us-central1', run:

    $ gcloud compute routers get-nat-ip-info r1 --region=us-central1

To show NAT IP information for a specific NAT 'nat1' in router 'r1' in
region 'us-central1', run:

    $ gcloud compute routers get-nat-ip-info r1 --region=us-central1 \
      --nat-name="nat1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/get-nat-ip-info)

---
### `gcloud compute routers get-nat-mapping-info`

Display NAT Mapping information in a router

    $ gcloud compute routers get-nat-mapping-info

shows a mapping of IP:port-ranges allocated to each VM's interface that is
configured to use NAT via the specified router.

**Synopsis:**
```
gcloud compute routers get-nat-mapping-info NAME [--nat-name=NAT_NAME]
    [--region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to get NAT mapping info.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat-name` | NAT_NAME |  | The NAT name to filter out NAT mapping information |
| `--region` | REGION |  | Region of the router to get NAT mapping info. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To show NAT mappings from all NATs in router 'r1' in region 'us-central1',
run:

    $ gcloud compute routers get-nat-mapping-info r1 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/get-nat-mapping-info)

---
### `gcloud compute routers get-route-policy`

Get a route policy from a Compute Engine router

gcloud compute routers get-route-policy gets a route policy from a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers get-route-policy NAME --policy-name=POLICY_NAME
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to get.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-name` | POLICY_NAME |  | Name of the route policy to get. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to get. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To get a route policy my-policy from a router my-router in region
us-central1, run:

    $ gcloud compute routers get-route-policy my-router \
        --region=us-central1 --policy-name=my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/get-route-policy)

---
### `gcloud compute routers get-status`

Get status of a Compute Engine router

gcloud compute routers get-status displays all runtime data associated with
a Compute Engine router.

**Synopsis:**
```
gcloud compute routers get-status NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/get-status)

---
### `gcloud compute routers list`

List Google Compute Engine routers

gcloud compute routers list displays all Google Compute Engine routers in a
project.

By default, routers from all regions are listed. The results can be
narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute routers list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all routers in a project in table form, run:

    $ gcloud compute routers list

To list the URIs of all routers in a project, run:

    $ gcloud compute routers list --uri

To list all routers in the us-central1 and europe-west1 regions, run:

    $ gcloud compute routers list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/list)

---
### `gcloud compute routers list-bgp-routes`

List routes advertised and learned on individual BGP sessions, both pre- and post-policy evaluation

gcloud compute routers list-bgp-routes lists routes advertised and learned
on individual BGP sessions, both pre- and post-policy evaluation.

**Synopsis:**
```
gcloud compute routers list-bgp-routes NAME --address-family=ADDRESS_FAMILY
    --peer=PEER --route-direction=ROUTE_DIRECTION
    [--destination-range=CIDR_RANGE] [--no-policy-applied]
    [--region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to list.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--address-family` | one of: IPV4 Interface with IPv4-based BGP |  | Limit results to routes learned for this Address Family Identifier. ADDRESS_FAMILY must be one of: IPV4 Interface with IPv4-based BGP. IPV6 Interface with IPv6-based BGP. |
| `--peer` | PEER |  | Limit results to routes learned from this peer (name). |
| `--route-direction` | one of: INBOUND Learned routes |  | Limit results to routes in this direction. ROUTE_DIRECTION must be one of: INBOUND Learned routes. OUTBOUND Advertised routes. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-range` | CIDR_RANGE |  | Limit results to prefixes. |
| `--policy-applied` |  |  | Routes returned are post-policy evaluation. Enabled by default, use --no-policy-applied to disable. |
| `--region` | REGION |  | Region of the router to list. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To list inbound BGP routes limited to IPv4 addess family from a router
my-router BGP peer my-bgp-peer in region us-central1, run:

    $ gcloud compute routers list-bgp-routes my-router \
      --region=us-central1 --address-family=IPV4 --peer=my-bgp-peer \
      --route-direction=INBOUND"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/list-bgp-routes)

---
### `gcloud compute routers list-route-policies`

List route policies from a Compute Engine router

gcloud compute routers list-route-policies lists all route policies from a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers list-route-policies NAME [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to list. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To list route policies from a router my-router in region us-central1, run:

    $ gcloud compute routers list-route-policies my-router \
    --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/list-route-policies)

---
### `gcloud compute routers remove-bgp-peer`

Remove a BGP peer from a Compute Engine router

gcloud compute routers remove-bgp-peer removes a BGP peer from a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers remove-bgp-peer NAME
    (--peer-name=PEER_NAME | --peer-names=[PEER_NAME,...])
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-name` | PEER_NAME |  | _[Exactly one of these must be specified:]_ The name of the peer being removed. |
| `--peer-names` | [PEER_NAME,...] |  | _[Exactly one of these must be specified:]_ The list of names for peers being removed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/remove-bgp-peer)

---
### `gcloud compute routers remove-interface`

Remove an interface from a Compute Engine router

gcloud compute routers remove-interface removes an interface from a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers remove-interface NAME
    (--interface-name=INTERFACE_NAME
      | --interface-names=[INTERFACE_NAME,...]) [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface-name` | INTERFACE_NAME |  | _[Exactly one of these must be specified:]_ The name of the interface being removed. |
| `--interface-names` | [INTERFACE_NAME,...] |  | _[Exactly one of these must be specified:]_ The list of names for interfaces being removed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/remove-interface)

---
### `gcloud compute routers remove-route-policy`

Remove a route policy from a Compute Engine router

gcloud compute routers remove-route-policy removes a route policy from a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers remove-route-policy NAME --policy-name=POLICY_NAME
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-name` | POLICY_NAME |  | Name of the route policy to be removed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To remove a route policy my-policy from a router my-router in region
us-central1, run:

    $ gcloud compute routers remove-route-policy my-router \
    --region=us-central1 --policy-name=my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/remove-route-policy)

---
### `gcloud compute routers remove-route-policy-term`

Remove a route policy term of a Compute Engine router

gcloud compute routers remove-route-policy-term removes a term of a route
policy.

**Synopsis:**
```
gcloud compute routers remove-route-policy-term NAME
    --policy-name=POLICY_NAME --priority=PRIORITY [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to remove a route policy term from.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy-name` | POLICY_NAME |  | Name of the route policy from which the term should be removed. |
| `--priority` | PRIORITY |  | Order of the term within the policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to remove a route policy term from. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To remove a route policy term with priority 0 from a route policy my-policy
from a router my-router in region us-central1, run:

    $ gcloud compute routers remove-route-policy-term my-router \
     --region=us-central1 --policy-name=my-policy --priority=0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/remove-route-policy-term)

---
### `gcloud compute routers update`

Update a Compute Engine router

gcloud compute routers update is used to update a Compute Engine router.

**Synopsis:**
```
gcloud compute routers update NAME [--advertisement-mode=MODE] [--asn=ASN]
    [--async] [--bgp-identifier-range=BGP_IDENTIFIER_RANGE]
    [--keepalive-interval=KEEPALIVE_INTERVAL] [--region=REGION]
    [--set-advertisement-groups=[GROUP,...]]
    [--set-advertisement-ranges=[CIDR_RANGE=DESC,...]]
    [--add-advertisement-groups=[GROUP,...]
      | --add-advertisement-ranges=[CIDR_RANGE=DESC,...]
      | --remove-advertisement-groups=[GROUP,...]
      | --remove-advertisement-ranges=[CIDR_RANGE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--advertisement-mode` | one of: CUSTOM Custom (user-configured) BGP advertisements |  | The new advertisement mode for this router. MODE must be one of: CUSTOM Custom (user-configured) BGP advertisements. DEFAULT Default (Google-managed) BGP advertisements. |
| `--asn` | ASN |  | The optional BGP autonomous system number (ASN) for this router. Must be a 16-bit or 32-bit private ASN as defined in https://tools.ietf.org/html/rfc6996, for example --asn=64512. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--bgp-identifier-range` | BGP_IDENTIFIER_RANGE |  | The range of valid BGP Identifiers for this Router. Must be a link-local IPv4 range from 169.254.0.0/16, of size at least /30, even if the BGP sessions are over IPv6. It must not overlap with any IPv4 BGP session ranges. This is commonly called "router ID" by other vendors. |
| `--keepalive-interval` | KEEPALIVE_INTERVAL |  | The interval between BGP keepalive messages that are sent to the peer. If set, this value must be between 20 and 60 seconds. The default is 20 seconds. See $ gcloud topic datetimes for information on duration formats. BGP systems exchange keepalive messages to determine whether a link or host has failed or is no longer available. Hold time is the length of time in seconds that the BGP session is considered operational without any activity. After the hold time expires, the session is dropped. Hold time is three times the interval at which keepalive messages are sent, and the hold time is the maximum number of seconds allowed to elapse between successive keepalive messages that BGP receives from a peer. BGP will use the smaller of either the local hold time value or the peer's hold time value as the hold time for the BGP connection between the two peers. |
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--set-advertisement-groups` | [GROUP,...] |  | The list of pre-defined groups of IP ranges to dynamically advertise on this router. This list can only be specified in custom advertisement mode. GROUP must be (only one value is supported): ALL_SUBNETS Automatically advertise all available subnets. This excludes any routes learned for subnets that use VPC Network Peering. |
| `--set-advertisement-ranges` | [CIDR_RANGE=DESC,...] |  | The list of individual IP ranges, in CIDR format, to dynamically advertise on this router. Each IP range can (optionally) be given a text description DESC. For example, to advertise a specific range, use --set-advertisement-ranges=192.168.10.0/24. To store a description with the range, use --set-advertisement-ranges=192.168.10.0/24=my-networks. This list can only be specified in custom advertisement mode. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/update)

---
### `gcloud compute routers update-bgp-peer`

Update a BGP peer on a Compute Engine router

gcloud compute routers update-bgp-peer is used to update a BGP peer on a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers update-bgp-peer NAME --peer-name=PEER_NAME
    [--advertised-route-priority=ADVERTISED_ROUTE_PRIORITY]
    [--advertisement-mode=MODE] [--async] [--clear-md5-authentication-key]
    [--custom-learned-route-priority=PRIORITY] [--[no-]enable-ipv4]
    [--[no-]enable-ipv6] [--[no-]enabled]
    [--export-policies=[EXPORT_POLICY,...]]
    [--import-policies=[IMPORT_POLICY,...]] [--interface=INTERFACE]
    [--ip-address=IP_ADDRESS] [--ipv4-nexthop-address=IPV4_NEXTHOP_ADDRESS]
    [--ipv6-nexthop-address=IPV6_NEXTHOP_ADDRESS]
    [--md5-authentication-key=MD5_AUTHENTICATION_KEY] [--peer-asn=PEER_ASN]
    [--peer-ip-address=PEER_IP_ADDRESS]
    [--peer-ipv4-nexthop-address=PEER_IPV4_NEXTHOP_ADDRESS]
    [--peer-ipv6-nexthop-address=PEER_IPV6_NEXTHOP_ADDRESS]
    [--region=REGION] [--set-advertisement-groups=[GROUP,...]]
    [--set-advertisement-ranges=[CIDR_RANGE=DESC,...]]
    [--set-custom-learned-route-ranges=[CIDR_RANGE,...]]
    [--add-advertisement-groups=[GROUP,...]
      | --add-advertisement-ranges=[CIDR_RANGE=DESC,...]
      | --remove-advertisement-groups=[GROUP,...]
      | --remove-advertisement-ranges=[CIDR_RANGE,...]]
    [--add-custom-learned-route-ranges=[CIDR_RANGE,...]
      | --remove-custom-learned-route-ranges=[CIDR_RANGE,...]]
    [--bfd-min-receive-interval=BFD_MIN_RECEIVE_INTERVAL
      --bfd-min-transmit-interval=BFD_MIN_TRANSMIT_INTERVAL
      --bfd-multiplier=BFD_MULTIPLIER
      --bfd-session-initialization-mode=BFD_SESSION_INITIALIZATION_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--peer-name` | PEER_NAME |  | The name of the new BGP peer being updated. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--advertised-route-priority` | ADVERTISED_ROUTE_PRIORITY |  | The priority of routes advertised to this BGP peer. In the case where there is more than one matching route of maximum length, the routes with lowest priority value win. 0 <= priority <= 65535. If not specified, will use Google-managed priorities. |
| `--advertisement-mode` | one of: CUSTOM Custom (user-configured) BGP advertisements |  | The new advertisement mode for this peer. MODE must be one of: CUSTOM Custom (user-configured) BGP advertisements. DEFAULT Default (Google-managed) BGP advertisements. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--clear-md5-authentication-key` |  |  | If specified, remove MD5 authentication from the BGP peer. |
| `--custom-learned-route-priority` | PRIORITY |  | An integral value 0 <= priority <= 65535, to be applied to all custom learned route IP address ranges for this peer. If not specified, a Google-managed priority value of 100 is used. The routes with the lowest priority value win. |
| `--[no-]enable-ipv4` |  |  | If IPv4 is enabled, the peer connection can be established with IPv4 route exchange. If disabled, no IPv4 route exchange is allowed on any active session. Use --enable-ipv4 to enable and --no-enable-ipv4 to disable. |
| `--[no-]enable-ipv6` |  |  | If IPv6 is enabled, the peer connection can be established with IPv6 route exchange. If disabled, no IPv6 route exchange is allowed on any active session. Use --enable-ipv6 to enable and --no-enable-ipv6 to disable. |
| `--[no-]enabled` |  |  | If enabled, the peer connection can be established with routing information. If disabled, any active session with the peer is terminated and all associated routing information is removed. Use --enabled to enable and --no-enabled to disable. |
| `--export-policies` | [EXPORT_POLICY,...] |  | Comma-separated list of export policies. Passing an empty string removes all export policies. |
| `--import-policies` | [IMPORT_POLICY,...] |  | Comma-separated list of import policies. Passing an empty string removes all import policies. |
| `--interface` | INTERFACE |  | The name of the interface for this BGP peer. |
| `--ip-address` | IP_ADDRESS |  | The address of the Cloud Router interface for this BGP peer. Must be a link-local IPv4 address in the range 169.254.0.0/16 or an ULA IPv6 address in the range fdff:1::/64. It must also be in the same subnet as the interface address of the peer router. |
| `--ipv4-nexthop-address` | IPV4_NEXTHOP_ADDRESS |  | If IPv4 route exchange is enabled for IPv6-based BGP, the IPv4 next hop address of the Cloud Router interface for this BGP peer. Ignored otherwise. Must be a Google owned link-local IPv4 address in the range 169.254.0.0/16 and must belong to the same subnet as the interface address of the peer router. |
| `--ipv6-nexthop-address` | IPV6_NEXTHOP_ADDRESS |  | If IPv6 route exchange is enabled for IPv4-based BGP, the IPv6 next hop address of the Cloud Router interface for this BGP peer. Ignored otherwise. Must be a Google owned global unicast IPv6 address belonging to the range 2600:2d00:0:2:0:0:0:0/64 or 2600:2d00:0:3:0:0:0:0/64 and must belong to same subnet as the interface address of the peer router. |
| `--md5-authentication-key` | MD5_AUTHENTICATION_KEY |  | The MD5 authentication key for this BGP peer. Maximum length is 80 characters. Can contain only printable ASCII characters. |
| `--peer-asn` | PEER_ASN |  | The BGP autonomous system number (ASN) for this BGP peer. Must be a 16-bit or 32-bit private ASN as defined in https://tools.ietf.org/html/rfc6996, for example --asn=64512. |
| `--peer-ip-address` | PEER_IP_ADDRESS |  | The address of the peer router. Must be a link-local IPv4 address in the range 169.254.0.0/16 or an ULA IPv6 address in the range fdff:1::/64. |
| `--peer-ipv4-nexthop-address` | PEER_IPV4_NEXTHOP_ADDRESS |  | If IPv4 route exchange is enabled for IPv6-based BGP, the IPv4 next hop address of the peer router. Ignored otherwise. Must be a Google owned link-local IPv4 address in the range 169.254.0.0/16. |
| `--peer-ipv6-nexthop-address` | PEER_IPV6_NEXTHOP_ADDRESS |  | If IPv6 route exchange is enabled for IPv4-based BGP, the IPv6 next hop address of the peer router. Ignored otherwise. Must be a Google owned global unicast IPv6 address belonging to the range 2600:2d00:0:2:0:0:0:0/64 or 2600:2d00:0:3:0:0:0:0/64. |
| `--region` | REGION |  | Region of the router to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--set-advertisement-groups` | [GROUP,...] |  | The list of pre-defined groups of IP ranges to dynamically advertise on this peer. This list can only be specified in custom advertisement mode. GROUP must be (only one value is supported): ALL_SUBNETS Automatically advertise all available subnets. This excludes any routes learned for subnets that use VPC Network Peering. |
| `--set-advertisement-ranges` | [CIDR_RANGE=DESC,...] |  | The list of individual IP ranges, in CIDR format, to dynamically advertise on this peer. Each IP range can (optionally) be given a text description DESC. For example, to advertise a specific range, use --set-advertisement-ranges=192.168.10.0/24. To store a description with the range, use --set-advertisement-ranges=192.168.10.0/24=my-networks. This list can only be specified in custom advertisement mode. |
| `--set-custom-learned-route-ranges` | [CIDR_RANGE,...] |  | The list of user-defined custom learned route IP address ranges for this peer. This list is a comma separated IP address ranges such as 1.2.3.4,6.7.0.0/16,2001:db8:abcd:12::/64 where each IP address range must be a valid CIDR-formatted prefix. If an IP address is provided without a subnet mask, it is interpreted as a /32 singular IP address range for IPv4, and /128 for IPv6. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/update-bgp-peer)

---
### `gcloud compute routers update-interface`

Update an interface on a Compute Engine router

gcloud compute routers update-interface is used to update an interface on a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers update-interface NAME
    --interface-name=INTERFACE_NAME [--ip-address=IP_ADDRESS]
    [--ip-version=IP_VERSION] [--mask-length=MASK_LENGTH] [--region=REGION]
    [--interconnect-attachment=INTERCONNECT_ATTACHMENT
      | --interconnect-attachment-region=INTERCONNECT_ATTACHMENT_REGION
      | --vpn-tunnel=VPN_TUNNEL | --vpn-tunnel-region=VPN_TUNNEL_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interface-name` | INTERFACE_NAME |  | The name of the interface being updated. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ip-address` | IP_ADDRESS |  | The link local (IPv4) or ULA (IPv6) address of the router for this interface. |
| `--ip-version` | one of: IPV4 Interface with IPv4-based BGP |  | IP version of the interface. Possible values are IPV4 and IPV6. Defaults to IPV4. IP_VERSION must be one of: IPV4 Interface with IPv4-based BGP. IPV6 Interface with IPv6-based BGP. |
| `--mask-length` | MASK_LENGTH |  | The subnet mask for the IP range of the interface. The interface IP address and BGP peer IP address must be selected from the subnet defined by this range. |
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/update-interface)

---
### `gcloud compute routers update-route-policy-term`

Updates a term of an existing route policy of a Comute Engine router

gcloud compute routers update-route-policy-term updates a term of a route
policy.

**Synopsis:**
```
gcloud compute routers update-route-policy-term NAME --actions=[ACTION;...]
    --match=MATCH --policy-name=POLICY_NAME --priority=PRIORITY
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--actions` | [ACTION;...] |  | Semicolon separated CEL expressions for the actions to take when the rule matches. |
| `--match` | MATCH |  | CEL expression for matching a route. |
| `--policy-name` | POLICY_NAME |  | Name of the route policy to which the term should be updated. |
| `--priority` | PRIORITY |  | Order of the term within the policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the router to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To update a term with priority 128 with match destination ==
'192.168.0.0/24' and actions med.set(12345);asPath.prependSequence([1, 2])
of a route policy example-policy-name of a router example-router in region
router-region, run:

    $ gcloud compute routers update-route-policy-term example-router \
        --region=router-region --policy-name=example-policy-name \
        --priority=128 --match="destination == '192.168.0.0/24'" \
        --actions="med.set(12345);asPath.prependSequence([1, 2])"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/update-route-policy-term)

---
### `gcloud compute routers upload-route-policy`

Upload a route policy into a Compute Engine router

gcloud compute routers upload-route-policy uploads a route policy into a
Compute Engine router.

**Synopsis:**
```
gcloud compute routers upload-route-policy NAME --file-name=FILE_NAME
    [--file-format=FILE_FORMAT] [--policy-name=POLICY_NAME]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the router to upload.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-name` | FILE_NAME |  | Local path to the file defining the policy |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--file-format` | one of: json, yaml |  | Format of the file passed to --file-name. FILE_FORMAT must be one of: json, yaml. |
| `--policy-name` | POLICY_NAME |  | Name of the route policy to add/replace. |
| `--region` | REGION |  | Region of the router to upload. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To upload a route policy my-import-policy from a file my-import-policy.yaml
into a router my-router in region us-central1, run:

    $ gcloud compute routers upload-route-policy my-router \
    --region=us-central1 --policy-name=my-import-policy \
    --file-name=my-import-policy.yaml"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/upload-route-policy)

---

## `gcloud compute routers nats` — list, create, describe, and delete Cloud NAT
### `gcloud compute routers nats create`

Add a NAT to a Compute Engine router

gcloud compute routers nats create is used to create a NAT on a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers nats create NAME --router=ROUTER [--async]
    [--auto-network-tier=AUTO_NETWORK_TIER]
    [--[no-]enable-dynamic-port-allocation]
    [--enable-endpoint-independent-mapping] [--enable-logging]
    [--endpoint-types=[ENDPOINT_TYPE,...]]
    [--icmp-idle-timeout=ICMP_IDLE_TIMEOUT] [--log-filter=LOG_FILTER]
    [--max-ports-per-vm=MAX_PORTS_PER_VM]
    [--min-ports-per-vm=MIN_PORTS_PER_VM] [--region=REGION] [--rules=RULES]
    [--tcp-established-idle-timeout=TCP_ESTABLISHED_IDLE_TIMEOUT]
    [--tcp-time-wait-timeout=TCP_TIME_WAIT_TIMEOUT]
    [--tcp-transitory-idle-timeout=TCP_TRANSITORY_IDLE_TIMEOUT]
    [--type=TYPE] [--udp-idle-timeout=UDP_IDLE_TIMEOUT]
    [--auto-allocate-nat-external-ips
      | --nat-external-ip-pool=IP_ADDRESS,[IP_ADDRESS,...]]
    [--nat-all-subnet-ip-ranges
      | --nat-custom-subnet-ip-ranges=SUBNETWORK[:RANGE_NAME|:ALL],[...]
      | --nat-primary-subnet-ip-ranges]
    [--nat64-all-v6-subnet-ip-ranges
      | --nat64-custom-v6-subnet-ip-ranges=SUBNETWORK,[SUBNETWORK,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the NAT to create
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-network-tier` | one of: PREMIUM High quality, Google-grade network tier with support for all networking products |  | Network tier to use when automatically reserving NAT IP addresses. AUTO_NETWORK_TIER must be one of: PREMIUM High quality, Google-grade network tier with support for all networking products. STANDARD Public internet quality, with only limited support for other networking products. |
| `--[no-]enable-dynamic-port-allocation` |  |  | Enable dynamic port allocation. If not specified, Dynamic Port Allocation is disabled by default. Use --enable-dynamic-port-allocation to enable and --no-enable-dynamic-port-allocation to disable. |
| `--enable-endpoint-independent-mapping` |  |  | Enable endpoint-independent mapping for the NAT (as defined in RFC 5128). If not specified, NATs have endpoint-independent mapping disabled by default. Use --no-enable-endpoint-independent-mapping to disable endpoint-independent mapping. |
| `--enable-logging` |  |  | Enable logging for the NAT. Logs will be exported to Stackdriver. NAT logging is disabled by default. To disable logging for the NAT, use $ gcloud compute routers nats update MY-NAT --no-enable-logging \ --router ROUTER --region REGION |
| `--endpoint-types` | one of: ENDPOINT_TYPE_VM For VM Endpoints ENDPOINT_TYPE_SWG For Secure Web Gateway Endpoints ENDPOINT_TYPE_MANAGED_PROXY_LB For regional Application Load Balancers (internal and external) and regional proxy Network Load Balancers (internal and external) endpoints The default is ENDPOINT_TYPE_VM |  | Endpoint Types supported by the NAT Gateway. ENDPOINT_TYPE must be one of: ENDPOINT_TYPE_VM For VM Endpoints ENDPOINT_TYPE_SWG For Secure Web Gateway Endpoints ENDPOINT_TYPE_MANAGED_PROXY_LB For regional Application Load Balancers (internal and external) and regional proxy Network Load Balancers (internal and external) endpoints The default is ENDPOINT_TYPE_VM. ENDPOINT_TYPE must be one of: ENDPOINT_TYPE_VM, ENDPOINT_TYPE_SWG, ENDPOINT_TYPE_MANAGED_PROXY_LB. |
| `--icmp-idle-timeout` | ICMP_IDLE_TIMEOUT |  | Timeout for ICMP connections. See https://cloud.google.com/sdk/gcloud/reference/topic/datetimes for information on duration formats. |
| `--log-filter` | one of: ALL Export logs for all connections handled by this NAT |  | Filter for logs exported to stackdriver. The default is ALL. If logging is not enabled, filter settings will be persisted but will have no effect. Use --[no-]enable-logging to enable and disable logging. LOG_FILTER must be one of: ALL Export logs for all connections handled by this NAT. ERRORS_ONLY Export logs for connection failures only. TRANSLATIONS_ONLY Export logs for successful connections only. |
| `--max-ports-per-vm` | MAX_PORTS_PER_VM |  | Maximum ports to be allocated to a VM. This field can only be set when Dynamic Port Allocation is enabled and defaults to 65536. It must be set to a power of 2 that is greater than minPortsPerVm and at most 65536. |
| `--min-ports-per-vm` | MIN_PORTS_PER_VM |  | Minimum ports to be allocated to a VM. If Dynamic Port Allocation is disabled, this defaults to 64. If Dynamic Port Allocation is enabled, this defaults to 32 and must be set to a power of 2 that is at least 32 and lower than maxPortsPerVm. |
| `--region` | REGION |  | Region of the NAT to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--rules` | RULES |  | Path to YAML file containing NAT Rules applied to the NAT. The YAML file format must follow the REST API schema for NAT Rules. See API Discovery docs (https://www.googleapis.com/discovery/v1/apis/compute/alpha/rest) for reference. |
| `--tcp-established-idle-timeout` | TCP_ESTABLISHED_IDLE_TIMEOUT |  | Timeout for TCP established connections. See https://cloud.google.com/sdk/gcloud/reference/topic/datetimes for information on duration formats. |
| `--tcp-time-wait-timeout` | TCP_TIME_WAIT_TIMEOUT |  | Timeout for TCP connections in the TIME_WAIT state. See https://cloud.google.com/sdk/gcloud/reference/topic/datetimes for information on duration formats. |
| `--tcp-transitory-idle-timeout` | TCP_TRANSITORY_IDLE_TIMEOUT |  | Timeout for TCP transitory connections. See https://cloud.google.com/sdk/gcloud/reference/topic/datetimes for information on duration formats. |
| `--type` | one of: PRIVATE Used for private-to-private NAT translations |  | Type of the NAT Gateway. Defaults to PUBLIC if not specified. TYPE must be one of: PRIVATE Used for private-to-private NAT translations. Allows communication between VPC Networks. PUBLIC Used for private-to-public NAT translations. Allows VM instances to communicate with the internet. |
| `--udp-idle-timeout` | UDP_IDLE_TIMEOUT |  | Timeout for UDP connections. See https://cloud.google.com/sdk/gcloud/reference/topic/datetimes for information on duration formats. |


**Examples:**
```bash
Auto-allocate NAT for all IP addresses of all subnets in the region:

    $ gcloud compute routers nats create nat1 --router=my-router \
        --auto-allocate-nat-external-ips --nat-all-subnet-ip-ranges

Specify IP addresses for NAT: Each IP address is the name of a reserved
static IP address resource in the same region.

    $ gcloud compute routers nats create nat1 --router=my-router \
        --nat-external-ip-pool=ip-address1,ip-address2

Specify subnet ranges for NAT:

By default, NAT works for all primary and secondary IP ranges for all
subnets in the region for the given VPC network. You can restrict which
subnet primary and secondary ranges can use NAT.

    $ gcloud compute routers nats create nat1 --router=my-router \
        --auto-allocate-nat-external-ips \
        --nat-custom-subnet-ip-ranges=subnet-1,\
    subnet-3:secondary-range-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/create)

---
### `gcloud compute routers nats delete`

Remove a NAT from a Compute Engine router

gcloud compute routers nats delete is used to delete a NAT on a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers nats delete NAME [NAME ...] --router=ROUTER
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Name of the NATs to delete
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the NATs to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete NAT 'n1' in router 'r1', run:

    $ gcloud compute routers nats delete n1 --router=r1 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/delete)

---
### `gcloud compute routers nats describe`

Describe a NAT in a Compute Engine router

gcloud compute routers nats describe is used to describe a NAT in a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers nats describe NAME --router=ROUTER [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the NAT to describe
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the NAT to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe NAT 'n1' in router 'r1', run:

    $ gcloud compute routers nats describe n1 --router=r1 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/describe)

---
### `gcloud compute routers nats list`

Lists the NATs on a Compute Engine router

gcloud compute routers nats list is used to list the NATs on a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers nats list --router=ROUTER [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the NATs to list. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To list all NATs in router r1 in region us-central1, run:

    $ gcloud compute routers nats list --router=r1 --region=us-central1.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/list)

---
### `gcloud compute routers nats update`

Update a NAT on a Compute Engine router

gcloud compute routers nats update is used to update a NAT in a Compute
Engine router.

**Synopsis:**
```
gcloud compute routers nats update NAME --router=ROUTER [--async]
    [--auto-network-tier=AUTO_NETWORK_TIER]
    [--[no-]enable-dynamic-port-allocation]
    [--enable-endpoint-independent-mapping] [--enable-logging]
    [--log-filter=LOG_FILTER] [--region=REGION] [--rules=RULES]
    [--auto-allocate-nat-external-ips
      | --nat-external-ip-pool=IP_ADDRESS,[IP_ADDRESS,...]]
    [--clear-icmp-idle-timeout | --icmp-idle-timeout=ICMP_IDLE_TIMEOUT]
    [--clear-max-ports-per-vm | --max-ports-per-vm=MAX_PORTS_PER_VM]
    [--clear-min-ports-per-vm | --min-ports-per-vm=MIN_PORTS_PER_VM]
    [--clear-nat-external-drain-ip-pool
      | --nat-external-drain-ip-pool=NAT_EXTERNAL_DRAIN_IP_POOL,[...]]
    [--clear-nat-subnet-ip-ranges | --nat-all-subnet-ip-ranges
      | --nat-custom-subnet-ip-ranges=SUBNETWORK[:RANGE_NAME|:ALL],[...]
      | --nat-primary-subnet-ip-ranges]
    [--clear-nat64-subnet-ip-ranges | --nat64-all-v6-subnet-ip-ranges
      | --nat64-custom-v6-subnet-ip-ranges=SUBNETWORK,[SUBNETWORK,...]]
    [--clear-tcp-established-idle-timeout
      | --tcp-established-idle-timeout=TCP_ESTABLISHED_IDLE_TIMEOUT]
    [--clear-tcp-time-wait-timeout
      | --tcp-time-wait-timeout=TCP_TIME_WAIT_TIMEOUT]
    [--clear-tcp-transitory-idle-timeout
      | --tcp-transitory-idle-timeout=TCP_TRANSITORY_IDLE_TIMEOUT]
    [--clear-udp-idle-timeout | --udp-idle-timeout=UDP_IDLE_TIMEOUT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the NAT to create
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-network-tier` | one of: PREMIUM High quality, Google-grade network tier with support for all networking products |  | Network tier to use when automatically reserving NAT IP addresses. AUTO_NETWORK_TIER must be one of: PREMIUM High quality, Google-grade network tier with support for all networking products. STANDARD Public internet quality, with only limited support for other networking products. |
| `--[no-]enable-dynamic-port-allocation` |  |  | Enable dynamic port allocation. If not specified, Dynamic Port Allocation is disabled by default. Use --enable-dynamic-port-allocation to enable and --no-enable-dynamic-port-allocation to disable. |
| `--enable-endpoint-independent-mapping` |  |  | Enable endpoint-independent mapping for the NAT (as defined in RFC 5128). If not specified, NATs have endpoint-independent mapping disabled by default. Use --no-enable-endpoint-independent-mapping to disable endpoint-independent mapping. |
| `--enable-logging` |  |  | Enable logging for the NAT. Logs will be exported to Stackdriver. NAT logging is disabled by default. To disable logging for the NAT, use $ gcloud compute routers nats update MY-NAT --no-enable-logging \ --router ROUTER --region REGION |
| `--log-filter` | one of: ALL Export logs for all connections handled by this NAT |  | Filter for logs exported to stackdriver. The default is ALL. If logging is not enabled, filter settings will be persisted but will have no effect. Use --[no-]enable-logging to enable and disable logging. LOG_FILTER must be one of: ALL Export logs for all connections handled by this NAT. ERRORS_ONLY Export logs for connection failures only. TRANSLATIONS_ONLY Export logs for successful connections only. |
| `--region` | REGION |  | Region of the NAT to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--rules` | RULES |  | Path to YAML file containing NAT Rules applied to the NAT. The YAML file format must follow the REST API schema for NAT Rules. See API Discovery docs (https://www.googleapis.com/discovery/v1/apis/compute/alpha/rest) for reference. |


**Examples:**
```bash
Change subnetworks and IP address resources associated with NAT:

    $ gcloud compute routers nats update nat1 --router=my-router \
        --nat-external-ip-pool=ip-address2,ip-address3 \
        --nat-custom-subnet-ip-ranges=subnet-2,\
    subnet-3:secondary-range-2

Change minimum default ports allocated per VM associated with NAT:

    $ gcloud compute routers nats update nat1 --router=my-router \
        --min-ports-per-vm=128

Change connection timeouts associated with NAT:

    $ gcloud compute routers nats update nat1 --router=my-router \
        --udp-idle-timeout=60s --icmp-idle-timeout=60s \
        --tcp-established-idle-timeout=60s \
        --tcp-transitory-idle-timeout=60s

Reset connection timeouts associated NAT to default values:

    $ gcloud compute routers nats update nat1 --router=my-router \
        --clear-udp-idle-timeout --clear-icmp-idle-timeout \
        --clear-tcp-established-idle-timeout \
        --clear-tcp-transitory-idle-timeout
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/update)

---

## `gcloud compute routers nats rules` — list, create, update, describe, and delete Cloud NAT Rules
### `gcloud compute routers nats rules create`

Add a Rule to a Compute Engine NAT

gcloud compute routers nats rules create is used to create a Rule on a
Compute Engine NAT.

**Synopsis:**
```
gcloud compute routers nats rules create RULE_NUMBER --match=MATCH
    --nat=NAT --router=ROUTER [--async] [--region=REGION]
    [--source-nat-active-ips=IP_ADDRESS,[IP_ADDRESS,...]]
    [--source-nat-active-ranges=SUBNETWORK,[SUBNETWORK,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RULE_NUMBER
   Number that uniquely identifies the Rule to create
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--match` | MATCH |  | CEL Expression used to identify traffic to which this rule applies. * Supported attributes (Public NAT): destination.ip * Supported attributes (Private NAT): nexthop.hub * Supported methods (Public Nat): inIpRange * Supported operators (Public NAT): \|\|, == * Supported operators (Private NAT): == Examples of allowed Match expressions (Public NAT): * 'inIpRange(destination.ip, "203.0.113.0/24")'' * 'destination.ip == "203.0.113.7"' * 'destination.ip == "203.0.113.7" \|\| inIpRange(destination.ip, "203.0.113.16/25")' Example of allowed Match expression (Private NAT): * nexthop.hub == "//networkconnectivity.googleapis.com/projects/p1/locations/global/hubs/h1" |
| `--nat` | NAT |  | Name of the NAT that contains the Rule |
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--region` | REGION |  | Region of the NAT to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--source-nat-active-ips` | IP_ADDRESS,[IP_ADDRESS,...] |  | External IP Addresses to use for connections matching this rule. This flag is supported only for Public NAT and is required when creating a Public NAT gateway. These must be valid reserved external IP addresses in the same region. |
| `--source-nat-active-ranges` | SUBNETWORK,[SUBNETWORK,...] |  | Subnetworks from which addresses are used for connections matching this rule. This flag is supported only for Private NAT and is required when creating a Private NAT gateway. These must be subnetwork resources in the same region, with purpose set to PRIVATE_NAT. |


**Examples:**
```bash
Create a rule to use the IP Address address-1 to talk to destination IPs in
the CIDR Range "203.0.113.0/24".

    $ gcloud compute routers nats rules create 1 --nat=my-nat \
        --router=my-router --region=us-central1 \
        --match='inIpRange(destination.ip, "203.0.113.0/24")' \
        --source-nat-active-ips=a1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/rules/create)

---
### `gcloud compute routers nats rules delete`

Delete a Rule in a Compute Engine NAT

gcloud compute routers nats rules delete is used to delete a Rule on a
Compute Engine NAT.

**Synopsis:**
```
gcloud compute routers nats rules delete RULE_NUMBER [RULE_NUMBER ...]
    --nat=NAT --router=ROUTER [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RULE_NUMBER [RULE_NUMBER ...]
   Number that uniquely identifies the Rules to operate on
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat` | NAT |  | Name of the NAT that contains the Rule |
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the NAT containing the Rules to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete Rule 1 in NAT 'n1' in router 'r1', run:

    $ gcloud compute routers nats rules delete 1 --nat=n1 --router=r1 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/rules/delete)

---
### `gcloud compute routers nats rules describe`

Describe a Rule in a Compute Engine NAT

gcloud compute routers nats rules describe is used to describe a Rule on a
Compute Engine NAT.

**Synopsis:**
```
gcloud compute routers nats rules describe RULE_NUMBER --nat=NAT
    --router=ROUTER [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RULE_NUMBER
   Number that uniquely identifies the Rule to operate on
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat` | NAT |  | Name of the NAT that contains the Rule |
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the NAT containing the Rule to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To describe Rule 1 in NAT 'n1' in router 'r1', run:

    $ gcloud compute routers nats rules describe 1 --nat=n1 \
        --router=r1 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/rules/describe)

---
### `gcloud compute routers nats rules list`

Lists the NATs on a Compute Engine router

gcloud compute routers nats rules list is used to list the Rule on a
Compute Engine NAT.

**Synopsis:**
```
gcloud compute routers nats rules list --nat=NAT --router=ROUTER
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat` | NAT |  | Name of the NAT that contains the Rule |
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the NAT containing the Rules to list. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To list all Rules in Nat n1 in router r1 in region us-central1, run:

    $ gcloud compute routers nats rules list --nat=n1 --router=r1 \
      --region=us-central1.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/rules/list)

---
### `gcloud compute routers nats rules update`

Update a Rule in a Compute Engine NAT

gcloud compute routers nats rules update is used to update a Rule in a
Compute Engine NAT.

**Synopsis:**
```
gcloud compute routers nats rules update RULE_NUMBER --nat=NAT
    --router=ROUTER [--async] [--match=MATCH] [--region=REGION]
    [--source-nat-active-ips=IP_ADDRESS,[IP_ADDRESS,...]]
    [--source-nat-active-ranges=SUBNETWORK,[SUBNETWORK,...]]
    [--clear-source-nat-drain-ips
      | --source-nat-drain-ips=IP_ADDRESS,[IP_ADDRESS,...]]
    [--clear-source-nat-drain-ranges
      | --source-nat-drain-ranges=SUBNETWORK,[SUBNETWORK,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RULE_NUMBER
   Number that uniquely identifies the Rule to update
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nat` | NAT |  | Name of the NAT that contains the Rule |
| `--router` | ROUTER |  | Router to use for NAT. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--match` | MATCH |  | CEL Expression used to identify traffic to which this rule applies. * Supported attributes (Public NAT): destination.ip * Supported attributes (Private NAT): nexthop.hub * Supported methods (Public Nat): inIpRange * Supported operators (Public NAT): \|\|, == * Supported operators (Private NAT): == Examples of allowed Match expressions (Public NAT): * 'inIpRange(destination.ip, "203.0.113.0/24")'' * 'destination.ip == "203.0.113.7"' * 'destination.ip == "203.0.113.7" \|\| inIpRange(destination.ip, "203.0.113.16/25")' Example of allowed Match expression (Private NAT): * nexthop.hub == "//networkconnectivity.googleapis.com/projects/p1/locations/global/hubs/h1" |
| `--region` | REGION |  | Region of the NAT containing the Rule to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--source-nat-active-ips` | IP_ADDRESS,[IP_ADDRESS,...] |  | External IP Addresses to use for connections matching this rule. This flag is supported only for Public NAT and is required when creating a Public NAT gateway. These must be valid reserved external IP addresses in the same region. |
| `--source-nat-active-ranges` | SUBNETWORK,[SUBNETWORK,...] |  | Subnetworks from which addresses are used for connections matching this rule. This flag is supported only for Private NAT and is required when creating a Private NAT gateway. These must be subnetwork resources in the same region, with purpose set to PRIVATE_NAT. |


**Examples:**
```bash
To drain connections established using address-1 and use address-2 for all
new connections matching Rule 1 in NAT nat-1, run:

    $ gcloud compute routers nats rules update 1 --nat=nat1 \
        --router=my-router --region=us-central1 \
        --source-nat-drain-ips=address-1 \
        --source-nat-active-ips=address-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routers/nats/rules/update)

---
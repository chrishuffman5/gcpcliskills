# gcloud compute networks

list, create, and delete Compute Engine networks

### `gcloud compute networks create`

Create a Compute Engine network

gcloud compute networks create is used to create virtual networks. A
network performs the same function that a router does in a home network: it
describes the network range and gateway IP address, handles communication
between instances, and serves as a gateway between instances and callers
outside the network.

**Synopsis:**
```
gcloud compute networks create NAME
    [--bgp-routing-mode=MODE; default="regional"]
    [--description=DESCRIPTION] [--[no-]enable-ula-internal-ipv6]
    [--internal-ipv6-range=INTERNAL_IPV6_RANGE] [--mtu=MTU]
    [--network-firewall-policy-enforcement-order=NETWORK_FIREWALL_POLICY_ENFORCEMENT_ORDER]
    [--network-profile=NETWORK_PROFILE] [--range=RANGE]
    [--resource-manager-tags=[KEY=VALUE,...]] [--subnet-mode=MODE]
    [--bgp-best-path-selection-mode=BGP_BEST_PATH_SELECTION_MODE
      --[no-]bgp-bps-always-compare-med
      --bgp-bps-inter-region-cost=BGP_BPS_INTER_REGION_COST]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bgp-routing-mode` | one of: global Cloud Routers in this network advertise subnetworks from all regions to their BGP peers, and program instances in all regions with the router's best learned BGP routes | regional | The BGP routing mode for this network. If not specified, defaults to regional. MODE must be one of: global Cloud Routers in this network advertise subnetworks from all regions to their BGP peers, and program instances in all regions with the router's best learned BGP routes. regional Cloud Routers in this network advertise subnetworks from their local region only to their BGP peers, and program instances in their local region only with the router's best learned BGP routes. |
| `--description` | DESCRIPTION |  | An optional, textual description for the network. |
| `--[no-]enable-ula-internal-ipv6` |  |  | Enable/disable ULA internal IPv6 on this network. Enabling this feature will assign a /48 from google defined ULA prefix fd20::/20. Use --enable-ula-internal-ipv6 to enable and --no-enable-ula-internal-ipv6 to disable. |
| `--internal-ipv6-range` | INTERNAL_IPV6_RANGE |  | When enabling ULA internal IPv6, caller can optionally specify the /48 range they want from the google defined ULA prefix fd20::/20. ULA_IPV6_RANGE must be a valid /48 ULA IPv6 address and within the fd20::/20. Operation will fail if the speficied /48 is already in used by another resource. If the field is not speficied, then a /48 range will be randomly allocated from fd20::/20 and returned via this field. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet that can be transmitted on this network. Default value is 1460 bytes. The minimum value is 1300 bytes and the maximum value is 8896 bytes. The MTU advertised via DHCP to all instances attached to this network. |
| `--network-firewall-policy-enforcement-order` | one of: AFTER_CLASSIC_FIREWALL Network Firewall Policy is enforced after classic firewall |  | The Network Firewall Policy enforcement order of this network. If not specified, defaults to AFTER_CLASSIC_FIREWALL. NETWORK_FIREWALL_POLICY_ENFORCEMENT_ORDER must be one of: AFTER_CLASSIC_FIREWALL Network Firewall Policy is enforced after classic firewall. BEFORE_CLASSIC_FIREWALL Network Firewall Policy is enforced before classic firewall. |
| `--network-profile` | NETWORK_PROFILE |  | The network profile to apply to this network. |
| `--range` | RANGE |  | Specifies the IPv4 address range of legacy mode networks. The range must be specified in CIDR format: http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing This flag only works if mode is legacy (https://cloud.google.com/compute/docs/vpc/legacy). Using legacy networks is **DEPRECATED**, given that many newer Google Cloud Platform features are not supported on legacy networks. Please be advised that legacy networks may not be supported in the future. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the network. |
| `--subnet-mode` | one of: auto Subnets are created automatically |  | The subnet mode of the network. If not specified, defaults to AUTO. MODE must be one of: auto Subnets are created automatically. This is the recommended selection. custom Create subnets manually. legacy [Deprecated] Create an old style network that has a range and cannot have subnets. This is not recommended for new networks. |


**Examples:**
```bash
To create a regional auto subnet mode network with the name 'network-name',
run:

    $ gcloud compute networks create network-name

To create a global custom subnet mode network with the name 'network-name',
run:

    $ gcloud compute networks create network-name \
        --bgp-routing-mode=global --subnet-mode=custom
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/create)

---
### `gcloud compute networks delete`

Delete Compute Engine networks

gcloud compute networks delete deletes one or more Compute Engine networks.
Networks can only be deleted when no other resources (e.g., virtual machine
instances) refer to them.

**Synopsis:**
```
gcloud compute networks delete NAME [NAME ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the networks to delete.
```

**Examples:**
```bash
To delete a network with the name 'network-name', run:

    $ gcloud compute networks delete network-name

To delete two networks with the names 'network-name1' and 'network-name2',
run:

    $ gcloud compute networks delete network-name1 network-name2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/delete)

---
### `gcloud compute networks describe`

Describe a Compute Engine network

gcloud compute networks describe displays all data associated with Compute
Engine network in a project.

**Synopsis:**
```
gcloud compute networks describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network to describe.
```

**Examples:**
```bash
To describe a network with the name 'network-name', run:

    $ gcloud compute networks describe network-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/describe)

---
### `gcloud compute networks get-effective-firewalls`

Get the effective firewalls of a Compute Engine network

gcloud compute networks get-effective-firewalls is used to get the
effective firewalls applied to the network.

**Synopsis:**
```
gcloud compute networks get-effective-firewalls NAME [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network to get effective firewalls.

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


**Examples:**
```bash
To get the effective firewalls of network with name example-network, run:

    $ gcloud compute networks get-effective-firewalls example-network

To show all fields of the firewall rules, please show in JSON format with
option --format=json

To list more the fields of the rules of network example-network in table
format, run:

    $ gcloud compute networks get-effective-firewalls example-network \
        --format="table(
      type,
      firewall_policy_name,
      rule_type,
      priority,
      action,
      direction,
      ip_ranges.list():label=IP_RANGES,
      target_svc_acct,
      enableLogging,
      description,
      name,
      disabled,
      target_tags,
      src_svc_acct,
      src_tags,
      ruleTupleCount,
      targetResources:label=TARGET_RESOURCES)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/get-effective-firewalls)

---
### `gcloud compute networks list`

List Google Compute Engine networks

gcloud compute networks list displays all Google Compute Engine networks in
a project.

**Synopsis:**
```
gcloud compute networks list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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


**Examples:**
```bash
To list all networks in a project in table form, run:

    $ gcloud compute networks list

To list the URIs of all networks in a project, run:

    $ gcloud compute networks list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/list)

---
### `gcloud compute networks update`

Update a Compute Engine network

gcloud compute networks update is used to update Compute Engine networks.

**Synopsis:**
```
gcloud compute networks update NAME [--async]
    [--[no-]enable-ula-internal-ipv6]
    [--internal-ipv6-range=INTERNAL_IPV6_RANGE] [--mtu=MTU]
    [--network-firewall-policy-enforcement-order=NETWORK_FIREWALL_POLICY_ENFORCEMENT_ORDER]
    [--bgp-best-path-selection-mode=BGP_BEST_PATH_SELECTION_MODE
      --[no-]bgp-bps-always-compare-med
      --bgp-bps-inter-region-cost=BGP_BPS_INTER_REGION_COST]
    [--bgp-routing-mode=MODE | --switch-to-custom-subnet-mode]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--[no-]enable-ula-internal-ipv6` |  |  | Enable/disable ULA internal IPv6 on this network. Enabling this feature will assign a /48 from google defined ULA prefix fd20::/20. Use --enable-ula-internal-ipv6 to enable and --no-enable-ula-internal-ipv6 to disable. |
| `--internal-ipv6-range` | INTERNAL_IPV6_RANGE |  | When enabling ULA internal IPv6, caller can optionally specify the /48 range they want from the google defined ULA prefix fd20::/20. ULA_IPV6_RANGE must be a valid /48 ULA IPv6 address and within the fd20::/20. Operation will fail if the speficied /48 is already in used by another resource. If the field is not speficied, then a /48 range will be randomly allocated from fd20::/20 and returned via this field. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet that can be transmitted on this network. Default value is 1460 bytes. The minimum value is 1300 bytes and the maximum value is 8896 bytes. The MTU advertised via DHCP to all instances attached to this network. |
| `--network-firewall-policy-enforcement-order` | one of: AFTER_CLASSIC_FIREWALL Network Firewall Policy is enforced after classic firewall |  | The Network Firewall Policy enforcement order of this network. If not specified, defaults to AFTER_CLASSIC_FIREWALL. NETWORK_FIREWALL_POLICY_ENFORCEMENT_ORDER must be one of: AFTER_CLASSIC_FIREWALL Network Firewall Policy is enforced after classic firewall. BEFORE_CLASSIC_FIREWALL Network Firewall Policy is enforced before classic firewall. |


**Examples:**
```bash
To update regional network with the name 'network-name' to global, run:

    $ gcloud compute networks update network-name \
        --bgp-routing-mode=global

To update an auto subnet mode network with the name 'network-name' to
custom subnet mode, run:

    $ gcloud compute networks update network-name \
        --switch-to-custom-subnet-mode
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/update)

---

## `gcloud compute networks peerings` — list, create, and delete, and update VPC Network Peering
### `gcloud compute networks peerings create`

Create a Compute Engine network peering

gcloud compute networks peerings create is used to create peerings between
virtual networks. Each side of a peering association is set up
independently. Peering will be active only when the configuration from both
sides matches.

**Synopsis:**
```
gcloud compute networks peerings create NAME --network=NETWORK
    --peer-network=PEER_NETWORK [--async] [--auto-create-routes]
    [--export-custom-routes] [--export-subnet-routes-with-public-ip]
    [--import-custom-routes] [--import-subnet-routes-with-public-ip]
    [--peer-project=PEER_PROJECT] [--stack-type=STACK_TYPE]
    [--update-strategy=UPDATE_STRATEGY] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the peering.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The name of the network in the current project to be peered with the peer network. |
| `--peer-network` | PEER_NETWORK |  | The name of the network to be peered with the current network. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-create-routes` |  |  | (DEPRECATED) If set, will automatically create routes for the network peering. Flag auto-create-routes is deprecated. Peer network subnet routes are always created in a network when peered. Flag --auto-create-routes is deprecated and will be removed in a future release. |
| `--export-custom-routes` |  |  | If set, the network will export custom routes to peer network. Use --no-export-custom-routes to disable it. |
| `--export-subnet-routes-with-public-ip` |  |  | If set, the network will export subnet routes with addresses in the public IP ranges to peer network. Use --no-export-subnet-routes-with-public-ip to disable it. |
| `--import-custom-routes` |  |  | If set, the network will import custom routes from peer network. Use --no-import-custom-routes to disable it. |
| `--import-subnet-routes-with-public-ip` |  |  | If set, the network will import subnet routes with addresses in the public IP ranges from peer network. Use --no-import-subnet-routes-with-public-ip to disable it. |
| `--peer-project` | PEER_PROJECT |  | The name of the project for the peer network. If not specified, defaults to current project. |
| `--stack-type` | one of: IPV4_ONLY Only IPv4 traffic and routes will be exchanged across this peering |  | Stack type of the peering. If not specified, defaults to IPV4_ONLY. STACK_TYPE must be one of: IPV4_ONLY Only IPv4 traffic and routes will be exchanged across this peering. IPV4_IPV6 IPv4 traffic and routes will be exchanged across this peering. IPv6 traffic and routes will be exchanged if the matching peering configuration also has stack_type set to IPV4_IPV6. |
| `--update-strategy` | one of: INDEPENDENT Updates and deletes to the peering connection can be performed by either network admin |  | Update strategy of the peering. If not specified, defaults to INDEPENDENT. UPDATE_STRATEGY must be one of: INDEPENDENT Updates and deletes to the peering connection can be performed by either network admin. CONSENSUS Updates and deletes to the peering connection must be agreed upon by both network admins. |


**Examples:**
```bash
To create a network peering with the name 'peering-name' between the
network 'local-network' and the network 'peer-network' which exports and
imports custom routes and subnet routes with public IPs, run:

    $ gcloud compute networks peerings create peering-name \
        --network=local-network --peer-network=peer-network \
        --export-custom-routes --import-custom-routes \
        --export-subnet-routes-with-public-ip \
        --import-subnet-routes-with-public-ip
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/create)

---
### `gcloud compute networks peerings delete`

Delete a Compute Engine network peering

gcloud compute networks peerings delete deletes a Compute Engine network
peering.

**Synopsis:**
```
gcloud compute networks peerings delete NAME --network=NETWORK
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the peering to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The name of the network in the current project containing the peering. |


**Examples:**
```bash
To delete a network peering with the name 'peering-name' on the network
'local-network', run:

    $ gcloud compute networks peerings delete peering-name \
        --network=local-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/delete)

---
### `gcloud compute networks peerings list`

List Google Compute Engine peerings

gcloud compute networks peerings list displays all Google Compute Engine
peerings in a project.

**Synopsis:**
```
gcloud compute networks peerings list [--network=NETWORK]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | Only show peerings of a specific network. |


**Examples:**
```bash
To list all peerings in a project in table form, run:

    $ gcloud compute networks peerings list

To list the URIs of all peerings in a project, run:

    $ gcloud compute networks peerings list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/list)

---
### `gcloud compute networks peerings list-routes`

List received or advertised routes for a VPC network peering

gcloud compute networks peerings list-routes is used to list received or
advertised routes for a VPC network peering. This includes subnetwork
routes, static custom routes, and dynamic custom routes.

**Synopsis:**
```
gcloud compute networks peerings list-routes NAME --direction=DIRECTION
    --network=NETWORK --region=REGION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the peering to list routes for.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--direction` | one of: INCOMING To list received routes |  | Direction of the routes to list. To list received routes, use INCOMING. To list advertised routes, use OUTGOING. DIRECTION must be one of: INCOMING To list received routes. OUTGOING To list advertised routes. |
| `--network` | NETWORK |  | Network of the peering. |
| `--region` | REGION |  | Region to list the routes for. |


**Examples:**
```bash
List received routes for VPC network peering in us-central1:

    $ gcloud compute networks peerings list-routes peering-name \
        --network=network-name --region=us-central1 --direction=INCOMING
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/list-routes)

---
### `gcloud compute networks peerings request-delete`

Request deletion of a Compute Engine network peering

gcloud compute networks peerings request-delete is used to request deletion
of a consensus peering between virtual networks. The peering can be deleted
if both sides request deletion.

**Synopsis:**
```
gcloud compute networks peerings request-delete NAME --network=NETWORK
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the peering.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The name of the network in the current project containing the peering. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To request deletion of a consensus peering with the name 'peering-name'
between the network 'local-network' and the network 'peer-network', run:

    $ gcloud compute networks peerings request-delete peering-name \
      --network=local-network

    $ gcloud compute networks peerings request-delete peering-name \
      --network=peer-network

To complete the deletion, run gcloud compute networks peerings delete for
each side of the peering.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/request-delete)

---
### `gcloud compute networks peerings update`

Update a Compute Engine network peering

**Synopsis:**
```
gcloud compute networks peerings update NAME --network=NETWORK
    [--export-custom-routes] [--export-subnet-routes-with-public-ip]
    [--import-custom-routes] [--import-subnet-routes-with-public-ip]
    [--stack-type=STACK_TYPE] [--update-strategy=UPDATE_STRATEGY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the peering.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The name of the network in the current project to be peered with the peer network. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--export-custom-routes` |  |  | If set, the network will export custom routes to peer network. Use --no-export-custom-routes to disable it. |
| `--export-subnet-routes-with-public-ip` |  |  | If set, the network will export subnet routes with addresses in the public IP ranges to peer network. Use --no-export-subnet-routes-with-public-ip to disable it. |
| `--import-custom-routes` |  |  | If set, the network will import custom routes from peer network. Use --no-import-custom-routes to disable it. |
| `--import-subnet-routes-with-public-ip` |  |  | If set, the network will import subnet routes with addresses in the public IP ranges from peer network. Use --no-import-subnet-routes-with-public-ip to disable it. |
| `--stack-type` | one of: IPV4_ONLY Only IPv4 traffic and routes will be exchanged across this peering |  | Stack type of the peering. If not specified, defaults to IPV4_ONLY. STACK_TYPE must be one of: IPV4_ONLY Only IPv4 traffic and routes will be exchanged across this peering. IPV4_IPV6 IPv4 traffic and routes will be exchanged across this peering. IPv6 traffic and routes will be exchanged if the matching peering configuration also has stack_type set to IPV4_IPV6. |
| `--update-strategy` | one of: INDEPENDENT Updates and deletes to the peering connection can be performed by either network admin |  | Update strategy of the peering. If not specified, defaults to INDEPENDENT. UPDATE_STRATEGY must be one of: INDEPENDENT Updates and deletes to the peering connection can be performed by either network admin. CONSENSUS Updates and deletes to the peering connection must be agreed upon by both network admins. |


**Examples:**
```bash
To update the peering named peering-name to both export and import custom
routes, run:

    $ gcloud compute networks peerings update peering-name \
        --export-custom-routes --import-custom-routes

To update the peering named peering-name to both export and import subnet
routes with public ip, run:

    $ gcloud compute networks peerings update peering-name \
        --export-subnet-routes-with-public-ip \
        --import-subnet-routes-with-public-ip
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/peerings/update)

---

## `gcloud compute networks subnets` — list, describe, and delete, and update Compute Engine subnetworks
### `gcloud compute networks subnets add-iam-policy-binding`

Add an IAM policy binding to a Compute Engine subnetwork

Add an IAM policy binding to a Compute Engine subnetwork.

**Synopsis:**
```
gcloud compute networks subnets add-iam-policy-binding
    (SUBNETWORK : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnetwork resource - The subnetwork for which to add the IAM policy to.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument subnetwork on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNETWORK
     ID of the subnetwork or fully qualified identifier for the
     subnetwork.

     To set the subnetwork attribute:
     + provide the argument subnetwork on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument subnetwork on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/compute.securityAdmin'
for the user 'test-user@gmail.com' with subnetwork 'my-subnet' and region
'REGION', run:

    $ gcloud compute networks subnets add-iam-policy-binding my-subnet \
        --region=REGION --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/add-iam-policy-binding)

---
### `gcloud compute networks subnets create`

Define a subnet for a network in custom subnet mode

gcloud compute networks subnets create define a subnetwork for a network in
custom subnet mode. Subnets must be uniquely named per region.

**Synopsis:**
```
gcloud compute networks subnets create NAME --network=NETWORK
    [--description=DESCRIPTION] [--enable-flow-logs]
    [--enable-private-ip-google-access]
    [--external-ipv6-prefix=EXTERNAL_IPV6_PREFIX]
    [--internal-ipv6-prefix=INTERNAL_IPV6_PREFIX]
    [--ip-collection=IP_COLLECTION] [--ipv6-access-type=IPV6_ACCESS_TYPE]
    [--logging-aggregation-interval=LOGGING_AGGREGATION_INTERVAL]
    [--logging-filter-expr=LOGGING_FILTER_EXPR]
    [--logging-flow-sampling=LOGGING_FLOW_SAMPLING]
    [--logging-metadata=LOGGING_METADATA]
    [--logging-metadata-fields=[METADATA_FIELD,...]]
    [--private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE]
    [--purpose=PURPOSE] [--range=RANGE] [--region=REGION]
    [--reserved-internal-range=RESERVED_INTERNAL_RANGE]
    [--resource-manager-tags=[KEY=VALUE,...]] [--role=ROLE]
    [--secondary-range=PROPERTY=VALUE,[...]]
    [--secondary-range-with-reserved-internal-range=RANGE_NAME=INTERNAL_RANGE_URL,
      [...]] [--stack-type=STACK_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the subnetwork to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network to which the subnetwork belongs. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional description of this subnetwork. |
| `--enable-flow-logs` |  |  | Enable/disable VPC Flow Logs for this subnet. More information for VPC Flow Logs can be found at https://cloud.google.com/vpc/docs/using-flow-logs. |
| `--enable-private-ip-google-access` |  |  | Enable/disable access to Google Cloud APIs from this subnet for instances without a public ip address. |
| `--external-ipv6-prefix` | EXTERNAL_IPV6_PREFIX |  | The /64 external IPv6 CIDR range to assign to this subnet. The range must be associated with an IPv6 BYOIP sub-prefix that is defined by the --ip-collection flag. If you specify --ip-collection but not --external-ipv6-prefix, a random /64 range is allocated from the sub-prefix. For example, --external-ipv6-prefix=2600:1901:0:0:0:0:0:0/64 |
| `--internal-ipv6-prefix` | INTERNAL_IPV6_PREFIX |  | The /64 internal IPv6 CIDR range to assign to this subnet. The range must be associated with an IPv6 BYOIP sub-prefix that is defined by the --ip-collection flag. If you specify --ip-collection but not --internal-ipv6-prefix, a random /64 range is allocated from the sub-prefix. For example, --internal-ipv6-prefix 2600:1901:0:0:0:0:0:0/64 |
| `--ip-collection` | IP_COLLECTION |  | Resource reference to a public delegated prefix. The PublicDelegatedPrefix must be a sub-prefix in EXTERNAL_IPV6_SUBNETWORK_CREATION or INTERNAL_IPV6_SUBNETWORK_CREATION mode. |
| `--ipv6-access-type` | one of: EXTERNAL VMs in this subnet can have external IPv6 |  | IPv6 access type can be specified only when the subnet is created, or when the subnet is first updated to have a stack type of IPV4_IPV6. Once set, the access type is immutable. IPV6_ACCESS_TYPE must be one of: EXTERNAL VMs in this subnet can have external IPv6. INTERNAL VMs in this subnet can have internal IPv6. |
| `--logging-aggregation-interval` | one of: interval-10-min, interval-15-min, interval-1-min, interval-30-sec, interval-5-min, interval-5-sec |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. Toggles the aggregation interval for collecting flow logs. Increasing the interval time will reduce the amount of generated flow logs for long lasting connections. Default is an interval of 5 seconds per connection. LOGGING_AGGREGATION_INTERVAL must be one of: interval-10-min, interval-15-min, interval-1-min, interval-30-sec, interval-5-min, interval-5-sec. |
| `--logging-filter-expr` | LOGGING_FILTER_EXPR |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. Export filter used to define which logs should be generated. |
| `--logging-flow-sampling` | LOGGING_FLOW_SAMPLING |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. The value of the field must be in [0, 1]. Set the sampling rate of VPC flow logs within the subnetwork where 1.0 means all collected logs are reported and 0.0 means no logs are reported. Default is 0.5 which means half of all collected logs are reported. |
| `--logging-metadata` | one of: custom, exclude-all, include-all |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. Configures whether metadata fields should be added to the reported logs. Default is to exclude all metadata. LOGGING_METADATA must be one of: custom, exclude-all, include-all. |
| `--logging-metadata-fields` | [METADATA_FIELD,...] |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled and "metadata" is set to CUSTOM_METADATA. The comma-separated list of metadata fields that should be added to reported logs. |
| `--private-ipv6-google-access-type` | one of: disable, enable-bidirectional-access, enable-outbound-vm-access |  | The private IPv6 google access type for the VMs in this subnet. PRIVATE_IPV6_GOOGLE_ACCESS_TYPE must be one of: disable, enable-bidirectional-access, enable-outbound-vm-access. |
| `--purpose` | one of: GLOBAL_MANAGED_PROXY Reserved for Global Envoy-based Load Balancing |  | The purpose of this subnetwork. PURPOSE must be one of: GLOBAL_MANAGED_PROXY Reserved for Global Envoy-based Load Balancing. INTERNAL_HTTPS_LOAD_BALANCER Reserved for Internal HTTP(S) Load Balancing. PEER_MIGRATION Reserved for subnet migration between peered VPCs. PRIVATE Regular user created or automatically created subnet. PRIVATE_NAT Reserved for use as source range for Private NAT. PRIVATE_SERVICE_CONNECT Reserved for Private Service Connect Internal Load Balancing. REGIONAL_MANAGED_PROXY Reserved for Regional Envoy-based Load Balancing. |
| `--range` | RANGE |  | The IP space allocated to this subnetwork in CIDR format. |
| `--region` | REGION |  | Region of the subnetwork to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--reserved-internal-range` | RESERVED_INTERNAL_RANGE |  | If set, the primary IP range of the subnetwork will be associated with the given internal range resource. If --range is set, the subnetwork will only use the given IP range, which must be contained by the IP range defined by the internal range resource. For example, --range=10.0.0.0/24 --reserved-internal-range //networkconnectivity.googleapis.com/projects/PROJECT/locations/global/internalRanges/RANGE If --range is not set, the subnetwork will use the entire IP range defined by the internal range resource. For example, --reserved-internal-range //networkconnectivity.googleapis.com/projects/PROJECT/locations/global/internalRanges/RANGE |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the subnetwork. |
| `--role` | one of: ACTIVE The ACTIVE subnet that is currently used |  | The role of subnetwork. This field is required when the purpose is set to GLOBAL_MANAGED_PROXY, REGIONAL_MANAGED_PROXY or INTERNAL_HTTPS_LOAD_BALANCER. ROLE must be one of: ACTIVE The ACTIVE subnet that is currently used. BACKUP The BACKUP subnet that could be promoted to ACTIVE. |
| `--secondary-range` | PROPERTY=VALUE,[...] |  | Adds a secondary IP range to the subnetwork for use in IP aliasing. For example, --secondary-range range1=192.168.64.0/24 adds a secondary range 192.168.64.0/24 with name range1. * RANGE_NAME - Name of the secondary range. * RANGE - IP range in CIDR format. |
| `--secondary-range-with-reserved-internal-range` | RANGE_NAME=INTERNAL_RANGE_URL,[...] |  | Adds secondary IP ranges that are associated with internal range resources. For example, --secondary-range-with-reserved-internal-range range1=//networkconnectivity.googleapis.com/projects/PROJECT/locations/global/internalRanges/RANGE adds a secondary range with the reserved internal range resource. * RANGE_NAME - Name of the secondary range. * INTERNAL_RANGE_URL - URL of an internal range resource. |
| `--stack-type` | STACK_TYPE |  | The stack type for this subnet. Determines if IPv6 is enabled on the subnet. If not specified IPV4_ONLY will be used. STACK_TYPE must be one of: IPV4_IPV6 New VMs in this subnet can have both IPv4 and IPv6 addresses IPV4_ONLY New VMs in this subnet will only be assigned IPv4 addresses IPV6_ONLY New VMs in this subnet will only be assigned IPv6 addresses |


**Examples:**
```bash
To create the subnetwork subnet-1 with address range 10.10.0.0/24 in the
network network-0, run:

    $ gcloud compute networks subnets create subnet-1 \
        --network=network-0 --range=10.10.0.0/24 --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/create)

---
### `gcloud compute networks subnets delete`

Delete Google Cloud subnetworks

gcloud compute networks subnets delete deletes one or more Google Cloud
subnetworks. Subnetworks can only be deleted when no other resources, such
as VM instances, refer to them.".

**Synopsis:**
```
gcloud compute networks subnets delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the subnetworks to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the subnetworks to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete the subnetwork subnet-1 in the us-central1, run:

    $ gcloud compute networks subnets delete subnet-1 \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/delete)

---
### `gcloud compute networks subnets describe`

Describe a Compute Engine subnetwork

gcloud compute networks subnets describe displays all data associated with
a Compute Engine subnetwork.

**Synopsis:**
```
gcloud compute networks subnets describe NAME [--region=REGION]
    [--view=VIEW] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the subnetwork to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the subnetwork to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--view` | VIEW |  | Specifies the information to include in the output. VIEW must be (only one value is supported): WITH_UTILIZATION Output includes the IP address utilization data of all subnetwork ranges, showing total allocated and free IPv4 and IPv6 IP addresses. |


**Examples:**
```bash
To display all data associated with subnetwork subnet-1, run:

    $ gcloud compute networks subnets describe subnet-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/describe)

---
### `gcloud compute networks subnets expand-ip-range`

Expand the IP range of a Compute Engine subnetwork

gcloud compute networks subnets expand-ip-range expands the IP range of a
VPC subnetwork.

For more information about expanding a subnet, see Expanding a primary IP
range (https://cloud.google.com/vpc/docs/using-vpc#expand-subnet).

This command doesn't work for secondary subnets or for subnets that are
used exclusively for load balancer proxies. For more information, see
Proxy-only subnets for load balancers
(https://cloud.google.com/load-balancing/docs/l7-internal/proxy-only-subnets).

**Synopsis:**
```
gcloud compute networks subnets expand-ip-range NAME
    --prefix-length=PREFIX_LENGTH [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the subnetwork to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--prefix-length` | PREFIX_LENGTH |  | The new prefix length of the subnet. It must be smaller than the original and in the private address space 10.0.0.0/8, 172.16.0.0/12 or 192.168.0.0/16 defined in RFC 1918. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the subnetwork to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To expand the IP range of SUBNET to /16, run:

    $ gcloud compute networks subnets expand-ip-range SUBNET \
        --region=us-central1 --prefix-length=16
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/expand-ip-range)

---
### `gcloud compute networks subnets get-iam-policy`

Get the IAM policy for a Compute Engine subnetwork

gcloud compute networks subnets get-iam-policy displays the IAM policy
associated with a Compute Engine subnetwork in a project. If formatted as
JSON, the output can be edited and used as a policy file for
set-iam-policy. The output includes an "etag" field identifying the version
emitted and allowing detection of concurrent policy updates; see $ {parent}
set-iam-policy for additional details.

**Synopsis:**
```
gcloud compute networks subnets get-iam-policy
    (SUBNETWORK : --region=REGION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnetwork resource - The network to display the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument subnetwork on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNETWORK
     ID of the subnetwork or fully qualified identifier for the
     subnetwork.

     To set the subnetwork attribute:
     + provide the argument subnetwork on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument subnetwork on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Examples:**
```bash
To print the IAM policy for a given subnetwork, run:

    $ gcloud compute networks subnets get-iam-policy my-subnet \
        --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/get-iam-policy)

---
### `gcloud compute networks subnets list`

List Google Compute Engine subnetworks

gcloud compute networks subnets list displays all Google Compute Engine
subnetworks in a project.

By default, subnetworks from all regions are listed. The results can be
narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute networks subnets list [NAME ...] [--network=NETWORK]
    [--regexp=REGEXP, -r REGEXP] [--regions=REGION,[REGION,...]]
    [--view=VIEW] [--filter=EXPRESSION] [--limit=LIMIT]
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
| `--network` | NETWORK |  | Only show subnetworks of a specific network. |
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--regions` | REGION,[REGION,...] |  | If provided, only resources from the given regions are queried. |
| `--view` | VIEW |  | Specifies the information to include in the output. VIEW must be (only one value is supported): WITH_UTILIZATION Output includes the IP address utilization data of all subnetwork ranges, showing total allocated and free IPv4 and IPv6 IP addresses. |


**Examples:**
```bash
To list all subnetworks in a project in table form, run:

    $ gcloud compute networks subnets list

To list the URIs of all subnetworks in a project, run:

    $ gcloud compute networks subnets list --uri

To list all subnetworks in the us-central1 and europe-west1 regions, run:

    $ gcloud compute networks subnets list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/list)

---
### `gcloud compute networks subnets list-usable`

List Compute Engine subnetworks permitted for use

gcloud compute networks subnets list-usable is used to list Compute Engine
subnetworks in a project that the user has permission to use.

By default, usable subnetworks are listed for the default Google Cloud
project and user account. These values can be overridden by setting the
global flags: --project=PROJECT_ID and/or --account=ACCOUNT.

**Synopsis:**
```
gcloud compute networks subnets list-usable
    [--service-project=SERVICE_PROJECT] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-project` | SERVICE_PROJECT |  | The project id or project number in which the subnetwork is intended to be used. Only applied for Shared VPC. See Shared VPC documentation (https://cloud.google.com/vpc/docs/shared-vpc/). |


**Examples:**
```bash
To list all subnetworks in the default project that are usable by the
default user:

    $ gcloud compute networks subnets list-usable

To list all subnetworks in the host project HOST_PROJECT_ID of Shared VPC
that are usable in the service project SERVICE_PROJECT_ID (see Shared VPC
documentation (https://cloud.google.com/vpc/docs/shared-vpc/)) by the
default user:

    $ gcloud compute networks subnets list-usable \
        --project=HOST_PROJECT_ID --service-project=SERVICE_PROJECT_ID

To list all subnetworks in the project PROJECT_ID that are usable by the
user ACCOUNT:

    $ gcloud compute networks subnets list-usable --project=PROJECT_ID \
        --account=ACCOUNT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/list-usable)

---
### `gcloud compute networks subnets remove-iam-policy-binding`

Remove an IAM policy binding from a Compute Engine subnetwork

Remove an IAM policy binding from a Compute Engine subnetwork.

**Synopsis:**
```
gcloud compute networks subnets remove-iam-policy-binding
    (SUBNETWORK : --region=REGION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnetwork resource - The subnetwork for which to remove the IAM policy
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument subnetwork on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNETWORK
     ID of the subnetwork or fully qualified identifier for the
     subnetwork.

     To set the subnetwork attribute:
     + provide the argument subnetwork on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument subnetwork on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of
'roles/compute.securityAdmin' for the user 'test-user@gmail.com' with
subnetwork 'my-subnet' and region 'REGION', run:

    $ gcloud compute networks subnets remove-iam-policy-binding \
        my-subnet --region=REGION --member='user:test-user@gmail.com' \
        --role='roles/compute.securityAdmin'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/remove-iam-policy-binding)

---
### `gcloud compute networks subnets set-iam-policy`

Set the IAM policy for a Compute Engine subnetwork

Sets the IAM policy for the given subnetwork as defined in a JSON or YAML
file.

**Synopsis:**
```
gcloud compute networks subnets set-iam-policy
    (SUBNETWORK : --region=REGION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Subnetwork resource - The subnetwork to set the IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument subnetwork on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SUBNETWORK
     ID of the subnetwork or fully qualified identifier for the
     subnetwork.

     To set the subnetwork attribute:
     + provide the argument subnetwork on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The name of the Google Compute Engine region.

     To set the region attribute:
     + provide the argument subnetwork on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property compute/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read am IAM policy defined in a JSON file
'policy.json' and set it for the subnetwork my-subnet:

    $ gcloud compute networks subnets set-iam-policy my-subnet \
        policy.json --region=REGION

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/set-iam-policy)

---
### `gcloud compute networks subnets update`

Updates properties of an existing Compute Engine subnetwork

gcloud compute networks subnets update is used to update properties of an
existing Compute Engine subnetwork.

**Synopsis:**
```
gcloud compute networks subnets update NAME
    [--add-secondary-ranges-with-reserved-internal-range=RANGE_NAME=INTERNAL_RANGE_URL,
      [...]] [--drain-timeout=DRAIN_TIMEOUT; default="0s"]
    [--external-ipv6-prefix=EXTERNAL_IPV6_PREFIX]
    [--internal-ipv6-prefix=INTERNAL_IPV6_PREFIX]
    [--ip-collection=IP_COLLECTION] [--ipv6-access-type=IPV6_ACCESS_TYPE]
    [--logging-aggregation-interval=LOGGING_AGGREGATION_INTERVAL]
    [--logging-filter-expr=LOGGING_FILTER_EXPR]
    [--logging-flow-sampling=LOGGING_FLOW_SAMPLING]
    [--logging-metadata=LOGGING_METADATA]
    [--logging-metadata-fields=[METADATA_FIELD,...]] [--region=REGION]
    [--stack-type=STACK_TYPE]
    [--add-secondary-ranges=PROPERTY=VALUE,[...] | --[no-]enable-flow-logs
      | --[no-]enable-private-ip-google-access
      | --private-ipv6-google-access-type=PRIVATE_IPV6_GOOGLE_ACCESS_TYPE
      | --purpose=PURPOSE | --remove-secondary-ranges=PROPERTY=VALUE,[...]
      | --role=ROLE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the subnetwork to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-secondary-ranges-with-reserved-internal-range` | RANGE_NAME=INTERNAL_RANGE_URL,[...] |  | Adds secondary IP ranges that are associated with internal range resources. For example, --add-secondary-ranges-with-reserved-internal-range range1=//networkconnectivity.googleapis.com/projects/PROJECT/locations/global/internalRanges/RANGE adds a secondary range with the reserved internal range resource. * RANGE_NAME - Name of the secondary range. * INTERNAL_RANGE_URL - URL of an internal range resource. |
| `--drain-timeout` | DRAIN_TIMEOUT | 0s | The time period for draining traffic from Internal HTTP(S) Load Balancer proxies that are assigned addresses in the current ACTIVE subnetwork. For example, 1h, 60m and 3600s each specify a duration of 1 hour for draining the traffic. Longer times reduce the number of proxies that are draining traffic at any one time, and so improve the availability of proxies for load balancing. The drain timeout is only applicable when the [--role=ACTIVE] flag is being used. |
| `--external-ipv6-prefix` | EXTERNAL_IPV6_PREFIX |  | The /64 external IPv6 CIDR range to assign to this subnet. The range must be associated with an IPv6 BYOIP sub-prefix that is defined by the --ip-collection flag. If you specify --ip-collection but not --external-ipv6-prefix, a random /64 range is allocated from the sub-prefix. For example, --external-ipv6-prefix=2600:1901:0:0:0:0:0:0/64 |
| `--internal-ipv6-prefix` | INTERNAL_IPV6_PREFIX |  | The /64 internal IPv6 CIDR range to assign to this subnet. The range must be associated with an IPv6 BYOIP sub-prefix that is defined by the --ip-collection flag. If you specify --ip-collection but not --internal-ipv6-prefix, a random /64 range is allocated from the sub-prefix. For example, --internal-ipv6-prefix 2600:1901:0:0:0:0:0:0/64 |
| `--ip-collection` | IP_COLLECTION |  | Resource reference to a public delegated prefix. The PublicDelegatedPrefix must be a sub-prefix in EXTERNAL_IPV6_SUBNETWORK_CREATION or INTERNAL_IPV6_SUBNETWORK_CREATION mode. |
| `--ipv6-access-type` | one of: EXTERNAL VMs in this subnet can have external IPv6 |  | IPv6 access type can be specified only when the subnet is created, or when the subnet is first updated to have a stack type of IPV4_IPV6. Once set, the access type is immutable. IPV6_ACCESS_TYPE must be one of: EXTERNAL VMs in this subnet can have external IPv6. INTERNAL VMs in this subnet can have internal IPv6. |
| `--logging-aggregation-interval` | one of: interval-10-min, interval-15-min, interval-1-min, interval-30-sec, interval-5-min, interval-5-sec |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. Toggles the aggregation interval for collecting flow logs. Increasing the interval time will reduce the amount of generated flow logs for long lasting connections. Default is an interval of 5 seconds per connection. LOGGING_AGGREGATION_INTERVAL must be one of: interval-10-min, interval-15-min, interval-1-min, interval-30-sec, interval-5-min, interval-5-sec. |
| `--logging-filter-expr` | LOGGING_FILTER_EXPR |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. Export filter used to define which logs should be generated. |
| `--logging-flow-sampling` | LOGGING_FLOW_SAMPLING |  | Can only be specified if VPC Flow logs for this subnetwork is enabled. The value of the field must be in [0, 1]. Set the sampling rate of VPC flow logs within the subnetwork where 1.0 means all collected logs are reported and 0.0 means no logs are reported. Default is 0.5 which means half of all collected logs are reported. |
| `--logging-metadata` | one of: custom, exclude-all, include-all |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled. Configures whether metadata fields should be added to the reported logs. Default is to exclude all metadata. LOGGING_METADATA must be one of: custom, exclude-all, include-all. |
| `--logging-metadata-fields` | [METADATA_FIELD,...] |  | Can only be specified if VPC Flow Logs for this subnetwork is enabled and "metadata" is set to CUSTOM_METADATA. The comma-separated list of metadata fields that should be added to reported logs. |
| `--region` | REGION |  | Region of the subnetwork to update. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--stack-type` | STACK_TYPE |  | The stack type for this subnet. Determines if IPv6 is enabled on the subnet. STACK_TYPE must be one of: IPV4_IPV6 New VMs in this subnet can have both IPv4 and IPv6 addresses IPV4_ONLY New VMs in this subnet will only be assigned IPv4 addresses |


**Examples:**
```bash
To enable external IPv6 addresses on the subnetwork example-subnet-1 in
network-1, run

    $ gcloud compute networks subnets update example-subnet-1 \
        --stack-type=IPV4_IPV6 --ipv6-access-type=EXTERNAL \
        --region=REGION
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/subnets/update)

---

## `gcloud compute networks vpc-access` — manage VPC Access Service resources

## `gcloud compute networks vpc-access connectors` — manage Serverless VPC Access Service connectors
### `gcloud compute networks vpc-access connectors create`

Create a VPC Access connector

Create a new VPC Access connector with the given name.

This command can fail for the following reasons:
  o An instance with the same name already exists.
  o The active account does not have permission to create instances.

**Synopsis:**
```
gcloud compute networks vpc-access connectors create
    (CONNECTOR : --region=REGION) [--async] [--machine-type=MACHINE_TYPE]
    [--max-instances=MAX_INSTANCES;
      default=10 --min-instances=MIN_INSTANCES; default=2
      | --max-throughput=MAX_THROUGHPUT --min-throughput=MIN_THROUGHPUT]
    [--network=NETWORK; default="default" --range=RANGE
      | --subnet=SUBNET --subnet-project=SUBNET_PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Arguments and flags that specify the VPC Access
connector you want to create. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Compute region (e.g. us-central1) for the connector.

     To set the region attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--machine-type` | MACHINE_TYPE |  | Machine type of VMs underlying the VPC Access connector. Accepted values are e2-micro, f1-micro, and e2-standard-4. If left unspecified, the e2-micro machine type is used. |


**Examples:**
```bash
The following command creates a VPC Access connector with name
'my-vpc-connector' in region 'us-central1' in network 'my-network' with IP
CIDR range of '10.132.0.0/28'.

    $ gcloud compute networks vpc-access connectors create \
        my-vpc-connector --region=us-central1 --network=my-network \
        --range=10.132.0.0/28
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/connectors/create)

---
### `gcloud compute networks vpc-access connectors delete`

Delete a VPC Access connector

Delete a new VPC Access connector with the given name.

This command can fail for the following reasons:
  o An instance with the same name already exists.
  o The active account does not have permission to delete instances.

**Synopsis:**
```
gcloud compute networks vpc-access connectors delete
    (CONNECTOR : --region=REGION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Arguments and flags that specify the VPC Access
connector you want to delete. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Compute region (e.g. us-central1) for the connector.

     To set the region attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes a VPC Access connector with name
my-vpc-connector in region us-central1:

    $ gcloud compute networks vpc-access connectors delete \
        my-vpc-connector --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/connectors/delete)

---
### `gcloud compute networks vpc-access connectors describe`

Show metadata for a VPC Access connector

Display all metadata associated with a VPC Access connector given a valid
connector name.

This command can fail for the following reasons:
  o The connector specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud compute networks vpc-access connectors describe
    (CONNECTOR : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - The connector to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Compute region (e.g. us-central1) for the connector.

     To set the region attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
The following command prints metadata for a connector with name
my-vpcaccesss-connector in region us-central1:

    $ gcloud compute networks vpc-access connectors describe \
        my-vpcaccess-connector --region=us-central
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/connectors/describe)

---
### `gcloud compute networks vpc-access connectors list`

List VPC Access connectors

List all VPC Access connectors under the specified project and region.

You can specify the maximum number of connectors to list using the --limit
flag.

**Synopsis:**
```
gcloud compute networks vpc-access connectors list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
The following command lists a maximum of five instances in us-central1:

    $ gcloud compute networks vpc-access connectors list \
      --region=us-central1 --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/connectors/list)

---
### `gcloud compute networks vpc-access connectors update`

Update a VPC Access connector

Update an existing VPC Access connector with the given name.

This command can fail for the following reasons:
  o Invalid parameters are passed to this command.
  o The active account does not have permission to update instances.

**Synopsis:**
```
gcloud compute networks vpc-access connectors update
    (CONNECTOR : --region=REGION) [--async] [--machine-type=MACHINE_TYPE]
    [--max-instances=MAX_INSTANCES] [--min-instances=MIN_INSTANCES]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connector resource - Arguments and flags that specify the VPC Access
connector you want to update. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connector on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTOR
     ID of the connector or fully qualified identifier for the connector.

     To set the connector attribute:
     + provide the argument connector on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Compute region (e.g. us-central1) for the connector.

     To set the region attribute:
     + provide the argument connector on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--machine-type` | MACHINE_TYPE |  | If set, updates the machine type of VMs underlying the connector. Accepted values are "e2-micro", "f1-micro", and "e2-standard-4". |
| `--max-instances` | MAX_INSTANCES |  | If set, updates the maximum number of instances within an autoscaling group underlying the connector. Value must be between 3 and 10, inclusive, greater than or equal to the currently set maximum number of instances, and greater than the value specified by --min-instances. --min-instances must be provided. |
| `--min-instances` | MIN_INSTANCES |  | If set, updates the minimum number of instances within an autoscaling group underlying the connector. Value must be between 2 and 9, inclusive, greater than or equal to the currently set minimum number of instances, and less than the value specified by --max-instances. --max-instances must be provided |


**Examples:**
```bash
The following command updates a VPC Access connector with name
my-vpc-connector in region us-central1:

    $ gcloud compute networks vpc-access connectors update \
        my-vpc-connector --region=us-central1 --min-instances=3 \
        --max-instances=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/connectors/update)

---

## `gcloud compute networks vpc-access locations` — manage locations resource for VPC Access Service
### `gcloud compute networks vpc-access locations list`

List VPC Access Service regions

List all regions where VPC Access Service API is available.

**Synopsis:**
```
gcloud compute networks vpc-access locations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists all the regions where you can create VPC Access
connectors:

    $ gcloud compute networks vpc-access locations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/locations/list)

---

## `gcloud compute networks vpc-access operations` — manage operations resource for VPC Access Service
### `gcloud compute networks vpc-access operations describe`

Show metadata for a VPC Access Service operation

Display all metadata associated with a VPC Access Service operation given a
valid operation name.

This command can fail for the following reasons:
  o The operation specified does not exist.
  o The active account does not have permission to access the given
    operation.

**Synopsis:**
```
gcloud compute networks vpc-access operations describe
    (OPERATION : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

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

  --region=REGION
     Compute region (e.g. us-central1) for the connector.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
The following command prints metadata for an operation with the name in
region us-central1:

    $ gcloud compute networks vpc-access operations describe \
        operation-1564112342235-435a134f8c3f8-81bb4b49-0830c1f8 \
        --region=us-central
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/operations/describe)

---
### `gcloud compute networks vpc-access operations list`

List VPC Access Service operations

List all VPC Access Service operations under the specified project and
region.

You can specify the maximum number of operations to list using the --limit
flag.

**Synopsis:**
```
gcloud compute networks vpc-access operations list --region=REGION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[This must be specified.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
The following command lists a maximum of five operations in region
us-central1:

    $ gcloud compute networks vpc-access operations list \
      --region=us-central1 --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/networks/vpc-access/operations/list)

---
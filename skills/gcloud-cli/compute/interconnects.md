# gcloud compute interconnects

read and manipulate Compute Engine interconnects

### `gcloud compute interconnects create`

Create a Compute Engine interconnect

gcloud compute interconnects create is used to create interconnects. An
interconnect represents a single specific connection between Google and the
customer.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects create NAME
    --interconnect-type=INTERCONNECT_TYPE --link-type=LINK_TYPE
    --location=LOCATION --requested-link-count=REQUESTED_LINK_COUNT
    [--admin-enabled] [--customer-name=CUSTOMER_NAME]
    [--description=DESCRIPTION] [--noc-contact-email=NOC_CONTACT_EMAIL]
    [--remote-location=REMOTE_LOCATION]
    [--requested-features=[FEATURES,...]]
    [--resource-manager-tags=[KEY=VALUE,...]] [--subzone=SUBZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interconnect-type` | one of: DEDICATED Dedicated private interconnect |  | Type of the interconnect. INTERCONNECT_TYPE must be one of: DEDICATED Dedicated private interconnect. PARTNER Partner interconnect. Only available to approved partners. |
| `--link-type` | one of: LINK_TYPE_ETHERNET_100G_LR 100Gbps Ethernet, LR Optics |  | Type of the link for the interconnect. LINK_TYPE must be one of: LINK_TYPE_ETHERNET_100G_LR 100Gbps Ethernet, LR Optics. LINK_TYPE_ETHERNET_10G_LR 10Gbps Ethernet, LR Optics. LINK_TYPE_ETHERNET_400G_LR4 400Gbps Ethernet, LR4 Optics. |
| `--location` | LOCATION |  | The location for the interconnect. The locations can be listed by using the gcloud compute interconnects locations list command to find the appropriate location to use when creating an interconnect. |
| `--requested-link-count` | REQUESTED_LINK_COUNT |  | Target number of physical links in the link bundle. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-enabled` |  |  | Administrative status of the interconnect. If not provided on creation, defaults to enabled. When this is enabled, the interconnect is operational and will carry traffic across any functioning linked interconnect attachments. Use --no-admin-enabled to disable it. |
| `--customer-name` | CUSTOMER_NAME |  | Customer name to put in the Letter of Authorization as the party authorized to request an interconnect. This field is required for most interconnects, however it is prohibited when creating a Cross-Cloud Interconnect. |
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect. |
| `--noc-contact-email` | NOC_CONTACT_EMAIL |  | Email address to contact the customer NOC for operations and maintenance notifications regarding this interconnect. |
| `--remote-location` | REMOTE_LOCATION |  | The remote location for a Cross-Cloud Interconnect. The remote locations can be listed by using the gcloud compute interconnects remote-locations list command to find the appropriate remote location to use when creating a Cross-Cloud Interconnect. |
| `--requested-features` | one of: CROSS_SITE_NETWORK If specified then the interconnect is created on Cross-Site Network capable hardware ports |  | List of features requested for this interconnect. FEATURES must be one of: CROSS_SITE_NETWORK If specified then the interconnect is created on Cross-Site Network capable hardware ports. This parameter can only be provided during interconnect INSERT and cannot be changed using interconnect PATCH. L2_FORWARDING If specified then the interconnect is created on L2 forwarding capable hardware ports. This parameter can only be provided during interconnect INSERT and cannot be changed using interconnect PATCH. MACSEC If specified then the interconnect is created on MACsec capable hardware ports. If not specified, the interconnect is created on non-MACsec capable ports first, if available. This parameter can only be provided during interconnect INSERT and cannot be changed using interconnect PATCH. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the interconnect. |
| `--subzone` | one of: a Subzone a |  | Subzone in the LOCATION specified by the --location flag. SUBZONE must be one of: a Subzone a. b Subzone b. |


**Examples:**
```bash
To create an interconnect of type DEDICATED, run:

    $ gcloud compute interconnects create example-interconnect \
        --customer-name="Example Customer Name" \
        --interconnect-type=DEDICATED \
        --link-type=LINK_TYPE_ETHERNET_10G_LR \
        --location=example-zone1-1 --requested-link-count=1 \
        --noc-contact-email=noc@example.com \
        --description="Example interconnect"

To create a Cross-Cloud Interconnect, run:

    $ gcloud compute interconnects create example-cc-interconnect \
        --interconnect-type=DEDICATED \
        --link-type=LINK_TYPE_ETHERNET_10G_LR \
        --location=example-zone1-1 --requested-link-count=1 \
        --remote-location=example-remote-location \
        --noc-contact-email=noc@example.com \
        --description="Example Cross-Cloud Interconnect"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/create)

---
### `gcloud compute interconnects delete`

Delete Compute Engine interconnects

gcloud compute interconnects delete deletes Compute Engine interconnects.
Interconnects can only be deleted when no other resources (e.g.,
InterconnectAttachments) refer to them.

**Synopsis:**
```
gcloud compute interconnects delete NAME [NAME ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the interconnects to delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/delete)

---
### `gcloud compute interconnects describe`

Describe a Compute Engine interconnect

gcloud compute interconnects describe displays all data associated with
Compute Engine interconnect in a project.

**Synopsis:**
```
gcloud compute interconnects describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/describe)

---
### `gcloud compute interconnects get-diagnostics`

Get diagnostics of a Compute Engine interconnect

gcloud compute interconnects get-diagnostics displays all runtime data
associated with Compute Engine interconnect in a project.

**Synopsis:**
```
gcloud compute interconnects get-diagnostics NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/get-diagnostics)

---
### `gcloud compute interconnects list`

List Google Compute Engine interconnects

gcloud compute interconnects list displays all Google Compute Engine
interconnects in a project.

**Synopsis:**
```
gcloud compute interconnects list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all interconnects in a project in table form, run:

    $ gcloud compute interconnects list

To list the URIs of all interconnects in a project, run:

    $ gcloud compute interconnects list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/list)

---
### `gcloud compute interconnects update`

Update a Compute Engine interconnect

gcloud compute interconnects update is used to update interconnects. An
interconnect represents a single specific connection between Google and the
customer.

**Synopsis:**
```
gcloud compute interconnects update NAME [--admin-enabled]
    [--description=DESCRIPTION] [--noc-contact-email=NOC_CONTACT_EMAIL]
    [--requested-link-count=REQUESTED_LINK_COUNT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-enabled` |  |  | Administrative status of the interconnect. When this is enabled, the interconnect is operational and will carry traffic across any functioning linked interconnect attachments. Use --no-admin-enabled to disable it. |
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect. |
| `--noc-contact-email` | NOC_CONTACT_EMAIL |  | Email address to contact the customer NOC for operations and maintenance notifications regarding this interconnect. |
| `--requested-link-count` | REQUESTED_LINK_COUNT |  | Target number of physical links in the link bundle. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/update)

---

## `gcloud compute interconnects application-awareness` — read and manipulate configuration for application awareness on Compute Engine interconnect
### `gcloud compute interconnects application-awareness configure-bandwidth-percentage-policy`

Configure bandwidth percentage policy for application awareness configuration of a Compute Engine interconnect

gcloud compute interconnects application-awareness
configure-bandwidth-percentage-policy is used to configure bandwidth
percentage policy for using application awareness on interconnect.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects application-awareness
    configure-bandwidth-percentage-policy NAME
    --bandwidth-percentages=[TC1=TC1],
      [TC2=TC2],[TC3=TC3],[TC4=TC4],[TC5=TC5],[TC6=TC6] [--enabled]
    [--profile-description=PROFILE_DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to patch.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth-percentages` | [TC1=TC1],[TC2=TC2],[TC3=TC3],[TC4=TC4],[TC5=TC5],[TC6=TC6] |  | A list of bandwidth percentages, for configuring the bandwidth percentage policy or traffic shaping. For configuring bandwidth percentages for the bandwidth percentage policy: 1. Each bandwidth percentage value must be an integer between 1-100. 2. It is required to provide a percentage value for each class. 3. The sum of all bandwidth percentages must be 100. For configuring bandwidth percentages for traffic shaping: 1. Each bandwidth percentage value must be an integer between 1-100. 2. It is not required to provide a percentage value for each class. 3. The sum of all bandwidth percentages does not need to be 100. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enabled` |  |  | Enable or disable application awareness on the interconnect. Application awareness enablement will fail if the application awareness configuration is not specified. Use --no-enabled to disable it. |
| `--profile-description` | PROFILE_DESCRIPTION |  | Add profile description for application awareness. |


**Examples:**
```bash
To configure bandwidth percentage policy for an interconnect
example-interconnect, run:

    $ gcloud compute interconnects application-awareness \
        configure-bandwidth-percentage-policy example-interconnect \
        --bandwidth-percentages="TC1=5,TC2=5,TC3=75,TC4=5,TC5=5,TC6=5" \
        --enabled --profile-description="some string"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/application-awareness/configure-bandwidth-percentage-policy)

---
### `gcloud compute interconnects application-awareness configure-shaper-average-percentage`

Configure shaper average percentage for application awareness configuration of a Compute Engine interconnect

gcloud compute interconnects application-awareness
configure-shaper-average-percentage is used to configure shaper average
percentage for using application awareness on interconnect. Note that an
application awareness policy (strict priority or bandwidth percentage)
should be configure before configuring traffic shaping.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects application-awareness
    configure-shaper-average-percentage NAME
    --bandwidth-percentages=[TC1=TC1],
      [TC2=TC2],[TC3=TC3],[TC4=TC4],[TC5=TC5],[TC6=TC6] [--enabled]
    [--profile-description=PROFILE_DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to patch.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth-percentages` | [TC1=TC1],[TC2=TC2],[TC3=TC3],[TC4=TC4],[TC5=TC5],[TC6=TC6] |  | A list of bandwidth percentages, for configuring the bandwidth percentage policy or traffic shaping. For configuring bandwidth percentages for the bandwidth percentage policy: 1. Each bandwidth percentage value must be an integer between 1-100. 2. It is required to provide a percentage value for each class. 3. The sum of all bandwidth percentages must be 100. For configuring bandwidth percentages for traffic shaping: 1. Each bandwidth percentage value must be an integer between 1-100. 2. It is not required to provide a percentage value for each class. 3. The sum of all bandwidth percentages does not need to be 100. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enabled` |  |  | Enable or disable application awareness on the interconnect. Application awareness enablement will fail if the application awareness configuration is not specified. Use --no-enabled to disable it. |
| `--profile-description` | PROFILE_DESCRIPTION |  | Add profile description for application awareness. |


**Examples:**
```bash
To configure shaper average percentage for an interconnect
example-interconnect, run:

    $ gcloud compute interconnects application-awareness \
        configure-shaper-average-percentage example-interconnect \
        --bandwidth-percentages="TC1=30,TC2=90
    --enabled --profile-description="some string"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/application-awareness/configure-shaper-average-percentage)

---
### `gcloud compute interconnects application-awareness configure-strict-priority-policy`

Configure strict priority policy for application awareness configuration of a Compute Engine interconnect

gcloud compute interconnects application-awareness
configure-strict-priority-policy is used to configure strict priority
policy for using application awareness on interconnect.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects application-awareness
    configure-strict-priority-policy NAME [--enabled]
    [--profile-description=PROFILE_DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to patch.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enabled` |  |  | Enable or disable application awareness on the interconnect. Application awareness enablement will fail if the application awareness configuration is not specified. Use --no-enabled to disable it. |
| `--profile-description` | PROFILE_DESCRIPTION |  | Add profile description for application awareness. |


**Examples:**
```bash
To configure strict priority policy for an interconnect
example-interconnect, run:

    $ gcloud compute interconnects application-awareness \
        configure-strict-priority-policy example-interconnect \
        --enabled --profile-description="some string"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/application-awareness/configure-strict-priority-policy)

---
### `gcloud compute interconnects application-awareness delete`

Delete application awareness configuration of a Compute Engine interconnect

gcloud compute interconnects application-awareness delete is used to delete
all configuration state for application awareness on interconnect.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects application-awareness delete NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to patch.
```

**Examples:**
```bash
To delete application awareness configuration for an interconnect
example-interconnect, run:

    $ gcloud compute interconnects application-awareness delete \
        example-interconnect
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/application-awareness/delete)

---
### `gcloud compute interconnects application-awareness get-config`

Get application awareness configuration of a Compute Engine interconnect

gcloud compute interconnects application-awareness get-config displays
configuration data associated with application awareness on Compute Engine
interconnect in a project.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects application-awareness get-config NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to describe.
```

**Examples:**
```bash
To displays configuration data associated with application awareness on
Compute Engine interconnect in a project, run:

    $ gcloud compute interconnects application-awareness get-config \
        example-interconnect
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/application-awareness/get-config)

---
### `gcloud compute interconnects application-awareness update`

Updates application awareness configuration of a Compute Engine interconnect

gcloud compute interconnects application-awareness update allows the user
to enable or disable application awareness on Interconnect, as well as
add/update the description of the application awareness on Interconnect
profile. For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects application-awareness update NAME [--enabled]
    [--profile-description=PROFILE_DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to patch.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enabled` |  |  | Enable or disable application awareness on the interconnect. Application awareness enablement will fail if the application awareness configuration is not specified. Use --no-enabled to disable it. |
| `--profile-description` | PROFILE_DESCRIPTION |  | Add profile description for application awareness. |


**Examples:**
```bash
To update the application awareness config on Compute Engine interconnect
in a project, run:

    $ gcloud compute interconnects application-awareness update \
        example-interconnect application-awareness update --enabled \
        --profile-description="Some string"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/application-awareness/update)

---

## `gcloud compute interconnects attachments` — read and manipulate Compute Engine interconnect attachments
### `gcloud compute interconnects attachments delete`

Delete Compute Engine interconnect attachments

gcloud compute interconnects attachments delete deletes Compute Engine
interconnect attachments.

**Synopsis:**
```
gcloud compute interconnects attachments delete NAME [NAME ...]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the interconnect attachments to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the interconnect attachments to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/delete)

---
### `gcloud compute interconnects attachments describe`

Describe a Compute Engine interconnect attachment

gcloud compute interconnects attachments describe displays all data
associated with Compute Engine interconnect attachment in a project.

**Synopsis:**
```
gcloud compute interconnects attachments describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the interconnect attachment to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/describe)

---
### `gcloud compute interconnects attachments list`

List Google Compute Engine interconnect attachments

gcloud compute interconnects attachments list displays all Google Compute
Engine interconnect attachments in a project.

By default, interconnect attachments from all regions are listed. The
results can be narrowed down using a filter: --filter="region:( REGION ...
)".

**Synopsis:**
```
gcloud compute interconnects attachments list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all interconnect attachments in a project in table form, run:

    $ gcloud compute interconnects attachments list

To list the URIs of all interconnect attachments in a project, run:

    $ gcloud compute interconnects attachments list --uri

To list all interconnect attachments in the us-central1 and europe-west1
regions, run:

    $ gcloud compute interconnects attachments list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/list)

---

## `gcloud compute interconnects attachments dedicated` — create or manipulate dedicated interconnect attachments
### `gcloud compute interconnects attachments dedicated create`

Create a Compute Engine dedicated interconnect attachment

gcloud compute interconnects attachments dedicated create is used to create
a dedicated interconnect attachments. An interconnect attachment is what
binds the underlying connectivity of an interconnect to a path into and out
of the customer's cloud network.

**Synopsis:**
```
gcloud compute interconnects attachments dedicated create NAME
    --interconnect=INTERCONNECT --router=ROUTER [--bandwidth=BANDWIDTH]
    [--candidate-cloud-router-ip-address=CANDIDATE_CLOUD_ROUTER_IP_ADDRESS]
    [--candidate-cloud-router-ipv6-address=CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS]
    [--candidate-customer-router-ip-address=CANDIDATE_CUSTOMER_ROUTER_IP_ADDRESS]
    [--candidate-customer-router-ipv6-address=CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS]
    [--candidate-ipv6-subnets=[IPV6_SUBNET,...]]
    [--candidate-subnets=[SUBNET,...]]
    [--cloud-router-ipv6-interface-id=INTERFACE_ID]
    [--customer-router-ipv6-interface-id=PEER_INTERFACE_ID]
    [--description=DESCRIPTION] [--enable-admin] [--encryption=ENCRYPTION]
    [--ipsec-internal-addresses=[ADDRESSES]] [--mtu=MTU] [--region=REGION]
    [--resource-manager-tags=[KEY=VALUE,...]] [--stack-type=STACK_TYPE]
    [--subnet-length=SUBNET_LENGTH] [--vlan=VLAN] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interconnect` | INTERCONNECT |  | The interconnect for the interconnect attachment |
| `--router` | ROUTER |  | Google Cloud Router to use for dynamic routing. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth` | BANDWIDTH |  | Provisioned capacity of the attachment. BANDWIDTH must be one of: 50m 50 Mbit/s 100m 100 Mbit/s 200m 200 Mbit/s 300m 300 Mbit/s 400m 400 Mbit/s 500m 500 Mbit/s 1g 1 Gbit/s 2g 2 Gbit/s 5g 5 Gbit/s 10g 10 Gbit/s 20g 20 Gbit/s 50g 50 Gbit/s 100g 100 Gbit/s |
| `--candidate-cloud-router-ip-address` | CANDIDATE_CLOUD_ROUTER_IP_ADDRESS |  | Single IPv4 address + prefix length to be configured on the cloud router interface for this interconnect attachment. Example: 203.0.113.1/29 |
| `--candidate-cloud-router-ipv6-address` | CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the cloud router interface for this interconnect attachment. Example: 2001:db8::1/125 |
| `--candidate-customer-router-ip-address` | CANDIDATE_CUSTOMER_ROUTER_IP_ADDRESS |  | Single IPv4 address + prefix length to be configured on the customer router interface for this interconnect attachment. Example: 203.0.113.2/29 |
| `--candidate-customer-router-ipv6-address` | CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the customer router interface for this interconnect attachment. Example: 2001:db8::2/125 |
| `--candidate-ipv6-subnets` | [IPV6_SUBNET,...] |  | The candididate-ipv6-subnets field is not available. |
| `--candidate-subnets` | [SUBNET,...] |  | Up to 16 candidate prefixes that can be used to restrict the allocation of cloudRouterIpAddress and customerRouterIpAddress for this attachment. All prefixes must be within link-local address space. Google attempts to select an unused subnet of SUBNET_LENGTH from the supplied candidate subnet(s), or all of link-local space if no subnets supplied. Google does not re-use a subnet already in-use by your project, even if it's contained in one of the candidate subnets. The request fails if all candidate subnets are in use at Google's edge. |
| `--cloud-router-ipv6-interface-id` | INTERFACE_ID |  | cloud-router-ipv6-interface-id field is not available. |
| `--customer-router-ipv6-interface-id` | PEER_INTERFACE_ID |  | customer-router-ipv6-interface-id field is not available. |
| `--description` | DESCRIPTION |  | Human-readable plain-text description of attachment. |
| `--enable-admin` |  |  | Administrative status of the interconnect attachment. If not provided on creation, defaults to enabled. When this is enabled, the attachment is operational and will carry traffic. Use --no-enable-admin to disable it. |
| `--encryption` | one of: IPSEC, NONE |  | Indicates the user-supplied encryption option for this interconnect attachment (VLAN attachment). Possible values are: NONE - This is the default value, which means the interconnect attachment carries unencrypted traffic. VMs can send traffic to or receive traffic from such interconnect attachment. IPSEC - The interconnect attachment carries only traffic that is encrypted by an IPsec device; for example, an HA VPN gateway or third-party IPsec VPN. VMs cannot directly send traffic to or receive traffic from such an interconnect attachment. To use HA VPN over Cloud Interconnect, the interconnect attachment must be created with this option. ENCRYPTION must be one of: IPSEC, NONE. |
| `--ipsec-internal-addresses` | [ADDRESSES] |  | List of IP address range names that have been reserved for the interconnect attachment (VLAN attachment). Use this option only for an interconnect attachment that has its encryption option set as IPSEC. Currently only one internal IP address range can be specified for each attachment. When creating an HA VPN gateway for the interconnect attachment, if the attachment is configured to use a regional internal IP address, then the VPN gateway's IP address is allocated from the IP address range specified here. If this field is not specified when creating the interconnect attachment, then when creating any HA VPN gateways for this interconnect attachment, the HA VPN gateway's IP address is allocated from a regional external IP address pool. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet passing through this interconnect attachment. Must be one of 1440, 1460, 1500, or 8896. If not specified, the value will default to 1440. |
| `--region` | REGION |  | Region of the interconnect attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the interconnect. |
| `--stack-type` | one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment |  | Stack type of the protocol(s) enabled on this interconnect attachment. STACK_TYPE must be one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment. IPV4_ONLY Only IPv4 protocol is enabled on this attachment. |
| `--subnet-length` | one of: 29, 30 |  | Length of the IPv4 subnet mask for this attachment. 29 is the default value, except for attachments on Cross-Cloud Interconnects whose remote location's "constraints.subnetLengthRange" field specifies a minimum subnet length of 30. In that case, the default value is 30. The default value is recommended when there's no requirement on the subnet length. SUBNET_LENGTH must be one of: 29, 30. |
| `--vlan` | VLAN |  | Desired VLAN for this attachment, in the range 2-4093. If not supplied, Google will automatically select a VLAN. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/dedicated/create)

---
### `gcloud compute interconnects attachments dedicated update`

Update a Compute Engine dedicated interconnect attachment

gcloud compute interconnects attachments dedicated update is used to update
interconnect attachments. An interconnect attachment is what binds the
underlying connectivity of an interconnect to a path into and out of the
customer's cloud network.

**Synopsis:**
```
gcloud compute interconnects attachments dedicated update NAME
    [--bandwidth=BANDWIDTH]
    [--candidate-cloud-router-ipv6-address=CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS]
    [--candidate-customer-router-ipv6-address=CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS]
    [--candidate-ipv6-subnets=[IPV6_SUBNET,...]]
    [--cloud-router-ipv6-interface-id=INTERFACE_ID]
    [--customer-router-ipv6-interface-id=PEER_INTERFACE_ID]
    [--description=DESCRIPTION] [--enable-admin] [--mtu=MTU]
    [--region=REGION] [--stack-type=STACK_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to patch.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth` | BANDWIDTH |  | Provisioned capacity of the attachment. BANDWIDTH must be one of: 50m 50 Mbit/s 100m 100 Mbit/s 200m 200 Mbit/s 300m 300 Mbit/s 400m 400 Mbit/s 500m 500 Mbit/s 1g 1 Gbit/s 2g 2 Gbit/s 5g 5 Gbit/s 10g 10 Gbit/s 20g 20 Gbit/s 50g 50 Gbit/s 100g 100 Gbit/s |
| `--candidate-cloud-router-ipv6-address` | CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the cloud router interface for this interconnect attachment. Example: 2001:db8::1/125 |
| `--candidate-customer-router-ipv6-address` | CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the customer router interface for this interconnect attachment. Example: 2001:db8::2/125 |
| `--candidate-ipv6-subnets` | [IPV6_SUBNET,...] |  | The candididate-ipv6-subnets field is not available. |
| `--cloud-router-ipv6-interface-id` | INTERFACE_ID |  | cloud-router-ipv6-interface-id field is not available. |
| `--customer-router-ipv6-interface-id` | PEER_INTERFACE_ID |  | customer-router-ipv6-interface-id field is not available. |
| `--description` | DESCRIPTION |  | Human-readable plain-text description of attachment. |
| `--enable-admin` |  |  | Administrative status of the interconnect attachment. When this is enabled, the attachment is operational and will carry traffic. Use --no-enable-admin to disable it. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet passing through this interconnect attachment. Must be one of 1440, 1460, 1500, or 8896. If not specified, the value will default to 1440. |
| `--region` | REGION |  | Region of the interconnect attachment to patch. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--stack-type` | one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment |  | Stack type of the protocol(s) enabled on this interconnect attachment. STACK_TYPE must be one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment. IPV4_ONLY Only IPv4 protocol is enabled on this attachment. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/dedicated/update)

---

## `gcloud compute interconnects attachments groups` — create or manipulate interconnect attachment groups
### `gcloud compute interconnects attachments groups add-members`

Add member interconnect attachments to a Compute Engine interconnect attachment group

gcloud compute interconnects attachments groups add-members is used to add
member interconnect attachments to an interconnect attachment group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups add-members NAME
    --attachments=[INTERCONNECT_ATTACHMENT,...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachments` | [INTERCONNECT_ATTACHMENT,...] |  | Member interconnect attachments to add to or remove from the interconnect attachment group. |


**Examples:**
```bash
To add attachment-1 and attachment-2 to interconnect attachment group
example-attachment-group, run:

    $ gcloud compute interconnects attachments groups add-members \
        example-attachment-group \
        --attachments=region-1/attachment-1,region-2/attachment-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/add-members)

---
### `gcloud compute interconnects attachments groups create`

Create a Compute Engine interconnect attachment group

gcloud compute interconnects attachments groups create is used to create
interconnect attachment groups. An interconnect attachment group connects a
set of redundant interconnect attachments between Google and the customer.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups create NAME
    --intended-availability-sla=INTENDED_AVAILABILITY_SLA
    [--attachments=[INTERCONNECT_ATTACHMENT,...]]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment group to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--intended-availability-sla` | INTENDED_AVAILABILITY_SLA |  | The availability SLA that the user intends this group to support. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachments` | [INTERCONNECT_ATTACHMENT,...] |  | Member interconnect attachments to add to the interconnect attachment group initially. |
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect attachment group. |


**Examples:**
```bash
To create an interconnect attachment group capable of PRODUCTION_CRITICAL,
run:

    $ gcloud compute interconnects attachments groups create \
        example-attachment-group \
        --intended-availability-sla=PRODUCTION_CRITICAL \
        --description="Example interconnect attachment group"

It is easy to add members to an existing interconnect attachment group
after creation using the add-members command.

To create an interconnect attachment group capable of
PRODUCTION_NON_CRITICAL, with two members at creation time, run:

    $ gcloud compute interconnects attachments groups create \
        example-attachment-group \
        --intended-availability-sla=PRODUCTION_NON_CRITICAL \
        --attachments=region-1/attachment-1,region-2/attachment-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/create)

---
### `gcloud compute interconnects attachments groups delete`

Delete Compute Engine interconnect attachment groups

gcloud compute interconnects attachments groups delete is used to delete
interconnect attachment groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the interconnect attachment groups to delete.
```

**Examples:**
```bash
To delete an interconnect attachment group, run:

    $ gcloud compute interconnects attachments groups delete \
        example-attachment-group"

Although not shown in this example, you can delete multiple interconnect
attachment groups in a single command.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/delete)

---
### `gcloud compute interconnects attachments groups describe`

Describe a Compute Engine interconnect attachment group

gcloud compute interconnects attachments groups describe is used to
describe interconnect attachment groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups describe NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment group to describe.
```

**Examples:**
```bash
To describe an interconnect attachment group, run:

    $ gcloud compute interconnects attachments groups describe \
        example-attachment-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/describe)

---
### `gcloud compute interconnects attachments groups get-operational-status`

Get the operational status of a Compute Engine interconnect attachment group

gcloud compute interconnects attachments groups get-operational-status is
used to get the operational status of interconnect attachment groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups get-operational-status NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment group to get operational status.
```

**Examples:**
```bash
To get the operational status of interconnect attachment group
example-attachment-group, run:

    $ gcloud compute interconnects attachments groups \
        get-operational-status example-attachment-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/get-operational-status)

---
### `gcloud compute interconnects attachments groups list`

List interconnect attachment groups

gcloud compute interconnects attachments groups list is used to list
interconnect attachment groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list interconnect attachment groups, run:

    $ gcloud compute interconnects attachments groups list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/list)

---
### `gcloud compute interconnects attachments groups remove-members`

Remove member interconnect attachments from a Compute Engine interconnect attachment group

gcloud compute interconnects attachments groups remove-members is used to
remove member interconnect attachments from an interconnect attachment
group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups remove-members NAME
    --attachments=[INTERCONNECT_ATTACHMENT,...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachments` | [INTERCONNECT_ATTACHMENT,...] |  | Member interconnect attachments to add to or remove from the interconnect attachment group. |


**Examples:**
```bash
To remove attachment-1 and attachment-2 from interconnect attachment group
example-attachment-group, run:

    $ gcloud compute interconnects attachments groups remove-members \
        example-attachment-group \
        --attachments=region-1/attachment-1,region-2/attachment-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/remove-members)

---
### `gcloud compute interconnects attachments groups update`

Update a Compute Engine interconnect attachment group

gcloud compute interconnects attachments groups update is used to update
interconnect attachment groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects attachments groups update NAME
    [--attachments=[INTERCONNECT_ATTACHMENT,...]]
    [--description=DESCRIPTION]
    [--intended-availability-sla=INTENDED_AVAILABILITY_SLA]
    [--update-mask=UPDATE_MASK] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment group to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachments` | [INTERCONNECT_ATTACHMENT,...] |  | Member interconnect attachments to add to the interconnect attachment group initially. |
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect attachment group. |
| `--intended-availability-sla` | INTENDED_AVAILABILITY_SLA |  | The availability SLA that the user intends this group to support. |
| `--update-mask` | UPDATE_MASK |  | Optional update mask to specify which fields to update. Use commas to separate masks. If not specified, all fields present in the command will be updated. |


**Examples:**
```bash
To update an interconnect attachment group example-attachment-group's
intended availability SLA to PRODUCTION_CRITICAL, run:

    $ gcloud compute interconnects attachments groups update \
        example-attachment-group \
        --intended-availability-sla=PRODUCTION_CRITICAL

To update an interconnect attachment group example-attachment-group's
description to "example attachment group description", run:

    $ gcloud compute interconnects attachments groups update \
        example-attachment-group \
        --description="example attachment group description"

To update an interconnect attachment group example-attachment-group's
member attachments to attachment-1 and attachment-2, run:

    $ gcloud compute interconnects attachments groups update \
        example-attachment-group \
        --attachments=region-1/attachment-1,region-2/attachment-2 \
        --update-mask=attachments

Although you can add or remove member attachments using this command, it is
recommended to add or remove member attachments using the add-members and
remove-members commands.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/groups/update)

---

## `gcloud compute interconnects attachments l2-forwarding` — create or manipulate dedicated interconnect attachments
### `gcloud compute interconnects attachments l2-forwarding add-mapping`

Add new vlan to ip mapping rule to an L2-forwarding attachment

gcloud compute interconnects attachments l2-forwarding add-mapping add new
vlan to ip mapping rule to an L2-forwarding attachment.

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding add-mapping NAME
    --vlan-key=VLAN_KEY [--appliance-ip-address=ADDRESSES]
    [--appliance-name=APPLIANCE_NAME]
    [--inner-vlan-to-appliance-mappings=[innerApplianceIpAddress=INNERAPPLIANCEIPADDRESS],
      [innerVlanTags=INNERVLANTAGS]] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to patch.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vlan-key` | VLAN_KEY |  | Desired VLAN key for L2 forwarding mapping for the attachment. If not supplied, all mappings will be displayed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--appliance-ip-address` | ADDRESSES |  | A single IPv4 or IPv6 address used as the destination IP address for ingress packets that match on a VLAN tag, but do not match a more specific inner VLAN tag. |
| `--appliance-name` | APPLIANCE_NAME |  | The name of the L2 appliance mapping rule. |
| `--inner-vlan-to-appliance-mappings` | [innerApplianceIpAddress=INNERAPPLIANCEIPADDRESS],[innerVlanTags=INNERVLANTAGS] |  | A list of mapping rules from inner VLAN tags to IP addresses. If the inner VLAN is not explicitly mapped to an IP address range, the applianceIpAddress is used. |
| `--region` | REGION |  | Region of the interconnect attachment to patch. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/add-mapping)

---
### `gcloud compute interconnects attachments l2-forwarding create`

Create a Compute Engine L2 forwarding interconnect attachment

gcloud compute interconnects attachments l2-forwarding create is used to
create a L2 forwarding interconnect attachments. An interconnect attachment
is what binds the underlying connectivity of an interconnect to a path into
and out of the customer's cloud network.

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding create NAME
    --geneve-vni=GENEVE_HEADER --interconnect=INTERCONNECT
    --network=NETWORK
    --tunnel-endpoint-ip-address=TUNNEL_ENDPOINT_IP_ADDRESS
    [--bandwidth=BANDWIDTH]
    [--default-appliance-ip-address=DEFAULT_APPLIANCE_IP_ADDRESS]
    [--description=DESCRIPTION] [--enable-admin] [--mtu=MTU]
    [--region=REGION] [--resource-manager-tags=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--geneve-vni` | GENEVE_HEADER |  | A VNI identier for Geneve header, as defined in https://datatracker.ietf.org/doc/html/rfc8926, used for L2 forwarding. |
| `--interconnect` | INTERCONNECT |  | The interconnect for the interconnect attachment |
| `--network` | NETWORK |  | The Google Network to use for L2 forwarding. |
| `--tunnel-endpoint-ip-address` | TUNNEL_ENDPOINT_IP_ADDRESS |  | A single IPv4 or IPv6 address. This address will be used as the source IP address for L2 forwarding packets sent to the appliances, and must be used as the destination IP address for packets that should be sent out through this attachment. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth` | BANDWIDTH |  | Provisioned capacity of the attachment. BANDWIDTH must be one of: 50m 50 Mbit/s 100m 100 Mbit/s 200m 200 Mbit/s 300m 300 Mbit/s 400m 400 Mbit/s 500m 500 Mbit/s 1g 1 Gbit/s 2g 2 Gbit/s 5g 5 Gbit/s 10g 10 Gbit/s 20g 20 Gbit/s 50g 50 Gbit/s 100g 100 Gbit/s |
| `--default-appliance-ip-address` | DEFAULT_APPLIANCE_IP_ADDRESS |  | A single IPv4 or IPv6 address used as the default destination IP when there is no VLAN mapping result found for L2 forwarding. Unset field indicates the unmatched packet should be dropped. |
| `--description` | DESCRIPTION |  | Human-readable plain-text description of attachment. |
| `--enable-admin` |  |  | Administrative status of the interconnect attachment. If not provided on creation, defaults to enabled. When this is enabled, the attachment is operational and will carry traffic. Use --no-enable-admin to disable it. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet passing through this interconnect attachment. Must be one of 1440, 1460, 1500, or 8896. If not specified, the value will default to 1440. |
| `--region` | REGION |  | Region of the interconnect attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the interconnect. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/create)

---
### `gcloud compute interconnects attachments l2-forwarding describe-mapping`

Describe a Compute Engine L2 forwarding interconnect attachment

gcloud compute interconnects attachments l2-forwarding describe-mapping
displays all data associated with Compute Engine interconnect attachment in
a project.

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding describe-mapping
    NAME --vlan-key=VLAN_KEY [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vlan-key` | VLAN_KEY |  | Desired VLAN key for L2 forwarding mapping for the attachment. If not supplied, all mappings will be displayed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the interconnect attachment to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/describe-mapping)

---
### `gcloud compute interconnects attachments l2-forwarding list-mapping`

List Google Compute Engine interconnect attachments

gcloud compute interconnects attachments l2-forwarding list-mapping
displays all Google Compute Engine interconnect attachments in a project.

By default, interconnect attachments from all regions are listed. The
results can be narrowed down using a filter: --filter="region:( REGION ...
)".

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding list-mapping NAME
    [--region=REGION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the interconnect attachment to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To list all interconnect attachments in a project in table form, run:

    $ gcloud compute interconnects attachments l2-forwarding list-mapping

To list the URIs of all interconnect attachments in a project, run:

    $ gcloud compute interconnects attachments l2-forwarding \
        list-mapping --uri

To list all interconnect attachments in the us-central1 and europe-west1
regions, run:

    $ gcloud compute interconnects attachments l2-forwarding \
        list-mapping --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/list-mapping)

---
### `gcloud compute interconnects attachments l2-forwarding remove-mapping`

Remove vlan to ip mapping rule to an L2-forwarding attachment

gcloud compute interconnects attachments l2-forwarding remove-mapping
remove vlan to ip mapping rule to an L2-forwarding attachment.

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding remove-mapping NAME
    --vlan-key=VLAN_KEY [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vlan-key` | VLAN_KEY |  | Desired VLAN key for L2 forwarding mapping for the attachment. If not supplied, all mappings will be displayed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the interconnect attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/remove-mapping)

---
### `gcloud compute interconnects attachments l2-forwarding update`

Update a Compute Engine L2 forwarding interconnect attachment

gcloud compute interconnects attachments l2-forwarding update is used to
update interconnect attachments. An interconnect attachment is what binds
the underlying connectivity of an interconnect to a path into and out of
the customer's cloud network.

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding update NAME
    [--bandwidth=BANDWIDTH]
    [--default-appliance-ip-address=DEFAULT_APPLIANCE_IP_ADDRESS]
    [--description=DESCRIPTION] [--enable-admin]
    [--geneve-vni=GENEVE_HEADER] [--mtu=MTU] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to patch.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth` | BANDWIDTH |  | Provisioned capacity of the attachment. BANDWIDTH must be one of: 50m 50 Mbit/s 100m 100 Mbit/s 200m 200 Mbit/s 300m 300 Mbit/s 400m 400 Mbit/s 500m 500 Mbit/s 1g 1 Gbit/s 2g 2 Gbit/s 5g 5 Gbit/s 10g 10 Gbit/s 20g 20 Gbit/s 50g 50 Gbit/s 100g 100 Gbit/s |
| `--default-appliance-ip-address` | DEFAULT_APPLIANCE_IP_ADDRESS |  | A single IPv4 or IPv6 address used as the default destination IP when there is no VLAN mapping result found for L2 forwarding. Unset field indicates the unmatched packet should be dropped. |
| `--description` | DESCRIPTION |  | Human-readable plain-text description of attachment. |
| `--enable-admin` |  |  | Administrative status of the interconnect attachment. If not provided on creation, defaults to enabled. When this is enabled, the attachment is operational and will carry traffic. Use --no-enable-admin to disable it. |
| `--geneve-vni` | GENEVE_HEADER |  | A VNI identier for Geneve header, as defined in https://datatracker.ietf.org/doc/html/rfc8926, used for L2 forwarding. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet passing through this interconnect attachment. Must be one of 1440, 1460, 1500, or 8896. If not specified, the value will default to 1440. |
| `--region` | REGION |  | Region of the interconnect attachment to patch. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/update)

---
### `gcloud compute interconnects attachments l2-forwarding update-mapping`

Update vlan to ip mapping rule to an L2-forwarding attachment

gcloud compute interconnects attachments l2-forwarding update-mapping
update vlan to ip mapping rule to an L2-forwarding attachment.

**Synopsis:**
```
gcloud compute interconnects attachments l2-forwarding update-mapping NAME
    --vlan-key=VLAN_KEY [--appliance-ip-address=ADDRESSES]
    [--appliance-name=APPLIANCE_NAME]
    [--inner-vlan-to-appliance-mappings=[innerApplianceIpAddress=INNERAPPLIANCEIPADDRESS],
      [innerVlanTags=INNERVLANTAGS]] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--vlan-key` | VLAN_KEY |  | Desired VLAN key for L2 forwarding mapping for the attachment. If not supplied, all mappings will be displayed. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--appliance-ip-address` | ADDRESSES |  | A single IPv4 or IPv6 address used as the destination IP address for ingress packets that match on a VLAN tag, but do not match a more specific inner VLAN tag. |
| `--appliance-name` | APPLIANCE_NAME |  | The name of the L2 appliance mapping rule. |
| `--inner-vlan-to-appliance-mappings` | [innerApplianceIpAddress=INNERAPPLIANCEIPADDRESS],[innerVlanTags=INNERVLANTAGS] |  | A list of mapping rules from inner VLAN tags to IP addresses. If the inner VLAN is not explicitly mapped to an IP address range, the applianceIpAddress is used. |
| `--region` | REGION |  | Region of the interconnect attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/l2-forwarding/update-mapping)

---

## `gcloud compute interconnects attachments partner` — create or manipulate partner interconnect attachments
### `gcloud compute interconnects attachments partner create`

Create a Compute Engine partner interconnect attachment

gcloud compute interconnects attachments partner create is used to create
partner interconnect attachments. A partner interconnect attachment binds
the underlying connectivity of a provider's Interconnect to a path into and
out of the customer's cloud network.

**Synopsis:**
```
gcloud compute interconnects attachments partner create NAME
    --edge-availability-domain=AVAILABILITY_DOMAIN --router=ROUTER
    [--candidate-cloud-router-ip-address=CANDIDATE_CLOUD_ROUTER_IP_ADDRESS]
    [--candidate-cloud-router-ipv6-address=CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS]
    [--candidate-customer-router-ip-address=CANDIDATE_CUSTOMER_ROUTER_IP_ADDRESS]
    [--candidate-customer-router-ipv6-address=CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS]
    [--description=DESCRIPTION] [--enable-admin] [--encryption=ENCRYPTION]
    [--ipsec-internal-addresses=[ADDRESSES]] [--mtu=MTU] [--region=REGION]
    [--resource-manager-tags=[KEY=VALUE,...]] [--stack-type=STACK_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--edge-availability-domain` | AVAILABILITY_DOMAIN |  | Desired edge availability domain for this attachment: availability-domain-1, availability-domain-2, any. In each metro where the Partner can connect to Google, there are two sets of redundant hardware. These sets are described as edge availability domain 1 and 2. Within a metro, Google will only schedule maintenance in one availability domain at a time. This guarantee does not apply to availability domains outside the metro; Google may perform maintenance in (say) New York availability domain 1 at the same time as Chicago availability domain 1. AVAILABILITY_DOMAIN must be one of: any Any Availability Domain availability-domain-1 Edge Availability Domain 1 availability-domain-2 Edge Availability Domain 2 |
| `--router` | ROUTER |  | Google Cloud Router to use for dynamic routing. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--candidate-cloud-router-ip-address` | CANDIDATE_CLOUD_ROUTER_IP_ADDRESS |  | Single IPv4 address + prefix length to be configured on the cloud router interface for this interconnect attachment. Example: 203.0.113.1/29 |
| `--candidate-cloud-router-ipv6-address` | CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the cloud router interface for this interconnect attachment. Example: 2001:db8::1/125 |
| `--candidate-customer-router-ip-address` | CANDIDATE_CUSTOMER_ROUTER_IP_ADDRESS |  | Single IPv4 address + prefix length to be configured on the customer router interface for this interconnect attachment. Example: 203.0.113.2/29 |
| `--candidate-customer-router-ipv6-address` | CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the customer router interface for this interconnect attachment. Example: 2001:db8::2/125 |
| `--description` | DESCRIPTION |  | Human-readable plain-text description of attachment. |
| `--enable-admin` |  |  | Administrative status of the interconnect attachment. If not provided on creation, defaults to disabled. When this is enabled, the attachment is operational and will carry traffic. Use --no-enable-admin to disable it. |
| `--encryption` | one of: IPSEC, NONE |  | Indicates the user-supplied encryption option for this interconnect attachment (VLAN attachment). Possible values are: NONE - This is the default value, which means the interconnect attachment carries unencrypted traffic. VMs can send traffic to or receive traffic from such interconnect attachment. IPSEC - The interconnect attachment carries only traffic that is encrypted by an IPsec device; for example, an HA VPN gateway or third-party IPsec VPN. VMs cannot directly send traffic to or receive traffic from such an interconnect attachment. To use HA VPN over Cloud Interconnect, the interconnect attachment must be created with this option. ENCRYPTION must be one of: IPSEC, NONE. |
| `--ipsec-internal-addresses` | [ADDRESSES] |  | List of IP address range names that have been reserved for the interconnect attachment (VLAN attachment). Use this option only for an interconnect attachment that has its encryption option set as IPSEC. Currently only one internal IP address range can be specified for each attachment. When creating an HA VPN gateway for the interconnect attachment, if the attachment is configured to use a regional internal IP address, then the VPN gateway's IP address is allocated from the IP address range specified here. If this field is not specified when creating the interconnect attachment, then when creating any HA VPN gateways for this interconnect attachment, the HA VPN gateway's IP address is allocated from a regional external IP address pool. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet passing through this interconnect attachment. Must be one of 1440, 1460, 1500, or 8896. If not specified, the value will default to 1440. |
| `--region` | REGION |  | Region of the interconnect attachment to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the interconnect. |
| `--stack-type` | one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment |  | Stack type of the protocol(s) enabled on this interconnect attachment. STACK_TYPE must be one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment. IPV4_ONLY Only IPv4 protocol is enabled on this attachment. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/partner/create)

---
### `gcloud compute interconnects attachments partner update`

Update a Compute Engine partner interconnect attachment

gcloud compute interconnects attachments partner update is used to update
partner interconnect attachments. A partner interconnect attachment binds
the underlying connectivity of a provider's Interconnect to a path into and
out of the customer's cloud network.

**Synopsis:**
```
gcloud compute interconnects attachments partner update NAME
    [--candidate-cloud-router-ipv6-address=CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS]
    [--candidate-customer-router-ipv6-address=CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS]
    [--description=DESCRIPTION] [--enable-admin] [--mtu=MTU]
    [--region=REGION] [--stack-type=STACK_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect attachment to patch.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--candidate-cloud-router-ipv6-address` | CANDIDATE_CLOUD_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the cloud router interface for this interconnect attachment. Example: 2001:db8::1/125 |
| `--candidate-customer-router-ipv6-address` | CANDIDATE_CUSTOMER_ROUTER_IPV6_ADDRESS |  | Single IPv6 address + prefix length to be configured on the customer router interface for this interconnect attachment. Example: 2001:db8::2/125 |
| `--description` | DESCRIPTION |  | Human-readable plain-text description of attachment. |
| `--enable-admin` |  |  | Administrative status of the interconnect attachment. When this is enabled, the attachment is operational and will carry traffic. Use --no-enable-admin to disable it. |
| `--mtu` | MTU |  | Maximum transmission unit (MTU) is the size of the largest IP packet passing through this interconnect attachment. Must be one of 1440, 1460, 1500, or 8896. If not specified, the value will default to 1440. |
| `--region` | REGION |  | Region of the interconnect attachment to patch. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--stack-type` | one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment |  | Stack type of the protocol(s) enabled on this interconnect attachment. STACK_TYPE must be one of: IPV4_IPV6 Both IPv4 and IPv6 protocols are enabled on this attachment. IPV4_ONLY Only IPv4 protocol is enabled on this attachment. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/attachments/partner/update)

---

## `gcloud compute interconnects cross-site-networks` — create or manipulate cross site networks
### `gcloud compute interconnects cross-site-networks create`

Create a Compute Engine cross site network

gcloud compute interconnects cross-site-networks create is used to create
cross site networks. A cross site network contains wire groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects cross-site-networks create NAME
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the crossSiteNetwork to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the cross site network. |


**Examples:**
```bash
To create a cross site network, run:

    $ gcloud compute interconnects cross-site-networks create \
        example-csn --description="Example cross site network"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/cross-site-networks/create)

---
### `gcloud compute interconnects cross-site-networks delete`

Delete Compute Engine cross site networks

gcloud compute interconnects cross-site-networks delete is used to delete
cross site networks.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects cross-site-networks delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the crossSiteNetworks to delete.
```

**Examples:**
```bash
To delete a cross site network, run:

    $ gcloud compute interconnects cross-site-networks delete example-csn

Although not shown in this example, you can delete multiple cross site
networks in a single command.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/cross-site-networks/delete)

---
### `gcloud compute interconnects cross-site-networks describe`

Describe a Compute Engine cross site network

gcloud compute interconnects cross-site-networks describe is used to
describe a cross site network.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects cross-site-networks describe NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the crossSiteNetwork to describe.
```

**Examples:**
```bash
To describe a cross site network, run:

    $ gcloud compute interconnects cross-site-networks describe \
        example-csn
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/cross-site-networks/describe)

---
### `gcloud compute interconnects cross-site-networks list`

List Google Compute Engine cross site networks

gcloud compute interconnects cross-site-networks list displays all Google
Compute Engine cross site networks in a project.

**Synopsis:**
```
gcloud compute interconnects cross-site-networks list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all cross site networks in a project in table form, run:

    $ gcloud compute interconnects cross-site-networks list

To list the URIs of all cross site networks in a project, run:

    $ gcloud compute interconnects cross-site-networks list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/cross-site-networks/list)

---
### `gcloud compute interconnects cross-site-networks update`

Update a Compute Engine cross site network

gcloud compute interconnects cross-site-networks update is used to update
cross site networks.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects cross-site-networks update NAME
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the crossSiteNetwork to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the cross site network. |


**Examples:**
```bash
To update a cross site network's description, run:

    $ gcloud compute interconnects cross-site-networks update \
        example-csn --description="New description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/cross-site-networks/update)

---

## `gcloud compute interconnects groups` — create or manipulate interconnect groups
### `gcloud compute interconnects groups add-members`

Add member interconnects to a Compute Engine interconnect group

gcloud compute interconnects groups add-members is used to add member
interconnects to an interconnect group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups add-members NAME
    --interconnects=[INTERCONNECT,...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interconnects` | [INTERCONNECT,...] |  | Member interconnects to add to or remove from the interconnect group. |


**Examples:**
```bash
To add interconnects interconnect1 and interconnect2 to interconnect group
example-interconnect-group, run:

    $ gcloud compute interconnects groups add-members \
        example-interconnect-group \
        --interconnects=interconnect1,interconnect2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/add-members)

---
### `gcloud compute interconnects groups create`

Create a Compute Engine interconnect group

gcloud compute interconnects groups create is used to create interconnect
groups. An interconnect group connects a set of redundant interconnects
between Google and the customer.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups create NAME
    --intended-topology-capability=INTENDED_TOPOLOGY_CAPABILITY
    [--description=DESCRIPTION] [--interconnects=[INTERCONNECT,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--intended-topology-capability` | INTENDED_TOPOLOGY_CAPABILITY |  | The reliability the user intends this group to be capable of, in terms of the Interconnect product SLAs. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect group. |
| `--interconnects` | [INTERCONNECT,...] |  | Member interconnects to add to the interconnect group initially. |


**Examples:**
```bash
To create an interconnect group capable of PRODUCTION_CRITICAL, run:

    $ gcloud compute interconnects groups create \
        example-interconnect-group \
        --intended-topology-capability=PRODUCTION_CRITICAL \
        --description="Example interconnect group"

It is easy to add members to an existing interconnect group after creation
using the add-members command.

To create an interconnect group capable of PRODUCTION_NON_CRITICAL, with
two members at creation time, run:

    $ gcloud compute interconnects groups create \
        example-interconnect-group \
        --intended-topology-capability=PRODUCTION_NON_CRITICAL \
        --interconnects=interconnect-1,interconnect-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/create)

---
### `gcloud compute interconnects groups create-members`

Create new member interconnects in a Compute Engine interconnect group

gcloud compute interconnects groups create-members is used to create new
member interconnects in an interconnect group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups create-members NAME
    --interconnect=[INTERCONNECT,...] [--admin-enabled]
    [--customer-name=CUSTOMER_NAME] [--description=DESCRIPTION]
    [--facility=FACILITY]
    [--intent-mismatch-behavior=INTENT_MISMATCH_BEHAVIOR]
    [--interconnect-type=INTERCONNECT_TYPE] [--link-type=LINK_TYPE]
    [--noc-contact-email=NOC_CONTACT_EMAIL]
    [--remote-location=REMOTE_LOCATION]
    [--requested-features=[FEATURES,...]]
    [--requested-link-count=REQUESTED_LINK_COUNT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to create members.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interconnect` | [INTERCONNECT,...] |  | New member interconnects to create in the interconnect group. To create multiple interconnects, this flag should be specified multiple times. Each interconnect takes in the same set of flags as the gcloud compute interconnects create command, except instead of a location, a facility must be specified. These flags are defined as a comma separated list of flag=value pairs. Example: --interconnect name=interconnect1,facility=iad-1,description="my interconnect",link-type=LINK_TYPE_ETHERNET_10G_LR,requested-link-count=1, interconnect-type=DEDICATED,admin-enabled, noc-contact-email=noc@google.com,customer-name=customer-name requested-features=MACSEC:CROSS_SITE_NETWORK Note that for multiple requested-features, use a colon (:) as the delimiter, as the comma is used to separate the flags. Similarly, if you need to use a comma in another flag value, you should set an alternative delimiter for the --interconnect flag. Run gcloud topic escaping for more information. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-enabled` |  |  | Administrative status of the interconnect. If not provided on creation, defaults to enabled. When this is enabled, the interconnect is operational and will carry traffic across any functioning linked interconnect attachments. Use --no-admin-enabled to disable it. |
| `--customer-name` | CUSTOMER_NAME |  | Customer name to put in the Letter of Authorization as the party authorized to request an interconnect. This field is required for most interconnects, however it is prohibited when creating a Cross-Cloud Interconnect. |
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect. |
| `--facility` | FACILITY |  | The facility (zone free location) to create the interconnect in. |
| `--intent-mismatch-behavior` | one of: REJECT, CREATE |  | The behavior when the intent of the interconnect group does not match the topology capability of the member interconnects. INTENT_MISMATCH_BEHAVIOR must be one of: REJECT, CREATE. |
| `--interconnect-type` | one of: DEDICATED Dedicated private interconnect |  | Type of the interconnect. INTERCONNECT_TYPE must be one of: DEDICATED Dedicated private interconnect. PARTNER Partner interconnect. Only available to approved partners. |
| `--link-type` | one of: LINK_TYPE_ETHERNET_100G_LR 100Gbps Ethernet, LR Optics |  | Type of the link for the interconnect. LINK_TYPE must be one of: LINK_TYPE_ETHERNET_100G_LR 100Gbps Ethernet, LR Optics. LINK_TYPE_ETHERNET_10G_LR 10Gbps Ethernet, LR Optics. LINK_TYPE_ETHERNET_400G_LR4 400Gbps Ethernet, LR4 Optics. |
| `--noc-contact-email` | NOC_CONTACT_EMAIL |  | Email address to contact the customer NOC for operations and maintenance notifications regarding this interconnect. |
| `--remote-location` | REMOTE_LOCATION |  | The location of the interconnect for Cross-Cloud Interconnect. |
| `--requested-features` | one of: CROSS_SITE_NETWORK If specified then the interconnect is created on Cross-Site Network capable hardware ports |  | List of features requested for this interconnect. FEATURES must be one of: CROSS_SITE_NETWORK If specified then the interconnect is created on Cross-Site Network capable hardware ports. This parameter can only be provided during interconnect INSERT and cannot be changed using interconnect PATCH. L2_FORWARDING If specified then the interconnect is created on L2 forwarding capable hardware ports. This parameter can only be provided during interconnect INSERT and cannot be changed using interconnect PATCH. MACSEC If specified then the interconnect is created on MACsec capable hardware ports. If not specified, the interconnect is created on non-MACsec capable ports first, if available. This parameter can only be provided during interconnect INSERT and cannot be changed using interconnect PATCH. |
| `--requested-link-count` | REQUESTED_LINK_COUNT |  | Target number of physical links in the link bundle. |


**Examples:**
```bash
To create interconnects interconnect1 and interconnect2 in interconnect
group example-interconnect-group, run:

    $ gcloud compute interconnects groups create-members \
        example-interconnect-group --interconnect-type=DEDICATED \
        --link-type=LINK_TYPE_ETHERNET_10G_LR --requested-link-count=1 \
        --facility=iad-1 --interconnect="name=interconnect1" \
        --interconnect="name=interconnect2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/create-members)

---
### `gcloud compute interconnects groups delete`

Delete Compute Engine interconnect groups

gcloud compute interconnects groups delete is used to delete interconnect
groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the interconnect groups to delete.
```

**Examples:**
```bash
To delete an interconnect group, run:

    $ gcloud compute interconnects groups delete \
        example-interconnect-group"

Although not shown in this example, you can delete multiple interconnect
groups in a single command.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/delete)

---
### `gcloud compute interconnects groups describe`

Describe a Compute Engine interconnect group

gcloud compute interconnects groups describe is used to describe an
interconnect group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to describe.
```

**Examples:**
```bash
To describe interconnect group example-interconnect-group, run:

    $ gcloud compute interconnects groups describe \
        example-interconnect-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/describe)

---
### `gcloud compute interconnects groups get-operational-status`

Get the operational status of a Compute Engine interconnect group

gcloud compute interconnects groups get-operational-status is used to get
the operational status of an interconnect group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups get-operational-status NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to get operational status.
```

**Examples:**
```bash
To get the operational status of interconnect group
example-interconnect-group, run:

    $ gcloud compute interconnects groups get-operational-status \
        example-interconnect-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/get-operational-status)

---
### `gcloud compute interconnects groups list`

List interconnect groups

gcloud compute interconnects groups list is used to list interconnect
groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list interconnect groups, run:

    $ gcloud compute interconnects groups list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/list)

---
### `gcloud compute interconnects groups remove-members`

Remove member interconnects from a Compute Engine interconnect group

gcloud compute interconnects groups remove-members is used to remove member
interconnects from an interconnect group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups remove-members NAME
    --interconnects=[INTERCONNECT,...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interconnects` | [INTERCONNECT,...] |  | Member interconnects to add to or remove from the interconnect group. |


**Examples:**
```bash
To remove interconnects interconnect1 and interconnect2 from interconnect
group example-interconnect-group, run:

    $ gcloud compute interconnects groups remove-members \
        example-interconnect-group \
        --interconnects=interconnect1,interconnect2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/remove-members)

---
### `gcloud compute interconnects groups update`

Update a Compute Engine interconnect group

gcloud compute interconnects groups update is used to update interconnect
groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects groups update NAME [--description=DESCRIPTION]
    [--intended-topology-capability=INTENDED_TOPOLOGY_CAPABILITY]
    [--interconnects=[INTERCONNECT,...]] [--update-mask=UPDATE_MASK]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect group to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the interconnect group. |
| `--intended-topology-capability` | INTENDED_TOPOLOGY_CAPABILITY |  | The reliability the user intends this group to be capable of, in terms of the Interconnect product SLAs. |
| `--interconnects` | [INTERCONNECT,...] |  | Member interconnects to set the interconnect group to contain. |
| `--update-mask` | UPDATE_MASK |  | Optional update mask to specify which fields to update. Use commas to separate masks. If not specified, all fields present in the command will be updated. |


**Examples:**
```bash
To update an interconnect group example-interconnect-group's intended
topology capability to PRODUCTION_CRITICAL, run:

    $ gcloud compute interconnects groups update \
        example-interconnect-group \
        --intended-topology-capability=PRODUCTION_CRITICAL

To update an interconnect group example-interconnect-group's description to
"example interconnect group description", run:

    $ gcloud compute interconnects groups update \
        example-interconnect-group \
        --description="example interconnect group description"

To update an interconnect group example-interconnect-group's member
interconnects to interconnect-1 and interconnect-2, run:

    $ gcloud compute interconnects groups update \
        example-interconnect-group \
        --interconnects=interconnect-1,interconnect-2 \
        --update-mask=interconnects

Although you can add or remove member interconnects using this command, it
is recommended to add or remove member interconnects using the add-members
and remove-members commands.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/groups/update)

---

## `gcloud compute interconnects locations` — read and manipulate Compute Engine interconnect locations
### `gcloud compute interconnects locations describe`

Describe a Compute Engine interconnect location

Displays all data associated with Compute Engine interconnect location in a
project.

Example of usage:

    $ gcloud compute interconnects locations describe my-location

**Synopsis:**
```
gcloud compute interconnects locations describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect location to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/locations/describe)

---
### `gcloud compute interconnects locations list`

List Google Compute Engine interconnect locations

gcloud compute interconnects locations list displays all Google Compute
Engine interconnect locations in a project.

**Synopsis:**
```
gcloud compute interconnects locations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all interconnect locations in a project in table form, run:

    $ gcloud compute interconnects locations list

To list the URIs of all interconnect locations in a project, run:

    $ gcloud compute interconnects locations list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/locations/list)

---

## `gcloud compute interconnects macsec` — read and manipulate Compute Engine interconnect MACsec configuration
### `gcloud compute interconnects macsec add-key`

Add pre-shared key to a Compute Engine interconnect MACsec configuration

gcloud compute interconnects macsec add-key is used to add a pre-shared key
to MACsec configuration of interconnect.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects macsec add-key NAME --key-name=KEY_NAME
    [--start-time=START_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-name` | KEY_NAME |  | A name of pre-shared key being added to MACsec configuration of the interconnect. The name must be 1-63 characters long, and comply with RFC1035. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--start-time` | START_TIME |  | A RFC3339 timestamp on or after which the key is valid. startTime can be in the future. If the keychain has a single key, --start-time can be omitted. If the keychain has multiple keys, --start-time is mandatory for each key. The start times of two consecutive keys must be at least 6 hours apart. |


**Examples:**
```bash
To add a pre-shared key to MACsec configuration, run:

    $ gcloud compute interconnects macsec add-key example-interconnect \
        --key-name=default-key --start-time=2021-02-01T12:12:12Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/macsec/add-key)

---
### `gcloud compute interconnects macsec get-config`

Get MACsec configuration of a Compute Engine interconnect

gcloud compute interconnects macsec get-config displays all MACsec
configuration data associated with Compute Engine interconnect in a
project.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects macsec get-config NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to describe.
```

**Examples:**
```bash
To displays all MACsec configuration data associated with Compute Engine
interconnect in a project, run:

    $ gcloud compute interconnects macsec get-config example-interconnect
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/macsec/get-config)

---
### `gcloud compute interconnects macsec remove-key`

Remove pre-shared key from a Compute Engine interconnect MACsec configuration

gcloud compute interconnects macsec remove-key is used to remove pre-shared
key from MACsec configuration of interconnect.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects macsec remove-key NAME --key-name=KEY_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-name` | KEY_NAME |  | The name of pre-shared key being removed from MACsec configuration of the interconnect. |


**Examples:**
```bash
To remove a pre-shared key from MACsec configuration, run:

    $ gcloud compute interconnects macsec remove-key \
        example-interconnect --key-name=default-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/macsec/remove-key)

---
### `gcloud compute interconnects macsec update`

Update a Compute Engine interconnect MACsec configuration

gcloud compute interconnects macsec update is used to update MACsec
configuration of interconnect. An interconnect represents a single specific
connection between Google and the customer.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects macsec update NAME [--enabled] [--fail-open]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enabled` |  |  | Enable or disable MACsec on this Interconnect. MACsec enablement will fail if the MACsec configuration is not specified. Use --no-enabled to disable it. |
| `--fail-open` |  |  | If enabled, the Interconnect will be configured with a should-secure MACsec security policy, that allows the Google router to fallback to cleartext traffic if the MKA session cannot be established. By default, the Interconnect will be configured with a must-secure security policy that drops all traffic if the MKA session cannot be established with your router. Use --no-fail-open to disable it. |


**Examples:**
```bash
To enable MACsec on an interconnect, run:

    $ gcloud compute interconnects macsec update example-interconnect \
        --enabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/macsec/update)

---
### `gcloud compute interconnects macsec update-key`

Update pre-shared key in a Compute Engine interconnect MACsec configuration

gcloud compute interconnects macsec update-key is used to update a
pre-shared key in MACsec configuration of interconnect.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects macsec update-key NAME --key-name=KEY_NAME
    [--start-time=START_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the interconnect to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-name` | KEY_NAME |  | A name of pre-shared key being added to MACsec configuration of the interconnect. The name must be 1-63 characters long, and comply with RFC1035. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--start-time` | START_TIME |  | A RFC3339 timestamp on or after which the key is valid. startTime can be in the future. If the keychain has a single key, --start-time can be omitted. If the keychain has multiple keys, --start-time is mandatory for each key. The start times of two consecutive keys must be at least 6 hours apart. |


**Examples:**
```bash
To update a pre-shared key in MACsec configuration, run:

    $ gcloud compute interconnects macsec update-key \
        example-interconnect --key-name=default-key \
        --start-time=2021-02-01T12:12:12Z
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/macsec/update-key)

---

## `gcloud compute interconnects remote-locations` — read and manipulate Google Compute Engine interconnect remote locations
### `gcloud compute interconnects remote-locations describe`

Describe a Google Compute Engine interconnect remote location

Displays all data associated with Google Compute Engine interconnect remote
location in a project.

**Synopsis:**
```
gcloud compute interconnects remote-locations describe NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Cloud Interconnect remote location to describe.
```

**Examples:**
```bash
Example of usage:

    $ gcloud compute interconnects remote-locations describe \
        my-remote-location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/remote-locations/describe)

---
### `gcloud compute interconnects remote-locations list`

List Google Compute Engine Cloud Interconnect remote locations

gcloud compute interconnects remote-locations list displays all Google
Compute Engine Cloud Interconnect remote locations in a project.

**Synopsis:**
```
gcloud compute interconnects remote-locations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Cloud Interconnect remote locations in a project in table form,
run:

    $ gcloud compute interconnects remote-locations list

To list the URIs of all Cloud Interconnect remote locations in a project,
run:

    $ gcloud compute interconnects remote-locations list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/remote-locations/list)

---

## `gcloud compute interconnects wire-groups` — create or manipulate wire groups
### `gcloud compute interconnects wire-groups add-endpoint`

Add endpoint to a Compute Engine wire group

gcloud compute interconnects wire-groups add-endpoint is used to add
endpoints to a wire group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups add-endpoint NAME
    --cross-site-network=CROSS_SITE_NETWORK --endpoint-label=ENDPOINT_LABEL
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |
| `--endpoint-label` | ENDPOINT_LABEL |  | The endpoint label for the wire group. |


**Examples:**
```bash
To add an endpoint to a wire group, run:

    $ gcloud compute interconnects wire-groups add-endpoint example-wg \
        --cross-site-network=example-csn --endpoint-label=endpoint-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/add-endpoint)

---
### `gcloud compute interconnects wire-groups add-interconnect`

Add interconnect to a Compute Engine wire group

gcloud compute interconnects wire-groups add-interconnect is used to add
interconnects to a wire group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups add-interconnect NAME
    --cross-site-network=CROSS_SITE_NETWORK --endpoint-label=ENDPOINT_LABEL
    --interconnect=INTERCONNECT --interconnect-label=INTERCONNECT_LABEL
    --vlan-tags=VLAN_TAGS [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |
| `--endpoint-label` | ENDPOINT_LABEL |  | The endpoint label for the wire group. |
| `--interconnect` | INTERCONNECT |  | The interconnect for the wire group endpoint. |
| `--interconnect-label` | INTERCONNECT_LABEL |  | The interconnect label for the wire group endpoint. |
| `--vlan-tags` | VLAN_TAGS |  | The vlan tags for the interconnect on the wire group endpoint. |


**Examples:**
```bash
To add an interconnect to a wire group, run:

    $ gcloud compute interconnects wire-groups add-interconnect \
        example-wg --cross-site-network=example-csn \
        --endpoint-label=endpoint-1 \
        --interconnect-label=interconnect-1 \
        --interconnect=example-interconnect --vlan-tags=111
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/add-interconnect)

---
### `gcloud compute interconnects wire-groups create`

Create a Compute Engine wire group

gcloud compute interconnects wire-groups create is used to create wire
groups. A wire group represents a group of redundant wires between
interconnects in two different metros. Each WireGroup belongs to a
CrossSiteNetwork.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups create NAME
    --bandwidth-allocation=BANDWIDTH_ALLOCATION
    --bandwidth-unmetered=BANDWIDTH_UNMETERED
    --cross-site-network=CROSS_SITE_NETWORK [--admin-enabled]
    [--description=DESCRIPTION] [--fault-response=FAULT_RESPONSE]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--bandwidth-allocation` | one of: ALLOCATE_PER_WIRE Configures a separate unmetered bandwidth allocation (and associated charges) for each wire in the group |  | The bandwidth allocation for the wire group. BANDWIDTH_ALLOCATION must be one of: ALLOCATE_PER_WIRE Configures a separate unmetered bandwidth allocation (and associated charges) for each wire in the group. SHARED_WITH_WIRE_GROUP Configures one unmetered bandwidth allocation for the wire group. The unmetered bandwidth is divided equally across each wire in the group, but dynamic throttling reallocates unused unmetered bandwidth from unused or underused wires to other wires in the group. |
| `--bandwidth-unmetered` | BANDWIDTH_UNMETERED |  | The amount of unmetered bandwidth to assign to the wire group. |
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-enabled` |  |  | Administrative status of the wire group. If not provided on creation, defaults to enabled. When this is enabled, the wire group is operational and will carry traffic. Use --no-admin-enabled to disable it. |
| `--description` | DESCRIPTION |  | An optional, textual description for the wire group. |
| `--fault-response` | FAULT_RESPONSE |  | The fault response for the wire group. FAULT_RESPONSE must be one of: DISABLE_PORT Disable port NONE None |
| `--validate-only` |  |  | Validate the new configuration, but don't update it. |


**Examples:**
```bash
To create a wire group, run:

    $ gcloud compute interconnects wire-groups create example-wg \
        --cross-site-network=example-csn --bandwidth-unmetered=1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/create)

---
### `gcloud compute interconnects wire-groups delete`

Delete Compute Engine wire groups

gcloud compute interconnects wire-groups delete is used to delete wire
groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups delete NAME [NAME ...]
    --cross-site-network=CROSS_SITE_NETWORK [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the wire groups to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |


**Examples:**
```bash
To delete a wire group, run:

    $ gcloud compute interconnects wire-groups delete example-wg \
        --cross-site-network=example-csn
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/delete)

---
### `gcloud compute interconnects wire-groups describe`

Describe a Compute Engine wire group

gcloud compute interconnects wire-groups describe is used to describe a
wire group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups describe NAME
    --cross-site-network=CROSS_SITE_NETWORK [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to describe.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |


**Examples:**
```bash
To describe a wire group, run:

    $ gcloud compute interconnects wire-groups describe example-wg \
        --cross-site-network=example-csn
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/describe)

---
### `gcloud compute interconnects wire-groups list`

List Google Compute Engine wire groups

gcloud compute interconnects wire-groups list displays all Google Compute
Engine wire groups in a project.

**Synopsis:**
```
gcloud compute interconnects wire-groups list
    --cross-site-network=CROSS_SITE_NETWORK [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |


**Examples:**
```bash
To list all wire groups in a project in table form, run:

    $ gcloud compute interconnects wire-groups list

To list the URIs of all wire groups in a project, run:

    $ gcloud compute interconnects wire-groups list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/list)

---
### `gcloud compute interconnects wire-groups remove-endpoint`

Remove endpoint from a Compute Engine wire group

gcloud compute interconnects wire-groups remove-endpoint is used to remove
endpoints from a wire group.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups remove-endpoint NAME
    --cross-site-network=CROSS_SITE_NETWORK --endpoint-label=ENDPOINT_LABEL
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |
| `--endpoint-label` | ENDPOINT_LABEL |  | The endpoint label for the wire group. |


**Examples:**
```bash
To remove an endpoint from a wire group, run:

    $ gcloud compute interconnects wire-groups remove-endpoint \
        example-wg --cross-site-network=example-csn \
        --endpoint-label=endpoint-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/remove-endpoint)

---
### `gcloud compute interconnects wire-groups remove-interconnect`

Remove interconnect from a wire group

gcloud compute interconnects wire-groups remove-interconnect is used to
remove interconnects from a wire group endpoint.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups remove-interconnect NAME
    --cross-site-network=CROSS_SITE_NETWORK --endpoint-label=ENDPOINT_LABEL
    --interconnect-label=INTERCONNECT_LABEL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |
| `--endpoint-label` | ENDPOINT_LABEL |  | The endpoint label for the wire group. |
| `--interconnect-label` | INTERCONNECT_LABEL |  | The interconnect label for the wire group endpoint. |


**Examples:**
```bash
To remove an interconnect from a wire group endpoint, run:

    $ gcloud compute interconnects wire-groups remove-interconnect \
        example-wg --cross-site-network=example-csn \
        --endpoint-label=endpoint-1 \
        --interconnect-label=example-interconnect
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/remove-interconnect)

---
### `gcloud compute interconnects wire-groups update`

Update a Compute Engine wire group

gcloud compute interconnects wire-groups update is used to update wire
groups.

For an example, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud compute interconnects wire-groups update NAME
    --cross-site-network=CROSS_SITE_NETWORK [--admin-enabled]
    [--bandwidth-allocation=BANDWIDTH_ALLOCATION]
    [--bandwidth-unmetered=BANDWIDTH_UNMETERED] [--description=DESCRIPTION]
    [--fault-response=FAULT_RESPONSE] [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the wire group to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cross-site-network` | CROSS_SITE_NETWORK |  | Name of the crossSiteNetwork to operate on. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-enabled` |  |  | Administrative status of the wire group. When this is enabled, the wire group is operational and will carry traffic. Use --no-admin-enabled to disable it. |
| `--bandwidth-allocation` | one of: ALLOCATE_PER_WIRE Configures a separate unmetered bandwidth allocation (and associated charges) for each wire in the group |  | The bandwidth allocation for the wire group. BANDWIDTH_ALLOCATION must be one of: ALLOCATE_PER_WIRE Configures a separate unmetered bandwidth allocation (and associated charges) for each wire in the group. SHARED_WITH_WIRE_GROUP Configures one unmetered bandwidth allocation for the wire group. The unmetered bandwidth is divided equally across each wire in the group, but dynamic throttling reallocates unused unmetered bandwidth from unused or underused wires to other wires in the group. |
| `--bandwidth-unmetered` | BANDWIDTH_UNMETERED |  | The amount of unmetered bandwidth to assign to the wire group. |
| `--description` | DESCRIPTION |  | An optional, textual description for the wire group. |
| `--fault-response` | FAULT_RESPONSE |  | The fault response for the wire group. FAULT_RESPONSE must be one of: DISABLE_PORT Disable port NONE None |
| `--validate-only` |  |  | Validate the new configuration, but don't update it. |


**Examples:**
```bash
To disable a wire group, run:

    $ gcloud compute interconnects wire-groups update example-wg \
        --cross-site-network=example-csn --no-admin-enabled

To change a wire group's unmetered bandwidth, run:

    $ gcloud compute interconnects wire-groups update example-wg \
        --cross-site-network=example-csn --bandwidth-unmetered=5

To enable automatic failure detection for a wire group, run:

    $ gcloud compute interconnects wire-groups update example-wg \
        --cross-site-network=example-csn --fault-response=DISABLE_PORT

To enable bandwidth sharing for a wire group, run:

    $ gcloud compute interconnects wire-groups update example-wg \
        --cross-site-network=example-csn \
        --bandwidth-allocation=SHARED_WITH_WIRE_GROUP

To update a wire group's description, run:

    $ gcloud compute interconnects wire-groups update example-wg \
        --cross-site-network=example-csn --description="new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/interconnects/wire-groups/update)

---
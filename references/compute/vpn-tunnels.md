# gcloud compute vpn-tunnels

read and manipulate Compute Engine VPN tunnels

### `gcloud compute vpn-tunnels create`

Create a VPN tunnel

gcloud compute vpn-tunnels create is used to create a Classic VPN tunnel
between a target VPN gateway in Google Cloud Platform and a peer address;
or create Highly Available VPN tunnel between HA VPN gateway and another HA
VPN gateway, or Highly Available VPN tunnel between HA VPN gateway and an
external VPN gateway.

**Synopsis:**
```
gcloud compute vpn-tunnels create NAME --shared-secret=SHARED_SECRET
    (--peer-address=PEER_ADDRESS
      | --peer-external-gateway=PEER_EXTERNAL_GATEWAY
      | --peer-gcp-gateway=PEER_GCP_GATEWAY
      | --peer-gcp-gateway-region=PEER_GCP_GATEWAY_REGION)
    (--target-vpn-gateway=TARGET_VPN_GATEWAY
      | --target-vpn-gateway-region=TARGET_VPN_GATEWAY_REGION
      | --vpn-gateway=VPN_GATEWAY
      | --vpn-gateway-region=VPN_GATEWAY_REGION)
    [--description=DESCRIPTION] [--ike-version=IKE_VERSION]
    [--interface=INTERFACE] [--local-traffic-selector=CIDR,[CIDR,...]]
    [--peer-external-gateway-interface=PEER_EXTERNAL_GATEWAY_INTERFACE]
    [--phase1-dh=GROUPS,[GROUPS,...]]
    [--phase1-encryption=ALGORITHMS,[ALGORITHMS,...]]
    [--phase1-integrity=ALGORITHMS,[ALGORITHMS,...]]
    [--phase1-prf=PSEUDORANDOM FUNCTIONS,[...]]
    [--phase2-encryption=ALGORITHMS,[ALGORITHMS,...]]
    [--phase2-integrity=ALGORITHMS,[ALGORITHMS,...]]
    [--phase2-pfs=ALGORITHMS,[ALGORITHMS,...]] [--region=REGION]
    [--remote-traffic-selector=CIDR,[CIDR,...]] [--router=ROUTER]
    [--router-region=ROUTER_REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the VPN Tunnel to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--shared-secret` | SHARED_SECRET |  | Shared secret consisting of printable characters. Valid arguments match the regular expression [ -~]+ |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the VPN tunnel. |
| `--ike-version` | one of: 1, 2 |  | Internet Key Exchange protocol version number. Default is 2. IKE_VERSION must be one of: 1, 2. |
| `--interface` | one of: 0, 1 |  | Numeric interface ID of the VPN gateway with which this VPN tunnel is associated. This flag is required if the tunnel is being attached to a Highly Available VPN gateway. This option is only available for use with Highly Available VPN gateway and must be omitted if the tunnel is going to be connected to a Classic VPN gateway. INTERFACE must be one of: 0, 1. |
| `--local-traffic-selector` | CIDR,[CIDR,...] |  | Traffic selector is an agreement between IKE peers to permit traffic through a tunnel if the traffic matches a specified pair of local and remote addresses. --local-traffic-selector allows to configure the local addresses that are permitted. The value should be a comma separated list of CIDR formatted strings. Example: 192.168.0.0/16,10.0.0.0/24. Local traffic selector must be specified only for VPN tunnels that do not use dynamic routing with a Cloud Router. Omit this flag when creating a tunnel using dynamic routing, including a tunnel for a Highly Available VPN gateway. |
| `--peer-external-gateway-interface` | one of: 0, 1, 2, 3 |  | Interface ID of the external VPN gateway to which this VPN tunnel is connected to. This flag is required if the tunnel is being created from a Highly Available VPN gateway to an External Vpn Gateway. PEER_EXTERNAL_GATEWAY_INTERFACE must be one of: 0, 1, 2, 3. |
| `--phase1-dh` | GROUPS,[GROUPS,...] |  | Phase 1 Diffie-Hellman groups. |
| `--phase1-encryption` | ALGORITHMS,[ALGORITHMS,...] |  | Phase 1 encryption algorithms. |
| `--phase1-integrity` | ALGORITHMS,[ALGORITHMS,...] |  | Phase 1 integrity algorithms. |
| `--phase1-prf` | PSEUDORANDOM FUNCTIONS,[...] |  | Phase 1 pseudorandom functions. |
| `--phase2-encryption` | ALGORITHMS,[ALGORITHMS,...] |  | Phase 2 encryption algorithms. |
| `--phase2-integrity` | ALGORITHMS,[ALGORITHMS,...] |  | Phase 2 integrity algorithms. |
| `--phase2-pfs` | ALGORITHMS,[ALGORITHMS,...] |  | Phase 2 perfect forward secerecy algorithms. |
| `--region` | REGION |  | Region of the VPN Tunnel to create. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--remote-traffic-selector` | CIDR,[CIDR,...] |  | Traffic selector is an agreement between IKE peers to permit traffic through a tunnel if the traffic matches a specified pair of local and remote addresses. --remote-traffic-selector allows to configure the remote addresses that are permitted. The value should be a comma separated list of CIDR formatted strings. Example: 192.168.0.0/16,10.0.0.0/24. Remote traffic selector must be specified for VPN tunnels that do not use dynamic routing with a Cloud Router. Omit this flag when creating a tunnel using dynamic routing, including a tunnel for a Highly Available VPN gateway. |
| `--router` | ROUTER |  | Router to use for dynamic routing. |
| `--router-region` | ROUTER_REGION |  | Region of the router to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-tunnels/create)

---
### `gcloud compute vpn-tunnels delete`

Delete VPN tunnels

gcloud compute vpn-tunnels delete deletes one or more Compute Engine VPN
tunnels.

**Synopsis:**
```
gcloud compute vpn-tunnels delete NAME [NAME ...] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the VPN Tunnels to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the VPN Tunnels to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-tunnels/delete)

---
### `gcloud compute vpn-tunnels describe`

Describe a Compute Engine VPN tunnel

gcloud compute vpn-tunnels describe displays all data associated with a
Compute Engine VPN tunnel in a project.

**Synopsis:**
```
gcloud compute vpn-tunnels describe NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the VPN Tunnel to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the VPN Tunnel to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-tunnels/describe)

---
### `gcloud compute vpn-tunnels list`

List Google Compute Engine VPN tunnels

gcloud compute vpn-tunnels list displays all Google Compute Engine VPN
tunnels in a project.

By default, VPN tunnels from all regions are listed. The results can be
narrowed down using a filter: --filter="region:( REGION ... )".

**Synopsis:**
```
gcloud compute vpn-tunnels list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all VPN tunnels in a project in table form, run:

    $ gcloud compute vpn-tunnels list

To list the URIs of all VPN tunnels in a project, run:

    $ gcloud compute vpn-tunnels list --uri

To list all VPN tunnels in the us-central1 and europe-west1 regions, run:

    $ gcloud compute vpn-tunnels list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/vpn-tunnels/list)

---
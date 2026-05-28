# gcloud network-connectivity — Network Connectivity Center

## Overview

Network Connectivity Center (NCC) is an orchestration framework that simplifies connectivity among
spoke resources attached to a central hub, giving you a hub-and-spoke model for connecting VPC
networks, on-premises sites, and other clouds. Reach for `gcloud network-connectivity` to create and
manage hubs, attach spokes (VPC networks, HA VPN tunnels, VLAN attachments, Router appliances, and
producer VPCs), inspect route tables and PSC propagation, and manage related resources such as
internal ranges, policy-based routes, regional endpoints, and service connection policies.

## Quick reference — common workflows

First, enable the API (once per project):

```bash
gcloud services enable networkconnectivity.googleapis.com
```

**1. Create a hub and attach a VPC spoke**

```bash
# Create a hub with mesh topology (preset policy mode)
gcloud network-connectivity hubs create my-hub \
    --description="My NCC hub" \
    --policy-mode=preset \
    --preset-topology=mesh

# Verify the hub
gcloud network-connectivity hubs describe my-hub

# Attach a VPC spoke (VPC spokes are global)
gcloud network-connectivity spokes linked-vpc-network create my-vpc-spoke \
    --hub=my-hub \
    --global \
    --vpc-network=projects/my-project/global/networks/my-vpc

# List the spokes attached to the hub
gcloud network-connectivity hubs list-spokes my-hub
```

**2. Attach a hybrid (HA VPN) spoke with data transfer**

```bash
gcloud network-connectivity spokes linked-vpn-tunnels create my-vpn-spoke \
    --hub=my-hub \
    --region=us-central1 \
    --vpn-tunnels=projects/my-project/regions/us-central1/vpnTunnels/vpn-tunnel1,projects/my-project/regions/us-central1/vpnTunnels/vpn-tunnel2 \
    --site-to-site-data-transfer

gcloud network-connectivity spokes describe my-vpn-spoke --region=us-central1
```

**3. Attach a Router appliance spoke**

```bash
gcloud network-connectivity spokes linked-router-appliances create my-ra-spoke \
    --hub=my-hub \
    --region=us-central1 \
    --router-appliance=instance=projects/my-project/zones/us-central1-a/instances/vm1,ip=10.10.0.1 \
    --router-appliance=instance=projects/my-project/zones/us-central1-a/instances/vm2,ip=10.10.0.2 \
    --site-to-site-data-transfer

gcloud network-connectivity spokes list --region=us-central1
```

**4. Attach a VLAN attachment (Cloud Interconnect) spoke**

```bash
gcloud network-connectivity spokes linked-interconnect-attachments create my-vlan-spoke \
    --hub=my-hub \
    --region=us-central1 \
    --interconnect-attachments=projects/my-project/regions/us-central1/interconnectAttachments/ic1,projects/my-project/regions/us-central1/interconnectAttachments/ic2 \
    --site-to-site-data-transfer

gcloud network-connectivity spokes describe my-vlan-spoke --region=us-central1
```

**5. Manage spoke acceptance, status, and route tables**

```bash
# Accept a pending cross-project spoke into a preset-policy hub
gcloud network-connectivity hubs accept-spoke my-hub \
    --spoke="projects/spoke-project/locations/global/spokes/my-spoke"

# Query Private Service Connect propagation status, grouped
gcloud network-connectivity hubs query-status my-hub \
    --group-by="psc_propagation_status.source_spoke,psc_propagation_status.code"

# Inspect route tables and routes on the hub
gcloud network-connectivity hubs route-tables list --hub=my-hub
gcloud network-connectivity hubs route-tables routes list \
    --hub=my-hub --route_table=default
```

**6. Create a policy-based route**

```bash
gcloud network-connectivity policy-based-routes create my-pbr \
    --network=projects/my-project/global/networks/default \
    --next-hop-ilb-ip=10.0.0.1 \
    --source-range=192.168.1.0/24 \
    --ip-protocol=TCP \
    --priority=100

gcloud network-connectivity policy-based-routes list
gcloud network-connectivity policy-based-routes describe my-pbr
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `network-connectivity hubs` | [`hubs.md`](hubs.md) | 26 | manage NCC hubs (incl. `groups` and `route-tables` subgroups) |
| `network-connectivity internal-ranges` | [`internal-ranges.md`](internal-ranges.md) | 5 | manage internal ranges (reserve/allocate IP blocks) |
| `network-connectivity locations` | [`locations.md`](locations.md) | 2 | list/describe supported NCC locations |
| `network-connectivity multicloud-data-transfer-configs` | [`multicloud-data-transfer-configs.md`](multicloud-data-transfer-configs.md) | 10 | manage Multicloud Data Transfer Config resources (incl. `destinations`) |
| `network-connectivity multicloud-data-transfer-supported-services` | [`multicloud-data-transfer-supported-services.md`](multicloud-data-transfer-supported-services.md) | 2 | list/describe supported data-transfer services |
| `network-connectivity operations` | [`operations.md`](operations.md) | 2 | manage long-running NCC operations |
| `network-connectivity policy-based-routes` | [`policy-based-routes.md`](policy-based-routes.md) | 4 | manage policy-based routes |
| `network-connectivity regional-endpoints` | [`regional-endpoints.md`](regional-endpoints.md) | 4 | manage regional endpoints |
| `network-connectivity service-connection-policies` | [`service-connection-policies.md`](service-connection-policies.md) | 5 | manage service connection policies (PSC) |
| `network-connectivity spokes` | [`spokes.md`](spokes.md) | 13 | manage NCC spokes (VPC, VPN, interconnect, router-appliance, producer VPC) |

See [`index.md`](index.md) for a one-line index of all 73 GA commands.

## Common flags & tips

- **Location model.** Hubs are always global. Spokes are either global or regional depending on type:
  VPC and Producer-VPC spokes are global (use `--global`); VPN, VLAN-attachment, and Router-appliance
  spokes are regional (use `--region=REGION`). The top-level `spokes describe`/`delete` commands take
  `--global | --region`; `spokes list` with no location flag lists all regions.
- **Resource references.** `--hub`, `--vpc-network`, `--vpn-tunnels`, `--interconnect-attachments`,
  and `--router-appliance=instance=...` accept either bare IDs or fully qualified URIs; the linked
  resources must already exist. `--spoke` on hub accept/reject commands takes a spoke URI.
- **Data transfer.** Add `--site-to-site-data-transfer` on regional spokes (VPN, VLAN, router
  appliance) to enable site-to-site data transfer; this is only available in supported locations.
- **Async.** Most mutating commands accept `--async` to return immediately without waiting for the
  long-running operation; track it with `gcloud network-connectivity operations describe`.
- **Labels.** `create` commands take `--labels=KEY=VALUE,...`; `update` commands take
  `--update-labels`, `--remove-labels`, and `--clear-labels`.
- **Filtering / formatting.** `list` commands support standard `--filter`, `--sort-by`, `--limit`,
  and `--format`. For PSC status, `hubs query-status --group-by=...` aggregates by fields such as
  `psc_propagation_status.source_spoke` and `psc_propagation_status.code`. Example:
  `gcloud network-connectivity spokes list --format="table(name,spokeType,state)"`.
- **Route-table lists.** Use `--hub=-` and `--route_table=-` as wildcards to list across all hubs /
  route tables. Note the flag is spelled `--route_table` (underscore).

## beta / alpha

Both `gcloud beta network-connectivity` and `gcloud alpha network-connectivity` exist.

- **`transports`** — `gcloud beta network-connectivity transports` manages NCC transport resources.
  This group is **not present in the GA surface** (and is not documented here).
- **NCC Gateway spoke** support (a preview feature referenced in the hubs-and-spokes how-to) is
  surfaced through the beta/alpha tracks.

See the beta CLI reference: https://cloud.google.com/sdk/gcloud/reference/beta/network-connectivity

## Official documentation

- [Network Connectivity Center docs home](https://cloud.google.com/network-connectivity/docs/network-connectivity-center) — guides, concepts, quickstarts, and API reference.
- [NCC overview](https://cloud.google.com/network-connectivity/docs/network-connectivity-center/concepts/overview) — hub-and-spoke architecture, spoke types, and data-transfer concepts.
- [Working with hubs and spokes (how-to)](https://cloud.google.com/network-connectivity/docs/network-connectivity-center/how-to/working-with-hubs-spokes) — create, list, describe, update, and delete hubs and every spoke type.
- [Access control (IAM roles)](https://cloud.google.com/network-connectivity/docs/network-connectivity-center/concepts/access-control) — predefined NCC roles (`hubAdmin`, `hubViewer`, `spokeAdmin`, `groupAdmin`, etc.).
- [Network Connectivity suite home](https://cloud.google.com/network-connectivity/docs) — Cloud VPN, Cloud Interconnect, Cloud Router, and NCC.
- [gcloud CLI reference (GA)](https://cloud.google.com/sdk/gcloud/reference/network-connectivity) — full command-group reference for the GA surface.
- [gcloud CLI reference (beta)](https://cloud.google.com/sdk/gcloud/reference/beta/network-connectivity) — beta surface, including the `transports` group.

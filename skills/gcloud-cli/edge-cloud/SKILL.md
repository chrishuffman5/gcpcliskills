---
name: gcloud-edge-cloud
description: >-
  Google Distributed Cloud Edge via gcloud (`gcloud edge-cloud`). Manage edge-cloud resources — container, networking.
---

# gcloud edge-cloud — Google Distributed Cloud Edge

## Overview

`gcloud edge-cloud` manages **Google Distributed Cloud Edge (GDCE)** — Google-managed hardware
installed at customer or co-location edge sites that runs Kubernetes clusters and provides a
local network fabric. Reach for it to provision Edge Container clusters, node pools, and machines
(`edge-cloud container`), and to configure the Layer-2/3 edge network — networks, subnets,
routers, BGP peers, and interconnects (`edge-cloud networking`). Resources are scoped to a region
(`--location`) and, for networking, an edge zone (`--zone`).

## Quick reference — common workflows

### Enable the APIs

```bash
gcloud services enable edgecontainer.googleapis.com           # Edge Container API
gcloud services enable edgenetwork.googleapis.com             # Edge Network API
gcloud services enable gdchardwaremanagement.googleapis.com   # GDC Hardware Management API
```

### Discover regions, zones, and supported versions

```bash
# List regions (locations) where Edge Container clusters can be created
gcloud edge-cloud container regions list

# List zones where node pools can be created, then inspect one
gcloud edge-cloud container zones list
gcloud edge-cloud container zones describe us-central1-edge-operator-a

# Get supported cluster versions / release channels for a region
gcloud edge-cloud container get-server-config --location=us-central1
```

### Create a cluster, add a node pool, fetch credentials

```bash
# Create an HA (3-node) control plane cluster
gcloud edge-cloud container clusters create my-cluster \
    --location=us-central1 \
    --control-plane-node-count=3 \
    --control-plane-node-location=us-central1-edge-operator-a \
    --admin-users=user@example.com \
    --release-channel=REGULAR

# Add a worker node pool
gcloud edge-cloud container clusters node-pools create my-nodepool \
    --cluster=my-cluster \
    --location=us-central1 \
    --node-location=us-central1-edge-operator-a \
    --node-count=3

# Point kubectl at the cluster
gcloud edge-cloud container clusters get-credentials my-cluster \
    --location=us-central1
```

### Upgrade a cluster and wait on the operation

```bash
gcloud edge-cloud container get-server-config --location=us-central1

gcloud edge-cloud container clusters upgrade my-cluster \
    --location=us-central1 \
    --version=1.5.1 \
    --schedule=IMMEDIATELY

gcloud edge-cloud container operations wait \
    projects/my-project/locations/us-central1/operations/OPERATION_ID
```

### Set up edge networking (zone init → network → subnet → router → BGP)

```bash
# Initialize the edge zone's network fabric
gcloud edge-cloud networking zones init us-central1-edge-den1 \
    --location=us-central1

# Create a network and a subnet on it
gcloud edge-cloud networking networks create my-network \
    --location=us-central1 --zone=us-central1-edge-den1 --mtu=9000

gcloud edge-cloud networking subnets create my-subnet \
    --network=my-network --location=us-central1 \
    --zone=us-central1-edge-den1 --ipv4-range=192.168.1.1/24 --vlan-id=100

# Create a router, add a northbound interface, then a BGP peer
gcloud edge-cloud networking routers create my-router \
    --network=my-network --location=us-central1 \
    --zone=us-central1-edge-den1 --asn=65555

gcloud edge-cloud networking routers add-interface my-router \
    --interface-name=my-int-r1 \
    --interconnect-attachment=my-link-attachment \
    --ip-address=208.117.254.233 --ip-mask-length=31 \
    --location=us-central1 --zone=us-central1-edge-den1

gcloud edge-cloud networking routers add-bgp-peer my-router \
    --interface=my-int-r1 --peer-name=peer1 --peer-asn=33333 \
    --peer-ipv4-range=208.117.254.232/31 \
    --location=us-central1 --zone=us-central1-edge-den1
```

### Connect a cluster to a VPC over VPN

```bash
gcloud edge-cloud container vpn-connections create my-vpn \
    --location=us-central1 --cluster=my-cluster --vpc-network=my-vpc

gcloud edge-cloud container vpn-connections describe my-vpn \
    --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `edge-cloud container` | [`container.md`](container.md) | 25 | manage Edge Container resources (clusters, node pools, machines, VPN connections, regions/zones, operations) |
| `edge-cloud networking` | [`networking.md`](networking.md) | 28 | manage Distributed Cloud Edge Network resources (networks, subnets, routers, interconnects, zones, operations) |

See [`index.md`](index.md) for a one-line index of all 53 commands.

## Common flags & tips

- **Region vs. zone:** `--location` is the Google Cloud region (e.g. `us-central1`); it can be
  defaulted via the `edge_container/location` property. Networking resources additionally require
  `--zone`, the GDCE edge zone (e.g. `us-central1-edge-den1`). Container zones (e.g.
  `us-central1-edge-operator-a`) name where control-plane / node-pool nodes are placed.
- **HA control plane:** pass `--control-plane-node-count=3` to `clusters create` for a high-availability
  control plane; `1` creates a single-node control plane.
- **Release channels:** `--release-channel=REGULAR` enrolls a cluster in automatic GA upgrades; with
  REGULAR you cannot set a target `--version`. Use `NONE` to opt out and upgrade manually with
  `clusters upgrade --version=... --schedule=IMMEDIATELY`.
- **Async + operations:** most mutating commands accept `--async` to return immediately; poll the
  returned long-running operation with `gcloud edge-cloud container operations wait` (or
  `networking operations wait`).
- **List filtering:** `list` commands support `--filter`, `--sort-by`, `--limit`, and `--uri`, e.g.
  `gcloud edge-cloud container clusters list --location=us-central1 --filter="name~prod" --format="table(name,status)"`.
- **Machine filters:** restrict node placement with `--machine-filter` (AIP-160 syntax), e.g.
  `--machine-filter="name:edge-1"` or `--machine-filter="NOT name:edge-1"`.
- **MTU:** edge networks and dedicated interconnect attachments accept `--mtu` of `1500` or `9000`.

## beta / alpha

There is no `gcloud beta edge-cloud` track. The `gcloud alpha edge-cloud` surface exposes additional
subgroups not present in GA (for GDC Connected management): `api-keys`, `auth`, `identity-providers`,
`projects`, `service-accounts`, `services`, and a top-level `zones` group (distinct from
`container zones` / `networking zones`). The GA surface documented here covers only `container` and
`networking`.

## Official documentation

- [Google Distributed Cloud Edge docs home](https://docs.cloud.google.com/distributed-cloud/edge/latest/docs) — product overview, clusters, networking, and hardware management.
- [GDCE IAM permissions](https://docs.cloud.google.com/distributed-cloud/edge/latest/docs/permissions) — roles for Edge Container, Edge Network, and the GDC Hardware Management API, plus the API service names.
- [gcloud edge-cloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud) — full command reference; confirms the `container` and `networking` subgroups.
- [clusters create reference](https://cloud.google.com/sdk/gcloud/reference/edge-cloud/container/clusters/create) — cluster-creation flags, defaults, and examples.
- [alpha edge-cloud reference](https://cloud.google.com/sdk/gcloud/reference/alpha/edge-cloud) — alpha-only subgroups for GDC Connected.

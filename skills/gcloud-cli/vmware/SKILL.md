---
name: gcloud-vmware
description: >-
  Google Cloud VMware Engine via gcloud (`gcloud vmware`). Manage Google Cloud VMware Engine resources — announcements, datastores, dns-bind-permission, locations, network-peerings, network-policies, networks, node-types.
---

# gcloud vmware — Google Cloud VMware Engine

## Overview

`gcloud vmware` manages **Google Cloud VMware Engine private clouds, clusters, networks** — a fully managed service that runs the VMware stack (vSphere, vSAN, NSX-T, HCX) on dedicated nodes inside Google Cloud. Reach for it to provision VMware Engine networks, stand up private clouds and their management/workload clusters, control internet and external-IP access, peer with consumer VPCs, and attach datastores. The surface is fully GA (87 commands across 11 subgroups). Most create/delete/update operations are long-running; they default to `--async` (use `--no-async` to block until completion).

## Quick reference — common workflows

### 1. Enable the API and check available node types

```bash
gcloud services enable vmwareengine.googleapis.com

# List node types available in a zone
gcloud vmware node-types list --location=us-west2-a --project=my-project

# Inspect a node type (the availableCustomCoreCounts field shows core options)
gcloud vmware node-types describe standard-72 --location=us-west2-a --project=my-project
```

### 2. Create a VMware Engine network and private cloud

```bash
# Step 1: create a STANDARD (global) VMware Engine network
gcloud vmware networks create my-network --type=STANDARD \
    --location=global --project=my-project

# Step 2: create a private cloud with a 3-node management cluster
#   (long-running; --async returns immediately)
gcloud vmware private-clouds create my-private-cloud \
    --location=us-west2-a --project=my-project \
    --cluster=my-management-cluster \
    --node-type-config=type=standard-72,count=3 \
    --management-range=192.168.0.0/24 \
    --vmware-engine-network=my-network \
    --async

# Step 3: monitor progress until READY
gcloud vmware private-clouds list --location=us-west2-a
gcloud vmware private-clouds describe my-private-cloud --location=us-west2-a
```

### 3. Add and resize a workload cluster

```bash
# List existing clusters in the private cloud
gcloud vmware private-clouds clusters list \
    --private-cloud=my-private-cloud --location=us-west2-a

# Create a new workload cluster
gcloud vmware private-clouds clusters create my-workload-cluster \
    --location=us-west2-a --project=my-project \
    --private-cloud=my-private-cloud \
    --node-type-config=type=standard-72,count=3 \
    --async

# Scale the cluster out to 5 nodes
gcloud vmware private-clouds clusters update my-workload-cluster \
    --location=us-west2-a --project=my-project \
    --private-cloud=my-private-cloud \
    --update-nodes-config=type=standard-72,count=5
```

### 4. Create a network policy (enable internet / external-IP access)

```bash
# One network policy applies per VMware Engine network per region;
# --edge-services-cidr must be an RFC 1918 /26 block
gcloud vmware network-policies create my-network-policy \
    --location=us-west2 --project=my-project \
    --vmware-engine-network=my-network \
    --edge-services-cidr=192.168.0.0/26 \
    --internet-access \
    --external-ip-access

gcloud vmware network-policies describe my-network-policy \
    --location=us-west2 --project=my-project
```

### 5. Peer a VMware Engine network with a consumer VPC

```bash
# Peer with a STANDARD VPC network in another project
gcloud vmware network-peerings create my-peering \
    --vmware-engine-network=my-network \
    --peer-network=my-vpc-network \
    --peer-network-type=STANDARD \
    --peer-project=my-project

# Verify imported routes
gcloud vmware network-peerings routes list \
    --network-peering=my-peering \
    --filter="direction=INCOMING"
```

### 6. Soft-delete, recover, or permanently delete a private cloud

```bash
# Mark for deletion (default 3-hour delay; --delay-hours=0 starts immediately)
gcloud vmware private-clouds delete my-private-cloud \
    --location=us-west2-a --project=my-project

# Cancel the deletion within the delay window
gcloud vmware private-clouds undelete my-private-cloud \
    --location=us-west2-a --project=my-project

# Permanently delete a cloud already in soft-deleted state
gcloud vmware private-clouds delete-now my-private-cloud \
    --location=us-west2-a --project=my-project
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `vmware announcements` | [`announcements.md`](announcements.md) | 1 | list announcements in Google Cloud VMware Engine |
| `vmware datastores` | [`datastores.md`](datastores.md) | 5 | manage VMware Engine datastores |
| `vmware dns-bind-permission` | [`dns-bind-permission.md`](dns-bind-permission.md) | 3 | manage DNS binding permission |
| `vmware locations` | [`locations.md`](locations.md) | 1 | list VMware Engine locations |
| `vmware network-peerings` | [`network-peerings.md`](network-peerings.md) | 6 | manage VPC peering (plus `routes` subgroup) |
| `vmware network-policies` | [`network-policies.md`](network-policies.md) | 10 | manage network policies (plus `external-access-rules`) |
| `vmware networks` | [`networks.md`](networks.md) | 5 | manage VMware Engine networks |
| `vmware node-types` | [`node-types.md`](node-types.md) | 2 | show supported node types |
| `vmware operations` | [`operations.md`](operations.md) | 2 | list and describe long-running operations |
| `vmware private-clouds` | [`private-clouds.md`](private-clouds.md) | 46 | manage private clouds, `clusters`, `nodes`, `dns-forwarding`, `external-addresses` |
| `vmware private-connections` | [`private-connections.md`](private-connections.md) | 6 | manage Private Connections to VPC networks |

See [`index.md`](index.md) for a one-line index of all 87 commands.

## Common flags & tips

- **Resource scoping** — most commands take `--location` plus `--project` (or fall back to `core/project`). The expected location kind varies by resource:
  - *Zonal* (`compute/zone`): private clouds, clusters, nodes, node types, datastores, external addresses — e.g. `us-west2-a`.
  - *Regional* (`compute/region`): network policies, external-access-rules, private connections — e.g. `us-west2`.
  - *Global*: STANDARD VMware Engine networks and network peerings — `--location=global` (the default). LEGACY networks are regional.
- **`--async` / `--no-async`** — async is the default for create/delete/update. Add `--no-async` to wait, or track with `gcloud vmware operations describe OPERATION --location=...`.
- **`--node-type-config`** — `type=NODE_TYPE,count=N[,custom-core-count=N]`; e.g. `--node-type-config=type=standard-72,count=3`. On `clusters update`, prefer `--update-nodes-config` / `--remove-nodes-config` (`--node-type-config` is deprecated there).
- **CIDR constraints** — `--management-range` accepts /24–/20 and is immutable after creation; `--edge-services-cidr` on a network policy must be an RFC 1918 /26.
- **List filters & formatting** — list commands accept `--filter`, `--sort-by`, `--limit`. Useful examples:
  ```bash
  gcloud vmware network-policies list --location=- --project=my-project  # all regions
  gcloud vmware network-peerings list --filter="createTime > 2021-04-12T00:00:00.00Z" --sort-by=createTime
  gcloud vmware private-clouds clusters list --private-cloud=my-private-cloud --location=us-west2-a \
      --format="table(name.segment(-1), state, nodeTypeConfigs)"
  ```
- **Autoscaling** — `clusters update` supports `--autoscaling-min-cluster-node-count`, `--autoscaling-max-cluster-node-count`, and `--update-autoscaling-policy=...` to enable cluster autoscaling.
- **Datastores** — `gcloud vmware datastores create` requires exactly one backend: `--filestore`, `--netapp`, or `--third-party-nfs-*`; mount with `gcloud vmware private-clouds clusters mount-datastore`.

## beta / alpha

No documented beta-only or alpha-only commands. The `gcloud vmware` surface is fully GA, including autoscaling-policy management on `clusters update`. Some capabilities may also be available under `gcloud beta vmware` / `gcloud alpha vmware` (not documented here).

## Official documentation

- [Google Cloud VMware Engine documentation](https://cloud.google.com/vmware-engine/docs) — product docs home: overview, quickstarts, networking, pricing.
- [gcloud vmware CLI reference](https://cloud.google.com/sdk/gcloud/reference/vmware) — full reference for all GA `vmware` commands.
- [Quickstart prerequisites](https://cloud.google.com/vmware-engine/docs/quickstart-prerequisites) — API enablement, billing, and IAM roles needed before creating resources.
- [Networking requirements](https://cloud.google.com/vmware-engine/docs/quickstart-networking-requirements) — management CIDR rules (/24–/20) and prohibited overlaps.
- [IAM roles](https://cloud.google.com/vmware-engine/docs/iam) — VMware Engine Service Admin and Service Viewer roles.
- [Private cloud overview](https://cloud.google.com/vmware-engine/docs/private-cloud/private-cloud-overview) — management cluster, vSphere, vSAN, and NSX-T concepts.
- [Configuring VPC peering](https://cloud.google.com/vmware-engine/docs/networking/configuring-vpc-peering) — peer VMware Engine networks with VPC networks.

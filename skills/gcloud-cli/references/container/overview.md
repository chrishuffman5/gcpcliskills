# gcloud container — Google Kubernetes Engine (GKE)

## Overview

`gcloud container` manages Google Kubernetes Engine (GKE) — Google Cloud's managed Kubernetes service — and related container tooling. Use it to create and tear down clusters, manage node pools, fetch `kubectl` credentials, upgrade Kubernetes versions, and administer fleets, Anthos/attached clusters, and Container Registry images. GKE runs in two modes: **Autopilot** (Google manages nodes, scaling, and security; created with `clusters create-auto`) and **Standard** (you manage node pools and machine types; created with `clusters create`).

Reach for this group whenever you provision GKE infrastructure or wire `kubectl` up to a cluster. Day-to-day workload operations (deployments, pods, services) are done with `kubectl` after running `clusters get-credentials`.

## Quick reference — common workflows

### Enable the API
```bash
gcloud services enable container.googleapis.com
```

### Create a Standard cluster and connect kubectl
```bash
# Check the default and available Kubernetes versions for a location
gcloud container get-server-config --location=us-central1

# Create a zonal Standard cluster (defaults to 3 nodes)
gcloud container clusters create my-cluster \
    --location=us-central1-a \
    --release-channel=regular \
    --num-nodes=3 \
    --machine-type=e2-standard-4 \
    --disk-type=pd-balanced \
    --disk-size=100

# Write credentials to ~/.kube/config so kubectl targets this cluster
gcloud container clusters get-credentials my-cluster \
    --location=us-central1-a
```

### Create an Autopilot cluster
```bash
# Autopilot manages nodes automatically — use create-auto, not create
gcloud container clusters create-auto my-autopilot-cluster \
    --location=us-central1 \
    --release-channel=regular

gcloud container clusters get-credentials my-autopilot-cluster \
    --location=us-central1
```

### List and inspect clusters
```bash
gcloud container clusters list

gcloud container clusters describe my-cluster \
    --location=us-central1-a

# Auto-upgrade status, upgrade targets, end-of-support timelines
gcloud container clusters get-upgrade-info my-cluster \
    --location=us-central1-a
```

### Manage node pools (Standard clusters)
```bash
# Add a spot-VM node pool with autoscaling and autorepair
gcloud container node-pools create high-mem-pool \
    --cluster=my-cluster \
    --location=us-central1-a \
    --machine-type=n2-highmem-4 \
    --num-nodes=2 \
    --spot \
    --enable-autoscaling \
    --min-nodes=1 \
    --max-nodes=10 \
    --enable-autorepair

gcloud container node-pools list \
    --cluster=my-cluster \
    --location=us-central1-a

# Manually resize a specific node pool
gcloud container clusters resize my-cluster \
    --node-pool=high-mem-pool \
    --num-nodes=5 \
    --location=us-central1-a

gcloud container node-pools delete high-mem-pool \
    --cluster=my-cluster \
    --location=us-central1-a
```

### Upgrade a cluster
```bash
# Upgrade the control plane (master) to the default version
gcloud container clusters upgrade my-cluster \
    --master \
    --location=us-central1-a

# Upgrade a node pool to a specific version (node pools can't upgrade with the master)
gcloud container clusters upgrade my-cluster \
    --node-pool=default-pool \
    --cluster-version=1.30.5-gke.1014001 \
    --location=us-central1-a

# Roll back a canceled or failed node-pool upgrade
gcloud container node-pools rollback default-pool \
    --cluster=my-cluster \
    --location=us-central1-a
```

### Update cluster settings (autoscaling, monitoring)
```bash
# Enable node autoscaling on the default node pool
gcloud container clusters update my-cluster \
    --enable-autoscaling \
    --min-nodes=1 \
    --max-nodes=10 \
    --location=us-central1-a

# Switch the autoscaling profile and enable managed Prometheus
gcloud container clusters update my-cluster \
    --autoscaling-profile=optimize-utilization \
    --enable-managed-prometheus \
    --location=us-central1-a
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `container ai` | [`ai.md`](ai.md) | 9 | manage AI related workloads for GKE |
| `container attached` | [`attached.md`](attached.md) | 12 | manage Attached clusters for running containers |
| `container aws` | [`aws.md`](aws.md) | 17 | deploy and manage clusters of machines on AWS for running containers |
| `container azure` | [`azure.md`](azure.md) | 21 | deploy and manage clusters of machines on Azure for running containers |
| `container bare-metal` | [`bare-metal.md`](bare-metal.md) | 23 | deploy and manage Anthos clusters on bare metal for running containers |
| `container binauthz` | [`binauthz.md`](binauthz.md) | 21 | manage attestations for Binary Authorization on Google Cloud Platform |
| `container clusters` | [`clusters.md`](clusters.md) | 11 | deploy and teardown GKE clusters (create, create-auto, upgrade, resize, get-credentials) |
| `container fleet` | [`fleet.md`](fleet.md) | 112 | centrally manage features and services on all your Kubernetes clusters with fleet |
| `container hub` | [`hub.md`](hub.md) | 112 | alias for `container fleet` — centrally manage fleet features and services |
| `container images` | [`images.md`](images.md) | 7 | list and manipulate Google Container Registry images |
| `container node-pools` | [`node-pools.md`](node-pools.md) | 8 | create, update, and delete GKE node pools |
| `container operations` | [`operations.md`](operations.md) | 4 | get and list operations for GKE clusters |
| `container subnets` | [`subnets.md`](subnets.md) | 1 | manage subnets to be used by GKE clusters |
| `container vmware` | [`vmware.md`](vmware.md) | 22 | deploy and manage Anthos clusters on VMware for running containers |

Top-level command: `gcloud container get-server-config` (see [`_commands.md`](_commands.md)) returns the default and valid Kubernetes/image versions for a location. The full one-line index of all 381 GA commands is in [`index.md`](index.md).

## Common flags & tips

- **Location is required for most cluster/node-pool commands.** Prefer `--location=LOCATION` (accepts either a zone like `us-central1-a` or a region like `us-central1`) over the older `--zone`/`--region` flags. A zonal value creates a single-zone cluster; a regional value creates a regional cluster with the control plane replicated across zones.
- **Autopilot vs Standard:** `clusters create-auto` produces an Autopilot cluster (no node-pool management, no `--num-nodes`/`--machine-type`); `clusters create` produces a Standard cluster where you size node pools yourself. `--release-channel` (`rapid`, `regular`, `stable`, `extended`) controls automatic version management on both.
- **get-credentials is the bridge to kubectl.** It writes endpoint and auth data to `~/.kube/config` (override with `$KUBECONFIG`). Use `--internal-ip` or `--dns-endpoint` for private/DNS-based control-plane access.
- **Upgrades are split:** `--master` upgrades the control plane; `--node-pool=NAME` upgrades nodes. They cannot be upgraded in the same command. Omitting `--cluster-version` defaults node pools to the current master version and the master to the channel default.
- **Node pool naming:** node-pool commands take the pool name positionally and require `--cluster=CLUSTER`. Resizing is done via `clusters resize --node-pool=...`, not a node-pool subcommand.
- **Useful formatting/filtering:**
  ```bash
  # Tabular view of clusters with version and node count
  gcloud container clusters list \
      --format="table(name,location,currentMasterVersion,currentNodeCount,status)"

  # Only RUNNING clusters
  gcloud container clusters list --filter="status=RUNNING"

  # Just the endpoint of one cluster
  gcloud container clusters describe my-cluster \
      --location=us-central1-a --format="value(endpoint)"
  ```
- `container hub` is an alias for `container fleet`; both expose the same 112 commands.

## beta / alpha

- **`gcloud beta container clusters`** mirrors the GA surface but exposes additional/earlier flags. It adds the two-step staged control-plane upgrade, whose completion command is **beta-only** (not present in GA `container clusters`):
  ```bash
  gcloud beta container clusters upgrade CLUSTER_NAME \
      --master --location=LOCATION \
      --cluster-version=VERSION \
      --control-plane-soak-duration=SOAK_DURATION
  gcloud beta container clusters complete-control-plane-upgrade CLUSTER_NAME \
      --location=LOCATION
  ```
- **`gcloud alpha container clusters`** offers experimental features (e.g. `create-auto`, `check-autopilot-compatibility`, `complete-control-plane-upgrade`) at the alpha tier; alpha clusters are not covered by the GKE SLA and should not run production workloads.
- `gcloud container ai profiles ...` (GA) manages AI/ML workload profiles — accelerator profiles, model servers, and manifests — for GKE.

## Official documentation

- [GKE product documentation home](https://docs.cloud.google.com/kubernetes-engine/docs) — entry point for all GKE concepts, how-tos, and reference material.
- [Create Standard zonal/regional clusters](https://docs.cloud.google.com/kubernetes-engine/docs/how-to/creating-a-zonal-cluster) — how-to for `clusters create`.
- [Create Autopilot clusters](https://docs.cloud.google.com/kubernetes-engine/docs/how-to/creating-an-autopilot-cluster) — how-to for `clusters create-auto`.
- [Autopilot overview](https://docs.cloud.google.com/kubernetes-engine/docs/concepts/autopilot-overview) — Autopilot mode and comparison with Standard.
- [Cluster architecture](https://docs.cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture) — control plane, node pools, and mode differences.
- [Node pools how-to](https://docs.cloud.google.com/kubernetes-engine/docs/how-to/node-pools) — create, describe, resize, update, and delete node pools.
- [Upgrading a cluster](https://docs.cloud.google.com/kubernetes-engine/docs/how-to/upgrading-a-cluster) — control plane and node-pool version upgrades.
- [GKE IAM](https://docs.cloud.google.com/kubernetes-engine/docs/how-to/iam) — roles required for cluster management (e.g. `roles/container.admin`, `roles/container.clusterAdmin`).
- [gcloud container reference](https://docs.cloud.google.com/sdk/gcloud/reference/container) — full command/flag reference for this group.

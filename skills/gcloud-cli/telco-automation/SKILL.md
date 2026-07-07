---
name: gcloud-telco-automation
description: >-
  Telecom Network Automation via gcloud (`gcloud telco-automation`). Manage Telco Automation resources — operations, orchestration-cluster.
---

# gcloud telco-automation — Telecom Network Automation

## Overview

Telecom Network Automation is Google Cloud's managed implementation of [Nephio](https://nephio.org/),
an open-source, Kubernetes-based framework from Google and the Linux Foundation for carrier-grade,
intent-driven automation of multi-cloud, multi-vendor telecom network functions. The
`gcloud telco-automation` command group manages the foundational **orchestration clusters** (the
GKE-backed control-plane clusters that run Nephio operators and host blueprints/deployments) and the
long-running **operations** they produce. Reach for it when you are standing up or tearing down the
orchestration infrastructure that drives declarative telecom network automation.

## Quick reference — common workflows

### 1. Enable APIs and create an orchestration cluster

```bash
# Compute API is needed for the GKE-based orchestration cluster; plus the product API
gcloud services enable compute.googleapis.com telcoautomation.googleapis.com

# Create a cluster (waits for the operation by default)
gcloud telco-automation orchestration-cluster create my-cluster \
    --location=us-central1
```

### 2. Create asynchronously and track the operation

```bash
# Return immediately instead of blocking on the long-running create
gcloud telco-automation orchestration-cluster create my-cluster \
    --location=us-central1 \
    --async

# Poll the returned operation until it finishes
gcloud telco-automation operations wait OPERATION_ID \
    --location=us-central1
```

### 3. Create a cluster on a specific VPC with custom CIDR ranges

```bash
gcloud telco-automation orchestration-cluster create my-cluster \
    --location=us-central1 \
    --network=my-vpc \
    --subnet=my-subnet \
    --master-ipv4-cidr-block=172.16.0.0/28 \
    --cluster-cidr-block=10.96.0.0/14 \
    --services-cidr-block=10.100.0.0/20 \
    --cidr-blocks=cidr-block=192.168.1.0/24,display-name=corp-access
```

### 4. List and inspect orchestration clusters

```bash
# List all clusters in a region
gcloud telco-automation orchestration-cluster list \
    --location=us-central1

# Describe one cluster
gcloud telco-automation orchestration-cluster describe my-cluster \
    --location=us-central1
```

### 5. Delete a cluster and watch the operation

```bash
# Delete asynchronously
gcloud telco-automation orchestration-cluster delete my-cluster \
    --location=us-central1 \
    --async

# Inspect the operation's current status
gcloud telco-automation operations describe OPERATION_ID \
    --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `telco-automation operations` | [`operations.md`](operations.md) | 2 | Work with telco automation long-running operations (`describe`, `wait`). |
| `telco-automation orchestration-cluster` | [`orchestration-cluster.md`](orchestration-cluster.md) | 4 | Manage orchestration cluster instances (`create`, `delete`, `describe`, `list`). |

See [`index.md`](index.md) for a one-line index of all 6 commands.

## Common flags & tips

- **`--location` is required everywhere.** Every command in this group is regional; pass a region
  such as `--location=us-central1`. Both resources also accept a fully qualified resource name in
  place of the positional ID + `--location`.
- **Long-running by design.** `orchestration-cluster create` and `delete` are asynchronous server
  operations. They wait for completion by default; add `--async` to return immediately and then track
  the returned operation with `operations wait OPERATION_ID --location=...` (block) or
  `operations describe OPERATION_ID --location=...` (status snapshot).
- **Cluster creation can be slow.** Standing up the GKE-backed cluster takes time, so for synchronous
  runs raise the client timeout: `gcloud config set http_timeout 3600`.
- **Networking on `create`.** Use `--network`/`--subnet` to place the cluster in an existing VPC (the
  VPC is created if it doesn't exist). Control IP allocation with `--master-ipv4-cidr-block` (a `/28`
  for the control plane), `--cluster-cidr-block` and `--services-cidr-block` (or the named-range
  equivalents `--cluster-named-range` / `--services-named-range`). Add master-authorized networks via
  `--cidr-blocks=cidr-block=CIDR,display-name=NAME`. Use `--full-management-config` only when the
  supplied management arguments describe a full (Autopilot) cluster.
- **Filtering and formatting `list`.** `orchestration-cluster list` supports the standard
  `--filter`, `--limit`, `--sort-by`, `--page-size`, and `--uri` flags. Examples:

  ```bash
  # Only show clusters in the ACTIVE state, newest first
  gcloud telco-automation orchestration-cluster list \
      --location=us-central1 \
      --filter="state=ACTIVE" --sort-by="~createTime"

  # Project just the name and state as a table
  gcloud telco-automation orchestration-cluster list \
      --location=us-central1 \
      --format="table(name, state)"
  ```

## beta / alpha

- `gcloud alpha telco-automation` exists and mirrors the GA surface — the same `operations` and
  `orchestration-cluster` subgroups with the same commands and flags. Alpha commands "might change
  without notice," so prefer GA for production scripts.
- There is no distinct documented `gcloud beta telco-automation` command surface beyond GA.
- The product's predefined IAM roles (`roles/telcoautomation.admin`, `.editor`, `.viewer`,
  `.blueprintDesigner`) are still labeled **Beta** in the IAM reference, reflecting a maturing product.

## Official documentation

- [Telecom Network Automation docs home](https://cloud.google.com/telecom-network-automation/docs) — product guides, reference, and resources.
- [Overview](https://cloud.google.com/telecom-network-automation/docs/overview) — product concepts, Nephio architecture, and how it works.
- [Set up a project](https://cloud.google.com/telecom-network-automation/docs/set-up-project) — quickstart: enabling APIs, assigning IAM roles, and configuring gcloud.
- [Predefined IAM roles](https://cloud.google.com/iam/docs/roles-permissions/telcoautomation) — roles and permissions for the Telecom Network Automation API.
- [gcloud telco-automation reference](https://cloud.google.com/sdk/gcloud/reference/telco-automation) — full CLI reference for this command group.

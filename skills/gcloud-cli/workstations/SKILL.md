---
name: gcloud-workstations
description: >-
  Cloud Workstations via gcloud (`gcloud workstations`). Manage Cloud Workstations resources — clusters, configs.
---

# gcloud workstations — Cloud Workstations

## Overview

Cloud Workstations provides managed, preconfigured, and secure cloud development environments on Google Cloud. Administrators define reusable workstation *configurations* (machine type, container image, persistent disk, timeouts, security options) that developers launch on demand as ephemeral Compute Engine-backed VMs. Reach for `gcloud workstations` to provision the three-tier hierarchy — **cluster** (regional VPC/network boundary) → **config** (template) → **workstation** (running instance) — and to start, connect to (SSH/TCP tunnel), stop, and manage access to those instances.

## Quick reference — common workflows

### Enable the API and set default properties

```bash
gcloud services enable workstations.googleapis.com

# Optional: avoid repeating --region/--cluster/--config on every command
gcloud config set workstations/region us-central1
gcloud config set workstations/cluster my-cluster
gcloud config set workstations/config my-config
```

### Create a cluster (public or private/VPC-isolated)

```bash
# Public cluster
gcloud workstations clusters create my-cluster --region=us-central1

# Private cluster (internal IP only) wired to a VPC network/subnetwork
gcloud workstations clusters create my-private-cluster \
    --region=us-central1 \
    --enable-private-endpoint \
    --network='projects/my-project/global/networks/my-network' \
    --subnetwork='projects/my-project/regions/us-central1/subnetworks/my-subnet'

gcloud workstations clusters describe my-cluster --region=us-central1
gcloud workstations clusters list --region=us-central1
```

### Create a workstation configuration

```bash
# Basic config (defaults: codeoss image, e2-standard-4)
gcloud workstations configs create my-config \
    --cluster=my-cluster --region=us-central1

# IntelliJ on a larger machine, Shielded VM, 4 h idle timeout
gcloud workstations configs create my-intellij-config \
    --cluster=my-cluster --region=us-central1 \
    --machine-type=e2-standard-8 \
    --container-predefined-image=intellij \
    --idle-timeout=14400 \
    --shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring

# Custom container image with persistent PD-SSD home storage
gcloud workstations configs create my-custom-config \
    --cluster=my-cluster --region=us-central1 \
    --container-custom-image=us-central1-docker.pkg.dev/my-project/my-repo/my-image:latest \
    --pd-disk-type=pd-ssd --pd-disk-size=50

gcloud workstations configs list --cluster=my-cluster --region=us-central1
```

### Create, start, and connect to a workstation

```bash
gcloud workstations create my-workstation \
    --cluster=my-cluster --config=my-config --region=us-central1

gcloud workstations start my-workstation \
    --cluster=my-cluster --config=my-config --region=us-central1

# SSH in (run a one-off command and exit)
gcloud workstations ssh my-workstation \
    --cluster=my-cluster --config=my-config --region=us-central1 \
    --user=user --port=22 --command="ps -ejH"

# Forward a local port to a port on the workstation
gcloud workstations start-tcp-tunnel my-workstation 8080 \
    --cluster=my-cluster --config=my-config --region=us-central1 \
    --local-host-port=localhost:8080

gcloud workstations list --region=us-central1
gcloud workstations list-usable --region=us-central1
```

### Update, stop, and tear down (children first)

```bash
# Update a config in place
gcloud workstations configs update my-config \
    --cluster=my-cluster --region=us-central1 \
    --idle-timeout=3600 --machine-type=e2-standard-8

gcloud workstations stop my-workstation \
    --cluster=my-cluster --config=my-config --region=us-central1

# Delete in reverse order: workstation → config → cluster
gcloud workstations delete my-workstation \
    --cluster=my-cluster --config=my-config --region=us-central1
gcloud workstations configs delete my-config \
    --cluster=my-cluster --region=us-central1
gcloud workstations clusters delete my-cluster --region=us-central1
```

### Grant access via IAM (config- or workstation-scoped)

```bash
# Edit then apply the IAM policy on a config (add roles/workstations.user)
gcloud workstations configs get-iam-policy my-config \
    --cluster=my-cluster --region=us-central1 --format=json > policy.json
gcloud workstations configs set-iam-policy my-config \
    --cluster=my-cluster --region=us-central1 policy.json

# Same pattern for an individual workstation
gcloud workstations set-iam-policy my-workstation \
    --cluster=my-cluster --config=my-config --region=us-central1 policy.json
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `workstations` (top level) | [`_commands.md`](_commands.md) | 11 | create/delete/describe/start/stop workstations, SSH, TCP tunnel, IAM |
| `workstations clusters` | [`clusters.md`](clusters.md) | 4 | manage Cloud Workstations cluster resources |
| `workstations configs` | [`configs.md`](configs.md) | 7 | manage Cloud Workstations configuration resources |

See [`index.md`](index.md) for a one-line index of all 22 GA commands.

## Common flags & tips

- **Resource hierarchy is always explicit.** A workstation is identified by `--cluster`, `--config`, and `--region`; a config by `--cluster` and `--region`; a cluster by `--region`. Set them once with `gcloud config set workstations/region|cluster|config ...` to avoid repetition.
- **Config defaults:** `--machine-type` defaults to `e2-standard-4`, the image to `--container-predefined-image=codeoss`, `--idle-timeout`/`--running-timeout` to `7200` seconds (0 = never time out), and `--boot-disk-size` to `50` GB.
- **Image selection is mutually exclusive:** use either `--container-predefined-image` (e.g. `codeoss`, `intellij`) or `--container-custom-image=<Artifact Registry path>`, not both.
- **Persistent home disk** is configured at the config level with `--pd-disk-type` (default `pd-standard`) and `--pd-disk-size` (default `200`); `--no-persistent-storage` opts out.
- **Security hardening:** `--shielded-secure-boot`, `--shielded-vtpm`, `--shielded-integrity-monitoring`, `--enable-confidential-compute`, `--disable-public-ip-addresses`. On `configs update`, negate booleans with the `--no-` prefix (e.g. `--no-shielded-secure-boot`).
- **SSH access** must be enabled on the config (`--enable-ssh-to-vm`; the older `--disable-ssh-to-vm` is deprecated) before `gcloud workstations ssh` will connect.
- **Long-running ops:** add `--async` to clusters/configs/workstations create, delete, start, and stop to return immediately instead of waiting.
- **Filtering / formatting:** list and get-iam-policy commands support `--filter`, `--sort-by`, `--limit`, `--page-size`. Examples:
  - `gcloud workstations list --region=us-central1 --filter="state=STATE_RUNNING"`
  - `gcloud workstations clusters list --region=us-central1 --format="table(name, network, subnetwork)"`

## beta / alpha

`gcloud beta workstations` and `gcloud alpha workstations` exist with the same command surface as GA (identical `clusters` and `configs` subgroups and top-level commands). Beta/alpha commands carry the "might change without notice" caveat and may expose unreleased config flags first; use GA for stable automation. No GA-blocking capability was identified as beta/alpha-only.

## Official documentation

- [Cloud Workstations documentation](https://cloud.google.com/workstations/docs) — product docs home: guides, concepts, API reference.
- [Architecture overview](https://cloud.google.com/workstations/docs/overview) — clusters, configs, workstations, and IAM model.
- [Quickstart](https://cloud.google.com/workstations/docs/quickstart) — create a cluster, config, and workstation end to end.
- [Access control (IAM)](https://cloud.google.com/workstations/docs/access-control) — roles and permissions reference.
- [gcloud workstations CLI reference](https://cloud.google.com/sdk/gcloud/reference/workstations) — all GA commands and flags.

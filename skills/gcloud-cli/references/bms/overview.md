# gcloud bms — Bare Metal Solution

## Overview
`gcloud bms` manages Bare Metal Solution (BMS) resources — dedicated physical
servers, storage volumes and LUNs, networks, and NFS shares provisioned in
Google Cloud colocation facilities for specialized workloads such as Oracle
databases that cannot run on standard VMs. Reach for it to inventory and
inspect provisioned hardware, power-cycle instances, manage boot-volume
snapshots, and configure storage and network access. BMS hardware itself is
provisioned by Google (often allowlist-only as of 2025); the CLI operates on
already-provisioned environments rather than creating servers from scratch.

## Quick reference — common workflows

Enable the API once per project:

```bash
gcloud services enable baremetalsolution.googleapis.com
```

### 1. Inventory resources across a project

```bash
# All instances in the project (omit --region for all regions)
gcloud bms instances list --project=my-project

# Instances in one region, plus volumes and networks
gcloud bms instances list --region=us-central1 --project=my-project
gcloud bms volumes list --region=us-central1 --project=my-project
gcloud bms networks list --region=us-central1 --project=my-project
```

### 2. Inspect a specific instance, volume, and its LUNs

```bash
gcloud bms instances describe my-instance \
    --region=us-central1 --project=my-project

gcloud bms volumes describe my-volume \
    --region=us-central1 --project=my-project

gcloud bms volumes luns list \
    --volume=my-volume --region=us-central1 --project=my-project
```

### 3. Power-cycle an instance and track the operation

```bash
# Start / stop / hard reset (reset does NOT do a clean OS shutdown)
gcloud bms instances start my-instance --region=us-central1
gcloud bms instances stop  my-instance --region=us-central1
gcloud bms instances reset my-instance --region=us-central1

# Run a power op asynchronously, then poll the returned operation
gcloud bms instances reset my-instance --region=us-central1 --async
gcloud bms operations wait my-operation --project=my-project
```

### 4. Update an instance (labels, OS image, hyperthreading)

```bash
# Add or change a label
gcloud bms instances update my-instance --region=us-central1 \
    --update-labels=env=prod

# Change the OS image (list valid image codes first)
gcloud bms os-images list --project=my-project
gcloud bms instances update my-instance --region=us-central1 \
    --os-image=IMAGE_CODE

# Toggle hyperthreading
gcloud bms instances update my-instance --region=us-central1 \
    --enable-hyperthreading
```

### 5. Snapshot and restore a boot volume

```bash
# Create a snapshot (both --snapshot-name and --description are required)
gcloud bms volumes snapshot my-boot-volume --region=us-central1 \
    --snapshot-name=pre-patch --description="Pre-patching snapshot"

# List snapshots, then restore from one
gcloud bms volumes snapshots list \
    --volume=my-boot-volume --region=us-central1

gcloud bms volumes restore my-boot-volume --region=us-central1 \
    --snapshot=pre-patch

# Delete an old snapshot
gcloud bms volumes snapshots delete pre-patch \
    --volume=my-boot-volume --region=us-central1
```

### 6. Create and manage an NFS share

```bash
# SSD, 256 GiB, with one allowed client
gcloud bms nfs-shares create my-share --region=us-central1 \
    --size-gib=256 --storage-type=SSD \
    --allowed-client=network=my-network,cidr=10.130.240.24/29,mount-permissions=READ_WRITE,allow-dev=yes,allow-suid=no,enable-root-squash=yes

# List shares, update labels, then delete
gcloud bms nfs-shares list --project=my-project
gcloud bms nfs-shares update my-share --region=us-central1 \
    --update-labels=tier=gold
gcloud bms nfs-shares delete my-share --region=us-central1
```

### 7. Manage project SSH keys

```bash
# Add a key from a file, list keys, then remove one (keys are global)
gcloud bms ssh-keys add my-ssh-key --project=my-project \
    --key-file=/home/user/.ssh/id_rsa.pub
gcloud bms ssh-keys list --project=my-project
gcloud bms ssh-keys remove my-ssh-key --project=my-project
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `bms instances` | [`instances.md`](instances.md) | 9 | Manage bare metal instances (describe, list, start/stop/reset, update, rename, enable/disable serial console) |
| `bms networks` | [`networks.md`](networks.md) | 5 | Manage networks and IP-range reservations |
| `bms nfs-shares` | [`nfs-shares.md`](nfs-shares.md) | 6 | Create, manage, and delete NFS shares |
| `bms operations` | [`operations.md`](operations.md) | 2 | Describe and wait on long-running operations |
| `bms os-images` | [`os-images.md`](os-images.md) | 2 | List and describe available OS images |
| `bms ssh-keys` | [`ssh-keys.md`](ssh-keys.md) | 3 | Manage project-level SSH keys |
| `bms volumes` | [`volumes.md`](volumes.md) | 11 | Manage volumes, LUNs, and boot-volume snapshots |

See [`index.md`](index.md) for a one-line index of all 38 commands.

## Common flags & tips

- **Regional vs. global resources.** Most BMS resources (instances, networks,
  nfs-shares, volumes and their snapshots/LUNs) are regional — pass
  `--region=REGION` or use a fully qualified resource name. `operations`,
  `os-images`, and `ssh-keys` are global (`global` is the only supported
  location), so they take no `--region`.
- **Project selection.** Every command accepts the global `--project` flag, or
  falls back to the `core/project` property. `list` commands omit `--region`
  to span all regions in the project.
- **Async operations + polling.** Power and mutation commands that support
  `--async` (`instances start/stop/reset`, `instances/networks/nfs-shares
  update`, `nfs-shares create/delete`, `volumes restore`) return immediately
  and emit an operation name. Track it with
  `gcloud bms operations wait OPERATION` or re-`describe` the resource.
- **Labels.** Mutating commands use `--update-labels=KEY=VALUE,...`,
  `--remove-labels=KEY,...`, and `--clear-labels`; `nfs-shares create` uses
  `--labels` for the initial set.
- **NFS allowed clients.** `--allowed-client` takes a comma-joined property
  list (`network`, `network-project-id`, `cidr`, `mount-permissions`,
  `allow-dev`, `allow-suid`, `enable-root-squash`) and can be repeated.
  `nfs-shares update` adjusts them with `--add-allowed-client`,
  `--remove-allowed-client`, and `--clear-allowed-clients`.
- **Network IP reservations.** `networks update` edits reservations via
  `--add-ip-range-reservation`, `--remove-ip-range-reservation`, and
  `--clear-ip-range-reservations`; list current reservations with
  `gcloud bms networks list-ip-reservations`.
- **OS image codes.** Use `gcloud bms os-images list` to discover the image
  codes accepted by `instances update --os-image`.
- **Filtering output.** `list` commands support `--filter` and `--limit`, e.g.
  `gcloud bms instances list --filter="labels.env=prod" --limit=10` or
  project a table with `--format="table(name, state, machineType)"`.

## beta / alpha

There is no `gcloud beta bms` surface. `gcloud alpha bms` mirrors GA and adds:

- **`gcloud alpha bms serial-console-ssh-keys`** — `add`, `list`, `remove` SSH
  keys scoped to the interactive serial console (distinct from the GA
  `bms ssh-keys` group, which manages general project SSH keys).
- **Additional `gcloud alpha bms instances` commands** — `auth-info`
  (retrieve instance authentication info), `reimage` (reinstall the OS),
  and dedicated `enable-hyperthreading` / `disable-hyperthreading` commands
  (GA achieves the latter via `instances update --[no-]enable-hyperthreading`).

## Official documentation

- [Bare Metal Solution docs home](https://cloud.google.com/bare-metal/docs) — product overview, planning, setup, deployment, and maintenance.
- [BMS planning guide](https://cloud.google.com/bare-metal/docs/bms-planning) — regional availability, server configs, OS images, storage types, and networking architecture.
- [BMS IAM & access control](https://cloud.google.com/bare-metal/docs/bms-iam) — predefined roles such as `roles/baremetalsolution.admin`, `editor`, `viewer`, and the per-resource admin roles.
- [gcloud bms CLI reference](https://cloud.google.com/sdk/gcloud/reference/bms) — full GA command/flag reference.
- [gcloud alpha bms CLI reference](https://cloud.google.com/sdk/gcloud/reference/alpha/bms) — alpha-only subgroups and instance commands.

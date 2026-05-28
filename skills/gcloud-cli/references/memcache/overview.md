# gcloud memcache — Memorystore for Memcached

## Overview
`gcloud memcache` manages **Memorystore for Memcached**, Google Cloud's fully managed,
in-memory key-value cache that speaks the Memcached protocol. Each instance is a regional
cluster of 1–20 nodes (configurable CPU and memory per node) reachable over a VPC via
private services access. Reach for it when you need a managed Memcached-compatible cache for
application-tier acceleration without operating your own Memcached fleet.

> **Deprecation / shutdown notice:** Memorystore for Memcached will **shut down on
> January 31, 2029**, and after February 1, 2027 new instances cannot be created in new
> projects. Google recommends migrating to **Memorystore for Valkey**. Plan new
> caching workloads accordingly.

## Quick reference — common workflows

### 1. Enable APIs and create an instance
```bash
# One-time: enable Service Networking (private services access) + the Memcached API
gcloud services enable servicenetworking.googleapis.com memcache.googleapis.com

# See where Memcached instances can be created
gcloud memcache regions list

# Create a 3-node instance (2 vCPUs, 2 GB RAM per node)
gcloud memcache instances create my-memcache-instance \
    --region=us-central1 \
    --node-count=3 \
    --node-cpu=2 \
    --node-memory=2GB

# Confirm it reached READY (shows discovery endpoint and node IPs)
gcloud memcache instances describe my-memcache-instance --region=us-central1
```
A private services access connection must exist on the target VPC **before** creating an
instance. Use `--authorized-network` to target a non-default VPC and `--zones` to pin nodes.

### 2. List and inspect instances
```bash
# List all instances in a region
gcloud memcache instances list --region=us-central1

# Limit results
gcloud memcache instances list --limit=5 --region=us-central1

# Full metadata for one instance
gcloud memcache instances describe my-memcache-instance --region=us-central1
```

### 3. Scale nodes and update metadata
```bash
# Scale up to 5 nodes
gcloud memcache instances update my-memcache-instance \
    --node-count=5 \
    --region=us-central1

# Update display name + labels (these can be combined; cannot be combined with --parameters)
gcloud memcache instances update my-memcache-instance \
    --display-name="Foo Cache Service" \
    --labels="env=prod,team=backend" \
    --region=us-central1
```

### 4. Stage and apply parameter changes
Parameter changes are first **staged** in instance metadata via `update --parameters`, then
**applied** in a separate step. Applying a parameter update flushes the cache on affected nodes.
```bash
# Stage a parameter update (parameters cannot be combined with other update actions)
gcloud memcache instances update my-memcache-instance \
    --parameters="protocol=ascii,track-sizes=true" \
    --region=us-central1

# Apply staged parameters to all nodes
gcloud memcache instances apply-parameters my-memcache-instance \
    --apply-all \
    --region=us-central1

# ...or only to specific nodes
gcloud memcache instances apply-parameters my-memcache-instance \
    --node-ids=node-1,node-2 \
    --region=us-central1
```

### 5. Upgrade the Memcached engine version
```bash
# Upgrade to Memcached 1.6.15 (the only supported upgrade target)
gcloud memcache instances upgrade my-memcache-instance \
    --region=us-central1 \
    --memcached-version="1.6.15"

# Track the resulting long-running operation
gcloud memcache operations list --region=us-central1
gcloud memcache operations describe OPERATION_ID --region=us-central1
```

### 6. Reschedule maintenance, then delete
```bash
# Reschedule maintenance to the next available window
gcloud memcache instances reschedule-maintenance my-memcache-instance \
    --region=us-central1 \
    --reschedule-type=next-available-window

# ...or perform it immediately
gcloud memcache instances reschedule-maintenance my-memcache-instance \
    --region=us-central1 \
    --reschedule-type=immediate

# Delete when no longer needed
gcloud memcache instances delete my-memcache-instance --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `memcache instances` | [`instances.md`](instances.md) | 8 | manage Cloud Memorystore Memcached instances |
| `memcache operations` | [`operations.md`](operations.md) | 3 | manage Cloud Memorystore Memcached operations |
| `memcache regions` | [`regions.md`](regions.md) | 2 | manage Cloud Memorystore Memcached regions |

See [`index.md`](index.md) for a one-line index of all 13 GA commands.

## Common flags & tips
- **Region is required (regional service).** Nearly every command needs `--region`, or set a
  default with `gcloud config set memcache/region us-central1`. `regions list` needs no region.
- **Node sizing.** `--node-count` 1–20; `--node-cpu` is 1 or an even number 2–32 (1 isn't
  supported in all regions); `--node-memory` is a whole number with a `MB`/`GB` suffix
  (e.g. `2GB`, `3072MB`), between 1024MB and 307200MB.
- **Parameters are staged then applied.** `instances update --parameters` only stages the
  change; it takes effect after `instances apply-parameters` (which flushes affected nodes).
  `--parameters` cannot be combined with other `update` actions in the same call.
- **Async operations.** Most mutating commands accept `--async` to return immediately; track
  progress with `gcloud memcache operations list/describe`.
- **Networking.** Use `--authorized-network` to attach to a specific VPC and
  `--reserved-ip-range-id` to point at a named allocated range for private services access.
- **Useful list shaping:**
  ```bash
  # Names + node count + state, sorted by name
  gcloud memcache instances list --region=us-central1 \
      --format="table(name, nodeCount, state)" --sort-by=name

  # Only instances that are not READY
  gcloud memcache instances list --region=us-central1 --filter="state!=READY"

  # Just resource URIs (handy for scripting)
  gcloud memcache instances list --region=us-central1 --uri
  ```

## beta / alpha
Both `gcloud beta memcache` and `gcloud alpha memcache` exist with the same three command
groups (`instances`, `operations`, `regions`).

- **`gcloud beta memcache instances apply-software-update`** (beta-only, not in GA) — applies
  the latest available software update to all nodes or selected nodes; causes a full cache
  flush on affected nodes:
  ```bash
  gcloud beta memcache instances apply-software-update my-memcache-instance \
      --region=us-central1 \
      --apply-all
  ```
  (Use `--node-ids=NODE_IDS` instead of `--apply-all` to target specific nodes; `--async`
  returns immediately.)

All other instance commands (`create`, `delete`, `describe`, `list`, `update`, `upgrade`,
`apply-parameters`, `reschedule-maintenance`) are GA.

## Official documentation
- **Product docs home:** https://cloud.google.com/memorystore/docs/memcached — guides, reference, and resources for Memorystore for Memcached.
- **Quickstart (gcloud):** https://cloud.google.com/memorystore/docs/memcached/quickstart-gcloud — create an instance, connect from a Compute Engine VM, run get/set, then clean up.
- **Create & manage instances:** https://cloud.google.com/memorystore/docs/memcached/creating-managing-instances — create, view, scale nodes, edit parameters/labels, and delete.
- **Access control (IAM):** https://cloud.google.com/memorystore/docs/memcached/access-control — `memcache.admin` / `editor` / `viewer` roles and permissions.
- **Networking:** https://cloud.google.com/memorystore/docs/memcached/networking — private services access, VPC peering, IP range sizing, on-prem connectivity.
- **gcloud CLI reference (GA):** https://cloud.google.com/sdk/gcloud/reference/memcache — the `gcloud memcache` command surface.
- **gcloud CLI reference (beta):** https://cloud.google.com/sdk/gcloud/reference/beta/memcache — beta surface, including `apply-software-update`.

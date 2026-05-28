# gcloud memorystore — Memorystore for Valkey

## Overview

`gcloud memorystore` manages **Memorystore for Valkey** instances — Google Cloud's fully
managed, Redis-compatible Valkey Cluster service for high-performance in-memory data storage
(caching, session stores, leaderboards, queues). Reach for it when you want a managed Valkey
Cluster with sharding, replicas, in-transit TLS, persistence, and managed backups, connected
privately over Private Service Connect (PSC). This is the newer service line; the older
**Memorystore for Redis** (single-node/HA Redis instances) is managed separately under
`gcloud redis` and `gcloud redis clusters`. Use `gcloud memorystore` for Valkey workloads and
new Redis-Cluster-style deployments.

## Quick reference — common workflows

### 1. Enable APIs and create the networking prerequisite

A **service connection policy** for service class `gcp-memorystore` must already exist for the
project, VPC network, and region before any instance can be created (creation fails without it).

```bash
# Enable the required APIs
gcloud services enable memorystore.googleapis.com
gcloud services enable networkconnectivity.googleapis.com
gcloud services enable serviceconsumermanagement.googleapis.com

# Create the service connection policy (gcp-memorystore service class)
gcloud network-connectivity service-connection-policies create my-policy \
    --project=my-project \
    --region=us-central1 \
    --network=my-vpc \
    --service-class=gcp-memorystore \
    --subnets=projects/my-project/regions/us-central1/subnetworks/my-subnet
```

### 2. Create a Valkey Cluster instance

```bash
# Three-shard instance with one replica per shard and TLS, using PSC auto-connections
gcloud memorystore instances create my-instance \
    --project=my-project \
    --location=us-central1 \
    --shard-count=3 \
    --replica-count=1 \
    --node-type=highmem-medium \
    --mode=cluster \
    --transit-encryption-mode=server-authentication \
    --psc-auto-connections="network=projects/my-project/global/networks/my-vpc,projectId=my-project"
```

### 3. Inspect instances and fetch the TLS CA

```bash
# List instances in a region (--location is required)
gcloud memorystore instances list --project=my-project --location=us-central1

# Describe one instance
gcloud memorystore instances describe my-instance \
    --project=my-project --location=us-central1

# Get the certificate authority for TLS clients
gcloud memorystore instances get-certificate-authority my-instance \
    --project=my-project --location=us-central1
```

### 4. Scale and tune an instance

```bash
# Scale out to six shards
gcloud memorystore instances update my-instance \
    --project=my-project --location=us-central1 --shard-count=6

# Change an engine config (e.g. eviction policy)
gcloud memorystore instances update my-instance \
    --project=my-project --location=us-central1 \
    --update-engine-configs=maxmemory-policy=allkeys-lru
```

### 5. On-demand backup, then export to Cloud Storage

```bash
# Trigger an on-demand backup with a custom id and 7-day TTL
gcloud memorystore instances backup my-instance \
    --project=my-project --location=us-central1 \
    --backup-id=my-backup-20260527 --ttl=7d

# Find the backup collection, then list its backups
gcloud memorystore backup-collections list --project=my-project --location=us-central1
gcloud memorystore backup-collections backups list \
    --project=my-project --location=us-central1 \
    --backup-collection=my-backup-collection

# Export a backup to a GCS bucket
gcloud memorystore backup-collections backups export my-backup \
    --project=my-project --location=us-central1 \
    --backup-collection=my-backup-collection --gcs-bucket=my-bucket
```

### 6. Reschedule maintenance and track operations

```bash
# Run pending maintenance immediately
gcloud memorystore instances reschedule-maintenance my-instance \
    --project=my-project --location=us-central1 --reschedule-type=immediate

# Reschedule to a specific RFC 3339 time
gcloud memorystore instances reschedule-maintenance my-instance \
    --project=my-project --location=us-central1 \
    --reschedule-type=specific-time --schedule-time=2026-06-01T02:00:00Z

# List, describe, and cancel long-running operations
gcloud memorystore operations list --project=my-project --location=us-central1
gcloud memorystore operations describe OPERATION_ID \
    --project=my-project --location=us-central1
gcloud memorystore operations cancel OPERATION_ID \
    --project=my-project --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `memorystore backup-collections` | [`backup-collections.md`](backup-collections.md) | 6 | Manage Backup Collection resources (and the nested `backups` subgroup: delete, describe, export, list) |
| `memorystore instances` | [`instances.md`](instances.md) | 8 | Manage Instance resources: backup, create, delete, describe, get-certificate-authority, list, reschedule-maintenance, update |
| `memorystore locations` | [`locations.md`](locations.md) | 2 | List/describe Memorystore for Valkey locations |
| `memorystore operations` | [`operations.md`](operations.md) | 4 | Manage long-running operations: cancel, delete, describe, list |

See [`index.md`](index.md) for a one-line index of all 20 GA commands.

## Common flags & tips

- **`--location` is mandatory and regional.** Memorystore for Valkey is a regional service; every
  `instances`, `backup-collections`, `operations`, and `locations` command requires a region
  (e.g. `--location=us-central1`). There are no zonal resources here. Run
  `gcloud memorystore locations list` to see where instances can be created.
- **Resource identity.** You can pass a short ID plus `--location`/`--project`, or a fully
  qualified name like `projects/{project}/locations/{location}/instances/{instance}`.
- **Node types** (`--node-type`): `shared-core-nano`, `standard-small`, `highmem-medium`,
  `highmem-xlarge`. **Modes** (`--mode`): `cluster`, `cluster-disabled` (`standalone` is
  deprecated). **TLS** (`--transit-encryption-mode`): `server-authentication` or
  `transit-encryption-disabled`. **Auth** (`--authorization-mode`, create only): `auth-disabled`
  or `iam-auth`.
- **Sizing.** `--shard-count` and `--replica-count` are set at create and adjusted with
  `instances update`. Engine settings use `--engine-configs` at create, and on update use the
  additive/removing variants `--update-engine-configs`, `--remove-engine-configs`, and
  `--clear-engine-configs`.
- **Networking.** Connectivity is PSC-based. Prefer `--psc-auto-connections` (shorthand
  `network=...,projectId=...`); `--endpoints` accepts the same data in shorthand/JSON/file form.
  The legacy `--psc-auto-connections` is documented as deprecated in favor of
  `--endpoints.connections.pscAutoConnection`, but both remain accepted.
- **Async + idempotency.** Mutating commands accept `--async` to return immediately; create/delete/
  update accept `--request-id` (a UUID) so retries are idempotent.
- **Filtering & formatting.** List commands support `--filter`, `--sort-by`, `--limit`, and
  `--uri`. Examples:
  ```bash
  gcloud memorystore instances list --location=us-central1 \
      --filter="state=ACTIVE" --format="table(name,shardCount,replicaCount,state)"
  gcloud memorystore operations list --location=us-central1 \
      --filter="done=false" --sort-by=~createTime
  ```

## beta / alpha

- **`gcloud beta memorystore`** adds an **`acl-policies`** command group (create, delete, describe,
  list, update) for managing ACL Policy resources — not available in GA. Use beta for ACL/auth
  policy management until it is promoted.
- **`gcloud alpha memorystore`** mirrors beta's groups (`acl-policies`, `backup-collections`,
  `instances`, `locations`, `operations`) and may surface additional experimental flags before
  they reach beta/GA.

## Official documentation

- **Product docs home:** https://cloud.google.com/memorystore/docs/valkey — Memorystore for Valkey overview, concepts, and how-to guides.
- **Create instances:** https://cloud.google.com/memorystore/docs/valkey/create-instances — single-zone and multi-zone instance creation, required APIs, and IAM roles.
- **Networking:** https://cloud.google.com/memorystore/docs/valkey/networking — PSC connectivity and the service connection policy prerequisite.
- **Access control (IAM):** https://cloud.google.com/memorystore/docs/valkey/access-control — Memorystore for Valkey roles and permissions.
- **Node specifications:** https://cloud.google.com/memorystore/docs/valkey/instance-node-specification — node types, memory/CPU specs, and scaling limits.
- **gcloud CLI reference (GA):** https://cloud.google.com/sdk/gcloud/reference/memorystore — all `memorystore` subcommands.
- **gcloud `instances create` reference:** https://cloud.google.com/sdk/gcloud/reference/memorystore/instances/create — full flag list for instance creation.

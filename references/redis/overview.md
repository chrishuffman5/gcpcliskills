# gcloud redis — Memorystore for Redis

## Overview

`gcloud redis` manages **Memorystore for Redis**, Google Cloud's fully managed, in-memory Redis service offering sub-millisecond data access, high availability, and automatic failover. The command surface covers two products that share the same API: `redis instances` targets single-node / Standard-Tier (replicated) instances, while `redis clusters` targets the horizontally scalable, sharded Redis Cluster product. Reach for it to provision a managed cache or session store without running your own Redis servers.

All commands require the API to be enabled first: `gcloud services enable redis.googleapis.com` (covers both instances and clusters).

## Quick reference — common workflows

### Create a Standard-Tier HA instance with AUTH and in-transit encryption
```bash
gcloud services enable redis.googleapis.com

gcloud redis instances create my-redis \
    --region=us-central1 \
    --tier=standard \
    --size=5 \
    --redis-version=redis_7_2 \
    --transit-encryption-mode=server-authentication \
    --enable-auth \
    --maintenance-window-day=SUNDAY \
    --maintenance-window-hour=2

gcloud redis instances describe my-redis --region=us-central1
gcloud redis instances list --region=us-central1
```

### Scale memory, tune eviction, and enable read replicas
```bash
# Resize memory and change the maxmemory eviction policy
gcloud redis instances update my-redis \
    --region=us-central1 \
    --size=10 \
    --update-redis-config=maxmemory-policy=allkeys-lru

# Enable read replicas (Standard Tier, >=5 GiB, Redis 5.0+) — irreversible
gcloud redis instances update my-redis \
    --region=us-central1 \
    --read-replicas-mode=read-replicas-enabled \
    --replica-count=2
```

### Upgrade an instance to a newer Redis version
```bash
gcloud redis instances upgrade my-redis \
    --region=us-central1 \
    --redis-version=redis_7_2
```

### Export / import data via RDB snapshots in Cloud Storage
```bash
# Export to a GCS object (must use the .rdb extension)
gcloud redis instances export \
    gs://my-bucket/my-redis-backup.rdb my-redis \
    --region=us-central1

# Import from a GCS object (recovers with a flushed cache on cancel)
gcloud redis instances import \
    gs://my-bucket/my-redis-backup.rdb my-redis \
    --region=us-central1

# Track the long-running operation
gcloud redis operations list --region=us-central1
gcloud redis operations describe OPERATION_ID --region=us-central1
```

### Create and scale a sharded Redis Cluster
```bash
# Requires a Service Connection Policy on the target network/region first.
gcloud redis clusters create my-cluster \
    --region=us-central1 \
    --shard-count=3 \
    --replica-count=1 \
    --network=projects/MY_PROJECT/global/networks/default \
    --transit-encryption-mode=server-authentication \
    --auth-mode=iam-auth \
    --deletion-protection

gcloud redis clusters describe my-cluster --region=us-central1

# Scale shards and replicas
gcloud redis clusters update my-cluster \
    --region=us-central1 \
    --shard-count=5 \
    --replica-count=2
```

### Back up a cluster and export the backup to GCS
```bash
# On-demand backup, retained 30 days
gcloud redis clusters create-backup my-cluster \
    --region=us-central1 \
    --backup-id=backup-20260527 \
    --ttl=30d

# Find the backup collection (also shown by clusters describe)
gcloud redis clusters backup-collections list --region=us-central1

# List backups in a collection, then export one to a bucket
gcloud redis clusters backups list \
    --backup-collection=my-backup-collection --region=us-central1

gcloud redis clusters backups export my-backup \
    --backup-collection=my-backup-collection \
    --region=us-central1 \
    --gcs-bucket=my-bucket
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `redis clusters` | [`clusters.md`](clusters.md) | 19 | manage Memorystore for Redis Cluster instances (sharded), incl. `backup-collections` and `backups` subgroups |
| `redis instances` | [`instances.md`](instances.md) | 11 | manage Cloud Memorystore Redis instances (Basic / Standard Tier) |
| `redis operations` | [`operations.md`](operations.md) | 3 | manage long-running Redis operations (describe, list, cancel) |
| `redis regions` | [`regions.md`](regions.md) | 2 | list/describe regions where the Redis API is available |
| `redis zones` | [`zones.md`](zones.md) | 1 | list zones where Redis instances can be created |

See [`index.md`](index.md) for a one-line index of all 36 GA commands.

## Common flags & tips

- **Region is required for almost everything.** Pass `--region=REGION` on each command, or set a default once: `gcloud config set redis/region us-central1`. Instances, clusters, operations, and backups are all regional resources.
- **Tier & sizing (instances):** `--tier=basic` (no replication, default) vs `--tier=standard` (HA with automatic failover). `--size` is memory in GiB. Read replicas and `--alternative-zone` require Standard Tier.
- **Connection mode (instances):** `--connect-mode=direct-peering` (default) or `--connect-mode=private-service-access`; chosen at create time and not changeable later. Use `--reserved-ip-range` to pin the internal CIDR.
- **Clusters use PSC, not peering.** Provide `--network=projects/PROJECT/global/networks/NET` whose ID matches the Service Connection Policy. Cluster sizing is `--shard-count` x `--replica-count` with `--node-type` (e.g. `redis-highmem-medium`).
- **AUTH & encryption:** instances use `--enable-auth` + `gcloud redis instances get-auth-string`; clusters use `--auth-mode=iam-auth`. Both support `--transit-encryption-mode=server-authentication`.
- **Redis config:** set parameters with `--redis-config=KEY=VALUE` at create, or `--update-redis-config=KEY=VALUE` / `--remove-redis-config=KEY` on update (e.g. `maxmemory-policy`, `notify-keyspace-events`).
- **Async operations:** add `--async` to return immediately, then poll with `gcloud redis operations describe`. Import/export can be canceled with `gcloud redis operations cancel`.
- **Useful filtering/formatting:**
  - `gcloud redis instances list --region=us-central1 --filter="tier=STANDARD_HA" --format="table(name,host,port,state)"`
  - `gcloud redis clusters list --format="table(name,shardCount,replicaCount,state)"`
  - `gcloud redis instances list --uri` to pipe resource URIs into other commands.

## beta / alpha

`gcloud redis` exposes the same command groups under `gcloud beta redis` and `gcloud alpha redis`; the surface across tracks is nearly identical, with preview features appearing in `alpha`/`beta` first.

- **`gcloud (beta|alpha) redis acl-policies`** — manage ACL policies (`create`, `delete`, `describe`, `list`, `update`) for Memorystore Redis Cluster instances, granting fine-grained per-cluster key/command permissions. Not part of the GA reference files captured here.
- Check each command's "currently in beta/alpha and might change without notice" note on the gcloud reference site for track-specific behavior.

## Official documentation

- [Memorystore for Redis docs home](https://cloud.google.com/memorystore/docs/redis) — product overview, guides, quickstarts, and reference.
- [Redis overview](https://cloud.google.com/memorystore/docs/redis/redis-overview) — architecture, Basic vs Standard tier comparison, features, use cases.
- [Quickstart with gcloud](https://cloud.google.com/memorystore/docs/redis/quickstart-gcloud) — create an instance, connect from a VM, and delete via the CLI.
- [Managing instances](https://cloud.google.com/memorystore/docs/redis/managing-instances) — create/update/scale instances through console or gcloud.
- [Networking](https://cloud.google.com/memorystore/docs/redis/networking) — Direct Peering vs Private Service Access connection modes and IP ranges.
- [High availability](https://cloud.google.com/memorystore/docs/redis/high-availability) — Standard Tier failover, replication, and the 99.9% SLA.
- [Import / export](https://cloud.google.com/memorystore/docs/redis/import-export-overview) — moving data in and out using RDB snapshots in Cloud Storage.
- [Access control (IAM)](https://cloud.google.com/memorystore/docs/redis/access-control) — predefined roles (`redis.admin`, `redis.editor`, `redis.viewer`) and permissions.
- [Memorystore for Redis Cluster docs home](https://cloud.google.com/memorystore/docs/cluster) — the sharded, horizontally scalable product.
- [gcloud redis CLI reference](https://cloud.google.com/sdk/gcloud/reference/redis) — all command groups and subcommands.

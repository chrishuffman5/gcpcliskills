# gcloud managed-kafka — Managed Service for Apache Kafka

## Overview

`gcloud managed-kafka` administers Google Cloud's **Managed Service for Apache Kafka** — a fully managed Kafka service that automates cluster sizing, scaling, patching, security (TLS, SASL, mTLS), and high availability across three zones. Reach for it when you want native Apache Kafka semantics (topics, partitions, consumer groups, ACLs) without operating brokers yourself. The CLI also manages built-in Kafka Connect clusters and connectors for integrating Kafka with other systems (e.g. Pub/Sub, BigQuery).

Clusters are regional resources: nearly every command requires `--location`. Most create/update/delete operations are long-running — use `--async` to return immediately and the `operations` group to track progress.

## Quick reference — common workflows

### Create a cluster

```bash
# One-time: enable the API
gcloud services enable managedkafka.googleapis.com

# Create a cluster (minimum 3 vCPUs; memory 1–8 GiB per vCPU)
gcloud managed-kafka clusters create mycluster \
    --location=us-central1 \
    --cpu=3 \
    --memory=3GiB \
    --subnets=projects/PROJECT_ID/regions/us-central1/subnetworks/default

# Track the long-running create operation
gcloud managed-kafka operations list --location=us-central1
gcloud managed-kafka operations describe OPERATION_ID --location=us-central1

# Verify (use --full for per-broker detail and Kafka version)
gcloud managed-kafka clusters describe mycluster --location=us-central1 --full
```

### Scale a cluster

```bash
# Increase CPU/memory; auto-rebalance moves partitions onto the new brokers
gcloud managed-kafka clusters update mycluster \
    --location=us-central1 \
    --cpu=6 --memory=6GiB

gcloud managed-kafka clusters list --location=us-central1
```

### Create and manage topics

```bash
# Create a topic with 3-way replication (recommended for HA)
gcloud managed-kafka topics create mytopic \
    --cluster=mycluster --location=us-central1 \
    --partitions=10 --replication-factor=3 \
    --configs=cleanup.policy=compact,compression.type=producer

gcloud managed-kafka topics list mycluster --location=us-central1

# Increase partition count (cannot be decreased)
gcloud managed-kafka topics update mytopic \
    --cluster=mycluster --location=us-central1 \
    --partitions=20

gcloud managed-kafka topics delete mytopic \
    --cluster=mycluster --location=us-central1
```

### Inspect / reset consumer groups

```bash
gcloud managed-kafka consumer-groups list mycluster --location=us-central1

# Shows topic partition offsets
gcloud managed-kafka consumer-groups describe myconsumergroup \
    --cluster=mycluster --location=us-central1

# Reset offsets from a JSON/YAML file (or inline JSON)
gcloud managed-kafka consumer-groups update myconsumergroup \
    --cluster=mycluster --location=us-central1 \
    --topics-file=topics.json
```

### Configure access with ACLs

```bash
# Create a cluster-level ACL granting a service account all operations
gcloud managed-kafka acls create cluster \
    --cluster=mycluster --location=us-central1 \
    --acl-entry=principal='User:admin@PROJECT_ID.iam.gserviceaccount.com',operation=ALL,permission-type=ALLOW,host='*'

# Incrementally add a read entry for all topics (host defaults to "*")
gcloud managed-kafka acls add-acl-entry allTopics \
    --cluster=mycluster --location=us-central1 \
    --principal='User:reader@PROJECT_ID.iam.gserviceaccount.com' \
    --operation=READ --permission-type=ALLOW

gcloud managed-kafka acls list mycluster --location=us-central1
```

### Stream data with Kafka Connect

```bash
# Create a Connect cluster bound to an existing Kafka cluster
gcloud managed-kafka connect-clusters create myconnectcluster \
    --location=us-central1 --cpu=3 --memory=3GiB \
    --kafka-cluster=mycluster \
    --primary-subnet=projects/PROJECT_ID/regions/us-central1/subnetworks/default

# Create a connector from a config file, then control its lifecycle
gcloud managed-kafka connectors create myconnector \
    --location=us-central1 --connect-cluster=myconnectcluster \
    --config-file=my-config-file.yaml

gcloud managed-kafka connectors pause myconnector \
    --location=us-central1 --connect-cluster=myconnectcluster
gcloud managed-kafka connectors resume myconnector \
    --location=us-central1 --connect-cluster=myconnectcluster
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `managed-kafka acls` | [`acls.md`](acls.md) | 7 | Administer ACLs (cluster, topic, consumer-group, transactional-id resource patterns) |
| `managed-kafka clusters` | [`clusters.md`](clusters.md) | 5 | Create, scale, describe, and delete Kafka clusters |
| `managed-kafka connect-clusters` | [`connect-clusters.md`](connect-clusters.md) | 5 | Manage Kafka Connect clusters |
| `managed-kafka connectors` | [`connectors.md`](connectors.md) | 9 | Manage individual connectors and their lifecycle (pause/resume/stop/restart) |
| `managed-kafka consumer-groups` | [`consumer-groups.md`](consumer-groups.md) | 4 | List, describe, update (offset reset), and delete consumer groups |
| `managed-kafka operations` | [`operations.md`](operations.md) | 2 | Track long-running operations |
| `managed-kafka topics` | [`topics.md`](topics.md) | 5 | Create, list, describe, update, and delete topics |

See [`index.md`](index.md) for a one-line index of all 37 GA commands.

## Common flags & tips

- **`--location` is mandatory** on essentially every command — it is the cluster's region (see the supported [locations](https://cloud.google.com/managed-service-for-apache-kafka/docs/locations) list). Subnets and KMS encryption keys must be in the same region as the cluster.
- **Resource scoping:** topics, consumer-groups, and ACLs require `--cluster`; connectors require `--connect-cluster`.
- **Long-running operations:** add `--async` to `clusters`/`connect-clusters` create/update/delete to return immediately, then poll with `gcloud managed-kafka operations list/describe`.
- **Cluster sizing:** `--cpu` minimum is 3; `--memory` must be between 1 GiB and 8 GiB per vCPU (e.g. `--memory=3GiB`, also accepts forms like `1024Mi`, `4Gi`).
- **Auto-rebalance** is on by default at create; disable with `--no-auto-rebalance`. On `update`, toggle with `--auto-rebalance` / `--no-auto-rebalance`.
- **Topics:** partition count can only be increased, never decreased. Pass topic configs via `--configs=key=value,...` (e.g. `cleanup.policy=compact`).
- **ACLs:** the ACL **ID encodes the resource pattern** — `cluster`, `topic/NAME`, `consumerGroup/NAME`, `transactionalId/NAME`, the `*Prefixed/NAME` variants, or the wildcards `allTopics` / `allConsumerGroups` / `allTransactionalIds`. Principals use the Kafka `User:` prefix (e.g. `User:admin@PROJECT_ID.iam.gserviceaccount.com`, or `User:*`). `--host` must be `*`. Use `add-acl-entry`/`remove-acl-entry` for incremental edits; `acls update` does a full replacement and requires `--etag`.
- **Useful formatting/filtering:**

  ```bash
  # Show only cluster name and state
  gcloud managed-kafka clusters list --location=us-central1 \
      --format="table(name, state)"

  # Find topics with a high partition count
  gcloud managed-kafka topics list mycluster --location=us-central1 \
      --filter="partitionCount>=10" --sort-by=name
  ```

## beta / alpha

- `gcloud beta managed-kafka` mirrors all GA command groups and adds **`schema-registries`** (`create`, `delete`, `describe`, `list`). Schema Registry is in **Preview** and subject to the Pre-GA Offerings Terms.
- No `gcloud alpha managed-kafka` surface is documented.

## Official documentation

- [Managed Service for Apache Kafka — docs home](https://cloud.google.com/managed-service-for-apache-kafka/docs) — product overview, quickstarts, and reference hub.
- [Product overview](https://cloud.google.com/managed-service-for-apache-kafka/docs/overview) — architecture, HA, networking, and security model.
- [Quickstart](https://cloud.google.com/managed-service-for-apache-kafka/docs/quickstart) — create a cluster, connect a VM client, produce/consume messages.
- [Create a cluster](https://cloud.google.com/managed-service-for-apache-kafka/docs/create-cluster) — required flags, API enablement, IAM roles.
- [Create a topic](https://cloud.google.com/managed-service-for-apache-kafka/docs/create-topic) — partitions, replication factor, configs.
- [IAM roles & permissions](https://cloud.google.com/managed-service-for-apache-kafka/docs/roles-permissions) — predefined roles for clusters, topics, ACLs, Connect, and clients.
- [Supported locations](https://cloud.google.com/managed-service-for-apache-kafka/docs/locations) — regions where clusters can run.
- [gcloud CLI reference: managed-kafka](https://cloud.google.com/sdk/gcloud/reference/managed-kafka) — full command/flag reference.
- [gcloud beta CLI reference: managed-kafka](https://cloud.google.com/sdk/gcloud/reference/beta/managed-kafka) — beta surface including `schema-registries`.

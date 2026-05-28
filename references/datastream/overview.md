# gcloud datastream — Datastream

## Overview

Datastream is a serverless change data capture (CDC) and replication service. The `gcloud datastream`
command group manages the resources that move data from operational source databases (Oracle, MySQL,
PostgreSQL, SQL Server, MongoDB, Salesforce) into destinations such as BigQuery or Cloud Storage with
low latency. Reach for it to provision connection profiles, configure private or static-IP connectivity,
create and run replication streams, and monitor per-object backfill — all from the CLI.

The surface is **regional**: nearly every command requires `--location` (e.g. `us-central1`), and most
resources are addressed by a short ID plus that location. Streams and connection profiles are created as
long-running operations; use the `operations` group to track them.

## Quick reference — common workflows

### 1. Enable the API and get static IPs for allowlisting

```bash
# One-time: enable the Datastream API for the project
gcloud services enable datastream.googleapis.com

# List the regions where Datastream is available
gcloud datastream locations list

# Fetch the static outbound IPs for a region (allowlist these on your source firewall)
gcloud datastream locations fetch-static-ips us-central1
```

### 2. Create a MySQL source connection profile (static-IP connectivity)

```bash
gcloud datastream connection-profiles create my-mysql-profile \
  --location=us-central1 \
  --type=mysql \
  --display-name=my-mysql-profile \
  --mysql-hostname=35.188.150.50 \
  --mysql-port=3306 \
  --mysql-username=fakeuser \
  --mysql-password=fakepassword \
  --static-ip-connectivity

# Verify it, and list everything in the region
gcloud datastream connection-profiles describe my-mysql-profile --location=us-central1
gcloud datastream connection-profiles list --location=us-central1
```

### 3. Create a BigQuery destination connection profile

```bash
gcloud datastream connection-profiles create my-bq-profile \
  --location=us-central1 \
  --type=bigquery \
  --display-name=my-bq-profile
```

### 4. Set up a private connection (VPC peering) for a private source

```bash
gcloud datastream private-connections create my-private-conn \
  --location=us-central1 \
  --display-name=my-private-conn \
  --vpc=vpc-example \
  --subnet=10.0.0.0/29

gcloud datastream private-connections describe my-private-conn --location=us-central1
gcloud datastream private-connections list --location=us-central1
```

### 5. Create, start, and inspect a PostgreSQL → BigQuery stream

```bash
# Create the stream; --backfill-none skips historical data (use --backfill-all for a full load).
# Source/destination configs are JSON files (see "manage streams" docs for the schema).
gcloud datastream streams create my-pg-stream \
  --location=us-central1 \
  --display-name=my-pg-stream \
  --source=my-pg-profile \
  --postgresql-source-config=pg_source_config.json \
  --destination=my-bq-profile \
  --bigquery-destination-config=bq_dest_config.json \
  --backfill-none

# Streams start PAUSED; flip to RUNNING with a state update
gcloud datastream streams update my-pg-stream \
  --location=us-central1 \
  --state=RUNNING \
  --update-mask=state

gcloud datastream streams describe my-pg-stream --location=us-central1
gcloud datastream streams list --location=us-central1
```

### 6. Inspect stream objects and manage backfill

```bash
# List the objects (tables) the stream is replicating
gcloud datastream objects list --stream=my-pg-stream --location=us-central1

# Look up a specific object by its source identifier (schema.table for PostgreSQL)
gcloud datastream objects lookup \
  --stream=my-pg-stream --location=us-central1 \
  --postgresql-schema=public --postgresql-table=orders

# Start or stop a backfill on an object (OBJECT is the object ID, positional)
gcloud datastream objects start-backfill my-object --stream=my-pg-stream --location=us-central1
gcloud datastream objects stop-backfill  my-object --stream=my-pg-stream --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `datastream connection-profiles` | [`connection-profiles.md`](connection-profiles.md) | 6 | manage Datastream connection profiles |
| `datastream locations` | [`locations.md`](locations.md) | 3 | manage Datastream location resources |
| `datastream objects` | [`objects.md`](objects.md) | 5 | manage Datastream stream objects |
| `datastream operations` | [`operations.md`](operations.md) | 4 | manage Datastream operations |
| `datastream private-connections` | [`private-connections.md`](private-connections.md) | 4 | manage Datastream private connections |
| `datastream routes` | [`routes.md`](routes.md) | 4 | manage Datastream routes |
| `datastream streams` | [`streams.md`](streams.md) | 5 | manage Datastream stream resources |

See [`index.md`](index.md) for a one-line index of all 31 GA commands.

## Common flags & tips

- **`--location` is required almost everywhere.** Pass it explicitly, or set a default with
  `gcloud config set datastream/location us-central1`. Use `gcloud datastream locations list` to
  discover valid regions.
- **Connection-profile types** (`--type`): `mysql`, `oracle`, `postgresql`, `sqlserver`, `salesforce`,
  `mongodb`, `google-cloud-storage`, `bigquery`. Source-database profiles also need their per-engine
  host/port/username/password flags (e.g. `--mysql-hostname`, `--postgresql-database`).
- **Passwords**: prefer not putting secrets on the command line. Each engine supports a
  `--<engine>-prompt-for-password` flag and a `--<engine>-secret-manager-stored-password` flag in place
  of the plaintext `--<engine>-password`.
- **Connectivity methods** on a profile are mutually exclusive: `--static-ip-connectivity`,
  `--private-connection=NAME`, or forward-SSH tunneling (`--forward-ssh-hostname`, ...).
- **Private connections** use either VPC peering (`--vpc` + `--subnet`) or a PSC interface
  (`--network-attachment`). Deleting one requires `--force`.
- **Stream lifecycle**: control state with `streams update --state=RUNNING|PAUSED --update-mask=state`.
  The `--update-mask` field is required to scope which fields an update overwrites.
- **Backfill**: choose `--backfill-none` or `--backfill-all` at stream creation; per-object backfill is
  driven later with `objects start-backfill` / `objects stop-backfill`.
- **Validate before applying**: `connection-profiles create --force` skips validation, while
  `streams create --validate-only` and `private-connections create --validate-only` check without
  creating.
- **Filtering / formatting** (standard gcloud flags supported on every `list`):
  ```bash
  gcloud datastream streams list --location=us-central1 \
    --filter="state=RUNNING" --format="table(name, state, displayName)"
  gcloud datastream connection-profiles list --location=us-central1 --uri
  ```

## beta / alpha

`gcloud beta datastream` mirrors the GA surface — the same seven subgroups (connection-profiles,
locations, objects, operations, private-connections, routes, streams). No commands are exclusive to
beta or alpha; the GA `gcloud datastream` track is the primary interface, and beta exists for early
access to changes before GA promotion.

## Official documentation

- [Datastream product docs home](https://cloud.google.com/datastream/docs) — entry point for all guides, references, and resources.
- [Overview / quickstart](https://cloud.google.com/datastream/docs/quickstart) — what Datastream is, with supported sources and destinations.
- [Core concepts](https://cloud.google.com/datastream/docs/concepts) — connection profiles, private connectivity, and streams.
- [Create connection profiles](https://cloud.google.com/datastream/docs/create-connection-profiles) — per-source/destination profile setup.
- [Create a stream](https://cloud.google.com/datastream/docs/create-a-stream) — building a stream end to end.
- [Manage streams](https://cloud.google.com/datastream/docs/manage-streams) — gcloud/REST stream operations, including source/destination config JSON.
- [Private connectivity](https://cloud.google.com/datastream/docs/private-connectivity) — VPC Network Peering for private source access.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/datastream) — full reference for every `datastream` subgroup and command.

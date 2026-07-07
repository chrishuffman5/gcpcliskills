---
name: gcloud-pubsub
description: >-
  Cloud Pub/Sub via gcloud (`gcloud pubsub`). Manage Cloud Pub/Sub topics, subscriptions, and snapshots — lite-operations, lite-reservations, lite-subscriptions, lite-topics, message-transforms, schemas, snapshots, subscriptions.
---

# gcloud pubsub — Cloud Pub/Sub

## Overview

Cloud Pub/Sub is Google Cloud's asynchronous, scalable messaging service that decouples
publishers from subscribers. The core resources are **topics** (named channels publishers send
to), **subscriptions** (pull or push entities that receive a topic's messages, including BigQuery
and Cloud Storage export sinks), **schemas** (optional Avro or Protocol Buffer contracts attached
to topics), and **snapshots** (point-in-time ack-state captures used for replay/seek). The `gcloud
pubsub` surface is GA. Pub/Sub Lite (`gcloud pubsub lite-*`) is a separate, lower-cost zonal
product with its own resource model.

## Quick reference — common workflows

**Enable the API (once per project):**
```bash
gcloud services enable pubsub.googleapis.com
```

**Create a topic and a pull subscription:**
```bash
gcloud pubsub topics create my-topic --message-retention-duration=7d

gcloud pubsub subscriptions create my-sub \
  --topic=my-topic \
  --ack-deadline=60 \
  --message-retention-duration=7d
```

**Create a push subscription (Pub/Sub POSTs to your endpoint):**
```bash
gcloud pubsub subscriptions create my-push-sub \
  --topic=my-topic \
  --push-endpoint=https://my-app.example.com/pubsub/push \
  --push-auth-service-account=push-sa@my-project.iam.gserviceaccount.com
```

**Publish a message, then pull and acknowledge:**
```bash
gcloud pubsub topics publish my-topic \
  --message="Hello World!" \
  --attribute=env=prod,version=1

# Pull up to 5 messages and auto-ack them
gcloud pubsub subscriptions pull my-sub --limit=5 --auto-ack

# Or pull without acking, then ack the printed ACK_ID(s) manually
gcloud pubsub subscriptions pull my-sub --limit=1
gcloud pubsub subscriptions ack my-sub --ack-ids=ACK_ID_FROM_PULL
```

**Snapshot and seek (replay / purge backlog):**
```bash
# Retaining acked messages lets you seek back in time
gcloud pubsub subscriptions update my-sub \
  --retain-acked-messages --message-retention-duration=3d

gcloud pubsub snapshots create my-snapshot --subscription=my-sub
gcloud pubsub subscriptions seek my-sub --snapshot=my-snapshot
gcloud pubsub subscriptions seek my-sub --time=2026-01-01T00:00:00Z
```

**Dead-letter topic plus IAM bindings:**
```bash
gcloud pubsub topics create my-dlq-topic

gcloud pubsub subscriptions create my-sub-dlq \
  --topic=my-topic \
  --dead-letter-topic=my-dlq-topic \
  --max-delivery-attempts=10

gcloud pubsub topics add-iam-policy-binding my-topic \
  --member='serviceAccount:publisher@my-project.iam.gserviceaccount.com' \
  --role='roles/pubsub.publisher'

gcloud pubsub subscriptions add-iam-policy-binding my-sub \
  --member='serviceAccount:worker@my-project.iam.gserviceaccount.com' \
  --role='roles/pubsub.subscriber'
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `pubsub lite-operations` | [`lite-operations.md`](lite-operations.md) | 2 | manage Pub/Sub Lite operations |
| `pubsub lite-reservations` | [`lite-reservations.md`](lite-reservations.md) | 6 | manage Pub/Sub Lite reservations |
| `pubsub lite-subscriptions` | [`lite-subscriptions.md`](lite-subscriptions.md) | 8 | manage Pub/Sub Lite subscriptions |
| `pubsub lite-topics` | [`lite-topics.md`](lite-topics.md) | 7 | manage Pub/Sub Lite topics |
| `pubsub message-transforms` | [`message-transforms.md`](message-transforms.md) | 2 | manage Cloud Pub/Sub message transforms |
| `pubsub schemas` | [`schemas.md`](schemas.md) | 10 | manage Pub/Sub schemas |
| `pubsub snapshots` | [`snapshots.md`](snapshots.md) | 4 | manage Cloud Pub/Sub snapshots |
| `pubsub subscriptions` | [`subscriptions.md`](subscriptions.md) | 14 | manage Cloud Pub/Sub subscriptions |
| `pubsub topics` | [`topics.md`](topics.md) | 12 | manage Cloud Pub/Sub topics |

See [`index.md`](index.md) for a one-line index of all 65 commands.

## Common flags & tips

- **Subscription target:** `--topic=TOPIC` is required on `subscriptions create` (use `--topic-project` for a cross-project topic). A subscription is PULL by default and becomes PUSH when `--push-endpoint` is set.
- **Delivery tuning:** `--ack-deadline=SECONDS`, `--message-retention-duration=INTEGER[s|m|h|d]` (10m–31d), `--expiration-period=...` (or `never`), `--enable-exactly-once-delivery`, `--enable-message-ordering`. Topics carry their own `--message-retention-duration`.
- **Filtering messages:** `--message-filter='attributes.env = "prod"'` on `subscriptions create` delivers only matching messages (Pub/Sub filtering syntax).
- **Dead-letter:** `--dead-letter-topic=TOPIC` requires `--max-delivery-attempts=N`; clear later with `subscriptions update --clear-dead-letter-policy`.
- **Push auth:** `--push-auth-service-account`, `--push-auth-token-audience`; change the endpoint live with `subscriptions modify-push-config --push-endpoint=...`.
- **Publish:** `--message=BODY`, `--attribute=KEY=VALUE,...` (up to 100), `--ordering-key=KEY` (pairs with `--enable-message-ordering`).
- **Pull:** `--limit=N` (default 1), `--auto-ack`; otherwise capture ACK_IDs and call `subscriptions ack --ack-ids=...`.
- **Schemas:** attach with `topics create --schema=SCHEMA --message-encoding=json|binary`; create with `schemas create --type=avro|protocol-buffer --definition=... | --definition-file=...`.
- **Output control:** `gcloud pubsub topics list --format="value(name)"`, `gcloud pubsub subscriptions list --filter="topic:my-topic" --format=json`, and `--uri` to emit resource URIs for scripting.

## beta / alpha

Nearly all Pub/Sub features are GA on the `gcloud pubsub` surface, including schemas, snapshots/seek,
dead-letter topics, exactly-once delivery, message ordering, BigQuery/Cloud Storage export
subscriptions, and message transforms. `gcloud beta pubsub` and `gcloud alpha pubsub` exist but are
rarely needed for these workflows. Pub/Sub Lite (`gcloud pubsub lite-*`) is a distinct product, not
a track of standard Pub/Sub.

## Official documentation

- [Cloud Pub/Sub overview](https://cloud.google.com/pubsub/docs/overview) — concepts, delivery patterns, use cases
- [CLI quickstart](https://cloud.google.com/pubsub/docs/quickstart-cli) — enable API, create topic/subscription, publish, pull
- [Create and configure topics](https://cloud.google.com/pubsub/docs/create-topic) — schema, retention, encryption options
- [Push vs pull subscriptions](https://cloud.google.com/pubsub/docs/subscriber) — architecture and tradeoffs
- [Pub/Sub schemas](https://cloud.google.com/pubsub/docs/schemas) — Avro and Protocol Buffer types
- [Replay and purge with snapshots/seek](https://cloud.google.com/pubsub/docs/replay-overview) — point-in-time backlog reset
- [Access control (IAM)](https://cloud.google.com/pubsub/docs/access-control) — roles and permissions
- [gcloud pubsub CLI reference](https://cloud.google.com/sdk/gcloud/reference/pubsub) — all subgroups and commands

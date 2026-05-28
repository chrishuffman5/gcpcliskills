# gcloud eventarc — Eventarc

## Overview

Eventarc is Google Cloud's fully managed eventing service for building event-driven architectures without running your own messaging infrastructure. Reach for it when you need to route events from Google sources (Cloud Audit Logs, Pub/Sub, and direct provider events) or third-party providers to destinations like Cloud Run, GKE, Workflows, or HTTP endpoints. It comes in two editions: **Eventarc Standard** (triggers/channels for direct, single-source routing) and **Eventarc Advanced** (message buses, pipelines, and enrollments for multi-source routing with CEL filtering and message transformation).

## Quick reference — common workflows

### 1. Route Pub/Sub events to Cloud Run (Standard)

```bash
# Enable the API (required once per project)
gcloud services enable eventarc.googleapis.com

# Optionally set a default location to avoid repeating --location
gcloud config set eventarc/location us-central1

# Discover available event providers / types
gcloud eventarc providers list

# Create the trigger
gcloud eventarc triggers create my-pubsub-trigger \
    --event-filters="type=google.cloud.pubsub.topic.v1.messagePublished" \
    --destination-run-service=my-run-service \
    --destination-run-region=us-central1 \
    --service-account=my-sa@PROJECT_ID.iam.gserviceaccount.com

gcloud eventarc triggers describe my-pubsub-trigger
```

### 2. Trigger on Cloud Audit Log events (Standard)

```bash
# Discover valid serviceName / methodName values
gcloud eventarc audit-logs-provider service-names list
gcloud eventarc audit-logs-provider method-names list \
    --service-name=storage.googleapis.com

# Audit-log triggers need type + serviceName + methodName filters
gcloud eventarc triggers create my-audit-trigger \
    --event-filters="type=google.cloud.audit.log.v1.written" \
    --event-filters="serviceName=storage.googleapis.com" \
    --event-filters="methodName=storage.objects.create" \
    --destination-run-service=my-run-service \
    --service-account=my-sa@PROJECT_ID.iam.gserviceaccount.com

# List triggers across all locations
gcloud eventarc triggers list --location=-
```

### 3. Third-party events via a custom channel (Standard)

```bash
# Create a channel bound to a third-party provider
gcloud eventarc channels create my-channel \
    --location=us-central1 \
    --provider=projects/PROJECT_ID/locations/us-central1/providers/PROVIDER_ID

# Describe to retrieve the provider activation token
gcloud eventarc channels describe my-channel --location=us-central1

# Create a trigger bound to the channel
gcloud eventarc triggers create my-channel-trigger \
    --channel=my-channel \
    --event-filters="type=CUSTOM_EVENT_TYPE" \
    --destination-run-service=my-run-service \
    --service-account=my-sa@PROJECT_ID.iam.gserviceaccount.com
```

### 4. Eventarc Advanced — message bus + pipeline + enrollment

```bash
# Step 1 — Create the message bus
gcloud eventarc message-buses create my-bus \
    --location=us-central1 \
    --logging-config=INFO

# Step 2 — Create a pipeline with an HTTP endpoint destination and retry policy
gcloud eventarc pipelines create my-pipeline \
    --location=us-central1 \
    --destinations=http_endpoint_uri='https://my-service.example.com',google_oidc_authentication_service_account=my-sa@PROJECT_ID.iam.gserviceaccount.com \
    --max-retry-attempts=5 \
    --min-retry-delay=1s \
    --max-retry-delay=60s

# Step 3 — Create an enrollment connecting the bus to the pipeline via a CEL match
gcloud eventarc enrollments create my-enrollment \
    --location=us-central1 \
    --message-bus=my-bus \
    --cel-match="message.type == 'google.cloud.pubsub.topic.v1.messagePublished'" \
    --destination-pipeline=my-pipeline

# Verify the enrollment is attached to the bus
gcloud eventarc message-buses list-enrollments my-bus --location=us-central1
```

### 5. Publish an event directly to a message bus (Advanced)

```bash
gcloud eventarc message-buses publish my-bus \
    --location=us-central1 \
    --event-id=evt-001 \
    --event-type=com.example.my-event \
    --event-source="//example.com/my-source" \
    --event-data='{"key": "value"}'
```

### 6. Update and clean up

```bash
# Update a trigger's destination
gcloud eventarc triggers update my-pubsub-trigger \
    --destination-run-service=my-new-service

# Tear down Advanced resources in dependency order
gcloud eventarc enrollments delete my-enrollment --location=us-central1
gcloud eventarc pipelines delete my-pipeline --location=us-central1
gcloud eventarc message-buses delete my-bus --location=us-central1

# Tear down Standard resources
gcloud eventarc triggers delete my-pubsub-trigger
gcloud eventarc channels delete my-channel --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `eventarc audit-logs-provider` | [`audit-logs-provider.md`](audit-logs-provider.md) | 2 | Explore serviceName / methodName values for the `google.cloud.audit.log.v1.written` event type |
| `eventarc channel-connections` | [`channel-connections.md`](channel-connections.md) | 4 | Manage channel connections (third-party providers connecting to a channel) |
| `eventarc channels` | [`channels.md`](channels.md) | 5 | Manage channels for third-party / custom event sources (Standard) |
| `eventarc enrollments` | [`enrollments.md`](enrollments.md) | 5 | Manage enrollments that bind a message bus to a pipeline via CEL match (Advanced) |
| `eventarc google-api-sources` | [`google-api-sources.md`](google-api-sources.md) | 5 | Manage Google API sources that feed Google events into a message bus (Advanced) |
| `eventarc google-channels` | [`google-channels.md`](google-channels.md) | 2 | Manage the per-location Google channel (CMEK config) |
| `eventarc locations` | [`locations.md`](locations.md) | 1 | List locations available for Eventarc |
| `eventarc message-buses` | [`message-buses.md`](message-buses.md) | 7 | Manage message buses and publish events to them (Advanced) |
| `eventarc pipelines` | [`pipelines.md`](pipelines.md) | 5 | Manage pipelines that route, transform, and deliver bus events (Advanced) |
| `eventarc providers` | [`providers.md`](providers.md) | 2 | Explore event providers and their event types |
| `eventarc triggers` | [`triggers.md`](triggers.md) | 5 | Manage triggers that route events to a destination (Standard) |

See [`index.md`](index.md) for a one-line index of all 43 GA commands.

## Common flags & tips

- **Location is required for most resources.** Pass `--location=REGION`, or set the default once with `gcloud config set eventarc/location REGION`. Triggers, channels, providers, and channel-connections accept `global`; message buses, pipelines, enrollments, and Google API sources require a regional location.
- **Aggregate across locations** on `list` commands with `--location=-` (e.g. `gcloud eventarc triggers list --location=-`).
- **`--event-filters` is repeatable.** Every trigger filter set must include `type=...`; audit-log triggers additionally need `serviceName` and `methodName` filters. Use `--event-filters-path-pattern` for `resourceName` path patterns on audit-log events (requires `--channel`).
- **Trigger destinations are mutually exclusive groups:** Cloud Run (`--destination-run-service` + `--destination-run-region`/`--destination-run-path`), GKE (`--destination-gke-*`), Workflows (`--destination-workflow` + `--destination-workflow-location`), or an HTTP endpoint (`--destination-http-endpoint-uri` + `--network-attachment`).
- **Pipeline `--destinations` is a single dict** with exactly one of `http_endpoint_uri`, `workflow`, `message_bus`, or `pubsub_topic`. Auth keys (`google_oidc_authentication_service_account`, `oauth_token_authentication_service_account`), payload-format keys, and `network_attachment` are set inside the same `--destinations` value. Retry behavior is controlled by the separate `--max-retry-attempts` / `--min-retry-delay` / `--max-retry-delay` flags.
- **Logging level** on buses, pipelines, and Google API sources uses `--logging-config` (one of `NONE, DEBUG, INFO, NOTICE, WARNING, ERROR, CRITICAL, ALERT, EMERGENCY`).
- **CMEK:** `--crypto-key=` (and `--clear-crypto-key` on update) is available on channels, message buses, pipelines, Google API sources, and the Google channel.
- **Format/filter examples:**
  - `gcloud eventarc triggers list --location=- --format="table(name, destination.cloudRun.service, eventFilters)"`
  - `gcloud eventarc providers list --location=us-central1 --filter="eventTypes.type:audit"`
  - `gcloud eventarc message-buses list --location=- --uri`
- **Use `--async`** on create/update/delete to return immediately instead of waiting for the long-running operation.
- **IAM reminders:** grant the trigger/pipeline service account `roles/eventarc.eventReceiver`; for Cloud Run destinations also grant `roles/run.invoker`, and for Workflows destinations `roles/workflows.invoker`. Direct publishing to Eventarc Advanced requires `gcloud services enable eventarcpublishing.googleapis.com`.

## beta / alpha

`gcloud beta eventarc` exists and mirrors the GA surface for the Advanced-focused groups, which may receive new flags earlier:

- `gcloud beta eventarc enrollments`
- `gcloud beta eventarc google-api-sources`
- `gcloud beta eventarc message-buses`
- `gcloud beta eventarc pipelines`

The GA `gcloud eventarc` surface covers these plus `triggers`, `channels`, `channel-connections`, `providers`, `audit-logs-provider`, `google-channels`, and `locations`. Use GA commands for triggers and channels in production. There is no documented `gcloud alpha eventarc` group at the time of research.

## Official documentation

- [Eventarc documentation home](https://cloud.google.com/eventarc/docs) — product docs covering both Standard and Advanced editions.
- [Eventarc overview](https://cloud.google.com/eventarc/docs/overview) — concepts; compares Standard vs. Advanced and explains triggers, channels, and providers.
- [Eventarc Advanced overview](https://cloud.google.com/eventarc/advanced/docs/overview) — buses, enrollments, and pipelines and their role in routing.
- [Event providers and destinations](https://cloud.google.com/eventarc/docs/event-providers-targets) — supported event sources and routing targets for both editions.
- [Create an enrollment to receive events](https://cloud.google.com/eventarc/advanced/docs/receive-events/create-enrollment) — how-to for enrollments and pipelines in Eventarc Advanced.
- [Access control (IAM)](https://cloud.google.com/eventarc/docs/access-control) — predefined Eventarc roles and permissions.
- [gcloud eventarc CLI reference](https://cloud.google.com/sdk/gcloud/reference/eventarc) — full command reference (11 groups, 43 GA commands).
- [gcloud beta eventarc CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/eventarc) — beta variants of the Advanced-focused groups.

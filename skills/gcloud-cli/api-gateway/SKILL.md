---
name: gcloud-api-gateway
description: >-
  API Gateway via gcloud (`gcloud api-gateway`). Manage Cloud API Gateway resources — api-configs, apis, gateways, operations.
---

# gcloud api-gateway — API Gateway

## Overview

Cloud API Gateway is a fully managed service that provides secure, monitored access to backend services (Cloud Run, Cloud Functions, App Engine, and others) through a well-defined REST API. Reach for `gcloud api-gateway` when you need to publish an API surface — defined by an OpenAPI or gRPC spec — handle authentication and API keys, and deploy a managed, scalable gateway endpoint without running your own proxy infrastructure. The CLI manages four resource types: **APIs** (logical containers), **API configs** (immutable spec + backend bindings), **gateways** (regional serving endpoints), and **operations** (long-running task tracking).

## Quick reference — common workflows

### 1. Enable the API

```bash
gcloud services enable apigateway.googleapis.com
gcloud services enable servicemanagement.googleapis.com
gcloud services enable servicecontrol.googleapis.com
```

### 2. Full deployment — API, config, then gateway

The API config binds the spec to a backend. The gateway (regional) serves it. Note `api-configs create` will implicitly create the API if it does not yet exist.

```bash
# Create the API (logical container)
gcloud api-gateway apis create my-api

# Create an API config from an OpenAPI spec, signing backend tokens with a service account
gcloud api-gateway api-configs create my-config \
    --api=my-api \
    --openapi-spec=path/to/openapi_spec.yaml \
    --backend-auth-service-account=SA_EMAIL@PROJECT.iam.gserviceaccount.com

# Deploy a gateway in a region (location is required for gateways)
gcloud api-gateway gateways create my-gateway \
    --api=my-api \
    --api-config=my-config \
    --location=us-central1

# Read back the gateway and note its defaultHostname
gcloud api-gateway gateways describe my-gateway --location=us-central1
```

### 3. Roll out a new config to a live gateway

API configs are immutable, so create a new one and point the gateway at it.

```bash
gcloud api-gateway api-configs create my-config-v2 \
    --api=my-api \
    --openapi-spec=path/to/openapi_spec_v2.yaml \
    --backend-auth-service-account=SA_EMAIL@PROJECT.iam.gserviceaccount.com

gcloud api-gateway gateways update my-gateway \
    --api=my-api \
    --api-config=my-config-v2 \
    --location=us-central1
```

### 4. List and inspect resources

```bash
gcloud api-gateway apis list
gcloud api-gateway api-configs list --api=my-api
gcloud api-gateway gateways list --location=us-central1

# Inspect a config including the base64-encoded source spec
gcloud api-gateway api-configs describe my-config --api=my-api --view=FULL
```

### 5. Grant access on an API

```bash
gcloud api-gateway apis add-iam-policy-binding my-api \
    --member='user:developer@example.com' \
    --role='roles/editor'

gcloud api-gateway apis get-iam-policy my-api
```

### 6. Tear down (order matters)

Delete the gateway first, then the config, then the API. An API cannot be deleted while configs still belong to it.

```bash
gcloud api-gateway gateways delete my-gateway --location=us-central1
gcloud api-gateway api-configs delete my-config --api=my-api
gcloud api-gateway apis delete my-api
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `api-gateway api-configs` | [`api-configs.md`](api-configs.md) | 5 | manage Cloud API Gateway API Configs |
| `api-gateway apis` | [`apis.md`](apis.md) | 8 | manage Cloud API Gateway APIs |
| `api-gateway gateways` | [`gateways.md`](gateways.md) | 8 | manage Cloud API Gateway Gateways |
| `api-gateway operations` | [`operations.md`](operations.md) | 4 | manage operations for Cloud API Gateways |

See [`index.md`](index.md) for a one-line index of all 25 GA commands.

## Common flags & tips

- **Spec source (config):** `api-configs create` requires exactly one of `--openapi-spec=[FILE,...]` (REST) or `--grpc-files=[FILE,...]` (gRPC service config + proto descriptors). These flags accept comma-separated lists of files.
- **Backend auth:** `--backend-auth-service-account` on `api-configs create` names the service account used to sign tokens for authenticated backends. That account needs the matching invoker role on the backend (e.g. `roles/run.invoker` for Cloud Run, `roles/cloudfunctions.invoker` for Cloud Functions).
- **Locations:** APIs and API configs default to **global** — they take no `--location`. Gateways and operations are **regional**; gateways require `--location` on create/describe/update/delete, and `gateways list` / `operations list` default to a wildcard across regions unless `--location` is given.
- **Immutability:** Only the display name and labels are mutable on APIs and API configs (`update` accepts `--display-name`, `--update-labels`, `--clear-labels`, `--remove-labels`). To change a spec, create a new config. Gateways additionally allow re-pointing via `--api`/`--api-config` on `update`.
- **Async:** Most mutating commands accept `--async` to return immediately; pair with `gcloud api-gateway operations wait OPERATION --location=LOCATION` to block on completion.
- **Implicit API creation:** `api-configs create` creates the named API automatically if it does not exist.
- **Filtering / formatting examples:**

  ```bash
  # Just gateway IDs and their hostnames
  gcloud api-gateway gateways list --location=us-central1 \
      --format="table(name, defaultHostname, state)"

  # Configs filtered by a label
  gcloud api-gateway api-configs list --api=my-api \
      --filter="labels.env=prod"

  # Watch in-flight operations in a region
  gcloud api-gateway operations list --location=us-central1 \
      --filter="NOT done"
  ```

## beta / alpha

`gcloud beta api-gateway` and `gcloud alpha api-gateway` exist and expose the same four subgroups (`api-configs`, `apis`, `gateways`, `operations`) as the GA surface. No feature differences from GA are documented in the official reference; use GA (`gcloud api-gateway`) for production work. The beta/alpha tracks may surface experimental flags not reflected in the GA docs.

## Official documentation

- [API Gateway documentation](https://cloud.google.com/api-gateway/docs) — product docs home and navigation hub for all topics.
- [About API Gateway](https://cloud.google.com/api-gateway/docs/about-api-gateway) — concept intro to the secure REST API abstraction model.
- [Quickstart](https://cloud.google.com/api-gateway/docs/quickstart) — end-to-end walkthrough deploying a backend behind a gateway with optional API key security.
- [Architecture overview](https://cloud.google.com/api-gateway/docs/architecture-overview) — request flow through Service Control, Service Management, and backend forwarding.
- [Creating an API](https://cloud.google.com/api-gateway/docs/creating-api) — `apis create` naming rules and commands.
- [Creating an API config](https://cloud.google.com/api-gateway/docs/creating-api-config) — `api-configs create` with OpenAPI or gRPC.
- [Configure your dev environment](https://cloud.google.com/api-gateway/docs/configure-dev-env) — APIs to enable, IAM roles, and service account setup.
- [gcloud api-gateway reference](https://cloud.google.com/sdk/gcloud/reference/api-gateway) — full CLI command reference (all 25 GA commands).

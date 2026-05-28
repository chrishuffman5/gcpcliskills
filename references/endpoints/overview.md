# gcloud endpoints — Cloud Endpoints

## Overview
Cloud Endpoints is a distributed API management system that lets you secure, monitor, analyze, and set quotas on your APIs using the same infrastructure Google uses for its own APIs. The `gcloud endpoints` command group manages the **managed service** side of Endpoints: you deploy an API service configuration (OpenAPI/Swagger, gRPC proto descriptors, or Google Service Config), inspect config versions and long-running operations, and control consumer access via IAM. Reach for it whenever you publish an API fronted by the Extensible Service Proxy (ESP/ESPv2) on Compute Engine, GKE, Cloud Run, or App Engine.

## Quick reference — common workflows

### 1. Enable the prerequisite APIs
```bash
# Service Management + Service Control back the managed service and the runtime proxy.
# `services deploy` typically enables these automatically, but enable explicitly if needed.
gcloud services enable servicemanagement.googleapis.com
gcloud services enable servicecontrol.googleapis.com
```

### 2. Deploy an OpenAPI (REST) service configuration
```bash
# Deploy a Swagger/OpenAPI spec — creates or updates the managed service.
gcloud endpoints services deploy openapi.yaml

# Validate a config without deploying (the service must already exist).
gcloud endpoints services deploy openapi.yaml --validate-only

# Inspect the resulting service.
gcloud endpoints services describe my-service
```

### 3. Deploy a gRPC service configuration
```bash
# Deploy a compiled proto descriptor together with its service config YAML.
gcloud endpoints services deploy ~/my_app/service-config.yaml ~/my_app/service-protos.pb

# Confirm the deployment.
gcloud endpoints services describe my-service
```

### 4. List services and inspect configuration versions
```bash
# List the services produced by the current project.
gcloud endpoints services list

# List every config version for a service, then describe a specific one.
gcloud endpoints configs list --service=my-service
gcloud endpoints configs describe 2017-01-01R0 --service=my-service
```

### 5. Monitor and wait on deploy operations
```bash
# List operations for a service; filter to completed ones.
gcloud endpoints operations list --service=my-service
gcloud endpoints operations list --service=my-service --filter='done = true'

# Describe one operation, then block until a long-running operation finishes.
gcloud endpoints operations describe serviceConfigs.my-service.1
gcloud endpoints operations wait serviceConfigs.my-service.1
```

### 6. Manage consumer access (IAM)
```bash
# Let a developer enable and consume the API.
gcloud endpoints services add-iam-policy-binding my-service \
    --member='user:developer@example.com' \
    --role='roles/servicemanagement.serviceConsumer'

# Grant a CI/CD service account permission to deploy configs.
gcloud endpoints services add-iam-policy-binding my-service \
    --member='serviceAccount:deploy-sa@my-project.iam.gserviceaccount.com' \
    --role='roles/servicemanagement.configEditor'

# View the policy, check your own effective permissions, and remove a binding.
gcloud endpoints services get-iam-policy my-service
gcloud endpoints services check-iam-policy my-service
gcloud endpoints services remove-iam-policy-binding my-service \
    --member='user:developer@example.com' \
    --role='roles/servicemanagement.serviceConsumer'
```

### 7. Delete and restore a service
```bash
# Delete a service (retained for 30 days), optionally without blocking.
gcloud endpoints services delete my-service
gcloud endpoints services delete my-service --async

# Restore a service deleted within the last 30 days.
gcloud endpoints services undelete my-service
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `endpoints configs` | [`configs.md`](configs.md) | 2 | View configuration versions for a service |
| `endpoints operations` | [`operations.md`](operations.md) | 3 | Describe, list, and wait on long-running operations |
| `endpoints services` | [`services.md`](services.md) | 9 | Deploy, describe, list, delete/undelete services and manage their IAM |

See [`index.md`](index.md) for a one-line index of all 14 GA commands.

## Common flags & tips
- **Service naming:** the service name comes from the `host` field in an OpenAPI spec or the `name` field in a Google Service Config / proto config (often `api.endpoints.PROJECT_ID.cloud.goog` for Endpoints-on-Cloud-Run/GKE).
- **`services deploy` is multi-file:** pass multiple `SERVICE_CONFIG_FILE` paths (e.g. a `.pb` proto descriptor plus a `.yaml` config). If a service name appears in more than one file, the first wins.
- **`--validate-only`** (deploy) checks a configuration without applying it; the service must already exist.
- **`--force` / `-f`** (deploy) pushes a config through even when hazardous changes are detected.
- **`--async`** (`deploy`, `delete`, `undelete`) returns immediately; combine with `operations wait OPERATION` to block on completion later.
- **`--service` is required** on `configs list` and on `configs describe` in practice; it is optional on `operations list` (which can list project-wide).
- **`operations list --filter`** supports only `startTime` (ISO 8601, with `>=`/`>`/`<=`/`<`, value in quotes) and `done` (boolean, `=`/`!=`). Example: `--filter='startTime >= "2017-02-01"'`.
- **IAM `--member` forms:** `user:`, `group:`, `serviceAccount:`, `domain:`, plus `allUsers` / `allAuthenticatedUsers`. The `roles/servicemanagement.serviceConsumer` role can only be bound to a user, group, or service account.
- **Operation names:** the `operations/` prefix is optional for `operations describe` and `operations wait`.

## beta / alpha
- `gcloud beta endpoints` and `gcloud alpha endpoints` mirror the GA surface (`configs`, `operations`, `services` subgroups) and carry the standard "may change without notice" disclaimer.
- **alpha-only:** `gcloud alpha endpoints quota` manages service-consumer quota (inspect or override quota for consumers of a managed service). This subgroup exists only in the alpha track — not in GA or beta.

## Official documentation
- [Cloud Endpoints documentation home](https://cloud.google.com/endpoints/docs) — overview, quickstarts, and how-to guides.
- [Endpoints architecture overview](https://cloud.google.com/endpoints/docs/overview) — ESP vs ESPv2, supported platforms, Service Infrastructure.
- [Quickstart: OpenAPI on Compute Engine](https://cloud.google.com/endpoints/docs/openapi/get-started-compute-engine) — deploy a REST API fronted by ESP.
- [Quickstart: gRPC on Compute Engine (Docker)](https://cloud.google.com/endpoints/docs/grpc/get-started-compute-engine-docker) — deploy a gRPC API fronted by ESP.
- [Control API access (IAM)](https://cloud.google.com/endpoints/docs/openapi/control-api-access) — Endpoints IAM roles and the matching gcloud commands.
- [gcloud endpoints CLI reference](https://cloud.google.com/sdk/gcloud/reference/endpoints) — full command/flag reference.
- [gcloud beta endpoints CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/endpoints) — beta (and alpha) command variants.

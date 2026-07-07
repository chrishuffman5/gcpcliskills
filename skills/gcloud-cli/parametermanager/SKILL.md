---
name: gcloud-parametermanager
description: >-
  Parameter Manager via gcloud (`gcloud parametermanager`). Parameter Manager is a single source of truth to store, access and manage the lifecycle of your application parameters.
---

# gcloud parametermanager — Parameter Manager

## Overview
Parameter Manager is a single source of truth for storing, versioning, and accessing your application's configuration parameters. A parameter holds one or more immutable *versions* whose payload can be unstructured plaintext or structured JSON/YAML (up to 1 MiB). Payloads may embed `__REF__()` references to Secret Manager secrets that are resolved at render time, so you can keep config and secrets together without exposing the secret values. Reach for it when you need centralized, versioned, IAM-controlled application config — either `global` or in a specific region.

## Quick reference — common workflows

### Enable the API (prerequisite)
```bash
gcloud services enable parametermanager.googleapis.com
```

### 1. Create a parameter and add a plaintext version
```bash
# Create an unformatted (plaintext) global parameter
gcloud parametermanager parameters create my-parameter \
    --location=global \
    --parameter-format=unformatted

# Add a version with an inline payload
gcloud parametermanager parameters versions create v1 \
    --parameter=my-parameter \
    --location=global \
    --payload-data="DATABASE_URL=postgres://host:5432/mydb"

# Confirm the version exists
gcloud parametermanager parameters versions describe v1 \
    --parameter=my-parameter \
    --location=global
```

### 2. Create a structured (JSON) parameter from inline data or a file
```bash
gcloud parametermanager parameters create app-config \
    --location=global \
    --parameter-format=json

# From an inline JSON payload
gcloud parametermanager parameters versions create prod-v1 \
    --parameter=app-config \
    --location=global \
    --payload-data='{"db_host":"10.0.0.1","db_port":5432,"cache_ttl":300}'

# Or load the payload from a local file
gcloud parametermanager parameters versions create prod-v2 \
    --parameter=app-config \
    --location=global \
    --payload-data-from-file=config.json
```

### 3. Render a version (resolve Secret Manager references)
```bash
# render returns the full payload with any __REF__() secret references resolved
gcloud parametermanager parameters versions render prod-v1 \
    --parameter=app-config \
    --location=global

# Regional parameter
gcloud parametermanager parameters versions render prod-v1 \
    --parameter=app-config \
    --location=us-central1
```

### 4. List and inspect parameters and versions
```bash
# All parameters in a location
gcloud parametermanager parameters list --location=global

# All versions of a parameter
gcloud parametermanager parameters versions list \
    --parameter=my-parameter \
    --location=global

# Full version output includes the payload (basic returns metadata only)
gcloud parametermanager parameters versions describe v1 \
    --parameter=my-parameter \
    --location=global \
    --view=full
```

### 5. Disable and re-enable a version
```bash
# Disable — payload is never returned and render fails while disabled
gcloud parametermanager parameters versions update v1 \
    --parameter=my-parameter \
    --location=global \
    --disabled

# Re-enable
gcloud parametermanager parameters versions update v1 \
    --parameter=my-parameter \
    --location=global \
    --no-disabled
```

### 6. Create a CMEK-encrypted parameter, then clear the key
```bash
# The KMS key location must match the parameter location
gcloud parametermanager parameters create secure-config \
    --location=global \
    --parameter-format=json \
    --kms-key="projects/KMS_PROJECT_ID/locations/global/keyRings/MY_KEY_RING/cryptoKeys/MY_KEY"

# Revert to Google-managed encryption
gcloud parametermanager parameters update secure-config \
    --location=global \
    --clear-kms-key
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `parametermanager parameters` | [`parameters.md`](parameters.md) | 11 | Manage Parameter Manager parameter resources and their versions |

See [`index.md`](index.md) for a one-line index of all 11 commands.

## Common flags & tips
- **`--location` is effectively mandatory.** Every command needs a location, either passed as `--location=global` / `--location=REGION` or baked into a fully qualified resource name (`projects/*/locations/*/parameters/*`). There is no project-wide default; `list` requires `--location` explicitly.
- **`--parameter-format`** on `parameters create`/`update` is one of `json`, `yaml`, or `unformatted`. Set it at the parameter level; versions then carry payloads in that format.
- **Payload input is mutually exclusive** on `versions create`: supply exactly one of `--payload-data="..."` (inline) or `--payload-data-from-file=PATH` (local file, good for large or multiline JSON/YAML).
- **`describe` vs `render`:** `versions describe --view=full` returns the raw payload as stored (secret refs are *not* resolved); `versions render` resolves `__REF__()` Secret Manager references and returns the materialized payload. A disabled version forces `--view=basic` and makes `render` fail.
- **Enable/disable** with `versions update --disabled` / `--no-disabled` (the flag is `--[no-]disabled`).
- **CMEK:** set `--kms-key=...` (optionally with `--key-ring=...`) on create/update; remove it with `--clear-kms-key` on `update`. The key's location must match the parameter's location.
- **Labels:** `--labels` sets the full set on create; on `update` use `--update-labels`, `--remove-labels`, or `--clear-labels`.
- **`--request-id`** accepts a UUID for idempotent retries on mutating commands (create/update/delete).
- **Filtering and scripting:** `list` supports `--filter`, `--sort-by`, `--limit`, and `--uri`. Example — list only enabled versions:
  ```bash
  gcloud parametermanager parameters versions list \
      --parameter=my-parameter --location=global \
      --filter="disabled=false" \
      --format="table(name, disabled, createTime)"
  ```
- **Secret references** also require the caller (or parameter's identity) to hold `roles/secretmanager.secretAccessor` on the referenced secret(s) for `render` to succeed.

## Official documentation
- [Parameter Manager docs home](https://cloud.google.com/secret-manager/parameter-manager/docs) — product landing page and navigation.
- [Product overview](https://cloud.google.com/secret-manager/parameter-manager/docs/overview) — concepts, use cases, and comparison with Secret Manager.
- [Prepare your environment](https://cloud.google.com/secret-manager/parameter-manager/docs/prepare-environment) — API enablement, billing, and required IAM roles.
- [Access control](https://cloud.google.com/secret-manager/parameter-manager/docs/access-control) — Parameter Manager IAM roles and permissions.
- [Create a parameter](https://cloud.google.com/secret-manager/parameter-manager/docs/create-parameter) — create global and regional parameters.
- [Add a parameter version](https://cloud.google.com/secret-manager/parameter-manager/docs/add-parameter-version) — add versions and supply payload data.
- [Reference secrets in a parameter](https://cloud.google.com/secret-manager/parameter-manager/docs/reference-secrets-in-parameter) — embed Secret Manager secrets with `__REF__()`.
- [Render a parameter version](https://cloud.google.com/secret-manager/parameter-manager/docs/render-parameter-version) — resolve secret references and return the full payload.
- [Configure CMEK](https://cloud.google.com/secret-manager/parameter-manager/docs/cmek) — customer-managed encryption keys.
- [gcloud parametermanager reference](https://cloud.google.com/sdk/gcloud/reference/parametermanager) — full CLI command reference.

_Note: the gcloud reference documents only GA commands; there are no `gcloud beta parametermanager` or `gcloud alpha parametermanager` subgroups._

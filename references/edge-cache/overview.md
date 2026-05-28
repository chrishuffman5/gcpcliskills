# gcloud edge-cache — Media CDN

## Overview

`gcloud edge-cache` manages Media CDN resources — Google Cloud's media delivery
platform optimized for high-throughput egress workloads such as streaming video
and large file downloads. Reach for it to serve content from Google's global
edge-caching infrastructure close to users, reducing origin load and latency.
The CLI manages four resource types: **origins** (backend sources),
**services** (the CDN endpoint with routing/caching config), **keysets**
(signing keys for signed-request validation), and **operations** (long-running
async work). All resources are global (`--location=global`).

## Quick reference — common workflows

### 1. Enable the API and list existing resources

```bash
gcloud services enable networkservices.googleapis.com
gcloud services enable certificatemanager.googleapis.com   # for TLS/SSL certs on services

gcloud edge-cache services list
gcloud edge-cache origins list
```

### 2. Create an origin (Cloud Storage or public backend)

```bash
# Cloud Storage bucket origin (canonical gs:// form required)
gcloud edge-cache origins create my-origin \
    --origin-address="gs://my-bucket"

# Public backend with failover, retries, and HTTP/2
gcloud edge-cache origins create my-origin \
    --origin-address="origin.example.com" \
    --protocol=http2 \
    --max-attempts=3 \
    --retry-conditions=connect-failure,http-5xx \
    --failover-origin=my-backup-origin

gcloud edge-cache origins describe my-origin
```

### 3. Create or update a service via YAML import

Services have no `create` command — complex routing/caching config is managed
declaratively with `import` (creates if absent, updates if present).

```bash
# Export an existing service to YAML for editing
gcloud edge-cache services export my-service \
    --destination=my-service.yaml

# Import (create or update) a service from the edited YAML
gcloud edge-cache services import my-service \
    --source=my-service.yaml

# Verify the service and read its assigned IP addresses
gcloud edge-cache services describe my-service

# Toggle a top-level property directly (e.g. enable request logging)
gcloud edge-cache services update my-service \
    --enable-logging \
    --logging-sample-rate=1.0
```

### 4. Invalidate cached content

At least one of `--host`, `--path`, or `--tags` is required; combined filters
are treated as AND. Path prefixes use a trailing `*`.

```bash
# By cache tag and host
gcloud edge-cache services invalidate-cache my-service \
    --tags="status=404" --host="media.example.com"

# By path prefix
gcloud edge-cache services invalidate-cache my-service \
    --path="/static/*"

# Combine tag + path (AND)
gcloud edge-cache services invalidate-cache my-service \
    --tags="status=404" --path="/static/*"
```

### 5. Manage a keyset for signed requests

```bash
# Self-managed Ed25519 public key
gcloud edge-cache keysets create my-keyset \
    --public-key='id=key-1,value=BASE64PUBLICKEY'

# Google-managed key (dual-token setup)
gcloud edge-cache keysets create my-keyset \
    --public-key='id=key-1,managed=true'

# Secret Manager shared key
gcloud edge-cache keysets create my-keyset \
    --validation-shared-key='secret_version=projects/PROJECT/secrets/SECRET/versions/VERSION'

# update appends keys; to remove keys, re-import the full keyset omitting them
gcloud edge-cache keysets update my-keyset \
    --public-key='id=key-2,value=NEWPUBLICKEY'

gcloud edge-cache keysets list
gcloud edge-cache keysets describe my-keyset
```

### 6. Run and monitor async operations

```bash
gcloud edge-cache origins create my-origin \
    --origin-address="origin.example.com" --async

gcloud edge-cache operations list
gcloud edge-cache operations describe OPERATION
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `edge-cache keysets` | [`keysets.md`](keysets.md) | 7 | interact with and manage EdgeCacheKeyset resources |
| `edge-cache operations` | [`operations.md`](operations.md) | 2 | manage EdgeCache operations |
| `edge-cache origins` | [`origins.md`](origins.md) | 7 | interact with and manage EdgeCacheOrigin resources |
| `edge-cache services` | [`services.md`](services.md) | 7 | interact with and manage EdgeCacheService resources |

See [`index.md`](index.md) for a one-line index of all 23 GA commands.

## Common flags & tips

- **Resources are global.** Names resolve under `locations/global`; use
  `--location=global` (the default) or pass a fully qualified resource name.
- **Origins** point at one backend via `--origin-address` (FQDN, IPv4, IPv6, or
  `gs://bucketname`). Use `--protocol` (`http`, `http2`, `https`; default
  HTTP/2), `--max-attempts` (1–3), `--retry-conditions`, and `--failover-origin`
  to control cache-fill resilience; total attempts across an origin chain are
  capped at four.
- **Services are declarative.** There is no `services create` — use `import`
  with `--source` to create/update from YAML. `services update` only exposes
  top-level toggles: `--enable-logging`, `--logging-sample-rate` (0.0–1.0),
  `--require-tls`, `--edge-ssl-certificate` (up to 5), and
  `--edge-security-policy` (Cloud Armor EDGE policy).
- **`--require-tls`** needs at least one `--edge-ssl-certificate` attached.
- **Keysets** hold up to three public keys. `update` *appends* keys; to delete
  keys, `export` then `import` the full keyset omitting the unwanted entries.
- **Async:** create/update/import/delete accept `--async`; track the returned
  operation with `gcloud edge-cache operations describe`.
- **Backup/migrate:** every resource type supports `export`/`import` to YAML,
  which is the recommended way to version-control and replicate config.
- Useful list shaping:
  ```bash
  gcloud edge-cache services list --format="table(name, ipv4Addresses, ipv6Addresses)"
  gcloud edge-cache origins list --filter="originAddress~gs://" --uri
  ```

## beta / alpha

- `gcloud alpha edge-cache` mirrors the GA surface (keysets, operations,
  origins, services) on the alpha track; alpha commands may change without
  notice.
- No `gcloud beta edge-cache` surface is documented.

## Official documentation

- Media CDN docs home: https://cloud.google.com/media-cdn/docs — product
  landing page for all Media CDN guides.
- Product overview: https://cloud.google.com/media-cdn/docs/overview —
  architecture (Router / Cache / Cache Filler) and use cases.
- Quickstart: https://cloud.google.com/media-cdn/docs/quickstart — create a GCS
  origin, import a service YAML, test cache hit/miss; lists IAM roles and APIs.
- Origins concept guide: https://cloud.google.com/media-cdn/docs/origins —
  origin types, protocols, retry/failover, flex shielding.
- EdgeCacheKeyset REST reference:
  https://cloud.google.com/media-cdn/docs/reference/rest/v1/projects.locations.edgeCacheKeysets
  — keyset resource structure (Ed25519 public keys, shared secret keys).
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/edge-cache
  — full command/flag reference for the GA `edge-cache` group.
- gcloud alpha reference:
  https://cloud.google.com/sdk/gcloud/reference/alpha/edge-cache — alpha-track
  variant of the same subgroups.

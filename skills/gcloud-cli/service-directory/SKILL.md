---
name: gcloud-service-directory
description: >-
  Service Directory via gcloud (`gcloud service-directory`). Command groups for Service Directory — endpoints, locations, namespaces, services.
---

# gcloud service-directory — Service Directory

## Overview

Service Directory is Google Cloud's centralized registry for publishing, discovering, and
connecting services across any environment — hybrid, multi-cloud, and on-premises. It is the
single source of truth for service metadata and endpoint information. Resources form a
three-level, regional hierarchy: **namespaces** (logical containers for related services) →
**services** (named logical groups, e.g. an app or API) → **endpoints** (a concrete network
location: IP address + port). Reach for it when clients need to resolve where a service is
running without hard-coding addresses.

## Quick reference — common workflows

### 1. Full setup — namespace, service, endpoint

```bash
# Enable the API once per project
gcloud services enable servicedirectory.googleapis.com

# Create a namespace in a region
gcloud service-directory namespaces create my-namespace \
    --location=us-east1 --labels=env=prod

# Create a service inside the namespace
gcloud service-directory services create my-service \
    --namespace=my-namespace --location=us-east1 \
    --annotations=version=v1

# Register an endpoint (IP + port)
gcloud service-directory endpoints create my-endpoint \
    --service=my-service --namespace=my-namespace \
    --location=us-east1 --address=1.2.3.4 --port=8080
```

### 2. Resolve a service (look up endpoints)

```bash
# Return all registered endpoints for a service
gcloud service-directory services resolve my-service \
    --namespace=my-namespace --location=us-east1

# Narrow with a boolean endpoint filter and cap the result count
gcloud service-directory services resolve my-service \
    --namespace=my-namespace --location=us-east1 \
    --endpoint-filter="address=1.2.3.4" --max-endpoints=5
```

### 3. List and inspect resources

```bash
gcloud service-directory namespaces list --location=us-east1

gcloud service-directory services list \
    --namespace=my-namespace --location=us-east1

gcloud service-directory endpoints list \
    --service=my-service --namespace=my-namespace --location=us-east1

gcloud service-directory endpoints describe my-endpoint \
    --service=my-service --namespace=my-namespace --location=us-east1
```

### 4. Update an endpoint's address/port

```bash
gcloud service-directory endpoints update my-endpoint \
    --service=my-service --namespace=my-namespace \
    --location=us-east1 --address=10.0.0.5 --port=9090 \
    --annotations=updated=true
```

### 5. Manage IAM on a namespace

```bash
# Grant viewer access
gcloud service-directory namespaces add-iam-policy-binding my-namespace \
    --location=us-east1 --role=roles/servicedirectory.viewer \
    --member=user:dev@example.com

# Inspect the policy
gcloud service-directory namespaces get-iam-policy my-namespace \
    --location=us-east1

# Revoke the binding
gcloud service-directory namespaces remove-iam-policy-binding my-namespace \
    --location=us-east1 --role=roles/servicedirectory.viewer \
    --member=user:dev@example.com
```

### 6. Tear down in order (endpoints → service → namespace)

```bash
gcloud service-directory endpoints delete my-endpoint \
    --service=my-service --namespace=my-namespace --location=us-east1

gcloud service-directory services delete my-service \
    --namespace=my-namespace --location=us-east1

gcloud service-directory namespaces delete my-namespace \
    --location=us-east1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `service-directory endpoints` | [`endpoints.md`](endpoints.md) | 5 | manage Service Directory endpoints |
| `service-directory locations` | [`locations.md`](locations.md) | 2 | manage Service Directory locations |
| `service-directory namespaces` | [`namespaces.md`](namespaces.md) | 9 | manage Service Directory namespaces |
| `service-directory services` | [`services.md`](services.md) | 10 | manage Service Directory services |

See [`index.md`](index.md) for a one-line index of all 26 GA commands.

## Common flags & tips

- **Everything is regional.** Almost every command requires `--location` (a region such as
  `us-east1`). The exception is `locations list`, which takes no flags, and
  `locations describe LOCATION`, which takes the region as a positional argument.
- **Context flags chain down the hierarchy.** Services need `--namespace` + `--location`;
  endpoints need `--service` + `--namespace` + `--location`. Alternatively, pass a fully
  qualified resource name as the positional argument and omit the context flags.
- **Resource IDs** must be 1–63 chars, lowercase, matching `[a-z](?:[-a-z0-9]{0,61}[a-z0-9])?`.
- **`--labels`** apply to namespaces only; **`--annotations`** (free-form KEY=VALUE pairs)
  apply to services and endpoints. Endpoint annotations cap at 512 chars; service annotations
  at 2000.
- **Endpoint addressing:** `--address` accepts IPv4 or IPv6; `--port` must be in `[0, 65535]`.
  Attach a VPC with `--network=projects/<PROJECT_NUM>/locations/global/networks/<NAME>` at
  create time.
- **Resolve vs. list:** `services resolve` returns the service plus its endpoints in one call
  (use `--endpoint-filter` / `--max-endpoints`); `endpoints list` enumerates endpoint resources
  with the standard `--filter` / `--sort-by` / `--page-size` flags.
- **`--format` / `--filter` examples:**
  ```bash
  # Just the endpoint addresses for a service
  gcloud service-directory endpoints list --service=my-service \
      --namespace=my-namespace --location=us-east1 \
      --format="value(address)"

  # Namespaces tagged env=prod
  gcloud service-directory namespaces list --location=us-east1 \
      --filter="labels.env=prod"
  ```
- **IAM scope:** policy bindings can be set at the namespace or service level via the
  `add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy`
  commands. Common roles: `roles/servicedirectory.admin`, `.editor`, `.viewer`,
  `.networkAttacher`, `.pscAuthorizedService`.

## beta / alpha

Both `gcloud beta service-directory` and `gcloud alpha service-directory` exist and expose the
same four command groups (endpoints, locations, namespaces, services) with the same core CRUD
and IAM operations as GA. The beta/alpha tracks surface preview API fields ahead of promotion;
the underlying API exposes a `v1beta1` version of `servicedirectory.googleapis.com` for clients
needing pre-release fields. No GA-only command gaps were identified — feature parity is complete
at the command-group level. Commands on these tracks may change without notice.

## Official documentation

- [Service Directory docs home](https://cloud.google.com/service-directory/docs) — navigation hub for all guides.
- [Overview](https://cloud.google.com/service-directory/docs/overview) — concepts and the namespace/service/endpoint model.
- [Configuring Service Directory](https://cloud.google.com/service-directory/docs/configuring-service-directory) — how-to with gcloud command sequences.
- [Access control (IAM)](https://cloud.google.com/service-directory/docs/access-control) — predefined roles and their permissions.
- [REST API reference](https://cloud.google.com/service-directory/docs/reference/rest) — `servicedirectory.googleapis.com` v1 / v1beta1.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/service-directory) — full command/flag reference.

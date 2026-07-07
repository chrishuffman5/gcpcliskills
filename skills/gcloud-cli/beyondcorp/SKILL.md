---
name: gcloud-beyondcorp
description: >-
  BeyondCorp Enterprise (Chrome Enterprise Premium) via gcloud (`gcloud beyondcorp`). Manage Beyondcorp resources — operations, security-gateways.
---

# gcloud beyondcorp — BeyondCorp Enterprise (Chrome Enterprise Premium)

## Overview

`gcloud beyondcorp` manages the **Security Gateway** resources of Google Cloud's BeyondCorp Enterprise zero-trust access platform (now branded **Chrome Enterprise Premium**). A security gateway proxies and routes traffic to internal, on-premises, or external applications based on user identity, device posture, and context — without a traditional VPN. Reach for it when you need to publish private or SaaS applications behind a context-aware, identity-driven gateway. The GA surface covers two groups: `security-gateways` (with a nested `applications` subgroup) and `operations`.

## Quick reference — common workflows

### 1. Enable the API and create a security gateway

```bash
gcloud services enable beyondcorp.googleapis.com

# Security gateways support only the global location
gcloud beyondcorp security-gateways create my-gateway \
    --location=global \
    --display-name="My Security Gateway"

# Create asynchronously, then poll the long-running operation
gcloud beyondcorp security-gateways create my-gateway \
    --location=global \
    --display-name="My Security Gateway" \
    --async
gcloud beyondcorp operations list --location=global
```

### 2. List and describe security gateways

```bash
gcloud beyondcorp security-gateways list --location=global

gcloud beyondcorp security-gateways describe my-gateway \
    --location=global
```

### 3. Register an application on a security gateway

```bash
# endpoint-matchers maps hostnames/ports to this application (OR logic across matchers)
gcloud beyondcorp security-gateways applications create my-app \
    --security-gateway=my-gateway \
    --location=global \
    --display-name="My Application" \
    --endpoint-matchers=hostname=myapp.internal.example.com,ports=[443]

gcloud beyondcorp security-gateways applications list \
    --security-gateway=my-gateway \
    --location=global

gcloud beyondcorp security-gateways applications describe my-app \
    --security-gateway=my-gateway \
    --location=global
```

### 4. Update a gateway and its regional hubs

```bash
gcloud beyondcorp security-gateways update my-gateway \
    --location=global \
    --display-name="Updated Gateway Name"

# Replace the regional data-path hubs map (key = GCP region)
gcloud beyondcorp security-gateways update my-gateway \
    --location=global \
    --hubs='{"us-central1": {}}'
```

### 5. Manage IAM policy on a gateway or application

```bash
gcloud beyondcorp security-gateways get-iam-policy my-gateway \
    --location=global \
    --project=my-project-id

gcloud beyondcorp security-gateways set-iam-policy my-gateway policy.json \
    --location=global

gcloud beyondcorp security-gateways applications get-iam-policy my-app \
    --security-gateway=my-gateway \
    --location=global \
    --project=my-project-id
```

### 6. Delete an application and gateway

```bash
# Dry-run first: --validate-only does not alter the resource
gcloud beyondcorp security-gateways applications delete my-app \
    --security-gateway=my-gateway \
    --location=global \
    --validate-only

gcloud beyondcorp security-gateways applications delete my-app \
    --security-gateway=my-gateway \
    --location=global

gcloud beyondcorp security-gateways delete my-gateway \
    --location=global
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `operations` | [operations.md](operations.md) | describe, list | Track long-running BeyondCorp operations |
| `security-gateways` | [security-gateways.md](security-gateways.md) | create, delete, describe, list, update, get-iam-policy, set-iam-policy | Manage zero-trust security gateways |
| `security-gateways applications` | [security-gateways.md](security-gateways.md) | create, delete, describe, list, update, get-iam-policy, set-iam-policy | Manage applications published behind a gateway |

## Common flags & tips

- **Location is always `global`.** Every `security-gateways` and `applications` command requires `--location=global`; no other location is supported.
- **Application scoping.** Every `applications` command requires `--security-gateway=GATEWAY` in addition to `--location` (or a fully qualified resource name).
- **Async operations.** `create`, `update`, and `delete` accept `--async` to return immediately; track progress with `gcloud beyondcorp operations list --location=global` and `gcloud beyondcorp operations describe OPERATION --location=global`.
- **Dry runs.** `delete` supports `--validate-only` to validate the request without altering the resource.
- **Idempotency.** Mutating commands accept `--request-id` (a valid non-zero UUID) so retries are not double-applied.
- **Endpoint matchers.** Use shorthand `--endpoint-matchers=hostname=HOST,ports=[443]`, or pass JSON / a YAML/JSON file for multiple matchers.
- **Update list fields.** On `security-gateways update`, hubs can be set with `--hubs`, `--update-hubs`, `--remove-hubs`, or `--clear-hubs`; on `applications update`, endpoint matchers and upstreams each have matching `--add-`, `--remove-`, and `--clear-` variants.
- **Filtering / format.** `list` and `get-iam-policy` support `--filter`, `--limit`, `--sort-by`, `--page-size`; `list` also supports `--uri`. Example:
  ```bash
  gcloud beyondcorp security-gateways list --location=global \
      --filter="displayName~prod" --format="table(name, displayName, state)"
  ```

## beta / alpha

The brand surface is broader under beta/alpha than the GA `gcloud beyondcorp`:

- **`gcloud beta beyondcorp`** adds the connector-based architecture:
  - `app` — `connections`, `connectors`, `gateways`, `operations` (App Connectors / App Connections for routing private and on-prem traffic).
  - `client-connector` *(deprecated)* — `gateways` and `services` for context-aware access to non-web apps.
  - `security-gateways` — same surface as GA.
- **`gcloud alpha beyondcorp`** exposes only `app` (`connections`, `connectors`, `operations`); no `security-gateways` or `client-connector`. Alpha commands carry a "may change without notice" warning.

Summary: GA = security gateways only; beta adds the App Connector model; alpha = App Connectors/Connections only.

## Official documentation

- [Chrome Enterprise Premium docs home](https://cloud.google.com/beyondcorp-enterprise/docs) — product home for Zero Trust access, DLP, threat protection, and context-aware access (redirects to docs.cloud.google.com).
- [Product overview](https://cloud.google.com/beyondcorp-enterprise/docs/overview) — the three pillars: Data Loss Prevention, Threat Protection, Context-Aware Access.
- [Manage a security gateway](https://cloud.google.com/beyondcorp-enterprise/docs/manage-security-gateway) — create, update hubs, list, describe, and delete gateways and their applications.
- [App Connector overview](https://cloud.google.com/beyondcorp-enterprise/docs/app-connector-overview) — securing non-Google-Cloud and on-prem apps via the connector model (beta/alpha `app` surface).
- [BeyondCorp IAM roles](https://cloud.google.com/iam/docs/roles-permissions/beyondcorp) — predefined `roles/beyondcorp.*` roles (admin, editor, viewer, subscriptionAdmin, subscriptionViewer).
- [gcloud beyondcorp reference](https://cloud.google.com/sdk/gcloud/reference/beyondcorp) — full GA command and flag reference.

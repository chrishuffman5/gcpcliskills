---
name: gcloud-services
description: >-
  Service Usage via gcloud (`gcloud services`). List, enable and disable APIs and services — api-keys, operations, peered-dns-domains, vpc-peerings.
---

# gcloud services — Service Usage

## Overview

`gcloud services` is the Service Usage front door for **enabling and disabling Google Cloud APIs on a project** — the single prerequisite step that every other gcloud service group depends on. Before you can use Compute Engine, Cloud SQL, BigQuery, Pub/Sub, or any other API, that API must first be enabled with `gcloud services enable <api>.googleapis.com`. Beyond enable/disable, this group lists available and enabled services, manages API keys, and configures private service access (VPC peerings and peered DNS domains). Service Usage itself is enabled by default in every project, so these commands work out of the box.

> **This is how you turn APIs on and off for a project.** Almost every other reference in this skill assumes the relevant API is already enabled here first (e.g. `gcloud services enable sqladmin.googleapis.com` before using Cloud SQL).

## Quick reference — common workflows

### Enable one or more APIs for a project (the universal prerequisite)
```bash
# Enable a single API
gcloud services enable compute.googleapis.com

# Enable several APIs at once
gcloud services enable compute.googleapis.com storage.googleapis.com bigquery.googleapis.com

# Enable without blocking (returns an operation immediately)
gcloud services enable run.googleapis.com --async

# Enable an API on a specific project (not the active one)
gcloud services enable pubsub.googleapis.com --project=my-project
```

### List and audit what's enabled
```bash
# Services currently enabled (this is the default mode)
gcloud services list --enabled

# Everything available to enable (includes already-enabled services)
gcloud services list --available

# Audit another project, filtering by name
gcloud services list --enabled --project=my-other-project --filter="name:bigquery"
```

### Disable an API (with dependency handling)
```bash
# Disable a service; the call warns/blocks if other enabled services depend on it
gcloud services disable bigquery.googleapis.com

# Force-disable, also disabling dependent services (and overriding the
# recently-used / recently-enabled guard rails)
gcloud services disable bigquery.googleapis.com --force
```

### Create and manage API keys
```bash
# Create an IP-restricted server key
gcloud services api-keys create --display-name="My Server Key" --allowed-ips=203.0.113.10

# Create a key restricted to a specific API
gcloud services api-keys create --display-name="Maps Key" \
    --api-target=service=maps-backend.googleapis.com

# List keys, then fetch the usable key string for a key ID
gcloud services api-keys list
gcloud services api-keys get-key-string 1234

# Tighten restrictions later; soft-delete (recoverable 30 days); undelete
gcloud services api-keys update 1234 --allowed-ips=203.0.113.10,203.0.113.20
gcloud services api-keys delete 1234
gcloud services api-keys undelete 1234
```

### Track an async operation
```bash
# Capture the operation name from an --async call, then describe or block on it
gcloud services operations describe operations/abc
gcloud services operations wait operations/abc
```

### Configure VPC private service access (peering)
```bash
# Connect a network to a producer service using pre-allocated IP ranges
gcloud services vpc-peerings connect --network=my-vpc \
    --service=servicenetworking.googleapis.com --ranges=my-allocated-range

# List peerings, then update the ranges for an existing connection
gcloud services vpc-peerings list --network=my-vpc
gcloud services vpc-peerings update --network=my-vpc \
    --service=servicenetworking.googleapis.com --ranges=my-allocated-range,my-second-range

# Enable / inspect VPC Service Controls on the peering
gcloud services vpc-peerings enable-vpc-service-controls --network=my-vpc \
    --service=servicenetworking.googleapis.com
gcloud services vpc-peerings get-vpc-service-controls --network=my-vpc \
    --service=servicenetworking.googleapis.com
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| _(top-level)_ | [`_commands.md`](_commands.md) | 3 | `enable`, `disable`, `list` services for a project |
| `services api-keys` | [`api-keys.md`](api-keys.md) | 8 | Manage API keys |
| `services operations` | [`operations.md`](operations.md) | 2 | Describe / wait on long-running Service Usage operations |
| `services peered-dns-domains` | [`peered-dns-domains.md`](peered-dns-domains.md) | 3 | Peered DNS domains for private service connections |
| `services vpc-peerings` | [`vpc-peerings.md`](vpc-peerings.md) | 9 | VPC peerings to producer services (incl. VPC Service Controls + operations) |

See [`index.md`](index.md) for the one-line index of all 25 GA commands.

## Common flags & tips

- **Service names are API hostnames.** Enable/disable always take the fully qualified form, e.g. `compute.googleapis.com`, `run.googleapis.com`, `sqladmin.googleapis.com`. Find the exact name with `gcloud services list --available --filter="name:<keyword>"`.
- **`--async`** is available on `enable`, `disable`, the `api-keys` mutating commands (`create`/`update`/`delete`/`undelete`), and the `vpc-peerings` mutating commands. It returns an operation name immediately; resolve it with `gcloud services operations describe|wait`.
- **`--force` on `disable`** also disables dependent services and overrides the guard rails for services used in the last 30 days or enabled in the last 3 days — use deliberately.
- **`gcloud services list` defaults to `--enabled`.** Pass `--available` for the catalog of enable-able APIs. Both modes support `--filter`, `--limit`, `--page-size` (default 200), and `--sort-by`.
- **API key IDs vs. key strings.** Commands take the key ID (or the fully qualified `projects/PROJECT/locations/global/keys/ID` name); `get-key-string` returns the actual secret string used in API calls, and `lookup KEY_STRING` reverses a string back to its resource name. `list --show-deleted` surfaces keys soft-deleted in the last 30 days.
- **VPC peering scope.** `vpc-peerings` commands require `--network` and default `--service` to `servicenetworking.googleapis.com`; `--ranges` references pre-allocated IP range *names* (create them first with `gcloud compute addresses`).
- **Useful formatting:**
  ```bash
  gcloud services list --enabled --format="value(config.name)"
  gcloud services list --available --filter="config.name~run" --format="table(config.name, config.title)"
  ```

## beta / alpha

Capabilities beyond GA `gcloud services` (see the gcloud beta/alpha reference URLs in `sources.md`):

- **`gcloud beta services identity`** — manage service identities; `create` provisions a service identity for a consumer (common pre-step before granting IAM to managed services like Cloud Run or Pub/Sub). No GA equivalent.
- **`gcloud beta services groups`** — view service group information.
- **`gcloud beta services policies`** — get/update consumer policies and the effective policy.
- **`gcloud beta services mcp`** — list, enable, and disable MCP endpoints.
- **`gcloud alpha services quota`** — manage service consumer quota overrides (`create`/`delete`/`list`/`update`). Alpha only.

For everyday enable/disable workflows the GA commands are sufficient; reach for beta/alpha only for service identities, consumer policies, MCP endpoints, or quota overrides.

## Official documentation

- [Service Usage docs home](https://cloud.google.com/service-usage/docs) — product landing page for listing and managing APIs/services.
- [Service Usage overview](https://cloud.google.com/service-usage/docs/overview) — what Service Usage is and its key concepts.
- [Enable and disable APIs](https://cloud.google.com/service-usage/docs/enable-disable) — how to enable/disable services via console, gcloud, or REST.
- [List services](https://cloud.google.com/service-usage/docs/list-services) — listing enabled vs. available services.
- [Access control (IAM)](https://cloud.google.com/service-usage/docs/access-control) — roles like `serviceUsageAdmin`, `serviceUsageConsumer`, `apiKeysAdmin`.
- [API keys overview](https://cloud.google.com/api-keys/docs/overview) — what API keys are and security best practices.
- [Configure private services access](https://cloud.google.com/vpc/docs/configure-private-services-access) — VPC peering setup behind `vpc-peerings`.
- [gcloud services CLI reference](https://cloud.google.com/sdk/gcloud/reference/services) — full command/flag reference (GA).

---
name: gcloud-looker
description: >-
  Looker (Google Cloud core) via gcloud (`gcloud looker`). Manage Looker resources — backups, instances, operations, regions.
---

# gcloud looker — Looker (Google Cloud core)

## Overview
`gcloud looker` provisions and manages **Looker (Google Cloud core)** instances — Google Cloud's fully managed, cloud-native business intelligence platform for self-service data exploration and embedded analytics. Use it to create and configure Looker instances, manage their backups, run export/import migrations, and track the long-running operations those actions kick off. This is the SaaS instance model (distinct from the original self-hosted Looker); instance creation is asynchronous and typically takes ~30 minutes, so `--async` is recommended.

## Quick reference — common workflows

### Create a new instance
```bash
# Enable the API first (one-time per project)
gcloud services enable looker.googleapis.com

# See where you can deploy
gcloud looker regions list

# Create the instance — always use --async (creation takes ~30 min)
gcloud looker instances create my-looker-instance \
    --region=us-central1 \
    --edition=core-standard \
    --oauth-client-id=MY_OAUTH_CLIENT_ID \
    --oauth-client-secret=MY_OAUTH_CLIENT_SECRET \
    --async

# Poll the create operation until it finishes
gcloud looker operations list --region=us-central1
gcloud looker operations describe OPERATION_ID --region=us-central1
```

### Inspect instances
```bash
# List (use --limit / --filter to narrow)
gcloud looker instances list --region=us-central1 --limit=5

# Human-readable summary
gcloud looker instances describe my-looker-instance --region=us-central1

# Full metadata as JSON
gcloud looker instances describe my-looker-instance --region=us-central1 --format=json
```

### Back up and restore
```bash
# Create a manual backup (both --instance and --region are required)
gcloud looker backups create --instance=my-looker-instance --region=us-central1

# List backups for the instance
gcloud looker backups list --instance=my-looker-instance --region=us-central1 --limit=5

# Restore the instance from a backup (overwrites current data)
gcloud looker instances restore my-looker-instance \
    --backup="7e504e66-c389-4d8d-bca7-f710c6d96567" \
    --region=us-central1 \
    --async
```

### Export / import (migration or DR)
```bash
# Export to GCS — both --target-gcs-uri and --kms-key are required;
# grant the Looker Service Agent the Storage Object Creator role on the bucket.
gcloud looker instances export my-looker-instance \
    --region=us-central1 \
    --target-gcs-uri='gs://my-bucket/looker-export' \
    --kms-key='projects/MY_PROJECT/locations/us-central1/keyRings/my-ring/cryptoKeys/my-key'

# Import into an existing instance
gcloud looker instances import my-looker-instance \
    --region=us-central1 \
    --source-gcs-uri='gs://my-bucket/looker-export'

# Cancel an in-progress export/import operation
gcloud looker operations cancel OPERATION_ID --region=us-central1
```

### Update settings (maintenance window, user seats, custom domain)
```bash
# Schedule a weekly maintenance window (UTC)
gcloud looker instances update my-looker-instance \
    --region=us-central1 \
    --maintenance-window-day=sunday \
    --maintenance-window-time='23:00' \
    --async

# Add user seats (up to 50 total across viewer/standard/developer)
gcloud looker instances update my-looker-instance \
    --region=us-central1 \
    --add-viewer-users=10 \
    --add-developer-users=2

# Set a custom domain and restrict email-deliverable domains
gcloud looker instances update my-looker-instance \
    --region=us-central1 \
    --custom-domain=looker.mycompany.com \
    --allowed-email-domains=mycompany.com
```

### Restart or delete
```bash
gcloud looker instances restart my-looker-instance --region=us-central1 --async
gcloud looker instances delete  my-looker-instance --region=us-central1 --async
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `looker backups` | [`backups.md`](backups.md) | 4 | Create, delete, describe, and list backups of a Looker instance |
| `looker instances` | [`instances.md`](instances.md) | 9 | Create, update, restart, delete, restore, export/import, and describe/list instances |
| `looker operations` | [`operations.md`](operations.md) | 3 | List, describe, and cancel long-running Looker operations |
| `looker regions` | [`regions.md`](regions.md) | 1 | List available Looker regions |

See [`index.md`](index.md) for a one-line index of all 17 commands.

## Common flags & tips
- **Region is pervasive.** Most commands take `--region`; you can avoid repeating it by setting `gcloud config set looker/region us-central1`. `--region` on the command line overrides that property. `regions list` shows valid values.
- **Always go async for mutations.** `instances create` *fails* without `--async`. `restore`, `restart`, `delete`, and `update` also accept `--async` — pair them with `gcloud looker operations list` / `describe` to track progress, and `operations cancel` to stop an in-flight export/import.
- **Backups need both flags.** `backups create` and `backups list` require `--instance` *and* `--region` (no positional instance). `backups delete` / `backups describe` take the backup ID positionally plus `--instance`.
- **Edition is required at create.** Pick from the `--edition` enum, e.g. `core-standard`, `core-standard-annual`, `core-enterprise-annual`, `core-embed-annual`, or the `core-trial*` / `nonprod-*` variants.
- **CMEK / export.** `instances export` requires `--kms-key` (full key resource name) and `--target-gcs-uri`. For periodic exports, configure on `update` with `--periodic-export-gcs-uri`, `--periodic-export-kms-key`, and `--periodic-export-start-time` (clear with `--clear-periodic-export-config`).
- **Networking.** At create time, choose public IP (`--public-ip-enabled` / `--no-public-ip-enabled`), private IP (`--private-ip-enabled` with `--consumer-network` / `--reserved-range`), or Private Service Connect (`--psc-enabled` with `--psc-allowed-vpcs`). PSC settings can be adjusted later on `update`.
- **Filtering & formatting.** `list` commands support `--filter`, `--sort-by`, `--limit`, and `--uri`. Examples:
  - `gcloud looker instances list --region=us-central1 --format="table(name,state,lookerVersion)"`
  - `gcloud looker backups list --instance=my-looker-instance --region=us-central1 --filter="state=ACTIVE"`

## beta / alpha
- `gcloud alpha looker` exposes the same four command groups (backups, instances, operations, regions) as GA and may surface new flags before promotion.
- There are no documented alpha- or beta-only flags: notable capabilities (`--psc-enabled`, `--fips-enabled`, `--kms-key`, periodic export, PSC service attachments, controlled egress) are all present on the GA surface. Use GA `gcloud looker` for production.

## Official documentation
- [Looker (Google Cloud core) overview](https://cloud.google.com/looker/docs/looker-core-overview) — product docs home: editions, capabilities, and setup process.
- [Create a Looker (Google Cloud core) instance](https://cloud.google.com/looker/docs/looker-core-instance-create) — prerequisites, required API, IAM roles, and create commands.
- [Back up and restore](https://cloud.google.com/looker/docs/looker-core-backup-restore) — automatic (24h) and manual backups, 30-day retention, and restore caveats.
- [Maintenance windows and deny periods](https://cloud.google.com/looker/docs/looker-core-maintenance) — scheduling maintenance via CLI or console.
- [Instance setup](https://cloud.google.com/looker/docs/looker-core-instance-setup) — post-creation LookML, authentication, and user management.
- [IAM roles for Looker](https://cloud.google.com/iam/docs/roles-permissions/looker) — `roles/looker.*` predefined roles and permissions.
- [Looker Application API reference](https://cloud.google.com/looker/docs/reference/looker-api/latest) — v4.0 JSON REST API for programmatic access.
- [gcloud looker CLI reference](https://cloud.google.com/sdk/gcloud/reference/looker) — full command/flag reference.

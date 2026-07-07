---
name: gcloud-asset
description: >-
  Cloud Asset Inventory via gcloud (`gcloud asset`). Manage the Cloud Asset Inventory — feeds, operations, saved-queries.
---

# gcloud asset — Cloud Asset Inventory

## Overview

Cloud Asset Inventory is a global metadata inventory service for Google Cloud. Use `gcloud asset` to view, search, export, analyze, and monitor asset metadata — resource configurations, IAM policies, org policies, access policies, OS inventory, and resource relationships — across projects, folders, and organizations. Reach for it when you need a point-in-time snapshot of your estate, ad-hoc search across a scope, IAM access analysis, or real-time change notifications via Pub/Sub.

## Quick reference — common workflows

### Enable the API and grant access

```bash
gcloud services enable cloudasset.googleapis.com

# Grant the viewer role so an analyst can search/list/export
gcloud projects add-iam-policy-binding my-project \
    --member='user:analyst@example.com' \
    --role='roles/cloudasset.viewer'
```

### List or export an asset snapshot

```bash
# Inline snapshot of Compute disks at a point in time
gcloud asset list \
    --project='my-project' \
    --asset-types='compute.googleapis.com/Disk' \
    --content-type='resource' \
    --snapshot-time='2024-01-15T00:00:00Z'

# Export full resource metadata to Cloud Storage (long-running)
gcloud asset export \
    --project='my-project' \
    --output-path='gs://my-bucket/snapshots/export.json' \
    --content-type='resource'

# Export to BigQuery, overwriting the table if present
gcloud asset export \
    --project='my-project' \
    --content-type='resource' \
    --bigquery-table='projects/my-project/datasets/inventory/tables/assets' \
    --output-bigquery-force

# Poll the operation returned by export (name is printed by the export command)
gcloud asset operations describe OPERATION_NAME
```

### Search resources across a scope

```bash
# Compute instances whose name starts with "prod", sorted by name
gcloud asset search-all-resources \
    --scope='organizations/123456' \
    --query='name:prod*' \
    --asset-types='compute.googleapis.com/Instance' \
    --order-by='name'

# Resources carrying a specific label
gcloud asset search-all-resources \
    --scope='projects/my-project' \
    --query='labels.env:production'
```

### Search and analyze IAM policies

```bash
# Find IAM bindings that mention a user across the org
gcloud asset search-all-iam-policies \
    --scope='organizations/123456' \
    --query='policy:alice@example.com'

# Who can actAs a service account? Expand groups and roles
gcloud asset analyze-iam-policy \
    --organization='YOUR_ORG_ID' \
    --full-resource-name='//iam.googleapis.com/projects/my-project/serviceAccounts/sa@my-project.iam.gserviceaccount.com' \
    --permissions='iam.serviceAccounts.actAs' \
    --expand-groups \
    --expand-roles

# Same analysis, written asynchronously to BigQuery (for large orgs)
gcloud asset analyze-iam-policy-longrunning \
    --organization='YOUR_ORG_ID' \
    --identity='user:alice@example.com' \
    --bigquery-dataset='projects/my-project/datasets/iam_analysis' \
    --bigquery-table-prefix='analysis'
```

### Monitor asset changes with a real-time feed

```bash
# Pub/Sub topic for change notifications
gcloud pubsub topics create asset-changes

# Watch Compute Network and Disk changes in a project
gcloud asset feeds create my-feed \
    --project='my-project' \
    --asset-types='compute.googleapis.com/Network,compute.googleapis.com/Disk' \
    --content-type='resource' \
    --pubsub-topic='projects/my-project/topics/asset-changes'

# Inspect, extend, then remove the feed
gcloud asset feeds list --project='my-project'
gcloud asset feeds update my-feed --project='my-project' \
    --add-asset-types='pubsub.googleapis.com/Topic'
gcloud asset feeds delete my-feed --project='my-project'
```

### Analyze a project move

```bash
# Check what would break before moving a project to another org
gcloud asset analyze-move --project='my-project' \
    --destination-organization='ORGANIZATION_ID'

# Only surface hard blockers (skip warnings)
gcloud asset analyze-move --project='my-project' \
    --destination-folder='FOLDER_ID' \
    --blockers-only=true
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `asset` (top-level) | [`_commands.md`](_commands.md) | 13 | analyze, export, list, query, search, history, effective IAM |
| `asset feeds` | [`feeds.md`](feeds.md) | 5 | manage real-time Pub/Sub change feeds |
| `asset operations` | [`operations.md`](operations.md) | 1 | describe long-running operations (e.g. export) |
| `asset saved-queries` | [`saved-queries.md`](saved-queries.md) | 5 | manage reusable saved queries |

See [`index.md`](index.md) for the one-line index of all 24 GA commands.

## Common flags & tips

- **Scope vs. parent flags.** Search commands (`search-all-resources`, `search-all-iam-policies`) and org-policy analysis take a single `--scope` (e.g. `projects/foo-bar`, `folders/1234567`, `organizations/123456`). Snapshot/export/feed/saved-query commands instead take exactly one of `--project`, `--folder`, or `--organization`. The analyze-iam-policy commands use `--project | --folder | --organization`.
- **`--content-type`** (on `list`, `export`, `get-history`, `feeds create/update`) must be one of: `resource`, `iam-policy`, `org-policy`, `access-policy`, `os-inventory`, `relationship`. Omitting it returns only asset name and type.
- **`--asset-types`** accepts a comma-separated list of types such as `compute.googleapis.com/Disk`; search commands also accept RE2 regular expressions (e.g. `compute.googleapis.com.*`). See the supported-asset-types reference for valid values.
- **Snapshots and history.** `--snapshot-time` accepts a current or past timestamp; `get-history --start-time` must be within the last 35 days. Run `gcloud topic datetimes` for accepted time formats.
- **Sorting.** `--order-by` is server-side and limited to specific singular fields (`name`, `assetType`, `project`, etc.); the global `--sort-by` is client-side and works on any output field.
- **Async exports.** `export` and `analyze-iam-policy-longrunning` are long-running; capture the returned operation name and poll with `gcloud asset operations describe OPERATION_NAME`.
- **Billing a different project.** When operating on a project other than the one you want billed, use the global `--billing-project` flag or a service account.
- **Filter/format example:** `gcloud asset search-all-resources --scope='projects/my-project' --format='table(name, assetType, location)'`.

## beta / alpha

All 24 commands listed in [`index.md`](index.md) are GA. `gcloud beta asset` and `gcloud alpha asset` expose the same command names (documented on the beta/alpha reference pages) and exist for early access to future flags; no capability is exclusively beta or alpha at the time of writing. Check the per-command reference pages for release-level notes when a newer flag is needed.

## Official documentation

- [Cloud Asset Inventory overview](https://cloud.google.com/asset-inventory/docs/overview) — what CAI is and its core capabilities (product docs home).
- [Access control](https://cloud.google.com/asset-inventory/docs/access-control) — IAM roles and permissions required for all CAI operations.
- [Export to Cloud Storage](https://cloud.google.com/asset-inventory/docs/exporting-to-cloud-storage) — how to export asset snapshots with `gcloud asset export`.
- [Search resources](https://cloud.google.com/asset-inventory/docs/searching-resources) — query syntax for `gcloud asset search-all-resources`.
- [Monitor asset changes](https://cloud.google.com/asset-inventory/docs/monitoring-asset-changes) — create and manage real-time Pub/Sub feeds.
- [Analyze IAM policy](https://cloud.google.com/asset-inventory/docs/analyzing-iam-policy) — IAM access analysis with `gcloud asset analyze-iam-policy`.
- [Supported asset types](https://cloud.google.com/asset-inventory/docs/supported-asset-types) — all supported asset and relationship types.
- [gcloud asset CLI reference](https://cloud.google.com/sdk/gcloud/reference/asset) — full reference for the `asset` command group.

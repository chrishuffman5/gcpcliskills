---
name: gcloud-dataplex
description: >-
  Dataplex via gcloud (`gcloud dataplex`). Manage Dataplex resources — aspect-types, assets, content, datascans, encryption-config, entries, entry-groups, entry-types.
---

# gcloud dataplex — Dataplex

## Overview

Dataplex (rebranded to "Knowledge Catalog" in April 2026 — the `gcloud dataplex` commands and APIs
are unchanged) is Google Cloud's unified platform for **data lakes, governance, and catalog**. It
organizes distributed data into **lakes** → **zones** → **assets** (Cloud Storage buckets and
BigQuery datasets), automates metadata discovery, runs **data quality / profile / discovery /
documentation scans** (`datascans`), and provides a metadata catalog of entries, entry types,
aspect types, entry groups, and glossaries for cross-org governance. Reach for it when you need to
catalog, profile, quality-check, or apply consistent governance across data spread over many
projects and storage services.

## Quick reference — common workflows

**Enable the API (once per project):**
```bash
gcloud services enable dataplex.googleapis.com
```

**1. Create a lake, zone, and attach assets:**
```bash
gcloud dataplex lakes create my-lake \
  --location=us-central1 \
  --display-name="My Data Lake" \
  --description="Central data lake for analytics"

# RAW zone for data needing further processing
gcloud dataplex zones create raw-zone \
  --location=us-central1 --lake=my-lake \
  --type=RAW --resource-location-type=SINGLE_REGION \
  --discovery-enabled --discovery-schedule="0 * * * *"

# Attach a Cloud Storage bucket as an asset in the zone
gcloud dataplex assets create raw-gcs-asset \
  --location=us-central1 --lake=my-lake --zone=raw-zone \
  --resource-type=STORAGE_BUCKET \
  --resource-name=projects/my-project/buckets/my-raw-bucket \
  --discovery-enabled

gcloud dataplex assets list --location=us-central1 --lake=my-lake --zone=raw-zone
```

**2. Authorize the service agent and grant IAM:**
```bash
# Let the Dataplex service agent manage a Cloud Storage bucket
gcloud dataplex lakes authorize --project=my-project \
  --storage-bucket-resource=my-raw-bucket

gcloud dataplex lakes add-iam-policy-binding my-lake \
  --location=us-central1 \
  --role=roles/dataplex.viewer \
  --member=user:analyst@example.com
```

**3. Run a data quality scan on a BigQuery table:**
```bash
# --data-quality-spec-file is a JSON/YAML rules file (see use-auto-data-quality docs)
gcloud dataplex datascans create data-quality my-dq-scan \
  --project=my-project --location=us-central1 \
  --data-source-resource="//bigquery.googleapis.com/projects/my-project/datasets/my_dataset/tables/my_table" \
  --data-quality-spec-file="dq-spec.yaml" \
  --display-name="Sales Table Quality Scan"

gcloud dataplex datascans run my-dq-scan --location=us-central1

gcloud dataplex datascans jobs list --location=us-central1 --datascan=my-dq-scan
gcloud dataplex datascans jobs describe JOB_ID \
  --location=us-central1 --datascan=my-dq-scan --view=FULL
```

**4. Create a data profile scan:**
```bash
gcloud dataplex datascans create data-profile my-profile-scan \
  --project=my-project --location=us-central1 \
  --data-source-resource="//bigquery.googleapis.com/projects/my-project/datasets/my_dataset/tables/my_table" \
  --display-name="Customer Table Profile"

gcloud dataplex datascans run my-profile-scan --location=us-central1
gcloud dataplex datascans list --project=my-project --location=us-central1
```

**5. Catalog — entry groups, glossary terms, and search:**
```bash
gcloud dataplex entry-groups create my-entry-group \
  --location=us-central1 --display-name="My Entry Group"

gcloud dataplex glossaries create my-glossary \
  --location=us-central1 --display-name="Analytics Glossary"

# A term's --parent is its glossary or a category within it
gcloud dataplex glossaries terms create revenue-term \
  --glossary=my-glossary --location=us-central1 \
  --parent="projects/my-project/locations/us-central1/glossaries/my-glossary" \
  --display-name="Revenue"

# Search entries across the project (search takes --project, not --location)
gcloud dataplex entries search "customer orders" --project=my-project

# Inspect a specific catalog entry
gcloud dataplex entries describe my-entry \
  --entry-group=my-entry-group --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `dataplex aspect-types` | [`aspect-types.md`](aspect-types.md) | 9 | manage Dataplex Aspect Types |
| `dataplex assets` | [`assets.md`](assets.md) | 10 | manage Dataplex Asset resources |
| `dataplex content` | [`content.md`](content.md) | 9 | manage Dataplex Content |
| `dataplex datascans` | [`datascans.md`](datascans.md) | 16 | manage Dataplex Datascan (quality, profile, discovery, documentation) |
| `dataplex encryption-config` | [`encryption-config.md`](encryption-config.md) | 3 | manage Dataplex encryption configs |
| `dataplex entries` | [`entries.md`](entries.md) | 9 | manage Dataplex Catalog Entries resources |
| `dataplex entry-groups` | [`entry-groups.md`](entry-groups.md) | 9 | manage Dataplex Entry Groups |
| `dataplex entry-types` | [`entry-types.md`](entry-types.md) | 9 | manage Dataplex Entry Types |
| `dataplex environments` | [`environments.md`](environments.md) | 10 | manage Dataplex Environments |
| `dataplex glossaries` | [`glossaries.md`](glossaries.md) | 19 | manage Dataplex glossaries, categories, and terms |
| `dataplex lakes` | [`lakes.md`](lakes.md) | 12 | manage Dataplex Lake resources |
| `dataplex metadata-jobs` | [`metadata-jobs.md`](metadata-jobs.md) | 4 | manage Dataplex metadata jobs |
| `dataplex tasks` | [`tasks.md`](tasks.md) | 13 | manage Dataplex Task services |
| `dataplex zones` | [`zones.md`](zones.md) | 10 | manage Dataplex Zone resources |

See [`index.md`](index.md) for a one-line index of all 142 commands.

## Common flags & tips

- **Resource hierarchy in flags:** most commands need `--location=LOCATION`; zone commands add
  `--lake=LAKE`; asset commands add `--lake` and `--zone`; entry commands add `--entry-group`. The
  location can also be set via the `dataplex/location` property.
- **Lakes/zones/assets create:** all support `--display-name`, `--description`,
  `--labels=KEY=VALUE,...`, `--async`, and `--validate-only`. Zones require
  `--type=RAW|CURATED` and `--resource-location-type=SINGLE_REGION|MULTI_REGION`. Assets require
  `--resource-type=STORAGE_BUCKET|BIGQUERY_DATASET` and `--resource-name=...`.
- **Discovery:** enable automatic metadata discovery on a zone or asset with
  `--discovery-enabled` plus a cron `--discovery-schedule="0 * * * *"`; narrow scope with
  `--discovery-include-patterns` / `--discovery-exclude-patterns`.
- **DataScans:** `datascans create` has subcommands `data-quality`, `data-profile`,
  `data-discovery`, and `data-documentation`. Point at data with
  `--data-source-resource="//bigquery.googleapis.com/projects/.../tables/..."` (BigQuery) or
  `//storage.googleapis.com/projects/.../buckets/...` (Cloud Storage), or use
  `--data-source-entity`. Schedule with `--on-demand`, `--schedule=...`, or `--one-time`; run
  immediately with `datascans run`. Quality scans require `--data-quality-spec-file`.
- **Scan results:** `datascans describe ... --view=FULL` and
  `datascans jobs describe JOB --datascan=SCAN --view=FULL` include spec/result data.
- **Catalog vs. data IAM:** lakes/zones/assets/datascans/entry-groups expose
  `add-iam-policy-binding`, `remove-iam-policy-binding`, `get-iam-policy`, and
  `set-iam-policy POLICY_FILE` (JSON/YAML). Use `roles/dataplex.viewer|editor|admin` for resources
  and `roles/dataplex.catalog*` / `roles/dataplex.dataScanAdmin` for catalog/scan scopes.
- **Service agent:** `lakes authorize` / `lakes deauthorize` grant or revoke the Dataplex service
  agent's access to a `--storage-bucket-resource`, `--bigquery-dataset-resource`, or
  `--project-resource`.
- **List/format:** list commands accept `--filter`, `--sort-by`, `--limit`, `--page-size`, and
  `--uri`. Examples: `gcloud dataplex lakes list --location=us-central1 --format="value(name)"`;
  list across all regions with `--location=-`.

## beta / alpha

There is **no beta track** for Dataplex. An alpha track exists alongside GA — the reference page
notes the variant `gcloud alpha dataplex`. All sub-groups documented here (including `content`,
`environments`, `datascans`, and the catalog groups) are GA under `gcloud dataplex`; reach for
`gcloud alpha dataplex` only for preview capabilities not present in the GA surface.

## Official documentation

- [Dataplex documentation home](https://cloud.google.com/dataplex/docs) — concepts, how-to guides, API reference
- [Dataplex overview](https://cloud.google.com/dataplex/docs/overview) — product overview, governance, context graph
- [Introduction to Dataplex](https://cloud.google.com/dataplex/docs/introduction) — lakes, zones, assets, catalog concepts
- [Catalog overview](https://cloud.google.com/dataplex/docs/catalog-overview) — entry types, aspect types, entry groups, entries
- [Data quality overview](https://cloud.google.com/dataplex/docs/data-quality-overview) — scan types and rule dimensions
- [Create and run auto data quality scans](https://cloud.google.com/dataplex/docs/use-auto-data-quality) — gcloud how-to and spec-file format
- [IAM roles for Dataplex](https://cloud.google.com/dataplex/docs/iam-roles) — predefined roles and permissions
- [gcloud dataplex CLI reference](https://cloud.google.com/sdk/gcloud/reference/dataplex) — all sub-groups and commands

---
name: gcloud-data-catalog
description: >-
  Data Catalog via gcloud (`gcloud data-catalog`). Manage Data Catalog resources — entries, entry-groups, tag-templates, tags, taxonomies.
---

# gcloud data-catalog — Data Catalog

## Overview

> **DEPRECATED — sunset June 1, 2026.** Data Catalog is deprecated and will be discontinued on **June 1, 2026**. It is succeeded by **Knowledge Catalog** (the catalog capabilities of Dataplex Universal Catalog). Most `gcloud data-catalog` commands are already marked `(DEPRECATED)` in GA: migrate `entries`/`entry-groups` to `gcloud dataplex entries` / `gcloud dataplex entry-groups`, `tag-templates`/`tags` to `gcloud dataplex aspect-types` / `gcloud dataplex entries`, and `search` to `gcloud dataplex entries search`. Only `taxonomies` and its `policy-tags` sub-group (BigQuery column-level / policy-tag security) are not deprecated. Treat the rest as legacy.

Data Catalog is a managed metadata service for discovering and describing data assets across Google Cloud. With `gcloud data-catalog` you manage **entries** and **entry groups** (catalog records, including custom and fileset entries), **tag templates** and **tags** (structured business metadata), policy-tag **taxonomies** (column-level security for BigQuery), and run catalog **search**. Reach for it only on existing/legacy catalogs; new work should target Dataplex Universal Catalog.

## Quick reference — common workflows

Enable the API once per project:

```bash
gcloud services enable datacatalog.googleapis.com
```

### 1. Create an entry group and a Cloud Storage fileset entry

```bash
gcloud data-catalog entry-groups create group1 \
    --location=us-central1 \
    --display-name="analytics data" \
    --description="Entries related to analytics data."

gcloud data-catalog entries create entry1 \
    --location=us-central1 \
    --entry-group=group1 \
    --type=FILESET \
    --gcs-file-patterns="gs://bucket1/abc/*,gs://bucket1/file1" \
    --display-name="analytics data"

gcloud data-catalog entries list --entry-group=group1 --location=us-central1
```

### 2. Look up an auto-cataloged BigQuery or Pub/Sub entry

```bash
# Lookup by Google Cloud resource name
gcloud data-catalog entries lookup \
    //pubsub.googleapis.com/projects/project1/topics/topic1

# Lookup a BigQuery table by its SQL name
gcloud data-catalog entries lookup \
    'bigquery.table.`my-project1`.my_dataset.my_table'

# Update the schema of an auto-cataloged Pub/Sub entry (system entry groups use @)
gcloud data-catalog entries update entry1 --location=global \
    --entry-group=@pubsub --schema="column1=type1,column2=type2"
```

### 3. Create a tag template and attach a tag to an entry

```bash
# Required string field + optional enum field
gcloud data-catalog tag-templates create my-template \
    --location=us-central1 \
    --display-name="Data Quality" \
    --field=id=owner,display-name="Data Owner",type=string,required=TRUE \
    --field=id=quality,display-name="Quality",type='enum(HIGH|MEDIUM|LOW)'

# Attach a tag using a JSON/YAML tag file (keys map to template field IDs)
gcloud data-catalog tags create \
    --entry=entry1 --entry-group=group1 --location=us-central1 \
    --tag-template=my-template --tag-template-location=us-central1 \
    --tag-file=/tmp/tag.json

gcloud data-catalog tags list --entry=entry1 \
    --entry-group=group1 --location=us-central1
```

### 4. Search the catalog (a scope flag is required)

```bash
# Simple predicate, scoped to a project
gcloud data-catalog search 'foo' --include-project-ids=my-project

# Name predicate, scoped to an organization
gcloud data-catalog search 'name:foo' --include-organization-ids=1234
```

### 5. Manage a policy-tag taxonomy (not deprecated)

```bash
gcloud data-catalog taxonomies list --location=us-central1

gcloud data-catalog taxonomies policy-tags list \
    --taxonomy=TAXONOMY --location=us-central1

# Grant column-level read access on a policy tag
gcloud data-catalog taxonomies policy-tags add-iam-policy-binding POLICY_TAG \
    --taxonomy=TAXONOMY --location=us-central1 \
    --member='user:analyst@example.com' \
    --role='roles/datacatalog.categoryFineGrainedReader'
```

### 6. Export and import taxonomies

```bash
# Export to a file (TAXONOMIES is a comma-separated positional list)
gcloud data-catalog taxonomies export "TAXONOMY1,TAXONOMY2" \
    --location=us-central1 > /tmp/taxonomies.yaml

# Import serialized taxonomies (positional file path)
gcloud data-catalog taxonomies import "/tmp/taxonomies.yaml" \
    --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `data-catalog entries` | [`entries.md`](entries.md) | 8 | Manage entries — create/lookup/describe/list/update, plus star/unstar (DEPRECATED → `gcloud dataplex entries`) |
| `data-catalog entry-groups` | [`entry-groups.md`](entry-groups.md) | 9 | Manage entry groups and their IAM (DEPRECATED → `gcloud dataplex entry-groups`) |
| `data-catalog tag-templates` | [`tag-templates.md`](tag-templates.md) | 13 | Manage tag templates, fields, and enum values (DEPRECATED → `gcloud dataplex aspect-types`) |
| `data-catalog tags` | [`tags.md`](tags.md) | 4 | Attach/list/update/delete tags on entries (DEPRECATED → `gcloud dataplex entries`) |
| `data-catalog taxonomies` | [`taxonomies.md`](taxonomies.md) | 14 | Policy-tag taxonomies, policy-tags, and IAM (active — not deprecated) |

Top-level command (see [`_commands.md`](_commands.md)): `gcloud data-catalog search` — search the catalog (DEPRECATED → `gcloud dataplex entries search`). See [`index.md`](index.md) for the one-line index of all 49 commands.

## Common flags & tips

- **Resource scoping.** Most commands need `--location` (a region such as `us-central1`, or `global`). Entries and tags also need `--entry-group` (and `--entry` for tags). You can pass a fully-qualified resource name instead of the ID + `--location`/`--entry-group` flags.
- **System entry groups.** Auto-cataloged sources are addressed with `@`-prefixed entry groups, e.g. `--entry-group=@pubsub` or `--entry-group=@bigquery`, typically with `--location=global`.
- **`entries create` types.** `--type` accepts values such as `fileset`, `table`, `database`, `model`, `service` (case-insensitive in examples, e.g. `FILESET`). For externally-ingested resources use `--user-specified-system` / `--user-specified-type` with `--linked-resource` instead of `--type`.
- **Schemas.** Provide inline (`--schema="col=TYPE,..."`) or from a file (`--schema-from-file=PATH`).
- **Tag templates.** `--field` is repeatable; keys are `id`, `type` (`double`, `string`, `bool`, `timestamp`, `enum(A|B)`), `display-name`, `required`. `--force` on `tag-templates delete` and `tag-templates fields delete` cascades the deletion to existing tags/fields.
- **Tag files.** `tags create`/`update` require `--tag-file` (JSON/YAML whose keys are the template field IDs); use `--scope` to tag a specific column (`outer.inner` for nested columns).
- **`search` requires a scope.** At least one of `--include-project-ids`, `--include-organization-ids`, `--include-gcp-public-datasets`, or `--restricted-locations` must be given. Use `--order-by`, `--limit`, and `--page-size` to shape results. Query syntax: https://cloud.google.com/data-catalog/docs/how-to/search-reference
- **List/format.** `entries list`, `entry-groups list`, `tags list`, `taxonomies list`, and `taxonomies policy-tags list` support `--filter`, `--limit`, `--sort-by`, `--page-size`, `--uri`. Examples:
  - `gcloud data-catalog entry-groups list --location=us-central1 --format='table(name, displayName)'`
  - `gcloud data-catalog taxonomies list --location=us-central1 --filter='displayName:PII'`
- **IAM.** `entry-groups`, `tag-templates`, `taxonomies`, and `taxonomies policy-tags` each expose `add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy` (`--member`, `--role`; `set-iam-policy` takes a `POLICY_FILE`).

## beta / alpha

- `gcloud beta data-catalog` mirrors the GA surface — same groups (`entries`, `entry-groups`, `tag-templates`, `tags`, `taxonomies`) and the top-level `search` command — and carries the same deprecation notices. There is no distinct `gcloud alpha data-catalog` surface in the GA reference. There is no beta-only capability to highlight; use GA unless a workflow specifically calls for the beta track.

## Official documentation

- [Data Catalog product docs](https://cloud.google.com/data-catalog/docs) — overview, quickstarts, how-to guides, and API references (product docs home).
- [Concepts overview](https://cloud.google.com/data-catalog/docs/concepts/overview) — entries, entry groups, tags, tag templates, taxonomies, and policy tags.
- [IAM roles & permissions](https://cloud.google.com/data-catalog/docs/concepts/iam) — Data Catalog predefined roles (`datacatalog.admin`, `datacatalog.viewer`, `datacatalog.tagEditor`, etc.).
- [Searching the catalog](https://cloud.google.com/data-catalog/docs/how-to/search) — search scope, filters, and syntax.
- [REST API reference](https://cloud.google.com/data-catalog/docs/reference/rest) — service endpoint `datacatalog.googleapis.com`.
- [gcloud data-catalog CLI reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog) — full GA command reference.
- [gcloud beta data-catalog CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/data-catalog) — beta command reference.

See [`sources.md`](sources.md) for the full citation list.

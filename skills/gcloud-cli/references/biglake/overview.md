# gcloud biglake — BigLake (Lakehouse for Apache Iceberg)

> **Note:** This command group reached the GA track after gcloud SDK 552.0.0. In the product documentation, BigLake was renamed **Lakehouse for Apache Iceberg** (and BigLake metastore renamed the **Lakehouse runtime catalog**) as of April 20, 2026; the CLI group name remains `gcloud biglake`.

## Overview

`gcloud biglake` creates and manages Google Cloud BigLake resources — specifically **Iceberg REST catalogs** served by the managed Apache Iceberg REST catalog endpoint (`https://biglake.googleapis.com/iceberg/v1/restcatalog`). Resources form a three-level hierarchy: **catalogs** contain **namespaces**, which contain **tables**. Catalogs come in two types: `gcs-bucket` (a catalog backed by a single Cloud Storage bucket) and `biglake` (a multi-bucket catalog whose namespaces and tables can map to locations beyond the catalog's default). Access is via end-user credentials or credential vending (`--credential-mode`), and IAM policies can be read/set at catalog, namespace, and table level. Replicated catalogs support failover to a different primary replica region.

## Quick reference — common workflows

### 1. Enable the API and create a catalog

```bash
gcloud services enable biglake.googleapis.com --project PROJECT_ID

# Catalog backed by a single Cloud Storage bucket
gcloud biglake iceberg catalogs create my-catalog-bucket --catalog-type=gcs-bucket

# Multi-bucket BigLake catalog with a default storage location and
# credential vending
gcloud biglake iceberg catalogs create my-catalog \
    --catalog-type=biglake \
    --default-location=gs://my-bucket/ \
    --credential-mode=vended-credentials
```

### 2. Create a namespace and a table

```bash
gcloud biglake iceberg namespaces create my-namespace --catalog=my-catalog

# Table schema/metadata comes from an Iceberg CreateTableRequest JSON file
gcloud biglake iceberg tables create \
    --namespace=my-namespace --catalog=my-catalog \
    --create-from-file=table_creation.json
```

### 3. Register an existing Iceberg table and inspect it

```bash
gcloud biglake iceberg tables register my-table \
    --namespace=my-namespace --catalog=my-catalog \
    --metadata-location=gs://my-bucket/metadata.json

gcloud biglake iceberg tables describe my-table \
    --namespace=my-namespace --catalog=my-catalog
```

### 4. List resources at each level

```bash
gcloud biglake iceberg catalogs list
gcloud biglake iceberg namespaces list --catalog=my-catalog
gcloud biglake iceberg tables list --namespace=my-namespace --catalog=my-catalog
```

### 5. Manage IAM on a catalog, namespace, or table

```bash
gcloud biglake iceberg catalogs get-iam-policy my-catalog

# Edit the policy file, then apply it (same pattern works for
# namespaces/tables with --catalog / --namespace flags)
gcloud biglake iceberg catalogs set-iam-policy my-catalog policy.json
gcloud biglake iceberg tables set-iam-policy my-table policy.json \
    --catalog=my-catalog --namespace=my-namespace
```

### 6. Fail over a replicated catalog

```bash
# Validate first, then execute; omit the conditional timestamp for a
# zero-data-loss failover
gcloud biglake iceberg catalogs failover my-catalog \
    --primary-replica=us-east1 --validate-only

gcloud biglake iceberg catalogs failover my-catalog --primary-replica=us-east1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `biglake iceberg catalogs` | [`iceberg-catalogs.md`](iceberg-catalogs.md) | 8 | manage BigLake Iceberg REST catalogs |
| `biglake iceberg namespaces` | [`iceberg-namespaces.md`](iceberg-namespaces.md) | 7 | manage BigLake Iceberg REST catalog namespaces |
| `biglake iceberg tables` | [`iceberg-tables.md`](iceberg-tables.md) | 8 | manage BigLake Iceberg REST catalog tables |

See [`index.md`](index.md) for a one-line index of all 23 commands.

## Common flags & tips

- **Resource hierarchy flags:** namespace commands take `--catalog`; table commands take both `--catalog` and `--namespace` (or pass a fully qualified resource name and omit them).
- **Catalog types:** `--catalog-type=gcs-bucket` backs the catalog with one Cloud Storage bucket; `--catalog-type=biglake` is the multi-bucket type supporting `--default-location`, `--restricted-locations`, and `--primary-location`. `catalogs update` can only change the type *to* `biglake`.
- **Credential modes:** `--credential-mode` is `end-user` by default; `vended-credentials` makes the catalog vend downscoped credentials to engines instead of using the caller's credentials.
- **Properties updates:** `namespaces update` and `tables update` share the trio `--update-properties=KEY=VALUE,...`, `--remove-properties=KEY,...`, and `--clear-properties`.
- **IAM:** `get-iam-policy` / `set-iam-policy` exist at all three levels; `set-iam-policy` takes a JSON or YAML `POLICY_FILE` (the output of `get-iam-policy` is valid input). Product-doc IAM roles include `roles/biglake.admin`, `roles/biglake.editor`, and `roles/biglake.viewer`.
- **Iceberg REST endpoint:** engines (Spark, Trino, etc.) connect to `https://biglake.googleapis.com/iceberg/v1/restcatalog`; the gcloud surface manages the same catalogs/namespaces/tables.
- **`tables create` is file-driven:** there are no schema flags — the whole Iceberg `CreateTableRequest` (name, schema, partition-spec, write-order, properties, ...) is supplied via `--create-from-file`.
- **List commands** support the standard `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri` flags.

## beta / alpha

`gcloud beta biglake` contains everything in GA **plus a `hive` group** (`gcloud beta biglake hive catalogs|databases|tables`) for BigLake Hive catalogs — the Hive-metastore-compatible surface is beta-only. `gcloud alpha biglake` mirrors the same surfaces. Per the product docs, BigLake metastore (classic) is a legacy feature; the Iceberg REST catalog (GA) is the recommended path, with Apache Iceberg V2 tables GA and V3 tables in Preview.

## Official documentation

- **Product docs (runtime catalog):** https://docs.cloud.google.com/bigquery/docs/about-blms — "About the Lakehouse runtime catalog" (formerly BigLake metastore).
- **Iceberg REST catalog setup:** https://docs.cloud.google.com/lakehouse/docs/lakehouse-iceberg-rest-catalog — endpoint, catalog types, credential modes, IAM roles, and `gcloud biglake iceberg` examples.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/biglake — the `gcloud biglake` command group.

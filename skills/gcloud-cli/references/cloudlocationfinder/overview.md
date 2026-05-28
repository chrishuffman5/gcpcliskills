# gcloud cloudlocationfinder — Cloud Location Finder

> **Preview:** Cloud Location Finder is in Preview and subject to the Pre-GA Offerings Terms. It is provided "as is" with potentially limited support, and its surface may change before GA.

## Overview

Cloud Location Finder is a read-only discovery API that exposes a single repository of cloud locations across Google Cloud and Google Distributed Cloud, plus locations for Amazon Web Services, Microsoft Azure, and Oracle Cloud Infrastructure. Reach for it when you need to enumerate available locations, find Google Cloud regions or zones close to an existing workload in another cloud, filter locations by provider/type for placement decisions, or screen locations by attributes such as country (for compliance) or carbon data. All commands are read-only — there is no create/update/delete surface.

## Quick reference — common workflows

### 1. Enable the API and grant access

```bash
gcloud services enable cloudlocationfinder.googleapis.com --project PROJECT_ID

# Read access for all list / search / describe operations
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:USER@example.com" \
    --role="roles/cloudlocationfinder.viewer"
```

### 2. List cloud locations

```bash
# All locations (resource scope is always global)
gcloud cloudlocationfinder cloud-locations list

# Output just the resource URIs (handy for scripting)
gcloud cloudlocationfinder cloud-locations list --uri
```

### 3. Describe a specific location

```bash
gcloud cloudlocationfinder cloud-locations describe gcp-us-central1

# Equivalent, with the location explicitly set (always global)
gcloud cloudlocationfinder cloud-locations describe gcp-us-central1 \
    --location=global
```

### 4. Filter the list by provider and location type

```bash
# Only GCP regions
gcloud cloudlocationfinder cloud-locations list \
    --filter="cloud_provider=CLOUD_PROVIDER_GCP AND cloud_location_type=CLOUD_LOCATION_TYPE_REGION"

# Only AWS zones
gcloud cloudlocationfinder cloud-locations list \
    --filter="cloud_provider=CLOUD_PROVIDER_AWS AND cloud_location_type=CLOUD_LOCATION_TYPE_ZONE"
```

### 5. Find locations near an existing workload in another cloud

```bash
# GCP locations near AWS us-east-1, narrowed with a query
gcloud cloudlocationfinder cloud-locations search \
    --source-cloud-location=aws-us-east-1 \
    --query=display_name="us-east4"
```

### 6. Paginate a large result set

```bash
gcloud cloudlocationfinder cloud-locations list \
    --page-size=50 \
    --limit=200
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `cloudlocationfinder cloud-locations` | [`cloud-locations.md`](cloud-locations.md) | 3 | manage Cloud Location resources |

See [`index.md`](index.md) for a one-line index of all 3 commands.

## Common flags & tips

- **Resource scope is always global.** Cloud Location Finder data lives in a single global location. `--location` accepts `global` (or a fully qualified name) but you can normally omit it.
- **`describe` takes a positional location ID** named like `<provider>-<region>` — e.g. `gcp-us-central1`, `aws-us-east-1`. Either pass the bare ID or supply a fully qualified name plus `--location`.
- **`search` requires `--source-cloud-location`** — the reference point you want results to be relative to (e.g. `aws-us-east-1`). Refine results with `--query`.
- **`--filter` (list) vs `--query` (search).** `list` supports the standard gcloud `--filter` expression language over location fields; `search` uses its own server-side `--query` string. Common fields seen in expressions: `cloud_provider` (`CLOUD_PROVIDER_GCP`, `CLOUD_PROVIDER_AWS`, …), `cloud_location_type` (`CLOUD_LOCATION_TYPE_REGION`, `CLOUD_LOCATION_TYPE_ZONE`, `CLOUD_LOCATION_TYPE_GDCC_ZONE`, …), `display_name`, and `containing_cloud_location`.
- **Pagination:** both `list` and `search` accept `--page-size` and `--limit`. `--uri` (list only) emits just resource URIs.
- **Useful formatting:**
  ```bash
  # Table of provider, type and display name across all locations
  gcloud cloudlocationfinder cloud-locations list \
      --format="table(cloudProvider, cloudLocationType, displayName)"
  ```

## beta / alpha

There is no `gcloud beta cloudlocationfinder` surface. An **alpha** surface (`gcloud alpha cloudlocationfinder`) mirrors the same three commands (`cloud-locations describe`, `list`, `search`) and is where more advanced `search`/`list` query expressions tend to appear first. The underlying REST API also has a `v1alpha` version that adds an `extraLocationTypes` parameter to the location-list method. The whole product remains in Preview regardless of the CLI track.

## Official documentation

- **Product docs home:** https://docs.cloud.google.com/location-finder/docs — Cloud Location Finder overview, guides, and API reference.
- **Concept overview:** https://docs.cloud.google.com/location-finder/docs/overview — supported providers, location types, and use cases.
- **Quickstart:** https://docs.cloud.google.com/location-finder/docs/quickstart — enable the API, grant IAM, and run your first `list`/`search`.
- **REST API (v1):** https://docs.cloud.google.com/location-finder/docs/reference/rest/v1/projects.locations.cloudLocations — `cloudLocations` resource (get, list, search).
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/cloudlocationfinder — the `gcloud cloudlocationfinder` command group.

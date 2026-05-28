# gcloud assured — Assured Workloads

## Overview

Assured Workloads lets organizations apply sovereign data, access, and personnel controls to Google Cloud resources by provisioning them inside a compliance-bounded environment (a "workload"). Each workload enforces a chosen **compliance regime** (FedRAMP, IL2/4/5, CJIS, ITAR, HIPAA, EU/regional data boundaries, partner-managed sovereign controls, and more), manages encryption-key rotation, and surfaces compliance **violations** for review. Reach for `gcloud assured` to create and maintain these environments, monitor for policy violations, and acknowledge them with a business justification. All commands operate at the **organization** level.

## Quick reference — common workflows

### 1. Enable the API

```bash
gcloud services enable assuredworkloads.googleapis.com
```

### 2. Create a FedRAMP Moderate workload

```bash
gcloud assured workloads create \
    --organization=123 \
    --location=us-central1 \
    --display-name=Test-Workload \
    --compliance-regime=fedramp-moderate \
    --billing-account=billingAccounts/456 \
    --next-rotation-time=2020-12-30T10:15:00.00Z \
    --rotation-period=172800s \
    --labels=Env=prod,Team=security \
    --provisioned-resources-parent=folders/789 \
    --resource-settings=consumer-project-id=my-custom-id \
    --external-identifier=external-id
```

### 3. List and describe workloads

```bash
# List workloads in an org/location (page-by-page, capped)
gcloud assured workloads list \
    --organization=123 --location=us-central1 \
    --limit=30 --page-size=10

# Describe one workload by fully qualified name
gcloud assured workloads describe \
    organizations/123/locations/us-central1/workloads/456
```

### 4. Update a workload (display name + labels)

```bash
gcloud assured workloads update \
    organizations/123/locations/us-central1/workloads/456 \
    --display-name=Test-Workload-2 \
    --labels=Env=prod,Team=security \
    --etag=789
```

Update requires at least one of `--display-name`, `--labels`, or `--violation-notifications-enabled`. Pass the `--etag` read from `describe` to avoid clobbering concurrent changes.

### 5. Triage compliance violations

```bash
# List violations for a workload
gcloud assured workloads violations list \
    --organization=123 --location=us-central1 --workload=w123 \
    --limit=30 --page-size=10

# Inspect one violation
gcloud assured workloads violations describe \
    organizations/123/locations/us-central1/workloads/456/violations/789

# Acknowledge with a business justification
gcloud assured workloads violations acknowledge \
    organizations/123/locations/us-central1/workloads/456/violations/789 \
    --comment="Reviewed and accepted per security team approval" \
    --acknowledge-type=SINGLE_VIOLATION
```

### 6. Enable monitoring and track long-running operations

```bash
# Turn on resource-violation monitoring for a workload
gcloud assured workloads enable-resource-monitoring \
    organizations/123/locations/us-central1/workloads/456

# List operations (e.g. workload creation/deletion) for an org/location
gcloud assured operations list \
    organizations/123/locations/us-central1 --limit=30 --page-size=10

# Describe a single operation
gcloud assured operations describe \
    organizations/123/locations/us-central1/operations/456
```

### 7. Delete a workload

```bash
gcloud assured workloads delete \
    organizations/123/locations/us-central1/workloads/456 --etag=789
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `assured operations` | [`operations.md`](operations.md) | 2 | Read Assured Workloads long-running operation resources (`describe`, `list`) |
| `assured workloads` | [`workloads.md`](workloads.md) | 9 | Create/read/update/delete workloads, enable monitoring, and manage violations |

See [`index.md`](index.md) for a one-line index of all 11 commands.

## Common flags & tips

- **Resource targeting (org-level).** Every command targets an organization. Supply the three resource attributes either as separate flags (`--organization=123 --location=us-central1 [--workload=456]`) or, for commands that take a positional, as a fully qualified name like `organizations/123/locations/us-central1/workloads/456`. Violation commands also need `--workload`.
- **Compliance regime is fixed at create time.** `--compliance-regime` accepts a long enum (e.g. `fedramp-moderate`, `fedramp-high`, `il2`, `il4`, `il5`, `cjis`, `itar`, `hipaa`, `hitrust`, `eu-regions-and-support`, `regional-controls`, `assured-workloads-for-partners`). It cannot be changed afterward — only `--display-name`, `--labels`, and `--violation-notifications-enabled` are updatable.
- **KMS rotation.** `--next-rotation-time` (RFC 3339, e.g. `2020-12-30T10:15:30.00Z`) and `--rotation-period` (seconds, e.g. `172800s`) configure key rotation at create time.
- **Partner (sovereign) workloads.** Use `--compliance-regime=assured-workloads-for-partners` with `--partner=` (e.g. `sovereign-controls-by-cntxt`, `local-controls-by-s3ns`), plus `--partner-services-billing-account=` and optional `--partner-permissions=data-logs-viewer=true`.
- **EU sovereign controls.** `--enable-sovereign-controls=true` is currently supported only with the EU regions regime.
- **Concurrency safety.** `update` and `delete` accept `--etag`; pass the value from `describe` to guard against lost updates.
- **Listing.** `list` commands support `--limit`, `--page-size`, `--filter`, `--sort-by`, and `--uri`. Useful pattern: `--filter` to narrow and `--format` to project, e.g. `--format="table(name, complianceRegime, createTime)"`.
- **Acknowledging violations.** `--comment` is required; `--acknowledge-type` is `SINGLE_VIOLATION` (default behavior) or `EXISTING_CHILD_RESOURCE_VIOLATIONS` to also clear child-resource violations of an org-policy violation.

## beta / alpha

`gcloud beta assured` and `gcloud alpha assured` expose the same command surface as GA (the `operations` and `workloads` groups with identical subcommands). No beta/alpha-exclusive commands exist; partner workload creation is part of GA.

## Official documentation

- [Assured Workloads documentation home](https://cloud.google.com/assured-workloads/docs) — overview, quickstarts, and how-to guides.
- [Assured Workloads overview](https://cloud.google.com/assured-workloads/docs/overview) — concepts, supported compliance regimes, and capabilities.
- [Supported locations](https://cloud.google.com/assured-workloads/docs/locations) — valid `--location` values per compliance regime.
- [Access control (IAM)](https://cloud.google.com/assured-workloads/docs/access-control) — roles and permissions required to manage workloads.
- [gcloud assured CLI reference](https://cloud.google.com/sdk/gcloud/reference/assured) — full command/flag reference.

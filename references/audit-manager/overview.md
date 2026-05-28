# gcloud audit-manager — Audit Manager

## Overview

Google Cloud Audit Manager automates compliance assessments of Google Cloud projects and folders against regulatory frameworks (FedRAMP, NIST, SOC 2, PCI DSS, and others), collecting evidence and identifying gaps. Reach for `gcloud audit-manager` when you need to enroll a resource for auditing, preview audit coverage (an "audit scope"), and generate compliance audit reports that land in Cloud Storage. Report and scope generation are long-running operations whose status you track with `operations describe`.

## Quick reference — common workflows

### 1. Enable the API

```bash
gcloud services enable auditmanager.googleapis.com
```

### 2. Enroll a resource for auditing

Enrollment registers the eligible Cloud Storage buckets where reports and evidence may later be uploaded. Enroll a project, folder, or organization:

```bash
# Enroll project 123 with two eligible buckets
gcloud audit-manager enrollments add \
    --project=123 \
    --eligible-gcs-buckets="gs://test-bucket-1,gs://my-bucket-2"

# Or enroll a folder
gcloud audit-manager enrollments add \
    --folder=FOLDER_ID \
    --eligible-gcs-buckets="gs://test-bucket-1"
```

### 3. Generate an audit scope (preview coverage)

Generate a scope first to review which controls/resources the audit will cover. The scope report is written locally:

```bash
gcloud audit-manager audit-scopes generate \
    --project=123 \
    --location=us-central1 \
    --compliance-framework=fedramp_moderate \
    --report-format=odf \
    --output-directory="scopes/currentyear" \
    --output-file-name=auditreport
```

### 4. Generate a compliance audit report

Run the full audit and upload the report plus evidence to one of the enrolled buckets:

```bash
gcloud audit-manager audit-reports generate \
    --project=123 \
    --location=us-central1 \
    --compliance-framework=fedramp_moderate \
    --report-format=odf \
    --gcs-uri=gs://testbucketauditmanager
```

This is a long-running operation; it returns an operation ID.

### 5. Check audit operation status

```bash
# Project-scoped operation
gcloud audit-manager operations describe operation-456 \
    --project=123 --location=us-central1

# Folder-scoped operation
gcloud audit-manager operations describe operation-456 \
    --folder=FOLDER_ID --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `audit-manager audit-reports` | [`audit-reports.md`](audit-reports.md) | 1 | command group for Audit Manager Audit Reports |
| `audit-manager audit-scopes` | [`audit-scopes.md`](audit-scopes.md) | 1 | command group for Audit Manager Audit Scopes |
| `audit-manager enrollments` | [`enrollments.md`](enrollments.md) | 1 | command group for Audit Manager Enrollments |
| `audit-manager operations` | [`operations.md`](operations.md) | 1 | check audit operation status |

See [`index.md`](index.md) for a one-line index of all 4 commands.

## Common flags & tips

- **Resource scope is mutually exclusive.** Every command targets exactly one resource:
  - `enrollments add` accepts `--project`, `--folder`, or `--organization`.
  - `audit-scopes generate` and `audit-reports generate` accept `--project` or `--folder` (no organization scope).
  - `operations describe` takes a positional `OPERATION` ID plus `--folder` (or `--project` via the `core/project` property) and `--location`.
- **`--location`** is required for scope generation, report generation, and `operations describe` (e.g. `us-central1`). It is *not* used by `enrollments add`.
- **`--report-format`** currently supports only `odf` for both `audit-scopes generate` and `audit-reports generate`.
- **`--compliance-framework`** names the framework to assess against (e.g. `fedramp_moderate`).
- **Scope vs. report output differs:**
  - `audit-scopes generate` writes locally — use `--output-file-name` (required) and optional `--output-directory`.
  - `audit-reports generate` uploads to Cloud Storage — use `--gcs-uri`, which must be one of the buckets passed to `--eligible-gcs-buckets` at enrollment time.
- **Enroll before you audit.** The `--gcs-uri` bucket for a report must have been registered via `enrollments add --eligible-gcs-buckets`.
- **Operations are long-running.** After `audit-reports generate` returns an operation ID, poll it with `operations describe`. The default `--format` is YAML; add `--format=json` for machine parsing or `--format="value(done)"` to check completion.

## Official documentation

- [Audit Manager documentation home](https://cloud.google.com/audit-manager/docs) — entry point to all guides, resources, and release notes.
- [Audit Manager overview](https://cloud.google.com/audit-manager/docs/overview) — concepts: supported compliance frameworks, the enrollment model, and pricing tiers.
- [Enroll a resource](https://cloud.google.com/audit-manager/docs/enroll-resource) — enrolling an org, folder, or project; required IAM roles; eligible bucket configuration.
- [Run an audit](https://cloud.google.com/audit-manager/docs/run-audit) — generating an audit scope and running a compliance report against a framework.
- [View an audit](https://cloud.google.com/audit-manager/docs/view-audit) — viewing completed audit artifacts and downloading reports from Cloud Storage.
- [Access control](https://cloud.google.com/audit-manager/docs/access-control) — IAM roles (admin, auditor, CCF admin/viewer).
- [Supported locations](https://cloud.google.com/audit-manager/docs/locations) — regions available for Audit Manager.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/audit-manager) — full reference for all `gcloud audit-manager` command groups.
- [REST API reference](https://cloud.google.com/audit-manager/docs/reference/auditmanager/rest) — `auditmanager.googleapis.com` endpoint and resource model.

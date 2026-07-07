---
name: gcloud-policy-intelligence
description: >-
  Policy Intelligence via gcloud (`gcloud policy-intelligence`). A platform to help better understand, use, and manage policies at scale — simulate, troubleshoot-policy.
---

# gcloud policy-intelligence — Policy Intelligence

## Overview

Policy Intelligence is a Google Cloud suite for understanding, analyzing, and simulating IAM and organization policies at scale. The `gcloud policy-intelligence` group exposes three GA tools: Activity Analyzer (`query-activity`) to surface service-account last-authentication times, Policy Simulator for Organization Policy (`simulate orgpolicy`) to preview the impact of org-policy and custom-constraint changes before enforcing them, and the IAM Troubleshooter (`troubleshoot-policy iam`) to explain whether a principal has a specific permission on a resource. Reach for it when auditing stale service accounts, validating org-policy changes safely, or diagnosing unexpected access grants or denials.

## Quick reference — common workflows

### 1. Find stale or unused service accounts (last authentication)
```bash
gcloud services enable policyanalyzer.googleapis.com

# Last-authentication time for every service account in a project
gcloud policy-intelligence query-activity \
    --activity-type=serviceAccountLastAuthentication \
    --project=PROJECT_ID

# Same query with no result cap
gcloud policy-intelligence query-activity \
    --activity-type=serviceAccountLastAuthentication \
    --project=PROJECT_ID \
    --limit=unlimited
```

### 2. Audit service account key usage
```bash
# Last-authentication time for service account keys
gcloud policy-intelligence query-activity \
    --activity-type=serviceAccountKeyLastAuthentication \
    --project=PROJECT_ID

# Narrow to a single service account with a query filter
gcloud policy-intelligence query-activity \
    --activity-type=serviceAccountKeyLastAuthentication \
    --project=PROJECT_ID \
    --query-filter='activities.full_resource_name="//iam.googleapis.com/projects/PROJECT_ID/serviceAccounts/SA_NAME@PROJECT_ID.iam.gserviceaccount.com"'
```

### 3. Simulate an organization policy change before enforcing it
```bash
gcloud services enable policysimulator.googleapis.com cloudresourcemanager.googleapis.com

# Preview a custom constraint defined in a local JSON/YAML file
gcloud policy-intelligence simulate orgpolicy \
    --organization=ORGANIZATION_ID \
    --custom-constraints=custom-constraint.json

# Preview a new org policy
gcloud policy-intelligence simulate orgpolicy \
    --organization=ORGANIZATION_ID \
    --policies=policy.json

# Simulate a custom constraint and a policy together
gcloud policy-intelligence simulate orgpolicy \
    --organization=ORGANIZATION_ID \
    --custom-constraints=custom-constraint.json \
    --policies=policy.json
```
The result lists resources that would violate the proposed policy.

### 4. Troubleshoot why a principal lacks (or has) a permission
```bash
gcloud services enable policytroubleshooter.googleapis.com

# Does my-user@example.com have resourcemanager.projects.get on my-project?
gcloud policy-intelligence troubleshoot-policy iam \
    //cloudresourcemanager.googleapis.com/projects/my-project \
    --principal-email=my-user@example.com \
    --permission=resourcemanager.projects.get
```

### 5. Troubleshoot with IAM Conditions context
```bash
# Supply condition attributes so the troubleshooter can evaluate conditional bindings
gcloud policy-intelligence troubleshoot-policy iam \
    //cloudresourcemanager.googleapis.com/projects/my-project \
    --principal-email=my-user@example.com \
    --permission=compute.images.get \
    --resource-name=//compute.googleapis.com/projects/my-project/zones/images/my-image \
    --resource-service=compute.googleapis.com \
    --resource-type=compute.googleapis.com/Image \
    --destination-ip=192.2.2.2 \
    --destination-port=8080 \
    --request-time=2023-01-01T00:00:00Z
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `policy-intelligence simulate` | [`simulate.md`](simulate.md) | 1 | Simulate changes to organization policies (`simulate orgpolicy`) |
| `policy-intelligence troubleshoot-policy` | [`troubleshoot-policy.md`](troubleshoot-policy.md) | 1 | Troubleshoot IAM allow and deny policies (`troubleshoot-policy iam`) |

Top-level command (see [`_commands.md`](_commands.md)):

- `gcloud policy-intelligence query-activity` — query activities on a cloud resource

See [`index.md`](index.md) for a one-line index of all 3 commands.

## Common flags & tips

- **`query-activity` is project-scoped and required.** Both `--activity-type` and `--project` are mandatory. `--activity-type` accepts only `serviceAccountLastAuthentication` or `serviceAccountKeyLastAuthentication`.
- **Result paging.** `--limit` defaults to `1000` (use `--limit=unlimited` to remove the cap); `--page-size` defaults to `500` with a max of `1000`.
- **`--query-filter` syntax.** Filter on `activities.full_resource_name`, combining up to 10 restrictions with `OR`. Useful to focus on specific service accounts.
- **`simulate orgpolicy` is organization-scoped.** `--organization` is required; supply `--custom-constraints` and/or `--policies` as comma-separated paths to local JSON or YAML files (e.g. `--custom-constraints=c1.json,c2.json`).
- **`troubleshoot-policy iam` takes the target as a positional full resource name** (e.g. `//cloudresourcemanager.googleapis.com/projects/my-project`); `--permission` and `--principal-email` are required. Only Google Accounts and service accounts are supported as principals. Permissions accept v1 (`resourcemanager.projects.get`) or v2 (`cloudresourcemanager.googleapis.com/projects.get`) form.
- **Conditional bindings.** When a resource uses IAM Conditions, pass `--resource-name`, `--resource-service`, `--resource-type`, `--destination-ip`, `--destination-port`, and/or `--request-time` (RFC 3339, e.g. `2021-01-01T00:00:00Z`) so the troubleshooter can evaluate them.
- **Output shaping.** Add `--format` and `--filter` as with any gcloud command, e.g. `--format='table(activities.fullResourceName, activities.activity)'` on `query-activity` results.

## beta / alpha

- `gcloud beta policy-intelligence` exists and includes the `simulate` subgroup, mirroring the GA `simulate orgpolicy` command (with the usual beta "might change without notice" disclaimer). It is primarily a staging track and does not add new subcommands. If you hit unexpected behavior with the GA `simulate orgpolicy`, the beta variant can be a fallback.
- No `gcloud alpha policy-intelligence` group is documented in the official reference.

## Official documentation

- [Policy Intelligence product home](https://cloud.google.com/policy-intelligence/docs) — overview of all tools (Policy Analyzer, Activity Analyzer, Policy Simulator, IAM Troubleshooter, Role Recommendations).
- [Policy Intelligence overview](https://cloud.google.com/policy-intelligence/docs/overview) — conceptual overview of every feature (simulators, analyzers, troubleshooters).
- [Test organization policies](https://cloud.google.com/policy-intelligence/docs/test-organization-policies) — how-to for Policy Simulator for Organization Policy (`simulate orgpolicy`).
- [Activity Analyzer: service account authentication](https://cloud.google.com/policy-intelligence/docs/activity-analyzer-service-account-authentication) — querying last-authentication timestamps for service accounts and keys (`query-activity`).
- [gcloud policy-intelligence reference](https://cloud.google.com/sdk/gcloud/reference/policy-intelligence) — top-level CLI reference listing all commands and subgroups.

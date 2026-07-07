---
name: gcloud-pam
description: >-
  Privileged Access Manager via gcloud (`gcloud pam`). Manage Privileged Access Manager entitlements and grants — entitlements, grants, operations.
---

# gcloud pam — Privileged Access Manager

## Overview

Privileged Access Manager (PAM) provides just-in-time, time-bound privilege elevation on Google Cloud, replacing standing IAM grants with temporary, auditable access. It uses a two-object model: an **entitlement** defines who may request access, which roles are granted, for how long, and whether approval is required; a **grant** is the actual temporary-access instance a requester creates against an entitlement, automatically activated and then revoked when its duration expires. Reach for `gcloud pam` when you need to manage entitlements, request/approve/deny/revoke temporary elevated access, or audit privileged-access operations at the project, folder, or organization scope.

PAM resources are scoped by a resource attribute (`--project`, `--folder`, or `--organization`) plus a `--location` (use `global`). Grants additionally live under an entitlement (`--entitlement`).

## Quick reference — common workflows

### 1. Enable the API and check onboarding status

```bash
gcloud services enable privilegedaccessmanager.googleapis.com

# Confirm PAM is onboarded for a project (or use --folder / --organization)
gcloud pam check-onboarding-status \
    --project=sample-project --location=global

gcloud pam check-onboarding-status \
    --organization=ORGANIZATION_ID --location=global
```

### 2. Create an entitlement (admin)

Author the entitlement config in a YAML file, then create it. (See the create-entitlements guide for the full schema.)

```bash
gcloud pam entitlements create sample-entitlement \
    --project=sample-project --location=global \
    --entitlement-file=sample-entitlement.yaml
```

### 3. List, inspect, and export entitlements

```bash
gcloud pam entitlements list \
    --project=sample-project --location=global

gcloud pam entitlements describe sample-entitlement \
    --project=sample-project --location=global

# Export current config to a local YAML file (for editing, then update)
gcloud pam entitlements export sample-entitlement \
    --project=sample-project --location=global \
    --destination=sample-entitlement.yaml

gcloud pam entitlements update sample-entitlement \
    --project=sample-project --location=global \
    --entitlement-file=sample-entitlement.yaml
```

### 4. Request temporary elevated access (requester)

```bash
# Find entitlements you can request against
gcloud pam entitlements search \
    --project=sample-project --location=global \
    --caller-access-type=grant-requester

# Create a grant (90 minutes) against the entitlement's full name
gcloud pam grants create \
    --entitlement=ENTITLEMENT_NAME \
    --requested-duration=5400s \
    --justification="some justification" \
    --additional-email-recipients=oncall@example.com
```

### 5. Approve or deny a grant (approver)

```bash
# Find entitlements where you are an approver
gcloud pam entitlements search \
    --project=sample-project --location=global \
    --caller-access-type=grant-approver

# Find grants awaiting your approval
gcloud pam grants search \
    --entitlement=ENTITLEMENT_NAME \
    --caller-relationship=can-approve

gcloud pam grants approve GRANT_NAME --reason="approval reason"
gcloud pam grants deny GRANT_NAME --reason="denial reason"
```

### 6. Revoke an active grant, then delete the entitlement

```bash
gcloud pam grants revoke GRANT_NAME --reason="revoke reason"

# Deletion fails if non-terminal grants still exist under the entitlement
gcloud pam entitlements delete sample-entitlement \
    --project=sample-project --location=global
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `pam entitlements` | [`entitlements.md`](entitlements.md) | 7 | Manage entitlements (create, delete, describe, export, list, search, update) |
| `pam grants` | [`grants.md`](grants.md) | 7 | Manage grants (approve, create, deny, describe, list, revoke, search) |
| `pam operations` | [`operations.md`](operations.md) | 4 | Manage long-running operations (delete, describe, list, wait) |

Top-level command: `gcloud pam check-onboarding-status` — check PAM onboarding status for a resource (see [`_commands.md`](_commands.md)). See [`index.md`](index.md) for a one-line index of all 19 GA commands.

## Common flags & tips

- **Scope selectors (`--project` / `--folder` / `--organization`)** are mutually exclusive; pair with `--location` (use `global`). They appear on `check-onboarding-status`, all `entitlements` commands, all `operations` commands, and `grants list`/`search`.
- **`--location=global`** is the location used for PAM resources.
- **Entitlement YAML** is supplied via `--entitlement-file=PATH` on `create` and `update`; round-trip it with `entitlements export --destination=PATH`. Omitting `--destination` writes to standard output.
- **Grant duration** uses a seconds string: `--requested-duration=5400s` (90 minutes).
- **`--additional-email-recipients`** takes a comma-separated list: `--additional-email-recipients=abc@example.com,xyz@example.com`.
- **Search filters by caller role:** `entitlements search --caller-access-type=` accepts `grant-requester` or `grant-approver`; `grants search --caller-relationship=` accepts `can-approve`, `had-approved`, or `had-created`.
- **Approve/deny/revoke** take a free-text `--reason`; `revoke` also supports `--async`.
- **`--async`** (on `entitlements create`/`delete`/`update` and `grants revoke`) returns immediately; poll the returned operation with `gcloud pam operations wait OPERATION_NAME`.
- **Fully qualified names:** grant actions (`approve`, `deny`, `describe`, `revoke`) and `grants list` accept a grant's full resource name, so you can omit the scope flags. Use `entitlements search` / `grants search` to discover those names.
- **List/format examples** (standard gcloud flags `--filter`, `--limit`, `--sort-by`, `--format` are supported on `list` and `search`):

```bash
# Show only entitlement names and states
gcloud pam entitlements list --project=sample-project --location=global \
    --format="table(name, state)"

# Find grants you created, newest first
gcloud pam grants search --entitlement=ENTITLEMENT_NAME \
    --caller-relationship=had-created --sort-by=~createTime
```

## beta / alpha

- **`gcloud beta pam`** adds a **`settings`** command group not present in GA: `settings describe`, `settings describe-effective` (effective/inherited settings), `settings export`, and `settings update`.
- **`gcloud alpha pam`** is also available. Official how-to guides sometimes show alpha-only grant flags (e.g. `--scheduled-activation-time`, `--requested-resources`, `--requested-access-from-file`) that are not in the GA `grants create` command documented here — verify against the GA reference before using them.

## Official documentation

- [PAM product overview](https://cloud.google.com/iam/docs/pam-overview) — concepts, entitlements, and grants (product docs home).
- [Permissions and setup](https://cloud.google.com/iam/docs/pam-permissions-and-setup) — required IAM roles, service-agent setup, and prerequisites.
- [Create entitlements](https://cloud.google.com/iam/docs/pam-create-entitlements) — entitlement YAML schema and creation walkthrough.
- [View, update, and delete entitlements](https://cloud.google.com/iam/docs/pam-view-update-delete-entitlements) — list, describe, update, export, and delete.
- [Request temporary elevated access](https://cloud.google.com/iam/docs/pam-request-temporary-elevated-access) — requester workflow for creating grants.
- [Approve or deny grants](https://cloud.google.com/iam/docs/pam-approve-deny-grants) — approver workflow.
- [Revoke grants](https://cloud.google.com/iam/docs/pam-revoke-grants) — revoke active grants.
- [gcloud pam reference (GA)](https://cloud.google.com/sdk/gcloud/reference/pam) — full command/flag reference.
- [gcloud beta pam reference](https://cloud.google.com/sdk/gcloud/reference/beta/pam) — includes the `settings` group.

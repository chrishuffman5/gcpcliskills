---
name: gcloud-projects
description: >-
  Cloud Resource Manager (Projects) via gcloud (`gcloud projects`). Create and manage project access policies.
---

# gcloud projects — Cloud Resource Manager (Projects)

## Overview

`gcloud projects` is the CLI surface for **Cloud Resource Manager projects** — the fundamental organizing entity in Google Cloud. Every API is enabled per-project, billing attaches per-project, and the project-level IAM policy governs access to every resource the project contains. Reach for it to create, list, describe, label, move, delete, and recover projects, and — most importantly — to manage **project-level IAM bindings** with `add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy`. These project IAM commands are the canonical grant/revoke surface that most other Google Cloud services point back to.

## Quick reference — common workflows

### 1. Create a project (standalone or under an org/folder)

```bash
# Resource Manager API is enabled by default; enable explicitly if needed
gcloud services enable cloudresourcemanager.googleapis.com

# Create a standalone project with a display name and a label
gcloud projects create example-foo-bar-1 \
    --name="Happy project" \
    --labels=type=happy

# Create under an organization
gcloud projects create example-3 --organization=2048

# Create under a folder and make it the active project
gcloud projects create example-2 --folder=12345 --set-as-default
```

### 2. Grant a role on a project (add-iam-policy-binding)

This is the canonical way to give a user, group, or service account access to a project and all its resources. Many other gcloud services document this exact command for project-wide grants.

```bash
# Grant a user the Editor role
gcloud projects add-iam-policy-binding example-project-id-1 \
    --member='user:test-user@gmail.com' \
    --role='roles/editor'

# Grant a service account the Editor role
gcloud projects add-iam-policy-binding example-project-id-1 \
    --member='serviceAccount:test-proj1@example.domain.com' \
    --role='roles/editor'

# Grant a time-bound (conditional) role — basic roles can't use conditions
gcloud projects add-iam-policy-binding example-project-id-1 \
    --member='user:test-user@gmail.com' \
    --role='roles/browser' \
    --condition='expression=request.time < timestamp("2019-01-01T00:00:00Z"),title=expires_end_of_2021,description=Expires at midnight on 2021-12-31'
```

### 3. Revoke a role on a project (remove-iam-policy-binding)

```bash
# Remove a specific binding
gcloud projects remove-iam-policy-binding example-project-id-1 \
    --member='user:test-user@gmail.com' \
    --role='roles/editor'

# Remove the binding for everyone authenticated
gcloud projects remove-iam-policy-binding example-project-id-1 \
    --member='allAuthenticatedUsers' \
    --role='roles/editor'

# Remove every binding for this principal+role regardless of any condition
gcloud projects remove-iam-policy-binding example-project-id-1 \
    --member='user:test-user@gmail.com' \
    --role='roles/browser' --all
```

### 4. Read or replace the entire IAM policy

```bash
# Export the current policy to a file
gcloud projects get-iam-policy example-project-id-1 --format=json > policy.json

# (edit policy.json as needed, then set it back atomically)
gcloud projects set-iam-policy example-project-id-1 policy.json

# See policies inherited from folder/org ancestors (add --include-deny for deny policies)
gcloud projects get-ancestors-iam-policy example-project-id-1
```

### 5. List, inspect, and locate projects in the hierarchy

```bash
# List the five most-recent projects, sorted alphabetically by ID
gcloud projects list --sort-by=projectId --limit=5

# List projects marked for deletion
gcloud projects list --filter='lifecycleState:DELETE_REQUESTED'

# Show metadata for one project, then print its folder/org ancestry
gcloud projects describe example-project-id-1
gcloud projects get-ancestors example-project-id-1
```

### 6. Rename, delete, and recover a project

```bash
# Rename a project (the project ID is immutable; only the display name changes)
gcloud projects update example-foo-bar-1 --name="Foo Bar & Grill"

# Schedule deletion (30-day recovery window), then recover within the window
gcloud projects delete example-foo-bar-1
gcloud projects undelete example-foo-bar-1
```

## Command groups

`gcloud projects` is a flat command group — there are no subgroups. All 12 GA commands live at the top level.

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `projects` (top level) | [`_commands.md`](_commands.md) | 12 | create and manage projects and project-level IAM policies |

See [`index.md`](index.md) for a one-line index of all 12 GA commands.

## Common flags & tips

- **Project identifier.** `create`, `update`, `get-ancestors`, and the IAM-binding commands take a `PROJECT_ID`; `delete`, `describe`, `get-iam-policy`, `set-iam-policy`, and `undelete` accept `PROJECT_ID_OR_NUMBER` (project ID or numeric project number). IDs are immutable, 6–30 chars, lowercase letter first, lowercase letters/digits/hyphens only.
- **Parent on create.** `gcloud projects create` defaults to no parent. Use **exactly one** of `--organization=ORG_ID` or `--folder=FOLDER_ID` to nest it. Add `--set-as-default` to set `[core/project]` to the new project, `--labels=KEY=VALUE,...` for labels, and `--no-enable-cloud-apis` to skip enabling `cloudapis.googleapis.com`. (`move` between parents is beta/alpha only — see below.)
- **IAM members.** `--member` takes `user:`, `group:`, `serviceAccount:`, or `domain:` prefixes, plus the special `allUsers` and `allAuthenticatedUsers`. On `remove-iam-policy-binding`, deleted principals use a `deleted:` prefix with a `?uid=...` suffix.
- **IAM conditions.** `--condition` requires `expression=` and `title=` (`description=` optional) and **cannot** be combined with a basic role (`roles/owner`, `roles/editor`, `roles/viewer`). Use `--condition=None` to target a binding that has no condition. If the expression contains a comma, switch the delimiter, e.g. `--condition=^:^title=TITLE:expression=EXPRESSION`. Or supply `--condition-from-file=PATH` (JSON/YAML).
- **Removing bindings precisely.** On `remove-iam-policy-binding`, `--all` strips every binding for the member+role regardless of condition; otherwise the condition must match exactly to remove a conditional binding.
- **set-iam-policy is a full replace.** It overwrites the policy with the supplied JSON/YAML file. To avoid clobbering concurrent edits, start from a fresh `get-iam-policy` export (the read-modify-write pattern), which preserves the `etag`.
- **Filtering & formatting.** `list`, `get-iam-policy`, and `get-ancestors-iam-policy` support the standard `--filter`, `--sort-by`, `--limit`, `--page-size`, and `--format`. `list` also supports `--uri`. Example: `gcloud projects list --format="table(projectId, name, lifecycleState)"`.

## beta / alpha

- **`gcloud beta projects`** — all 12 GA commands are also available in beta with identical flags; no beta-exclusive top-level commands. Adds the **`move`** command for relocating a project into an organization or folder: `gcloud beta projects move PROJECT_ID --folder=FOLDER_ID` (or `--organization=ORGANIZATION_ID`).
- **`gcloud alpha projects`** — includes **`move`** plus **`search`**, which finds projects matching a query string (broader than `list`, covering projects you may not directly own).

## Official documentation

- [Cloud Resource Manager — product overview](https://cloud.google.com/resource-manager/docs/overview) — the org → folder → project hierarchy and what projects are for.
- [Creating and managing projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects) — how-to for creating, listing, updating, deleting, and recovering projects with gcloud and REST.
- [Access control for projects (IAM)](https://cloud.google.com/resource-manager/docs/access-control-proj) — predefined Resource Manager project roles (projectCreator, projectDeleter, projectMover, projectIamAdmin, plus owner/editor/viewer/browser).
- [Managing IAM policies](https://cloud.google.com/iam/docs/managing-policies) — grant/modify/revoke policies; the reference for `add-iam-policy-binding` usage.
- [IAM Conditions overview](https://cloud.google.com/iam/docs/conditions-overview) — required reading for the `--condition` flag on binding commands.
- [gcloud projects CLI reference](https://cloud.google.com/sdk/gcloud/reference/projects) — full command/flag reference for all 12 GA commands.
- [Cloud Resource Manager REST API](https://cloud.google.com/resource-manager/reference/rest) — the underlying `cloudresourcemanager.googleapis.com` API.

See [`sources.md`](sources.md) for the full citation record.

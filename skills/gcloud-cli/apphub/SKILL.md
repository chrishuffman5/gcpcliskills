---
name: gcloud-apphub
description: >-
  App Hub via gcloud (`gcloud apphub`). Manage App Hub resources — applications, boundary, discovered-services, discovered-workloads, locations, operations, service-projects.
---

# gcloud apphub — App Hub

## Overview

App Hub is Google Cloud's application-centric registry that lets you group services and workloads scattered across projects into logical **Applications**, aligning infrastructure with business functions. Each Application is composed of **Services** (network/API interfaces) and **Workloads** (compute resources), which App Hub auto-detects as *discovered* resources within a defined boundary (a folder, a single project, or a legacy host project). Reach for `gcloud apphub` to attach service projects to a host project, create and govern Applications, register discovered services/workloads, and manage application-level IAM. Applications are either `GLOBAL` or `REGIONAL` in scope.

## Quick reference — common workflows

### 1. Enable the API and attach a service project to the host project
```bash
# One-time: enable the App Hub API on the management/host project
gcloud services enable apphub.googleapis.com --project=HOST_PROJECT_ID

# Attach a service project (attachments only support the global location)
gcloud apphub service-projects add SERVICE_PROJECT_ID --project=HOST_PROJECT_ID

# Verify the attachment, then inspect a specific one
gcloud apphub service-projects list --project=HOST_PROJECT_ID
gcloud apphub service-projects describe SERVICE_PROJECT_ID --project=HOST_PROJECT_ID
```

### 2. Create an application (global or regional)
```bash
# Global-scoped application with metadata
gcloud apphub applications create my-global-app \
    --location=global \
    --scope-type=GLOBAL \
    --display-name="My Global Application" \
    --environment-type=PRODUCTION \
    --criticality-type=HIGH \
    --project=HOST_PROJECT_ID

# Regional-scoped application
gcloud apphub applications create my-regional-app \
    --location=us-east1 \
    --scope-type=REGIONAL \
    --display-name="My Regional Application" \
    --project=HOST_PROJECT_ID

# Confirm and inspect
gcloud apphub applications list --location=global --project=HOST_PROJECT_ID
gcloud apphub applications describe my-global-app --location=global --project=HOST_PROJECT_ID
```

### 3. Discover and register a service
```bash
# List services auto-detected within the boundary
gcloud apphub discovered-services list --location=global --project=HOST_PROJECT_ID

# Resolve a discovered service from a GCP resource URI (--uri is required)
gcloud apphub discovered-services lookup \
    --location=global --uri=DISCOVERED_SERVICE_URI --project=HOST_PROJECT_ID

# Register the discovered service into an application
gcloud apphub applications services create frontend-svc \
    --application=my-global-app \
    --location=global \
    --discovered-service=DISCOVERED_SERVICE_ID \
    --display-name="Frontend Service" \
    --project=HOST_PROJECT_ID
```

### 4. Discover and register a workload
```bash
# List discovered workloads in a region
gcloud apphub discovered-workloads list --location=us-east1 --project=HOST_PROJECT_ID

# Register a discovered workload into an application
gcloud apphub applications workloads create my-workload \
    --application=my-regional-app \
    --location=us-east1 \
    --discovered-workload=DISCOVERED_WORKLOAD_ID \
    --display-name="My Workload" \
    --criticality-type=MISSION_CRITICAL \
    --environment-type=PRODUCTION \
    --project=HOST_PROJECT_ID

# List workloads registered in the application
gcloud apphub applications workloads list \
    --application=my-regional-app --location=us-east1 --project=HOST_PROJECT_ID
```

### 5. Update application metadata (owners, criticality, environment)
```bash
gcloud apphub applications update my-global-app \
    --location=global \
    --environment-type=PRODUCTION \
    --criticality-type=MISSION_CRITICAL \
    --developer-owners=display-name="Dev Team",email=dev@example.com \
    --operator-owners=display-name="Ops Team",email=ops@example.com \
    --business-owners=display-name="Business Owner",email=biz@example.com \
    --project=HOST_PROJECT_ID
```

### 6. Manage application-level IAM
```bash
# Grant viewer access on a specific application
gcloud apphub applications add-iam-policy-binding my-global-app \
    --location=global \
    --role=roles/apphub.viewer \
    --member=user:analyst@example.com \
    --project=HOST_PROJECT_ID

# View the current IAM policy
gcloud apphub applications get-iam-policy my-global-app \
    --location=global --project=HOST_PROJECT_ID
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `apphub applications` | [`applications.md`](applications.md) | 19 | manage App Hub Applications (plus `services` and `workloads` subgroups) |
| `apphub boundary` | [`boundary.md`](boundary.md) | 2 | manage App Hub boundaries |
| `apphub discovered-services` | [`discovered-services.md`](discovered-services.md) | 3 | manage App Hub Discovered Services |
| `apphub discovered-workloads` | [`discovered-workloads.md`](discovered-workloads.md) | 3 | manage App Hub Discovered Workloads |
| `apphub locations` | [`locations.md`](locations.md) | 2 | manage App Hub Locations |
| `apphub operations` | [`operations.md`](operations.md) | 2 | manage App Hub Operations (long-running operations) |
| `apphub service-projects` | [`service-projects.md`](service-projects.md) | 6 | manage App Hub Service Projects |

See [`index.md`](index.md) for a one-line index of all 37 GA commands.

## Common flags & tips

- **Location is pervasive.** Most commands require `--location` (or a fully qualified resource name). Applications are `GLOBAL` (use `--location=global`) or `REGIONAL` (e.g. `--location=us-east1`); `--scope-type` is set to `GLOBAL`/`REGIONAL` at create time. **Service project attachments and boundaries only support the `global` location.**
- **Host vs. service project.** Run management commands against the host/management project with `--project=HOST_PROJECT_ID` (or `gcloud config set project`). `service-projects detach` and `service-projects lookup` instead take the *service* project: `--project=SERVICE_PROJECT_ID`.
- **Metadata enums** are shared across applications, services, and workloads: `--criticality-type` (`HIGH|LOW|MEDIUM|MISSION_CRITICAL|TYPE_UNSPECIFIED`) and `--environment-type` (`DEVELOPMENT|PRODUCTION|STAGING|TEST|TYPE_UNSPECIFIED`).
- **Owner flags** repeat per role and take a `display-name=...,email=...` pair: `--developer-owners`, `--operator-owners`, `--business-owners`.
- **Register, don't create from scratch.** `applications services create` requires `--discovered-service`, and `applications workloads create` requires `--discovered-workload` — register discovered resources rather than inventing them.
- **Lookups need a URI.** `discovered-services lookup` and `discovered-workloads lookup` both require `--uri=URI` (the GCP resource URI) in addition to `--location`.
- **Long-running operations:** add `--async` to create/update/delete and `service-projects add/remove` to return immediately; track with `gcloud apphub operations list --location=LOCATION` and `gcloud apphub operations describe`.
- **`--format` / `--filter` examples:**
  - `gcloud apphub applications list --location=global --format="table(name, scope.type, state)"`
  - `gcloud apphub applications list --location=global --filter="environmentType=PRODUCTION"`
  - `gcloud apphub discovered-services list --location=us-east1 --sort-by=name --limit=20`
  - `gcloud apphub service-projects list --project=HOST_PROJECT_ID --uri`

## beta / alpha

`gcloud alpha apphub` exists and mirrors the GA surface (documented at the alpha reference URL below); use it for in-flight capabilities not yet promoted to GA. A distinct `gcloud beta apphub` reference is not published — beta features are either graduated to GA or remain under alpha. Single-project boundary mode is in Preview in the setup documentation.

## Official documentation

- [App Hub documentation home](https://cloud.google.com/app-hub/docs/overview) — product overview: what App Hub is, core concepts, and boundary models.
- [Key concepts](https://cloud.google.com/app-hub/docs/key-concepts) — applications, services, workloads, boundaries, and management projects.
- [Quickstart: create an application](https://cloud.google.com/app-hub/docs/quickstart-create-application) — deploy Cloud Run + load balancer, then discover and register services.
- [Set up App Hub](https://cloud.google.com/app-hub/docs/set-up-app-hub) — folder-level, single-project, and host-project (legacy) boundary setup.
- [Manage applications](https://cloud.google.com/app-hub/docs/manage-applications) — list, describe, create, update, and delete applications.
- [Roles and permissions](https://cloud.google.com/app-hub/docs/roles-permissions) — IAM roles (`roles/apphub.admin`, `editor`, `viewer`) and permissions.
- [gcloud apphub CLI reference](https://cloud.google.com/sdk/gcloud/reference/apphub) — full command reference for all `gcloud apphub` commands.
- [gcloud alpha apphub CLI reference](https://cloud.google.com/sdk/gcloud/reference/alpha/apphub) — alpha command surface.

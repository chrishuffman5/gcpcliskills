---
name: gcloud-service-health
description: >-
  Personalized Service Health via gcloud (`gcloud service-health`). Request events that are relevant to your project or organization (Personalized Service Health, read-only) — events, organization-events, organization-impacts.
---

# gcloud service-health — Personalized Service Health

## Overview

Personalized Service Health surfaces Google Cloud service health events (incidents, planned maintenance) that are relevant to *your* projects and organization, rather than the generic public status dashboard. The `gcloud service-health` group requests events relevant to your project or organization: project-scoped **events**, organization-scoped **organization-events**, and **organization-impacts** (which assets/projects in the organization are affected by an event). The entire surface is read-only (`list` / `describe`); for service health incident events the location is always `global`.

## Quick reference — common workflows

### 1. Enable the API and grant access

```bash
gcloud services enable servicehealth.googleapis.com --project PROJECT_ID

# Least-privilege read access (project level)
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:USER@example.com" \
    --role="roles/servicehealth.viewer"

# Organization-level access (inherited by all projects; needed for
# organization-events and organization-impacts)
gcloud organizations add-iam-policy-binding ORGANIZATION_ID \
    --member="user:USER@example.com" \
    --role="roles/servicehealth.viewer"
```

### 2. List service health events for a project

```bash
# Incident events always live in location global
gcloud service-health events list --project=my-project --location=global

# Include the full event payload (adds the updates field)
gcloud service-health events list \
    --project=my-project --location=global --view=event-view-full
```

### 3. Describe a single event

```bash
gcloud service-health events describe my-event \
    --project=my-project --location=global
```

### 4. List and describe organization-wide events

```bash
gcloud service-health organization-events list \
    --organization=123456789 --location=global

gcloud service-health organization-events describe my-event \
    --organization=123456789 --location=global
```

### 5. See which assets in the organization an event impacts

```bash
gcloud service-health organization-impacts list \
    --organization=123456789 --location=global

gcloud service-health organization-impacts describe my-impact \
    --organization=123456789 --location=global
```

### 6. Paginate / sort / script the output

```bash
gcloud service-health events list \
    --project=my-project --location=global \
    --page-size=50 --limit=200 --sort-by=~updateTime

# Just the resource URIs (handy for scripting)
gcloud service-health events list \
    --project=my-project --location=global --uri
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `service-health events` | [`events.md`](events.md) | 2 | represents events that may affect Google Cloud products |
| `service-health organization-events` | [`organization-events.md`](organization-events.md) | 2 | represents events that may affect products used across the organization |
| `service-health organization-impacts` | [`organization-impacts.md`](organization-impacts.md) | 2 | represents impact to assets at organizational level |

See [`index.md`](index.md) for a one-line index of all 6 commands.

## Common flags & tips

- **Location is `global` for incidents.** Every command takes `--location`; to retrieve service health incident events, set it to `global`. You can also set the `servicehealth/location` property once (`gcloud config set servicehealth/location global`) and omit the flag.
- **Project vs organization scope.** `events` is project-scoped (uses `--project` / `core/project`); `organization-events` and `organization-impacts` require `--organization=ORGANIZATION_ID` (the numeric organization ID — see "Getting your organization resource ID" in Resource Manager docs).
- **`--view` on list commands** controls payload size: `events list` accepts `event-view-basic` (default, excludes `updates`) or `event-view-full`; `organization-events list` accepts `organization-event-view-basic` (default) or `organization-event-view-full`.
- **Read-only surface.** There is no create/update/delete — the API only exposes get/list over events and impacts.
- **Standard list flags** (`--filter`, `--limit`, `--page-size`, `--sort-by`, `--uri`) work on all three `list` commands.
- **Fully qualified names work everywhere**, e.g. `projects/{project}/locations/global/events/{event_id}` or `organizations/{org_id}/locations/global/organizationEvents/{event_id}`, in place of the bare ID plus scope flags.
- **IAM:** grant `roles/servicehealth.viewer` (Personalized Service Health Viewer). Granting it on the organization is inherited by all projects and unlocks the organization-level APIs. Basic roles (Viewer/Editor/Owner) also include the needed permissions.

## beta / alpha

Both `gcloud beta service-health` and `gcloud alpha service-health` surfaces exist and mirror the same three read-only groups (`events`, `organization-events`, `organization-impacts`); there are no extra pre-GA command groups documented beyond the GA surface.

## Official documentation

- **Product docs home / overview:** https://docs.cloud.google.com/service-health/docs/overview — what Personalized Service Health is, event concepts.
- **Quickstart (view events):** https://docs.cloud.google.com/service-health/docs/view-events — enable the API and view events in the console.
- **Organization events:** https://docs.cloud.google.com/service-health/docs/organization-events — access organization events with the API.
- **Manage access:** https://docs.cloud.google.com/service-health/docs/manage-access — IAM roles (`roles/servicehealth.viewer`) at project and organization level.
- **Alerting quickstart:** https://docs.cloud.google.com/service-health/docs/configure-alerts-dashboard — set up alerts on service health events.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/service-health — the `gcloud service-health` command group.

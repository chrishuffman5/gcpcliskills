---
name: gcloud-monitoring
description: >-
  Cloud Monitoring via gcloud (`gcloud monitoring`). Manage Cloud Monitoring dashboards — dashboards, policies, snoozes, uptime.
---

# gcloud monitoring — Cloud Monitoring

## Overview

Cloud Monitoring collects metrics, events, and metadata from Google Cloud, and provides tools to visualize that data and alert on it. The `gcloud monitoring` command surface manages four GA resource types: **dashboards** (custom visualizations), **policies** (alerting policies and their conditions), **snoozes** (temporary suppression of alerts), and **uptime** checks / synthetic monitors. Reach for it to script the creation and lifecycle of monitoring configuration as code, or to migrate Prometheus alerting rules into Cloud Monitoring.

## Quick reference — common workflows

### 1. Enable the API and create a dashboard from a config file

```bash
gcloud services enable monitoring.googleapis.com

# Validate the config without saving
gcloud monitoring dashboards create --config-from-file=dashboard.yaml --validate-only

# Create the dashboard, then find its ID and inspect it
gcloud monitoring dashboards create --config-from-file=dashboard.yaml
gcloud monitoring dashboards list
gcloud monitoring dashboards describe MY-DASHBOARD --format=json
```

### 2. Create a metric-threshold alerting policy (via flags)

```bash
# Alert when GCE instance CPU utilization exceeds 80% for 5 minutes
gcloud monitoring policies create \
    --display-name="High CPU Alert" \
    --condition-display-name="CPU utilization above 80%" \
    --condition-filter='resource.type="gce_instance" AND metric.type="compute.googleapis.com/instance/cpu/utilization"' \
    --duration=300s \
    --if="> 0.8" \
    --combiner=OR

gcloud monitoring policies list
```

### 3. Attach a notification channel and disable/enable a policy

```bash
# Add a notification channel to an existing policy (channel referenced by ID)
gcloud monitoring policies update ALERT_POLICY \
    --add-notification-channels=CHANNEL_ID

# Temporarily disable, then re-enable the policy
gcloud monitoring policies update ALERT_POLICY --no-enabled
gcloud monitoring policies update ALERT_POLICY --enabled

gcloud monitoring policies describe ALERT_POLICY
```

### 4. Snooze a policy during a maintenance window

```bash
# Suppress a policy's alerts for a fixed interval
gcloud monitoring snoozes create \
    --criteria-policies=projects/MY-PROJECT/alertPolicies/MY-POLICY \
    --display-name="Maintenance window snooze" \
    --start-time=2026-06-01T02:00:00Z \
    --end-time=2026-06-01T06:00:00Z

gcloud monitoring snoozes list

# End the snooze early if maintenance finishes ahead of schedule
gcloud monitoring snoozes cancel MY-SNOOZE
```

### 5. Create and manage an uptime check

```bash
# HTTP uptime check against a public URL (period is in minutes: 1, 5, 10, 15)
gcloud monitoring uptime create "My Website Check" \
    --resource-type=uptime-url \
    --resource-labels=host=example.com,project_id=MY-PROJECT \
    --period=5 \
    --timeout=30

gcloud monitoring uptime list-configs   # all checks + synthetic monitors
gcloud monitoring uptime list-ips        # egress IP ranges of check servers

gcloud monitoring uptime update CHECK_ID --period=10 --timeout=30
gcloud monitoring uptime delete CHECK_ID
```

### 6. Migrate Prometheus alerting rules to Cloud Monitoring

```bash
# Convert Prometheus alert rules (+ Alertmanager config) into policies/channels
gcloud monitoring policies migrate \
    --policies-from-prometheus-alert-rules-yaml=rules.yaml \
    --channels-from-prometheus-alertmanager-yaml=alertmanager.yaml

gcloud monitoring policies list
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `monitoring dashboards` | [`dashboards.md`](dashboards.md) | 5 | Manage Cloud Monitoring dashboards (create/update from JSON/YAML configs) |
| `monitoring policies` | [`policies.md`](policies.md) | 10 | Manage alerting policies and their conditions; migrate Prometheus rules |
| `monitoring snoozes` | [`snoozes.md`](snoozes.md) | 5 | Manage snoozes that temporarily suppress alerting policies |
| `monitoring uptime` | [`uptime.md`](uptime.md) | 6 | Manage uptime checks and synthetic monitors |

See [`index.md`](index.md) for a one-line index of all 26 commands.

## Common flags & tips

- **Dashboards are config-driven.** `dashboards create` / `update` take either `--config=CONFIG` (inline JSON/YAML string) or `--config-from-file=PATH_TO_FILE`. Use `--validate-only` on create to check a config without saving. Updates require the current `etag` (visible in `describe`/`list`) to prevent concurrent overwrites.
- **Two ways to build a policy.** Supply a full policy with `--policy` / `--policy-from-file`, or build a basic one from flags: `--display-name`, `--condition-display-name`, `--condition-filter`, `--duration`, `--if` (`"absent"`, `"< THRESHOLD"`, or `"> THRESHOLD"`), and `--combiner` (`AND`, `AND_WITH_MATCHING_RESOURCE`, `OR`). Use `--enabled` / `--no-enabled` to toggle.
- **Notification channels** are managed on `policies update` with `--add-notification-channels`, `--remove-notification-channels`, `--set-notification-channels`, or `--clear-notification-channels`. There is no GA `notification-channels` group; channels are referenced by ID.
- **Conditions** can be added to an existing policy with `gcloud monitoring policies conditions create ALERT_POLICY ...`; reference a condition either by `CONDITION` ID plus `--policy=POLICY`.
- **Uptime `--period`** is in minutes and must be one of `1`, `5`, `10`, `15`; `--timeout` is in seconds (default 60). `--regions` (≥3) defaults to all regions. `--protocol` is one of `http`, `https`, `tcp`.
- **Resource scoping:** every resource ID can be a short ID with `--project=MY-PROJECT`, or a fully qualified name (e.g. `projects/MY-PROJECT/alertPolicies/MY-POLICY`). These are global Monitoring resources — no `--region`/`--zone` on the resources themselves.
- **Filtering & sorting** on `list` commands use standard `--filter`, `--sort-by`, `--limit`. Example: `gcloud monitoring policies list --filter "description:(cloud)"` or `gcloud monitoring snoozes list --filter="interval.end_time<+PT1S"` (expired snoozes only).

## beta / alpha

- **Notification channel management** (create/list/describe/update/delete) is not in the GA surface; check `gcloud beta monitoring --help`. GA policies still reference existing channels by ID via `--notification-channels` / `--add-notification-channels`.
- The reference page notes some capabilities may also be available under `gcloud beta monitoring` or `gcloud alpha monitoring`.

## Official documentation

- [Cloud Monitoring docs home](https://cloud.google.com/monitoring/docs) — central hub for all Cloud Monitoring guides and references.
- [gcloud monitoring CLI reference](https://cloud.google.com/sdk/gcloud/reference/monitoring) — full reference for every `gcloud monitoring` command group.
- [Dashboards overview](https://cloud.google.com/monitoring/dashboards) and [Manage custom dashboards via the API/gcloud](https://cloud.google.com/monitoring/dashboards/api-dashboard) — designing and scripting dashboards.
- [Alerting overview](https://cloud.google.com/monitoring/alerts) and [Create metric-threshold policies](https://cloud.google.com/monitoring/alerts/using-alerting-ui) — alerting policies, incidents, and channels.
- [Uptime checks & synthetic monitors](https://cloud.google.com/monitoring/uptime-checks/introduction) and [Manage uptime checks](https://cloud.google.com/monitoring/uptime-checks/manage) — purpose, structure, and lifecycle.
- [Cloud Monitoring access control](https://cloud.google.com/monitoring/access-control) — IAM roles (`roles/monitoring.viewer`, `.editor`, `.admin`, `.metricWriter`).

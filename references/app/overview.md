# gcloud app — App Engine

## Overview
App Engine is Google Cloud's fully managed, serverless platform for building and hosting web applications and APIs at scale. The `gcloud app` command group creates the per-project App Engine application, deploys code/configuration from `app.yaml` (and related config files), and manages services, versions, traffic splits, instances, domains, SSL certificates, and firewall rules. Reach for it when you want to deploy a web app without managing servers — App Engine supports both the **Standard** environment (language-specific runtimes that scale to zero) and the **Flexible** environment (Docker-based, running on Compute Engine VMs).

## Quick reference — common workflows

### 1. Create the App Engine app and deploy for the first time
```bash
# Enable the App Engine Admin API (one-time per project)
gcloud services enable appengine.googleapis.com

# List available regions, then create the app (one-time, region is permanent)
gcloud app regions list
gcloud app create --region=us-central

# Deploy the default service from app.yaml in the current directory
gcloud app deploy

# Open the live app in a browser
gcloud app browse
```

### 2. Deploy a new version without sending it traffic
```bash
# Deploy a new version but keep traffic on the existing one
gcloud app deploy app.yaml --no-promote --version=v2

# Confirm the version is listed (and not yet serving)
gcloud app versions list --service=default

# When ready, migrate all traffic to v2 (automatically-scaled Standard versions)
gcloud app versions migrate v2 --service=default
```

### 3. Canary / traffic split between two versions
```bash
# Send 90% of traffic to v1 and 10% to v2, split by cookie
gcloud app services set-traffic default \
    --splits=v1=9,v2=1 \
    --split-by=cookie

# Inspect the current traffic allocation
gcloud app services describe default

# When confident, shift all traffic to v2
gcloud app services set-traffic default --splits=v2=1
```

### 4. List, stop, and delete old versions
```bash
# List every version across all services
gcloud app versions list

# List only versions currently receiving traffic
gcloud app versions list --hide-no-traffic

# Stop a version (manual-scaling services only)
gcloud app versions stop v1 --service=default

# Delete a version (it must not be receiving traffic)
gcloud app versions delete v1 --service=default
```

### 5. Read and tail logs
```bash
# Read the latest entries (default limit 200) across all log types
gcloud app logs read

# Read warning-or-higher entries for a specific service/version
gcloud app logs read --service=default --version=v2 --level=warning

# Stream live logs
gcloud app logs tail

# Stream only request logs (request_log for Standard, nginx.request for Flex)
gcloud app logs tail --service=default --logs=request_log
```

### 6. Debug a Flexible-environment instance over SSH
```bash
# Find the instance ID
gcloud app instances list --service=default --version=v2

# Enable debug mode (removes the instance from health checking, enables SSH)
gcloud app instances enable-debug --service=default --version=v2 i1

# SSH into the instance, or into the app container specifically
gcloud app instances ssh i1 --service=default --version=v2
gcloud app instances ssh i1 --service=default --version=v2 --container=gaeapp

# Re-enable health checking when finished
gcloud app instances disable-debug --service=default --version=v2 i1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `app domain-mappings` | [`domain-mappings.md`](domain-mappings.md) | 5 | view and manage your App Engine domain mappings |
| `app firewall-rules` | [`firewall-rules.md`](firewall-rules.md) | 6 | view and manage your App Engine firewall rules |
| `app instances` | [`instances.md`](instances.md) | 7 | view and manage your App Engine instances |
| `app logs` | [`logs.md`](logs.md) | 2 | manage your App Engine logs |
| `app operations` | [`operations.md`](operations.md) | 3 | view and manage your App Engine operations |
| `app regions` | [`regions.md`](regions.md) | 1 | view regional availability of App Engine runtime environments |
| `app runtimes` | [`runtimes.md`](runtimes.md) | 1 | list runtimes available to Google App Engine |
| `app services` | [`services.md`](services.md) | 6 | view and manage your App Engine services |
| `app ssl-certificates` | [`ssl-certificates.md`](ssl-certificates.md) | 5 | view and manage your App Engine SSL certificates |
| `app versions` | [`versions.md`](versions.md) | 7 | view and manage your App Engine versions |

Top-level commands (`browse`, `create`, `deploy`, `describe`, `open-console`, `update`) are in [`_commands.md`](_commands.md). A one-line index of all 49 GA commands is in [`index.md`](index.md).

## Common flags & tips
- **App is one-per-project and region is permanent.** `gcloud app create --region=REGION` runs once; the region cannot be changed afterward. Run `gcloud app regions list` first to see Standard/Flexible availability.
- **Service / version targeting.** Most version-, instance-, and log-related commands accept `--service` (`-s`) and `--version` (`-v`). The unnamed default service is literally `default`.
- **Deploy traffic control.** `gcloud app deploy` promotes by default; use `--no-promote` to deploy without shifting traffic, and `--version=NAME` to set a predictable version ID. `--no-stop-previous-version` keeps the old version running. Persist the no-promote default with `gcloud config set app/promote_by_default false`.
- **Traffic splitting.** `gcloud app services set-traffic` takes `--splits=v1=9,v2=1` (relative weights) and `--split-by=cookie|ip|random` (default `ip`). Add `--migrate` to let the autoscaler ramp gradually.
- **Version migration is Standard-only.** `gcloud app versions migrate` works only for automatically-scaled Standard versions; `start`/`stop` only apply to manual-scaling services.
- **Debug/SSH is Flexible-only.** `instances enable-debug`, `ssh`, and `scp` work only on the Flexible environment; `--container=gaeapp` targets the app container, and `--tunnel-through-iap` routes through Identity-Aware Proxy.
- **Ingress controls.** Restrict who can reach a service with `gcloud app services update default --ingress=internal-only` (also `all`, `internal-and-cloud-load-balancing`).
- **Useful `--format` / `--filter`.** List commands support standard output formatting, e.g.:
  ```bash
  gcloud app versions list --format="json"
  gcloud app versions list \
      --filter="version.createTime.date('%Y-%m-%d', Z)>'2017-11-03'"
  gcloud app instances list --uri
  ```
- **Deploy prerequisites.** Beyond `appengine.googleapis.com`, `gcloud app deploy` uses Cloud Build and Cloud Storage to build and stage artifacts (`cloudbuild.googleapis.com`, `storage.googleapis.com`). The deployer also needs `roles/iam.serviceAccountUser` to act as the App Engine service account.

## beta / alpha
- `gcloud beta app migrate-to-run` — beta-exclusive command group to migrate second-generation App Engine apps to Cloud Run.
- `gcloud beta app gen-config` — deprecated beta command that generates missing config files for a local source directory.
- `gcloud alpha app` exists for experimental features. The core GA commands above (`deploy`, `services set-traffic`, `versions migrate`, etc.) need no beta/alpha flags for standard workflows.

## Official documentation
- App Engine product docs home — https://cloud.google.com/appengine/docs — serverless web-app hosting platform overview (Standard and Flexible environments).
- gcloud `app` CLI reference — https://cloud.google.com/sdk/gcloud/reference/app — all 49 GA commands.
- Python 3 quickstart — https://cloud.google.com/appengine/docs/standard/python3/quickstart — create, deploy, and add persistence to a Flask app on Standard.
- Configuration files — https://cloud.google.com/appengine/docs/standard/configuration-files — `app.yaml`, `cron.yaml`, `dispatch.yaml`, `index.yaml`.
- Splitting traffic — https://cloud.google.com/appengine/docs/standard/splitting-traffic — IP, cookie, and random splitting for canary/blue-green deploys.
- IAM roles for App Engine — https://cloud.google.com/appengine/docs/standard/roles — admin, deployer, service admin, and viewer roles.
- gcloud `beta app` reference — https://cloud.google.com/sdk/gcloud/reference/beta/app — beta surface including `migrate-to-run`.

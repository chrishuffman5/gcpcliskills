# gcloud deploy — Google Cloud Deploy

## Overview

Google Cloud Deploy is a managed, opinionated continuous-delivery service that automates application delivery to a sequence of target environments in a defined promotion order. Reach for `gcloud deploy` when you want to model a delivery pipeline (dev → staging → prod), create releases from built artifacts, and drive rollouts to GKE clusters, Cloud Run services, or custom targets — with optional approval gates, deploy policies, and automated promote/rollback rules. Resources are regional, so nearly every command takes `--region` (or the `deploy/region` property).

Core resource model: **DeliveryPipeline** (ordered promotion sequence) → **Target** (a deployment destination) → **Release** (a snapshot of rendered manifests for a build) → **Rollout** (associates a release with a target and performs the deploy). **Automation** rules automate actions on a pipeline; **DeployPolicy** adds time-window/approval guardrails.

## Quick reference — common workflows

Enable the API once per project:

```bash
gcloud services enable clouddeploy.googleapis.com
```

### 1. Create a pipeline and targets from YAML config

```bash
# Apply a single file containing pipeline, targets, automations, deploy policies
gcloud deploy apply --file=clouddeploy.yaml \
    --region=us-central1 --project=my-project

# Or apply separate files
gcloud deploy apply --file=delivery-pipeline.yaml --region=us-central1
gcloud deploy apply --file=target-prod.yaml       --region=us-central1

# Confirm registration
gcloud deploy delivery-pipelines list --region=us-central1
gcloud deploy delivery-pipelines describe my-pipeline --region=us-central1
```

### 2. Create a release and deploy to the first target

```bash
# From source in the current dir, supplying the image(s) to substitute
gcloud deploy releases create 'my-release-$DATE-$TIME' \
    --delivery-pipeline=my-pipeline \
    --region=us-central1 \
    --images=app=gcr.io/my-project/app:v1.2.3

# Or from a pre-built artifacts file (e.g. from Cloud Build)
gcloud deploy releases create 'my-release-$DATE-$TIME' \
    --delivery-pipeline=my-pipeline \
    --region=us-central1 \
    --build-artifacts=artifacts.json

# Check the rollout created on the first target
gcloud deploy rollouts list \
    --delivery-pipeline=my-pipeline \
    --release=my-release-20240101-1200 \
    --region=us-central1
```

Wrap a release name containing `$DATE`/`$TIME` in single quotes so the shell does not expand them.

### 3. Promote a release through the pipeline

```bash
# Promote to the next target in sequence (auto-selects furthest target)
gcloud deploy releases promote \
    --release=my-release-20240101-1200 \
    --delivery-pipeline=my-pipeline \
    --region=us-central1

# Promote to a specific target
gcloud deploy releases promote \
    --release=my-release-20240101-1200 \
    --delivery-pipeline=my-pipeline \
    --region=us-central1 \
    --to-target=prod
```

### 4. Approve or reject a gated rollout

```bash
# Find rollouts awaiting approval
gcloud deploy rollouts list \
    --delivery-pipeline=my-pipeline \
    --release=my-release-20240101-1200 \
    --region=us-central1

# Approve
gcloud deploy rollouts approve my-rollout \
    --delivery-pipeline=my-pipeline \
    --release=my-release-20240101-1200 \
    --region=us-central1

# Reject
gcloud deploy rollouts reject my-rollout \
    --delivery-pipeline=my-pipeline \
    --release=my-release-20240101-1200 \
    --region=us-central1
```

### 5. Roll back or redeploy a target

```bash
# Roll back to the previous successful release (auto-selected)
gcloud deploy targets rollback prod \
    --delivery-pipeline=my-pipeline --region=us-central1

# Roll back to a specific release
gcloud deploy targets rollback prod \
    --delivery-pipeline=my-pipeline --region=us-central1 \
    --release=my-release-20231215-0900

# Re-run the last release on the target (not a prior one)
gcloud deploy targets redeploy prod \
    --delivery-pipeline=my-pipeline --region=us-central1
```

### 6. Inspect health and troubleshoot a rollout

```bash
# Pipeline status (targets, active release, pending approvals)
gcloud deploy delivery-pipelines describe my-pipeline --region=us-central1

# Target status (active release/rollout, last deploy time, pending approvals)
gcloud deploy targets describe prod \
    --delivery-pipeline=my-pipeline --region=us-central1

# Rollout detail (phases, jobs, state)
gcloud deploy rollouts describe my-rollout \
    --delivery-pipeline=my-pipeline \
    --release=my-release-20240101-1200 --region=us-central1

# Retry a failed job in a rollout phase
gcloud deploy rollouts retry-job my-rollout \
    --job-id=deploy --phase-id=stable \
    --delivery-pipeline=my-pipeline \
    --release=my-release-20240101-1200 --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `deploy automation-runs` | [`automation-runs.md`](automation-runs.md) | 3 | Manage AutomationRun resources (cancel, describe, list) |
| `deploy automations` | [`automations.md`](automations.md) | 4 | Manage Automation resources (auto-promote/rollback rules) |
| `deploy custom-target-types` | [`custom-target-types.md`](custom-target-types.md) | 8 | Create and manage Custom Target Type resources |
| `deploy delivery-pipelines` | [`delivery-pipelines.md`](delivery-pipelines.md) | 8 | Create and manage Delivery Pipeline resources |
| `deploy deploy-policies` | [`deploy-policies.md`](deploy-policies.md) | 7 | Create and manage Deploy Policy resources (guardrails) |
| `deploy job-runs` | [`job-runs.md`](job-runs.md) | 3 | Manage job run resources (describe, list, terminate) |
| `deploy releases` | [`releases.md`](releases.md) | 5 | Create and manage Release resources |
| `deploy rollouts` | [`rollouts.md`](rollouts.md) | 8 | Create and manage Rollout resources |
| `deploy targets` | [`targets.md`](targets.md) | 10 | Create and manage Target resources |

Top-level commands (see [`_commands.md`](_commands.md)): `gcloud deploy apply`, `gcloud deploy delete`, `gcloud deploy get-config`. See [`index.md`](index.md) for a one-line index of all 59 commands.

## Common flags & tips

- **Region is required almost everywhere.** Pass `--region=us-central1` or set it once with `gcloud config set deploy/region us-central1`. You can also set `gcloud config set deploy/delivery-pipeline my-pipeline` so release/rollout commands don't need `--delivery-pipeline`.
- **Declarative vs. imperative.** `gcloud deploy apply --file=...` creates/updates DeliveryPipelines, Targets, CustomTargetTypes, DeployPolicies, and Automations from one YAML config; `gcloud deploy delete --file=... [--force]` removes them. Use `... export` on most resources to dump the YAML you can re-apply.
- **Release source.** `releases create` defaults `--source` to `.` (the current directory) with a `skaffold.yaml`. Substitute images with `--images=NAME=TAG,...` or supply a Cloud Build output via `--build-artifacts=artifacts.json` (the two are mutually exclusive). Generate a skaffold config from a manifest with `--from-k8s-manifest=` or `--from-run-manifest=`.
- **Date/time in release names.** `$DATE` and `$TIME` expand to the current UTC date/time (e.g. `my-release-20240101-1200`). Single-quote the name so the shell doesn't override them.
- **Deploy policies.** Privileged operations (`releases create/promote`, `rollouts advance/approve/reject/cancel/retry-job/ignore-job`, `targets rollback/redeploy`) accept `--override-deploy-policies=POLICY,...` to bypass active guardrails.
- **Listing/filtering.** `list` commands support standard `--filter`, `--limit`, `--sort-by`, and `--uri`. Examples:
  - `gcloud deploy rollouts list --delivery-pipeline=my-pipeline --release=my-release --region=us-central1 --filter="state=FAILED"`
  - `gcloud deploy releases list --delivery-pipeline=my-pipeline --region=us-central1 --format="table(name, createTime)"`
- **IAM.** DeliveryPipelines, Targets, CustomTargetTypes, and DeployPolicies each support `add-iam-policy-binding` / `remove-iam-policy-binding` / `get-iam-policy` / `set-iam-policy`. Common roles: `roles/clouddeploy.operator`, `roles/clouddeploy.releaser`, `roles/clouddeploy.approver`, `roles/clouddeploy.viewer`.

## beta / alpha

Both `gcloud beta deploy` and `gcloud alpha deploy` exist and mirror the GA command surface — the same nine subgroups (`automation-runs`, `automations`, `custom-target-types`, `delivery-pipelines`, `deploy-policies`, `job-runs`, `releases`, `rollouts`, `targets`) and the same three top-level commands (`apply`, `delete`, `get-config`). No commands or flags are documented as beta/alpha-only; the GA surface already includes Automations, DeployPolicy, and CustomTargetType. Prefer the GA track unless a specific behavior requires beta.

## Official documentation

- [Cloud Deploy overview](https://cloud.google.com/deploy/docs/overview) — product concepts, resource model, and supported runtimes.
- [Create delivery pipelines and targets](https://cloud.google.com/deploy/docs/create-pipeline-targets) — how-to for `gcloud deploy apply`.
- [Deploy your application](https://cloud.google.com/deploy/docs/deploying-application) — creating releases and triggering rollouts.
- [View pipelines and resources](https://cloud.google.com/deploy/docs/view-pipeline) — listing/describing pipelines, targets, releases, rollouts.
- [Configuration file schema](https://cloud.google.com/deploy/docs/config-files) — YAML schema for DeliveryPipeline, Target, Automation, DeployPolicy.
- [IAM roles and permissions](https://cloud.google.com/deploy/docs/iam-roles-permissions) — predefined Cloud Deploy roles.
- [gcloud deploy CLI reference](https://cloud.google.com/sdk/gcloud/reference/deploy) — full command/flag reference.

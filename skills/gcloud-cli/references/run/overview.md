# gcloud run — Cloud Run

## Overview

Cloud Run is Google Cloud's fully managed serverless platform for running containers without managing infrastructure. It exposes two resource types: **services** (long-running containers that serve HTTP requests and autoscale, including to zero) and **jobs** (containers that run a task to completion). Each service deployment produces an immutable **revision**, and traffic can be split, tagged, and rolled back across revisions. `gcloud run deploy` (services) and `gcloud run jobs deploy` (jobs) build from source or a prebuilt image.

## Quick reference — common workflows

### Deploy a service from a prebuilt image
```bash
gcloud services enable run.googleapis.com

gcloud run deploy my-service \
  --image=us-docker.pkg.dev/PROJECT/IMAGE:TAG \
  --region=us-central1 \
  --allow-unauthenticated

gcloud run services describe my-service --region=us-central1 --format=export
```

### Deploy a service from source (builds the image for you)
```bash
# --source triggers a Cloud Build; deploy without serving traffic, then promote.
gcloud run deploy my-service \
  --source=. \
  --region=us-central1 \
  --revision-suffix=v2 \
  --no-traffic

gcloud run services update-traffic my-service \
  --region=us-central1 --to-latest
```

### Split / migrate traffic between revisions (canary, then rollback)
```bash
# Deploy a tagged revision that receives no traffic for pre-release testing.
gcloud run deploy my-service \
  --image=us-docker.pkg.dev/PROJECT/IMAGE:v2 \
  --region=us-central1 --no-traffic --tag=candidate

# Send 10% to the new revision, 90% to the old one.
gcloud run services update-traffic my-service --region=us-central1 \
  --to-revisions=my-service-00002-abc=10,my-service-00001-xyz=90

# Promote to 100% latest and clean up the tag.
gcloud run services update-traffic my-service --region=us-central1 \
  --to-latest --remove-tags=candidate

# Roll back: pin all traffic to a known-good revision.
gcloud run services update-traffic my-service --region=us-central1 \
  --to-revisions=my-service-00001-xyz=100
```

### Create and execute a job
```bash
gcloud run jobs create my-batch-job \
  --image=us-docker.pkg.dev/PROJECT/IMAGE:TAG \
  --region=us-central1 \
  --tasks=10 --parallelism=5 --max-retries=3 --task-timeout=30m

gcloud run jobs execute my-batch-job --region=us-central1 --wait
gcloud run jobs executions list --job=my-batch-job --region=us-central1
gcloud run jobs logs read my-batch-job --region=us-central1
```

### Map a custom domain (fully managed — beta; see note below)
```bash
gcloud beta run domain-mappings create \
  --service=my-service --domain=www.example.com --region=us-central1

gcloud beta run domain-mappings describe \
  --domain=www.example.com --region=us-central1   # shows DNS records to add
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `run domain-mappings` | [`domain-mappings.md`](domain-mappings.md) | 4 | view and manage your Cloud Run for Anthos domain mappings |
| `run jobs` | [`jobs.md`](jobs.md) | 19 | view and manage your Cloud Run jobs |
| `run multi-region-services` | [`multi-region-services.md`](multi-region-services.md) | 5 | manage your Cloud Run multi-region services |
| `run regions` | [`regions.md`](regions.md) | 1 | view available Cloud Run (fully managed) regions |
| `run revisions` | [`revisions.md`](revisions.md) | 3 | view and manage your Cloud Run revisions |
| `run services` | [`services.md`](services.md) | 12 | view and manage your Cloud Run services |

Top-level command (see [`_commands.md`](_commands.md)): `gcloud run deploy` — create or update a Cloud Run service. See [`index.md`](index.md) for a one-line index of all 45 GA commands.

## Common flags & tips

- **Source vs image:** `--image=IMAGE` deploys a prebuilt container; `--source=SOURCE` (e.g. `--source=.`) builds it from local code via Cloud Build.
- **Region:** `--region=us-central1` is required for most commands unless you set `gcloud config set run/region us-central1`.
- **Access:** `--allow-unauthenticated` makes a service public; `--no-allow-unauthenticated` keeps it private (IAM-gated).
- **Env vars:** `--set-env-vars=KEY=VALUE,...` replaces all; `--update-env-vars=KEY=VALUE,...` merges; `--remove-env-vars`, `--clear-env-vars`, `--set-secrets`/`--update-secrets` likewise.
- **Resources & scaling:** `--cpu`, `--memory` (e.g. `--memory=512Mi`), `--concurrency=80`, `--min-instances=1`, `--max-instances=100`, `--timeout`.
- **Traffic (`run services update-traffic`):** `--to-latest`, `--to-revisions=REV=PERCENT,...`, `--to-tags=TAG=PERCENT,...`, plus tag management with `--set-tags`/`--update-tags`/`--remove-tags`/`--clear-tags`.
- **Revision naming:** `--revision-suffix=v2` and `--tag=candidate` make revisions easy to target; `--no-traffic` deploys without shifting traffic.
- **Format / filter:**
  ```bash
  gcloud run services list --region=us-central1 \
    --filter="metadata.name:api-*" --format="table(metadata.name, status.url)"
  gcloud run services describe my-service --region=us-central1 --format=export
  gcloud run services logs read my-service --region=us-central1 \
    --log-filter="severity>=ERROR" --limit=20 --format=json
  ```

## beta / alpha

- **Custom domain mapping (fully managed Cloud Run) requires beta.** The GA `gcloud run domain-mappings` group targets **Cloud Run for Anthos** only. As the GA help states: *"For domain mapping support with fully managed Cloud Run, use gcloud beta run domain-mappings create."* Use `gcloud beta run domain-mappings {create,describe,list,delete}` for fully managed services.
- Beta/alpha tracks generally mirror the GA surface and may expose preview-only capabilities ahead of GA. Add `beta` or `alpha` after `gcloud` (e.g. `gcloud beta run deploy`); these tracks are not documented in the GA reference files here.

## Official documentation

- [Cloud Run product docs](https://cloud.google.com/run/docs) — overview, guides, and reference home.
- [Deploy container images](https://cloud.google.com/run/docs/deploying) — deploy options, sidecars, and flags.
- [Quickstart: deploy a prebuilt container](https://cloud.google.com/run/docs/quickstarts/deploy-container) — fastest first deploy.
- [Create and manage jobs](https://cloud.google.com/run/docs/managing/jobs) — create, execute, list, and delete jobs.
- [Rollouts, rollbacks & traffic migration](https://cloud.google.com/run/docs/rollouts-rollbacks-traffic-migration) — splitting traffic and using tags.
- [Map custom domains](https://cloud.google.com/run/docs/mapping-custom-domains) — verified domain mapping (beta for fully managed).
- [Manage access (IAM)](https://cloud.google.com/run/docs/securing/managing-access) — invoker, developer, admin, and related roles.
- [gcloud run CLI reference](https://cloud.google.com/sdk/gcloud/reference/run) — full command and flag reference.

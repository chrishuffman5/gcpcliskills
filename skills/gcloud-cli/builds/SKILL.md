---
name: gcloud-builds
description: >-
  Cloud Build via gcloud (`gcloud builds`). Create and manage builds for Google Cloud Build — connections, repositories, triggers, worker-pools.
---

# gcloud builds — Cloud Build

## Overview

Cloud Build is Google Cloud's fully managed, serverless CI/CD platform that runs your builds on Google infrastructure. Use `gcloud builds` to submit ad-hoc builds from local or remote source (producing container images, JARs, binaries, etc.), to manage build triggers that fire automatically on source-repository events, and to manage the 2nd-gen source connections/repositories and private worker pools those builds run against. Reach for it whenever you want to compile, test, package, or publish artifacts without managing build servers.

## Quick reference — common workflows

### Submit a build from local source (quick Docker image)

```bash
# Enable the API once per project
gcloud services enable cloudbuild.googleapis.com

# Build the current directory and push the image to Artifact Registry
gcloud builds submit . \
    --tag=us-central1-docker.pkg.dev/MY-PROJECT/my-repo/my-image:latest \
    --region=us-central1
```

### Submit with a cloudbuild.yaml config, substitutions, and a timeout

```bash
gcloud builds submit . \
    --config=cloudbuild.yaml \
    --substitutions=_ENV=prod,_VERSION=1.2.3 \
    --timeout=30m \
    --region=us-central1

# Check what's still running, then tail the logs
gcloud builds list --ongoing --region=us-central1
gcloud builds log BUILD_ID --stream --region=us-central1
```

### Create a 2nd-gen GitHub trigger for push-to-main

```bash
# 1. Create a GitHub connection (prints a URL to authorize in a browser)
gcloud builds connections create github my-github-conn \
    --region=us-central1

# 2. Link a repository to the connection
gcloud builds repositories create my-repo \
    --remote-uri=https://github.com/owner/repo.git \
    --connection=my-github-conn \
    --region=us-central1

# 3. Create a push trigger on the main branch
gcloud builds triggers create github \
    --name=push-to-main \
    --repository=projects/MY-PROJECT/locations/us-central1/connections/my-github-conn/repositories/my-repo \
    --branch-pattern="^main$" \
    --build-config=cloudbuild.yaml \
    --region=us-central1

# 4. List triggers, then run one manually to test it
gcloud builds triggers list --region=us-central1
gcloud builds triggers run push-to-main --branch=main --region=us-central1
```

### Create and use a private worker pool

```bash
# Create a pool peered to a VPC with a custom machine type and disk
gcloud builds worker-pools create my-pool \
    --region=us-central1 \
    --peered-network=projects/MY-PROJECT/global/networks/default \
    --peered-network-ip-range=192.168.0.0/28 \
    --worker-machine-type=e2-standard-2 \
    --worker-disk-size=64GB

# Submit a build that runs on the private pool
gcloud builds submit . \
    --config=cloudbuild.yaml \
    --worker-pool=projects/MY-PROJECT/locations/us-central1/workerPools/my-pool \
    --region=us-central1

# Resize the pool later
gcloud builds worker-pools update my-pool \
    --region=us-central1 \
    --worker-machine-type=e2-highcpu-8 \
    --worker-disk-size=64GB
```

### Monitor and manage running builds

```bash
gcloud builds list                                  # most recent 50 builds
gcloud builds list --ongoing --region=us-central1   # only QUEUED/WORKING
gcloud builds describe BUILD_ID --region=us-central1
gcloud builds log BUILD_ID --stream --region=us-central1
gcloud builds cancel BUILD_ID --region=us-central1
gcloud builds get-default-service-account --region=us-central1
```

### Export and re-import a trigger as YAML

```bash
# Capture an existing trigger to a file
gcloud builds triggers describe MY-TRIGGER --region=us-central1 > trigger.yaml

# Create or update a trigger from the file
gcloud builds triggers import --source=trigger.yaml --region=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `builds` (top-level) | [`_commands.md`](_commands.md) | 6 | submit, list, describe, log, cancel builds; get default service account |
| `builds connections` | [`connections.md`](connections.md) | 16 | manage 2nd-gen source connections (GitHub, GitLab, Bitbucket) and their IAM |
| `builds repositories` | [`repositories.md`](repositories.md) | 4 | manage repositories linked to a connection |
| `builds triggers` | [`triggers.md`](triggers.md) | 23 | create, run, import, and manage build triggers |
| `builds worker-pools` | [`worker-pools.md`](worker-pools.md) | 5 | manage private worker pools |

See [`index.md`](index.md) for a one-line index of all 54 GA commands.

## Common flags & tips

- **`--region`** — almost every command takes it. If unset it falls back to the `builds/region` property, then to `global`. 2nd-gen repositories, triggers, and worker pools require an explicit region (`global` is not supported for them). Set a default with `gcloud config set builds/region us-central1`. Available regions: https://cloud.google.com/build/docs/locations.
- **`gcloud builds submit`** — source can be a local directory, a `.zip`/`.tar.gz`/manifest `.json` in Cloud Storage, a Git URL, a 2nd-gen repository resource, or a Developer Connect link. Local uploads honor `.gcloudignore` (or `--ignore-file`). Pick exactly one output mode: `--tag`/`-t` (Dockerfile build), `--config` (default `cloudbuild.yaml`), or `--pack` (buildpacks). Use `--no-source` to skip uploading source.
- **`--substitutions=KEY=VALUE,...`** — user-defined keys must start with `_` (e.g. `_ENV=prod`). On `submit`/`triggers run` only these built-ins may be set: `REPO_NAME, BRANCH_NAME, TAG_NAME, REVISION_ID, COMMIT_SHA, SHORT_SHA`.
- **`--machine-type`** (on `submit`) accepts only: `e2-highcpu-32, e2-highcpu-8, e2-medium, n1-highcpu-32, n1-highcpu-8`. Worker-pool machine types (`--worker-machine-type`) are separate and accept general Compute Engine types such as `e2-standard-2`.
- **`--async`** returns immediately instead of waiting/streaming; pair with `gcloud builds log --stream` later. `--suppress-logs` keeps a synchronous submit quiet.
- **Trigger types** — `triggers create` has subcommands per source: `github`, `gitlab`, `bitbucket-cloud`, `bitbucket-data-center`, `bitbucketserver`, `cloud-source-repositories`, `manual`, `pubsub`, `webhook`. Event matching uses `--branch-pattern`, `--tag-pattern`, or `--pull-request-pattern` (mutually exclusive regexes). Build definition uses one of `--build-config`, `--inline-config`, or `--dockerfile`.
- **Filtering / formatting:** `gcloud builds list --filter="status=FAILURE" --format="table(id,status,createTime)"` or `--format="value(id)"` to pipe IDs. `--ongoing` is a shortcut for QUEUED/WORKING.
- **2nd-gen connection secrets** live in Secret Manager and are passed as version resources, e.g. `--authorizer-token-secret-version=projects/PROJ/secrets/NAME/versions/1`.

## beta / alpha

`gcloud beta builds` adds a manual-approval workflow not present in GA:

- **`gcloud beta builds approve BUILD`** — approve a build that is pending approval.
- **`gcloud beta builds reject BUILD`** — reject a pending build.

These apply when a trigger was created/updated with `--require-approval` (the `--[no-]require-approval` flag exists on GA `triggers create`/`triggers update`, but the approve/reject actions themselves are exposed under beta). All four subgroups (`connections`, `repositories`, `triggers`, `worker-pools`) exist in beta and alpha with the same surface as GA.

## Official documentation

- Cloud Build product docs home: https://cloud.google.com/build/docs/overview — what Cloud Build is and its core concepts.
- Quickstart (build & push a Docker image): https://cloud.google.com/build/docs/quickstart-build
- Create a basic build configuration (`cloudbuild.yaml`): https://cloud.google.com/build/docs/configuring-builds/create-basic-configuration
- Substitution variables: https://cloud.google.com/build/docs/configuring-builds/substitute-variable-values
- Create & manage build triggers: https://cloud.google.com/build/docs/automating-builds/create-manage-triggers
- Private pools overview: https://cloud.google.com/build/docs/private-pools/private-pools-overview
- IAM roles & permissions: https://cloud.google.com/build/docs/iam-roles-permissions
- Supported regions: https://cloud.google.com/build/docs/locations
- gcloud CLI reference: https://cloud.google.com/sdk/gcloud/reference/builds

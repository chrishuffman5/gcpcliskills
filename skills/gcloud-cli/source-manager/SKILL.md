---
name: gcloud-source-manager
description: >-
  Secure Source Manager via gcloud (`gcloud source-manager`). Manage Secure Source Manager resources — instances, locations, operations, repos.
---

# gcloud source-manager — Secure Source Manager

## Overview

Secure Source Manager is a regionally deployed, single-tenant managed Git service hosted on Google Cloud. It provides private Git repositories with pull requests, issue tracking, HTTPS/SSH authentication, optional CMEK encryption, and Private Service Connect (PSC) for private instances. Reach for `gcloud source-manager` to provision instances, create repositories within them, and manage IAM access at both the instance and repository level. Repository content itself (commits, branches, files) is managed with ordinary `git` once an instance and repo exist.

## Quick reference — common workflows

### Enable the API and list available locations
```bash
gcloud services enable securesourcemanager.googleapis.com

# Locations where Secure Source Manager is available
gcloud source-manager locations list
```

### Create an instance and verify it
```bash
# Asynchronous create (default)
gcloud source-manager instances create my-instance \
    --region=us-central1

# Synchronous create — wait up to 30 minutes
gcloud source-manager instances create my-instance \
    --region=us-central1 --no-async --max-wait=30m

gcloud source-manager instances describe my-instance \
    --region=us-central1
```

### Create a private (PSC + CMEK) instance
```bash
gcloud source-manager instances create my-private-instance \
    --region=us-central1 \
    --is-private \
    --ca-pool=projects/PROJECT_ID/locations/us-central1/caPools/MY_CA_POOL \
    --psc-allowed-projects=PROJECT_ID \
    --kms-key=projects/PROJECT_ID/locations/us-central1/keyRings/MY_RING/cryptoKeys/MY_KEY \
    --no-async --max-wait=60m
```

### Create and inspect a repository
```bash
# Create with an initialized default branch
gcloud source-manager repos create my-repo \
    --region=us-central1 \
    --instance=my-instance \
    --description="My project repository" \
    --default-branch=main

# List repos under an instance
gcloud source-manager repos list \
    --region=us-central1 \
    --instance=my-instance

gcloud source-manager repos describe my-repo \
    --region=us-central1
```

### Grant instance and repository access
```bash
# Instance-level access (view-only accessor)
gcloud source-manager instances add-iam-policy-binding my-instance \
    --region=us-central1 \
    --member=user:alice@example.com \
    --role=roles/securesourcemanager.instanceAccessor

# Repository-level admin access
gcloud source-manager repos add-iam-policy-binding my-repo \
    --region=us-central1 \
    --member=user:alice@example.com \
    --role=roles/securesourcemanager.repoAdmin

# Review the repo's effective policy
gcloud source-manager repos get-iam-policy my-repo \
    --region=us-central1
```

### Update and delete resources
```bash
gcloud source-manager repos update my-repo \
    --region=us-central1 \
    --description="Updated description"

gcloud source-manager repos delete my-repo \
    --region=us-central1

# Synchronous instance delete
gcloud source-manager instances delete my-instance \
    --region=us-central1 --no-async --max-wait=30m
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `source-manager instances` | [`instances.md`](instances.md) | 8 | Manage instances and their IAM policies |
| `source-manager locations` | [`locations.md`](locations.md) | 1 | List locations where Secure Source Manager is available |
| `source-manager operations` | [`operations.md`](operations.md) | 2 | Describe and list long-running operations |
| `source-manager repos` | [`repos.md`](repos.md) | 9 | Manage repositories and their IAM policies |

See [`index.md`](index.md) for a one-line index of all 20 GA commands.

## Common flags & tips

- **`--region` is required almost everywhere.** Every instance, repo, and operation command needs a `--region` (the Secure Source Manager location), e.g. `--region=us-central1`. Alternatively, pass a fully qualified resource name as the positional argument. Use `locations list` to discover valid regions.
- **Async by default.** `instances create` and `instances delete` return immediately (`--async`, on by default). Use `--no-async` to block, paired with `--max-wait` (default `60m`) to cap the synchronous wait, e.g. `--no-async --max-wait=30m`. Track in-progress work with `operations list --region=...` and `operations describe`.
- **Two IAM levels.** Instance roles are applied with `instances add-iam-policy-binding` / `set-iam-policy` / `remove-iam-policy-binding`; repository roles use the matching `repos` commands. Common roles: `roles/securesourcemanager.instanceOwner`, `instanceAccessor`, `instanceRepositoryCreator`, `repoAdmin`, `repoCreator`, `repoReader`, `repoWriter`.
- **Repository initialization.** On `repos create`, `--default-branch` enables optional content seeding alongside `--gitignores`, `--license`, and `--readme`; `--description` is limited to 500 characters.
- **Private instances.** `--is-private` requires `--ca-pool` and optionally `--psc-allowed-projects`; add `--kms-key` for CMEK. `--enable-workforce-identity-federation` configures workforce identity federation.
- **Filtering & formatting.** List/get-iam-policy commands accept the standard `--filter`, `--limit`, `--sort-by`, and `--page-size`. Examples:
  - `gcloud source-manager repos list --region=us-central1 --instance=my-instance --limit=20`
  - `gcloud source-manager instances list --region=us-central1 --format="table(name, state)"`
- **Safe-by-default edits.** `repos update --validate-only` previews a change without applying it; `repos delete --allow-missing` makes deletes idempotent.

## beta / alpha

Both `gcloud beta source-manager` and `gcloud alpha source-manager` exist and mirror the same four command groups (`instances`, `locations`, `operations`, `repos`). No subcommands were found that exist only in alpha/beta and not in GA — the GA surface is feature-equivalent at this time. The beta and alpha tracks carry the usual "might change without notice" caveat.

## Official documentation

- [Secure Source Manager docs home](https://cloud.google.com/secure-source-manager/docs) — guides, reference, and resources.
- [Product overview](https://cloud.google.com/secure-source-manager/docs/overview) — single-tenant private Git hosting on Google Cloud.
- [Create an instance](https://cloud.google.com/secure-source-manager/docs/create-instance) — provision an instance via gcloud, Console, or Terraform.
- [Create and clone a repository](https://cloud.google.com/secure-source-manager/docs/create-clone-repository) — create a repo and clone it with Git credentials.
- [Access control (IAM)](https://cloud.google.com/secure-source-manager/docs/access-control) — IAM roles and permissions reference.
- [Grant instance access](https://cloud.google.com/secure-source-manager/docs/grant-users-instance-access) — grant instance-level IAM access via gcloud.
- [gcloud CLI reference](https://cloud.google.com/sdk/gcloud/reference/source-manager) — all GA command groups.
- [gcloud beta CLI reference](https://cloud.google.com/sdk/gcloud/reference/beta/source-manager) — beta command surface.

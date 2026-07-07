---
name: gcloud-gemini
description: >-
  Gemini Code Assist & Cloud Assist (admin) via gcloud (`gcloud gemini`). Manage resources associated with Gemini Code Assist and Gemini Cloud Assist — code-repository-indexes, code-tools-settings, data-sharing-with-google-settings, gemini-gcp-enablement-settings, logging-settings, operations, release-channel-settings.
---

# gcloud gemini — Gemini Code Assist & Cloud Assist (admin)

## Overview

`gcloud gemini` manages the administrative configuration for **Gemini for Google Cloud** — primarily **Gemini Code Assist** (AI code completion, generation, and chat in IDEs, with Enterprise private-repo code customization) and **Gemini Cloud Assist** (AI assistant for understanding and operating Google Cloud). Reach for it when you administer these products at the project/org level: building code repository indexes for code customization, and managing logging, web-grounding (`gemini-gcp-enablement-settings`), release-channel, code-tools, and data-sharing settings plus their target bindings. It is an admin surface, not the IDE/chat experience itself — the underlying API is `cloudaicompanion.googleapis.com`. All commands are GA (67 commands across 7 groups).

## Quick reference — common workflows

### Enable the API and grant a user access

```bash
gcloud services enable cloudaicompanion.googleapis.com --project=PROJECT_ID

gcloud projects add-iam-policy-binding PROJECT_ID \
    --member=user:EMAIL_ADDRESS \
    --role=roles/cloudaicompanion.user

gcloud projects add-iam-policy-binding PROJECT_ID \
    --member=user:EMAIL_ADDRESS \
    --role=roles/serviceusage.serviceUsageConsumer
```

### Create a code repository index for code customization (Enterprise)

```bash
# Create the index instance
gcloud gemini code-repository-indexes create my-index \
    --project=my-project --location=us-central1

# Confirm it exists / list all indexes in the location
gcloud gemini code-repository-indexes describe my-index \
    --project=my-project --location=us-central1
gcloud gemini code-repository-indexes list \
    --project=my-project --location=us-central1
```

### Group repositories under an index (Developer Connect)

```bash
# Create a repository group pointing at a Developer Connect Git repo link
gcloud gemini code-repository-indexes repository-groups create my-repo-group \
    --code-repository-index=my-index \
    --project=my-project --location=us-central1 \
    --repositories=branchPattern=.*,resource=developerconnect.googleapis.com/projects/PROJECT/locations/LOCATION/connections/CONNECTION/gitRepositoryLinks/REPO

# Narrow indexing to the main branch later
gcloud gemini code-repository-indexes repository-groups update my-repo-group \
    --code-repository-index=my-index \
    --project=my-project --location=us-central1 \
    --repositories=branchPattern=main,resource=developerconnect.googleapis.com/projects/PROJECT/locations/LOCATION/connections/CONNECTION/gitRepositoryLinks/REPO
```

The Developer Connect Git repository link must already exist (`branchPattern` uses RE2 syntax).

### Log Gemini prompts and responses, then bind to a target

```bash
gcloud gemini logging-settings create my-logging-setting \
    --project=my-project --location=global \
    --log-prompts-and-responses --log-metadata

gcloud gemini logging-settings setting-bindings create my-binding \
    --logging-setting=my-logging-setting \
    --project=my-project --location=global \
    --target=//cloudresourcemanager.googleapis.com/projects/TARGET_PROJECT_NUMBER \
    --product=gemini-code-assist
```

### Configure web grounding (enablement settings)

```bash
# Grounding with Google Search for Enterprise
gcloud gemini gemini-gcp-enablement-settings create my-enablement \
    --project=my-project --location=global \
    --web-grounding-type=web-grounding-for-enterprise

# Switch to standard Google Search grounding
gcloud gemini gemini-gcp-enablement-settings update my-enablement \
    --project=my-project --location=global \
    --web-grounding-type=grounding-with-google-search
```

### Pin a release channel and bind it to a target

```bash
gcloud gemini release-channel-settings create my-channel-setting \
    --project=my-project --location=global \
    --release-channel=stable

gcloud gemini release-channel-settings setting-bindings create my-binding \
    --release-channel-setting=my-channel-setting \
    --project=my-project --location=global \
    --target=//cloudresourcemanager.googleapis.com/projects/TARGET_PROJECT_NUMBER \
    --product=gemini-code-assist
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `gemini code-repository-indexes` | [`code-repository-indexes.md`](code-repository-indexes.md) | 12 | manage Code Repository Index resources (incl. `repository-groups`, with IAM policy) |
| `gemini code-tools-settings` | [`code-tools-settings.md`](code-tools-settings.md) | 10 | manage Code Tools Setting resources (incl. `setting-bindings`) |
| `gemini data-sharing-with-google-settings` | [`data-sharing-with-google-settings.md`](data-sharing-with-google-settings.md) | 10 | manage Data Sharing With Google Setting resources (incl. `setting-bindings`) |
| `gemini gemini-gcp-enablement-settings` | [`gemini-gcp-enablement-settings.md`](gemini-gcp-enablement-settings.md) | 10 | manage Gemini GCP Enablement Setting resources, incl. web grounding (incl. `setting-bindings`) |
| `gemini logging-settings` | [`logging-settings.md`](logging-settings.md) | 10 | manage Logging Setting resources for prompt/response & metadata logging (incl. `setting-bindings`) |
| `gemini operations` | [`operations.md`](operations.md) | 5 | manage long-running Operation resources |
| `gemini release-channel-settings` | [`release-channel-settings.md`](release-channel-settings.md) | 10 | manage Release Channel Setting resources (incl. `setting-bindings`) |

See [`index.md`](index.md) for a one-line index of all 67 commands.

## Common flags & tips

- **Resource scoping is always `--project` + `--location`.** Settings resources (logging, enablement, release-channel, code-tools, data-sharing) typically use `--location=global`; code repository indexes are regional (e.g. `--location=us-central1`).
- **Settings have a two-step model:** create the setting, then create a `setting-bindings` child that ties it to a `--target` (a resource URI such as `//cloudresourcemanager.googleapis.com/projects/PROJECT_NUMBER`) and a `--product`. Valid `--product` values: `gemini-cloud-assist`, `gemini-code-assist`, `gemini-in-bigquery`, `gemini-in-looker`.
- **Repository groups** take `--repositories=branchPattern=...,resource=...` (repeatable, or `--repositories=@file.json`); `branchPattern` is RE2 regex. On `update` you can also use `--add-repositories` / `--remove-repositories` / `--clear-repositories`.
- **Async operations:** create/update/delete on indexes and bindings accept `--async`; track results with `gcloud gemini operations describe|wait|list --location=LOCATION`.
- **Labels** are editable via `--update-labels` / `--remove-labels` / `--clear-labels` on `update` commands.
- **`--kms-key`** (CMEK) can only be set at index creation, not on update.
- **Filtering / formatting** on `list`:
  - `gcloud gemini code-repository-indexes list --location=us-central1 --filter="labels.env=prod" --format="table(name, createTime)"`
  - `gcloud gemini operations list --location=us-central1 --filter="done=false"`
- Delete an index together with its repository groups using `--force` (otherwise it must be empty).

## beta / alpha

The full GA surface (67 commands) is available under `gcloud gemini` with no `beta`/`alpha` prefix; no capabilities are documented as beta/alpha-only at this time. Note that in `gemini-gcp-enablement-settings`, `--disable-web-grounding` is **DEPRECATED** — use `--web-grounding-type` (`grounding-with-google-search` or `web-grounding-for-enterprise`) instead.

## Official documentation

- Gemini for Google Cloud docs home (covers Code Assist, Cloud Assist, data governance, responsible AI): https://cloud.google.com/gemini/docs
- Gemini Code Assist product overview (Standard & Enterprise editions): https://cloud.google.com/gemini/docs/codeassist/overview
- Set up Gemini Code Assist (enable API, IAM roles, project config): https://cloud.google.com/gemini/docs/codeassist/set-up-gemini
- Code customization overview (how private-repo indexing works): https://cloud.google.com/gemini/docs/codeassist/code-customization-overview
- Gemini Cloud Assist docs home: https://cloud.google.com/cloud-assist/
- gcloud CLI reference for this group: https://cloud.google.com/sdk/gcloud/reference/gemini

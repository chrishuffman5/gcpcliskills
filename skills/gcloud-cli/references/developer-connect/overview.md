# gcloud developer-connect — Developer Connect

## Overview

Developer Connect is a Google Cloud service for securely linking source-code management (SCM) repositories — GitHub, GitHub Enterprise, GitLab, GitLab Enterprise, Bitbucket Cloud, Bitbucket Data Center, and generic HTTP endpoints — to Google Cloud services such as Cloud Build, Cloud Run, Firebase App Hosting, and Vertex AI Agent Builder. Credentials (OAuth tokens, webhook secrets, private keys) are referenced from Secret Manager rather than stored directly. Reach for it when you need a managed, reusable connection to a Git provider, short-lived read/write tokens for linked repositories, or Developer Connect Insights to map app runtimes, artifacts, and build provenance.

## Quick reference — common workflows

### 1. Enable the API and create a GitHub connection
```bash
gcloud services enable developerconnect.googleapis.com

# Store the GitHub OAuth token in Secret Manager, then reference its version
gcloud developer-connect connections create my-connection \
    --github-config-app=developer-connect \
    --github-config-authorizer-credential-oauth-token-secret-version=projects/my-project/secrets/my-oauth-token/versions/1 \
    --github-config-app-installation-id=12345 \
    --location=us-central1
```

### 2. Link a Git repository to a connection and list links
```bash
gcloud developer-connect connections git-repository-links create my-git-repository-link \
    --clone-uri=https://github.com/my-org/my-repo.git \
    --connection=my-connection \
    --location=us-central1

gcloud developer-connect connections git-repository-links list \
    --connection=my-connection \
    --location=us-central1
```

### 3. Fetch short-lived tokens for a linked repository
```bash
# Read-only token (e.g. for a CI clone)
gcloud developer-connect connections git-repository-links fetch-read-token my-git-repository-link \
    --connection=my-connection \
    --location=us-central1 \
    --project=my-project

# Read/write token (e.g. for push access)
gcloud developer-connect connections git-repository-links fetch-read-write-token my-git-repository-link \
    --connection=my-connection \
    --location=us-central1 \
    --project=my-project
```

### 4. Inspect, disable, and delete a connection
```bash
gcloud developer-connect connections list --location=us-central1
gcloud developer-connect connections describe my-connection --location=us-central1

# Disable repository API methods and webhook processing for the connection
gcloud developer-connect connections update my-connection --disabled --location=us-central1

# Delete the connection
gcloud developer-connect connections delete my-connection --location=us-central1
```

### 5. Set up Developer Connect Insights
```bash
# Scope to specific projects...
gcloud developer-connect insights-configs create insights-config-name \
    --target-projects=project1,project2 \
    --location=us-central1

# ...or to an App Hub application
gcloud developer-connect insights-configs create insights-config-name \
    --app-hub-application=projects/my-project/locations/us-central1/applications/my-app-hub-application \
    --location=us-central1

# Kick off the discovery flow, then check status
gcloud developer-connect insights-configs update insights-config-name --run-discovery --location=us-central1
gcloud developer-connect insights-configs describe insights-config-name --location=us-central1
```

### 6. Track long-running operations
```bash
gcloud developer-connect operations list --location=us-central1
gcloud developer-connect operations describe OPERATION --location=us-central1
gcloud developer-connect operations wait OPERATION --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `developer-connect connections` | [`connections.md`](connections.md) | 11 | manage connection resources (incl. `git-repository-links` subgroup) |
| `developer-connect insights-configs` | [`insights-configs.md`](insights-configs.md) | 5 | manage Insights Config resources |
| `developer-connect operations` | [`operations.md`](operations.md) | 5 | manage Operation resources |

See [`index.md`](index.md) for a one-line index of all 21 GA commands.

## Common flags & tips

- **`--location` is region-scoped and almost always required.** `connections`, `insights-configs`, and `operations` resources are regional; list/describe/create/delete/update commands need `--location` (or a fully qualified resource path). Common region: `us-central1`.
- **Provider config is a one-of choice on `connections create`.** Pick exactly one provider block: GitHub (`--github-config-app`, `--github-config-app-installation-id`, `--github-config-authorizer-credential-oauth-token-secret-version`), GitHub Enterprise (`--github-enterprise-config-host-uri`, ...), GitLab / GitLab Enterprise (`--gitlab-config-*` / `--gitlab-enterprise-config-*`), Bitbucket Cloud / Data Center (`--bitbucket-cloud-config-*` / `--bitbucket-data-center-config-*`), or generic HTTP (`--http-config-host-uri` with `--http-config-bearer-token-authentication-secret-version` or `--http-config-basic-authentication-*`).
- **Credentials come from Secret Manager.** Token/secret/private-key flags take a secret *version* resource path (e.g. `projects/PROJECT/secrets/NAME/versions/1`). Use `--secret`, `--location`, and `--namespace` as fallback values when you pass a short ID instead of a full URI path.
- **Git proxy.** Enable Git-over-HTTPS proxying with `--git-proxy-config-enabled` on `connections create`, or toggle it on update via `--[no-]git-proxy-config-enabled` / `--clear-git-proxy-config`.
- **CMEK.** Encrypt a connection with a customer-managed key using `--crypto-key-config-reference` (paired with `--key-ring`).
- **`--async` + operations.** Mutating commands accept `--async` to return immediately; track the returned operation with `gcloud developer-connect operations wait OPERATION --location=...`.
- **Idempotency & safety.** `--request-id` (a UUID) makes retries idempotent; `--etag` guards updates/deletes against stale state; `--validate-only` checks a request without applying it.
- **Useful `--filter` / `--format` examples:**
  - `gcloud developer-connect connections list --location=us-central1 --filter="disabled=true"`
  - `gcloud developer-connect connections list --location=us-central1 --format="table(name, createTime)"`
  - `gcloud developer-connect operations list --location=us-central1 --filter="done=false"`

## beta / alpha

- **`gcloud beta developer-connect`** mirrors the GA subgroups (`connections`, `insights-configs`, `operations`); no beta-exclusive commands are documented.
- **`gcloud alpha developer-connect`** adds an `account-connectors` subgroup (Preview): Account Connectors link individual Google Cloud user accounts to an SCM provider's OAuth identity. This feature is subject to Pre-GA terms and may change without notice.

## Official documentation

- [Developer Connect documentation home](https://cloud.google.com/developer-connect/docs) — quickstarts, how-to guides, and API reference.
- [Product overview](https://cloud.google.com/developer-connect/docs/overview) — concepts: Git connections, HTTP connections, Account Connectors, Insights.
- [HTTP connections](https://cloud.google.com/developer-connect/docs/http-connections) — connecting to arbitrary HTTP endpoints without a user present.
- [Account connectors](https://cloud.google.com/developer-connect/docs/account-connectors) — Preview feature linking user accounts to SCM providers.
- [Developer Connect Insights](https://cloud.google.com/developer-connect/docs/insights) — mapping app runtimes, artifacts, and build provenance for deployment diagnostics.
- [Set up Developer Connect Insights](https://cloud.google.com/developer-connect/docs/set-up-insights) — how-to with gcloud examples.
- [Access control (IAM)](https://cloud.google.com/developer-connect/docs/access-control) — predefined roles and permissions.
- [gcloud developer-connect reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect) — all GA subgroups and commands.

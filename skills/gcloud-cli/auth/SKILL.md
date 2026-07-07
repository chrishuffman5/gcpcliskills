---
name: gcloud-auth
description: >-
  Credentials & authentication via gcloud (`gcloud auth`). Manage oauth2 credentials for the Google Cloud CLI — application-default, enterprise-certificate-config.
---

# gcloud auth — Credentials & authentication

## Overview

`gcloud auth` manages the Google Cloud CLI's own credentials — the OAuth2 tokens, service account keys, and Application Default Credentials (ADC) that let gcloud (and Google client libraries) authenticate to Google Cloud APIs. It is not a cloud API service; it is the credential-management layer of the Cloud SDK. Reach for it to log in interactively, activate a service account, set up ADC for local development, mint access/identity tokens, or revoke stored credentials.

There is no API to enable. Installing the [Google Cloud SDK](https://cloud.google.com/sdk/docs/install) is the only prerequisite; basic user login needs no project-level IAM role.

## Quick reference — common workflows

### 1. First-time interactive login (user account)

```bash
# Authorize gcloud with your Google account (opens a browser)
gcloud auth login

# Verify the active account
gcloud auth list
```

### 2. Login on a headless / remote machine (no local browser)

```bash
# Print a URL to paste into a browser on another machine, then return the code
gcloud auth login --no-launch-browser

# Or delegate the browser step to a second trusted machine that has gcloud
gcloud auth login --no-browser
```

### 3. Activate a service account from a key file

```bash
# Authorize gcloud using a downloaded JSON service account key, set the project
gcloud auth activate-service-account SA_EMAIL@PROJECT.iam.gserviceaccount.com \
    --key-file=/path/to/key.json \
    --project=PROJECT_ID

# Confirm the service account is now active
gcloud auth list
```

### 4. Set up Application Default Credentials (ADC) for local development

```bash
# Generate ADC credentials for client libraries (stored in a well-known location)
gcloud auth application-default login

# Set/update the quota project ADC bills against
gcloud auth application-default set-quota-project PROJECT_ID

# Print the ADC access token (handy for curl testing)
gcloud auth application-default print-access-token
```

### 5. Use a bearer token with an external HTTP client

```bash
# Print the active account's access token, then call a Google API with it
TOKEN=$(gcloud auth print-access-token)
curl -H "Authorization: Bearer ${TOKEN}" \
     -H "X-Goog-User-Project: PROJECT_ID" \
     https://storage.googleapis.com/storage/v1/b/BUCKET_NAME/o
```

### 6. Authenticate with Workload / Workforce Identity Federation

```bash
# Workload identity federation: pass an external-account config file (or SA key JSON)
gcloud auth login --cred-file=/path/to/workload-identity-config.json

# Workforce identity federation: browser-based sign-in via a login config file
gcloud auth login --login-config=/path/to/workforce-login-config.json
```

### 7. Revoke credentials and clean up

```bash
# Revoke the current active account's credentials (logs out of that account)
gcloud auth revoke

# Revoke all stored credentials at once
gcloud auth revoke --all

# Revoke ADC credentials specifically and delete the local ADC file
gcloud auth application-default revoke
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `auth` (top-level) | [`_commands.md`](_commands.md) | 7 | login, list, revoke, activate-service-account, configure-docker, print-access-token, print-identity-token |
| `auth application-default` | [`application-default.md`](application-default.md) | 4 | Manage your active Application Default Credentials (ADC) |
| `auth enterprise-certificate-config` | [`enterprise-certificate-config.md`](enterprise-certificate-config.md) | 3 | Create enterprise certificate configurations for mTLS (Linux/macOS/Windows) |

See [`index.md`](index.md) for a one-line index of all 14 commands.

## Common flags & tips

- **Headless auth:** `--no-launch-browser` prints a URL to paste into a browser elsewhere; `--no-browser` bootstraps the flow from a second machine that also has gcloud. Both apply to `auth login` and `auth application-default login`.
- **External accounts:** `auth login --cred-file=FILE` accepts a workload identity-pool config or a service account key JSON; `--login-config=FILE` drives workforce identity federation sign-in.
- **Sync ADC with login:** `gcloud auth login --update-adc` writes the obtained user credentials into the ADC well-known location too.
- **Tokens:** `print-access-token` and `print-identity-token` default to the active account; pass an `[ACCOUNT]` positional or `--impersonate-service-account` to target another identity. `--lifetime` extends a token (service-account impersonation only). `print-identity-token` supports `--audiences`, `--include-email`, and `--token-format=full --include-license`.
- **Quota project:** if a token returns "API has not been used in project ... or it is disabled", supply a quota project via the `X-Goog-User-Project` header (the identity needs `serviceusage.services.use`). For ADC, set it with `auth application-default set-quota-project`, or skip it with `auth application-default login --disable-quota-project`.
- **Scripting account selection:** filter the account list, e.g.
  - Active account name: `gcloud auth list --filter=status:ACTIVE --format="value(account)"`
  - One account only: `gcloud auth list --filter-account=SA_EMAIL`
- **Docker registries:** `gcloud auth configure-docker [REGISTRIES]` registers gcloud as a Docker credential helper (e.g. `gcloud auth configure-docker gcr.io`).
- **ADC scopes:** `auth application-default login --scopes=...` controls the granted scopes; non-Google-Cloud scopes (e.g. Drive) require your own OAuth client via `--client-id-file`.

## beta / alpha

Nearly all `gcloud auth` commands are GA, and `gcloud beta auth` mirrors the GA surface almost exactly — `print-identity-token` and `enterprise-certificate-config` exist at both GA and beta. There is no significant capability gap; beta/alpha variants "may change without notice." See the [beta reference](https://cloud.google.com/sdk/gcloud/reference/beta/auth) for the current beta command list.

## Official documentation

- [Cloud SDK — Authorizing the gcloud CLI](https://cloud.google.com/sdk/docs/authorizing) — primary guide to credential types and authorization flows.
- [Authentication overview](https://cloud.google.com/docs/authentication) — user vs. service accounts vs. workload/workforce identity federation, and when to use each.
- [Application Default Credentials](https://cloud.google.com/docs/authentication/application-default-credentials) — ADC search order and how `application-default login` stores credentials.
- [Initializing the gcloud CLI](https://cloud.google.com/sdk/docs/initializing) — establishing credentials from scratch with `gcloud init` / `gcloud auth login`.
- [Workload identity federation](https://cloud.google.com/iam/docs/workload-identity-federation) — external credentials (AWS, Azure, on-prem) via `--cred-file`.
- [Workforce identity federation](https://cloud.google.com/iam/docs/workforce-identity-federation) — browser-based or headless OIDC/SAML login via `--login-config`.
- [Service account overview](https://cloud.google.com/iam/docs/service-account-overview) — service account concepts and roles for impersonation / key-based auth.
- [gcloud auth reference](https://cloud.google.com/sdk/gcloud/reference/auth) — full CLI reference for all `gcloud auth` commands.

# gcloud iap — Identity-Aware Proxy (Cloud IAP)

## Overview

Identity-Aware Proxy (IAP) establishes an application-level authorization layer for HTTPS and TCP
access to Google Cloud resources, letting you control who can reach an app or VM by identity and
context instead of relying on network-level firewalls or a VPN. Reach for `gcloud iap` to enable
IAP on App Engine apps, Compute Engine backend services, and forwarding rules; to grant
per-resource access via IAM bindings; to manage TCP tunnel Destination Groups; and to read/write
IAP resource settings (CORS, GCIP/Identity Platform tenants, login hints).

## Quick reference — common workflows

### 1. Enable IAP on a Compute Engine backend service and grant access

```bash
# Enable the IAP API (one-time per project)
gcloud services enable iap.googleapis.com

# Enable IAP on a global backend service (OAuth client ID + secret required)
gcloud iap web enable --resource-type=backend-services \
    --oauth2-client-id=CLIENT_ID --oauth2-client-secret=SECRET \
    --service=SERVICE_ID

# For a regional backend service, add --region
gcloud iap web enable --resource-type=backend-services \
    --oauth2-client-id=CLIENT_ID --oauth2-client-secret=SECRET \
    --service=SERVICE_ID --region=REGION

# Grant a group access to the IAP-protected app
gcloud iap web add-iam-policy-binding --resource-type=backend-services \
    --service=SERVICE_ID \
    --member='group:eng@example.com' \
    --role='roles/iap.httpsResourceAccessor'
```

### 2. Enable IAP on an App Engine application

```bash
gcloud iap web enable --resource-type=app-engine \
    --oauth2-client-id=CLIENT_ID --oauth2-client-secret=SECRET

# Verify the IAM policy on the App Engine app
gcloud iap web get-iam-policy --resource-type=app-engine

# Grant a single user access
gcloud iap web add-iam-policy-binding --resource-type=app-engine \
    --member='user:alice@example.com' \
    --role='roles/iap.httpsResourceAccessor'
```

### 3. Define a TCP tunnel Destination Group and grant tunnel access

A Destination Group describes the set of IP ranges / FQDNs that an IAP TCP tunnel may reach.
(The tunnel itself is opened with `gcloud compute ssh`/`start-iap-tunnel` `--tunnel-through-iap`,
which lives in the `compute` group, not here.)

```bash
# Create a regional Destination Group from CIDR ranges
gcloud iap tcp dest-groups create my-group --region=us-west1 \
    --ip-range-list=CIDR1,CIDR2

# Grant tunnel access on the Destination Group
gcloud iap tcp dest-groups add-iam-policy-binding \
    --dest-group=my-group --region=us-west1 \
    --member='user:alice@example.com' \
    --role='roles/iap.tunnelResourceAccessor'

# List Destination Groups across all regions
gcloud iap tcp dest-groups list
```

### 4. Read and update IAP resource settings (CORS, GCIP tenants)

```bash
# Get current settings for a backend service
gcloud iap settings get --project=PROJECT_ID \
    --resource-type=backend-services --service=SERVICE_ID

# Apply settings from a YAML file
gcloud iap settings set iap_settings.yaml --project=PROJECT_ID \
    --resource-type=backend-services --service=SERVICE_ID
```

Example `iap_settings.yaml` (CORS preflight + GCIP/Identity Platform tenants):

```yaml
accessSettings:
  corsSettings:
    allowHttpOptions: true
  gcipSettings:
    tenantIds:
    - tenant1-p9puj
    loginPageUri: https://auth.example.com/?apiKey=abcd_efgh
```

### 5. Manage the web IAM policy by file, then disable IAP

```bash
# Export the policy, edit, and re-apply (etag guards against concurrent writes)
gcloud iap web get-iam-policy --resource-type=backend-services \
    --service=SERVICE_ID --format=json > policy.json
gcloud iap web set-iam-policy policy.json --resource-type=backend-services \
    --service=SERVICE_ID

# Remove a single binding
gcloud iap web remove-iam-policy-binding --resource-type=backend-services \
    --service=SERVICE_ID \
    --member='user:alice@example.com' \
    --role='roles/iap.httpsResourceAccessor'

# Disable IAP (OAuth credentials are preserved)
gcloud iap web disable --resource-type=backend-services --service=SERVICE_ID
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `iap oauth-brands` | [`oauth-brands.md`](oauth-brands.md) | 3 | manage IAP OAuth brands — **deprecated** (see below) |
| `iap oauth-clients` | [`oauth-clients.md`](oauth-clients.md) | 5 | manage IAP OAuth clients — **deprecated** (see below) |
| `iap settings` | [`settings.md`](settings.md) | 2 | get/set IAP resource settings (CORS, GCIP, login hint) |
| `iap tcp` | [`tcp.md`](tcp.md) | 9 | manage IAP TCP tunnel Destination Groups |
| `iap web` | [`web.md`](web.md) | 6 | enable/disable IAP and manage web IAM policies |

Total: 25 GA commands. See [`index.md`](index.md) for the one-line command index.

> **Deprecation — `oauth-brands` / `oauth-clients`:** These groups call the IAP OAuth Admin APIs,
> which Google is shutting down. As of **Jan 19, 2026** new projects can no longer use these APIs,
> and on **Mar 19, 2026** the APIs are permanently shut down — the commands become non-functional.
> Use Google-managed OAuth instead: enable IAP from the Cloud console, or use IAP directly on
> Cloud Run, neither of which requires manually creating a brand/client.

## Common flags & tips

- **`--resource-type`** selects the IAP resource and constrains which other flags apply:
  - `iap web enable`/`disable`: `app-engine` | `backend-services`.
  - `iap web add/remove/get/set-iam-policy`: `app-engine` | `backend-services` | `forwarding-rule`.
  - `iap settings get`/`set`: `app-engine` | `iap_web` | `compute` | `organization` | `folder` |
    `backend-services` | `forwarding-rule` (for backend services, `compute` and `backend-services`
    are interchangeable).
- **`--service`** is required with `--resource-type=backend-services` on `web enable`/`disable`;
  for App Engine you can additionally scope to `--service` and `--version`.
- **Regional vs global:** add `--region` only for regional backend services / compute resources;
  omit it for global backend services and for App Engine (where `--region` does not apply).
- **TCP Destination Groups are always regional:** `--region` is required on
  `create`/`delete`/`describe`/`update` and on the IAM commands; `dest-groups list` defaults to
  all regions (`--region=-`). Populate with `--ip-range-list` (CIDRs) and/or `--fqdn-list`;
  on `update`, pass `--ip-range-list=""` or `--fqdn-list=""` to clear a list.
- **IAM members & roles:** `--member` takes `user:`, `group:`, `serviceAccount:`, `domain:`, or
  the special `allUsers` / `allAuthenticatedUsers`. Key IAP roles:
  `roles/iap.httpsResourceAccessor` (web access), `roles/iap.tunnelResourceAccessor` (TCP tunnel),
  `roles/iap.admin` (policy admin).
- **Conditional bindings:** `add/remove-iam-policy-binding` accept `--condition` /
  `--condition-from-file`; on `remove`, use `--all` to drop every binding for a member+role
  regardless of condition.
- **Policy files:** `get-iam-policy --format=json` emits an `etag`; re-supplying it in the file
  passed to `set-iam-policy` makes the write fail if the policy changed in the meantime.
- **Filtering Destination Groups:** `dest-groups list --filter="cidrs=CIDR"`,
  `--filter="fqdns=FQDN"`, or `--filter="name=NAME"`; combine with `--sort-by` and `--limit`.

## beta / alpha

`gcloud beta iap` and `gcloud alpha iap` mirror the GA surface (same five subgroups —
`oauth-brands`, `oauth-clients`, `settings`, `tcp`, `web`) with no documented commands beyond the
GA set. The `oauth-brands` / `oauth-clients` deprecation applies across GA, beta, and alpha.
New `settings` or `tcp` capabilities may appear in beta/alpha before graduating to GA — check the
beta/alpha reference pages when a feature is announced.

## Official documentation

- **Product docs home:** https://cloud.google.com/iap/docs — Cloud Identity-Aware Proxy overview.
- **Concepts:** https://cloud.google.com/iap/docs/concepts-overview — what IAP is and how it works.
- **TCP forwarding:** https://cloud.google.com/iap/docs/tcp-forwarding-overview — SSH/RDP tunneling without bastion hosts.
- **Managing access:** https://cloud.google.com/iap/docs/managing-access — IAP IAM roles (httpsResourceAccessor, tunnelResourceAccessor, iap.admin).
- **Enable on Compute Engine:** https://cloud.google.com/iap/docs/enabling-compute-howto — backend services and forwarding rules.
- **Enable on GKE:** https://cloud.google.com/iap/docs/enabling-kubernetes-howto — IAP via BackendConfig Ingress.
- **Enable on Cloud Run:** https://cloud.google.com/iap/docs/enabling-cloud-run — direct IAP on Cloud Run or via load balancer.
- **App Engine quickstart:** https://cloud.google.com/iap/docs/app-engine-quickstart — protect an App Engine app with Google-managed OAuth.
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/iap — all `gcloud iap` subgroups and commands.

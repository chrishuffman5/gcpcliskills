# gcloud access-approval — Access Approval

## Overview

Access Approval lets you require explicit approval whenever Google Cloud Customer Care and engineering teams need to access your customer data. Each access attempt generates a request that a designated administrator must approve, dismiss, or let expire — and approvals can be cryptographically signed with your own Cloud KMS key. Reach for this group to enroll projects/folders/organizations into Access Approval, manage the pending approval queue, and configure signing keys and notifications. It complements Access Transparency (which logs Google personnel actions) by putting you in the approval loop before access happens.

## Quick reference — common workflows

### 1. Enable Access Approval for a project (all services)
```bash
# Enable the API
gcloud services enable accessapproval.googleapis.com --project=PROJECT_ID

# Enroll all supported services and set a notification email
gcloud access-approval settings update \
  --project=PROJECT_ID \
  --enrolled_services=all \
  --notification_emails='security-team@example.com'

# Verify the resulting settings
gcloud access-approval settings get --project=PROJECT_ID
```

### 2. Enroll an organization for specific services
```bash
# At the organization level you can enroll individual services
gcloud access-approval settings update \
  --organization=ORG_ID \
  --enrolled_services='storage.googleapis.com,compute.googleapis.com' \
  --notification_emails='security-team@example.com'

gcloud access-approval settings get --organization=ORG_ID
```

### 3. List and inspect pending requests
```bash
# Pending requests for a project (list defaults to --state=pending)
gcloud access-approval requests list --project=PROJECT_ID

# All requests regardless of state
gcloud access-approval requests list --project=PROJECT_ID --state=all

# Pending requests owned by an organization
gcloud access-approval requests list --organization=ORG_ID

# Full detail for one request
gcloud access-approval requests get \
  projects/PROJECT_ID/approvalRequests/REQUEST_ID
```

### 4. Approve, dismiss, or revoke a request
```bash
# Approve a pending request (grants access until it expires)
gcloud access-approval requests approve \
  projects/PROJECT_ID/approvalRequests/REQUEST_ID

# Dismiss a pending request (does NOT deny if another approval exists)
gcloud access-approval requests dismiss \
  projects/PROJECT_ID/approvalRequests/REQUEST_ID

# Invalidate an already-approved request to revoke active access
gcloud access-approval requests invalidate \
  projects/PROJECT_ID/approvalRequests/REQUEST_ID
```

### 5. Use a custom KMS signing key and Pub/Sub notifications
```bash
# Retrieve the Access Approval service account (grant it KMS access first)
gcloud access-approval service-account get --project=PROJECT_ID

# Point Access Approval at a CMEK key version and a Pub/Sub topic
gcloud access-approval settings update \
  --project=PROJECT_ID \
  --active_key_version='projects/PROJECT_ID/locations/global/keyRings/RING/cryptoKeys/KEY/cryptoKeyVersions/1' \
  --notification_pubsub_topic='projects/PROJECT_ID/topics/TOPIC_NAME'

# Revert to the Google-managed key (empty value clears it)
gcloud access-approval settings update \
  --project=PROJECT_ID \
  --active_key_version=''
```

### 6. Tune approval policy and request scope preferences
```bash
# Set the approval policy (transparency | streamlined-support | access-approval | inherit-policy-from-parent)
gcloud access-approval settings update --project=PROJECT_ID \
  --approval_policy=access-approval

# Ask Google to request the narrowest scope, capped at the project level
gcloud access-approval settings update --project=PROJECT_ID \
  --prefer_no_broad_approval_requests=true \
  --request_scope_max_width_preference=PROJECT \
  --preferred_request_expiration_days=5
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `access-approval requests` | [`requests.md`](requests.md) | 5 | manage Access Approval requests (approve, dismiss, get, invalidate, list) |
| `access-approval service-account` | [`service-account.md`](service-account.md) | 1 | get the service account used to sign approvals with KMS |
| `access-approval settings` | [`settings.md`](settings.md) | 3 | manage Access Approval settings (delete, get, update) |

See [`index.md`](index.md) for a one-line index of all 9 commands.

## Common flags & tips

- **Resource scope is mutually exclusive.** Every command takes at most one of `--project`, `--folder`, or `--organization`. If none is supplied, gcloud falls back to the `core/project` config property. Folders and organizations use numeric IDs.
- **Request names are positional, not flags.** `approve`, `dismiss`, `get`, and `invalidate` take the full resource name as a positional `NAME` argument, e.g. `projects/PROJECT_ID/approvalRequests/REQUEST_ID`.
- **`requests list` defaults to pending.** Pass `--state=all` to see every request. Combine with standard list flags such as `--filter`, `--limit`, `--page-size`, and `--sort-by`.
- **`settings update` is a partial update.** You can change just the notification emails without touching enrolled services, and vice versa. Use `''` (empty string) to clear `--enrolled_services`, `--notification_emails`, or `--active_key_version`.
- **Enrollment granularity.** For project and folder enrollments only `--enrolled_services=all` is supported; per-service enrollment (e.g. `storage.googleapis.com,compute.googleapis.com`) is available at the organization level.
- **`--preferred_request_expiration_days`** must be between 1 and 30; it can be overridden when a request is created and at approval time.
- **Output formatting:** narrow the request list to one column with
  `gcloud access-approval requests list --project=PROJECT_ID --state=all --format='value(name)'`,
  or surface request state with
  `--format='table(name, requestedReason.type, requestedExpiration.expireTime)'`.

## beta / alpha

Both `gcloud beta access-approval` and `gcloud alpha access-approval` exist and mirror the GA `requests` and `settings` subgroups with the same subcommands and flags. They carry the usual pre-GA "might change without notice" caveat, and no capabilities unique to beta/alpha are documented. Note that the `service-account` subgroup is surfaced only in the GA track.

## Official documentation

- [Access Approval product home](https://docs.cloud.google.com/assured-workloads/access-approval/docs) — guides, reference, and release notes.
- [Access Approval overview](https://docs.cloud.google.com/assured-workloads/access-approval/docs/overview) — concepts and how approval requests flow.
- [Access control (IAM roles)](https://docs.cloud.google.com/assured-workloads/access-approval/docs/access-control) — viewer, approver, configEditor, and invalidator roles and their permissions.
- [Approve requests](https://docs.cloud.google.com/assured-workloads/access-approval/docs/approve-requests) — approving, dismissing, and taking no action on pending requests.
- [Supported services](https://docs.cloud.google.com/assured-workloads/access-approval/docs/supported-services) — services covered by Access Approval and their API identifiers.
- [REST API reference](https://docs.cloud.google.com/assured-workloads/access-approval/docs/reference/rest) — REST surface and the `accessapproval.googleapis.com` endpoint.
- [gcloud access-approval reference](https://cloud.google.com/sdk/gcloud/reference/access-approval) — full CLI command and flag reference.
- [gcloud settings update reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/settings/update) — every `settings update` flag in detail.
